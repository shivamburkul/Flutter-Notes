# Positioned Widget in Flutter

## 1️⃣ What is Positioned Widget?

`Positioned` widget is used inside a `Stack` widget.

It helps to place a widget at a specific position using `top`, `left`, `right`, `bottom`.

**Simple meaning:**

> Positioned = exact placement of widget inside Stack

---

## 2️⃣ Important Rule (VERY IMPORTANT)

⚠️ `Positioned` ONLY works inside `Stack`

❌ Using `Positioned` outside `Stack` → ERROR

---

## 3️⃣ Why Positioned Widget is Used

- To place widgets on top of each other
- To control exact location of a widget

**Used for:**

- Floating buttons
- Badges
- Image overlays
- Custom UI layouts

---

## 4️⃣ Basic Positioned Example
```dart
Stack(
  children: [
    Container(
      width: 200,
      height: 200,
      color: Colors.blue,
    ),
    Positioned(
      top: 20,
      left: 30,
      child: Container(
        width: 50,
        height: 50,
        color: Colors.red,
      ),
    ),
  ],
)
```

---

## 5️⃣ Positioned Properties

- `top`: distance from top
- `bottom`: distance from bottom
- `left`: distance from left
- `right`: distance from right
- `width`: fixed width
- `height`: fixed height

---

## 6️⃣ Using Multiple Positioned Widgets
```dart
Stack(
  children: [
    Positioned(top: 10, left: 10, child: Icon(Icons.star)),
    Positioned(bottom: 10, right: 10, child: Icon(Icons.favorite)),
  ],
)
```

---

## 7️⃣ Positioned.fill

Fills the available Stack space
```dart
Positioned.fill(
  child: Container(color: Colors.black12),
)
```

---

## 8️⃣ Positioned vs Align

| Positioned          | Align                |
|---------------------|----------------------|
| Exact position      | Relative alignment   |
| Uses top/left       | Uses alignment       |
| Only inside Stack   | Can be used anywhere |

---

## 9️⃣ Common Mistakes

- ❌ Using Positioned outside Stack
- ❌ Giving conflicting values (top + bottom + height)
- ❌ Forgetting Stack parent

---

## 🔟 Best Practices

- Use Positioned only when exact placement needed
- Prefer Align for simple positioning
- Keep UI responsive

---

## 1️⃣1️⃣ Interview Questions

- What is Positioned widget?
- Where can Positioned be used?
- Difference between Positioned and Align?
- What is Positioned.fill?

---

## 1️⃣2️⃣ Quick Revision Points

- Positioned works ONLY inside Stack
- Uses `top`, `bottom`, `left`, `right`
- Used for overlay & custom layouts
- Exact positioning widget
