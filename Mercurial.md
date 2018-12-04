
# Mercurial

##  General Workflow

Create new mercurial repository

	hg init
	hg init <folder>

Show status of changed files in working directory

	hg status
	hg st

Show status relative to current folder or specified path

	hg status .
	hg status <path>

Add untracked files (all / specific)

	hg add
	hg add <file>

Show diff of pending changes since last commit

	hg diff

Commit current changes

	hg commit -m "<message>"
	hg ci -m "<message>"

Pull in latest changes (fetches only, does not update working copy)

	hg pull

## Summary and History Information

Repository summary, root directory and branch heads

	hg summary
	hg root
	hg heads

Show last commit diff

	hg show

Show commit history (summary / verbose / diffs)

	hg log
	hg log -v
	hg log -p

Info about a specific commit (summary / diff)

	hg log -r <rev-id>
	hg log -p -r <rev-id>

Example history variations (`-f` starts at your current commit and moves backwards)

	hg log -f
	hg log --graph
	hg log --style=compact

## Amend Changes

Amend an existing commit with current changes (`-m` to update commit message)

	hg amend
	hg amend -m "<new-message>"

To amend and change the commit message via editor

	hg commit --amend
	hg ci --amend

## Purge Changes

Remove untracked files (`--all` to purge everything including ignored temp files)

	hg purge
	hg purge --all

## Revert Changes

Revert changes to an uncommitted file (return to clean, pre-edit state)

	hg revert <file>

Revert a file to an earlier version in history

	hg revert -r <rev-id> <file>

## Squash Commits

Fold the current commit to the specified revision

	hg fold --from -r <rev-id>

Combine the current commit with the previous commit

	hg fold --from .^

## Split Diff

Check out the diff to split and uncheck the items you want to move to the next commit

	hg split

## Bookmarks

Add new bookmark to current commit

	hg bookmark <bookmark>
	hg book <bookmark>

Add bookmark to specific commit

	hg book -r <rev-id> <bookmark>

Show current bookmarks (local and all)

	hg book
	hg book -a

Delete existing bookmark

	hg book -d <bookmark>

Rename existing bookmark

	hg book --rename <old-bookmark> <new-bookmark>

Move bookmark label (`-f` is force, `-r` is for revision identifier)

	hg book -f -r <destination-rev-id> <bookmark>

Show a list of new incoming remote bookmarks

	hg incoming -B

## Sparse Checkout

Check current sparse config

	hg sparse

Add sparse configs

	hg sparse --enable-profile <sparse-profile>

Refresh sparse checkout

	hg sparse --refresh
