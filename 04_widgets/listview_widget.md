# ListView Widget and Its Components

## 1️⃣ What is ListView?

- `ListView` is a scrollable list widget in Flutter.
- Used to display multiple items vertically or horizontally.
- Automatically provides scrolling.
- Most commonly used widget in real apps.

**Examples:**

- Contact list
- Chat list
- Product list

---

## 2️⃣ Why ListView is IMPORTANT

- Handles large data efficiently
- Prevents overflow errors
- Easy to build dynamic UI

👉 Almost every Flutter app uses ListView.

---

## 3️⃣ Types of ListView

1. `ListView()`
2. `ListView.builder()`
3. `ListView.separated()`
4. `ListView.custom()` (advanced)

---

## 4️⃣ Basic ListView
```dart
ListView(
  children: [
    ListTile(title: Text('Item 1')),
    ListTile(title: Text('Item 2')),
    ListTile(title: Text('Item 3')),
  ],
)
```

**Use when:**

- Small fixed list

---

## 5️⃣ ListView.builder (MOST IMPORTANT)

- Creates items on demand
- Best for large or dynamic lists
```dart
ListView.builder(
  itemCount: 20,
  itemBuilder: (context, index) {
    return ListTile(
      leading: Icon(Icons.person),
      title: Text('User $index'),
      subtitle: Text('Subtitle'),
    );
  },
)
```

---

## 6️⃣ ListView.separated

- Adds separator between items
```dart
ListView.separated(
  itemCount: 10,
  separatorBuilder: (context, index) {
    return Divider();
  },
  itemBuilder: (context, index) {
    return ListTile(title: Text('Item $index'));
  },
)
```

---

## 7️⃣ ListView Components (VERY IMPORTANT)

### 🔹 itemCount

- Number of items

### 🔹 itemBuilder

- Builds each list item

### 🔹 separatorBuilder

- Divider between items

### 🔹 scrollDirection
```dart
scrollDirection: Axis.horizontal
```

---

## 8️⃣ ListTile (ListView Component)

- Prebuilt row widget for lists
```dart
ListTile(
  leading: Icon(Icons.home),
  title: Text('Home'),
  subtitle: Text('Go to home'),
  trailing: Icon(Icons.arrow_forward),
  onTap: () {},
)
```

---

## 9️⃣ ListView inside Column (COMMON ERROR)

### ❌ Error:
```
Vertical viewport was given unbounded height
```

### ✅ Fix:
```dart
Expanded(
  child: ListView.builder(
    itemCount: 5,
    itemBuilder: (context, index) => Text('Item'),
  ),
)
```

---

## 🔟 ListView with InkWell
```dart
ListView.builder(
  itemBuilder: (context, index) {
    return InkWell(
      onTap: () {},
      child: Padding(
        padding: EdgeInsets.all(16),
        child: Text('Clickable Item'),
      ),
    );
  },
)
```

---

## 1️⃣1️⃣ Performance Tips

- Use `ListView.builder`
- Avoid heavy widgets inside list
- Use const widgets where possible

---

## 1️⃣2️⃣ Common Mistakes

- ❌ Using ListView for small data unnecessarily
- ❌ Nesting ListView inside ScrollView
- ❌ Forgetting itemCount

---

## 1️⃣3️⃣ Interview Questions

- Difference between ListView & Column?
- Why ListView.builder is preferred?
- How to fix ListView inside Column error?

---

## 1️⃣4️⃣ Quick Revision Points

- ListView = scrollable list
- builder = best for large data
- separated = divider between items
- Expanded fixes height issue

---
