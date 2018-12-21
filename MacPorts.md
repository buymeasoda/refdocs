# MacPorts

Reference for working with [MacPorts](http://www.macports.org/).

## MacPorts help

Manual for ports

    man port

Location of installed ports

    /opt

## Update MacPorts

Upgrade mac ports and the port list

    sudo port selfupdate

## Search for ports and display port info

List all available ports

    port list

Search for a port name

    port search <name>

Show information about a particular port

    port info <name>

Show the variants (additional components) that can be installed with a port

    port variants <name>

## Install / uninstall ports

Install an item (use `+<variant>` or `-<default>` to add or remove additional components)

    sudo port install <name>

Remove an installed item (will fail if item has dependants, override with `-f` flag)

    port uninstall <name>

Remove all inactive ports

    port uninstall inactive

## Upgrade installed ports

Show a list of outdated items, their installed version and the available MacPorts version

    port outdated

Update the old items and remove the old version

    sudo port -u upgrade outdated

Update the old items (keeping the original version and deactivating it)

    sudo port upgrade outdated

Upgrade an installed item (add `-n` to not update dependencies, `-u` to remove old version)

    port upgrade <name>

## Show installed port information

Show all installed items, their versions and activation status

    port installed

Show details about an installed item

    port installed <name>

Show active installed ports

    port list active

Show inactive installed ports

    port list inactive

Show items that depend on the named item (eg. `port dependents curl`):

    port dependents <name>

Show dependencies the item has

    port deps <name>

Show the files that were installed by a port install

    port contents <name>

## Clean up MacPorts

Clean up all files (work, dist, archive) for all ports

    sudo port clean --all all

Clean up selected file types (work, dist, archive) for specified port

    sudo port clean --<type> <name>
