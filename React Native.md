# React Native

## Setup Overview

Development Tools

- [Xcode](https://developer.apple.com/xcode/)
- [Xcode Command Line Tools](https://developer.apple.com/download/more/)
- [CocoaPods](https://cocoapods.org/)
- [Android Studio](https://developer.android.com/studio/)
- [Node](https://nodejs.org/en/)
- [Watchman](https://facebook.github.io/watchman/)
- [OpenJDK](https://adoptium.net/)

## Base Setup

Install base environment

    brew install node
    brew install watchman

## Android Setup

Install Java 11 JDK

    brew install --cask homebrew/cask-versions/zulu11

Install Android Studio

    brew install --cask android-studio

Android environment setup instructions

- https://reactnative.dev/docs/environment-setup
- Refer to: React Native CLI Quickstart -> macOS -> Android

## iOS Setup

Install iOS environment

- Manually install Xcode via the Apple App Store

Install Cocoapods (iOS)

    sudo gem install cocoapods

iOS environment setup instructions

- https://reactnative.dev/docs/environment-setup
- Refer to: React Native CLI Quickstart -> macOS -> iOS

## React Native CLI

Run React Native CLI commands

    npx react-native <command>

Show system and React Native info

    npx react-native info

# Projects

## Create Project

Initialize new project

    npx react-native init <app-name>
    cd <app-name>

## Run Server

Start server (and optionally reset cache)

    npx react-native start
    npx react-native start --reset-cache

## Install and Run App

Build, install and run app on iOS Simulator / Android Emulator

    npx react-native run-ios
    npx react-native run-android

## Emulator / Simulator Commands

Show development / debug menu

- CMD + M (Android)
- CMD + D (iOS)
- Shake (Hardware Device)

Reload application

- R + R (Android)
- R (iOS)

## Android Tips

Unable to connect to remote debugger

Open in browser first

    http://localhost:8081/debugger-ui/

Configure reverse socket connection for react native server

    adb reverse tcp:8081 tcp:8081

## iOS Tips

Install pods (run from within project directory)

    npx pod-install
