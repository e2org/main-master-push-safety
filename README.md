Main/Master Push Safety
-----------------------

Simple githook to prevent errant pushes (especially force-pushes) from wrecking your main/master branches.

**Why?** Github now provides a "protected branches" feature that accomplishes this.

A few reasons:
- Gitub's "protected branches" feature is only available on paid Github accounts. Why they would choose to make such a fundamental safety feature a paid addon, I can't fathom (cough, MCAS) but more generally implementing measures at this layer undermines many of the reasons we use Git in the first place. Safety measures shouldn't need to be put in place by some central authority, on a central repository; they should be available anywhere, to anyone who wants to use them -- there is a D in DVCS after all.
- Personally, I want these rules to be configurable across the board -- I want my Git experience to be consistently safe everywhere. In many cases, I'm doing work on repositories that are too early-stage to configure these, or their owners don't believe branch protection is a necessary measure to have in place. This is fine for them -- I should be able to configure it for myself, and at least my own interactions with repositories will be safe.

To install the hook globally, to apply when pushing any of your repositories:
```
mkdir -p ~/.githooks/ && cp ~/main-master-push-safety/pre-push ~/.githooks
git config --global core.hooksPath ~/.githooks
```
**Note:** repos that define their own `.git/hooks` will override any global `.githooks` directory; use installation method below to set up locally.

To install the hook locally in a specific repo:
```sh
mkdir -p ~/myrepo/.git/hooks/ && cp ~/main-master-push-safety/pre-push ~/myrepo/.git/hooks
```

To set custom list of "protected" branches (default is `main,master`):
```sh
# in ~/.bashrc or similar...

export GIT_PROTECTED_BRANCHES="foo,bar,baz"
```

