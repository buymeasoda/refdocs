
# Homebrew

## Install multiple versions of the same module

Install the latest version of a module

	brew install <module>

Keep the old version after install

	brew unlink <module>

## Manage multiple versions of the same module

Show available homebrew versions of a particular module

	brew versions <module>

Switch to a specific version

	git checkout <hash> <path>

Switch between version of a module, cleaning up state

	brew switch <module> <version>

Remove an installed module

	brew uninstall <module>
