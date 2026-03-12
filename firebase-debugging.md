# Firebase Push Debugging (Android)

Guide for debugging Firebase Cloud Messaging (FCM) using ADB.

---

## Clear Logs Before Testing

Always start with clean logs.

adb logcat -c

---

## View Firebase Messaging Logs

adb logcat -v time FirebaseMessaging:D "*:S"

Shows:

- token generation
- message reception
- subscription events
- delivery errors

---

## Show Only Errors

adb logcat FirebaseMessaging:E "*:S"

---

## Common Errors

| Error | Meaning |
|------|------|
| SERVICE_NOT_AVAILABLE | Network or Google Play Services issue |
| TOO_MANY_SUBSCRIBERS | Too many topic subscriptions |
| MismatchSenderId | Firebase project mismatch |
| InvalidRegistration | Invalid token |

---

## Verify Token Generation

adb logcat -s FirebaseMessaging

Example output:

FirebaseMessaging: New token generated

---

## Confirm Push Received By Device

adb logcat -s FirebaseMessaging NotificationService

---

## Check Only Your App Logs

Get process id:

adb shell pidof your.package.name

Then filter logs:

adb logcat --pid=PROCESS_ID

---

## Useful Debug Command

adb logcat -v time | grep -i firebase

---

## Common Issue

If OnMessageReceived() is not triggered, the push may have been sent using:

notification

Instead of:

data

Recommended payload:

{
  "to": "DEVICE_TOKEN",
  "data": {
    "title": "Test",
    "message": "Hello"
  }
}
