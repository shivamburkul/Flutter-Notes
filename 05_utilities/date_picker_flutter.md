# Flutter Date Picker Tutorial

## 1️⃣ What is Date Picker?

Date Picker allows user to select a date from calendar UI.

**Used in:**

- Forms
- Booking apps
- DOB selection
- Attendance apps

Flutter provides built-in Date Picker dialog.

---

## 2️⃣ Why Date Picker is Important

- Avoids manual date input
- Reduces user errors
- Better UX

---

## 3️⃣ Basic Date Picker Function
```dart
Future<void> selectDate(BuildContext context) async {
  DateTime? pickedDate = await showDatePicker(
    context: context,
    initialDate: DateTime.now(),
    firstDate: DateTime(2000),
    lastDate: DateTime(2100),
  );
}
```

---

## 4️⃣ Using Date Picker with Button
```dart
ElevatedButton(
  onPressed: () {
    selectDate(context);
  },
  child: Text('Select Date'),
)
```

---

## 5️⃣ Store Selected Date
```dart
DateTime selectedDate = DateTime.now();

Future<void> selectDate(BuildContext context) async {
  DateTime? picked = await showDatePicker(
    context: context,
    initialDate: selectedDate,
    firstDate: DateTime(2000),
    lastDate: DateTime(2100),
  );
  
  if (picked != null) {
    setState(() {
      selectedDate = picked;
    });
  }
}
```

---

## 6️⃣ Display Selected Date
```dart
Text(
  DateFormat('dd MMM yyyy').format(selectedDate),
)
```

---

## 7️⃣ Date Picker Properties Explained

- `context` → current screen
- `initialDate` → default selected date
- `firstDate` → minimum selectable date
- `lastDate` → maximum selectable date

---

## 8️⃣ Restrict Future or Past Dates

**Only past dates:**
```dart
lastDate: DateTime.now()
```

**Only future dates:**
```dart
firstDate: DateTime.now()
```

---

## 9️⃣ Custom Theme for Date Picker
```dart
showDatePicker(
  context: context,
  initialDate: DateTime.now(),
  firstDate: DateTime(2000),
  lastDate: DateTime(2100),
  builder: (context, child) {
    return Theme(
      data: ThemeData.light().copyWith(
        colorScheme: ColorScheme.light(
          primary: Colors.blue,
        ),
      ),
      child: child!,
    );
  },
);
```

---

## 🔟 Date Picker with TextField (Common Use)
```dart
TextField(
  readOnly: true,
  onTap: () {
    selectDate(context);
  },
  decoration: InputDecoration(
    labelText: 'Select Date',
  ),
)
```

---

## 1️⃣1️⃣ Common Mistakes

- ❌ Not handling null picked date
- ❌ Forgetting setState
- ❌ Allowing invalid date range

---

## 1️⃣2️⃣ Best Practices

- Always check for null
- Use formatted date
- Restrict date range properly

---

## 1️⃣3️⃣ Interview Questions

- How to show Date Picker in Flutter?
- What is showDatePicker?
- How to restrict dates?

---

## 1️⃣4️⃣ Quick Revision Points

- `showDatePicker()` → opens calendar
- Returns DateTime
- Use intl for formatting

---
