<a name="history"></a>
# History

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

[1]: https://www.rackspace.com
[2]: saferepo.md
[3]: https://dl.iuscommunity.org/pub/ius/IUS-COMMUNITY-EUA
