# ADB Cheatsheet

Quick reference for common Android Debug Bridge (ADB) commands.

---

## Device Commands

### List Connected Devices
adb devices

### Restart ADB Server
adb kill-server
adb start-server

### Connect Device via WiFi
adb connect DEVICE_IP

Example:
adb connect 192.168.1.10:5555

---

## App Installation

### Install APK
adb install app.apk

### Reinstall App
adb install -r app.apk

### Install and Grant Permissions
adb install -g app.apk

---

## App Management

### Uninstall App
adb uninstall your.package.name

### Clear App Data
adb shell pm clear your.package.name

### Force Stop App
adb shell am force-stop your.package.name

---

## Logs

### View Logs
adb logcat

### Clear Logs
adb logcat -c

### Filter Logs by Tag
adb logcat -s TAG_NAME

Example:
adb logcat -s FirebaseMessaging

---

## Filter Logs by Process

Get process id:
adb shell pidof your.package.name

Then filter logs:
adb logcat --pid=PROCESS_ID

---

## File Transfer

### Pull File From Device
adb pull /sdcard/file.txt

### Push File To Device
adb push file.txt /sdcard/

---

## Screenshots

adb exec-out screencap -p > screenshot.png

---

## Screen Recording

adb shell screenrecord /sdcard/demo.mp4

Stop recording with Ctrl + C then pull file:

adb pull /sdcard/demo.mp4
