# Buttons in Flutter (Complete Guide)

This file covers ALL types of buttons in Flutter, their properties, usage, examples, mistakes, and interview points.

---

## 1. What are Buttons in Flutter?

- Buttons are used to perform actions on user interaction (tap/click)
- Flutter provides pre-built Material buttons
- Buttons trigger logic using the `onPressed` callback

---

## 2. Common Button Rules

- All buttons need an `onPressed` function
- If `onPressed: null` → button becomes disabled
- Buttons usually contain `Text`, `Icon`, or both

---

## 3. ElevatedButton (Most Used)

### 3.1 What is ElevatedButton?

- Used for primary actions
- Has background color and elevation (shadow)

### 3.2 Basic Example
```dart
ElevatedButton(
  onPressed: () {
    print('Button clicked');
  },
  child: Text('Click Me'),
)
```

---

### 3.3 Styling ElevatedButton
```dart
ElevatedButton(
  onPressed: () {},
  style: ElevatedButton.styleFrom(
    backgroundColor: Colors.blue,
    foregroundColor: Colors.white,
    padding: EdgeInsets.symmetric(horizontal: 20, vertical: 12),
    shape: RoundedRectangleBorder(
      borderRadius: BorderRadius.circular(10),
    ),
  ),
  child: Text('Styled Button'),
)
```

---

## 4. TextButton

### 4.1 What is TextButton?

- Flat button with no background
- Used for secondary actions

### 4.2 Example
```dart
TextButton(
  onPressed: () {},
  child: Text('Text Button'),
)
```

---

## 5. OutlinedButton

### 5.1 What is OutlinedButton?

- Button with border outline
- Used when you want emphasis without background

### 5.2 Example
```dart
OutlinedButton(
  onPressed: () {},
  child: Text('Outlined Button'),
)
```

---

## 6. IconButton

### 6.1 What is IconButton?

- Button that contains only an icon
- Used in AppBar, toolbars, etc.

### 6.2 Example
```dart
IconButton(
  onPressed: () {},
  icon: Icon(Icons.add),
)
```

---

## 7. FloatingActionButton (FAB)

### 7.1 What is FAB?

- Circular button for primary screen action
- Mostly used inside `Scaffold`

### 7.2 Example
```dart
FloatingActionButton(
  onPressed: () {},
  child: Icon(Icons.add),
)
```

---

## 8. Button with Icon + Text
```dart
ElevatedButton.icon(
  onPressed: () {},
  icon: Icon(Icons.send),
  label: Text('Send'),
)
```

---

## 9. Button Size Control
```dart
SizedBox(
  width: 200,
  height: 50,
  child: ElevatedButton(
    onPressed: () {},
    child: Text('Big Button'),
  ),
)
```

---

## 10. Disable Button
```dart
ElevatedButton(
  onPressed: null,
  child: Text('Disabled'),
)
```

---

## 11. Button Themes (Overview)
```dart
ThemeData(
  elevatedButtonTheme: ElevatedButtonThemeData(
    style: ElevatedButton.styleFrom(),
  ),
)
```

---

## 12. Old Buttons (Deprecated)

⚠️ **DO NOT USE (Deprecated)**

- `RaisedButton`
- `FlatButton`
- `OutlineButton`

**Use:**

- `ElevatedButton`
- `TextButton`
- `OutlinedButton`

---

## 13. Common Mistakes

- Forgetting `onPressed`
- Using deprecated buttons
- Over-styling buttons
- Not handling button disable state

---

## 14. Interview Questions

- Difference between ElevatedButton & TextButton?
- What happens when onPressed is null?
- How to style buttons globally?

---

## 15. Summary

- Flutter provides multiple button types
- `ElevatedButton` is most commonly used
- Buttons trigger actions via `onPressed`
- Styling is done using `styleFrom`

---

✅ This file is enough for complete button revision
