# Create React Native with Firebase App with Expo
## 1. install needed dependencies

> npx create-expo-app name -t default
 
> npx expo install @react-native-firebase/app @react-native-firebase/auth

> npx expo install expo-build-properties

## 2. update app.json

### add expo-build-properties and firebase to plugins
```json
"plugins": {
    ...
    [
        "expo-build-properties", {
            "ios": {
              "useFrameworks": "static"
            }
        }
    ],
    "@react-native-firebase/app",
    "@react-native-firebase/auth",
    ...
}
```

### add bundle identifier to ios and android 
```json
...
"ios": {
    "supportsTablet": true,
    "bundleIdentifier": "com.domthedev.xxx"
},
...
"android": {
    "adaptiveIcon": {
        "foregroundImage": "./assets/images/adaptive-icon.png",
        "backgroundColor": "#ffffff"
    },
    "package": "com.domthedev.xxx"
},
...
```

## 3. generate native ios and android folder
> npx expo prebuild


#### GoogleService-Info.plist is not defined
> Get your GoogleService-Info.plist as well as your googleServices.json from firebase console.

####  Path to GoogleService-Info.plist is not defined.
```json 
...
"ios": {
    "supportsTablet": true,
    "bundleIdentifier": "com.domthedev.cr",
    "googleServicesFile": "./GoogleService-Info.plist"
}
...
"android": {
    "adaptiveIcon": {
        "foregroundImage": "./assets/images/adaptive-icon.png",
        "backgroundColor": "#ffffff"
    },
    "package": "com.domthedev.cr",
    "googleServicesFile": "./google-services.json"
},
...
```

#### Failed to parse your GoogleService-Info.plist. Are you sure it is a valid Info.Plist file with a REVERSE_CLIENT_ID field?
> ios: Add Authentication in your Firebase Console and add Email/Password as well as Google Authentication. Download new GoogleService-Info.plist

> android: Provide sha1 link in Firebase Console for Android app and download new google-services.json

#### Get SHA1 KEy for your app
> `cd android`
> 
> `./gradlew signingReport`
> 
> Then add from first created debug key the SHA1

## 3. Add expo-dev-client
> npx expo install expo-dev-client

> npx pod install
 
## 4. Google Sign In 
### (with RN Google Sign In)
https://react-native-google-signin.github.io/docs/install
#### install dependency
> npm i @react-native-google-signin/google-signin@latest

#### add config to app.json 

```json
{
...
    "plugins": [
      ...
        "@react-native-google-signin/google-signin",
      ...
    ],
...
}
```

> npx expo prebuild --clean

### Get your web client ID from console.cloud.google.com
> go to console.cloud.google.com select your project
> firebase already created your client ID


## Start App on ios device
#### Start Server
> npm run start

#### Build the app with xcode on your device
> cd ios

> open xxx.xcworkspace
