switch-svn2git - A tool to migrate existing Subversion checkouts to Git
-----------------------------------------------------------------------

`switch-svn2git` turns an existing Subversion working copy into a Git clone, for
project that are being migrated or have been migrated from SVN to Git. This
assumes that there is a Git server (or share bare repository) with the same
revision history as on SVN before. This program is also useful to switch
repositories to Git in cases where SVN and Git services are offered in parallel
(e.g. via [SubGit](http://subgit.com/)).

`switch-svn2git` replaces the `.svn` sub-directories in your SVN working copy
by a `.git` sub-directory. The actual content of your working copy is *not*
touched, so all uncommitted changes and untracked files are preserved.

This program assumes the your SVN repository URL of your working copy has the
format BASE_URL/PROJECT/trunk or BASE_URL/PROJECT/branches/BRANCH.

Revisions are matched by time stamp, in cases where the time stamp is not
unique, a warning will be given and the latest time stamp will be used.

This package also includes a tool `switch-git2git` that makes it easy to
change the remote URL (of remote "origin") of a Git repository.


Installation
------------

Just copy the shell-scripts `switch-svn2git` and `switch-git2git` into a
directory on your `PATH`, or add the switch-svn2git to your `PATH`.


Usage
-----

In the top-level directory of your SVN working copy, run

    # switch-svn2git GIT_BASE_PATH

Examples:

    # switch-svn2git git@github.com:GITHUB_USER
    # switch-svn2git https://github.com/GITHUB_USER

Assuming your SVN URL was

    https://my-svn-server/repo/my-project/trunk

switch-svn2git will then try turn your working copy into a Git clone of, e.g.,

    # git@github.com:GITHUB_USER/my-project.git

For a short online help, just run `switch-svn2git` without arguments.

Warning: While this program has been implemented with care, it comes WITHOUT
ANY WARRANTY. It is recommended that you make a backup of your SVN working copy
first!

If you later want to change change change the origin (the remote server) URL of
your new Git clone, use `switch-git2git`. For example, to switch your origin URL
from `https://github.com/GITHUB_USER/my-project.git` to
`git@github.com:GITHUB_USER/my-project.git`, simply run

    # switch-git2git git@github.com:GITHUB_USER
