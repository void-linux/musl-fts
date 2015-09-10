dnl Process this file with autoconf to produce a configure script

AC_PREREQ(2.69)

AC_INIT([fts], [1.1], [Jürgen Buchmüller <pullmoll@t-online.de>])

AM_INIT_AUTOMAKE([1.15])

AC_PROG_CC
AC_PROG_LIBTOOL

LT_INIT

AC_CHECK_HEADERS(assert.h dirent.h errno.h fcntl.h stdlib.h string.h unistd.h sys/param.h sys/stat.h)

AC_CONFIG_FILES([Makefile musl-fts.pc])
AC_OUTPUT
