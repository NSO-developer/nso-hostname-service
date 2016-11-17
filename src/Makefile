all:	fxs

# Include standard NCS examples build definitions and rules
include $(NCS_DIR)/src/ncs/build/include.ncs.mk

SRC = $(wildcard yang/*.yang)
FXS = $(SRC:yang/%.yang=../load-dir/%.fxs)

YANGPATH ?= --yangpath yang
## Uncomment and patch the line below if you have a dependency to a NED
# YANGPATH += ../../<ned-name>/src/ncsc-out/modules

fxs:	$(FXS)

../load-dir/%.fxs:	yang/%.yang
	$(NCSC)  `ls $*-ann.yang  > /dev/null 2>&1 && echo "-a $*-ann.yang"` \
             $(YANGPATH) -c -o $@ $<
clean:
	rm -rf  ../load-dir/*

