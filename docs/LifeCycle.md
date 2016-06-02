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

* [Supported Versions Table][3]
* [EOL Versions Table][4]
* [Release Process][5]
* [Release History (Wikipedia)][6]
* 5.3 EOL date: [2014-08-14][7]
* 5.4 EOL date: [2015-09-14][8]
* 5.5 expected EOL date: 2016-07-10
* 5.6 expected EOL date: 2018-12-31
* 7.0 expected EOL date: 2018-12-03

### MySQL

* [Oracle Premier and Extended Support][9]
* [EOL Announcements][10]
* [Release History (Wikipedia)][11]
* 5.0 EOL date: [2012-01-09][mysql-eol]
* 5.1 EOL date: [2013-12-31][mysql-eol]
* 5.5 expected EOL date: [2018-12-03][14]
* 5.6 expected EOL date: [2021-02-05][15]

### MariaDB

* [Maintenance Policy][16]
* 10.0 expected EOL date: 2019-03-31
* 10.1 expected EOL date: 2020-10-17

### Python

* [Development Cycle][17]
* 2.6 EOL date: [2013-10-29][18]
* 2.7 expected EOL date: [2020-07-03][19]
* 3.0 EOL date: [2009-06-27][20]
* 3.1 EOL date: [2012-06-27][21]
* 3.2 expected EOL date: [2016-02-20][22]
* 3.3 expected EOL date: [2017-09-29][23]
* 3.4 expected EOL date: [2019-03-16][pep-0429]
* 3.5 expected EOL date: [2020-09-13][pep-0478]

### Redis

* [Redis releases][redis-downloads]
* 2.6 EOL date: [2015-04-01][redis-3.0.0] (redis 3.0.0 release date)
* 2.8 EOL date: [2016-05-06][redis-3.2.0] (redis 3.2.0 release date)
* 3.0 expected EOL date: TBD (redis 3.4.0 release date)
* 3.2 expected EOL date: TBD (redis 3.6.0 release date)

[1]: https://access.redhat.com/support/policy/updates/errata/
[2]: https://access.redhat.com/security/updates/backporting
[3]: http://php.net/supported-versions.php
[4]: http://php.net/eol.php
[5]: https://wiki.php.net/rfc/releaseprocess
[6]: http://en.wikipedia.org/wiki/PHP#Release_history
[7]: http://php.net/archive/2014.php#id2014-08-14-1
[8]: http://php.net/archive/2015.php#id2015-09-04-4
[9]: http://www.mysql.com/support/
[10]: http://www.mysql.com/support/eol-notice.html
[11]: https://en.wikipedia.org/wiki/MySQL#Versions
[14]: http://dev.mysql.com/doc/relnotes/mysql/5.5/en/
[15]: http://dev.mysql.com/doc/relnotes/mysql/5.6/en/
[16]: https://mariadb.com/kb/en/mariadb/mariadb-maintenance-policy/
[17]: https://docs.python.org/devguide/devcycle.html
[18]: https://www.python.org/download/releases/2.6.9/
[19]: https://www.python.org/dev/peps/pep-0373/
[20]: https://www.python.org/download/releases/3.0.1/
[21]: https://www.python.org/download/releases/3.1.5/
[22]: https://www.python.org/dev/peps/pep-0392/
[23]: https://www.python.org/dev/peps/pep-0398/

[mysql-eol]: http://www.mysql.com/support/eol-notice.html
[pep-0429]: https://www.python.org/dev/peps/pep-0429/
[pep-0478]: https://www.python.org/dev/peps/pep-0478/
[redis-downloads]: http://redis.io/download
[redis-3.0.0]: https://github.com/antirez/redis/blob/3.0.0/00-RELEASENOTES#L15
[redis-3.2.0]: https://github.com/antirez/redis/blob/3.2.0/00-RELEASENOTES#L14
