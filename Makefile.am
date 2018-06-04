#
# Copyright (c) 2016,2018 Thorsten Kukuk, Germany
#
# Author: Thorsten Kukuk <kukuk@suse.de>
#
AUTOMAKE_OPTIONS = 1.6 foreign check-news dist-xz
#
SUBDIRS = sbin man udev systemd tmpfiles.d tests

CLEANFILES = *~

M4_FILES = m4/jh_path_xml_catalog.m4

EXTRA_DIST = ChangeLog $(M4_FILES) README.md

ACLOCAL_AMFLAGS = -I m4

install-data-local:
	$(mkinstalldirs) $(DESTDIR)$(ISSUEDIR)
	$(mkinstalldirs) $(DESTDIR)${sysconfdir}/issue.d
 
