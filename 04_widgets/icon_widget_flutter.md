# Icon Widget in Flutter

## 1️⃣ What is Icon Widget?

`Icon` widget is used to display icons in a Flutter application.

Flutter provides Material Icons by default.

**Simple meaning:**

> Icon = small graphic symbol (like home, call, menu)

---

## 2️⃣ Why Icon Widget is Important

- Improves UI and user understanding
- Makes app visually attractive
- Used in buttons, app bars, lists, etc.

---

## 3️⃣ Basic Icon Syntax
```dart
Icon(
  Icons.home,
)
```

---

## 4️⃣ Icon with Size and Color
```dart
Icon(
  Icons.favorite,
  color: Colors.red,
  size: 30,
)
```

---

## 5️⃣ Commonly Used Icon Properties

- `icon`: Type of icon (`Icons.home`)
- `color`: Color of icon
- `size`: Size of icon in pixels
- `semanticLabel`: Accessibility text

---

## 6️⃣ Using Icon Inside Buttons
```dart
ElevatedButton.icon(
  onPressed: () {},
  icon: Icon(Icons.send),
  label: Text('Send'),
)
```

---

## 7️⃣ Using IconButton
```dart
IconButton(
  icon: Icon(Icons.add),
  onPressed: () {
    print('Icon pressed');
  },
)
```

---

## 8️⃣ Custom Icons

Flutter supports custom icons using:

- Icon fonts
- SVG icons (using packages)

**Example with custom font:**
```dart
Icon(
  IconData(0xe900, fontFamily: 'CustomIcons'),
)
```

---

## 9️⃣ Common Mistakes

- ❌ Forgetting to import material.dart
- ❌ Using very large icon sizes
- ❌ Not adding onPressed in IconButton

---

## 🔟 Best Practices

- Use icons meaningfully
- Keep icon size consistent
- Use material icons for standard UI

---

## 1️⃣1️⃣ Interview Questions

- What is Icon widget?
- Difference between Icon and IconButton?
- How to use custom icons?

---

## 1️⃣2️⃣ Quick Revision Points

- Icon widget displays symbols
- Uses `Icons.` class
- Can control color & size
- IconButton = clickable icon
