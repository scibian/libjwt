AC_PREREQ([2.61])
AC_INIT([libjwt], [1.10.2], [https://github.com/benmcollins/libjwt/issues])
AM_INIT_AUTOMAKE
LT_PREREQ([2.2])
LT_INIT([])
AC_CONFIG_MACRO_DIR([m4])
AC_CONFIG_HEADERS([libjwt/config.h])

AC_SUBST([AM_CFLAGS], [-Wall])

dnl Prefer OpenSSL unless asked to ignore it
AC_ARG_WITH([openssl],
	AS_HELP_STRING([--without-openssl], [Ignore presence of OpenSSL libraries and use GnuTLS]))

AS_IF([test "x$with_openssl" != "xno"], [
	PKG_CHECK_MODULES([OPENSSL], [openssl >= 0.9.8])
	AM_CONDITIONAL([HAVE_OPENSSL], [true])
], [
	PKG_CHECK_MODULES([GNUTLS], [gnutls >= 3.5.8])
	AM_CONDITIONAL([HAVE_OPENSSL], [false])
])

PKG_CHECK_MODULES([JANSSON], [jansson >= 2.0])
PKG_CHECK_MODULES([CHECK], [check >= 0.9.4], [true], [true])

AX_VALGRIND_CHECK

AX_CODE_COVERAGE

WEAK_ALIAS_SUPPORT

DX_MAN_FEATURE(ON)
DX_HTML_FEATURE(ON)
DX_CHM_FEATURE(OFF)
DX_CHI_FEATURE(OFF)
DX_RTF_FEATURE(OFF)
DX_XML_FEATURE(OFF)
DX_PDF_FEATURE(OFF)
DX_PS_FEATURE(OFF)
DX_INIT_DOXYGEN($PACKAGE_NAME, doxygen.cfg)

AC_CONFIG_FILES([
	Makefile
	include/Makefile
	libjwt/Makefile
	tests/Makefile
	libjwt/libjwt.pc
])

AC_OUTPUT
