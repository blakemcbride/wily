dnl Process this file with autoconf to produce a configure script.
AC_INIT
AC_CONFIG_SRCDIR([wily/wily.c])
AC_CONFIG_HEADERS([config.h])

dnl Checks for programs.
AC_PROG_INSTALL
AC_PROG_CC
AC_PROG_LN_S
AC_PROG_RANLIB

AC_SEARCH_LIBS([strerror],[cposix])
AC_PATH_XTRA

dnl Checks for libraries.
AC_CHECK_LIB(m, sin)
AC_CHECK_LIB(nsl, gethostent)
AC_CHECK_LIB(socket, connect)

dnl Checks for header files.
AC_HEADER_DIRENT
m4_warn([obsolete],
[The preprocessor macro 'STDC_HEADERS' is obsolete.
  Except in unusual embedded environments, you can safely include all
  C89 headers unconditionally.])dnl
# Autoupdate added the next two lines to ensure that your configure
# script's behavior did not change.  They are probably safe to remove.
AC_CHECK_INCLUDES_DEFAULT
AC_PROG_EGREP

AC_HEADER_SYS_WAIT
AC_CHECK_HEADERS(fcntl.h limits.h malloc.h sys/time.h unistd.h sys/select.h stdarg.h stdlib.h)

dnl Checks for typedefs, structures, and compiler characteristics.
AC_C_CONST
AC_TYPE_SIZE_T
m4_warn([obsolete],
[Update your code to rely only on HAVE_SYS_TIME_H,
then remove this warning and the obsolete code below it.
All current systems provide time.h; it need not be checked for.
Not all systems provide sys/time.h, but those that do, all allow
you to include it and time.h simultaneously.])dnl
AC_CHECK_HEADERS_ONCE([sys/time.h])
# Obsolete code to be removed.
if test $ac_cv_header_sys_time_h = yes; then
  AC_DEFINE([TIME_WITH_SYS_TIME],[1],[Define to 1 if you can safely include both <sys/time.h>
	     and <time.h>.  This macro is obsolete.])
fi
# End of obsolete code.

AC_CHECK_HAVE_TYPE(ulong)
AC_CHECK_HAVE_TYPE(ushort)
AC_CHECK_HAVE_TYPE(uint)
AC_CHECK_HAVE_TYPE(uchar)
AC_CHECK_HAVE_TYPE(caddr_t)

dnl Checks for library functions.
m4_warn([obsolete],
[your code may safely assume C89 semantics that RETSIGTYPE is void.
Remove this warning and the 'AC_CACHE_CHECK' when you adjust the code.])dnl
AC_CACHE_CHECK([return type of signal handlers],[ac_cv_type_signal],[AC_COMPILE_IFELSE(
[AC_LANG_PROGRAM([#include <sys/types.h>
#include <signal.h>
],
		 [return *(signal (0, 0)) (0) == 1;])],
		   [ac_cv_type_signal=int],
		   [ac_cv_type_signal=void])])
AC_DEFINE_UNQUOTED([RETSIGTYPE],[$ac_cv_type_signal],[Define as the return type of signal handlers
		    ('int' or 'void').])

AC_FUNC_VPRINTF
AC_CHECK_FUNCS(strerror memmove remove)

AC_CONFIG_FILES([Makefile wily/Makefile libXg/Makefile libframe/Makefile libmsg/Makefile])
AC_OUTPUT
