# MacOS

## Information

Show operating system version

    sw_vers

Report detailed system configuration

    system_profiler

View and set macOS system settings

    sudo systemsetup

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

## Screen Capture

Capture entire screen to file (default format: PNG)

    screencapture <file>

Activate interactive screen capture mode (CTRL clipboard, SPACE selection/window, ESC cancel)

    screencapture -i <file>

Other useful screen capture options

- `-t <format>` png, pdf, jpg
- `-c` Send to clipboard
- `-P` Send to Preview app
- `-S` Capture screen instead of window
- `-o` Exclude window shadow
- `-T <secs>` Capture after elapsed seconds

## Audio

Show audio file information

    afinfo <file>

Play audio file

    afplay <file>

Play audio file with volume (`-v`), playback rate (`-r`) and duration in seconds (`-t`)

    afplay <file> -v <volume> -r <rate> -t <time>

Convert audio file format

    afconvert -f <file-format> -d <data-format> -b <bit-rate> <input-file> <output-file>

Example converting audio file from wav to mp3 at 128kbps

    afconvert -f mp4f -d aac -b 128000 input.wav output.mp3

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

## Quick Look Plugins

List all registered quick look plugins (includes ones provided internally by apps)

    qlmanage -m

Directories for stand along quick look providers

    /Library/QuickLook
    ~/Library/QuickLook

## SF Mono Fonts

Xcode SF Mono font assets

    /Applications/Xcode.app/Contents/SharedFrameworks/DVTKit.framework/Versions/A/Resources/Fonts/

Terminal SF Mono font assets

    /Applications/Utilities/Terminal.app/Contents/Resources/Fonts
