
# Git

Reference for working with [Git](http://git-scm.com/).

## Installing git

If you are on Mac OSX, you can install git using one of the following options:

With [Homebrew](http://mxcl.github.com/homebrew/)

	brew install git

With [MacPorts](http://www.macports.org/)

	sudo port install git-core +svn

Or use a pre-built [installer package](http://git-scm.com/download).

## Getting help

Show a list of basic git commands

	git help

Show a list of all git commands

	git help -a

Display help for a command

	git help <command>

Display the man page for a command

	man git-<command>

Display the current installed version of git

	git --version

# Working with git

## Creating a repository

Create a new git repository in the current directory

	git init

Create a bare git repository (bare repositories don't have a working directory of files)

	git init --bare

## Status of the index

Show a summary of the state of working directory and index

	git status

## Adding files to the index

Add a file to the index (staging files)

	git add <file>

Add all files from the current location and below to the index.

	git add .

Interactively stage files

	git add -i

Interactive add allows selective staging, unstaging of changed files as well as partial commits of specific lines.

Partial commits can be created by choosing the `patch` option and then specifying `split` to further refine chunks.

After exiting interactive adding, you need to the commit the index.

Stage all tracked, changed files

	git add --update
	git add -u

Add all files in the current repository

	git add -all
	git add --A

Add parts of the changes with each file (interactively add)

	git add --patched
	git add -p

Open the current diff in text editor

	git add -e

## Removing files from the index

Removing a file from the index (unstaging files)

	git reset HEAD <file>

Unstage all files from the index

	git reset HEAD

## Undoing local file changes

Discard local changes to a modified, unstaged file

	git checkout -- <file>

Discard local changes for all modified, unstaged files

	git checkout -- .

Remove newly added, but previously uncommitted, file from staged file list
Only affects index not file

	git rm --cached

## Committing changes

Commit current staged index

	git commit -m "<commit message>"

Commit current staged index, opening default editor to enter commit message

	git commit

Verbose commit, include a diff of the commit in the commit message

	git commit -v

## Altering Commits

Adjusting last commit

	git commit --amend

Amend is useful for quickly correcting or updating the most recent commit. If you haven't changed any files since committing, amend will simply allow you to update or correct the commit message.

Alternatively, if you wish to alter the committed files, make relevant edits in the working directory and stage the files as you want them to appear in the commit then run --amend.

The updated files will become part of the commit.

## Resetting Commits

Reset allows you to change the repository and working directory to a known state
Allows altering a combination of the HEAD, index and working directory depending on the mode used

Soft updates only the HEAD pointer

	git reset --soft <commit>

Mixed (default) updates the HEAD pointer and the index

	git reset --mixed <commit>

Hard moves the HEAD pointer, update the index and update the working directory

	git reset --hard <commit>

## Removing and renaming files

Stage an existing tracked file for removal (Removal occurs when committed). Git checks if the file being removed has any unsaved changes. It notifies you if it does and doesn't remove it

	git rm <file>

To force the removal of a file that has unsaved changes

	git rm -f <file>

Rename file1 to file2 (Move occurs when committed)

	git mv <file1> <file2>

Force overwrite of file2 with file1

	git mv -f <file1> <file2>

Show the full log history for a file that has been renamed. Without --follow, the log stops at the rename point

	git log --follow <file>

# Git repository history

## View history log

Show the commit log for the current branch

	git log

Show the commit log for the named branch

	git log <branch>

Show the commit log for the specified file or directory

	git log <file>
	git log <dir>

Use a double dash -- to separate a file to act on from the settings to use

	git log <settings> -- <file>

Set the output format for the commit summary (Options: oneline, short, full)

	git log --pretty=oneline

Abbreviate the commit hash so that it is shorter

	git log --abbrev-commit

Output the diff patches for each commit along with the details

	git log -p

Output statistics about each commit eg. the files affected and the number of lines changed

	git log --stat

Output an graphical representation of the commits and branches

	git log --graph

Show the last number of specified commits in the log eg. `git log -5` shows the last 5

	git log -<n>

Combine the above eg. show a log of all commits with a graphical output of timeline

	git log --graph --pretty=oneline --abbrev-commit

Search commit messages for the search string

	git log --grep="<search string>"

Search the commit message for the author name

	git log --author="<author name>"

Return commits where the search string was part of a files edit (known as _pickaxe_)
eg. `git log -Sdiv` (returns all commits where the string 'div' formed part of an addition or deletion)

	git log -S<search string>

Output the log for the specified range. Since and until are any valid identifiers such has relative or absolute history reference or sha1 identifier

	git log <since>..<until>

After a merge, use --merge with log to show only the commits from files that relate to the merge conflict

	git log --merge

Shows < in the log if a commit is from the left side of a merge (target / ours), and > if it is from the right (source / theirs)

	git log --left-right

Show commits more recent than a specific date. Date can be formatted date or human readable (eg. "3 days ago")

	git log --since="<date>"
	git log --after="<date>"

Show commits older than a specific date. Date can be formatted date or human readable (eg. "3 days ago")

	git log --until="<date>"
	git log --before="<date>"

## Show details about commits, tags, branches & files

Show details of the latest commit

	git show

Show details of a specific commit

	git show <sha1>

Show details of a commit relative to the current state

	git show <relative>

Show details about a specific tag

	git show <tag>

Show details about the latest commit on another branch

	git show <branch>

Show contents of file on another branch

	git show <branch>:<file>

Show the commit hash for any reference input

	git rev-parse <sha1|relative|tag|branch>

List the files tracked in the git repo. Add -s to show all files with SHA1 hashes. Add -u to show only conflicted files

	git ls-files

## Additional commit references, ranges and symrefs

As well as dates, parameters and sha1 references, the following features are available for referencing points in history.

Reference a parent commit (if multiple parents exist, eg. following a merge, use ^1, ^2, ^3 etc)

Show the first parent of HEAD

	git show HEAD^1

Show the second parent of HEAD

	git show HEAD^2

Reference the next ancestor in the history (~1 is the parent, ~2 is the grandparent etc), eg. To specify the last 50 commits on branch master: `master~50`

Current branch, diff between commits 2 and 3 times back

	git diff HEAD~3 HEAD~2

Specifies the range of commits between commit1 and commit2, any method of specify a commit may be used

	<commit1>..<commit2>

The set of commits that are reachable from either commit1 or commit2, but not both

	<commit1>...<commit2>

The most recent commit of the current branch

	HEAD

The saved state before an operation is performed, allows comparing before and after or rollback

	ORIG_HEAD

A temporary reference to the last branch fetched, only available immediately after a fetch operation

	FETCH_HEAD

A temporary reference to the head of the branch that is being merged in

	MERGE_HEAD

# Git blame and diff

## Using Blame to find who edited what

Show blame details for a file

	git blame <file>

Start the blame output at a particular line number

	git blame -L <linenumber>, <file>

## Comparing changes using diff

Diff shares many of the same commands, flags and options as log

Diff local working directory against current index (staged files), exposing what is dirty in the working directory

	git diff

Diff index (staged files) against HEAD (current repo state)

	git diff --staged

Diff local working directory against HEAD (current repo state)

	git diff HEAD

Diff between the working directory state and the state at the named commit

	git diff <commit>

Diff between the staged state and the named commit state

	git diff --staged <commit>

Diff current branch against another branch

	git diff <branch>

Diff only the named file (use -- <file> if there is any confusion between file names and tag names)

	git diff <file>
	git diff <dir>

Diff between any tree objects within the commit graph, the working directory or the index. A tree object can be referenced by commit id, branch name, tag or any valid identifier method

	git diff <state1> <state2>

Show the diff between the current state and the state prior to the latest commit (see what changed due to the last commit)

	git diff HEAD^ HEAD

Return on diff results that include the <string> as a changed item (-S is also called _pickaxe_)

	git diff -S<string>

Show the stats for the diff (number of lines changed, added and removed)

	git diff --stat

Example: Show stats for the state at commit1 and commit2, limiting to files in the named directory

	git diff --stat <commit1> <commit2> <dir>

List the file names affected and their change status

	git diff --name-status

List the number of lines affected and the file names

	git diff --numstat

Show only the file names of the files affected

	git diff --name-only

Set the number of context lines to surround the diff output with to <n> lines before and after

	git diff --unified=<n>

Output the diff result as a patch file eg. file.patch (for use with git apply)

	git diff <settings> > <file>

## Flags for diff

Detect renames and show only the rename rather than the full add and removal of the file

	-M

Ignore whitespace differences in files

	-w

Include statistics about the diffs (number of lines changed, number added, number removed)

	--stat

## Sample diff output

	diff --git a/<file1> b/<file2>
	index <file1 sha>..<file2 sha> <file mode>
	--- a/<file1 (original)>
	+++ b/<file2 (new)>
	@@ -<starting line for output a>,<number of lines in a> <starting line for output b>,<number oflines in b> @@
	 Shared line the same in both files
	+Line must be added to a to create b
	-Line must be removed from a to create b
	 Shared line the same in both files

# Working with branches and tags

## Show the current branches

Show a list of local branch names

	git branch

Show a complete list of branch names, including remote branches

	git branch -a

## Create a new branch

Create a branch new branch

	git branch <branch>

Create a branch name with a suffix. Used for convenience in organising branches. Allows wild carding actions against the suffix to affect all sub branches etc

	git branch <suffix>/<branch>

Start a branch at a commit other than the current state

	git branch <branch> <commit>

## Delete an existing branch

Deletes a branch (issues a warning if changes exist on the branch that haven't been merged)

	git branch -d <branch>

Force the deletion of a branch even if there are unmerged changes

	git branch -D <branch>

Delete a remote branch

	git push <remote> --delete <branch>

Alternative delete remote branch syntax

	git push <remote> :<branch>

Show stale remote branches from local (branches deleted from origin, which still exist locally)

	git remote prune origin --dry-run

Remove stale remote branches from local

	git remote prune origin

Rename a local branch

		git branch -m <original branch> <new branch>

## Renaming branches

Rename an existing branch (-m merges current branch entirely into the new branch)

	git checkout -m <original branch> <new branch>

Delete the original branch

	git branch -d <original branch>

## Switching branches

Switch to a branch

	git checkout <branch>

Create and switch branches in one step. Allows moving unstaged work directly to the new branch

	git checkout -b <branch>

If you have uncommitted changes on the current branch, you can't switch to a new branch if there is a conflict. Specifying -m merges your current changes into the branch being switched to (without creating a commit).

	git checkout -m <branch>

## Show a summary of the branch commits

Show recent commits for local branches

	git show-branch

Show recent commits for all branches including remotes

	git show-branch -a

Show activity for only the specified branches, can be used with the wildcard suffix

	git show-branch <branch1> <branch2>

Example of wildcard usage and having a suffix, allows showing all branches of a suffix type (eg. bug/*)

	git show-branch <suffix>/*

## Merging branches

Conflicted files from a merge contain standard merge markers (`<<<<<<<`, `=======`, `>>>>>>>`) to show each version. Manually correct the file, remove the markers until the file is in a state that you are happy with then add and commit

Merge a specified branch into the current branch

	git merge <branch>

Merge a specified branch from a remote into the current branch

	git merge <remote>/<branch>

Switch to the specified branch and merge in the contents of the current branch (merge only occurs on filesystem, no commit is made)

	git checkout -m <branch>

Switch to the specified branch and discard current branch changes

	git checkout -f <branch>

Abort a merge (any time before committing) and return to the state of the branch before initiating the merge

	git reset --hard HEAD

Abort a merge (after committing) and return to the state prior to merging (any dirty working directory files will be lost)

	git reset --hard ORIG_HEAD

Show details of the conflicted files from the merge

	git status

Shows a combined output with merge markers, using double column for showing lines added, removed and modified from both sources

	git diff

Compare the merge output to the original working directory

	git diff --ours
	git diff HEAD

Compare the merge output to the version being merged in

	git diff --theirs
	git diff MERGE_HEAD

Combined set of changes since the merge base

	git diff --base

Show the commits that contribute to the merge conflict and the changes they introduced for <file>. Omit <file> for all.

	git log --merge --left-right -p <file>

For merge commits, git log and git show include some additional information about the merge. A line labelled `Merge: <ancestor1 sha> <ancestor2 sha>` shows the origin of the merges. The files conflicted by the merge are listed in the commit and the diff is a combined diff.

	git show
	git log

Determine the commit at which the branch was created from the original branch

	git merge-base <originalbranch> <newbranch>

Apply the merge as a single squashed commit, destroying the source branches commit history in the target branch

	git merge --squash

Resolve conflicts by selecting wholesale our version (`--ours`), or their version (`--theirs`)

	git checkout --ours
	git checkout --theirs

Check out a single file from another branch into the current branch

	git checkout <otherbranch> <file>

## Rebase branch

Rebase takes the current branch, sets it to state of the target branch specified, the 'replays' all the branch change sets over the top.

	git rebase master

## Create and manage tags

List tags

	git tag

Create a new tag at the current point

	git tag -m "<description>" <tag>

Create a new tag at the specified commit

	git tag -m "<description>" <tag> <commit>

Delete tag

	git tag -d <tag>

Checkout tag (update the working directory to reflect the history at the tag)

	git checkout <tag>

# Git Stash

## Stash working directory changes

Stash away current Index (Staged files)

	git stash

Stash with message

	git stash save "My Message"

Restore stashed changes (keeps the stash in the stash list)

	git stash apply

List current stashes

	git stash list

Remove the most recent stash

	git stash drop

Drop the specified stash eg. git stash drop stash@{0}

	git stash drop <stash>

Clear all stashes

	git stash clear

Apply specific stash eg. git stash apply stash@{0}

	git stash apply <stash>

Apply stash to a new branch

	git stash branch <branch>

# Create and apply patches

Apply the patch file to the current working directory

	git apply <file>

# Remote repositories

## Working with remote repositories

Clone a remote repository to the local file system

	git clone <repourl> <localdir>

Clone a remote repository that requires a username

	git clone user@<host>:<path>

Clone a remote repository without the history (retrieves the latest code version)

	git clone --depth 1 <repourl>

Clone a remote repository to a given depth

	git clone --depth <depth> <repourl>

Note: Repos created with depth limit cannot be recloned into new repos, but they are good for quick checkout and development

Pull changes from remote repo

	git pull

Push current branch
Pushing a local branch to a non-existant remote branch name will create the remote branch

	git push

Push all branches (including new)

	git push --all

To push and pull from specific remote repositories with the current active local branch

	git pull <remote> <branch>
	git push <remote> <branch>


Push current branch and set it to automatically track the named remote branch

	git push -u <remote> <branch>

For example, to push to origin master and set your current branch to track master

	git push -u origin master

Assign the current branch to track the named remote branch

	git branch --track <remote>/<branch>

Assign the current branch to track the named remote branch

	git branch --track <local-branch> <remote>/<branch>

Show the name of the remote repository

	git remote show

Show details of the remote repo and status of branch tracking

	git remote show <remote>

Checkout and automatically add tracking for a branch in a remote repo

	git checkout -t <remote>/<branch>

Create a remote entry in .gitconfig for a remote called (labelled) <remotename>, located at <url>

Allows: git push <remotename> <branch>, to push a branch to the remote

	git remote add <remotename> <url>

Create a bare clone (no working directory) of an existing git repo. Useful when housing a bare repo on a remote server (use `<reponame>.git` as folder name)

	git clone --bare <repourl> <newfolder>

## Configuring push behaviour

git config push.default allows defining what `git push` will do

Using `git config push.default current` will only push the current active branch to it's tracking remote instead of pushing all tracked branches

Config to set up a repository to only push to its own remote branch with `git push`

	git config push.default current

Config to set up all repositories to only push to its own remote branch

	git config --global push.default current

# Git and SVN

## Working with SVN repositories

Clone an SVN repository

	git svn clone <url>

Show details about the SVN repository

	git svn info

Pull in the latest changes from the SVN repo (Stash before rebase)

	git svn rebase

Push git commits back to SVN (Stash before dcommit if working directory is dirty)

	git svn dcommit

Squash several commits from another branch into one commit on the current branch

	git merge --squash <branch>

## Useful git SVN commands

Show the SVN ignore file output

	git svn show-ignore

Append the SVN ignore info to the git exclude file

	git svn show-ignore >> .git/info/exclude

Create a .gitignore file based on the SVN ignore output

	git svn create-ignore

The git-svn-id that is included in the log info of each commit reveals the upstream repo, branch and commit info. This is the svn area dcommits will get pushed to.

	git-svn-id: svn://<url>/branches/<branch>@<svn-commit-id> <git-commit-id>

# Git Bisect

## Finding where an error was introduced with Bisect

Note: Always start bisect with a clean working directory

1) Initiate bisect, and set the 'bad' (present failing state) and 'good' (earlier known working state) points

Initiate bisect mode

	git bisect start

Find the commit where the error occurs (usually HEAD), and assign it as bad

	git bisect bad

Find a commit (ideally close by) where the state is working and assign it as good

	git bisect good <commit>

2) Git will now halve the distance between the bad and good commit and update the working directory to that commit.

3) Test the code to determine if it's good or bad, then issue the appropriate command

If the error is still present in the new version

	git bisect bad

If the error is not present in the new version

	git bisect good

4) Continue until git narrows down the selection to the single commit where the error was introduced

Other bisect commands:

To skip a commit, if it's not testable for whatever reason

	git bisect skip

Show the history of the commits checked and the good / bad state they were assigned

	git bisect log

Open an editor to visually inspect the remaining commits

	git bisect visualize

Return the working directory to the original state before bisect commenced

	git bisect reset

To correct a mistake in your bisect choices, copy the output of bisect log to a new text file and edit the lines to change good / bad. Then use git bisect replay, pointing to this modified log file to replay the steps to recommence bisecting

	git bisect replay <file>

# Hooks

Hooks are executable shell scripted files that reside in .git/hooks/ and are triggered when their named action occurs

List hook related commands and options for git

	git help hooks

# Combining projects with submodules

To include another git project inside your existing project, use git submodule

* All submodule commands must be run from the project root directory.
* Files from submodules are not added or cloned along with the project, only the details of what the submodule is and how to recreate it.
* Details of the submodule location in the project and the submodules git clone source are contained in a generated file called .gitmodules.
* .gitmodules forms part of the project and will be included in clone operations so other uses can use git submodule commands to import submodules.

Add another git repository as a submodule to the current project in the named directory. A file called .gitmodules will be created in the project root directory of the parent project that lists the path and repo url details.

	git submodule add <repo> <dir>

Add the submodule references from .gitmodules into .git/config to allow the project to perform submodule update. If you wish to locally reference another repo (eg. local test repo), you can edit .git/config and modify the repo target details for the submodule

	git submodule init

Update current submodules inside the repository with the relevant files from their own repositories

	git submodule update

Show the commits that the included repository submodules point to

	git submodule status

A file that contains the location and source of the submodule repositories. This file is passed around with the project to allow others to update submodule files.

	.gitmodules

# Other commands

To be expanded

	git cherry-pick
	--more
	--tail

Rewrite history replacing an incorrect email address with an updated email for a git author (Do not use on shared repositories)

	git filter-branch --env-filter 'if [ $GIT_AUTHOR_EMAIL = incorrect@email ]; then GIT_AUTHOR_EMAIL=correct@email; fi; export GIT_AUTHOR_EMAIL'

# Configuring Git

## Configuration files and settings

More local configuration files override more general config files (System -> User -> Repository)
Files can be edited directly in a text area of be set with the git config command

Config settings applied to the current repository (`git config <settings>`)

	.git/config

Config settings applied for the current user and all repositories (`git config --global <settings>`)

	~/.gitconfig

Config settings applied system wide of all repositories and all users (`git config --system <settings>`)

	/etc/gitconfig

List all configuration variables that are in effect. They are listed in cascading order (older settings overwrite earlier)

	git config -l

## Using the config command to apply settings

Set committer name and email for all git repositories

	git config --global user.name <name>
	git config --global user.email <email>

While inside a git repo, set the committer name and email for just that repository

	git config user.name <name>
	git config user.email <email>

## Configuration for setting ignore rules

To ignore files (`.gitignore`) may be placed in any directory, this allows fine grained control over ignore rules. If you don't want to commit your ignore files into the repo, use the repo ignore or add `.gitignore` to be ignored. Alternatively, add and commit the `.gitignore` file to include it in the repo and allow others to receive and use the files.

Order of precedence for ignore file hierarchy:

* Command line
* .gitignore (current directory)
* .gitignore (parent directories)
* .git/info/ignore (repo wide ignore rules)
* .gitignore file specified by core.exclude file directive (user / system wide ignore rules)

Allows the ignore file to become part of the repo so other people cloning get the same ignore settings

	<repo>/.gitignore

## Flags for ignore rules

Reverse an earlier ignore rule eg. `!<pattern>` allows the pattern if it was ignored higher up the hierarchy

	!

Wild cards can be used

	*
	**

Example pattern for matching files to ignore

	/<path>/**/*

Items with a hash at the start are comments in the ignore file

	#

Directories to ignore end with a slash

	<path>/<to>/<directory>/

## Example ~/.gitconfig

	[core]
		pager = less -FRSX
		excludesfile = /Users/user/.gitignore
		editor = nano
	[user]
		name = user
		email = user@email.com
	[color]
		ui = auto
	[difftool "chdiff"]
		cmd = chdiff "$LOCAL" "$REMOTE"
	[difftool]
		prompt = false
	[alias]
		st = status
		br = branch
		ba = branch -a
		co = checkout
		ci = commit
		ca = commit -a
		lg = log --date=local
		amend = commit --amend
		unstage = reset HEAD
		glog = log --graph --pretty=format:\"%Cred%h%Creset — %s %Cblue%an%Creset %Cgreen(%cr)%Creset\"

## Example ~/.gitignore

	.DS_Store
	*.log

# Collaborating over the local network

To collaborate with your team, you can allocate a machine to act as a central server, just like SVN. However, there are lots of benefits to using the distributed features of git to collaborate directly between individual developers. For this you'll want to allow access to your git repos.

If you want to establish an interim git repository that others will share, and you will push to, you can use the following steps to set up a git user with git-shell access for collaborators to use. The limitation of this approach is that it treats all users as having the same privileges. More fine grained control requires the use of a system like [Gitolite](https://github.com/sitaramc/gitolite) or [Gitosis](https://wiki.archlinux.org/index.php/Gitosis) for local / behind firewall repos, or [GitHub](http://www.github.com) for public / private, externally hosted repos.

## Setting up a git user for sharing on OS X

Remote login needs to be enabled

	System Preferences -> Sharing -> Remote Login (CHECKED)

Create a new Git User

	System Preferences -> Accounts -> Click the [+] to Create New User

Give the user a name and password (in the following examples we'll using `git` as the user name)

	Full Name: Git
	Password: <password>

After choosing "Create Account", right click on the new account from the Account list on the left and choose "Advanced Options".

	Account name: git
	Login shell: path/to/git-shell
	Home directory: /Users/git
	Leave other values as defaults

For the login shell above, enter the path to the `git-shell` command.

MacPorts: `/opt/local/bin/git-shell`

Homebrew: `/usr/local/bin/git-shell`

Now we can remove all the extra files OSX creates by default in a git users home directory. Make absolutely sure you are in the new user directory before using `rm`.

	$ cd /Users/git
	$ sudo rm -rf *

Copy (or create) your bare git repos to the root of /Users/git, and set the owner to be git

	$ sudo chown -R git myrepo.git

You can now clone from this repo from another machine or location on your computer

	$ git clone git@<machine-address>:myrepo.git
	Password: <git user password>

# Working with external tools

Pipe output from any command into TextMate (or another text editor)

	git diff | mate

A visual view of the commit graph showing the repository history, commits and branches

	gitk

Start and detach instance of gitk

	gitk &

## Utility Commands

Clean up and compact repo

	git gc

# Generating summary reports for a repository

## Git statistics commands

Show all commit messages, grouped together by user

	git shortlog

Show total commit count per user

	git shortlog -s -n

Show total number of files changed, lines inserted and deleted

	git diff <commit> --shortstat

# Checkout GitHub pull request branch locally

In your `.gitconfig` file add the following fetch rule to your origin configuration:

	fetch = +refs/pull/*/head:refs/remotes/origin/pr/*

The fetch all pull requests with:

	git fetch origin

To check out a particular pull request (eg. pr/999)

	git checkout pr/999

# Good git GUI clients

* [Git Tower](http://www.git-tower.com)
* [Source Tree](http://www.sourcetreeapp.com/)
* [GitX](http://gitx.laullon.com/) (Laullon fork)
