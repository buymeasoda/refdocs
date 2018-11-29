
# Mercurial

Show summary of a particular commit

	hg log -r <rev>

Show diff from log item

	hg log -p -r <rev>

Show full log message

	hg log -v -r <rev>

## General information

Get an overview of the current repository state

	hg summary

## Undoing changes

Revert changes to an uncommitted file (return to clean, pre-edit state)

	hg revert <file>

Revert a file to an earlier version in history

	hg revert -r <revset> <file>

Change most recent commit message

	hg commit --amend
	hg ci --amend
