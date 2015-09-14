# Life Cycle

## Distibution Life Cycle

IUS only supports the current base release for Red Hat Enterprise Linux and
CentOS.  Older point releases and other distributions based on RHEL may work,
but with limited resource we focus efforts on our supported OSes.

## Package Life Cycle

RHEL has a [10 year life cycle][1], during which time stock packages recieve
[backported][2] security fixes.  These packages usually stay locked to a
particular upstream version, regardless of whether that version is still
supported by the upstream project.

On the other hand, IUS packages follow their respective upstream version.  This
is usually isoloated to a supported upstream branch (usually the major.minor
version).  This makes it unnecessary to backport security fixes, since the
latest upstream version typically contains fixes for all known vulnerabilities.
Once the upstream project declares a version end of life (EOL), IUS moves the
relevant packages from our stable repositories to our archive repositories.

It is important to note that IUS packages will not automatically upgrade to the
next major version.  Upgrading from foobar25u to foobar26u is a manual process,
similar to upgrading from stock foobar.  Even when foobar 2.5 is declared EOL
upstream, no automatic upgrade to foobar26u will take place.

## Upstream Policies and EOL Dates

Below is information we have collected regarding various upstream projects EOL
policies and relevant dates.  Not all projects have clear policies, so the
level of detail varies between projects.  Please contact us with corrections or
additions.

### PHP

* http://php.net/supported-versions.php
* http://php.net/eol.php
* https://wiki.php.net/rfc/releaseprocess
* http://en.wikipedia.org/wiki/PHP#Release_history
* 5.3 - [2014-08-14](http://php.net/archive/2014.php#id2014-08-14-1)
* 5.4 - 2015-09-14
* 5.5 - 2016-06-20
* 5.6 - 2017-08-28

### MySQL

* http://www.mysql.com/support/
* http://www.mysql.com/support/supportedplatforms/database.html
* http://en.wikipedia.org/wiki/MySQL#Versions
* 5.0 - [2012-03-21](http://dev.mysql.com/doc/relnotes/mysql/5.0/en/news-5-0-96.html)
* 5.1 - [TBD](http://dev.mysql.com/doc/relnotes/mysql/5.1/en/)
* 5.5 - [TBD](http://dev.mysql.com/doc/relnotes/mysql/5.5/en/)
* 5.6 - [TBD](http://dev.mysql.com/doc/relnotes/mysql/5.6/en/)

### MariaDB

[maintenance policy](https://mariadb.com/kb/en/mariadb/mariadb-maintenance-policy/)

### Python

[dev cycle](https://docs.python.org/devguide/devcycle.html)

* 2.6 - 2013-10-29
    * [pep-0361](https://www.python.org/dev/peps/pep-0361/)
    * last release: [2.6.9](https://www.python.org/download/releases/2.6.9/)
* 2.7 - 2020-??-??
    * [extended from 5 to 10 years](https://hg.python.org/peps/rev/76d43e52d978)
    * [pep-0373](https://www.python.org/dev/peps/pep-0373/)
    * last release: [2.7.10](https://www.python.org/downloads/release/python-2710/) (not final)
* 3.0 - 2009-06-27
    * [pep-0361](https://www.python.org/dev/peps/pep-0361/)
    * last release: [3.0.1](https://www.python.org/download/releases/3.0.1/)
* 3.1 - 2012-06-27
    * [pep-0375](https://www.python.org/dev/peps/pep-0375/)
    * last release: [3.1.5](https://www.python.org/downloads/release/python-315/)
* 3.2 - 2016-02-20
    * [pep-0392](https://www.python.org/dev/peps/pep-0392/)
    * last release: [3.2.6](https://www.python.org/downloads/release/python-326/) (not final)
* 3.3 - 2017-09-29
    * [pep-0398](https://www.python.org/dev/peps/pep-0398/)
    * last release: [3.3.6](https://www.python.org/downloads/release/python-336/) (not final)
* 3.4 - TBD
    * [pep-0429](https://www.python.org/dev/peps/pep-0429/)
    * last release: [3.4.3](https://www.python.org/downloads/release/python-343/) (not final)

### Redis

The last two [releases](http://redis.io/download) of redis should get all security fixes.  Still looking for a documented policy on this.

* 2.6 - [2015-04-01](https://github.com/antirez/redis/blob/7ae1d4d6f50fa627a32eee261743d41d64a13e96/00-RELEASENOTES#L36) (redis 3.0.0 release date)
* 2.8 - TBD (redis 3.2.0 release date)
* 3.0 - TBD (redis 3.4.0 release date)

[1]: https://access.redhat.com/support/policy/updates/errata/
[2]: https://access.redhat.com/security/updates/backporting
