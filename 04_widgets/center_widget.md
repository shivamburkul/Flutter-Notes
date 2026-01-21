# Center Widget in Flutter (Complete Notes)

This file contains everything about the Center widget for clear understanding, long-term revision, and interview preparation.

---

## 1. What is Center Widget?

- `Center` is a layout widget in Flutter
- It is used to center a child widget both horizontally and vertically
- It can have only **ONE child**

👉 Simply: `Center` puts its child exactly in the middle of available space

---

## 2. Basic Syntax
```dart
Center(
  child: Widget,
)
```

---

## 3. Simple Example
```dart
Center(
  child: Text('Hello Flutter'),
)
```

- Text will appear in the center of the screen

---

## 4. Center with Container
```dart
Center(
  child: Container(
    height: 100,
    width: 100,
    color: Colors.blue,
  ),
)
```

- Container is centered inside its parent

---

## 5. How Center Works Internally

- `Center` is a special case of `Align` widget
- Internally equivalent to:
```dart
Align(
  alignment: Alignment.center,
  child: Widget,
)
```

---

## 6. Center vs Align

| Feature    | Center         | Align             |
|------------|----------------|-------------------|
| Alignment  | Only center    | Any alignment     |
| Simplicity | Very simple    | More flexible     |
| Use case   | Center content | Custom positioning|

---

## 7. Size Behavior of Center

- `Center` takes maximum available space from parent
- Child is placed in the center of that space
- If parent has limited size → child centers within it

---

## 8. Center inside Column or Row
```dart
Column(
  children: [
    Text('Top'),
    Center(
      child: Text('Middle'),
    ),
    Text('Bottom'),
  ],
)
```

⚠️ In Column / Row, `Center` only centers in available space, not full screen

---

## 9. Center with Expanded
```dart
Column(
  children: [
    Expanded(
      child: Center(
        child: Text('Centered'),
      ),
    ),
  ],
)
```

- `Expanded` gives full space
- `Center` then centers inside it

---

## 10. Center vs SizedBox

- `Center` → positions widget
- `SizedBox` → controls size
```dart
SizedBox(
  height: 200,
  child: Center(child: Text('Text')),
)
```

---

## 11. Common Mistakes

- Expecting `Center` to work without space
- Using multiple children inside `Center`
- Confusing `Center` with `MainAxisAlignment`

---

## 12. Performance

- Very lightweight widget
- Safe to use anywhere
- Better than using unnecessary Containers

---

## 13. When to Use Center?

Use `Center` when:

- You want content exactly in the middle
- You don't need custom alignment
- You want clean & readable layout code

---

## 14. Interview Questions

- Difference between Center and Align?
- Can Center have multiple children?
- Does Center take full width & height?

---

## 15. Summary

- `Center` is used to align a widget to the center
- Only one child allowed
- Internally uses `Align`
- Best for simple centering needs

---
