# IUS vs. Software Collections

## Introduction

In 2013, Red Hat released a product called [Software Collections][1] (RHSCL).
This product later got it's own [community website][2].  The front page has
this statement:

> Software Collections give you power to build, install, and use multiple
> versions of software on the same system, without affecting system-wide
> installed packages.

Here is our mission statement for the IUS Community project:

> IUS is a community project that provides RPM packages for newer versions of
> select software for Enterprise Linux distributions.

Both projects seek to solve the same problem, but differ greatly in execution.

## Types of Packages

* IUS provides [Safe Replacement Packages][3] and [Parallel Installable
Packages][4].
* SCL provides a unique kind of [Parallel Installable Packages][4].

## File Locations

* Files from IUS packages are installed to similar locations as stock packages,
such as `/usr/bin`, `/usr/lib`, `/etc`, `/var`, and so on.
* Files from SCL packages are installed under `/opt`, `/etc/opt`, and
`/var/opt`.

## Usage

* Usage of IUS packages are the same or very close to stock packages.

```bash
php -v
service mysqld start
mysql -V
python2.7 -V
```

* Usage of SCL packages are very different from stock packages.

```bash
scl enable php54 "php -v"
service mysql55-mysqld start
scl enable mysql55 "mysql -V"
scl enable python27 "python -V"
```

## Releases

* IUS packages are updated in line with the upstream software project.  This
means that once upstream releases a new version of the corresponding release
branch, we will begin building RPMs as soon as possible.  It also means that
once software is declared "End of Life" (EOL) by the upstream project, we
remove it from our stable repositories.

* The [Product Life Cycle][5] for Red Hat Software Collections (RHSCL) states
that "Production Collections" are supported with security updates for three
years.  Major updates are grouped together and released as a new collection.

* Software Collections from [softwarecollections.org][6] are community driven
and have no guarantees.  Please see this [mailing list post][7].

## SCL in base repositories

Generally, users have to go out of their way to use SCL packages. Subscribing
to a RHSCL channel or installing the centos-release-scl package are needed to
access SCL packages. An exception occurred when Red Hat released [MySQL SCL
packages into the 5.10 base channel][8]. While this appears to be an isolated
case, it important to note this occurred and it is not clear if Red Hat will do
this again. For IUS users, this created confusion as there was a mysql55
package in both the base channel and IUS repository.

## More Info

* [Community Software Collections Homepage][9]
* [RHSCL 1.0 Beta Announcement][10]
* [RHSCL 1.0 General Availability Announcement][11]
* [RHSCL Guide][12]
* [RHSCL Update Policy][13]

[1]: https://www.redhat.com/en/about/press-releases/red-hat-extends-red-hat-enterprise-linux-platform-with-latest-versions-of-popular-programming-languages-and-databases
[2]: https://developerblog.redhat.com/2014/04/08/announcing-softwarecollections-org/
[3]: SafeRepo.md#safe-replacement-package
[4]: SafeRepo.md#parallel-installable-package
[5]: https://access.redhat.com/support/policy/updates/rhscl/
[6]: https://www.softwarecollections.org
[7]: https://www.redhat.com/archives/sclorg/2014-November/msg00005.html
[8]: https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/5/html/5.10_Release_Notes/general_updates.html
[9]: https://www.softwarecollections.org
[10]: https://www.redhat.com/about/news/archive/2013/6/red-hat-software-collections-1.0-beta-now-available
[11]: https://developerblog.redhat.com/2013/09/12/rhscl1-ga/
[12]: https://access.redhat.com/site/documentation/en-US/Red_Hat_Developer_Toolset/1/html/Software_Collections_Guide/
[13]: https://access.redhat.com/support/policy/updates/rhscl/
