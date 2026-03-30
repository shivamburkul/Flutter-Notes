# Flutter Shared Preferences Login Tutorial

## 1️⃣ What are we Building?

A login system where:
- User enters username & password → taps Login
- Login status is **saved in Shared Preferences**
- Next time app opens → user is **already logged in** (goes directly to Home)
- User taps Logout → login status cleared → back to Login screen

**Simple meaning:**

> Login karo → data save ho jaye → app band karo phir kholo → seedha Home screen

---

## 2️⃣ Why Shared Preferences for Login?

- No internet needed
- Data stays even after app close
- Simple and fast
- Perfect for saving login state (true/false)

> Real apps use this to remember if user is logged in

---

## 3️⃣ Package Required

Add in `pubspec.yaml`:
```yaml
dependencies:
  shared_preferences: ^2.2.2
```

Then run:
```
flutter pub get
```

Import:
```dart
import 'package:shared_preferences/shared_preferences.dart';
```

---

## 4️⃣ App Flow
```
App Opens
    ↓
Check Shared Preferences
    ↓
isLoggedIn == true?
   YES → HomeScreen
   NO  → LoginScreen
    ↓
LoginScreen → Enter credentials → Tap Login
    ↓
Save isLoggedIn = true in Shared Preferences
    ↓
Navigate to HomeScreen
    ↓
Tap Logout → Clear Shared Preferences → Back to LoginScreen
```

---

## 5️⃣ Keys Used in Shared Preferences
```dart
// Define keys as constants to avoid typos
static const String KEY_IS_LOGGED_IN = 'isLoggedIn';
static const String KEY_USERNAME = 'username';
```

---

## 6️⃣ Full Code

### main.dart
```dart
import 'package:flutter/material.dart';
import 'package:shared_preferences/shared_preferences.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: SplashScreen(),  // always start from splash
    );
  }
}
```

---

### SplashScreen (Check Login Status)
```dart
class SplashScreen extends StatefulWidget {
  @override
  State<SplashScreen> createState() => _SplashScreenState();
}

class _SplashScreenState extends State<SplashScreen> {

  @override
  void initState() {
    super.initState();
    checkLoginStatus();  // check on app start
  }

  void checkLoginStatus() async {
    SharedPreferences prefs = await SharedPreferences.getInstance();
    bool isLoggedIn = prefs.getBool('isLoggedIn') ?? false;

    if (isLoggedIn) {
      // already logged in → go to Home
      Navigator.pushReplacement(
        context,
        MaterialPageRoute(builder: (_) => HomeScreen()),
      );
    } else {
      // not logged in → go to Login
      Navigator.pushReplacement(
        context,
        MaterialPageRoute(builder: (_) => LoginScreen()),
      );
    }
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: CircularProgressIndicator(),  // loading while checking
      ),
    );
  }
}
```

---

### LoginScreen
```dart
class LoginScreen extends StatefulWidget {
  @override
  State<LoginScreen> createState() => _LoginScreenState();
}

class _LoginScreenState extends State<LoginScreen> {
  TextEditingController usernameController = TextEditingController();
  TextEditingController passwordController = TextEditingController();
  bool isPasswordVisible = false;
  String errorMessage = '';

  // Save login data
  void login() async {
    String username = usernameController.text.trim();
    String password = passwordController.text.trim();

    // Simple validation
    if (username.isEmpty || password.isEmpty) {
      setState(() {
        errorMessage = 'Please enter username and password';
      });
      return;
    }

    // Hardcoded check (in real app → check from API/database)
    if (username == 'admin' && password == '1234') {
      SharedPreferences prefs = await SharedPreferences.getInstance();
      await prefs.setBool('isLoggedIn', true);
      await prefs.setString('username', username);

      // Go to Home screen
      Navigator.pushReplacement(
        context,
        MaterialPageRoute(builder: (_) => HomeScreen()),
      );
    } else {
      setState(() {
        errorMessage = 'Invalid username or password';
      });
    }
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Login')),
      body: Padding(
        padding: EdgeInsets.all(24),
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [

            Icon(Icons.lock, size: 80, color: Colors.blue),
            SizedBox(height: 30),

            // Username field
            TextField(
              controller: usernameController,
              decoration: InputDecoration(
                labelText: 'Username',
                prefixIcon: Icon(Icons.person),
                border: OutlineInputBorder(),
              ),
            ),
            SizedBox(height: 16),

            // Password field
            TextField(
              controller: passwordController,
              obscureText: !isPasswordVisible,
              decoration: InputDecoration(
                labelText: 'Password',
                prefixIcon: Icon(Icons.lock),
                border: OutlineInputBorder(),
                suffixIcon: IconButton(
                  icon: Icon(
                    isPasswordVisible
                        ? Icons.visibility
                        : Icons.visibility_off,
                  ),
                  onPressed: () {
                    setState(() {
                      isPasswordVisible = !isPasswordVisible;
                    });
                  },
                ),
              ),
            ),
            SizedBox(height: 10),

            // Error message
            if (errorMessage.isNotEmpty)
              Text(
                errorMessage,
                style: TextStyle(color: Colors.red),
              ),

            SizedBox(height: 20),

            // Login button
            SizedBox(
              width: double.infinity,
              child: ElevatedButton(
                onPressed: login,
                child: Text('Login', style: TextStyle(fontSize: 18)),
              ),
            ),

          ],
        ),
      ),
    );
  }
}
```

