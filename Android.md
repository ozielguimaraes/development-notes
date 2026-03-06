# Android Development Notes

Quick commands and utilities for everyday Android development.

------------------------------------------------------------------------

## Check Java Version

``` bash
java -version
```

------------------------------------------------------------------------

## Check ADB Devices

``` bash
adb devices
```

------------------------------------------------------------------------

## Install APK

``` bash
adb install app.apk
```

Force reinstall:

``` bash
adb install -r app.apk
```

------------------------------------------------------------------------

## View Device Logs

``` bash
adb logcat
```

Filter by package:

``` bash
adb logcat | grep your.package.name
```

------------------------------------------------------------------------

## Clear App Data

``` bash
adb shell pm clear your.package.name
```

------------------------------------------------------------------------

## Uninstall App

``` bash
adb uninstall your.package.name
```

------------------------------------------------------------------------

## Generate SHA256 From Keystore

``` bash
keytool -list -v -keystore your-keystore.jks -alias your-alias
```

Debug keystore example:

``` bash
keytool -list -v -keystore ~/.android/debug.keystore -alias androiddebugkey -storepass android -keypass android
```

Look for:

    SHA256:

This value is required for **Android App Links**.

------------------------------------------------------------------------

## Related Documentation

See:

[Android App Link Guide](AndroidAppLink.md)
