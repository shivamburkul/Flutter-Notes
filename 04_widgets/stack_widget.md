# Stack Widget in Flutter

## 1️⃣ What is Stack Widget?

`Stack` is a widget used to place widgets on top of each other.

Widgets are layered one above another.

**Simple meaning:**

> One widget over another widget

---

## 2️⃣ Why Stack is Important

- Used for overlapping UI

**Common use cases:**

- Profile image with edit icon
- Image with text overlay
- Floating badge on icon

---

## 3️⃣ Basic Stack Example
```dart
Stack(
  children: [
    Container(
      height: 200,
      width: 200,
      color: Colors.blue,
    ),
    Container(
      height: 100,
      width: 100,
      color: Colors.red,
    ),
  ],
)
```

- First widget is at bottom
- Last widget is on top

---

## 4️⃣ Using Positioned Widget

`Positioned` controls where widget appears inside Stack
```dart
Stack(
  children: [
    Container(height: 200, width: 200, color: Colors.grey),
    Positioned(
      top: 20,
      left: 20,
      child: Icon(Icons.star, size: 40),
    ),
  ],
)
```

---

## 5️⃣ Positioned Properties

- `top`
- `bottom`
- `left`
- `right`

Used to control exact position.

---

## 6️⃣ Stack Alignment
```dart
Stack(
  alignment: Alignment.center,
  children: [
    Container(height: 200, width: 200, color: Colors.blue),
    Text('Center Text'),
  ],
)
```

---

## 7️⃣ Stack with Image & Text Overlay (Very Common)
```dart
Stack(
  children: [
    Image.network('https://example.com/image.jpg'),
    Positioned(
      bottom: 10,
      left: 10,
      child: Text(
        'Title',
        style: TextStyle(color: Colors.white, fontSize: 20),
      ),
    ),
  ],
)
```

---

## 8️⃣ Stack vs Column / Row

| Stack          | Column / Row    |
|----------------|-----------------|
| Overlapping    | No overlapping  |
| Z-axis         | Linear layout   |
| Used for layers| Used for lists  |

---

## 9️⃣ Common Mistakes

- ❌ Forgetting height/width in Stack
- ❌ Overusing Stack
- ❌ Wrong positioning values

---

## 🔟 Best Practices

- Use Stack only when overlapping is required
- Prefer Positioned for control
- Keep Stack small

---

## 1️⃣1️⃣ Interview Questions

- What is Stack widget?
- Difference between Stack & Column?
- What is Positioned widget?

---

## 1️⃣2️⃣ Quick Revision Points

- Stack = overlapping widgets
- Positioned = control position
- Last child appears on top

---
