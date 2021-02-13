Main/Master Push Safety
-----------------------

Simple githook to prevent errant pushes (especially force-pushes) from wrecking your main/master branches.

To install the hook globally, to apply when pushing any of your repos:
```
mkdir -p ~/.githooks/ && cp ~/main-master-push-safety/pre-push ~/.githooks
git config --global core.hooksPath ~/.githooks
```
Note: repos that define their own `.git/hooks` will override any global `.githooks` directory; use installation method below to set up locally.

To install the hook locally in a specific repo:
```sh
mkdir -p ~/myrepo/.git/hooks/ && cp ~/main-master-push-safety/pre-push ~/myrepo/.git/hooks
```

To set custom list of "protected" branches (default is `main,master`):
```sh
# in ~/.bashrc or similar...

export GIT_PROTECTED_BRANCHES="foo,bar,baz"
```

