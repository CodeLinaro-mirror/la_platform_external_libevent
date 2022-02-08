ACLOCAL_AMFLAGS := -I m4

AM_CFLAGS := -Wundef \
        -Wstrict-prototypes \
        -Wno-trigraphs \
        -g -O0 \
        $(LOCBASEUTIL_CFLAGS) \
        -fno-inline \
        -fno-short-enums \
        -fpic \
        -D_GNU_SOURCE \
        -DHAVE_CONFIG_H=1 \
        -DBUILD_DIVSUFSORT64 \
        -I../android_include \
        -I../include

AM_CPPFLAGS := \
        -I. \
        -D_FILE_OFFSET_BITS=64 \
        -I$(WORKSPACE)/OTA/streaming/external/libevent/include \
        -D_USE_RTTI_FOR_TYPE_TAGS \
        -DUSE_LE_MODE \
        -std=c++11

AUTOMAKE_OPTIONS = subdir-objects

AM_LDFLAGS := -shared -version-info 1:0:0


libevent_la_SOURCES :=  buffer.c \
        bufferevent.c \
        bufferevent_filter.c \
        bufferevent_pair.c \
        bufferevent_ratelim.c \
        bufferevent_sock.c \
        epoll.c \
        event.c \
        evmap.c \
        evthread.c \
        evutil.c \
        evutil_rand.c \
        listener.c \
        log.c \
        signal.c \
        strlcpy.c \
        evdns.c \
        event_tagging.c \
        evrpc.c \
        http.c \
        poll.c \
        select.c


library_includedir := $(pkgincludedir)

lib_LTLIBRARIES := libevent.la


if USE_GLIB
libevent_la_CFLAGS := $(AM_CFLAGS) -DUSE_GLIB @GLIB_CFLAGS@
libevent_la_CPPFLAGS := $(AM_CPPFLAGS) -DUSE_GLIB @GLIB_CFLAGS@
libevent_la_LIBADD := -lm -lpthread @GLIB_LIBS@
libevent_la_LDFLAGS = -shared
else
libevent_la_CFLAGS := $(AM_CFLAGS)
libevent_la_CPPFLAGS := $(AM_CPPFLAGS)
libevent_la_LIBADD := -lm -lpthread
libevent_la_LDFLAGS = -shared
endif


