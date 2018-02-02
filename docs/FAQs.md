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

#### Why is mysqlclient16 such an old version?

Our mysqlclient16 package provides the stock version of libmysqlclient, so stock
package can interact with our msyql-server packages.

#### Can IUS be used with DNF?

EPEL did contain DNF packages for EL 7, but they have been moved to a [CentOS
SIG][dnf sig].  Note, DNF is also referred to as YUM 4.

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

Watch our [announcements repository][10], where we open a new issue when a package has reached EOL status.

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
to our packages)?  The answer we came up with was to have separate repositories.

### PHP

#### I want to use Nginx with php-fpm, but when I install php it pulls in httpd as a dependency.  Why?

The PHP language is actually in the php56u-common package.  The php56u package
is mod\_php, an httpd module that serves as a PHP SAPI (server API).  Yes, the
naming is less than ideal, but it's something we inherited from Fedora/RHEL.

#### Why can't I install php56u with httpd24u?

As noted in the previous question, php56u is actually the mod\_php httpd
module.  It compiles against the MMN (magic module number) of httpd.  This
means that if you build mod\_php against httpd 2.2, it can only install with
httpd 2.2.  When we created httpd24u, [we decided to continue building our
mod\_php packages against stock httpd][mod_php_decision].  Building mod\_php
for every combination of php and httpd was far more complexity than we were
willing to maintain.  Additionally, there was no way to trigger automatic
updates for users to switch from php56u/httpd to php56u/httpd24u.  In order to
use httpd24u with PHP 5.6, you must use php56u-fpm. The FPM SAPI does not
compile against a specific webserver, so you can use it with httpd, nginx,
lighttpd, and more.

#### I don't see php70u in the repos, where is it?

To address the mod\_php naming confusion in our PHP 7.0 packages, we chose to
move the mod\_php files into a subpackage named mod\_php70u.  This means that
you should explicitly choose php70u-fpm or mod\_php70u. mod\_php70u still
provides php70u, so running `yum install php70u` still works.

#### I'm trying to install phpMyAdmin, but yum is failing with errors from IUS packages.  Why?

IUS packages usually work just fine with noarch stock and EPEL PHP packages,
but yum's dependency resolution is not always smart enough to pull in all the
correct dependencies.  You can work around this by explictly requesting a few
more package names to help the transaction resolve successfully.  Please note
that not all EPEL package version will be compatible with the latest versions
of PHP.  In particular, phpMyAdmin 4.0 from EPEL6 is not compatible with PHP 7,
and phpMyAdmin 4.4 from EPEL7 is not compatible with PHP 7.1.

* `yum install phpMyAdmin php56u-{bcmath,cli,common,gd,mbstring,mcrypt,mysqlnd,process,tidy,xml}`
* `yum install phpMyAdmin php70u-{bcmath,cli,common,gd,json,mbstring,mcrypt,mysqlnd,process,tidy,xml}`

Alternatively, you can use dnf which has much better dependency resolution
capabilities, and allows for a much easier installation.  See [this FAQ][dnf
faq] for more information.

* `dnf install phpMyAdmin php56u-common`
* `dnf install phpMyAdmin php70u-common`

#### I'm trying to install composer, but yum is failing with errors from IUS packages.  Why?

See the previous question regarding phpMyAdmin.

* `yum install composer php56u-{cli,common,gd,intl,mbstring,pdo,pecl-jsonc,process}`
* `yum install composer php70u-{cli,common,gd,intl,mbstring,pdo,process}`
* `yum install composer php71u-{cli,common,gd,intl,mbstring,pdo,process}`

* `dnf install composer php56u-common`
* `dnf install composer php70u-common`
* `dnf install composer php71u-common`

[2]: Philosophy.md#naming-convention
[3]: https://access.redhat.com/security/updates/backporting/?sc_cid=3093
[4]: IUSvsSCL.md
[5]: Contributing.md
[6]: Usage.md#using-testing-repositories
[7]: https://fedoraproject.org/wiki/Koji
[8]: https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/6.4_Technical_Notes/RHEA-2013-0422.html
[9]: https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/6.7_Technical_Notes/package-ImageMagick.html
[10]: https://github.com/iuscommunity/announce
[dnf sig]: https://seven.centos.org/2017/10/yum-4-is-available-for-testing/
[11]: History.md#launchpad

[mod_php_decision]: https://lists.launchpad.net/ius-community/msg01277.html
[dnf faq]: FAQs.md#can-ius-be-used-with-dnf
