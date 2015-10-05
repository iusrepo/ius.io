# Getting Started

## End User Agreement

Before using any packages from the IUS Community repositories, you should first
read our [End User Agreement][1].  Downloading, installing, or using our
packages implies that you agree to these terms.

## Usage Warning

If you are new to IUS, please understand that our packages work a bit
differently than you might expect.  If you are trying to directly upgrade from
a stock package to an IUS package, it will probably fail.  Please see our
[usage guide][2] for specific details.

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
yum commands to get the correct release package.


RHEL/CENTOS 5

```sh
yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-5.noarch.rpm
```

RHEL/CENTOS 6

```sh
yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-6.noarch.rpm
```

RHEL/CENTOS 7

```sh
yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
```


### ius-release

IUS compiles seperate packages for RHEL and CentOS.  Use one of the following
yum commands to get the correct release package.

RHEL 5

```sh
yum install https://rhel5.iuscommunity.org/ius-release.rpm
```

RHEL 6

```sh
yum install https://rhel6.iuscommunity.org/ius-release.rpm
```
RHEL 7

```sh
yum install https://rhel7.iuscommunity.org/ius-release.rpm
```

CENTOS 5

```sh
yum install https://centos5.iuscommunity.org/ius-release.rpm
```

CENTOS 6

```sh
yum install https://centos6.iuscommunity.org/ius-release.rpm
```

CENTOS 7

```sh
yum install https://centos7.iuscommunity.org/ius-release.rpm
```


[1]: https://dl.iuscommunity.org/pub/ius/IUS-COMMUNITY-EUA
[2]: Usage.md
[3]: http://setup.ius.io
[4]: https://fedoraproject.org/wiki/EPEL#How_can_I_use_these_extra_packages.3F
