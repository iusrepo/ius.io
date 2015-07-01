# Getting Started

## End User Agreement

Before using any packages from the IUS Community repositories, you should first
read our [End User Agreement][1].  Downloading, installing, or using our
packages implies that you agree to these terms.

## Usage Warning

If you are new to IUS, please understand that our packages work a bit
differently than you might expect.  If you are trying to directly upgrade from
a stock package to an IUS package, it will probably fail.  Please see our
[Usage Guide][2] for specific details.

## Subscribing to the IUS Repository

Release RPMs are the preferred method of subscribing to an RPM repository
because they contains all the necessary configuration and key files to access
the repository.

To subscribe a system to the IUS repository, you need to install the
ius-release RPM.  Please note that ius-release depends on epel-release, because
several IUS packages have dependencies from EPEL.

## Scripted Install

A short bash script is available at [setup.ius.io][3] that automatically
handles installation of both epel-release and ius-release.

## Manual Install

### epel-release

If you are using CentOS, you can skip this step.  The epel-release package is
available from the CentOS Extras repository (enabled by default) and will be
pulled in as a dependency of ius-release automatically.

RHEL users must follow the [EPEL documentation][4] and use one of the following
links to get the correct release package.

* [https://dl.fedoraproject.org/pub/epel/epel-release-latest-5.noarch.rpm][5]
* [https://dl.fedoraproject.org/pub/epel/epel-release-latest-6.noarch.rpm][6]
* [https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm][7]

### ius-release

IUS compiles seperate packages for RHEL and CentOS.  Use one of the following
links to get the correct release package.

* [https://rhel5.iuscommunity.org/ius-release.rpm][8]
* [https://rhel6.iuscommunity.org/ius-release.rpm][9]
* [https://rhel7.iuscommunity.org/ius-release.rpm][10]
* [https://centos5.iuscommunity.org/ius-release.rpm][11]
* [https://centos6.iuscommunity.org/ius-release.rpm][12]
* [https://centos7.iuscommunity.org/ius-release.rpm][13]

[1]: https://dl.iuscommunity.org/pub/ius/IUS-COMMUNITY-EUA
[2]: Usage_Guide.md
[3]: http://setup.ius.io
[4]: https://fedoraproject.org/wiki/EPEL#How_can_I_use_these_extra_packages.3F
[5]: https://dl.fedoraproject.org/pub/epel/epel-release-latest-5.noarch.rpm
[6]: https://dl.fedoraproject.org/pub/epel/epel-release-latest-6.noarch.rpm
[7]: https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
[8]: https://rhel5.iuscommunity.org/ius-release.rpm
[9]: https://rhel6.iuscommunity.org/ius-release.rpm
[10]: https://rhel7.iuscommunity.org/ius-release.rpm
[11]: https://centos5.iuscommunity.org/ius-release.rpm
[12]: https://centos6.iuscommunity.org/ius-release.rpm
[13]: https://centos7.iuscommunity.org/ius-release.rpm

