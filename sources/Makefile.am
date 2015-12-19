RAW_API = $(ASSEMBLY_NAME)-api.raw
API = $(ASSEMBLY_NAME)-api.xml
METADATA = $(ASSEMBLY_NAME).metadata
DLL = $(top_srcdir)/out/$(ASSEMBLY_NAME).dll
DLLMAP = $(top_srcdir)/out/$(ASSEMBLY_NAME).dll.config
GLUEDIR = $(srcdir)/glue

gapidir = $(GAPIXMLDIR)
gapi_DATA = $(API)

# Add any extra source files you need here
sources =

build_sources = AssemblyInfo.cs $(sources)

CLEANFILES = $(DLL) generated-stamp generated/*/*.cs $(API)

DISTCLEANFILES = AssemblyInfo.cs

noinst_DATA = $(DLL)

EXTRA_DIST = \
	$(RAW_API) \
	$(sources) \
	$(METADATA) \
	AssemblyInfo.cs.in \
	$(ASSEMBLY_NAME).snk

all: generated-stamp $(ASSEMBLY)

$(API): $(srcdir)/$(RAW_API) $(srcdir)/$(METADATA)
	cp $(srcdir)/$(RAW_API) $(API)
	chmod u+w $(API)
	$(GAPI_FIXUP) --api=$(srcdir)/$(API) --metadata=$(srcdir)/$(METADATA)

generated-stamp: $(API)
	 $(GAPI_CODEGEN) --generate $(srcdir)/$(API) $(GTK_SHARP_CFLAGS) \
		--outdir=generated \
		--glue-filename=$(GLUEDIR)/generated.c --gluelib-name=libsoupsharpglue-2.42.2.so \
		--glue-includes=libsoup/soup.h,libsoup/soup-cache.h,libsoup/soup-requester.h,libsoup/soup-request-http.h,libsoup/soup-request-data.h,libsoup/soup-request-file.h --gapidir=$(gapidir) \
	 	--assembly-name=$(ASSEMBLY_NAME) && touch generated-stamp

$(DLL): $(build_sources) generated-stamp
	$(CSC) -nowarn:169 -unsafe -target:library \
		$(build_sources)  $(GLIBSHARP_LIBS) $(GTK_SHARP_LIBS) generated/*/*.cs -out:$(DLL)

install-data-local:
	echo "$(GACUTIL) /i $(DLL) /f $(GACUTIL_FLAGS)";  \
        $(GACUTIL) /i $(DLL) /f $(GACUTIL_FLAGS) || exit 1;

uninstall-local:
	echo "$(GACUTIL) /u $(ASSEMBLY_NAME) $(GACUTIL_FLAGS)"; \
        $(GACUTIL) /u $(ASSEMBLY_NAME) $(GACUTIL_FLAGS) || exit 1;
