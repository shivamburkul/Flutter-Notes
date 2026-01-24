# Wrap Widget in Flutter

## 1️⃣ What is Wrap Widget?

`Wrap` widget is used to display child widgets in horizontal or vertical direction and automatically wraps to next line when space runs out.

Useful for dynamic layouts.

**Simple meaning:**

> Auto-wrap widgets to new line instead of overflowing

---

## 2️⃣ Why Wrap Widget is Important

- Prevents overflow error (Overflowed by pixels)
- Flexible layouts

**Used in:**

- Tags
- Chips
- Dynamic buttons
- Responsive UI

---

## 3️⃣ Basic Example of Wrap
```dart
Wrap(
  children: [
    Container(width: 100, height: 50, color: Colors.red),
    Container(width: 100, height: 50, color: Colors.green),
    Container(width: 100, height: 50, color: Colors.blue),
    Container(width: 100, height: 50, color: Colors.orange),
  ],
)
```

Widgets automatically move to next line if there is no space

---

## 4️⃣ Wrap Properties

- `direction`: `Axis.horizontal` / `Axis.vertical`
- `spacing`: Horizontal spacing between children
- `runSpacing`: Vertical spacing between lines
- `alignment`: Alignment of children on main axis
- `runAlignment`: Alignment of lines
- `crossAxisAlignment`: Alignment of children on cross axis

---

## 5️⃣ Example with Properties
```dart
Wrap(
  spacing: 10,
  runSpacing: 20,
  alignment: WrapAlignment.center,
  children: [
    Chip(label: Text('Flutter')),
    Chip(label: Text('Dart')),
    Chip(label: Text('Widget')),
    Chip(label: Text('Wrap')),
  ],
)
```

---

## 6️⃣ Common Mistakes

- ❌ Using Row when Wrap needed → causes overflow
- ❌ Forgetting spacing / runSpacing
- ❌ Using Wrap for very heavy lists → performance issue

---

## 7️⃣ Best Practices

- Use for tags, chips, buttons that can wrap
- Avoid for long scrollable lists → use GridView or ListView
- Adjust spacing for better UI

---

## 8️⃣ Interview Questions

- What is Wrap widget?
- Difference between Row and Wrap?
- What properties does Wrap have?
- When to use Wrap?

---

## 9️⃣ Quick Revision Points

- Wrap = auto line-break widget container
- `direction`, `spacing`, `runSpacing` = important properties
- `alignment` & `runAlignment` = for child & line placement
- Avoid Row overflow, use Wrap

---
