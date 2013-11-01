dnl rkutils

dnl Initialization
AC_INIT([rkutils], [0.1], [xypron.glpk@gmx.de])
AM_INIT_AUTOMAKE([-Wall -Werror foreign])

dnl Archiver support.
AM_PROG_AR

dnl Enhanced libtool support.
LT_INIT

dnl Compiler check
AC_PROG_CC
AC_CHECK_PROG([have_cc],[$CC],[yes],[no])
if test [$have_cc] != [yes]; then
  AC_MSG_ERROR([$CC is missing])
fi
dnl Provide $(LN_S)
AC_PROG_LN_S

dnl Configure macros
AC_CONFIG_MACRO_DIR([m4])

dnl Create config.h
AC_CONFIG_HEADERS([config.h])

dnl Load pkg.m4
PKG_PROG_PKG_CONFIG

PKG_CHECK_MODULES([USB], [libusb],
  [AC_DEFINE([HAS_LIBUSB],[1],[usb.h is available])],
  [AC_MSG_ERROR([package libusb-dev missing])])
LDFLAGS="$USB_LIBS $LDFLAGS"
CPPFLAGS="$USB_CFLAGS $CPPFLAGS"

AC_MSG_NOTICE([CPPFLAGS = $CPPFLAGS])
AC_MSG_NOTICE([LDFLAGS  = $LDFLAGS])

dnl Makefiles
AC_CONFIG_FILES([
  Makefile
  src/Makefile
  ])

dnl Generate files
AC_OUTPUT
