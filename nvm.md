# Node Version Manager

## Information

List currently installed node versions

    nvm ls

List available remote node versions for install

    nvm ls-remote

Show current active node version

    nvm current

Show path for specified node version

    nvm which <version>

## Installing Versions

Install latest node release

    nvm install node

Install specific node release (eg. LTS or version number)

    nvm install --lts
    nvm install <version>
    nvm install v16

Install node version specified in project via `.nvmrc` file

    npm install

## Switching Versions

Switch to system node version

    nvm use system

Switch to a specific node version (eg. LTS or version number)

    nvm use --lts
    nvm use <version>
    nvm use v16

Use node version specified in project via `.nvmrc` file

    npm use

## Run Node Commands

Run node scripts for specific versions directly

    nvm run <version> <command>
