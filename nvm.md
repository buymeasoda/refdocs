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

Install specific node release (or latest LTS version)

    nvm install <version>
    nvm install --lts

Install node version specified in project via `.nvmrc` file

    npm install

## Switching Versions

Switch to system node version

    nvm use system

Switch to a specific node version (or latest LTS version)

    nvm use <version>
    nvm use --lts

Use node version specified in project via `.nvmrc` file

    npm use

## Run Node Commands

Run node scripts for specific versions directly

    nvm run <version> <command>
