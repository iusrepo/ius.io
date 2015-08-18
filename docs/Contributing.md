# Contributing to IUS

## New Package Request

IUS users are encouraged to submit new package request to our [package
wishlist][1].  We can not promise that will proceed with every request, so we
came up with these questions to help evaluate requests:

* Is the new package a good fit for IUS?
* Will the new package be maintainable with our current resources?
* Is the requester willing to test the new package to ensure expected behavior?

We want to make sure new packages fit within the [scope of IUS][2].  The IUS
covedev team does have limited resources, so we want to make sure new packages
won't effect the maintenance of all packages.  Also, we would like to avoid
requests like, "It would be cool if IUS packaged $RANDOM_APPLICATION, even
though I do not have a use for it."

## Package Feedback

The most important way to contribute is to provide feedback on our packages.
We want positive and negative feedback alike.  Positive feedback helps indicate
which packages see the most usage, and negative feedback helps us isolate
issues and resolve them.  If it is determined that the issue isn't related to
packaging, but rather part of the upstream source code, we will work to get the
fix added to the upstream source code whenever possible.  Upstream developers
value the feedback we help generate by enabling users of Enterprise Linux to
use the latest versions of their software.

## Early Testing

The testing repository is added as part of the ius-release package, but is
disabled by default.  Users can participate in early testing by enabling this
repository and installing/updating from there.  We also recommend configuring
automatic nightly updates so that new updates are applied as soon as possible.
If you see an issue with a testing package, let us know as soon as you can; if
notified soon enough we can fix the issue before the update is pushed to the
stable repositories and affects more users.  Please see our [release policy][3]
for more information about how long packages stay in each repository.

## Spread the Word

There are many forums and blog posts around that internet describing various
methods of upgrading PHP, MySQL, Python, and other softare on Enterprise Linux.
Unfortunately, many of these recommend using problematic third party
repositories, one-time rebuilds of source RPMs, or just manually compiling
software from source.  We know there is a better way!  We stand behind the
quality of our packages, and want as many people as possible to benefit from
them.  If you come across posts like these, contact the author and introduce
them to IUS.  If you have your own blog, we encourage you to write a post about
your experiences with IUS.  If you were able to solve a problem with IUS, you
may be able to help someone else with the same problem.

An integral part of open source software is community.  You can help form the
identity of our community by discussing IUS in IRC channels, LUG meetings, or
conferences.  Recommending us to your friends and coleagues is another great
way to help.

## RPM Packaging

Users can participate in the development of our RPM packages by sending us pull
requests against our [spec files][4] on GitHub.  We also accept new package
requests on our [wishlist][5].

Currently only members of the Core Development Team who are Rackspace employees
have access to our package build system.  We are using a custom solution to
build both IUS packages and also private packages for Rackspace.  We plan to
eventually deploy a publicly accessible build system to allow trusted community
members to build IUS packages.

[1]: https://github.com/iuscommunity/wishlist
[2]: index.md#about
[3]: Philosophy.md#release-policy
[4]: https://github.com/iuscommunity-pkg
[5]: https://github.com/iuscommunity/wishlist
