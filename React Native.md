# React Native

## Setup

Development setup

- [Xcode](https://developer.apple.com/xcode/)
- [Xcode Command Line Tools](https://developer.apple.com/download/more/)
- [Android Studio](https://developer.android.com/studio/)
- [Node](https://nodejs.org/en/)
- [Watchman](https://facebook.github.io/watchman/)
- [OpenJDK](https://adoptopenjdk.net/)

Install base environment

    brew install node
    brew install watchman
    brew tap AdoptOpenJDK/openjdk
    brew cask install adoptopenjdk8

Install Android environment

    brew cask install android-studio
    brew cask install android-sdk

Install iOS environment

- Manually install Xcode via the Apple App Store

Install React Native command line tool

    npm install -g react-native-cli

## Create Project

Initialize new project

    react-native init <app-name>
    cd <app-name>

## Run Metro

Start Metro server (and optionally reset cache)

    react-native start
    react-native start --reset-cache

## Install App

Build, install and run app on iOS Simulator / Android Emulator

    react-native run-ios
    react-native run-android

## Install Packages

Install package for use in the app

    npm install <package-name> --save

Link native dependencies and update native build files (then rebuild)

    react-native link <package-name>

# Android

## Emulator

List available Android emulators

    emulator -list-avds

Run Android emulator

    emulator @<avd-name>
    emulator @Nexus_5X_Nougat_

Show react native debug menu

    CMD + M

Allow React Native debugger menu to work with emulator (search settings for "draw over")

    Settings -> Apps -> Your-App -> Advanced -> Draw over other app -> Permit

## Unable to connect to remote debugger

Open in browser first

    http://localhost:8081/debugger-ui/

Configure reverse socket connection for react native server

    adb reverse tcp:8081 tcp:8081
