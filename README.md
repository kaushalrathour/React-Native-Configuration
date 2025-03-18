## Project Setup & Core Dependencies
# Initialize project
```bash
npx @react-native-community/cli@15.0.1 init AppName --version 0.77.1
```
## Install core dependencies
```bash
npm install @react-native-async-storage/async-storage react-native-size-matters react-native-vector-icons
```
## Navigation Setup
```bash
npm install @react-navigation/native@^7.0.14 @react-navigation/stack@^7.1.1 react-native-gesture-handler@^2.23.1 react-native-reanimated@^3.16.7 react-native-safe-area-context@^5.2.0 react-native-screens@^4.7.0
```
## State Management
```bash
npm install @reduxjs/toolkit react-redux
```
## UI and Utilities
```bash
npm install react-native-paper react-native-toast-message
```

## Firebase Services
```bash
npm install @react-native-firebase/app @react-native-firebase/auth @react-native-firebase/firestore @react-native-firebase/database @react-native-firebase/storage
```

## Android Configuration
# Add to android/app/build.gradle
```bash
apply from: file(\"../../node_modules/react-native-vector-icons/fonts.gradle\")
```
```bash
apply plugin: 'com.google.gms.google-services'
```
## Add to android/build.gradle dependencies
```bash
classpath("com.google.gms:google-services:4.4.2")
```
# Note: Manually place google-services.json in android/app/

## KeyStore Management
# Generate keystore
```bash
keytool -genkeypair -v -keystore myapp-release.keystore -alias myapp-alias -keyalg RSA -keysize 2048 -validity 10000
```
# Get SHA-1 fingerprint
```bash
keytool -list -v -keystore myapp-release.keystore -alias myapp-alias
```
## Gradle Clean
```bash
cd android && ./gradlew clean
```
## Form and Validation
```bash
npm install formik yup
```
## Signing Configuration (Add to android/app/build.gradle)
```bash
android {
    // ... existing configurations
    
    signingConfigs {
        debug {
            storeFile file('debug.keystore')
            storePassword 'android'
            keyAlias 'androiddebugkey'
            keyPassword 'android'
        }
        release {
            storeFile file('C:\\keystores\\timer-app-release-key.keystore')
            storePassword 'android'
            keyPassword 'android'
            keyAlias 'my-key-alias'
        }
    }

    buildTypes {
        debug {
            signingConfig signingConfigs.debug
        }
        release {
            signingConfig signingConfigs.release
            minifyEnabled enableProguardInReleaseBuilds
            proguardFiles getDefaultProguardFile("proguard-android.txt"), "proguard-rules.pro"
        }
    }
}
```
## Firebase Configuration (src/firebaseConfig.ts)
```bash
import { initializeApp } from "@react-native-firebase/app";
import { getMessaging } from "@react-native-firebase/messaging";
import { getFirestore } from "@react-native-firebase/firestore";
import { getAuth } from "@react-native-firebase/auth";
import { getStorage } from "@react-native-firebase/storage";
import { apiKey, projectId, messagingSenderId, appId, authDomain } from "@env";

const credentials = { apiKey, projectId, messagingSenderId, appId, authDomain };

const app = initializeApp(credentials);

export const messaging = getMessaging(app);
export const firestore = getFirestore(app);
export const auth = getAuth(app);
export const storage = getStorage(app);
```

## Env Setup (babel.config.js)
```
module.exports = {
  presets: ['module:@react-native/babel-preset'],
  plugins: [
    [
      'module:react-native-dotenv',
      {
        moduleName: '@env',
        path: '.env',
      },
    ],
  ],
};
```
## .env Sample
```bash
webClientId = "your-web-client-id"

apiKey = "your-api-key"

projectId = "your-project-id"

messagingSenderId = "your-messaging-sender-id"

appId = "your-app-id"

authDomain = "your-auth-domain.firebaseapp.com"
```
