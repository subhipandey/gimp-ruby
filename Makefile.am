## Process this file with automake to produce Makefile.in

SUBDIRS = \
    ext      \
    gimp-lib \
    plug-ins \
    po

if PLATFORM_WIN32
no_undefined = -no-undefined
path_separator = ;
else
path_separator = :
endif

rubybase = ruby

rubydir = $(GIMP_LIBDIR)/$(rubybase)

rubyenvdir = $(GIMP_LIBDIR)/environ
rubyinterpdir = $(GIMP_LIBDIR)/interpreters

rubyenvfile = $(rubyenvdir)/ruby.env
rubyinterpfile = $(rubyinterpdir)/ruby.interp

rubyconsolefile = ruby-fu-console

install-env-files:
	$(mkinstalldirs) '$(DESTDIR)$(rubyenvdir)'
	echo '$(path_separator) RUBYLIB=$${gimp_plug_in_dir}/$(rubybase)' > '$(DESTDIR)$(rubyenvfile)'
	cp 'ext/$(rubyconsolefile)' '$(DESTDIR)$(rubydir)'

install-interp-file:
	$(mkinstalldirs) '$(DESTDIR)$(rubyinterpdir)'
	echo 'ruby=$(RUBY_BIN)' > '$(DESTDIR)$(rubyinterpfile)'
	echo '/usr/bin/ruby=$(RUBY_BIN)' >> '$(DESTDIR)$(rubyinterpfile)'
	echo ':Ruby:E::rb::ruby:' >> '$(DESTDIR)$(rubyinterpfile)'

install-data-local: install-env-files install-interp-file

uninstall-local:
	rm -f '$(DESTDIR)$(rubyenvfile)' '$(DESTDIR)$(rubyinterpfile)'
	rm -f '$(DESTDIR)$(rubydir)/$(rubyconsolefile)'
	rmdir '$(DESTDIR)$(rubydir)'

EXTRA_DIST = \
    AUTHORS             \
    ChangeLog           \
    COPYING             \
    MAINTAINERS         \
    NEWS                \
    README              \
    autogen.sh          \
    intltool-extract.in	\
    intltool-merge.in  	\
    intltool-update.in  \
    notes.txt          	\
    todo.txt

DISTCLEANFILES = \
    intltool-extract \
    intltool-merge   \
    intltool-update
