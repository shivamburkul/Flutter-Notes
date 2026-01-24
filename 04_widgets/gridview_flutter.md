# GridView in Flutter

## 1️⃣ What is GridView?

`GridView` is used to display items in 2D grid format (rows + columns).

**Common use cases:**

- Image gallery
- Product listing
- Dashboard cards

---

## 2️⃣ Why GridView is Important

- Shows more content in less space
- Looks clean and modern
- Used heavily in real apps

---

## 3️⃣ Types of GridView

1. `GridView.count`
2. `GridView.extent`
3. `GridView.builder`
4. `GridView.custom`

---

## 4️⃣ GridView.count (Fixed Columns)
```dart
GridView.count(
  crossAxisCount: 2,
  children: [
    Container(color: Colors.red),
    Container(color: Colors.green),
    Container(color: Colors.blue),
  ],
)
```

---

## 5️⃣ GridView.extent (Fixed Item Width)
```dart
GridView.extent(
  maxCrossAxisExtent: 150,
  children: [
    Container(color: Colors.orange),
    Container(color: Colors.purple),
  ],
)
```

---

## 6️⃣ GridView.builder (MOST USED)
```dart
GridView.builder(
  itemCount: 10,
  gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
    crossAxisCount: 2,
  ),
  itemBuilder: (context, index) {
    return Card(
      child: Center(child: Text('Item $index')),
    );
  },
)
```

---

## 7️⃣ GridDelegate Types

### Fixed Cross Axis Count
```dart
SliverGridDelegateWithFixedCrossAxisCount(
  crossAxisCount: 2,
  mainAxisSpacing: 10,
  crossAxisSpacing: 10,
  childAspectRatio: 1,
)
```

### Max Cross Axis Extent
```dart
SliverGridDelegateWithMaxCrossAxisExtent(
  maxCrossAxisExtent: 200,
)
```

---

## 8️⃣ Spacing in GridView

- `mainAxisSpacing` → vertical spacing
- `crossAxisSpacing` → horizontal spacing

---

## 9️⃣ GridView Inside Column (IMPORTANT)
```dart
Expanded(
  child: GridView.builder(
    itemCount: 6,
    gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
      crossAxisCount: 3,
    ),
    itemBuilder: (context, index) {
      return Container(color: Colors.blue);
    },
  ),
)
```

---

## 🔟 GridView with Images
```dart
GridView.builder(
  itemCount: images.length,
  gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
    crossAxisCount: 2,
  ),
  itemBuilder: (context, index) {
    return Image.network(images[index]);
  },
)
```

---

## 1️⃣1️⃣ Common Mistakes

- ❌ Not using Expanded
- ❌ Forgetting gridDelegate
- ❌ Performance issues with count/extent for large data

---

## 1️⃣2️⃣ Best Practices

- Use GridView.builder for large lists
- Always define spacing
- Use Card inside GridView

---

## 1️⃣3️⃣ Interview Questions

- Difference between ListView and GridView?
- GridView.count vs GridView.builder?
- What is SliverGridDelegate?

---

## 1️⃣4️⃣ Quick Revision Points

- GridView = rows + columns
- builder = best for performance
- gridDelegate controls layout

---
