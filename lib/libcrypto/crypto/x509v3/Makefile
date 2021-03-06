#
# OpenSSL/crypto/x509v3/Makefile
#

DIR=	x509v3
TOP=	../..
CC=	cc
INCLUDES= -I.. -I$(TOP) -I../../include
CFLAG=-g
MAKEFILE=	Makefile
AR=		ar r

CFLAGS= $(INCLUDES) $(CFLAG)

GENERAL=Makefile README
TEST=v3nametest.c
APPS=

LIB=$(TOP)/libcrypto.a
LIBSRC=	v3_bcons.c v3_bitst.c v3_conf.c v3_extku.c v3_ia5.c v3_lib.c \
v3_prn.c v3_utl.c v3err.c v3_genn.c v3_alt.c v3_skey.c v3_akey.c v3_pku.c \
v3_int.c v3_enum.c v3_sxnet.c v3_cpols.c v3_crld.c v3_purp.c v3_info.c \
v3_ocsp.c v3_akeya.c v3_pmaps.c v3_pcons.c v3_ncons.c v3_pcia.c v3_pci.c \
pcy_cache.c pcy_node.c pcy_data.c pcy_map.c pcy_tree.c pcy_lib.c \
v3_asid.c v3_addr.c v3_scts.c
LIBOBJ= v3_bcons.o v3_bitst.o v3_conf.o v3_extku.o v3_ia5.o v3_lib.o \
v3_prn.o v3_utl.o v3err.o v3_genn.o v3_alt.o v3_skey.o v3_akey.o v3_pku.o \
v3_int.o v3_enum.o v3_sxnet.o v3_cpols.o v3_crld.o v3_purp.o v3_info.o \
v3_ocsp.o v3_akeya.o v3_pmaps.o v3_pcons.o v3_ncons.o v3_pcia.o v3_pci.o \
pcy_cache.o pcy_node.o pcy_data.o pcy_map.o pcy_tree.o pcy_lib.o \
v3_asid.o v3_addr.o v3_scts.o

SRC= $(LIBSRC)

EXHEADER= x509v3.h
HEADER=	$(EXHEADER) pcy_int.h

ALL=    $(GENERAL) $(SRC) $(HEADER)

top:
	(cd ../..; $(MAKE) DIRS=crypto SDIRS=$(DIR) sub_all)

all:	lib

lib:	$(LIBOBJ)
	$(AR) $(LIB) $(LIBOBJ)
	$(RANLIB) $(LIB) || echo Never mind.
	@touch lib

files:
	$(PERL) $(TOP)/util/files.pl Makefile >> $(TOP)/MINFO

links:
	@$(PERL) $(TOP)/util/mklink.pl ../../include/openssl $(EXHEADER)
	@$(PERL) $(TOP)/util/mklink.pl ../../test $(TEST)
	@$(PERL) $(TOP)/util/mklink.pl ../../apps $(APPS)

install:
	@[ -n "$(INSTALLTOP)" ] # should be set by top Makefile...
	@headerlist="$(EXHEADER)"; for i in $$headerlist ; \
	do  \
	(cp $$i $(INSTALL_PREFIX)$(INSTALLTOP)/include/openssl/$$i; \
	chmod 644 $(INSTALL_PREFIX)$(INSTALLTOP)/include/openssl/$$i ); \
	done;

tags:
	ctags $(SRC)

tests:

lint:
	lint -DLINT $(INCLUDES) $(SRC)>fluff

update: depend

depend:
	@[ -n "$(MAKEDEPEND)" ] # should be set by upper Makefile...
	$(MAKEDEPEND) -- $(CFLAG) $(INCLUDES) $(DEPFLAG) -- $(PROGS) $(LIBSRC)

dclean:
	$(PERL) -pe 'if (/^# DO NOT DELETE THIS LINE/) {print; exit(0);}' $(MAKEFILE) >Makefile.new
	mv -f Makefile.new $(MAKEFILE)

clean:
	rm -f *.o *.obj lib tags core .pure .nfs* *.old *.bak fluff

# DO NOT DELETE THIS LINE -- make depend depends on it.

pcy_cache.o: ../../e_os.h ../cryptlib.h pcy_cache.c pcy_int.h
pcy_data.o: ../../e_os.h ../cryptlib.h pcy_data.c pcy_int.h
pcy_lib.o: ../../e_os.h ../cryptlib.h pcy_int.h pcy_lib.c
pcy_map.o: ../../e_os.h ../cryptlib.h pcy_int.h pcy_map.c
pcy_node.o: pcy_int.h pcy_node.c
pcy_tree.o: ../../e_os.h ../cryptlib.h pcy_int.h pcy_tree.c
v3_addr.o: ../../e_os.h ../cryptlib.h v3_addr.c
v3_akey.o: ../../e_os.h ../cryptlib.h v3_akey.c
v3_akeya.o: ../../e_os.h ../cryptlib.h v3_akeya.c
v3_alt.o: ../../e_os.h ../cryptlib.h v3_alt.c
v3_asid.o: ../../e_os.h ../cryptlib.h v3_asid.c
v3_bcons.o: ../../e_os.h ../cryptlib.h v3_bcons.c
v3_bitst.o: ../../e_os.h ../cryptlib.h v3_bitst.c
v3_conf.o: ../../e_os.h ../cryptlib.h v3_conf.c
v3_cpols.o: ../../e_os.h ../cryptlib.h pcy_int.h v3_cpols.c
v3_crld.o: ../../e_os.h ../cryptlib.h v3_crld.c
v3_enum.o: ../../e_os.h ../cryptlib.h v3_enum.c
v3_extku.o: ../../e_os.h ../cryptlib.h v3_extku.c
v3_genn.o: ../../e_os.h ../cryptlib.h v3_genn.c
v3_ia5.o: ../../e_os.h ../cryptlib.h v3_ia5.c
v3_info.o: ../../e_os.h ../cryptlib.h v3_info.c
v3_int.o: ../../e_os.h ../cryptlib.h v3_int.c
v3_lib.o: ../../e_os.h ../cryptlib.h ext_dat.h v3_lib.c
v3_ncons.o: ../../e_os.h ../cryptlib.h v3_ncons.c
v3_ocsp.o: ../../e_os.h ../cryptlib.h v3_ocsp.c
v3_pci.o: ../../e_os.h ../cryptlib.h v3_pci.c
v3_pcia.o: v3_pcia.c
v3_pcons.o: ../../e_os.h ../cryptlib.h v3_pcons.c
v3_pku.o: ../../e_os.h ../cryptlib.h v3_pku.c
v3_pmaps.o: ../../e_os.h ../cryptlib.h v3_pmaps.c
v3_prn.o: ../../e_os.h ../cryptlib.h v3_prn.c
v3_purp.o: ../../e_os.h ../cryptlib.h v3_purp.c
v3_scts.o: ../../e_os.h ../cryptlib.h v3_scts.c
v3_skey.o: ../../e_os.h ../cryptlib.h v3_skey.c
v3_sxnet.o: ../../e_os.h ../cryptlib.h v3_sxnet.c
v3_utl.o: ../../e_os.h ../cryptlib.h v3_utl.c
v3err.o: v3err.c
