# Git Workspace

This script is intended to ease the development in multirepo environment. By defining a workspace file
that contains all the repositories one can easily share the environment setup without the need for manual
git clones. With git configuration user and host can also be set for the repositories. This allows one
to use e.g. multiple bitbucket repositories with different SSH keys easily without altering the host in
each git clone command.

This script also provides a command to check the overall state of the workspace (branches, untracked files etc.).
Few commands are overridden, but most are plain passthroughs to git and are run in all of the workspace
repositories.

```
Installation:

  - Ensure that "git-ws" has execution permitted.
  - Either
    - run "./git-ws install"
    - manually create symlink into a directory included in \$PATH
    - copy the file to a direcotry included in \$PATH

Usage:

  git ws <cmd> [arg]

Commands:

  init:   Create a new (empty) workspace definition to the current directory
  clone:  Clone the repositories defined in the $WORKSPACE_FILE file
  state:  Display workspace state
  help:   Display this help and exit

  The command can be also any git operation such as push, pull or fetch (exception: clone has been redefined).
  This operation will be run for all of the repositories/directories defined in the $WORKSPACE_FILE file.
  e.g. "git ws pull origin/master"

Configuration:

  Configuration is currently in two parts. One is shareable workspace file and the other one will be user specific
  configuration containing git host and user. This is to allow for example multiple bitbucket accounts and ssh keys.
  Downside is that in the first version of this script, the user and host must be the same for all repositories.
  This is something to be looked into.

  $WORKSPACE_FILE:
    - One line, one repository
    - <path>/<repository>.git
    - e.g.
      MyGithubAccount/exmplarepository.git
      MyFriendsGithubAccount/collaborativerepository.git

  $WORKSPACE_GIT_CONFIGURATION:
    - Git user
    - Git host
    - e.g.
      GITUSER=git
      GITHOST=github.com

https://github.com/XC-/git-workspace
Licensed under MIT license
```