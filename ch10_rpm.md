# Chapter 10 - RPM

- RPM is a Package Management Utility for Red Hat. It originally stood for Redhat Package Manager.
- All files related to a specific task or subsystem are packaged into a single file, which also contains information about how and where to install and uninstall the files. 
- When developers create a new version of a program, they usually release a new RPM package.

![Caution RPM](img/0qjum14sc41v-Chap06-Caution-RPM.png)

The standard naming format for a binary RPM package is:

*<name>-<version>-<release>.<distro>.<architecture>.rpm
sed-4.5-2.e18.x86_64.rpm*

The standard naming format for a source RPM package is:

*<name>-<version>-<release>.<distro>.src.rpm
sed-4.5-2.e18.src.rpm*

Note that the distro field often actually specifies the repository that the package came from, as a given installation may use a number of different package repositories, 
as we shall see when we discuss dnf, yum and zypper which work at a level above RPM.

The default system directory which holds the RPM database files is */var/lib/rpm*, but these files should never be modified. They should updated using the rpm program.

You can use the --rebuilddb option to rebuild the database indices from the installed package headers; this is more of a repair, and not a rebuild from scratch.

*$ sudo rpm --rebuilddb*

## Queries

- -f: allows you to determine which package a file came from
- -l: lists the contents of a specific package
- -a: all the packages installed on the system
- -i: information about the package
- -p: run the query against a package file instead of the package database

| Task           |         Command |
|----------------|-------------------------|
| Which version of a package is installed?                                            | *$ rpm -q bash*                     |
| Which package did this file come from?                                              | *$ rpm -qf /bin/bash*               |
| What files were installed by this package?                                          | *$ rpm -ql bash*                    |
| Show information about this package                                                 | *$ rpm -qi bash*                    |
| Show information about this package from the package file, not the package database | *$ rpm -qip foo-1.0.0-1.noarch.rpm* | 
| List all installed packages on this sytem                                           | *$ rpm -qa*                         |
