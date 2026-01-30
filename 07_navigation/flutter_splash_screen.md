# Splash Screen in Flutter

## 1️⃣ What is a Splash Screen?

Splash screen is the first screen shown when app opens.

It usually shows:

- App logo
- App name
- Loading animation

**Simple meaning:**

> Intro screen of the app

---

## 2️⃣ Why Splash Screen is Used?

- Show branding (logo)
- Load initial data
- Improve user experience

---

## 3️⃣ Types of Splash Screen in Flutter

1. **Custom Splash Screen** (Flutter UI)
2. **Native Splash Screen** (Android / iOS)

This video mainly covers Custom Splash Screen.

---

## 4️⃣ Basic Logic of Splash Screen

1. Show splash screen
2. Wait for few seconds
3. Navigate to next screen (Home / Login)

---

## 5️⃣ Splash Screen Using StatefulWidget

**Why StatefulWidget?**

Because we use timer + navigation

---

## 6️⃣ Complete Splash Screen Example
```dart
class SplashScreen extends StatefulWidget {
  @override
  State<SplashScreen> createState() => _SplashScreenState();
}

class _SplashScreenState extends State<SplashScreen> {

  @override
  void initState() {
    super.initState();
    Future.delayed(Duration(seconds: 3), () {
      Navigator.pushReplacement(
        context,
        MaterialPageRoute(builder: (context) => HomeScreen()),
      );
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Icon(Icons.flutter_dash, size: 80),
            SizedBox(height: 20),
            Text('My App', style: TextStyle(fontSize: 24)),
          ],
        ),
      ),
    );
  }
}
```

---

## 7️⃣ Why initState() is Used?

`initState` runs only once

**Perfect place for:**

- Timer
- API call
- Navigation logic

---

## 8️⃣ Navigator.pushReplacement()

`Navigator.pushReplacement()`

- Replaces current screen
- Prevents going back to splash screen

---

## 9️⃣ Setting Splash Screen as First Screen

In `main.dart`:
```dart
home: SplashScreen(),
```

---

## 🔟 Common Mistakes

- ❌ Using `push` instead of `pushReplacement`
- ❌ Calling Navigator before `initState`
- ❌ Forgetting `super.initState()`

---

## 1️⃣1️⃣ Best Practices

- Keep splash screen short (2–3 sec)
- Do not load heavy logic
- Always replace splash screen

---

## 1️⃣2️⃣ Interview Questions

- What is splash screen?
- Why use `initState` for splash?
- Difference between push and pushReplacement?

---

## 1️⃣3️⃣ Quick Revision Points

- Splash screen = first screen
- Uses StatefulWidget
- `initState` handles timer
- `pushReplacement` prevents back
