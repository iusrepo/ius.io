# Usage Guide

## Summary

This document outlines the basic client usage of IUS. For common questions
regarding IUS please see the [FAQs][0].  Legal stuff can be found in our [End
User Agreement][1].

## Package Categories

IUS packages will fall into two different categories.

* **Primary Packages**: IUS packages that are newer versions of applications or
languages that already exist in RHEL or EPEL.  Whenever possible, these
packages will be updated inline with a major upstream branch (usually the
major.minor version).  These packages represent the primary purpose of IUS, and
thus have the highest priority and focus.

* **Secondary Supporting Packages**: IUS packages that are required by or
extend the functionality of primary packages.  Common examples include PECL
modules for PHP and PyPI modules for Python.  Occasional we may also need a
newer version of a system library in order to compile a primary package
(although we try to compile against stock libraries whenever possible).
Supporting packages might not replace anything in RHEL or EPEL, but sometimes
do.  While primary packages follow major upstream branches, secondary packages
will typically only exist for the absolute latest upstream version.  There can
be multiple packages for the latest upstream version when the software must be
built against a specfic primary package, such as programming language
libraries.  Updates for secondary packages might not occur as often as primary
packages.

## Package Types

IUS packages will be one of two different types.

* [Safe Replacement Packages][2]
* [Parallel Installable Packages][3]

## Configuration

Configuration steps can be found in our [getting started guide][4].

## Installing IUS Packages

There are multiple ways to install IUS packages.  The best method will depend
on the type of package and whether or not the stock equivalent is already
installed.

### Safe Replacement Packages

[Safe replacement packages][2] completely replace their stock equivalents, and
cannot be installed at the same time.  If the stock equivalent of an IUS
package is not already installed, then you can just directly install the
desired package.

[asciinema demo][6]

```bash
yum install redis30u
```

If the stock/EPEL equvalent of an IUS package is already installed, you must
uninstall it first.  If other packages depend on your installed stock package,
you may need to perform the removal and installation in a single transaction.
The native yum way to do this is via [yum shell][7].

[asciinema demo][8]

```bash
yum shell
> erase mysql-libs
> install mysql56u mysql56u-libs mysql56u-server mysqlclient16
> run
```

IUS also maintains the [yum replace plugin][9] to simplify this process.  It is
available in our repositories.

[asciinema demo][10]

```bash
yum install yum-plugin-replace
yum replace php --replace-with php56u
```

There is another option in the new [dnf][11] package manager.  The flag
[`--allowerasing`][12] allows you erase conflicting packages in the same
transaction.

_Note: Dnf is not yet available in base RHEL, but has been backported to EPEL 7._

[asciinema demo][13]

```bash
dnf --allowerasing install git2u
```

### Parallel Installable Packages

[Parallel packages][3] are specifically designed to coexist with their stock
equivalent.  This means that they can be directly installed just like any other
package.

[asciinema demo][14]

```bash
yum install python34u
```

## Reverting To Stock Packages

If you want to switch from an IUS package back to the stock equivalent, you can
just reverse the process you used to install it.  For example, you can switch
the erase/install commands in yum shell, or change the order of package sets
specified to the replace plugin.

## Using Testing Repositories

New packages requests and package updates appear in the testing repositories
before graduating to the stable repositories.  While we do not recommend using
the testing repositories in production, there may be a time when you need use them.

[asciinema demo][15]
```bash
yum --enablerepo=ius-testing install php56u-pecl-uploadprogress
```


[0]: FAQs.md
[1]: https://dl.iuscommunity.org/pub/ius/IUS-COMMUNITY-EUA
[2]: SafeRepo.md#safe-replacement-package
[3]: SafeRepo.md#parallel-installable-package
[4]: GettingStarted.md
[5]: Packages.md
[6]: https://asciinema.org/a/24585
[7]: http://man7.org/linux/man-pages/man8/yum-shell.8.html
[8]: https://asciinema.org/a/24507
[9]: https://github.com/iuscommunity/yum-plugin-replace
[10]: https://asciinema.org/a/24503
[11]: https://dnf.readthedocs.org
[12]: https://dnf.readthedocs.org/en/latest/cli_vs_yum.html#packages-replacement-without-yum-shell-or-yum-swap
[13]: https://asciinema.org/a/24559
[14]: https://asciinema.org/a/24505
[15]: https://asciinema.org/a/a1dznemtxfczm4t8309i9kgi4

