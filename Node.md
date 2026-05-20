# Node

## Information

Show node version

    node -v

## REPL

Start node REPL

    node

Exit node REPL

    .exit

## Scripts

Run script

    node <file>

Run script in watch mode

    node --watch <file>

# Module Versioning

Version numbers (semver)

    <major>.<minor>.<patch>

- Major: Breaking changes, API changes
- Minor: Non-breaking additions and improvements
- Patch: Bug fixes with no API changes

## Dependency symbols

Install same major with latest minor available

    ^<version>

Install same major and minor with latest patch version

    ~<version>

Install the exact specified version

    <version>

Install current latest version always

    *
