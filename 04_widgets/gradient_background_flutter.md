# Gradient as App Background in Flutter

## 1️⃣ What is Gradient?

- Gradient means **smooth transition from one color to another**.
- Used to make beautiful backgrounds instead of plain single color.

**Examples:**

- Blue → Purple background
- Red → Orange → Yellow background
- Top to bottom color change

---

## 2️⃣ Why Use Gradient?

- Looks more professional and modern
- Better UI than plain color
- No image needed for colorful background

---

## 3️⃣ Types of Gradient in Flutter

1. **LinearGradient** → colors change in a line (left→right, top→bottom)
2. **RadialGradient** → colors spread from center outward (circle)
3. **SweepGradient** → colors sweep around a center point (like clock)

---

## 4️⃣ How to Apply Gradient as Background

- Use `Container` with `BoxDecoration`
- Set `gradient` property inside `BoxDecoration`
- Make Container cover full screen using `double.infinity`
```dart
Container(
  width: double.infinity,
  height: double.infinity,
  decoration: BoxDecoration(
    gradient: LinearGradient(
      colors: [Colors.blue, Colors.purple],
    ),
  ),
)
```

---

## 5️⃣ LinearGradient (MOST USED)

- Colors change in a straight line direction
```dart
LinearGradient(
  colors: [Colors.blue, Colors.purple],
  begin: Alignment.topLeft,
  end: Alignment.bottomRight,
)
```

**Direction options:**

- `Alignment.topCenter` → `Alignment.bottomCenter` (top to bottom)
- `Alignment.centerLeft` → `Alignment.centerRight` (left to right)
- `Alignment.topLeft` → `Alignment.bottomRight` (diagonal)

---

## 6️⃣ Full Background Gradient Example
```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: Container(
          width: double.infinity,
          height: double.infinity,
          decoration: BoxDecoration(
            gradient: LinearGradient(
              colors: [Colors.blue, Colors.purple],
              begin: Alignment.topLeft,
              end: Alignment.bottomRight,
            ),
          ),
          child: Center(
            child: Text(
              'Gradient Background',
              style: TextStyle(
                color: Colors.white,
                fontSize: 24,
                fontWeight: FontWeight.bold,
              ),
            ),
          ),
        ),
      ),
    );
  }
}
```

---

## 7️⃣ LinearGradient with Multiple Colors
```dart
LinearGradient(
  colors: [Colors.red, Colors.orange, Colors.yellow],
  begin: Alignment.topCenter,
  end: Alignment.bottomCenter,
)
```

---

## 8️⃣ LinearGradient with Stops

- `stops` control where each color starts and ends
- Values between 0.0 to 1.0
```dart
LinearGradient(
  colors: [Colors.blue, Colors.green, Colors.yellow],
  stops: [0.0, 0.5, 1.0],  // blue at start, green at middle, yellow at end
  begin: Alignment.topCenter,
  end: Alignment.bottomCenter,
)
```

---

## 9️⃣ RadialGradient

- Colors spread outward from center like a circle
```dart
Container(
  width: double.infinity,
  height: double.infinity,
  decoration: BoxDecoration(
    gradient: RadialGradient(
      colors: [Colors.yellow, Colors.orange, Colors.red],
      center: Alignment.center,
      radius: 0.8,
    ),
  ),
)
```

---

## 🔟 SweepGradient

- Colors sweep around a center point like a clock hand
```dart
Container(
  width: 200,
  height: 200,
  decoration: BoxDecoration(
    shape: BoxShape.circle,
    gradient: SweepGradient(
      colors: [Colors.red, Colors.blue, Colors.green, Colors.red],
      center: Alignment.center,
    ),
  ),
)
```

---

## 1️⃣1️⃣ Gradient Comparison

| Type | Look | Use Case |
|---|---|---|
| LinearGradient | Straight line | App backgrounds, buttons |
| RadialGradient | Circle outward | Spotlight effect |
| SweepGradient | Clock sweep | Color wheels, loaders |

---

## 1️⃣2️⃣ Gradient on AppBar
```dart
AppBar(
  flexibleSpace: Container(
    decoration: BoxDecoration(
      gradient: LinearGradient(
        colors: [Colors.blue, Colors.purple],
        begin: Alignment.topLeft,
        end: Alignment.bottomRight,
      ),
    ),
  ),
  title: Text('Gradient AppBar'),
)
```

---

## 1️⃣3️⃣ Gradient on Button
```dart
Container(
  decoration: BoxDecoration(
    borderRadius: BorderRadius.circular(12),
    gradient: LinearGradient(
      colors: [Colors.pink, Colors.orange],
    ),
  ),
  child: ElevatedButton(
    onPressed: () {},
    style: ElevatedButton.styleFrom(
      backgroundColor: Colors.transparent,
      shadowColor: Colors.transparent,
    ),
    child: Text('Gradient Button'),
  ),
)
```

---

## 1️⃣4️⃣ Common Mistakes

- ❌ Applying gradient directly on Scaffold → won't work
- ❌ Forgetting `width` and `height` on Container → gradient won't show
- ❌ Not using `BoxDecoration` → gradient property not available without it
- ❌ Using `color` and `gradient` together in BoxDecoration → error

> **Note:** You cannot use `color` and `gradient` at the same time in `BoxDecoration`

---

## 1️⃣5️⃣ Interview Questions

- What are the types of Gradient in Flutter?
- How to apply gradient as app background?
- What is the difference between LinearGradient and RadialGradient?
- What do `stops` do in LinearGradient?
- Can you use `color` and `gradient` together in BoxDecoration?

---

## 1️⃣6️⃣ Quick Revision Points

- Gradient = smooth color transition
- 3 types → Linear, Radial, Sweep
- Always use `BoxDecoration` to apply gradient
- `Container` with `double.infinity` for full screen background
- `begin` and `end` control direction in LinearGradient
- `stops` control where each color appears
- Cannot use `color` and `gradient` together in BoxDecoration
- Works on background, AppBar, buttons — anywhere with BoxDecoration
