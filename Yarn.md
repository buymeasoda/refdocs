# Yarn

Install Yarn

    brew install yarn

## Information

Show yarn version and help

    yarn -v
    yarn help

Show information for a package

    yarn info <package>

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

Update all packages or specific package (local, global)

    yarn upgrade
    yarn upgrade <package>
    yarn global upgrade <package>

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
