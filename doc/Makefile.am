###Copyright (C) 2018 Vincent Torri <vincent dot torri at gmail dot com
###This code is public domain and can be freely used or copied.

MAINTAINERCLEANFILES = Makefile.in

### This is meant to be run in the doc directory itself.
### Not to be run from anywhere but in the source tree.

doc: buildconsumerpdf buildproducerpdf
# These pdf builds are to be undertaken only on request.
buildconsumerpdf:
	sh $(top_srcdir)/doc/pdfbld.sh -c

buildproducerpdf:
	rm libdwarfp.pdf
	sh $(top_srcdir)/doc/pdfbld.sh -p

man_MANS = dwarfdump.1
if HAVE_DWARFGEN
man_MANS += dwarfgen.1
endif

dox_verbose = $(dox_verbose_@AM_V@)
dox_verbose_ = $(dox_verbose_@AM_DEFAULT_V@)
dox_verbose_0 = @echo "  DOX      $@";

if HAVE_DOC
all-local: doxygen

doxygen:
	$(dox_verbose)$(DOXYGEN)

install-data-local:
	$(MKDIR_P) $(docdir)
	cp -r html $(docdir)
	cp -r latex $(docdir)
endif

clean-local:
	rm -rf html latex

uninstall-local:
	rm -rf $(docdir)/html $(docdir)/latex

EXTRA_DIST = \
Doxyfile \
mips_extensions.mm \
mips_extensions.pdf \
checkexamples.c \
dwarfdump.1 \
dwarfgen.1  \
libdwarf.pdf \
libdwarfp.mm \
libdwarfp.pdf \
pdfbld.sh
