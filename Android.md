# Android

## Install Prerequisites

Install Java JDK 17

    brew tap homebrew/cask-versions
    brew install --cask zulu17

Notes

- For any commands below that present MacOS "Unidentified Developer" dialog - Locate the command in Finder, right click and choose "Open" to approve running command
- Shell environment configuration are shown using fish shell commands

## Recommended Install (via Android Studio)

Install Android Studio

    brew install --cask android-studio

Configure Android SDK and Android Platform Tools via Android Studio

- Run Android Studio

Specify the following options during install

- Android SDK (Build and Command Line Tools)
- Android SDK Platform
- Android Virtual Device

## Alternate Install (via Homebrew)

Install Android SDK and Android Platform Tools via Homebrew

    brew install --cask android-sdk android-platform-tools

## Check and Configure Environment

Show installed and active Java version

    java --version

### Java Home

Show Java Home path and version (`-V` to show all available versions)

    /usr/libexec/java_home
    /usr/libexec/java_home -V

Output path for specific Java version (can be exact or major version)

    /usr/libexec/java_home -v <version>
    /usr/libexec/java_home -v 11
    /usr/libexec/java_home -v 17

Set Java Home path for JDK (determined from `java_home` output)

    set -x JAVA_HOME <java-home-path>

### Android SDK

Android SDK path for Android Studio install

    $HOME/Library/Android/sdk

Android SDK path for Homebrew install

    $(brew --prefix)/share/android-sdk

Android Home path for sdk

    set -x ANDROID_HOME $HOME/Library/Android/sdk

Add Android Tools to path

    fish_add_path --path --append $ANDROID_HOME/emulator
    fish_add_path --path --append $ANDROID_HOME/platform-tools

## Emulator

Emulator command manages loading available AVDs (AVD: Android Virtual Devices) into Android Emulator

Emulator AVD location

    ~/.android/avd/

List available Android emulators

    emulator -list-avds

Run Android emulator

    emulator @<avd-name>
    emulator @Nexus_5X_Nougat_

Alternative run command

    emulator -avd <avd-name>

Output more verbose logs

    emulator @<avd-name> -verbose

Output detailed real time logs

    emulator @<avd-name> -logcat '*:v'

## Android Debug Bridge (ADB)

Show list of available android devices

    adb devices

Start adb shell for connected device (interact with device filesystem)

    adb shell

Output path to device storage eg. `sdcard/` (while in device shell)

    echo $EXTERNAL_STORAGE

Copy files from device storage (eg. Device camera photos to Downloads folder)

    adb pull <remote> <local>
    adb pull sdcard/DCIM/Camera ~/Downloads

Transfer files to device storage

    adb push <local> <remote>

Install APK on device or emulator (enable `USB Debugging` via device `Developer Options` settings for physical devices)

    adb install <apk-file>

## ADB Key Management

Create public key from private key (inside `~/.android/`)

    adb pubkey adbkey > adbkey.pub

Output signature of public key (for checking USB Debugging match)

    cat ~/.android/adbkey.pub | base64 --decode | md5

## ADB Device Logs

Show all crash logs

    adb logcat

Show only errror logs

    adb logcat '*:E'

Configure reverse socket connection

    adb reverse tcp:<port> tcp:<port>

## ADB Device Events

Send key event to device (eg. `KEYCODE_MENU` for Menu Key)

    adb shell input keyevent <event-id>
    adb shell input keyevent 82

## Add Test Media

- Drag image to emulator
- Open: Settings (app) -> Storage -> Internal Storage -> Explore
- View the image, and add to Gallery

## Manage SDKs

SDK command for managing Android SDK packages

    sdkmanager

List SDK versions available for download and install (`--verbose` for added details)

    sdkmanager --list
    sdkmanager --list --verbose

Update installed SDK version

    sdkmanager --update

Read and acknowledge SDK licenses

    sdkmanager --licenses

Install latest Android platforms tools

    sdkmanager "platform-tools"

Install Android version platform (eg. Android API 29)

    sdkmanager "platforms;android-<api-version>"
    sdkmanager "platforms;android-29"

Install commands can be combined

    sdkmanager "platform-tools" "platforms;android-29"

Install system image (eg. Android API 29)

    sdkmanager "<sdk-variant>"
    sdkmanager "system-images;android-29;google_apis;x86"

## AVD Manager (Android Virtual Devices)

Manage virtual devices and API targets

- AVD: Virtual device (combination of hardware device and API target)
- Device: Physical hardware device emulator (eg. Pixel phone)
- Target: Android API platform target version (eg. API 29 = Android 10 / Android Q)

List all manager entries across categories

    avdmanager list

Lists only entries for AVD, Devices or Target categories

    avdmanager list avd
    avdmanager list device
    avdmanager list target

Delete existing Android Virtual Device

    avdmanager delete avd --name <avd-name>

## Create AVD

AVD Configuration

- Name: Arbitrary defined name used to refer to AVD via commands
- Device: Hardware device profile (eg. "pixel")
- Package: System and OS target configuration (eg. Android 29)

Create AVD

    avdmanager create avd --name <name> --device "<device>" --package  "<configuration>"

Example AVD for Pixel device running Android API 29 (x86)

    avdmanager --verbose create avd --name Pixel_API_29 --device "pixel" --package  "system-images;android-29;google_apis;x86" --abi "x86"
