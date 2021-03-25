# Semantic Versioning

SemVer or [Semantic Versioning](https://semver.org/) is a popular versioning,
designed to help developers track and maintain changes in their dependency graph
with minimal cognitive overhead.

It is a simple set of rules and requirements that dictate how version numbers
are assigned and incremented. These rules were based on common practices in use
in both closed and open-source software. For this system to work, you first need
to declare a public API. This may consist of documentation or be enforced by the
code itself. Regardless, it is important that this API be clear and precise.
Once you identify your public API, you communicate changes to it with specific
increments to your version number.

Under this scheme, version numbers and the way they change convey meaning about
the underlying code and what has been modified from one version to the next.

## How it works

The version string is split into three main components, separated by dots. e.g.
v1.4.1. The leftmost number is the MAJOR version number. The middle number is
the MINOR version number. The rightmost number is the PATCH version number.

### PATCH

You should increment the PATCH version number when non-breaking bugfixes are
released. For example, if the publicly available version v1.0.0 has a bug which
is discovered and patched, the fixed version would be deployed as v1.0.1.

### MINOR

You should increment the MINOR version number when new features are added in
such a way that backward compatibility is maintained. For example, if a new
route is added which does not modify any of the existing API which projects may
rely on, you would increment, say, v1.1.0 to v1.2.0. You would also reset the
PATCH version to 0 when this happens, e.g. v1.5.1 becomes v1.6.0

### MAJOR

You should increment the MAJOR version number when either a new feature or a
bugfix is released which breaks backward compatibility with the existing API.
For example, if a route is removed from a project, you might release that as
v2.0.0. You also reset both the MINOR and PATCH versions to 0 at this time.

## How Often Do I Need to Think About This?

This stuff only comes into play when we're publishing a release. You don't need
to increase the version number every time you push a commit to `main`. The
version number will be updated automatically by GHA based on the
[merged commits](../commits/index.md) since the previous release.

[Home](../README.md)
