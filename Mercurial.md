# Mercurial

## Configuration

Show mercurial configuration (`--debug` includes file paths)

    hg config
    hg config --debug

Edit mercurial config (Scope: local `-l`, user `-e`, global `-g`)

    hg config <scope>

## General Workflow

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

Info about a specific file or commit (summary / diff)

    hg log <path>
    hg log -p <path>
    hg log -r <rev-id>
    hg log -p -r <rev-id>

Example history variations (`-f` starts at your current commit and moves backwards)

    hg log -f
    hg log --graph
    hg log --style=compact

Show a summary of the files that changed for a rev set

    hg status --change <rev-id>

## Search code history

Grep for a specific string in file history commit messages or diffs

    hg log <path> | grep <search-string>
    hg log -p <path> | grep <search-string>

Grep mercurial history over time range for changes (eg. for last week `"date(-7)"`)

    hg histgrep -r "<time-range>" "<search-string>" <path>

## Amend Changes

Amend an existing commit with current changes (`-m` to update commit message)

    hg amend
    hg amend -m "<new-message>"

To amend and change the commit message via editor

    hg commit --amend
    hg ci --amend

## Purge Changes

Abandon changes and update to clean master state

    hg up master --clean

Remove untracked files (`--all` to purge everything including ignored temp files)

    hg purge
    hg purge --all

## Revert Changes

Revert changes to an uncommitted file (return to clean, pre-edit state)

    hg revert <file>

Revert a file to an earlier version in history (`.~1` for current parent)

    hg revert -r <rev-id> <file>
    hg revert -r .~1 <file>

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

## Reorder, Combine or Delete Commits

Interactively reorder, combine, or delete commits

    hg histedit

Remove commit completely

    hg strip <rev-id>

## Rebase Commits

Move revision and decedents (commits below it not on target branch) to destination

    hg rebase –d <destination> –b <rev-id>

Move revision and ancestors (commits above it) to destination

    hg rebase –d <destination> –s <rev-id>

Recover from a failed rebase or merge

    hg rebase --abort

Resolve merge conflict and continue rebase (after manual fix)

    hg resolve --mark <file>
    hg rebase --continue

## Cherry Pick Commits

Cherry pick and move revisions onto destination (specify multiple revisions with `"<rev-id1> + <rev-id2>"`)

    hg rebase –d <destination> –r <rev-id>
    hg rebase –d master –r "bug3765 + 530273"

## Bisect

Reset bisect state to begin a fresh bisect, and mark the current state as bad

    hg bisect --reset
    hg bisect --bad

Choose a known good point as close to now as possible (eg. 7 days ago) and mark it as good

    hg bisect --good 'first(date(-7) and public())'

Check the state and mark as good or bad until the problem revision is found

    hg bisect --good
    hg bisect --bad

End bisect and return to the current checkout revision

    hg bisect --reset

Bisect and run unit test per check (First reset and mark good/bad commits)

    hg bisect --command '<test-commands>'

## Sparse Checkout

Check current sparse config

    hg sparse

Add sparse configs

    hg sparse --enable-profile <sparse-profile>

Refresh sparse checkout

    hg sparse --refresh

## Backout Commits

Backout revisions one at a time in reverse order, from newest (top) commit to earliest (bottom) commit

    hg backout -r <rev>

Squash all backed out revisions to a single commit

    hg checkout -r <top-rev>
    hg squash -r <bottom-rev>

Update the commit message with additional details including message, summary, test plan, reviewed by (self)

    hg commit --amend

## Commit ID

Commit IDs contain local and global unique identifiers separated by `:`

    xxxxlocal:xxxxglobal
