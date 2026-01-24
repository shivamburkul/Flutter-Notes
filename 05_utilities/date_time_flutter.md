# Getting Current Date and Time in Flutter

## 1️⃣ Why Date and Time is Needed

- Show current date/time
- Timestamps (login, messages)
- Booking apps
- Attendance apps

Flutter uses Dart `DateTime` class to handle date and time.

---

## 2️⃣ DateTime Class (Core Concept)

`DateTime` is a built-in Dart class.

**Used for:**

- Date
- Time
- Both combined

---

## 3️⃣ Get Current Date and Time
```dart
DateTime now = DateTime.now();
```

---

## 4️⃣ Access Date Components
```dart
now.year   // Year
now.month  // Month
now.day    // Day
```

---

## 5️⃣ Access Time Components
```dart
now.hour    // Hour
now.minute  // Minute
now.second  // Second
```

---

## 6️⃣ Display Date & Time in Text Widget
```dart
Text(
  '${now.day}-${now.month}-${now.year}',
)

Text(
  '${now.hour}:${now.minute}:${now.second}',
)
```

---

## 7️⃣ Formatting Date and Time (intl package)

### Step 1: Add dependency in pubspec.yaml
```yaml
dependencies:
  intl: ^0.18.1
```

---

### Step 2: Import package
```dart
import 'package:intl/intl.dart';
```

---

### Step 3: Format Date
```dart
String formattedDate = DateFormat('dd-MM-yyyy').format(now);
```

---

### Step 4: Format Time
```dart
String formattedTime = DateFormat('hh:mm a').format(now);
```

---

## 8️⃣ Common Date Formats

- `dd-MM-yyyy`
- `yyyy-MM-dd`
- `hh:mm a`
- `HH:mm:ss`

---

## 9️⃣ Live Updating Time (Timer)
```dart
Timer.periodic(Duration(seconds: 1), (timer) {
  setState(() {
    now = DateTime.now();
  });
});
```

---

## 🔟 Date Picker (Bonus)
```dart
showDatePicker(
  context: context,
  initialDate: DateTime.now(),
  firstDate: DateTime(2000),
  lastDate: DateTime(2100),
);
```

---

## 1️⃣1️⃣ Common Mistakes

- ❌ Forgetting intl dependency
- ❌ Not using setState for live updates
- ❌ Hardcoding date format

---

## 1️⃣2️⃣ Best Practices

- Use intl for formatting
- Keep date logic separate
- Update UI using setState

---

## 1️⃣3️⃣ Interview Questions

- How to get current date and time in Flutter?
- What is DateTime class?
- How to format date?

---

## 1️⃣4️⃣ Quick Revision Points

- `DateTime.now()` → current date & time
- `intl` → formatting
- `Timer` → live clock

---