---

### HomeScreen
```dart
class HomeScreen extends StatefulWidget {
  @override
  State<HomeScreen> createState() => _HomeScreenState();
}

class _HomeScreenState extends State<HomeScreen> {
  String username = '';

  @override
  void initState() {
    super.initState();
    loadUsername();
  }

  // Load saved username
  void loadUsername() async {
    SharedPreferences prefs = await SharedPreferences.getInstance();
    setState(() {
      username = prefs.getString('username') ?? 'User';
    });
  }

  // Logout → clear data
  void logout() async {
    SharedPreferences prefs = await SharedPreferences.getInstance();
    await prefs.clear();   // clear all saved data

    Navigator.pushReplacement(
      context,
      MaterialPageRoute(builder: (_) => LoginScreen()),
    );
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Home'),
        actions: [
          IconButton(
            icon: Icon(Icons.logout),
            onPressed: logout,
          ),
        ],
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Icon(Icons.check_circle, size: 80, color: Colors.green),
            SizedBox(height: 20),
            Text(
              'Welcome, $username!',
              style: TextStyle(fontSize: 24, fontWeight: FontWeight.bold),
            ),
            SizedBox(height: 10),
            Text(
              'You are logged in.',
              style: TextStyle(fontSize: 16, color: Colors.grey),
            ),
            SizedBox(height: 30),
            ElevatedButton.icon(
              onPressed: logout,
              icon: Icon(Icons.logout),
              label: Text('Logout'),
              style: ElevatedButton.styleFrom(backgroundColor: Colors.red),
            ),
          ],
        ),
      ),
    );
  }
}
```

---

## 7️⃣ pushReplacement vs push

| Method | Behavior |
|---|---|
| `push` | New screen added on top → back button works |
| `pushReplacement` | Replaces current screen → no back button |

> After login → use `pushReplacement` so user cannot go back to Login screen

---

## 8️⃣ What Data is Saved
```dart
// Saved on Login
prefs.setBool('isLoggedIn', true);
prefs.setString('username', 'admin');

// Cleared on Logout
prefs.clear();
```

---

## 9️⃣ Common Mistakes

- ❌ Using `push` instead of `pushReplacement` → user can go back to login after logging in
- ❌ Not checking login status on app start → user has to login every time
- ❌ Forgetting `await` → data may not save properly
- ❌ Hardcoding credentials in real app → always validate from API
- ❌ Not clearing prefs on logout → user stays logged in forever

---

## 🔟 Interview Questions

- How do you persist login state in Flutter?
- What is the role of Shared Preferences in login?
- Why use `pushReplacement` after login?
- What happens if `isLoggedIn` key is not found in Shared Preferences?
- How do you implement logout with Shared Preferences?
- What is SplashScreen used for in login flow?

---

## 1️⃣1️⃣ Quick Revision Points

- Shared Preferences saves login state locally
- Always check login status on app start using SplashScreen
- `isLoggedIn = true` → save on login
- `prefs.clear()` → call on logout
- Use `pushReplacement` after login and logout
- `?? false` → default value if key not found
- In real apps → validate credentials from API, not hardcoded
- `username` can also be saved to show on Home screen
