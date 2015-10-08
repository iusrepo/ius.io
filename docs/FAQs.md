# FAQs

### General

#### What is the IUS community project?

The IUS Community Project is an effort to package RPMs of the latest stable
versions of the most commonly requested software on Red Hat Enterprise Linux
and CentOS. IUS provides a better way to upgrade PHP/MySQL/Python/etc on RHEL
or CentOS. The project is run by professional Linux Engineers that are
primarily focused on RPM Development in the web hosting industry.

#### What is it NOT?

For one, IUS is not a service of Rackspace but rather is sponsored by
Rackspace. Additionally, IUS is not the same as Fedora EPEL or similar
repositories.  EPEL is geared towards adding packages to RHEL, and has strict
guidelines that none of their packages replace anything in RHEL. IUS on the
other hand is explicitly geared towards providing packages that do replace
existing software in RHEL. Essentially, we are offering a proper way to upgrade
software on RHEL when you really need it the latest upstream versions of
software.

#### What does IUS stand for?

**I**nline with **U**pstream **S**table

#### Why can’t I just do a ‘yum upgrade’ and update my RPMs?

See [Naming Convention][2].

#### Why are IUS packages named differently and what the does the 'u' stand for?

See [Naming Convention][2].

#### Which repositories should I use for Scientific Linux, Oracle Linux or other distribution based on Red Hat?

We would recommend using our Red Hat repositories for these OSes since they are
based on RHEL and not CentOS.

#### Why are mysqlclient15 and mysqlclient16 such an old version?

Our mysqlclient15 and mysqlclient16 package provide the stock version of
libmysqlclient, so stock package can interact with our msyql-server packages.

#### Can IUS be used with DNF?

EPEL does contain DNF packages for EL 7, and can be used with IUS repositories.

#### What happened to LaunchPad?

See [LaunchPad][11].

### Is IUS right for me?

#### Am I a Rackspace customer?

Rackspace sponsors IUS, but anyone is free to use IUS packages.  Just using IUS
packages does not make you a Rackspace customer.

#### What is the relationship between Rackspace and IUS?

IUS is sponsored by Rackspace, but is not a service of Rackspace.  It is
similar to the relationship between Red Hat and EPEL.

* $COMPANY sponsors $PROJECT via engineer man-hours, servers, and bandwidth.
* The escalation path for $PROJECT packages is with $PROJECT, not with $COMPANY.
* No $COMPANY service level agreements apply to packages from $PROJECT.

#### Can I afford the risk of using IUS package vs super stable packages from Red Hat?

IUS might introduce bugs/stability issues because it is bleeding edge versions
of software. There is no way around that, so it is a give and take situation.
You get the latest and greatest, but you also get to be one of the first people
to find bugs before everyone else.

#### Should I use IUS so I can pass PCI or other security audits?

Some security audits only use software versions to confirm security
vulnerabilities have been addressed.  This approach does not take into account
[Red Hat's backporting of security fixes][3].  Some additional communication
with your security auditor may be needed on RHEL or CentOS servers.  It is not
recommended to use IUS packages just to pass a security audit.

#### Does Red Hat support the use of IUS packages?

No.

#### Do you recommend IUS over stock RHEL packages?

No, not necessarily. We do not want to give the impression that our packages
are better than those found in RHEL. Red Hat has teams of developers working
tirelessly to ensure the stability and reliability of their packages. IUS does
not have the resources to even begin to compete with the stability and quality
of the official packages maintained by Red Hat. Plus, we are also following the
latest and greatest sources from upstream directly which inevitably opens up a
higher level of risk that those packages will introduce bugs.

IUS is recommended for users that absolutely need newer versions of specific
software than RHEL can provide. IUS is not intended for users that want to
update their entire OS. You don't want to use IUS packages just because it
'feels good' or is 'cool' to have newer software. Though, don't get me wrong,
IUS is pretty cool.

IUS solves the problem of: "How do I upgrade software on my RHEL machine, and
keep that software updated and maintained for bugs/security issues?" You can
look all over the internets and see dozens of 'how-to' articles where people
explain how they upgraded PHP/MySQL/etc. on their RHEL server. But how many do
you find that explain how they keep that version of PHP/MySQL/etc. updated and
patched? Not many, until now.

#### How is IUS different than SCL?

See [IUS vs. Software Collections][4].

#### Does IUS cost anything?

IUS packages are free as in speech and beer.

#### How can I be notified when an IUS package I am using reaches EOL (end of life) status?

We post to our [public mailing list][10] when a package has reached EOL status.

### Development and Packaging Questions

#### How can I contribute to IUS?

See our [contributing page][5].

#### How do I install packages from testing?

See [Using Testing Repositories][6].

#### What packaging system do you use?

We built a system called MonkeyFarm that functions much like [Fedora Koji][7].
We make no attempt to compete with Koji in that department, however there were
other needs for a ‘build system’ outside of RPM packaging that lead us to
continue work on our own. Additionally, the preceptor to MonkeyFarm was RPE
(The Rackspace Packaging Environment) which was started before Koji was
released publicly (and before we knew about it).

#### Why are there separate repositories for Red Hat and CentOS?

There are times when Red Hat makes a changes during a new point releases (i.e.
RHEL 6.6 to 6.7) that require IUS packages to be rebuilt or they will not work
on the new point release.  Some examples include the change from [libjpeg to
libjpeg-turbo in RHEL 6.4][8] and updates to [ImageMagick in RHEL 6.7][9] that
required updates to IUS php packages.

Also, a new point release for CentOS does not happen the same day as RHEL. So
how can we make sure that our packages will work on both Red Hat and CentOS
during the gap between Red Hat and CentOS point releases (that requires updates
to our packages)?  The answer we came up with to have separate repositories.

[2]: Philosophy.md#naming-convention
[3]: https://access.redhat.com/security/updates/backporting/?sc_cid=3093
[4]: IUSvsSCL.md
[5]: Contributing.md
[6]: Usage.md#using-testing-repositories
[7]: https://fedoraproject.org/wiki/Koji
[8]: https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/6.4_Technical_Notes/RHEA-2013-0422.html
[9]: https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/6.7_Technical_Notes/package-ImageMagick.html
[10]: https://launchpad.net/~ius-community
[11]: History.md#launchpad


