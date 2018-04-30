# What's in the Box
A docker build packed with the latest Android SDK. The SDK home directory is available via `ANDROID_HOME` and you can locate the relevant SDK version via `ANDROID_VERSION` and `ANDROID_BUILD_TOOLS_VERSION`

# Update Android SDK
Please refer to https://developer.android.com/studio/command-line/sdkmanager#install_packages on how to install packages. 

If you intend to update the SDK to a.b.c, refer to https://developer.android.com/studio/ and locate the download link for the SDK package, i.e https://dl.google.com/android/repository/sdk-tools-linux-3859397.zip  Then replace the line 

```
ENV SDK_URL="https://dl.google.com/android/repository/sdk-tools-linux-[FILE NAME].zip" \
```
and update the SDK version 
```
  ANDROID_VERSION=[NEW ANDROID SDK VERSION] \
  ANDROID_BUILD_TOOLS_VERSION=[NEW ANDROID TOOLS VERSION]
```

# Demo
You can build any Android app with this SDK, for example GitLab CI
```
image: congz/androidsdk-27

stages:
  - build

build:
  stage: build
  script:
    - ./gradlew assembleDebug
  artifacts:
    paths:
    - app/build/outputs/
```
