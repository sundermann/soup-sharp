lib_LTLIBRARIES = libsoupsharpglue-2.40.3.la

libsoupsharpglue_2_40_3_la_SOURCES =

nodist_libsoupsharpglue_2_40_3_la_SOURCES = generated.c

libsoupsharpglue_2_40_3_la_LDFLAGS = -module -avoid-version -no-undefined

libsoupsharpglue_2_40_3_la_LIBADD = $(SOUP_LIBS)

INCLUDES = $(SOUP_CFLAGS) -I$(top_srcdir)

CFLAGS = -DLIBSOUP_USE_UNSTABLE_REQUEST_API

libsoupsharpglue.dll: $(libsoupsharpglue_2_40_3_la_OBJECTS) libsoupsharpglue.rc libsoupsharpglue.def
	./build-dll libsoupsharpglue $(VERSION)

CLEANFILES = lib*.a lib*.dll

EXTRA_DIST =
