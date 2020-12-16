# experiment1
Experiment for using submodule of cpnet-z80

### Background

This repo uses a submodule (embedded/linked repo). The simplest way to
get everything is:

```
git clone --recurse-submodules <URL>
```
If a normal clone command is/was used, the following
additional commands will setup (fetch) the embedded repo:
```
git submodule init
git submodule update
```

In this repo ("experiment1"), the submodule is in the
"cpnet-z80" subdirectory. All changes made under "experiment1/cpnet-z80"
will apply to the external repo 'cpnet-z80'. All other changes will apply
to the 'experiment1' repo.

Remember that the submodule changes must be committed and pushed separately.

Any directories or files added outside of "experiment1/cpnet-z80" are added to
this repo, and have no effect on the cpnet-z80 repo. This is used to maintain isolation
between the external "cpnet-z80" repo and this repo.

A submodule may be created to access any given branch of an external repo, however
the URL used should point to a "public" access method (i.e. should not contain
your user ID, etc.). Your working repo can modify the URL using:
```
git config submodule.cpnet-z80.url PRIVATE_URL
```
while still allowing the general public at access the repo
in the manner that is correct for them.

### Examples

The script "build" shows how to execute a 'make' command in the 'cpnet-z80' repo
while producing the build results in the 'experiment1' repo.

For example, to use the default BUILD directory of ${PWD}/bld, and
build w5500 mt011 use:
```
./build NIC=w5500 HBA=mt011
```

Note that, when adding "BUILD=/path" to the 'build' commandline, the path needs
to be absolute because the 'make' command changes directory before it uses
'BUILD'.
