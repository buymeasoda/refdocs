# Homebrew

## Information

Find formula

    brew search <formula>

Show information for a specific formula

    brew info <formula>

Show installed formula excluding dependencies

    brew leaves

Show all installed formula including dependencies

    brew list

## Install

Install/Uninstall formula

    brew install <formula>
    brew uninstall <formula>

Temporarily disable an installed formula

    brew unlink <formula>

## Update

Fetch newest Homebrew version and formulae

    brew update

Upgrade existing outdated formulae

    brew upgrade

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

## Cask

Add cask to homebrew

    brew tap caskroom/cask

Update casks

    brew cask upgrade

Install cask

    brew cask install <cask>

List installed casks

    brew cask list
