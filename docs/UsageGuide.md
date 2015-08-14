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

## View Available Packages

Once the IUS repository is enabled, you can use one of these commands to list
all packages in the repository.

```bash
# EL5/6
yum --disablerepo=* --enablerepo=ius list available
# EL7
yum repository-packages ius list available
# future
dnf repository-packages ius list available
```

You can view the packages in the testing, development, or archive repositories
by using the corresponding repoid, such as "ius-testing".

You can also look through our [repoview directories][5] in a web browser.

## Installing IUS Packages

There are multiple ways to install IUS packages.  The best method will depend
on the type of package and whether or not the stock equivalent is already
installed.

### Safe Replacement Packages

[Safe replacement packages][2] completely replace their stock equivalents, and
cannot be installed at the same time.  If the stock equivalent of an IUS
package is not already installed, then you can just directly install the
desired package.

<script type="text/javascript" src="https://asciinema.org/a/24585.js" id="asciicast-24585" async></script>

If the stock/EPEL equvalent of an IUS package is already installed, you must
uninstall it first.  If other packages depend on your installed stock package,
you may need to perform the removal and installation in a single transaction.
The native yum way to do this is via [yum shell][7].

<script type="text/javascript" src="https://asciinema.org/a/24507.js" id="asciicast-24507" async></script>

IUS also maintains the [yum replace plugin][6] to simplify the process.

<script type="text/javascript" src="https://asciinema.org/a/24503.js" id="asciicast-24503" async></script>

There is another option in the new [dnf][8] package manager.  The flag
`--allowerasing` allows you erase conflicting packages in the same transaction.

_Note: Dnf is not yet available in base RHEL, but has been backported to EPEL 7._

<script type="text/javascript" src="https://asciinema.org/a/24559.js" id="asciicast-24559" async></script>

### Parallel Installable Packages

[Parallel packages][3] are specifically designed to coexist with their stock
equivalent.  This means that they can be directly installed just like any other
package.

<script type="text/javascript" src="https://asciinema.org/a/25049.js" id="asciicast-25049" async></script>

## Downgrading from IUS Packages to Stock RHEL Packages

Please note that downgrading using the yum 'replace' plugin is slightly
experimental, and may not work for all package sets. If you have issues,
please use the old way.

Downgrading is really the same process but backwards. The 'replace' plugin for
yum also works for downgrading (but will produce many more missing providers)::

    [root@linuxbox ~]# yum replace php53 --replace-with php
    Loaded plugins: replace
    Excluding Packages in global exclude list
    Finished
    Replacing packages takes time, please be patient...
    
    WARNING: Unable to resolve all providers: ['php53-cgi', 'php53-pcntl', 'php53-readline', 'php53-cli', 'config(php53-common)', 'curl.so()(64bit)', 'fileinfo.so()(64bit)', 'json.so()(64bit)', 'phar.so()(64bit)', 'php(api)', 'php(zend-abi)', 'php-json', 'php-pecl(Fileinfo)', 'php-pecl(json)', 'php-pecl(phar)', 'php-pecl(zip)', 'php-pecl-Fileinfo', 'php-pecl-json', 'php-pecl-phar', 'php-pecl-zip', 'php-zip', 'php53(api)', 'php53(zend-abi)', 'php53-api', 'php53-bz2', 'php53-calendar', 'php53-ctype', 'php53-curl', 'php53-date', 'php53-exif', 'php53-ftp', 'php53-gettext', 'php53-gmp', 'php53-hash', 'php53-iconv', 'php53-json', 'php53-libxml', 'php53-openssl', 'php53-pcre', 'php53-pecl(Fileinfo)', 'php53-pecl(json)', 'php53-pecl(phar)', 'php53-pecl(zip)', 'php53-pecl-Fileinfo', 'php53-pecl-json', 'php53-pecl-phar', 'php53-pecl-zip', 'php53-posix', 'php53-reflection', 'php53-session', 'php53-shmop', 'php53-simplexml', 'php53-sockets', 'php53-spl', 'php53-sysvmsg', 'php53-sysvsem', 'php53-sysvshm', 'php53-tokenizer', 'php53-wddx', 'php53-zend-abi', 'php53-zip', 'php53-zlib', 'zip.so()(64bit)', 'php53-common', 'config(php53-devel)', 'php53-devel', 'config(php53-pspell)', 'pspell.so()(64bit)', 'php53-pspell']
    
    This may be normal depending on the package.  Continue? [y/N] y
    
    
    Removed:
      php53.x86_64 0:5.3.2-6.ius.el5                   php53-cli.x86_64 0:5.3.2-6.ius.el5              
      php53-common.x86_64 0:5.3.2-6.ius.el5            php53-devel.x86_64 0:5.3.2-6.ius.el5            
      php53-pear.noarch 1:1.8.1-4.ius.el5              php53-pspell.x86_64 0:5.3.2-6.ius.el5           
    
    Installed:
      php.x86_64 0:5.1.6-27.el5        php-cli.x86_64 0:5.1.6-27.el5  php-common.x86_64 0:5.1.6-27.el5 
      php-devel.x86_64 0:5.1.6-27.el5  php-pear.noarch 1:1.4.9-6.el5 
    
    Complete!
    
And of course we once again have stock PHP for EL5::

    [root@el5-i386 ~]# php -v
    PHP 5.1.6 (cli) (built: Feb 26 2009 07:01:10) 
    Copyright (c) 1997-2006 The PHP Group
    Zend Engine v2.1.0, Copyright (c) 1998-2006 Zend Technologies
    
## Known Yum Dependency Resolution Issues

The IUS CoreDev Team is aware of an issue with the previous versions of Yum and
how it resolves dependencies when installing packages. For background on this
matter please see the upstream bug reports that we have submitted:

* [LaunchPad IUS Bug #453543][6]
* [Yum Bug #296][7]
* [Red Hat Bug #529719][8]

As of Yum 3.2.26 (backported: 3.2.22-23) this is no longer a problem.

We had previously implemented an optional and temporary workaround by
backporting the original patch that we submitted to a yum3 package in the IUS
EL 5 repositories. If you had used this yum3 package, please revert to the
stock version of yum in RHEL 5.5/6.0::

    # yum install yum-utils
    
    # yumdownloader yum
    
    # rpm -e --nodeps yum3
    
    # rpm -Uvh yum-*.rpm

[0]: FAQs.md
[1]: https://dl.iuscommunity.org/pub/ius/IUS-COMMUNITY-EUA
[2]: SafeRepo.md#safe-replacement-package
[3]: SafeRepo.md#parallel-installable-package
[4]: GettingStarted.md
[5]: Packages.md
[6]: https://github.com/iuscommunity/yum-plugin-replace
[7]: http://man7.org/linux/man-pages/man8/yum-shell.8.html
[8]: https://dnf.readthedocs.org
[9]: https://bugs.launchpad.net/ius/+bug/453543
[10]: http://web.archive.org/web/20120114083114/http://yum.baseurl.org/ticket/296
[11]: https://bugzilla.redhat.com/show_bug.cgi?id=529719

