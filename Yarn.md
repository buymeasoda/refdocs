# Yarn

Install Yarn

    brew install yarn

Switch yarn to specific version / latest version (yarn 1.x)

    yarn policies set-version <version>
    yarn policies set-version

Switch yarn to specific version / latest version (yarn 2.x)

    yarn set version <version>
    yarn set version latest

## Information

Show yarn version and help

    yarn -v
    yarn help

Show information for a package

    yarn info <package>

Show why a package was installed

    yarn why <package>

## List

List installed packages (local / global)

    yarn list
    yarn global list

List only top level global packages

    yarn list --depth=0
    yarn global list --depth=0

List packages that match pattern

    yarn list --pattern <string>

## Init

Initialize package config in current folder (`-y` or `--yes` for default setup)

    yarn init
    yarn init --yes

Generate new yarn lock file from installed packages

    yarn import

## Install

Install all configured package.json dependencies (dev and production)

    yarn install

Install new dev (`-D`), peer (`-P`), optional (`-O`) package

    yarn add <package>
    yarn add <package>@<version>
    yarn add <package> --dev

Global packages

    yarn global add <package>

## Uninstall

Uninstall package (local, dev, global)

    yarn remove <package>
    yarn remove <package> --dev
    yarn global remove <package>

## Upgrade

Upgrade packages or specific package (local, global) for current major

    yarn upgrade
    yarn upgrade <package>
    yarn global upgrade <package>

Upgrade packages or specific package to latest version regardless of `package.json` version ranges

    yarn upgrade --latest
    yarn upgrade -L
    yarn upgrade -L <package>

Show outdated packages where new version exists

    yarn outdated
    yarn outdated <package>

## Scripts

Run scripts from package.json

    yarn run <script-name>

## Check

Check configured dependencies match lock file

    yarn check

## Global Packages and Cache

Show location of global packages folder

    yarn global bin

Show direction of global cache

    yarn cache dir

List all or matching packages in global cache

    yarn cache list
    yarn cache list --pattern <string>

Clear the global cache

    yarn cache clean

## Configuration

Display the current configuration

    yarn config list

Set configuration values

    yarn config set <key> <value>

Get configuration value

    yarn config get <key>

Delete configuration value

    yarn config delete <key>
