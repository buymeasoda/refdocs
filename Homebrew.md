# Homebrew

## Information

Find formula or cask

    brew search <name>
    brew search --cask <name>

Show information for a specific formula or cask

    brew info <name>
    brew info --cask <name>

Show installed formula excluding dependencies

    brew leaves

Show all installed formula or casks including dependencies

    brew list
    brew list --cask

Show all installed formula with associated dependencies

    brew deps --installed

Show all installed formula with associated dependencies in a tree

    brew deps --installed --tree

## Install

Install formula or cask

    brew install <name>
    brew install --cask <name>

Uninstall formula or cask

    brew uninstall <name>
    brew uninstall --cask <name>

Temporarily disable an installed formula

    brew unlink <formula>

## Update

Fetch newest Homebrew version and formulae

    brew update

Upgrade existing outdated formulae or casks

    brew upgrade
    brew upgrade --cask

Remove outdated downloads and old installed versions of formulae

    brew cleanup

## Versions

Switch between versions of a formula

    brew switch <formula> <version>

## Tap

List tapped repositories

    brew tap

Add or remove tap repository

    brew tap <tap-name>
    brew untap <tap-name>
