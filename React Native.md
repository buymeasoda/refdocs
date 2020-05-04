# React Native

## Setup Overview

Development Tools

- [Xcode](https://developer.apple.com/xcode/)
- [Xcode Command Line Tools](https://developer.apple.com/download/more/)
- [Cocoapods](https://cocoapods.org/)
- [Android Studio](https://developer.android.com/studio/)
- [Node](https://nodejs.org/en/)
- [Watchman](https://facebook.github.io/watchman/)
- [OpenJDK](https://adoptopenjdk.net/)

## Base Setup

Install base environment

    brew install node
    brew install watchman

## Android Setup

Install Java 8 JDK

    brew tap AdoptOpenJDK/openjdk
    brew cask install adoptopenjdk8

Install Android Studio

    brew cask install android-studio

Android environment instructions

- https://reactnative.dev/docs/environment-setup
- Refer to: React Native CLI Quickstart -> macOS -> Android

Configure Android SDK and Android Platform Tools via Android Studio

- Run Android Studio
- Section "Custom" setup option

Specify the following options during install

- Android SDK (Build and Command Line Tools)
- Android SDK Platform
- Performance (Intel HAXM)
- Android Virtual Device

Follow React Native guide for additional required SDK package and build tool version requirements

## iOS Setup

Install iOS environment

- Manually install Xcode via the Apple App Store

Install Cocoapods (iOS)

    brew install cocoapods

## React Native Setup

Install React Native command line tool

    npm install -g react-native-cli

# Projects

## Create Project

Initialize new project

    react-native init <app-name>
    cd <app-name>

## Run Metro

Start Metro server (and optionally reset cache)

    react-native start
    react-native start --reset-cache

## Install and Run App

Build, install and run app on iOS Simulator / Android Emulator

    react-native run-ios
    react-native run-android

## Install Packages

Install package for use in the app

    npm install <package-name> --save

Link native dependencies and update native build files (then rebuild)

    react-native link <package-name>

## Android Tips

Show React Native debug menu

    CMD + M

Allow React Native debugger menu to work with emulator (search settings for "draw over")

    Settings -> Apps -> Your-App -> Advanced -> Draw over other app -> Permit

## Android Troubleshooting

Unable to connect to remote debugger

Open in browser first

    http://localhost:8081/debugger-ui/

Configure reverse socket connection for react native server

    adb reverse tcp:8081 tcp:8081
