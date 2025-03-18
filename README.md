## Project Setup & Core Dependencies
```bash
# Initialize project
npx @react-native-community/cli@15.0.1 init AppName --version 0.77.1
```
```bash
# Install core dependencies
npm install @react-native-async-storage/async-storage react-native-size-matters react-native-vector-icons
```
```bash
# Navigation Setup
npm install @react-navigation/native@^7.0.14 @react-navigation/stack@^7.1.1 react-native-gesture-handler@^2.23.1 react-native-reanimated@^3.16.7 react-native-safe-area-context@^5.2.0 react-native-screens@^4.7.0
```
```bash
# State Management
npm install @reduxjs/toolkit react-redux
```

```bash
# UI and Utilities
npm install react-native-paper react-native-toast-message
```

```bash
# Firebase Services
npm install @react-native-firebase/app @react-native-firebase/auth @react-native-firebase/firestore @react-native-firebase/database @react-native-firebase/storage
```

```bash
# Android Configuration
# Add to android/app/build.gradle
apply from: file(\"../../node_modules/react-native-vector-icons/fonts.gradle\")

apply plugin: 'com.google.gms.google-services'"
```
```bash
# Add to android/build.gradle dependencies
classpath("com.google.gms:google-services:4.4.2")
# Note: Manually place google-services.json in android/app/
```


```bash
# KeyStore Management
# Generate keystore
keytool -genkeypair -v -keystore myapp-release.keystore -alias myapp-alias -keyalg RSA -keysize 2048 -validity 10000
```

```bash
# Get SHA-1 fingerprint
keytool -list -v -keystore myapp-release.keystore -alias myapp-alias
```

```bash
# Gradle Clean
cd android && ./gradlew clean
```

```bash
# Form and Validation
npm install formik yup
```

```bash
# Signing Configuration (Add to android/app/build.gradle)
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