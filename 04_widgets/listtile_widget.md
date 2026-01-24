# ListTile Widget in Flutter (Used with ListView.builder)

## 1️⃣ What is ListTile?

- `ListTile` is a pre-built row widget provided by Flutter.
- It is mainly used inside ListView or ListView.builder.
- Helps to create clean, standard list items easily.

**Common use cases:**

- Contact list
- Settings menu
- Chat list

---

## 2️⃣ Why ListTile is IMPORTANT

- Reduces UI code
- Follows Material Design
- Easy to maintain & readable

👉 Most real apps use ListTile with ListView.builder.

---

## 3️⃣ Basic ListTile Example
```dart
ListTile(
  title: Text('Home'),
)
```

---

## 4️⃣ ListTile with All Main Properties
```dart
ListTile(
  leading: Icon(Icons.person),
  title: Text('John Doe'),
  subtitle: Text('Software Engineer'),
  trailing: Icon(Icons.arrow_forward_ios),
  onTap: () {
    print('Tile clicked');
  },
)
```

---

## 5️⃣ ListTile Properties Explained

### 🔹 leading

- Widget before title (icon/image)

### 🔹 title

- Main text

### 🔹 subtitle

- Secondary text below title

### 🔹 trailing

- Widget after title (icon/button)

### 🔹 onTap

- Click action

---

## 6️⃣ ListTile inside ListView.builder (VERY IMPORTANT)
```dart
ListView.builder(
  itemCount: 10,
  itemBuilder: (context, index) {
    return ListTile(
      leading: Icon(Icons.person),
      title: Text('User $index'),
      subtitle: Text('Subtitle'),
      trailing: Icon(Icons.arrow_forward),
    );
  },
)
```

---

## 7️⃣ Making ListTile Clickable
```dart
ListTile(
  title: Text('Settings'),
  onTap: () {
    print('Settings clicked');
  },
)
```

---

## 8️⃣ ListTile with InkWell vs onTap

| Method   | Use                  |
|----------|----------------------|
| onTap    | Simple clicks        |
| InkWell  | Custom ripple control|

👉 Prefer onTap for ListTile.

---

## 9️⃣ Dense & Content Padding
```dart
ListTile(
  dense: true,
  contentPadding: EdgeInsets.symmetric(horizontal: 16),
  title: Text('Compact Tile'),
)
```

---

## 🔟 ListTile with CircleAvatar
```dart
ListTile(
  leading: CircleAvatar(
    child: Text('A'),
  ),
  title: Text('Alex'),
)
```

---

## 1️⃣1️⃣ Common Mistakes

- ❌ Using Column instead of ListTile
- ❌ Heavy UI inside ListTile
- ❌ Forgetting onTap

---

## 1️⃣2️⃣ Best Practices

- Use ListTile for standard lists
- Combine with ListView.builder
- Keep ListTile simple

---

## 1️⃣3️⃣ Interview Questions

- What is ListTile?
- Difference between ListTile & Row?
- How to use ListTile in ListView.builder?

---

## 1️⃣4️⃣ Quick Revision Points

- ListTile = prebuilt row
- Used inside ListView
- leading, title, subtitle, trailing
- onTap handles clicks

---
