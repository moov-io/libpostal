CFLAGS_BASE = -Wfloat-equal -Wpointer-arith -std=gnu99 -DLIBPOSTAL_DATA_DIR='"$(datadir)/libpostal"' -g
CFLAGS_O0 = $(CFLAGS_BASE) -O0
CFLAGS_O1 = $(CFLAGS_BASE) -O1
CFLAGS_O2 = $(CFLAGS_BASE) -O2
CFLAGS_O3 = $(CFLAGS_BASE) -O3
DEFAULT_INCLUDES = -I.. -I/usr/local/include

CFLAGS = $(CFLAGS_BASE)

TESTS = test_libpostal
noinst_PROGRAMS = test_libpostal test_threading
test_libpostal_SOURCES = test.c test_expand.c test_parser.c test_transliterate.c test_numex.c test_trie.c test_string_utils.c test_crf_context.c ../src/strndup.c ../src/file_utils.c ../src/string_utils.c ../src/utf8proc/utf8proc.c ../src/trie.c ../src/trie_search.c ../src/transliterate.c ../src/numex.c ../src/features.c
test_libpostal_LDADD = ../src/libpostal.la ../src/libscanner.la $(CBLAS_LIBS)
test_libpostal_CFLAGS = $(CFLAGS_O3)

# Threading stress test for concurrent access (the main goal of removing
# global mutable state that forced single-threaded use).
test_threading_SOURCES = test_threading.c ../src/strndup.c
test_threading_LDADD = ../src/libpostal.la $(PTHREAD_LIBS)
test_threading_CFLAGS = $(CFLAGS_O3) -I../src
