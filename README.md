# Development notes

## _This repo is a compiled notes with useful tools, hacks and problems solutions_

## Notes
Write readme online with https://dillinger.io


## Rest api
###  Mock
Mock api response - https://designer.mocky.io/

### For android
App Icon Generator - https://appicon.co/

Launcher icon generator - https://romannurik.github.io/AndroidAssetStudio/index.html

#### Get keystore information such as certificates fingerprints (SHA1, SHA256), alias name, owner, organization, fullname
Execute the command bellow replacing with your actual keystore path:

`keytool -list -v -keystore "C:\Users\admin\AppData\Local\Xamarin\Mono for Android\Keystore\SuperGrupos\SuperGrupos.keystore"`


#### How to create Android Facebook Key Hash?
`keytool -exportcert -alias androiddebugkey -keystore "C:\Documents and Settings\Administrator.android\debug.keystore" | "C:\OpenSSL\bin\openssl" sha1 -binary |"C:\OpenSSL\bin\openssl" base64`

_Reference_: https://stackoverflow.com/questions/7506392/how-to-create-android-facebook-key-hash



#### List all devices
`adb devices`


#### List all apps that is installed in my device, make sure to have just one device online
`adb shell pm list packages`

#### Install an apk to device
`adb uninstall com.myapp.android`


#### Uninstall apk from device
`adb install "C:\Users\admin\Downloads\app-brazil-debug.apk"`


#### Adding new directory to system environment 'path'
`setx path "%path%;c:\directoryPath"`


### For iOS
App Icon Generator - https://appicon.co/

