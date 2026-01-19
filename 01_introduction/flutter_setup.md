## Flutter Setup & Installation (Complete)

This note covers **complete Flutter installation and setup** on **Windows, Mac, and Linux**, including IDE setup (Android Studio, VS Code, Xcode), adding Flutter to PATH, running `flutter doctor`, and creating your first app.

---

### 1. System Requirements

#### Windows
- OS: Windows 7 SP1 or later (64-bit)  
- Disk Space: 1.64 GB (does not include IDE/tools)  
- Tools: Git for Windows  

#### Mac
- OS: macOS (64-bit)  
- Disk Space: 2.8 GB  
- Tools: Git  

#### Linux
- OS: Linux (64-bit)  
- Disk Space: 600 MB  
- Tools: Git, bash, curl, unzip, xz-utils, libglu1-mesa  

---

### 2. Download Flutter SDK
1. Go to [Flutter official website](https://flutter.dev)  
2. Click **Get Started → Select your OS**  
3. Download the **stable Flutter SDK zip file**  

**Notes:**
- Always use **stable version**, not beta/dev channels  
- Extract Flutter SDK to a folder like `C:\flutter` (Windows) or `~/flutter` (Mac/Linux)  

---

### 3. Extract Flutter SDK
- **Windows:** Extract to `C:\flutter`  
- **Mac/Linux:** Extract to `~/flutter`  
- Avoid `Program Files` (Windows) → permission issues  

---

### 4. Add Flutter to PATH

#### Windows
1. Search **Environment Variables** → Edit system variables  
2. Under **System Variables**, find **Path → Edit → Add**: C:\flutter\bin
3. Click **OK → Apply → OK**  

#### Mac/Linux
1. Open terminal  
2. Edit `.bash_profile` or `.zshrc` depending on your shell  
3. Add line:export PATH="$PATH:[PATH_TO_FLUTTER_DIRECTORY]/flutter/bin"
4. Save file → run:source ~/.bash_profile # or source ~/.zshrc

---

### 5. Check Flutter Installation
Run in terminal or command prompt:

This checks:
- Flutter SDK
- Android toolchain
- Connected devices
- IDE plugins

⚠ Fix **all warnings and errors** shown by `flutter doctor`.

---

### 6. Install IDEs

#### Android Studio (Recommended)
1. Download from [Android Studio official website](https://developer.android.com/studio)  
2. Install with default options  
3. During installation, select: **Android SDK, Android SDK Platform, Android Virtual Device (AVD)**  
4. Open Android Studio → Go to **Plugins** → Search **Flutter** → Install  
5. Dart plugin is installed automatically with Flutter plugin  
6. Optional: Create **Android emulator** in AVD Manager

#### VS Code (Lightweight Alternative)
1. Download [VS Code](https://code.visualstudio.com/)  
2. Install **Flutter and Dart extensions** from Extensions panel  
3. Can use VS Code instead of Android Studio for lightweight development  

#### Xcode (Mac only)
1. Required for **iOS development**  
2. Install from Mac App Store  
3. Open Xcode → Preferences → Locations → select Command Line Tools  
4. Install CocoaPods:sudo gem install cocoapods

---

### 7. Run Your First Flutter App
1. Open terminal → navigate to folder for project  
2. Create new project:flutter create my_first_app
3. Navigate into project folder:cd my_first_app
4. Run app:flutter run
5. Hot Reload:
- Press **`r`** in terminal  
- Or press **Hot Reload button** in IDE  

---

### 8. Key Points
- Always install **stable version** of Flutter  
- Run `flutter doctor` → fix all issues  
- IDE plugins (Flutter + Dart) are required  
- Hot Reload = instant UI update  
- Emulator or physical device needed to test apps  

---

### 9. Common Mistakes
- Not adding Flutter to PATH → `flutter` command won’t work  
- Extracting Flutter to Program Files (Windows) → permission issues  
- Ignoring `flutter doctor` warnings/errors  
- Forgetting IDE plugins  
- Not installing Xcode for iOS development on Mac  

---

### 10. Summary
- Download Flutter SDK → Extract → Add to PATH  
- Install IDE → Plugins → Emulator (if Android) → Run first app  
- Hot Reload makes development fast  
- Flutter ready for development on **Windows, Mac, Linux**
