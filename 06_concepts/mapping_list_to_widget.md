# Mapping List to Widget in Flutter

## 1️⃣ What is Mapping List to Widget?

- Converting a **List of data** into a **List of Widgets** automatically.
- Instead of writing each widget manually, we use `.map()` to generate widgets from data.

**Simple meaning:**

> Data List → `.map()` → Widget List

---

## 2️⃣ Why Use Mapping?

- Less code
- Dynamic UI — data changes, UI updates automatically
- No need to hardcode each widget manually
- Used in almost every real Flutter app

---

## 3️⃣ Without Mapping (BAD WAY)
```dart
// Hardcoding each item manually — very bad for large data
Column(
  children: [
    Text('Apple'),
    Text('Banana'),
    Text('Mango'),
  ],
)
```

**Problem:** If list has 100 items → you write 100 Text widgets manually 😵

---

## 4️⃣ With Mapping (GOOD WAY)
```dart
List<String> fruits = ['Apple', 'Banana', 'Mango'];

Column(
  children: fruits.map((fruit) {
    return Text(fruit);
  }).toList(),
)
```

**Simple explanation:**

- `.map()` → loops through every item in list
- `(fruit)` → each item one by one
- `return Text(fruit)` → creates a widget for each item
- `.toList()` → converts result back to List (required)

---

## 5️⃣ .toList() is IMPORTANT

- `.map()` returns an `Iterable`, not a `List`
- Flutter widgets need a `List`
- So always add `.toList()` at the end
```dart
// Without .toList() → ERROR
fruits.map((fruit) => Text(fruit))  // ❌

// With .toList() → CORRECT
fruits.map((fruit) => Text(fruit)).toList()  // ✅
```

---

## 6️⃣ Arrow Function Short Way
```dart
// Long way
fruits.map((fruit) {
  return Text(fruit);
}).toList()

// Short way (arrow function)
fruits.map((fruit) => Text(fruit)).toList()
```

Both are same — short way is more common.

---

## 7️⃣ Full Example with Column
```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  final List<String> fruits = ['Apple', 'Banana', 'Mango', 'Orange', 'Grapes'];

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: Text('Mapping List to Widget')),
        body: Column(
          children: fruits.map((fruit) {
            return ListTile(
              leading: Icon(Icons.circle),
              title: Text(fruit),
            );
          }).toList(),
        ),
      ),
    );
  }
}
```

---

## 8️⃣ Mapping with ListView
```dart
List<String> cities = ['Mumbai', 'Delhi', 'Pune', 'Bangalore'];

ListView(
  children: cities.map((city) {
    return Card(
      child: ListTile(
        leading: Icon(Icons.location_city),
        title: Text(city),
      ),
    );
  }).toList(),
)
```

---

## 9️⃣ Mapping List of Objects (REAL APP STYLE)
```dart
// Model class
class Product {
  String name;
  double price;
  Product(this.name, this.price);
}

// List of objects
List<Product> products = [
  Product('Shoes', 999),
  Product('Shirt', 499),
  Product('Watch', 1999),
];

// Mapping to widgets
ListView(
  children: products.map((product) {
    return Card(
      child: ListTile(
        title: Text(product.name),
        trailing: Text('₹${product.price}'),
      ),
    );
  }).toList(),
)
```

---

## 🔟 Mapping inside Row / Wrap
```dart
List<String> tags = ['Flutter', 'Dart', 'Mobile', 'UI'];

Wrap(
  spacing: 8,
  children: tags.map((tag) {
    return Chip(label: Text(tag));
  }).toList(),
)
```

---

## 1️⃣1️⃣ Mapping vs ListView.builder

| Feature | .map().toList() | ListView.builder |
|---|---|---|
| Best for | Small lists | Large / dynamic lists |
| Lazy loading | ❌ No | ✅ Yes |
| Use inside Column | ✅ Yes | ❌ Needs Expanded |
| Performance | Ok for small data | Better for large data |

---

## 1️⃣2️⃣ Common Mistakes

- ❌ Forgetting `.toList()` → type error
- ❌ Using `.map()` for very large lists → use `ListView.builder` instead
- ❌ Not returning widget inside `.map()` → blank UI
- ❌ Using `.map()` without wrapping in Column/Row/ListView → won't show

---

## 1️⃣3️⃣ Interview Questions

- What does `.map()` do in Flutter?
- Why is `.toList()` required after `.map()`?
- Difference between `.map().toList()` and `ListView.builder`?
- How do you map a list of objects to widgets?
- When should you use `.map()` vs `ListView.builder`?

---

## 1️⃣4️⃣ Quick Revision Points

- `.map()` converts each list item into a widget
- Always add `.toList()` at the end
- Arrow function `=>` is short way to write `.map()`
- Works with Column, ListView, Row, Wrap
- Best for small lists
- For large lists → use `ListView.builder`
- Works with String list, int list, object list — any list
