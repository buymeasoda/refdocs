# MacOS

## Clipboard

Copy content to the clipboard (eg. cat file.txt | pbcopy, copies contents of file.txt to the clipboard)

    pbcopy

Outputs the current contents of the clipboard

    pbpaste

## App Store

List available software updates

    softwareupdate -l

Install specific software update

    softwareupdate -i <package>

Install all available software updates

    softwareupdate -ia

Force App Store updater to remove pending updates (useful if update is in looped state and not installing)

    softwareupdate --clear-catalog
