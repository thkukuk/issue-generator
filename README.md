# issue-generator
Generate a volatile and temporary /run/issue file based on the input files
from different locations as specified in issue.d(5).

## How does this work?
The script can be run on the commandline, as systemd service or as
udev rule.

If invoked with no arguments, it applies all input files and creates a
temporary issue file as /run/issue.  /etc/issue should be symlink to
this file.

Input files could be located in /usr/lib/issue.d, /run/issue.d and
/etc/issue.d. Files in /etc/issue.d override files with the same name in
/usr/lib/issue.d and /run/issue.d. Files in /run/issue.d override files
with the same name in /usr/lib/issue.d. Packages should install their
configuration files in /usr/lib/issue.d. Files in /etc/issue.d are
reserved for the local administrator, who may use this logic to
override the files installed by vendor packages. All configuration
files are sorted by their filename in lexicographic order, regardless
of which of the directories they reside in.

issue-generator has two additional options used by udev rules and systemd
service files: network and ssh. The first one will create an issue snippet,
which displays the IPv4 and IPv6 address of an ethernet interface. The second
option will create an issue snippet, which displays the fingerprints of all
public ssh keys of that host.

To always build a /run/issue file, issue-generator.service needs to be
enabled. issue-add-ssh-keys.service needs to be enabled, if the fingerprint of
the public ssh keys of that machine should be shown. A udev rule will always
generate or remove a snippet, if a network interface is added or removed.

## Caveats
* The udev rule to add/remove the network interface should be configureable.
