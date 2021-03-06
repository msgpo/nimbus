# Honor aclocal flags
ACLOCAL="$ACLOCAL $ACLOCAL_FLAGS"

AC_INIT(metacity)
AM_INIT_AUTOMAKE(nimbus, 1.0)
DISTDIR=${PACKAGE}-${VERSION}
AM_MAINTAINER_MODE

AC_PROG_INTLTOOL([0.23])

# Checks for programs.
AC_PROG_CC
AC_PROG_INSTALL
AC_PROG_LN_S
AC_LIBTOOL_WIN32_DLL
AM_PROG_LIBTOOL
AC_PATH_PROG(GDK_PIXBUF_CSOURCE, gdk-pixbuf-csource, no)

# Checks for header files.
AC_HEADER_STDC
AM_CONFIG_HEADER([config.h])

PKG_CHECK_MODULES(GTK2, gtk+-2.0 >= 2.0.0)
AC_SUBST(GTK2_CFLAGS)
# remove cairo dependency hack
GTK2_LIBS=`echo $GTK2_LIBS | sed -e "s/-lpangocairo-1.0//g" | sed -e "s/-lcairo//g"`
AC_SUBST(GTK2_LIBS)

# Define the toplevel icons path here
AC_SUBST(themedir, "\${datadir}/icons/nimbus")
# Define  source toplevel icons path here
AC_SUBST(iconsrcdir)
iconsrcdir=`pwd`
echo $iconsrcdir



UTILS_REQUIRED=0.8.1

AC_MSG_CHECKING([icon-naming-utils >= $UTILS_REQUIRED])
PKG_CHECK_EXISTS(icon-naming-utils >= $UTILS_REQUIRED,
                 have_utils=yes, have_utils=no)
if test "x$have_utils" = "xyes"; then
   UTILS_PATH="`$PKG_CONFIG --variable=program_path icon-naming-utils`"
   ICONMAP="$UTILS_PATH/icon-name-mapping"
   AC_SUBST(ICONMAP)
   AC_MSG_RESULT([yes])
else
   AC_MSG_RESULT([no])
   AC_MSG_ERROR([icon-naming-utils >= $UTILS_REQUIRED is required to build
                 and install the nimbus icon theme])
fi


GTK2_VERSION=`$PKG_CONFIG --variable=gtk_binary_version gtk+-2.0`
AC_SUBST(GTK2_VERSION)

GETTEXT_PACKAGE=nimbus
AC_SUBST(GETTEXT_PACKAGE)
AC_DEFINE_UNQUOTED(GETTEXT_PACKAGE,"$GETTEXT_PACKAGE", [Gettext package.])
AM_GLIB_GNU_GETTEXT


AC_OUTPUT([
Makefile
gtk-engine/Makefile
gtk-engine/gtk-2.0/Makefile
gtk-engine/gtk-2.0/iconrc
gtk-engine/gtk-3.0/Makefile
gtk-engine/gtk-3.0/apps/Makefile
gtk-engine/gtk-3.0/assets/Makefile
gtk-engine/images/Makefile
metacity/Makefile
icons/192x192/devices/Makefile
icons/192x192/apps/Makefile
icons/192x192/categories/Makefile
icons/192x192/places/Makefile
icons/192x192/mimetypes/Makefile
icons/192x192/Makefile
icons/48x48/actions/Makefile
icons/48x48/devices/Makefile
icons/48x48/apps/Makefile
icons/48x48/status/Makefile
icons/48x48/emblems/Makefile
icons/48x48/categories/Makefile
icons/48x48/places/Makefile
icons/48x48/mimetypes/Makefile
icons/48x48/Makefile
icons/48x48/animations/Makefile
icons/32x32/actions/Makefile
icons/32x32/devices/Makefile
icons/32x32/apps/Makefile
icons/32x32/status/Makefile
icons/32x32/emblems/Makefile
icons/32x32/categories/Makefile
icons/32x32/places/Makefile
icons/32x32/mimetypes/Makefile
icons/32x32/Makefile
icons/24x24/actions/Makefile
icons/24x24/devices/Makefile
icons/24x24/apps/Makefile
icons/24x24/status/Makefile
icons/24x24/emblems/Makefile
icons/24x24/categories/Makefile
icons/24x24/places/Makefile
icons/24x24/mimetypes/Makefile
icons/24x24/Makefile
icons/24x24/animations/Makefile
icons/16x16/actions/Makefile
icons/16x16/devices/Makefile
icons/16x16/apps/Makefile
icons/16x16/status/Makefile
icons/16x16/emblems/Makefile
icons/16x16/categories/Makefile
icons/16x16/places/Makefile
icons/16x16/mimetypes/Makefile
icons/16x16/Makefile
icons/96x96/devices/Makefile
icons/96x96/apps/Makefile
icons/96x96/categories/Makefile
icons/96x96/places/Makefile
icons/96x96/mimetypes/Makefile
icons/96x96/Makefile
icons/36x36/actions/Makefile
icons/36x36/devices/Makefile
icons/36x36/apps/Makefile
icons/36x36/categories/Makefile
icons/36x36/places/Makefile
icons/36x36/mimetypes/Makefile
icons/36x36/Makefile
icons/36x36/animations/Makefile
icons/72x72/apps/Makefile
icons/72x72/categories/Makefile
icons/72x72/places/Makefile
icons/72x72/mimetypes/Makefile
icons/72x72/Makefile
icons/20x20/status/Makefile
icons/20x20/Makefile
icons/12x12/actions/Makefile
icons/12x12/apps/Makefile
icons/12x12/emblems/Makefile
icons/12x12/places/Makefile
icons/12x12/Makefile
icons/Makefile
po/Makefile.in
])
