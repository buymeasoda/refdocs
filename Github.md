# GitHub

## Open Source Contributions

Create and submit pull requests to GitHub hosted open source projects.

## Fork and Clone

Fork project repo via GitHub UI and clone fork to local development machine.

    git clone git@github.com:<user>/<fork>

## Configure Repo

Add original project repo as remote upstream

    git remote add upstream <original-repo>

Set email configuration for project commits

    git config user.email "<email>"

## Commit and Update

Make changes, commit and push to your fork, then update local fork to latest upstream repo state.

    git fetch upstream
    git checkout master
    git merge upstream/master

## Create Pull Request

Create pull request via GitHub UI for changes.
