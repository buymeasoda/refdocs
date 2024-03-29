# MacOS

## Information

Show operating system version

    sw_vers

View and set macOS system settings

    sudo systemsetup

## Disk Utility

List available internal / external disk volumes

    diskutil list

Show / delete APFS snapshot for volume

    diskutil apfs listSnapshots <volume>
    diskutil apfs deleteSnapshot <volume> -name <snapshot-name>

## Power Metrics

Show all system power / hardware metrics (CPU, GPU, Network etc)

    sudo powermetrics

Show specific power metrics (eg. `smc` for System Management Controller stats)

    sudo powermetrics --samplers smc

## Power Settings

Show current power settings in use

    pmset -g

Show power information for battery and ac adapter

    pmset -g batt
    pmset -g ac

List sleep and wake counts since boot

    pmset -g stats

Output all power setting stats

    pmset -g everything

## System Integrity Protection

Show System Integrity Protection status

    csrutil status

Enable / Disable System Integrity Protection (requires Safe Mode to run)

    csrutil enable
    csrutil disable

## System and Kernel Extensions

List user daemons, agents and XPC services (list all / list third party only)

    launchctl list
    launchctl list | grep -v com.apple

List system daemons, agents and XPC services

    sudo launchctl list

List system extensions

    systemextensionsctl list

List kernel extensions (list all / list third party only)

    kextstat
    kextstat | grep -v com.apple

Unload kernel extension

    sudo kextunload <extension.kext>

Location of kernel extension files

    /System/Library/Extensions
    /Library/Extensions

## System Paths

Location of default macOS system `$PATH` entries

	/etc/paths
	/etc/paths.d

## System Profiler

Report detailed system configuration (`-detailLevel` mini, basic, full)

    system_profiler

List all available profile data types

    system_profiler -listDataTypes

System hardware and software summary

    system_profiler SPHardwareDataType
    system_profiler SPSoftwareDataType

Other system information (storage, memory, display, audio, network, battery, USB, bluetooth)

    system_profiler SPStorageDataType
    system_profiler SPMemoryDataType
    system_profiler SPDisplaysDataType
    system_profiler SPAudioDataType
    system_profiler SPNetworkDataType
    system_profiler SPPowerDataType
    system_profiler SPUSBDataType
    system_profiler SPBluetoothDataType

## Troubleshooting

Relaunch Mac OS features

    killall Dock
    killall Finder
    killall ControlStrip

## Rosetta

Show Rosetta process if installed and available

    pgrep oahd

## Clipboard

Copy input content to the clipboard

    pbcopy

Examples for copy to clipboard from files

    pbcopy < <file>
    cat <file> | pbcopy

Outputs the current contents of the clipboard

    pbpaste

## Spotlight

Search spotlight file contents and names (or file name only via `-name`)

    mdfind <search-a> <search-b>
    mdfind -name <search>

Filter for specific file type (eg. `image`)

    mdfind kind:<type>
    mdfind kind:image

Limit search to specific directory

     mdfind -onlyin <directory> <search>

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

## Extended Attributes

Show macOS extended attributes for file

    xattr -l <file>

## Locked Files

macOS allows locking files via Finder to prevent accidental deletion and editing (Note: This setting prevents changes via `sudo`)

    File -> Get Info -> Locked

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

## Quick Look

Open quick look for file

    qlmanage -p <file>

List all registered quick look plugins (includes ones provided internally by apps)

    qlmanage -m

Directories for stand along quick look providers

    /Library/QuickLook
    ~/Library/QuickLook

## macOS Firewall Settings

List firewall rules

    sudo /usr/libexec/ApplicationFirewall/socketfilterfw --listapps

Add or remove app from firewall rules

    sudo /usr/libexec/ApplicationFirewall/socketfilterfw --add <app-path>
    sudo /usr/libexec/ApplicationFirewall/socketfilterfw --remove <app-path>

Block or unblock app in firewall rules

    sudo /usr/libexec/ApplicationFirewall/socketfilterfw --blockapp <app-path>
    sudo /usr/libexec/ApplicationFirewall/socketfilterfw --unblockapp <app-path>

## Security and Privacy Permissions

Manage associated app permissions (listed in System Preferences -> Security & Privacy -> Privacy)

Reset app access permissions for category

    tccutil reset <app-category>

Reset specific app access permissions for category

    tccutil reset <app-category> <app-bundle-id>

Available app categories

- `Accessibility`
- `AddressBook`
- `AppleEvents`
- `Calendar`
- `Camera`
- `Microphone`
- `Photos`
- `Reminders`
- `ScreenCapture`
- `SystemPolicyAllFiles`
- `SystemPolicyDesktopFolder`
- `SystemPolicyDeveloperFiles`
- `SystemPolicyDocumentsFolder`
- `SystemPolicyDownloadsFolder`
- `SystemPolicyNetworkVolumes`
- `SystemPolicyRemovableVolumes`
- `SystemPolicySysAdminFiles`

## SF Mono Fonts

Xcode SF Mono font assets

    /Applications/Xcode.app/Contents/SharedFrameworks/DVTKit.framework/Versions/A/Resources/Fonts/

Terminal SF Mono font assets

    /Applications/Utilities/Terminal.app/Contents/Resources/Fonts
