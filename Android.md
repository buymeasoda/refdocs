# Android

## Install Prerequisites

Install Java 8

    brew tap AdoptOpenJDK/openjdk
    brew cask install homebrew/cask-versions/adoptopenjdk8

## Recommended Install (via Android Studio)

Install Android Studio

    brew cask install android-studio

Configure Android SDK and Android Platform Tools via Android Studio

- Run Android Studio
- Section "Custom" setup option

Specify the following options during install

- Android SDK (Build and Command Line Tools)
- Android SDK Platform
- Performance (Intel HAXM)
- Android Virtual Device

## Alternate Install (via Homebrew)

Install Android SDK and Android Platform Tools via Homebrew

    brew cask install android-sdk android-platform-tools

Add SDK to path (Bash / ZDH)

    export ANDROID_SDK_ROOT="$(brew --prefix)/share/android-sdk"

Add SDK to path (Fish)

    set -x ANDROID_SDK_ROOT (brew --prefix)/share/android-sdk

Create repositories configuration file (if one does not exist)

    touch ~/.android/repositories.cfg

Note: For commands that present MacOS "Unidentified Developer" dialog - Locate the command in Finder, right click and choose "Open" to approve running command

## Configure Environment

Android SDK path for Android Studio install

    $HOME/Library/Android/sdk

Android SDK path for Homebrew install

    $(brew --prefix)/share/android-sdk

Add Android Tools to path (example bash configuration for use with Android Studio install)

    export ANDROID_HOME=<android-sdk-path>
    export PATH=$PATH:$ANDROID_HOME/emulator
    export PATH=$PATH:$ANDROID_HOME/tools
    export PATH=$PATH:$ANDROID_HOME/tools/bin
    export PATH=$PATH:$ANDROID_HOME/platform-tools

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

## Emulator

Emulator command manages loading available AVDs (AVD: Android Virtual Devices) into Android Emulator

Emulator AVD location

    ~/.android/avd/

List available Android emulators

    emulator -list-avds

Run Android emulator

    emulator @<avd-name>
    emulator @Nexus_5X_Nougat_

## Android Debug Bridge

Show list of available android devices

    adb devices

Show all crash logs

    adb logcat

Show only errror logs

    adb logcat '*:E'

Configure reverse socket connection

    adb reverse tcp:<port> tcp:<port>

## Add Test Media

- Drag image to emulator
- Open: Settings (app) -> Storage -> Internal Storage -> Explore
- View the image, and add to Gallery
