# Date Formatting in Flutter (intl Package)

## 1️⃣ What is Date Formatting?

Date formatting means changing date into readable format.

**Example:**

- `2026-01-24` → `24 Jan 2026`
- `2026-01-24 14:30:00` → `02:30 PM`

Flutter uses `intl` package for formatting dates.

---

## 2️⃣ Why Date Formatting is Important

- Better UI experience
- User-friendly date display
- Used in:
  - Chat apps
  - Booking apps
  - Attendance apps

---

## 3️⃣ Add intl Dependency (IMPORTANT)

Add in `pubspec.yaml`:
```yaml
dependencies:
  intl: ^0.18.1
```

Run:
```bash
flutter pub get
```

---

## 4️⃣ Import intl Package
```dart
import 'package:intl/intl.dart';
```

---

## 5️⃣ Get Current Date
```dart
DateTime now = DateTime.now();
```

---

## 6️⃣ Basic Date Formatting
```dart
String formattedDate = DateFormat('dd-MM-yyyy').format(now);
```

**Output example:**
```
24-01-2026
```

---

## 7️⃣ Common Date Format Patterns

| Pattern | Meaning      |
|---------|--------------|
| `dd`    | Day          |
| `MM`    | Month number |
| `MMM`   | Month name   |
| `yyyy`  | Year         |
| `HH`    | 24-hour      |
| `hh`    | 12-hour      |
| `mm`    | Minutes      |
| `a`     | AM / PM      |

---

## 8️⃣ Examples of Date Formats
```dart
DateFormat('dd MMM yyyy').format(now);   // 24 Jan 2026
DateFormat('yyyy-MM-dd').format(now);    // 2026-01-24
DateFormat('hh:mm a').format(now);       // 02:30 PM
DateFormat('HH:mm:ss').format(now);      // 14:30:45
```

---

## 9️⃣ Display Formatted Date in Text Widget
```dart
Text(
  DateFormat('dd MMM yyyy').format(DateTime.now()),
)
```

---

## 🔟 Formatting Custom Date
```dart
DateTime customDate = DateTime(2025, 12, 31);
String date = DateFormat('dd/MM/yyyy').format(customDate);
```

---

## 1️⃣1️⃣ Formatting Date from Timestamp
```dart
DateTime date = DateTime.fromMillisecondsSinceEpoch(timestamp);
String formatted = DateFormat('dd-MM-yyyy').format(date);
```

---

## 1️⃣2️⃣ Common Mistakes

- ❌ Forgetting to add intl dependency
- ❌ Wrong format symbols
- ❌ Not importing intl package

---

## 1️⃣3️⃣ Best Practices

- Use intl for all date formatting
- Keep formats consistent
- Avoid manual string formatting

---

## 1️⃣4️⃣ Interview Questions

- How to format date in Flutter?
- What is intl package?
- Difference between dd and MM?

---

## 1️⃣5️⃣ Quick Revision Points

- `intl` package used for formatting
- `DateFormat` handles patterns
- `DateTime` provides raw date

---
