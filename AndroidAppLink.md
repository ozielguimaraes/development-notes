# Android App Links Guide

Android App Links allow your app to open automatically when a user clicks a verified URL.

Example:

https://example.com/profile/123

Instead of opening the browser, Android launches the app.

---

## Step 1 – Add Intent Filter

Add this to your AndroidManifest.xml.

<intent-filter android:autoVerify="true">
    <action android:name="android.intent.action.VIEW"/>

    <category android:name="android.intent.category.DEFAULT"/>
    <category android:name="android.intent.category.BROWSABLE"/>

    <data
        android:scheme="https"
        android:host="example.com"/>
</intent-filter>

---

## Step 2 – Create Asset Links File

Create the file:

https://example.com/.well-known/assetlinks.json

Example:

[
  {
    "relation": ["delegate_permission/common.handle_all_urls"],
    "target": {
      "namespace": "android_app",
      "package_name": "com.example.app",
      "sha256_cert_fingerprints": [
        "YOUR_SHA256_CERTIFICATE"
      ]
    }
  }
]

---

## Step 3 – Generate SHA256 Certificate

Use:

keytool -list -v -keystore your-keystore.jks -alias your-alias

For debug builds:

keytool -list -v \
-keystore ~/.android/debug.keystore \
-alias androiddebugkey \
-storepass android \
-keypass android

Copy the value from:

SHA256:

---

## Step 4 – Verify App Link

Check verification status:

adb shell pm get-app-links your.package.name

Trigger link test:

adb shell am start -a android.intent.action.VIEW -d "https://example.com/test"

---

## Common Problems

| Issue | Cause |
|------|------|
| Link opens browser | assetlinks.json missing |
| Verification failed | wrong SHA256 |
| App not opening | incorrect host configuration |
