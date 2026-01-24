# CircleAvatar Widget in Flutter

## 1️⃣ What is CircleAvatar?

`CircleAvatar` is a circular widget used to display:

- Profile images
- User initials
- Icons

Mostly used in profile screens, chat lists, contact lists.

---

## 2️⃣ Why CircleAvatar is IMPORTANT

- Standard UI for user profile
- Clean and professional look
- Easy to use with ListTile

---

## 3️⃣ Basic CircleAvatar Example
```dart
CircleAvatar(
  radius: 30,
  backgroundColor: Colors.blue,
  child: Text('A'),
)
```

---

## 4️⃣ CircleAvatar with Image (MOST COMMON)

### From Assets
```dart
CircleAvatar(
  radius: 30,
  backgroundImage: AssetImage('assets/images/user.png'),
)
```

### From Network
```dart
CircleAvatar(
  radius: 30,
  backgroundImage: NetworkImage(
    'https://example.com/user.jpg',
  ),
)
```

---

## 5️⃣ CircleAvatar Properties Explained

### 🔹 radius

- Controls size of avatar

### 🔹 backgroundColor

- Background color

### 🔹 backgroundImage

- Image inside avatar

### 🔹 child

- Text or Icon

---

## 6️⃣ CircleAvatar inside ListTile (VERY IMPORTANT)
```dart
ListTile(
  leading: CircleAvatar(
    backgroundColor: Colors.green,
    child: Text('S'),
  ),
  title: Text('Shivam'),
  subtitle: Text('Online'),
)
```

---

## 7️⃣ CircleAvatar with Icon
```dart
CircleAvatar(
  radius: 25,
  child: Icon(Icons.person),
)
```

---

## 8️⃣ Using CircleAvatar as Button
```dart
InkWell(
  onTap: () {},
  child: CircleAvatar(
    radius: 30,
    child: Icon(Icons.camera_alt),
  ),
)
```

---

## 9️⃣ Common Mistakes

- ❌ Using large images without crop
- ❌ Forgetting to add asset path
- ❌ Too large radius in ListTile

---

## 🔟 Best Practices

- Use optimized images
- Keep radius consistent
- Use CircleAvatar with ListTile

---

## 1️⃣1️⃣ Interview Questions

- What is CircleAvatar used for?
- Difference between Image & CircleAvatar?
- How to use CircleAvatar in ListView?

---

## 1️⃣2️⃣ Quick Revision Points

- CircleAvatar = circular profile widget
- Used for images, text, icons
- Common in lists & profiles

---
