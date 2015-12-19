lib_LTLIBRARIES = libsoupsharpglue-2.42.2.la

libsoupsharpglue_2_42_2_la_SOURCES =

nodist_libsoupsharpglue_2_42_2_la_SOURCES = generated.c

libsoupsharpglue_2_42_2_la_LDFLAGS = -module -avoid-version -no-undefined

libsoupsharpglue_2_42_2_la_LIBADD = $(SOUP_LIBS)

AM_CPPFLAGS = $(SOUP_CFLAGS) -I$(top_srcdir)

AM_CFLAGS = -DLIBSOUP_USE_UNSTABLE_REQUEST_API

libsoupsharpglue.dll: $(libsoupsharpglue_2_42_2_la_OBJECTS) libsoupsharpglue.rc libsoupsharpglue.def
	./build-dll libsoupsharpglue $(VERSION)

CLEANFILES = lib*.a lib*.dll

DISTCLEANFILES = $(nodist_libsoupsharpglue_2_42_2_la_SOURCES)

EXTRA_DIST =
