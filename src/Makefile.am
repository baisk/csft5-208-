SRC_SPHINX = sphinx.cpp sphinxexcerpt.cpp sphinxquery.cpp \
	sphinxsoundex.cpp sphinxmetaphone.cpp sphinxstemen.cpp sphinxstemru.cpp sphinxstemcz.cpp \
	sphinxutils.cpp md5.cpp sphinxstd.cpp sphinxsort.cpp sphinxexpr.cpp sphinxfilter.cpp \
	sphinxsearch.cpp sphinxrt.cpp

SRC_MD5 = md5.cpp
SRC_HIREDIS = hiredis/hiredis.c hiredis/async.c hiredis/dict.c  hiredis/net.c hiredis/sds.c

noinst_LIBRARIES = libsphinx.a
libsphinx_a_SOURCES = $(SRC_SPHINX) $(SRC_MD5) $(SRC_HIREDIS)

bin_PROGRAMS = indexer searchd search spelldump indextool
noinst_PROGRAMS = tests

indexer_SOURCES = indexer.cpp
searchd_SOURCES = searchd.cpp
search_SOURCES = search.cpp
spelldump_SOURCES = spelldump.cpp
indextool_SOURCES = indextool.cpp
tests_SOURCES = tests.cpp

BUILT_SOURCES = extract-version
.PHONY: extract-version
extract-version:
	/bin/sh svnxrev.sh ..

AM_CPPFLAGS = -DSYSCONFDIR="\"$(sysconfdir)\"" -DDATADIR="\"$(localstatedir)/data\""
COMMON_LIBS = libsphinx.a $(LIBSTEMMER_LIBS) $(MYSQL_LIBS) $(PGSQL_LIBS)
LDADD = $(COMMON_LIBS)
