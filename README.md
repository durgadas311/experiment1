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

### Creating a submodule

The submodule 'cpnet-z80' was created initially by:
```
git submodule add https://github.com/durgadas311/cpnet-z80.git
```
This creates the submodule and populates it, and points it to the 'master' branch.

A different branch can be referenced using the `-b <branch>` option.
It also appears that the branch can be changed later using:
```
git submodule set-branch -b <branch> cpnet-z80
```

### Updating a submodule

Because the submodule repo is independent, it may get updated externally
and need to be refreshed locally. The following command will effectively
update the submodule to it's latest commit on the current branch:
```
git submodule update --remote cpnet-z80
```
Note that this update is local in the 'experiment1' repo, and needs to be
commited and pushed. TODO: determine whether a fresh clone uses the stale commit
or always uses the latest.

Note that this effectively provides a "frozen" environment - the submodule
repo will not change unless you update it.

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
