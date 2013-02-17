# Copyright (C) 2007-2010 Stefan Vigerske and others.
# All Rights Reserved.
# This file is distributed under the Eclipse Public License.

## $Id: configure.ac 2652 2012-11-21 14:49:57Z stefan $

#############################################################################
#                       Names and other basic things                        #
#############################################################################

AC_PREREQ(2.59)

AC_INIT([ThirdPartyCxxTest],[trunk],
	[http://projects.coin-or.org/BuildTools/newticket])

AC_COPYRIGHT([
Copyright 2007-2010 Stefan Vigerske and others.
All Rights Reserved.
This file is part of the open source package Coin which is distributed
under the Eclipse Public License.])

# List one file in the package so that the configure script can test
# whether the package is actually there.
AC_CONFIG_SRCDIR(cxxtest/bin/cxxtestgen)

# Where should everything be installed by default?  Here, we want it
# to be installed directly in 'bin', 'lib', 'include' subdirectories
# of the directory where configure is run.  The default would be
# /usr/local.
AC_PREFIX_DEFAULT([`pwd`])

AC_COIN_PROJECTDIR_INIT(CxxTest)

#############################################################################
#                         Standard build tool stuff                         #
#############################################################################

# CxxTest is a bit of an odd duck. It's source code, which might well
# benefit from some configuration, but it's never compiled on its own. All
# of the various bits of source here are used to compose custom test code
# for the unit under test. I'm going to leave these checks in place during
# development. It may be possible to remove some of the at a later date.
# -- lh, 130216 --

# Get the system type
AC_CANONICAL_BUILD

# Turn off warnings and pedantic mode since it seems to make trouble on the
# solaris platform and we can't fix it anyway.
coin_skip_warn_cflags=yes

# Check if the user wants to produce debugging code.
AC_COIN_DEBUG_COMPILE(CxxTest)

# Get the name of the C compiler
AC_COIN_PROG_CC

# Check if pkg-config is available (to set up the addlibs file).
AC_COIN_HAS_PKGCONFIG

# Initialize automake
AC_COIN_INIT_AUTO_TOOLS

###########################################################################
#                            check CxxTest version                        #
###########################################################################

# Get the version. Remember that m4 eats square brackets
AC_MSG_CHECKING([CxxTest version])
CXXTESTVER=`$srcdir/cxxtest/bin/cxxtestgen --version`
CXXTESTVER=`echo $CXXTESTVER | sed -n -e ['s/.*\([0-9]\.[0-9]\)\./\1/p']`
AC_MSG_RESULT([$CXXTESTVER])
AC_SUBST(CXXTESTVER)

# Generate a list of the header and code files that cxxtest uses when it
# generates the driver program for tests.

files=`ls $srcdir/cxxtest/cxxtest`
for file in $files ; do
  CXXTESTHDRS="$CXXTESTHDRS $srcdir/cxxtest/cxxtest/$file"
done
AC_SUBST(CXXTESTHDRS)

AC_CONFIG_FILES([Makefile coincxxtest.pc coincxxtest-uninstalled.pc])

AC_COIN_FINALIZE
