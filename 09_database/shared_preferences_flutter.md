# Shared Preferences in Flutter (Store & Retrieve Data)

## 1️⃣ What is Shared Preferences?

- `Shared Preferences` is used to **store small data locally** on device.
- Data is saved even after app is closed and reopened.
- Stores data as **key-value pairs**.

**Simple meaning:**

> App band karo, phir kholo → data wahi rahega → that is Shared Preferences

**Examples:**

- Save login status (logged in or not)
- Save user name
- Save theme (dark/light)
- Save app settings

---

## 2️⃣ What Data Can Be Stored?

- `String` → text
- `int` → numbers
- `double` → decimal numbers
- `bool` → true / false
- `List<String>` → list of strings

> ❌ Cannot store complex objects directly (like class objects)

---

## 3️⃣ Package Required

Add this in `pubspec.yaml`:
```yaml
dependencies:
  shared_preferences: ^2.2.2
```

Then run:
```
flutter pub get
```

---

## 4️⃣ Import in Dart File
```dart
import 'package:shared_preferences/shared_preferences.dart';
```

---

## 5️⃣ How to SAVE Data
```dart
// Step 1: Get instance
SharedPreferences prefs = await SharedPreferences.getInstance();

// Step 2: Save data using key
await prefs.setString('username', 'Shivam');
await prefs.setInt('age', 21);
await prefs.setBool('isLoggedIn', true);
await prefs.setDouble('rating', 4.5);
```

---

## 6️⃣ How to RETRIEVE Data
```dart
SharedPreferences prefs = await SharedPreferences.getInstance();

// Get data using same key
String? username = prefs.getString('username');
int? age = prefs.getInt('age');
bool? isLoggedIn = prefs.getBool('isLoggedIn');
double? rating = prefs.getDouble('rating');

print(username);     // Shivam
print(isLoggedIn);   // true
```

> **Note:** Returns `null` if key does not exist

---

## 7️⃣ How to DELETE Data
```dart
SharedPreferences prefs = await SharedPreferences.getInstance();

// Remove single key
await prefs.remove('username');

// Remove all data
await prefs.clear();
```

---

## 8️⃣ Save & Retrieve Methods Table

| Data Type | Save Method | Get Method |
|---|---|---|
| String | `setString('key', value)` | `getString('key')` |
| int | `setInt('key', value)` | `getInt('key')` |
| double | `setDouble('key', value)` | `getDouble('key')` |
| bool | `setBool('key', value)` | `getBool('key')` |
| List\<String\> | `setStringList('key', value)` | `getStringList('key')` |

---

## 9️⃣ Full Example — Save & Show Username
```dart
import 'package:flutter/material.dart';
import 'package:shared_preferences/shared_preferences.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(home: HomeScreen());
  }
}

class HomeScreen extends StatefulWidget {
  @override
  State<HomeScreen> createState() => _HomeScreenState();
}

class _HomeScreenState extends State<HomeScreen> {
  String displayName = '';
  TextEditingController nameController = TextEditingController();

  // Save data
  void saveName() async {
    SharedPreferences prefs = await SharedPreferences.getInstance();
    await prefs.setString('username', nameController.text);
    print('Name Saved!');
  }

  // Retrieve data
  void loadName() async {
    SharedPreferences prefs = await SharedPreferences.getInstance();
    String? name = prefs.getString('username');
    setState(() {
      displayName = name ?? 'No name found';
    });
  }

  // Delete data
  void deleteName() async {
    SharedPreferences prefs = await SharedPreferences.getInstance();
    await prefs.remove('username');
    setState(() {
      displayName = '';
    });
  }

  @override
  void initState() {
    super.initState();
    loadName(); // load on app start
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Shared Preferences')),
      body: Padding(
        padding: EdgeInsets.all(20),
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            TextField(
              controller: nameController,
              decoration: InputDecoration(
                labelText: 'Enter Name',
                border: OutlineInputBorder(),
              ),
            ),
            SizedBox(height: 16),
            ElevatedButton(
              onPressed: saveName,
              child: Text('Save Name'),
            ),
            ElevatedButton(
              onPressed: loadName,
              child: Text('Load Name'),
            ),
            ElevatedButton(
              onPressed: deleteName,
              child: Text('Delete Name'),
            ),
            SizedBox(height: 20),
            Text(
              'Saved Name: $displayName',
              style: TextStyle(fontSize: 20),
            ),
          ],
        ),
      ),
    );
  }
}
```

---

## 🔟 Real App Use Case — Save Login Status
```dart
// On Login button press → save true
Future<void> saveLoginStatus() async {
  SharedPreferences prefs = await SharedPreferences.getInstance();
  await prefs.setBool('isLoggedIn', true);
}

// On app start → check if already logged in
Future<void> checkLogin() async {
  SharedPreferences prefs = await SharedPreferences.getInstance();
  bool? isLoggedIn = prefs.getBool('isLoggedIn');

  if (isLoggedIn == true) {
    // go to HomeScreen
  } else {
    // go to LoginScreen
  }
}

// On Logout → clear data
Future<void> logout() async {
  SharedPreferences prefs = await SharedPreferences.getInstance();
  await prefs.clear();
}
```

---

## 1️⃣1️⃣ Default Value if Key Not Found
```dart
// If key not found, returns null
String? name = prefs.getString('username');  // null if not saved

// Safe way with default value
String name = prefs.getString('username') ?? 'Guest';
int age = prefs.getInt('age') ?? 0;
bool isLoggedIn = prefs.getBool('isLoggedIn') ?? false;
```

---

## 1️⃣2️⃣ Shared Preferences vs Other Storage

| Storage | Use Case |
|---|---|
| Shared Preferences | Small simple data (settings, login) |
| SQLite / Hive | Large structured data (database) |
| File Storage | Files, images, documents |

---

## 1️⃣3️⃣ Common Mistakes

- ❌ Forgetting `await` → data may not be saved properly
- ❌ Using wrong key name while getting → returns null
- ❌ Storing complex objects directly → not supported
- ❌ Forgetting to add package in `pubspec.yaml`
- ❌ Not calling `flutter pub get` after adding package

---

## 1️⃣4️⃣ Interview Questions

- What is Shared Preferences in Flutter?
- What types of data can Shared Preferences store?
- How is data saved and retrieved in Shared Preferences?
- What happens if a key does not exist in Shared Preferences?
- Difference between Shared Preferences and SQLite?
- How to delete data from Shared Preferences?

---

## 1️⃣5️⃣ Quick Revision Points

- Shared Preferences = local key-value storage
- Data persists even after app close
- Supports String, int, double, bool, List\<String\>
- Package → `shared_preferences`
- `getInstance()` → always required first
- `setString / getString` → save and get data
- `remove('key')` → delete one key
- `clear()` → delete all data
- Always use `await` with shared preferences methods
- Use `?? defaultValue` to handle null safely
