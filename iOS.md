# iOS

## Xcode

Install command line developer tools

    xcode-select --install

Show selected command line tools

    xcode-select -p

Reset to default command line tools path

    xcode-select --reset

Switch selected version

    sudo xcode-select -s /Applications/Xcode<xxxx>.app

## Simulator

Open simulator app

    open /Applications/Xcode.app/Contents/Developer/Applications/Simulator.app/

Show xcrun simulator commands

    xcrun simctl help

Show list of simulators (Sample device ID: `12AB3C4D-A12B-12A3-12AB-A12B34C5678D`)

    xcrun simctl list

Get device ID for booted simulators

    xcrun simctl list | grep -i booted

Boot / shutdown simulator device ID

    xcrun simctl boot <device-id>
    xcrun simctl shutdown <device-id>

## Install IPA to Simulator

Rename from ipa to .zip and unzip

    mv YourApp.ipa YourApp.zip
    unzip YourApp.zip

Install via xcrun to the booted device or specified device ID

    xcrun simctl install booted path/to/Your.app
    xcrun simctl install <device-id> path/to/Your.app

## Using FBSimulatorControl

Install

    brew tap facebook/fb
    brew install fbsimctl

List current simulators

    fbsimctl list

Load simulator

    fbsimctl <device-id> boot

Shut down simulators

    fbsimctl shutdown

Clean up old simulators

    fbsimctl --delete-all create --all-missing-defaults

Record simulator or device (CTRL + C to stop recording)

    fbsimrecord
    fbdevicerecord

## Simulator Crash Logs

Show iOS simulator app crash logs

- Open Console.app
- Navigate to `~/Library/Logs -> DiagnosticReports`

Manual logs will show in Console.app when viewing the related simulator from "Devices"

    NSLog(@"...");
