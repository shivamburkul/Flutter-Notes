# Row and Column Widgets (Layout in Flutter)

## 1️⃣ What are Row and Column?

- `Row` and `Column` are layout widgets in Flutter.
- They are used to arrange widgets horizontally or vertically.

| Widget | Direction                      |
|--------|--------------------------------|
| Row    | Left → Right (Horizontal)      |
| Column | Top → Bottom (Vertical)        |

---

## 2️⃣ Basic Structure

### Row Example
```dart
Row(
  children: [
    Text('A'),
    Text('B'),
    Text('C'),
  ],
)
```

### Column Example
```dart
Column(
  children: [
    Text('A'),
    Text('B'),
    Text('C'),
  ],
)
```

---

## 3️⃣ Main Properties (VERY IMPORTANT)

### 🔹 mainAxisAlignment

Controls alignment along main direction

- Row → horizontal
- Column → vertical

**Values:**

- `start`
- `center`
- `end`
- `spaceBetween`
- `spaceAround`
- `spaceEvenly`

**Example:**
```dart
Row(
  mainAxisAlignment: MainAxisAlignment.spaceEvenly,
  children: [
    Icon(Icons.star),
    Icon(Icons.star),
    Icon(Icons.star),
  ],
)
```

### 🔹 crossAxisAlignment

Controls alignment perpendicular to main axis

**Values:**

- `start`
- `center`
- `end`
- `stretch`
- `baseline` (needs text)

**Example:**
```dart
Column(
  crossAxisAlignment: CrossAxisAlignment.start,
  children: [
    Text('Hello'),
    Text('Flutter'),
  ],
)
```

---

## 4️⃣ Main Axis vs Cross Axis (INTERVIEW IMPORTANT)

### Row

- Main Axis → Horizontal
- Cross Axis → Vertical

### Column

- Main Axis → Vertical
- Cross Axis → Horizontal

---

## 5️⃣ SizedBox with Row & Column

Used for spacing between widgets.
```dart
Row(
  children: [
    Icon(Icons.home),
    SizedBox(width: 20),
    Icon(Icons.settings),
  ],
)
```

---

## 6️⃣ Expanded Widget (MOST IMPORTANT)

- Used inside Row or Column
- Takes available space
```dart
Row(
  children: [
    Expanded(
      child: Container(color: Colors.red),
    ),
    Expanded(
      child: Container(color: Colors.blue),
    ),
  ],
)
```

---

## 7️⃣ Flexible Widget

- Similar to `Expanded`
- More control over space
```dart
Row(
  children: [
    Flexible(
      flex: 1,
      child: Container(color: Colors.green),
    ),
    Flexible(
      flex: 2,
      child: Container(color: Colors.yellow),
    ),
  ],
)
```

---

## 8️⃣ Nested Row & Column (VERY COMMON)
```dart
Column(
  children: [
    Text('Profile'),
    Row(
      children: [
        Icon(Icons.person),
        Text('User Name'),
      ],
    ),
  ],
)
```

---

## 9️⃣ Common Errors & Fixes

### ❌ Overflow Error (Yellow/Black Stripes)

**Cause:**

- Row widgets exceed screen width

**Fix:**

- Use `Expanded`
- Wrap with `SingleChildScrollView`

---

## 🔟 Row vs Column Summary

| Feature   | Row        | Column     |
|-----------|------------|------------|
| Direction | Horizontal | Vertical   |
| mainAxis  | X-axis     | Y-axis     |
| common use| buttons, icons | forms, text |

---

## 1️⃣1️⃣ Best Practices

- Always think about screen size
- Use `Expanded` to avoid overflow
- Combine with `Padding` & `SizedBox`
- Keep layouts simple

---

## 1️⃣2️⃣ Quick Revision Points

- Row = horizontal layout
- Column = vertical layout
- `mainAxisAlignment` = main direction
- `crossAxisAlignment` = opposite direction
- `Expanded` avoids overflow

---
