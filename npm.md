# npm

## Information

Search for node packages

    npm search <package>

Show information for a package

    npm info <package>

## List

List installed packages (local / global)

    npm list
    npm list --global

List only top level global packages

    npm list --depth=0
    npm list --global --depth=0

## Init

Initialize package config in current folder (`-y` or `--yes` for default setup)

    npm init
    npm init --yes

## Install

Install package (local, local dev only, global)

    npm install <package>
    npm install --save-dev <package>
    npm install --global <package>

## Uninstall

Uninstall package (local, global)

    npm uninstall <package>
    npm uninstall --global <package>

## Update

Update all packages or specific package (local, global)

    npm update
    npm update <package>
    npm update --global
    npm update --global <package>

## Command Aliases

- `npm i` (`npm install`)
- `-g` (`--global`)
- `-D` (`--save-dev`)
