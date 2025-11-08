Perfect 👏 — since you want this to work **from clone → install → run** on both **iOS (simulator + iPhone)** and **Android (emulator + physical OnePlus)** on **Mac**, here’s a complete **production-grade `README.md`** you can drop directly into your repo
👉 [`https://github.com/ssgaur/mobile-3d-games`](https://github.com/ssgaur/mobile-3d-games)

It assumes only:

* You have **macOS**, **internet**, and **Git** installed.
* No prior setup (it installs Node, Watchman, Xcode, Android SDK, CocoaPods, etc.)
* Works for both simulator and connected mobile devices.

---

````markdown
# 🚀 Mobile 3D Games — React Native Setup Guide

This repository contains the **Mobile 3D Games App**, built using **React Native** with full cross-platform support for **iOS** and **Android**.

This guide will take you from a **fresh Mac setup** to running the app on both:
- 🧭 iOS Simulator / iPhone (via Xcode)
- 🤖 Android Emulator / OnePlus device (via Android Studio)

---

## 🧱 1. System Requirements

✅ macOS (Ventura or newer)  
✅ Stable internet connection  
✅ Git installed (`git --version`)  
✅ 25GB free disk space  

---

## ⚙️ 2. Install Global Dependencies

Open Terminal and run the following commands step-by-step:

### 📦 Install Homebrew
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
````

### 🧠 Install Node, Watchman, and Java

```bash
brew install node watchman openjdk@17
```

> React Native requires Node ≥ 18 and Java 17 for Gradle compatibility.

Add Java to your path:

```bash
echo 'export JAVA_HOME=$(/usr/libexec/java_home -v17)' >> ~/.zshrc
source ~/.zshrc
```

### 🛠️ Install Yarn (optional but faster)

```bash
npm install -g yarn
```

---

## 🍎 3. iOS Setup (Simulator & iPhone)

### Install Xcode

* Download from the **Mac App Store**.
* After installation:

  ```bash
  sudo xcode-select --switch /Applications/Xcode.app
  sudo xcodebuild -license accept
  ```

### Install CocoaPods (dependency manager for iOS)

```bash
sudo gem install cocoapods
```

---

## 🤖 4. Android Setup (Emulator & Physical Device)

### Install Android Studio

1. Download from [https://developer.android.com/studio](https://developer.android.com/studio)
2. During installation, **check all boxes**:

   * Android SDK
   * Android SDK Platform Tools
   * Android Virtual Device
3. Once installed:

   * Open **Android Studio → Preferences → Appearance & Behavior → System Settings → Android SDK**
   * Install the latest **SDK Platform (Android 14 / API 34)**.

### Add Android tools to PATH

```bash
echo 'export ANDROID_HOME=$HOME/Library/Android/sdk' >> ~/.zshrc
echo 'export PATH=$PATH:$ANDROID_HOME/emulator' >> ~/.zshrc
echo 'export PATH=$PATH:$ANDROID_HOME/platform-tools' >> ~/.zshrc
source ~/.zshrc
```

Verify:

```bash
adb devices
```

> If it lists your OnePlus or emulator — ✅ ready.

---

## 🧩 5. Clone and Install Project

```bash
git clone https://github.com/ssgaur/mobile-3d-games.git
cd mobile-3d-games
```

Install dependencies:

```bash
npm install
# OR
yarn install
```

---

## 🧵 6. iOS Setup (Pods & Run)

```bash
cd ios
pod install
cd ..
```

### Run on Simulator

```bash
npx react-native run-ios
```

### Run on Connected iPhone

1. Connect your iPhone via USB.
2. Open the Xcode workspace:

   ```bash
   open ios/mobile3dgames.xcworkspace
   ```
3. Select your device (top toolbar) → click **Run ▶️**.
4. If prompted, sign the app with your Apple ID (Xcode → Signing & Capabilities).

---

## ⚡ 7. Android Setup (Emulator & Device)

### Create an Emulator

1. Open **Android Studio → Device Manager**
2. Click **Create Device → Pixel 8 → Android 14 (API 34) → Finish**
3. Launch the emulator.

OR launch manually:

```bash
emulator -list-avds
emulator -avd Pixel_8_API_34
```

### Run on Emulator

```bash
npx react-native run-android
```

### Run on Connected Android (e.g. OnePlus)

1. Enable **Developer Options** → **USB Debugging** on your phone.
   (Settings → About phone → tap Build Number 7 times)
2. Connect via USB.
3. Verify:

   ```bash
   adb devices
   ```

   You should see your phone listed.
4. Run:

   ```bash
   npx react-native run-android
   ```

---

## 🧰 8. Common Commands

| Task                 | Command                                  |
| -------------------- | ---------------------------------------- |
| Start Metro bundler  | `npm start`                              |
| Run on iOS           | `npx react-native run-ios`               |
| Run on Android       | `npx react-native run-android`           |
| Clean Android build  | `cd android && ./gradlew clean && cd ..` |
| List Android devices | `adb devices`                            |
| Open iOS simulator   | `open -a Simulator`                      |

---

## 🧠 9. Troubleshooting

| Problem                        | Fix                                                |
| ------------------------------ | -------------------------------------------------- |
| **CocoaPods not found**        | `sudo gem install cocoapods`                       |
| **“adb: command not found”**   | Add Android SDK to PATH                            |
| **Gradle JvmVendorSpec error** | Ensure Java 17 (`brew install openjdk@17`)         |
| **Metro stuck or error**       | `npx react-native start --reset-cache`             |
| **Pods outdated**              | `cd ios && pod repo update && pod install`         |
| **App not appearing on phone** | Re-run `adb devices`, ensure USB Debugging enabled |

---

## 🧩 10. Verify Setup (Optional Doctor Check)

```bash
npx react-native doctor
```

✅ This will scan and auto-fix most setup issues.

---

## 🎮 11. You’re Done!

Now you can:

```bash
npm start
# or
yarn start
```

Then in separate terminals:

```bash
npm run ios
# or
npm run android
```

Your app will launch on:

* iPhone simulator or device (via Xcode)
* Android emulator or OnePlus (via adb)

---

## 💡 Notes

* For best performance, use **Node 20 LTS** and **React Native ≥ 0.82**.
* You can debug directly using **React Developer Tools** or **Flipper**.
* Hot Reloading is enabled by default — your app updates instantly on save.

---

### 🧑‍💻 Author

Maintained by [Shailendra Singh (ssgaur)](https://github.com/ssgaur)

---

### 🏁 Summary

From zero to running app:

```bash
git clone https://github.com/ssgaur/mobile-3d-games.git
cd mobile-3d-games
npm install
cd ios && pod install && cd ..
npx react-native run-ios
npx react-native run-android
```
