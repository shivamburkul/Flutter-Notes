# Boolean State Management in Flutter

## 1️⃣ What is Boolean State?

- `bool` is a data type that holds only two values → `true` or `false`
- When a `bool` value changes in the app → UI needs to update
- To update UI when bool changes → we use `setState`

**Simple meaning:**

> Koi bhi true/false value jab change ho → setState use karo → UI update hoga

---

## 2️⃣ Where is Boolean State Used?

Bool state is used in many places in real apps:

- ✅ Checkbox → checked or unchecked
- 🔆 Switch → on or off
- 👁️ Password field → show or hide password
- ❤️ Like button → liked or not liked
- 📂 Dropdown → expanded or collapsed
- 🌙 Dark mode → enabled or disabled
- 🔔 Notification → on or off

> All of these work on the same concept → one bool + setState

---

## 3️⃣ Basic Pattern (Always Same)
```dart
// Step 1: Declare bool variable
bool myValue = false;

// Step 2: Use it in widget
// Step 3: On change → setState to update UI

onChanged: (newValue) {
  setState(() {
    myValue = newValue;
  });
}
```

---

## 4️⃣ Why StatefulWidget is Required?

- `bool` value changes → UI must re-render
- StatelessWidget cannot re-render
- Only StatefulWidget can re-render using `setState`

---

## 5️⃣ Example 1 — Checkbox (Check / Uncheck)
```dart
class CheckboxExample extends StatefulWidget {
  @override
  State<CheckboxExample> createState() => _CheckboxExampleState();
}

class _CheckboxExampleState extends State<CheckboxExample> {
  bool isChecked = false;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Checkbox Example')),
      body: Center(
        child: CheckboxListTile(
          title: Text('I agree to Terms & Conditions'),
          value: isChecked,
          onChanged: (newValue) {
            setState(() {
              isChecked = newValue!;
            });
          },
          activeColor: Colors.green,
        ),
      ),
    );
  }
}
```

---

## 6️⃣ Example 2 — Switch (On / Off)
```dart
bool isSwitched = false;

SwitchListTile(
  title: Text('Enable Notifications'),
  value: isSwitched,
  onChanged: (newValue) {
    setState(() {
      isSwitched = newValue;
    });
  },
  activeColor: Colors.blue,
)
```

---

## 7️⃣ Example 3 — Show / Hide Password
```dart
bool isPasswordVisible = false;

TextField(
  obscureText: !isPasswordVisible,   // hide or show
  decoration: InputDecoration(
    labelText: 'Password',
    suffixIcon: IconButton(
      icon: Icon(
        isPasswordVisible ? Icons.visibility : Icons.visibility_off,
      ),
      onPressed: () {
        setState(() {
          isPasswordVisible = !isPasswordVisible;  // toggle
        });
      },
    ),
  ),
)
```

---

## 8️⃣ Example 4 — Like Button (Liked / Not Liked)
```dart
bool isLiked = false;

IconButton(
  icon: Icon(
    isLiked ? Icons.favorite : Icons.favorite_border,
    color: isLiked ? Colors.red : Colors.grey,
  ),
  onPressed: () {
    setState(() {
      isLiked = !isLiked;   // toggle
    });
  },
)
```

---

## 9️⃣ Toggle Shortcut

Instead of writing `if/else`, use `!` to flip bool value:
```dart
// Long way
if (isLiked == true) {
  isLiked = false;
} else {
  isLiked = true;
}

// Short way (toggle)
isLiked = !isLiked;  // flips true→false or false→true
```

---

## 🔟 Multiple Bools Example
```dart
class SettingsScreen extends StatefulWidget {
  @override
  State<SettingsScreen> createState() => _SettingsScreenState();
}

class _SettingsScreenState extends State<SettingsScreen> {
  bool isDarkMode = false;
  bool isNotification = true;
  bool isLocationOn = false;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Settings')),
      body: Column(
        children: [
          SwitchListTile(
            title: Text('Dark Mode'),
            value: isDarkMode,
            onChanged: (val) => setState(() => isDarkMode = val),
          ),
          SwitchListTile(
            title: Text('Notifications'),
            value: isNotification,
            onChanged: (val) => setState(() => isNotification = val),
          ),
          SwitchListTile(
            title: Text('Location'),
            value: isLocationOn,
            onChanged: (val) => setState(() => isLocationOn = val),
          ),
        ],
      ),
    );
  }
}
```

---

## 1️⃣1️⃣ Checkbox Widget Properties (for reference)

- `value` → current bool value **(required)**
- `onChanged` → called when tapped **(required)**
- `activeColor` → color when checked
- `checkColor` → tick mark color
- `tristate` → allows null (3 states: true, false, null)

**CheckboxListTile** = Checkbox + Label + ListTile in one widget
```dart
CheckboxListTile(
  title: Text('Label here'),
  value: isChecked,
  onChanged: (newValue) {
    setState(() => isChecked = newValue!);
  },
)
```

---

## 1️⃣2️⃣ Bool Widgets Comparison

| Widget | Bool Variable | Use Case |
|---|---|---|
| `Checkbox` | `isChecked` | Tick / Untick |
| `Switch` | `isSwitched` | On / Off toggle |
| `IconButton` | `isLiked` | Like / Unlike |
| `TextField` | `isVisible` | Show / Hide password |
| `Container` | `isExpanded` | Show / Hide content |

---

## 1️⃣3️⃣ Common Mistakes

- ❌ Using StatelessWidget → UI won't update
- ❌ Forgetting `setState` → value changes but UI stays same
- ❌ Forgetting `!` with `newValue` in Checkbox → null safety error
- ❌ Creating bool inside `build()` → resets on every rebuild

> **Always declare bool variable outside `build()` method**

---

## 1️⃣4️⃣ Interview Questions

- What is boolean state management in Flutter?
- Why is StatefulWidget needed for bool state?
- How do you toggle a bool value in Flutter?
- What is the difference between Checkbox and Switch?
- How to show/hide password using bool state?

---

## 1️⃣5️⃣ Quick Revision Points

- `bool` = true or false → used everywhere in UI
- StatefulWidget + `setState` required to update UI
- `!value` → toggles bool (true→false, false→true)
- Same pattern works for Checkbox, Switch, Like button, Password visibility
- Declare bool outside `build()` method
- `CheckboxListTile` = Checkbox + Label in one widget
- `SwitchListTile` = Switch + Label in one widget
- Multiple bools → declare multiple variables
