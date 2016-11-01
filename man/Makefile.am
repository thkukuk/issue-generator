#
# Copyright (c) 2016 Thorsten Kukuk, Germany
#
# Author: Thorsten Kukuk <kukuk@suse.de>
#

CLEANFILES = issue.d.5 issue-generator.8

EXTRA_DIST = $(MANS) $(XMLS)

man_MANS = issue.d.5 issue-generator.8 issue-generator.service.8 \
	issue-add-ssh-keys.service.8 90-issue-generator.rules.8 \
	issue-generator.conf.8
XMLS = issue.d.5.xml issue-generator.8.xml

if ENABLE_REGENERATE_MAN
issue.d.5: issue.d.5.xml
	$(XMLLINT) --nonet --xinclude --postvalid --noout $<
	$(XSLTPROC) -o $(srcdir)/$@ --path $(srcdir) --xinclude --nonet http://docbook.sourceforge.net/release/xsl/current/manpages/docbook.xsl $<

issue-generator.8: issue-generator.8.xml
	$(XMLLINT) --nonet --xinclude --postvalid --noout $<
	$(XSLTPROC) -o $(srcdir)/$@ --path $(srcdir) --xinclude --nonet http://docbook.sourceforge.net/release/xsl/current/manpages/docbook.xsl $<
endif
