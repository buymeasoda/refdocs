# iOS

## Manage Xcode

Show selected Xcode

    xcode-select -p

Switch selected version

    sudo xcode-select -s /Applications/Xcode<xxxx>.app

## Manage Simulators

Install `fbsimctl`

    brew tap facebook/fb
    brew install fbsimctl

List current simulators

    fbsimctl list

Load simulator (Sample device ID: 12AB3C4D-A12B-12A3-12AB-A12B34C5678D)

    fbsimctl <device-id> boot

Shut down simulators

    fbsimctl shutdown

Clean up old simulators

    fbsimctl --delete-all create --all-missing-defaults

## Screencast Recording

Record simulator or device (CTRL + C to stop recording)

    fbsimrecord
    fbdevicerecord

## Install IPA to Simulator

Rename from ipa to .zip and unzip

    mv YourApp.ipa YourApp.zip
    unzip YourApp.zip

Get device ID for running iOS Simulator

    xcrun simctl install booted path/to/Your.app
    xcrun simctl list | grep -i booted

Install via xcrun

    xcrun simctl install <device-id> path/to/Your.app
