# KornShell 93u+m

This repository is used to develop bugfixes
to the last stable release (93u+ 2012-08-01) of
[ksh93](http://www.kornshell.com/),
formerly developed by AT&T Software Technology (AST).
The sources in this repository were forked from the
Github [AST repository](https://github.com/att/ast)
which is no longer under active development.

To see what's fixed, see [NEWS](https://github.com/ksh93/ksh/blame/master/NEWS)
and click on commit messages for full details.

To see what's left to fix, see [TODO](./TODO).

## Policy

1. No new features; bug fixes only (but see items 3 and 4).
   Feature development is for a future separate branch.
2. No major rewrites. No refactoring code that is not fully understood.
3. No changes in documented behaviour, except if required for compliance with the
   [POSIX shell language standard](https://pubs.opengroup.org/onlinepubs/9699919799/utilities/contents.html)
   which David Korn [intended](http://www.kornshell.com/info/) for ksh to follow.
4. No 100% bug compatibility. Broken and undocumented behaviour gets fixed.
5. No bureaucracy, no formalities. Just fix it, or report it: create issues,
   send pull requests. Every interested party is invited to contribute.
6. To help increase everyone's understanding of this code base, fixes and
   significant changes should be fully documented in commit messages.

## Why?

Between 2017 and 2020 there was an ultimately unsuccessful
[attempt](https://github.com/att/ast/tree/2020.0.1)
to breathe new life into the KornShell by extensively refactoring the last
unstable AST beta version (93v-).
While that ksh2020 branch is now abandoned and still has many critical bugs,
it also had a lot of bugs fixed. More importantly, the AST issue tracker
now contains a lot of documentation on how to fix those bugs, which makes
it possible to backport many of them to the last stable release instead.

In February 2020, having concluded the AST 93v- beta was too broken to
base new work on, others decided to start a new fork based on the last stable
93u+ 2012-08-01 release. Unfortunately, as of June 2020, the new
[ksh-community](https://github.com/ksh-community/ksh/)
organisation is yet to see any significant activity four months after its
bootstrapping. I hope that will change; I am ready to join efforts with them
at any time, as well as anyone else who wants to contribute.

The last stable ksh93 release from 2012 is the least buggy release currently
available, but it still has many serious bugs. So it is well past time to
start fixing those bugs, leave the rest of the code alone, and get an
improved release out there.

## Build

After cloning this repo, cd to the top directory of it and run:
```sh
./bin/package make
```
If you have trouble or want to tune the binaries, you may pass additional
compiler and linker flags by appending it to the command shown above. E.g.:
```sh
./bin/package make \
    SHELL=/bin/bash CCFLAGS="-xc99 -D_XPG6 -m64 -xO4" LDFLAGS="-m64"
```
For more information run
```sh
        bin/package help
```
Many other commands in this repo self-document via the `--help`, `--man` and
`--html` options; those that do have no separate manual page.

## Test

After compiling, you can run the regression tests.
Start by reading the information printed by:
```sh
./bin/shtests --man
```
