go-build-info
=============

This script is designed to simplify the common task of setting build
information for Go applications using information provided by a Git repository.
Attributes set by this script include:

* branch
* revision
* username of user who invoked the build
* build date

``go-build-info`` assumes it is being executed within a Git repository to
gather the necessary information.

Usage
-----

Install ``go-build-info`` somewhere on your ``PATH`` and ensure it's
executable. Then add a ``go:generate`` line to a Go source file, such as the
following:

```go
//go:generate go-build-info -p version -o build_info.go

package version

...
```

Invoke ``go generate`` before building your project each time, and current
build information will be available within your code.

Options
-------

* ``-p``, ``--package``: Name of the Go package to specify in the output.
  Default is ``main``.
* ``-o``, ``--output``: Name of the output file to create. The file will be
  overwritten without warning. Default behavior simply writes to stdout.
* ``-f``, ``--prefix``: Prefix to give variables. Default is ``Build``.
* ``-b``, ``--branch``: Name to give the branch variable. Default is ``Branch``.
* ``-r``, ``--revision``: Name to give the revision variable. Default is
  ``Revision``.
* ``-u``, ``--user``: Name to give the user variable. Default is ``User``.
* ``-d``, ``--date``: Name to give the date variable. Default is ``Date``.
