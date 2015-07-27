# End of Life

IUS packages work differently from Red Hat packages when it comes life cycle
management/EOL (end of life). Generally, Red Hat will support and backport
packages for the entire life span of the OS release, even if the upstream
project has ended support for the version in question. IUS follows the upstream
project.  When the project declares a version EOL, IUS will do the same and
move the packages to the archive repositories.

It is important to note that IUS packages will not automatically upgrade to the
next major version. If The Foobar Project EOLs foobar 2.5, the IUS foobar25u
package will not automatically get updated to foobar26u. This is done
intentionally, as it is common for software to make change in major version
that could introduce breakage.

While not all projects have clear documentation about life cycle management
here is some information we have been able to find. Please contact us with
corrections or additions.

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
