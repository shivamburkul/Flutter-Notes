## Flutter Project & First App

This note covers **creating a new Flutter project**, **project structure**, and **running your first app** in both Android Studio and VS Code.

---

### 1. Creating a New Flutter Project

#### Android Studio
1. Open **Android Studio**  
2. Click **Start a new Flutter project**  
3. Select **Flutter Application** → Next  
4. Enter **Project Name** (lowercase_with_underscores)  
5. Set **Flutter SDK path** (where you installed Flutter)  
6. Set **Project Location** → Next  
7. Enter **Description** (optional) → Next  
8. Select **Platform options**: Android / iOS → Finish  

Your project is now created.  
Android Studio will generate **default Flutter project structure**.

#### VS Code
1. Open VS Code  
2. Press **Ctrl+Shift+P → Flutter: New Project**  
3. Select **Flutter Application** → Enter project name  
4. Select folder location → Wait for project to generate  

---

### 2. Flutter Project Structure (Overview)

**Default Flutter project structure:**
my_first_app/
├── android/ # Native Android code
├── ios/ # Native iOS code
├── lib/ # Main Dart code
│ └── main.dart # Entry point of Flutter app
├── test/ # Unit tests
├── pubspec.yaml # Project config, dependencies
├── pubspec.lock # Dependency versions
├── README.md # Project info
└── .gitignore # Git ignore rules

**Important files/folders:**

- `lib/main.dart` → **Entry point** of your app, contains main() function  
- `pubspec.yaml` → Add dependencies, fonts, images  
- `android/` & `ios/` → Native platform code, mostly handled by Flutter  
- `test/` → Write unit and widget tests  

---

### 3. main.dart (Entry Point)

Default `main.dart` example:

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'My First App',
      home: Scaffold(
        appBar: AppBar(
          title: Text('Flutter First App'),
        ),
        body: Center(
          child: Text('Hello Flutter!'),
        ),
      ),
    );
  }
}
```

### 4. Running Your First App

#### Android Studio

- Connect an emulator or physical device
- Select device in top bar
- Click Run → Run ‘main.dart’

Hot Reload button: saves changes instantly without restarting app

#### VS Code

- Open terminal and navigate to project folder
- Run: flutter run

Hot Reload:  
- Press r → reload code  
- Press R → full restart

---

### 5. Key Points

- Always write project name in lowercase_with_underscores  
- main.dart is entry point  
- pubspec.yaml manages dependencies  
- Hot Reload = fast UI updates  
- Android Studio / VS Code both work, choose what you like

---

### 6. Common Mistakes

- Forgetting to connect emulator or physical device  
- Not selecting Flutter SDK in Android Studio  
- Writing project name with spaces → causes errors  
- Modifying native folders (android/ or ios/) unnecessarily  
- Forgetting to save file before Hot Reload

---

### 7. Summary

- Create new Flutter project → Android Studio or VS Code  
- Learn project structure → lib/, android/, ios/, pubspec.yaml  
- Write code in main.dart  
- Run app → Hot Reload for fast development

Now you are ready to start adding widgets and UI
