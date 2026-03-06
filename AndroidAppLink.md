# Android App Links

Guide for configuring **Android App Links** with domain verification.

------------------------------------------------------------------------

## 1. Create assetlinks.json

File location on your website:

    https://yourdomain.com/.well-known/assetlinks.json

Example:

``` json
[
  {
    "relation": [
      "delegate_permission/common.handle_all_urls"
    ],
    "target": {
      "namespace": "android_app",
      "package_name": "your.package.name",
      "sha256_cert_fingerprints": [
        "YOUR_SHA256_HERE"
      ]
    }
  }
]
```

------------------------------------------------------------------------

## 2. Get SHA256 From Keystore

``` bash
keytool -list -v -keystore your-keystore.jks -alias your-alias
```

Debug example:

``` bash
keytool -list -v -keystore ~/.android/debug.keystore -alias androiddebugkey -storepass android -keypass android
```

Copy the value under:

    SHA256:

------------------------------------------------------------------------

## 3. Configure AndroidManifest

``` xml
<intent-filter android:autoVerify="true">
    <action android:name="android.intent.action.VIEW" />

    <category android:name="android.intent.category.DEFAULT" />
    <category android:name="android.intent.category.BROWSABLE" />

    <data
        android:scheme="https"
        android:host="yourdomain.com" />
</intent-filter>
```

------------------------------------------------------------------------

## 4. Verify Domain

Install the app and run:

``` bash
adb shell pm verify-app-links your.package.name
```

Check status:

``` bash
adb shell pm get-app-links your.package.name
```

------------------------------------------------------------------------

## 5. Common Problems

### 404 on assetlinks.json

The file **must be accessible** at:

    https://yourdomain.com/.well-known/assetlinks.json

Both versions should work:

    https://yourdomain.com
    https://www.yourdomain.com

------------------------------------------------------------------------

## 6. Test Link

Open a link:

    https://yourdomain.com/path

If domain verification succeeds, Android opens the **app directly**
instead of the browser.

------------------------------------------------------------------------

## Related Documentation

See:

**Android.md**
