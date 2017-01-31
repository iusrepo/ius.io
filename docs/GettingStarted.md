# Getting Started

## Disclaimers

Before using any packages from the IUS Community repositories, you should first
read our [End User Agreement][EUA].  Downloading, installing, or using our
packages implies that you agree to these terms.

If you are new to IUS, please understand that our packages work a bit
differently than you might expect.  Please see our [usage guide][usage] for
specific details.

## Subscribing to the IUS Repository

Release RPMs are the preferred method of subscribing to an RPM repository
because they contains all the necessary configuration and key files to access
the repository.

To subscribe a system to the IUS repository, you need to install the
ius-release RPM.  Please note that ius-release depends on epel-release, because
several IUS packages have dependencies from EPEL.

## Install via Automation

Automation examples are available at the [automation-examples github
repository][automation].  We also have the bash script from that repository
available at [setup.ius.io][setup].

## Manual Install

### epel-release

If you are using CentOS, you can skip this step.  The epel-release package is
available from the CentOS Extras repository (enabled by default) and will be
pulled in as a dependency of ius-release automatically.

RHEL users must follow the [EPEL documentation][EPEL_dcos] and use one of the
following links to get the correct release package.

* [https://dl.fedoraproject.org/pub/epel/epel-release-latest-6.noarch.rpm][EPEL6]
* [https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm][EPEL7]

### ius-release

IUS compiles seperate packages for RHEL and CentOS.  Use one of the following
links to get the correct release package.

* [https://rhel6.iuscommunity.org/ius-release.rpm][IUS_RHEL6]
* [https://rhel7.iuscommunity.org/ius-release.rpm][IUS_RHEL7]
* [https://centos6.iuscommunity.org/ius-release.rpm][IUS_CentOS6]
* [https://centos7.iuscommunity.org/ius-release.rpm][IUS_CentOS7]

[EUA]: https://dl.iuscommunity.org/pub/ius/IUS-COMMUNITY-EUA
[usage]: Usage.md
[automation]: https://github.com/iuscommunity/automation-examples
[setup]: https://setup.ius.io/
[EPEL_docs]: https://fedoraproject.org/wiki/EPEL#How_can_I_use_these_extra_packages.3F
[EPEL6]: https://dl.fedoraproject.org/pub/epel/epel-release-latest-6.noarch.rpm
[EPEL7]: https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
[IUS_RHEL6]: https://rhel6.iuscommunity.org/ius-release.rpm
[IUS_RHEL7]: https://rhel7.iuscommunity.org/ius-release.rpm
[IUS_CentOS6]: https://centos6.iuscommunity.org/ius-release.rpm
[IUS_CentOS7]: https://centos7.iuscommunity.org/ius-release.rpm
