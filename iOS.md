# iOS

## Xcode

Show Xcode app / build version

    xcodebuild -version

Install command line developer tools

    xcode-select --install

Show selected command line tools

    xcode-select -p

Reset to default command line tools path

    xcode-select --reset

Switch selected version

    sudo xcode-select -s /Applications/Xcode<xxxx>.app

List available developer tools (location via `xcode-select -p` eg. Xcode)

    ls -l /Applications/Xcode.app/Contents/Developer/usr/bin/

Xcode launch helper (command line tool for opening Xcode documents)

    xed

## Simulator

Open simulator app

    open -a simulator

Open simulator app (direct path alternative)

    open /Applications/Xcode.app/Contents/Developer/Applications/Simulator.app/

## Gestures

- Position touch gesture points using OPTION / SHIFT
- Engage touch by pressing (eg. click and hold mouse / trackpad)

Show touch gesture UI (scale distance between touches with mouse / trackpad)

    OPTION

Show touch gesture UI and move touches at set scale (release shift to adjust scale distance)

    OPTION then SHIFT

Toggle touch gesture UI to remain active with being engaged

    OPTION then SHIFT (then RELEASE)

Re-engage SHIFT to move touch points and hold OPTION to adjust scale distance

## Simulator Commands

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

## iOS Development Bridge (idb)

- https://fbidb.io/

Install

    brew install facebook/fb/idb-companion
    pip install fb-idb

If `fb-idb` fails to install globally use `--user` install and add user location to path

    pip install fb-idb --user

List current simulators (shows device udid)

    idb list-targets

Load simulator

    idb boot <udid>

Shut down simulators

    idb shutdown <udid>

## Simulator Logs

Show iOS simulator app crash logs

- Open Console.app
- Navigate to "Diagnostic Reports"

Manual logs will show in Console.app when viewing the related simulator from "Devices"

    NSLog(@"...");

Open system log from simulator (Shortcut: `CMD + /`)

    Debug -> Open System Log...

## SDK Configuration

Show current iPhone OS SDK path

    xcrun -k --sdk iphoneos --show-sdk-path

When no SDK is selected switch Xcode versions

    sudo xcode-select --switch /Applications/Xcode.app

## Cocoapods

Install cocoapods

    brew install cocoapods

Check pod version

    pod --version
