#
# Copyright (C) 2024 Simon Howard
#
# This program is free software; you can redistribute it and/or modify it
# under the terms of the GNU General Public License as published by the
# Free Software Foundation; either version 2 of the License, or (at your
# option) any later version. This program is distributed in the hope that
# it will be useful, but WITHOUT ANY WARRANTY; without even the implied
# warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
#

export SDL_VIDEODRIVER = dummy

SOURCE_PORT_NAME = chocolate-doom
SOURCE_PORT := $(shell which $(SOURCE_PORT_NAME) || echo missing_source_port)
DOOMOPTS = -mb 24 -nodraw -noblit -nosound \
           -noautoload -nogui -nograbmouse -nofullscreen

ALL_DEMOS = $(patsubst %,demos/%,$(shell cat demos.txt))
OUTPUTS = $(subst .lmp,.txt,$(subst demos/,output/,$(ALL_DEMOS)))
UNZIPOPTS = -L -o

check: expected output
	diff -x .gitignore -u -r expected output
	@echo all tests passed

output: $(OUTPUTS)

missing_source_port:
	@echo "Failed to find" $(SOURCE_PORT_NAME) "in PATH."
	@echo "To specify the path explicitly:"
	@echo "  make SOURCE_PORT=/path/to/$(SOURCE_PORT_NAME)"
	@echo "Or to search for a different source port:"
	@echo "  make SOURCE_PORT_NAME=lemon-doom"
	@false

.rules: makerules
	./makerules $@

extract/%:
	unzip $(UNZIPOPTS) -d extract $< $(notdir $@)
	@touch $@

extract/av.wad: pwads/av_new.zip
extract/cyber110.wad: pwads/cydreams.zip
extract/cyber110.deh: pwads/cydreams.zip
extract/d2twid.wad: pwads/d2twid.zip
extract/eternall.wad: pwads/eternal.zip
extract/hr.wad: pwads/hr.zip
extract/hr2final.wad: pwads/hr2final.zip
extract/mm.wad: pwads/mm_allup.zip
extract/mm2.wad: pwads/mm2.zip
extract/pl2.wad: pwads/pl2.zip

clean:
	rm -f extract/*.wad
	rm -rf output/*
	rm -f .rules

include .rules
