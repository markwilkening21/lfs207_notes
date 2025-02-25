---
layout: default
title: Chapter 9 - APT
---

##Chapter 9 – APT##

Queries are done using the apt-cache or apt-file utilities. You may have to install apt-file first, and update its database, as in:

**$ sudo apt-get install apt-file
$ sudo apt-file update**

To search the repository for a package named apache2:

**$ apt-cache search apache2**

To display basic information about the apache2 package:

**$ apt-cache show apache2**

To display detailed information about the apache2 package:

**$ apt-cache showpkg apache2**

List all dependent packages for apache2:

**$ apt-cache depends apache2**

Search the repository for a file named apache2.conf:

**$ apt-file search apache2.conf**

List all files in the apache2 package:

**$ apt-file list apache2**

Used to install new packages or update a package which is already installed: 

**$ sudo apt install [package]**

Used to remove a package from the system. This does not remove the configuration files: 

**$ sudo apt remove [package]**

Used to remove a package and its configuration files from a system: 

**$ sudo apt --purge remove [package]**

Used to synchronize the package index files with their sources. The indexes of available packages are fetched from the location(s) specified in /etc/apt/sources.list:

**$ sudo apt update**

upgrade is used to apply all available updates to packages already installed; dist-upgrade will not update to a whole new distribution version as is commonly misunderstood:

**$ sudo apt upgrade**

**$ sudo apt dist-upgrade**

Note that you must update before you upgrade, unlike with dnf or zypper, which can be confusing to habitual users of those utilities. Similarly, unlike with dnf or zypper, one never updates/upgrades individual packages; the entire package list is dealt with as a unit.

This command gets rid of any packages not needed anymore, such as older Linux kernel versions:

**$ sudo apt autoremove**

And this one cleans out cache files and any archived package files that have been installed:

**$ sudo apt clean**

All packages that contain a reference tobashin their name or description.

**$ apt-cache search bash**

Installed and available bash packages.

**$ apt-cache search -n bash**

The package information for bash

**$ apt-cache show bash**

The dependencies for the bash package

**$ apt-cache depends bash
$ apt-cache rdepends bash**
