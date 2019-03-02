# Android

## Devices

Show list of available android devices

    adb devices

## Crash Logs

All logs

    adb logcat

Error logs

    adb logcat '*:E'

## Reverse Socket

Configure reverse socket connection

    adb reverse tcp:<port> tcp:<port>

## Add Test Media

- Drag image to emulator
- Open: Settings (app) -> Storage -> Internal Storage -> Explore
- View the image, and add to Gallery
