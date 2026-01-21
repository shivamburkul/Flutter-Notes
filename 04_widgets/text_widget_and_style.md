# Text Widget & TextStyle in Flutter (Complete Notes)

This file contains everything about the Text widget and TextStyle needed for UI building, revision, and interviews.

---

## 1. What is Text Widget?

- `Text` is a basic UI widget in Flutter
- Used to display text on the screen
- Supports styling, alignment, overflow handling, and more
- It is one of the most used widgets in Flutter

---

## 2. Basic Syntax
```dart
Text('Hello Flutter')
```

---

## 3. Text with TextStyle
```dart
Text(
  'Hello Flutter',
  style: TextStyle(
    fontSize: 20,
    color: Colors.blue,
  ),
)
```

- `style` controls appearance of text

---

## 4. TextStyle Properties (IMPORTANT)

### 4.1 fontSize
```dart
fontSize: 18
```

- Controls size of text (logical pixels)

---

### 4.2 color
```dart
color: Colors.red
```

- Sets text color

---

### 4.3 fontWeight
```dart
fontWeight: FontWeight.bold
```

**Common values:**

- `FontWeight.w100` to `FontWeight.w900`
- `FontWeight.normal`
- `FontWeight.bold`

---

### 4.4 fontStyle
```dart
fontStyle: FontStyle.italic
```

---

### 4.5 letterSpacing
```dart
letterSpacing: 2
```

- Space between letters

---

### 4.6 wordSpacing
```dart
wordSpacing: 5
```

- Space between words

---

### 4.7 height (Line Height)
```dart
height: 1.5
```

- Controls line spacing

---

### 4.8 backgroundColor
```dart
backgroundColor: Colors.yellow
```

---

### 4.9 decoration (Underline / Line-through)
```dart
decoration: TextDecoration.underline
```

**Other values:**

- `TextDecoration.lineThrough`
- `TextDecoration.overline`

---

### 4.10 decorationColor & decorationStyle
```dart
decorationColor: Colors.red,
decorationStyle: TextDecorationStyle.dashed,
```

---

## 5. Text Alignment
```dart
Text(
  'Center Text',
  textAlign: TextAlign.center,
)
```

**Common values:**

- `TextAlign.left`
- `TextAlign.right`
- `TextAlign.center`
- `TextAlign.justify`

---

## 6. Max Lines & Overflow
```dart
Text(
  'Long long text...',
  maxLines: 2,
  overflow: TextOverflow.ellipsis,
)
```

**Overflow options:**

- `ellipsis` (...)
- `fade`
- `clip`

---

## 7. Soft Wrap
```dart
softWrap: true
```

- Allows text to wrap to next line

---

## 8. Text Direction
```dart
textDirection: TextDirection.ltr
```

**Values:**

- `ltr` (left to right)
- `rtl` (right to left)

---

## 9. Rich Text (Multiple Styles)
```dart
Text.rich(
  TextSpan(
    text: 'Hello ',
    children: [
      TextSpan(
        text: 'Flutter',
        style: TextStyle(fontWeight: FontWeight.bold),
      ),
    ],
  ),
)
```

---

## 10. Custom Fonts (Overview)

**Steps:**

1. Add font files in `assets/fonts/`
2. Declare in `pubspec.yaml`
3. Use in TextStyle
```dart
fontFamily: 'Poppins'
```

---

## 11. Common Mistakes

- Forgetting `maxLines` for long text
- Using too large `fontSize`
- Not handling overflow
- Forgetting to add custom font in `pubspec.yaml`

---

## 12. Performance Tips

- Avoid unnecessary `RichText`
- Reuse `TextStyle` when possible
- Prefer `const Text` when text is static
```dart
const Text('Hello')
```

---

## 13. Interview Questions

- Difference between Text and RichText?
- What is TextOverflow?
- How to apply custom fonts?
- How to underline text?

---

## 14. Summary

- `Text` widget displays text
- `TextStyle` controls appearance
- Supports alignment, overflow, decoration
- Very important for UI design

---
