# History

## Project History

The IUS Project started as an internal experiment at [Rackspace][1] in 2006.

Rackspace customers would regularly request newer versions of PHP and MySQL.
Third party RPM repositories existed that would provide these things, but they
were considered unsafe because they would unexpectedly replace other stock
packages beyond what was requested (see the [SafeRepo Initiative][2]).  A
better solution was needed.  Rackspace employees started building new packages
with alternate names from the stock packages.  These were special because they
would have a virtual provides for the stock package name, in order to satisfy
other packages' dependencies.  However, because the actual package name was
different, upgrading to the new package could never happen unexpectedly.  All
upgrades were on an individual, opt-in basis.  This gave customers the
flexibility and control they were looking for.

These RPM package repositories continued as an internal Rackspace offering
until 2009.  In the spirit of open source, it was decided that these RPM
packages should be publicly available so that anyone could benefit.  This was
the start of the IUS Project as we know it today.

The IUS project is fully sponsored by Rackspace, and the core developers are
Rackspace employees.  That said, **IUS is not a service of Rackspace!**  IUS
packages are not covered by any service level agreements.  For more details,
please read our [End User Agreement][3].

## Notable Removed Packages

### yum3

Older versions of yum in EL5 had issues resolving dependancies that were
provided by packages with alternative names.  IUS submitted a patch
[upstream][4] and also created a [yum3 package][5] with the fix.  The issue was
eventually [backported to the stock RHEL yum package][6], which made the yum3
package unnecessary.

### openssl10

Several years ago, we received a request for an updated version of
[openssl][7].  When the request first came in, there was an internal debate if
IUS should package something so important to the whole OS like openssl.  We
decided to package it and had second thoughts about that decision almost
immediately.  Since Red Hat updated their openssl packages, we pulled our
openssl10 packages from the stable repositories.

## LaunchPad

When the IUS project first started, [LaunchPad][8] was the best location for
version control, bugs and mailing lists. Unfortunately, LaunchPad is starting
to show its age and thus we switched to GitHub for version control and
bugs/issues. We still use LaunchPad for our mailing lists.


[1]: https://www.rackspace.com
[2]: SafeRepo.md
[3]: https://dl.iuscommunity.org/pub/ius/IUS-COMMUNITY-EUA
[4]: http://web.archive.org/web/20120114083114/http://yum.baseurl.org/ticket/296
[5]: https://bugs.launchpad.net/ius/+bug/453543
[6]: https://bugzilla.redhat.com/show_bug.cgi?id=529719
[7]: https://bugs.launchpad.net/ius/+bug/1034961
[8]: https://launchpad.net/ius
