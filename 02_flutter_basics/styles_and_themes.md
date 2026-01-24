# Flutter Styles and Themes (TextStyle, ThemeData)

## 1️⃣ What are Styles in Flutter?

Styles define how UI looks.

**Includes:**

- Text color
- Font size
- Font weight
- Background color
- Button style

Styles are mostly applied using `TextStyle` and widget properties.

---

## 2️⃣ TextStyle in Flutter (MOST IMPORTANT)

Used to style Text widget.
```dart
Text(
  'Hello Flutter',
  style: TextStyle(
    fontSize: 20,
    color: Colors.blue,
    fontWeight: FontWeight.bold,
    fontStyle: FontStyle.italic,
  ),
)
```

---

## 3️⃣ Common TextStyle Properties

- `fontSize`
- `color`
- `fontWeight`
- `fontStyle`
- `letterSpacing`
- `wordSpacing`
- `height`

**Example:**
```dart
TextStyle(
  fontSize: 18,
  letterSpacing: 1.2,
  wordSpacing: 2,
)
```

---

## 4️⃣ Styling Widgets Using ThemeData

`ThemeData` defines global styles for the app.

Applied in `MaterialApp`.
```dart
MaterialApp(
  theme: ThemeData(
    primaryColor: Colors.blue,
  ),
  home: MyHomePage(),
)
```

---

## 5️⃣ Why Themes are IMPORTANT

**Without Theme:**

- Repeating styles everywhere

**With Theme:**

- Centralized styling
- Easy UI changes
- Clean code

---

## 6️⃣ Applying Text Theme Globally
```dart
MaterialApp(
  theme: ThemeData(
    textTheme: TextTheme(
      bodyMedium: TextStyle(fontSize: 16),
      titleLarge: TextStyle(fontSize: 24, fontWeight: FontWeight.bold),
    ),
  ),
)
```

**Usage:**
```dart
Text('Hello', style: Theme.of(context).textTheme.bodyMedium)
```

---

## 7️⃣ Button Styles using Theme
```dart
ThemeData(
  elevatedButtonTheme: ElevatedButtonThemeData(
    style: ElevatedButton.styleFrom(
      backgroundColor: Colors.green,
      textStyle: TextStyle(fontSize: 18),
    ),
  ),
)
```

---

## 8️⃣ Dark Theme & Light Theme
```dart
MaterialApp(
  theme: ThemeData.light(),
  darkTheme: ThemeData.dark(),
  themeMode: ThemeMode.system,
)
```

---

## 9️⃣ Accessing Theme Anywhere
```dart
Theme.of(context).primaryColor
```

---

## 🔟 Inline Style vs Theme Style

| Inline Style    | Theme Style     |
|-----------------|-----------------|
| Repeated code   | Centralized     |
| Hard to manage  | Easy to manage  |
| Not scalable    | Scalable        |

---

## 1️⃣1️⃣ Common Mistakes

- ❌ Overusing inline styles
- ❌ Not using ThemeData
- ❌ Hardcoding colors everywhere

---

## 1️⃣2️⃣ Best Practices

- Use ThemeData for global styles
- Keep colors & fonts centralized
- Use TextTheme

---

## 1️⃣3️⃣ Interview Questions

- What is ThemeData?
- Difference between TextStyle & ThemeData?
- How to implement dark mode?

---

## 1️⃣4️⃣ Quick Revision Points

- TextStyle styles text
- ThemeData styles whole app
- Use themes for consistency

---
