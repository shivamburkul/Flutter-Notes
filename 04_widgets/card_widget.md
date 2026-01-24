# Card Widget in Flutter

## 1️⃣ What is Card Widget?

`Card` is a Material Design widget.

Used to show related information in a clean box with elevation.

**Commonly used in:**

- Lists
- Dashboards
- Profile screens
- Product items

---

## 2️⃣ Why Card is Important

- Gives elevation (shadow)
- Improves UI readability
- Follows Material Design standards
- Often combined with ListTile, Row, Column

---

## 3️⃣ Basic Card Example
```dart
Card(
  child: Padding(
    padding: EdgeInsets.all(16),
    child: Text('This is a Card'),
  ),
)
```

---

## 4️⃣ Card with Elevation
```dart
Card(
  elevation: 8,
  child: Text('Elevated Card'),
)
```

Higher elevation = more shadow

---

## 5️⃣ Card Shape (Rounded Corners)
```dart
Card(
  shape: RoundedRectangleBorder(
    borderRadius: BorderRadius.circular(12),
  ),
)
```

---

## 6️⃣ Card Color
```dart
Card(
  color: Colors.blue.shade100,
)
```

---

## 7️⃣ Card with ListTile (VERY COMMON)
```dart
Card(
  child: ListTile(
    leading: Icon(Icons.person),
    title: Text('Shivam'),
    subtitle: Text('Flutter Developer'),
    trailing: Icon(Icons.arrow_forward),
  ),
)
```

---

## 8️⃣ Card Inside ListView.builder
```dart
ListView.builder(
  itemCount: 5,
  itemBuilder: (context, index) {
    return Card(
      margin: EdgeInsets.all(8),
      child: ListTile(
        title: Text('Item $index'),
      ),
    );
  },
)
```

---

## 9️⃣ Card Margin
```dart
Card(
  margin: EdgeInsets.symmetric(horizontal: 12, vertical: 8),
)
```

---

## 🔟 InkWell with Card (Clickable Card)
```dart
Card(
  child: InkWell(
    onTap: () {
      print('Card tapped');
    },
    child: Padding(
      padding: EdgeInsets.all(16),
      child: Text('Tap me'),
    ),
  ),
)
```

---

## 1️⃣1️⃣ Common Mistakes

- ❌ Using Card without padding
- ❌ Too much elevation
- ❌ Forgetting margin between cards

---

## 1️⃣2️⃣ Best Practices

- Use padding inside Card
- Use ListTile inside Card for lists
- Keep elevation minimal

---

## 1️⃣3️⃣ Interview Questions

- What is Card widget?
- Difference between Container & Card?
- How to make Card clickable?

---

## 1️⃣4️⃣ Quick Revision Points

- Card gives elevation
- Used for grouped content
- Works well with ListTile & ListView

---
