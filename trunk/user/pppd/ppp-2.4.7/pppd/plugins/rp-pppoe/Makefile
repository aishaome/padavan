# Generated automatically from Makefile.in by configure.
#***********************************************************************
#
# Makefile
#
# Makefile for Roaring Penguin's Linux PPPoE plugin.
# Modified for integration with pppd sources by Paul Mackerras.
#
# Copyright (C) 2001 Roaring Penguin Software Inc.
#
# This program may be distributed according to the terms of the GNU
# General Public License, version 2 or (at your option) any later version.
#
# $Id$
#***********************************************************************

DESTDIR = $(INSTROOT)/usr
BINDIR = $(DESTDIR)/sbin
LIBDIR = $(DESTDIR)/lib/pppd/$(PPPDVERSION)

PPPDVERSION = $(shell awk -F '"' '/VERSION/ { print $$2; }' ../../patchlevel.h)

INSTALL	= install

# Version is set ONLY IN THE MAKEFILE!  Don't delete this!
RP_VERSION=3.12

COPTS=
CFLAGS+=$(COPTS) -I../../../include '-DRP_VERSION="$(RP_VERSION)"' -DPLUGIN=1
all: rp-pppoe.so

rp-pppoe.so: libplugin.a plugin.o
	$(LD) -o rp-pppoe.so -shared plugin.o libplugin.a

install: all
	$(INSTALL) -d -m 755 $(LIBDIR)
	$(INSTALL) -m 4550 rp-pppoe.so $(LIBDIR)

clean:
	rm -f *.o *.so *.a

plugin.o: plugin.c
	$(CC) $(CFLAGS) -I../../.. -c -o $@ -fPIC plugin.c

libplugin.a: discovery.o if.o common.o debug.o
	$(AR) -rc $@ $^

%.o: %.c
	$(CC) $(CFLAGS) -c -o $@ -fPIC $^
