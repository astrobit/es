CXX = $(MPICXX)

EXTRA_DIST = synapps.yaml

AM_CPPFLAGS = \
-I$(top_srcdir)/src/libes \
-I$(top_srcdir)/src/synapps \
-I$(top_srcdir)/external/yaml \
$(APPSPACK_CFLAGS) \
${cfitsio_CFLAGS} \
${yamlcpp_CFLAGS}

AM_LDFLAGS = \
-L$(top_builddir)/src/libes \
-L$(top_builddir)/src/synapps

AM_LIBS = \
$(top_builddir)/src/libes/libes.la \
$(APPSPACK_LIBS) $(LAPACK_LIBS) $(BLAS_LIBS) ${cfitsio_LIBS} ${yamlcpp_LIBS} -lm $(FLIBS)

AM_CXXFLAGS =

if HAVE_AM_OPENMP
  AM_CXXFLAGS += $(OPENMP_CXXFLAGS)
  AM_LIBS += $(OPENMP_CXXFLAGS)
endif

noinst_HEADERS = \
ES_Synapps_Config.hh \
ES_Synapps_Evaluator.hh \
ES_Synapps.hh

noinst_LTLIBRARIES = libesapps.la
libesapps_la_SOURCES =       \
ES_Synapps_Config.cc    \
ES_Synapps_Evaluator.cc
libesapps_la_CPPFLAGS = $(AM_CPPFLAGS)
libesapps_la_LIBADD = $(AM_LIBS)

bin_PROGRAMS = synapps

synapps_SOURCES  = synapps.cc
synapps_CPPFLAGS = $(AM_CPPFLAGS)
synapps_LDFLAGS  = $(AM_LDFLAGS)
synapps_LDADD    = libesapps.la $(AM_LIBS)

synappsyamldir = $(datadir)/es
synappsyaml_DATA = synapps.yaml

