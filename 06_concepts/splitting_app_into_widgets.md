# Splitting an App into Widgets in Flutter

## 1️⃣ What Does "Splitting App into Widgets" Mean?

It means breaking a big UI into small reusable widgets.

Instead of writing everything in one file, we divide UI into parts.

**Simple meaning:**

> One screen → many small widgets

---

## 2️⃣ Why Splitting Widgets is IMPORTANT

- Code becomes clean & readable
- Easy to maintain
- Reusable widgets
- Easy debugging
- Improves performance understanding

Real apps ALWAYS use this approach.

---

## 3️⃣ Problem Without Splitting Widgets
```dart
Scaffold(
  body: Column(
    children: [
      Text('Title'),
      Image.network('url'),
      ElevatedButton(onPressed: () {}, child: Text('Click')),
    ],
  ),
)
```

**Problems:**

- Hard to read
- Not reusable
- File becomes very large

---

## 4️⃣ Solution: Split into Small Widgets

We divide UI into:

- Header widget
- Image widget
- Button widget

---

## 5️⃣ Creating a Custom Widget (StatelessWidget)
```dart
class HeaderWidget extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Text(
      'Title',
      style: TextStyle(fontSize: 24),
    );
  }
}
```

---

## 6️⃣ Using Custom Widget in Main UI
```dart
Column(
  children: [
    HeaderWidget(),
  ],
)
```

---

## 7️⃣ Splitting UI with Multiple Widgets Example
```dart
class MyScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Column(
        children: [
          HeaderWidget(),
          ImageWidget(),
          ButtonWidget(),
        ],
      ),
    );
  }
}
```

---

## 8️⃣ Passing Data Between Widgets
```dart
class HeaderWidget extends StatelessWidget {
  final String title;

  HeaderWidget({required this.title});

  @override
  Widget build(BuildContext context) {
    return Text(title);
  }
}
```

**Usage:**
```dart
HeaderWidget(title: 'Home Screen')
```

---

## 9️⃣ Splitting Stateful Logic

- UI → separate widget
- Logic → parent widget

**Example use cases:**

- Button click
- Counter
- Form input

---

## 🔟 Folder Structure Example (Recommended)
```
lib/
│── main.dart
│
├── screens/
│   └── home_screen.dart
│
├── widgets/
│   ├── header_widget.dart
│   ├── custom_button.dart
│   └── image_widget.dart
```

---

## 1️⃣1️⃣ Common Mistakes

- ❌ Writing full UI in one file
- ❌ Not reusing widgets
- ❌ Mixing business logic in UI widgets

---

## 1️⃣2️⃣ Best Practices

- One widget = one responsibility
- Reuse widgets
- Use meaningful widget names
- Keep widgets small

---

## 1️⃣3️⃣ Interview Questions

- Why do we split widgets in Flutter?
- Difference between screen & widget?
- How to pass data to widgets?

---

## 1️⃣4️⃣ Quick Revision Points

- Split big UI into small widgets
- Improves readability & reusability
- Use custom Stateless/Stateful widgets

---
