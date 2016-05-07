###############################################################################


LANG1=kaz
LANG2=eng

PREFIX1=$(LANG1)-$(LANG2)

BASENAME=matxin-$(PREFIX1)

TARGETS_COMMON=$(PREFIX1).bilingual.bin \
	$(PREFIX1).chunk_type.dat \
	$(PREFIX1).lexical_selection.dat \
	$(PREFIX1).semantic.dat \
	$(PREFIX1).chunk_rules.dat 


@ap_include@

###############################################################################

$(PREFIX1).bilingual.bin: $(BASENAME).bilingual_mur.xml 
	lt-comp lr $< $@

$(PREFIX1).chunk_type.dat:  $(BASENAME).chunk_type.dat
	cp $< $@

$(PREFIX1).lexical_selection.dat: $(BASENAME).lexical_selection.dat
	cp $< $@

#
#
#


$(PREFIX1).semantic.dat: $(AP_SRC2)/matxin-$(LANG2).semantic.dat
	cat $<  > $@

#
#
#

$(PREFIX1).chunk_rules.dat: $(AP_SRC1)/matxin-$(LANG1).chunk_rules.dat
	cat $<  > $@

###############################################################################

EXTRA_DIST=$(BASENAME).bilingual_mur.xml \
	$(BASENAME).chunk_type.dat \
	$(BASENAME).intrachunk_move.dat \
	$(BASENAME).lexical_selection.dat

matxin_kaz_engdir=$(prefix)/share/matxin/$(BASENAME)
matxin_kaz_eng_srcdir=$(prefix)/share/matxin/$(BASENAME)

matxin_kaz_eng_DATA=$(TARGETS_COMMON)

# All modes are created by the same goal, listing several will just give problems with make -j2
noinst_DATA=modes/$(PREFIX1).mode

install-data-local: install-modes

CLEANFILES = $(TARGETS_COMMON)
clean-local:
	-rm -rf .deps modes

