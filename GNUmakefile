
export SOURCE_PORT=/usr/games/chocolate-doom

# Quiet output, convert to lower case, don't restore timestamps,
# overwrite without prompt, extract to extract/ directory.
UNZIPOPTS = -q -LL -o -d extract

OUTPUTS =
WADS = extract/miniwad.wad

all: check

extract/%:
	unzip $(UNZIPOPTS) $< $(subst extract/,,$@)
	@touch $@

extract/miniwad.wad: miniwad.zip
testrunner: $(SOURCE_PORT) extract/miniwad.wad

# Alien Vendetta, Ancalagon 4:13:37
extract/av.wad: pwads/av_new.zip
extract/30av-25337.lmp: demos/avall-41337.zip

output/av.txt: testrunner extract/av.wad extract/30av-25337.lmp
	./testrunner -merge av.wad -timedemo extract/30av-25337.lmp >$@

WADS += extract/av.wad
OUTPUTS += output/av.txt

# Cyberdreams, SuperWeaponDude 19:04
extract/cyber110.wad: pwads/cydreams.zip
extract/cyber110.deh: pwads/cydreams.zip
extract/30cyx1904.lmp: demos/cyallx1904.zip

output/cydreams.txt: testrunner extract/cyber110.wad extract/cyber110.deh extract/30cyx1904.lmp
	./testrunner -deh cyber110.deh -merge cyber110.wad -timedemo extract/30cyx1904.lmp >$@

WADS += extract/cyber110.wad
OUTPUTS += output/cydreams.txt

# Doom 2 The Way Id Did, William "crate" Striegl 45:25
extract/d2twid.wad: pwads/d2twid.zip
extract/30id-4525.lmp: demos/30id-4525.zip

output/d2twid.txt: testrunner extract/d2twid.wad extract/30id-4525.lmp
	./testrunner -nodehlump -merge d2twid.wad -timedemo extract/30id-4525.lmp >$@

WADS += extract/d2twid.wad
OUTPUTS += output/d2twid.txt

# Eternal Doom, ELMLE 2:18:54
extract/eternall.wad: pwads/eternal.zip
extract/30et-13854.lmp: demos/etall-21854.zip

output/eternal.txt: testrunner extract/eternall.wad extract/30et-13854.lmp
	./testrunner -merge eternall.wad -timedemo extract/30et-13854.lmp >$@

WADS += extract/eternall.wad
OUTPUTS += output/eternal.txt

# Hell Revealed, Yonatan Donner/Haggay Niv 43:39
extract/hr.wad: pwads/hr.zip
extract/hqr-4339.lmp: demos/hrall-4339.zip

output/hr.txt: testrunner extract/hr.wad extract/hqr-4339.lmp
	./testrunner -merge hr.wad -timedemo extract/hqr-4339.lmp >$@

WADS += extract/hr.wad
OUTPUTS += output/hr.txt

# Hell Revealed 2, tchkb 2:29:44
extract/hr2final.wad: pwads/hr2final.zip
extract/h2alls2-22944.lmp: demos/h2all-22944.zip

output/hr2.txt: testrunner extract/hr2final.wad extract/h2alls2-22944.lmp
	./testrunner -merge hr2final.wad -timedemo extract/h2alls2-22944.lmp >$@

WADS += extract/hr2final.wad
OUTPUTS += output/hr2.txt

# Memento Mori, stx-Vile 83:56
extract/mm.wad: pwads/mm_allup.zip
extract/30mm8356.lmp: demos/30mm8356.zip

output/mm.txt: testrunner extract/mm.wad extract/30mm8356.lmp
	./testrunner -merge mm.wad -timedemo extract/30mm8356.lmp >$@

WADS += extract/mm.wad
OUTPUTS += output/mm.txt

# Memento Mori 2, Cyberdemon531 49:38
extract/mm2.wad: pwads/mm2.zip
extract/mm2allnomo4938.lmp: demos/m2allo4938.zip

output/mm2.txt: testrunner extract/mm2.wad extract/mm2allnomo4938.lmp
	./testrunner -merge mm2.wad -timedemo extract/mm2allnomo4938.lmp >$@

WADS += extract/mm2.wad
OUTPUTS += output/mm2.txt

# Plutonia 2, Red-XIII 1:05:04
extract/pl2.wad: pwads/pl2.zip
extract/pl2all1.lmp: demos/p2all-6504.zip

output/pl2.txt: testrunner extract/pl2.wad extract/pl2all1.lmp
	./testrunner -gameversion final -merge pl2.wad -timedemo extract/pl2all1.lmp >$@

WADS += extract/pl2.wad
OUTPUTS += output/pl2.txt


wads: $(WADS)

check: $(OUTPUTS)
	@diff -q -x .gitignore -r expected output && echo all tests passed

clean:
	rm -rf output/* extract/*

.PHONY: wads check clean all
