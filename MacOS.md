# MacOS

## Troubleshooting

Relaunch Mac OS features

    killall Dock
    killall Finder
    killall ControlStrip

## Clipboard

Copy content to the clipboard (eg. cat file.txt | pbcopy, copies contents of file.txt to the clipboard)

    pbcopy

Outputs the current contents of the clipboard

    pbpaste

## App Store

Show software update history (`--all` includes initial app installs)

    softwareupdate --history
    softwareupdate --history --all

List available software updates

    softwareupdate -l

Install specific software update

    softwareupdate -i <package>

Install all available software updates (`-r` only recommend updates, `-R` auto restart if required)

    softwareupdate -ia

Download update or cancel in progress download without installing

    softwareupdate -d <package>
    softwareupdate -e <package>

Force App Store updater to remove pending updates (useful if update is in looped state and not installing)

    softwareupdate --clear-catalog

Ignore specific package update

    softwareupdate --ignore <package>

Clear ignored packages list

    softwareupdate --reset-ignored

## System Defaults

List defaults preference files (or list as one per line)

    defaults domains
    defaults domains | tr ',' '\n'

Show current defaults for domain

    defaults read <domain>

Show expected type for domain setting

    defaults read-type <domain> <key>

Set specific domain key

    defaults write <domain> <key> <value>
    defaults write <domain> <key> -<type> <value>
