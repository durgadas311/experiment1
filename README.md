# experiment1
Experiment for using submodule of cpnet-z80

=== Background

This repo uses a submodule (embedded/linked repo). The simplest way to
get everything is:

```
git clone --recurse-submodules <URL>
```
If a normal clone command is/was used, the following
additional commands will setup the embedded repo:
```
git submodule init
git submodule update
```

In this repo ("experiment1"), the submodule is in the
"cpnet-z80" subdirectory. All changes made under "experiment1/cpnet-z80"
will apply to the external repo 'cpnet-z80'. All other changes will apply
to the 'experiment1' repo.

Remember that the submodule changes must be committed and push separately.

=== Examples

The script "build" shows how to execute a 'make' command in the 'cpnet-z80' repo
while producing the build results in the 'experiment1' repo.


