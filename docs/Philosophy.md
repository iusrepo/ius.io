# Philosophy

## Overview

Stock Enterprise Linux packages can get pretty far out of date compared to
their respective upstream projects.  While Red Hat [backports][1] security
fixes, new features are rarely added.  This approach results in a very stable
overall operating system, but can be frustrating to users when a new upstream
feature is needed.

IUS stands for **I**nline with **U**pstream **S**table.  Our packages are
fundamentally different from their stock counterparts.  Our packages track the
latest upstream versions of their respective software.  There is an inherent
risk with this approach; new upstream versions may introduce bugs that users of
stock packages will never have to deal with.  That said, we stand behind the
quality of our packages, and work hard to find and resolve issues before a
packages are promoted to the stable repos.  IUS users are forfeiting a small
part of the their system stability in order to get the new features they need.
By using IUS packages, you implicitly agree to this trade off.  This risk can
be largely mitigated by participating in [early testing][2] using a
non-production environment.

## Don't Overwrite Stock Packages

IUS provides only [safe replacement][3] and [parallel installable][4] packages.
Because of this, users can subscribe to IUS with no surprises; IUS packages
will never overwrite stock packages.  Only explictly chosen packages will be
installed.  You can enjoy the stability of Enterprise Linux for the majority of
the system but still utilize the latest PHP, Python, MySQL, and more.

## Release Policy

Updates for our existing packages are first released in the [testing
repositories][5].  If no issues are reported after about two weeks, the updated
packages will be promoted to the [stable repositories][6].  In some cases, such
as critical security fixes, we will promote packages to the stable repositories
sooner than two weeks.

This release policy does not not apply to new packages that have yet to be
added to the stable repositories.  When a new package is requested, the
requester must agree to test the package.  Once the requester confirms that
everything works as expected, the package is eligible to be added to the stable
repositories.

## Naming Convention

IUS packages are typically named in the following format.

    {name}{major_version}{minor_version}u

A similar format can be seen with some EPEL packages such as python34 and
zabbix22.  Using alternative names from stock packages has several benefits.

* It ensures that the stock equivalent will never be overwritten with the
  alternative version during a normal system update.
* Users can subscribe to the entire IUS repository, but only use some of our
  packages.  Other repositories that use the same names as stock packages do
  not give users that flexibility.
* It allows us to offer multiple branches of an application in the same
  repository.
* It allows for greater clarity when using multiple third party repositories.
  For example, EPEL has multiple php pecl module packages that are built
  against stock php.  If you add another repository that ships a newer version
  of the php package with the same name, the EPEL php pecl module packages will
  not work with it.  It would be difficult to quickly determine which php
  packages work correctly with each other.

The only drawback to this naming format is that you can't directly upgrade from
stock packages to IUS packages.  Considering all the factors, we feel that the
benefits far outweigh this inconvenience.

In addition to appending the major and minor version numbers, most IUS packages
also have a "u" suffix.  We started using that suffix in 2010 when Red Hat
announced that [RHEL 5.6 would be adding a package named php53 to the base
repositories][7].  This conflicted with our existing php53 package, so we knew
we had to [make a change][8].  David Strauss [suggested on our mailing list][9]
that we add a "u" suffix to prevent the name conflict.  We liked the idea, and
[proceeded with implementing it][10].  At the time, [we thought it would be a
one-time fix][11].  In 2013, Red Hat released a product called [Software
Collections][2] (RHSCL).  Some of the packages that were offered overlapped
with IUS packages.  We were concerned that we would face more package name
conflicts, but were relieved to hear that RHSCL would not be enabled by
default.  However, Red Hat later decided to add the mysql55 SCL packages to the
base RHEL 5 repository.  The SCL metapackage mysql55 had the same name as our
existing mysql55 package.  We evaluated renaming our mysql55 package to
mysql55u to avoid the name conflict, but we were not able to find a solution
that provided seamless upgrades.  Since then, we have decided to add the "u"
suffix to all our new packages to keep from getting in the same situation
again.

[1]: https://access.redhat.com/security/updates/backporting
[2]: Contributing.md#early-testing
[3]: SafeRepo.md#safe-replacement-package
[4]: SafeRepo.md#parallel-installable-package
[5]: https://dl.iuscommunity.org/pub/ius/testing/
[6]: https://dl.iuscommunity.org/pub/ius/stable/
[7]: https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/5/html-single/5.6_Release_Notes/#idp12335856
[8]: https://lists.launchpad.net/ius-community/msg00145.html
[9]: https://lists.launchpad.net/ius-community/msg00151.html
[10]: https://bugs.launchpad.net/ius/+bug/691755
[11]: https://lists.launchpad.net/ius-community/msg00152.html
