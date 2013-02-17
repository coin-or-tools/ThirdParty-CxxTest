# Copyright (C) 2007-2009 Stefan Vigerske
# All Rights Reserved.
# This file is distributed under the Eclipse Public License.

## $Id: Makefile.am 2639 2012-11-20 15:30:18Z stefan $

AUTOMAKE_OPTIONS = foreign

EXTRA_DIST = get.CxxTest INSTALL.CxxTest

# pkg-config data file
pkgconfiglibdir = $(libdir)/pkgconfig
pkgconfiglib_DATA = coincxxtest.pc

# Source and header files to be installed in $(includedir)/cxxtest. Call them
# data to evade automake's need to see a static list for code files.

cxxincdir = $(includedir)/coin/ThirdParty/cxxtest
cxxinc_DATA = $(CXXTESTHDRS)

# Install cxxtestgen in the bin directory

bin_SCRIPTS = cxxtest/bin/cxxtestgen

# Copy the cxxtest/python subdirectory into $(libdir)/cxxtest

install-exec-local:
	cp -r $(srcdir)/cxxtest/python $(libdir)/cxxtest

uninstall-local:
	rm -rf $(libdir)/cxxtest

# Must be set, even if empty

DISTCLEANFILES =

include BuildTools/Makemain.inc

