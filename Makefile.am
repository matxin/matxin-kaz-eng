###############################################################################


LANG1=kaz
LANG2=eng

PREFIX1=$(LANG1)-$(LANG2)

BASENAME=matxin-$(PREFIX1)

TARGETS_COMMON=$(PREFIX1).autobil.bin \
	$(PREFIX1).t1x.bin \
	$(PREFIX1).l1x.dat \
	$(PREFIX1).gnx.bin \
	$(PREFIX1).autogen.bin \
	$(PREFIX1).autopgen.bin 


@ap_include@

###############################################################################


#
#
#


$(PREFIX1).autobil.bin: $(BASENAME).$(PREFIX1).dix
	lt-comp lr $< $@

$(PREFIX1).t1x.bin: $(BASENAME).$(PREFIX1).t1x
	matxin-preprocess-transfer $< $@

$(PREFIX1).l1x.dat: $(BASENAME).$(PREFIX1).l1x
	cp $< $@

$(PREFIX1).gnx.bin: $(AP_SRC2)/$(LANG2).gnx.bin
	cp $< $@

$(PREFIX1).autogen.bin: $(AP_SRC2)/$(LANG2).autogen.bin
	cp $< $@


#
#
#


$(PREFIX1).autopgen.bin: $(AP_SRC2a)/$(LANG2).autopgen.bin
	cp $< $@

###############################################################################

EXTRA_DIST=$(BASENAME).$(PREFIX1).dix

matxin_kaz_engdir=$(prefix)/share/matxin/$(BASENAME)
matxin_kaz_eng_srcdir=$(prefix)/share/matxin/$(BASENAME)

matxin_kaz_eng_DATA=$(TARGETS_COMMON)

# All modes are created by the same goal, listing several will just give problems with make -j2
noinst_DATA=modes/$(PREFIX1).mode

install-data-local: install-modes

CLEANFILES = $(TARGETS_COMMON)
clean-local:
	-rm -rf .deps modes

