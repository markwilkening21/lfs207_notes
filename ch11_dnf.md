# Chapter 11 - DNF and yum

dnf utilizes more high level tools compared to rpm. It is a front end to RPM, but can also retrieve packages from
remote repositories. A great feature is its' abilities to resolve dependencies. The config files are found at:

**/etc/yum.repos.d** and have a *repos* extension.

## yum

dnf replaced yum during the RHEL/centOS 7 to 8 transition. Fedora has used yum much longer. If you try to 
run yum, some versions of dnf will alert you that these are depracated. dnf is backwards compatible.

## Queries

To search for a package with keyword in it, run:

**$ dnf search keyword**

To display information about a package, run:

**$ dnf info package-name**

To list packages installed, available, or updates, run:

**$ dnf list [installed | updates | available ]**

To show information about package groups installed, available and updates, run:

**$ dnf grouplist**

To show information about a package group:

**$ dnf groupinfo packagegroup**

To show the owner of the package for file:

**$ dnf provides /path/to/file**

Please note the need to use at least one / in the file name, which can be confusing.

## Installing/Removing/Upgrading Packages

Install a package from a repository; also resolve and install dependencies:

**$ sudo dnf install package**

Install a package from a local rpm file:

**$ sudo dnf localinstall package-file**

Install a specific software group from a repository; also resolve and install dependencies for each package in the group:

**$ sudo dnf groupinstall 'group-name'**

Remove a package from the system:

**$ sudo dnf remove package**

Update a package from a repository (if no package is listed, update all packages):

**$ sudo dnf update [package]**

During installation (or update), if a package has a configuration file which is updated, it will rename the old configuration file with a .rpmsave extension. 
If the old configuration file will still work with the new software, it will name the new configuration file with a .rpmnew extension. 
You can search for these filename extensions to see if you need to do any reconciliation of the files.

## Additional dnf Commands

Lists additional dnf plugins:

**$ sudo dnf list "dnf-plugin*"**

Shows a list of enabled repositories:

**$ sudo dnf repolist**

Provides an interactive shell in which to run multiple dnf commands (the second form executes the commands in file.txt):

**$ sudo dnf shell**

**$ sudo dnf shell file.txt**

Downloads the packages for you (it stores them in the /var/cache/dnf directory):

**$ sudo dnf install --downloadonly package**

Views the history of dnf commands on the system, and with the correction options, even undoes or redoes previous commands:

**$ sudo dnf history**

Cleans up locally stored files and metadata under /var/cache/dnf. This saves space and does house cleaning of obsolete data:

**$ sudo dnf clean [packages|metadata|expire-cache|rpmdb|plugins|all]**
