# Chapter 12 - Zypper

zypper is the command line tool for installing and managing packages in SUSE Linux and openSUSE. It is very similar to dnf in its functionality and even in its basic command syntax, 
and also works with rpm packages.

For use on SUSE-based systems, the zypper program provides a higher level of intelligent services for using the underlying rpm program, and plays the same role as dnf/yum 
on Red Hat-based systems. It can automatically resolve dependencies when installing, updating, and removing packages. It accesses external software repositories, 
synchronizing with them and retrieving and installing software as needed.

## Queries
Shows a list of available updates:

**$ zypper list-updates**

Lists available repositories:

**$ zypper repos**

Searches repositories for string:

**$ zypper search <string>**

Lists information about a package:

**$ zypper info firefox**

Searches repositories to show what packages provide a file:

**$ zypper search --provides /usr/bin/firefox**
