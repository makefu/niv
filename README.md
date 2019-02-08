# niv

[![CircleCI](https://circleci.com/gh/nmattia/niv.svg?style=svg)](https://circleci.com/gh/nmattia/niv)

A tool for dealing with third-party packages in [Nix]. Read more about it in
the [usage](#usage) section.

## Install

``` bash
$ nix-env -iA niv -f https://github.com/nmattia/niv/tarball/master
```

## Build

Inside the provided nix shell:

``` bash
$ # GHCi:
$ snack ghci
$ # run:
$ snack run -- <args>
```

## Usage

`niv` simplifies [adding](#add) and [updating](#update) dependencies in Nix
projects. It uses a single file, `nix/sources.json`, where it stores the data
necessary for fetching and updating the packages.

* [Add](#add): inserts a package in `nix/sources.json`.
* [Update](#update): updates one or all packages in `nix/sources.json`.
* [Drop](#drop): deletes a package from `nix/sources.json`.

`niv` has two more utility functions:

* [Init](#init): bootstraps a Nix projects, in particular creates a
  `nix/sources.json` file containing `niv` and `nixpkgs` as well as a
  `nix/sources.nix` file that returns the sources as a Nix object.
* [Show](#show): shows the packages' information.

```
NIV - Version manager for Nix projects

Usage: niv COMMAND

Available options:
  -h,--help                Show this help text

Available commands:
  init                     Initialize a Nix project. Existing files won't be
                           modified.
  add                      Add dependency
  show                     
  update                   Update dependencies
  drop                     Drop dependency

```

### Add

```
Examples:

  niv add stedolan/jq
  niv add NixOS/nixpkgs-channel -n nixpkgs -b nixos-18.09
  niv add my-package -v alpha-0.1 -t http://example.com/archive/<version>.zip

Usage: niv add [-n|--name NAME] PACKAGE ([-a|--attribute KEY=VAL] |
               [-b|--branch BRANCH] | [-o|--owner OWNER] | [-r|--repo REPO] |
               [-v|--version VERSION] | [-t|--template URL])
  Add dependency

Available options:
  -n,--name NAME           Set the package name to <NAME>
  -a,--attribute KEY=VAL   Set the package spec attribute <KEY> to <VAL>
  -b,--branch BRANCH       Equivalent to --attribute branch=<BRANCH>
  -o,--owner OWNER         Equivalent to --attribute owner=<OWNER>
  -r,--repo REPO           Equivalent to --attribute repo=<REPO>
  -v,--version VERSION     Equivalent to --attribute version=<VERSION>
  -t,--template URL        Used during 'update' when building URL. Occurrences
                           of <foo> are replaced with attribute 'foo'.
  -h,--help                Show this help text

```

### Update

```
Examples:

  niv update
  niv update nixpkgs
  niv update my-package -v beta-0.2

Usage: niv update [PACKAGE] ([-a|--attribute KEY=VAL] | [-b|--branch BRANCH] |
                  [-o|--owner OWNER] | [-r|--repo REPO] | [-v|--version VERSION]
                  | [-t|--template URL])
  Update dependencies

Available options:
  -a,--attribute KEY=VAL   Set the package spec attribute <KEY> to <VAL>
  -b,--branch BRANCH       Equivalent to --attribute branch=<BRANCH>
  -o,--owner OWNER         Equivalent to --attribute owner=<OWNER>
  -r,--repo REPO           Equivalent to --attribute repo=<REPO>
  -v,--version VERSION     Equivalent to --attribute version=<VERSION>
  -t,--template URL        Used during 'update' when building URL. Occurrences
                           of <foo> are replaced with attribute 'foo'.
  -h,--help                Show this help text

```

### Drop

```
Examples:

  niv drop jq
  niv drop my-package version

Usage: niv drop PACKAGE [ATTRIBUTE]
  Drop dependency

Available options:
  -h,--help                Show this help text

```

### Init

```
Usage: niv init 
  Initialize a Nix project. Existing files won't be modified.

Available options:
  -h,--help                Show this help text

```

### show

```
Usage: niv show 

Available options:
  -h,--help                Show this help text

```

[Nix]: https://nixos.org/nix/
