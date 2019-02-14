# npm

## Information

Show npm version and help

    npm -v
    npm help

Search for node packages

    npm search <package>

Show information for a package

    npm info <package>

Show location of global modules folder

    npm root --global

Open home page or github repo for package

    npm home <package>
    npm repo <package>

Check if npm requires updating

    npm outdated -g npm

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

Install all configured package.json dependencies (dev and production)

    npm install

Install configured package.json dependencies for specific mode

    npm install --dev
    npm install --production

Install new local package

    npm install <package>
    npm install --save <package>

Install new dev (`-D`), prod (`-P`), optional (`-O`) or global (`-g`) package

    npm install --save-dev <package>
    npm install --save-prod <package>
    npm install --save-optional <package>
    npm install --global <package>

Install without saving reference in package.json

    npm install --no-save <package>

Install specific version

    npm install <package>@<version>

## Uninstall

Uninstall package (local, dev, global)

    npm uninstall <package>
    npm uninstall --save-dev <package>
    npm uninstall --global <package>

Remove packages not declared in package.json

    npm prune

## Update

Update all packages or specific package (local, global)

    npm update
    npm update <package>
    npm update --global
    npm update --global <package>

Show outdated packages

    npm outdated

## Scripts

package.json default script options

    npm start
    npm stop
    npm test

Other scripts require "run"

    npm run <script-name>

When executing scripts `pre` and `post` versions will automatically run if defined

    pre<script-name>
    post<script-name>

## Command Aliases

- `npm i` (`npm install`)
- `-g` (`--global`)
- `-D` (`--save-dev`)

# Manage package.json init defaults

Set default init config values

    npm config set init-<field> "<value>"
    npm set init-<field> "<value>"

Show default init config values

    npm config get init-<field>
    npm get init-<field>

Delete default init config values

    npm config delete init-<field>
