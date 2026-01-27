# RichText Widget in Flutter

## 1️⃣ What is RichText Widget?

`RichText` widget is used to display text with multiple styles in a single line or paragraph.

It allows styling different words or characters differently.

**Simple meaning:**

> One text, many styles

---

## 2️⃣ Why RichText is Important

When you need multiple colors, sizes, or styles in one text

**Used for:**

- Highlighted words
- Terms & conditions
- Mixed bold / normal text

---

## 3️⃣ Difference Between Text and RichText

| Text Widget    | RichText Widget   |
|----------------|-------------------|
| Single style   | Multiple styles   |
| Simple usage   | Advanced usage    |
| Easy           | Slightly complex  |

---

## 4️⃣ Basic RichText Syntax
```dart
RichText(
  text: TextSpan(
    text: 'Hello ',
    style: TextStyle(color: Colors.black, fontSize: 16),
    children: [
      TextSpan(
        text: 'Flutter',
        style: TextStyle(color: Colors.blue, fontWeight: FontWeight.bold),
      ),
    ],
  ),
)
```

---

## 5️⃣ Important Components

### 🔹 TextSpan

- Represents a part of text
- Can have its own style

### 🔹 children

- Used to add multiple TextSpan inside RichText

---

## 6️⃣ Styling TextSpan
```dart
TextSpan(
  text: 'Important',
  style: TextStyle(
    color: Colors.red,
    fontSize: 18,
    fontWeight: FontWeight.bold,
  ),
)
```

---

## 7️⃣ Clickable Text using RichText
```dart
RichText(
  text: TextSpan(
    text: 'Don't have an account? ',
    style: TextStyle(color: Colors.black),
    children: [
      TextSpan(
        text: 'Sign Up',
        style: TextStyle(color: Colors.blue),
        recognizer: TapGestureRecognizer()
          ..onTap = () {
            print('Sign Up clicked');
          },
      ),
    ],
  ),
)
```

⚠️ **Requires:**
```dart
import 'package:flutter/gestures.dart';
```

---

## 8️⃣ Common Mistakes

- ❌ Forgetting default style in parent TextSpan
- ❌ Using RichText when simple Text is enough
- ❌ Missing gesture import for clickable text

---

## 9️⃣ Best Practices

- Use Text widget for simple text
- Use RichText only when multiple styles needed
- Keep styles readable

---

## 🔟 Interview Questions

- What is RichText widget?
- Difference between Text and RichText?
- What is TextSpan?
- How to make clickable text in Flutter?

---

## 1️⃣1️⃣ Quick Revision Points

- RichText = multi-style text
- Uses `TextSpan`
- `children` property adds more styles
- Can make text clickable
