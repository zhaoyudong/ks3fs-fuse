######################################################################
# s3fs - FUSE-based file system backed by Amazon S3
#
# Copyright 2007-2008 Randy Rizun <rrizun@gmail.com>
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.
######################################################################
bin_PROGRAMS=s3fs

AM_CPPFLAGS = $(DEPS_CFLAGS)
if USE_GNUTLS_NETTLE
  AM_CPPFLAGS += -DUSE_GNUTLS_NETTLE
endif

s3fs_SOURCES = s3fs.cpp s3fs.h curl.cpp curl.h cache.cpp cache.h string_util.cpp string_util.h s3fs_util.cpp s3fs_util.h fdcache.cpp fdcache.h common_auth.cpp s3fs_auth.h addhead.cpp addhead.h common.h log.cpp log.h
if USE_SSL_OPENSSL
  s3fs_SOURCES += openssl_auth.cpp
endif
if USE_SSL_GNUTLS
  s3fs_SOURCES += gnutls_auth.cpp
endif
if USE_SSL_NSS
  s3fs_SOURCES += nss_auth.cpp
endif

INCLUDES = -I../third-party/fuse-2.9.7/include -I../third-party/curl-7.50.3/include/ -I../third-party/openssl-1.0.1c/include/ -I../third-party/libxml2-2.7.6/include/ -I../third-party/zlib-1.2.11/include/
DEPS_LIBS = -lfuse -lrt -ldl -lxml2 -lcurl -lssl -lcrypto -lstdc++ -lidn -lz
s3fs_LDFLAGS = -pthread
s3fs_LDADD = -L../third-party/fuse-2.9.7/lib -L../third-party/curl-7.50.3/lib/ -L../third-party/gcc-4.8.4/lib -L../third-party/zlib-1.2.11/lib -L../third-party/openssl-1.0.1c/lib -L../third-party/libxml2-2.7.6/lib $(DEPS_LIBS)

noinst_PROGRAMS = test_string_util

test_string_util_SOURCES = string_util.cpp test_string_util.cpp test_util.h

TESTS = test_string_util
