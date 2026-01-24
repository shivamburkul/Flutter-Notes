# Creating Custom Widgets in Flutter

## 1️⃣ What is a Custom Widget?

A custom widget is a reusable widget created by you.

Instead of repeating UI code, create a widget once and use it everywhere.

**Simple meaning:**

> Write once, reuse many times

---

## 2️⃣ Why Custom Widgets are Important

- **Reusability:** Use same widget in multiple screens
- **Clean Code:** Keep main UI file readable
- **Maintainable:** Easy to update UI
- **Consistent Design:** Same style across app

---

## 3️⃣ Types of Custom Widgets

1. **StatelessWidget:** UI does not change dynamically
2. **StatefulWidget:** UI changes based on user interaction or data

---

## 4️⃣ Creating a Stateless Custom Widget
```dart
class MyButton extends StatelessWidget {
  final String title;
  final VoidCallback onPressed;

  MyButton({required this.title, required this.onPressed});

  @override
  Widget build(BuildContext context) {
    return ElevatedButton(
      onPressed: onPressed,
      child: Text(title),
    );
  }
}
```

---

**Usage:**
```dart
MyButton(
  title: 'Click Me',
  onPressed: () {
    print('Button Clicked');
  },
)
```

---

## 5️⃣ Creating a Stateful Custom Widget
```dart
class CounterWidget extends StatefulWidget {
  @override
  _CounterWidgetState createState() => _CounterWidgetState();
}

class _CounterWidgetState extends State<CounterWidget> {
  int count = 0;

  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        Text('Count: $count'),
        ElevatedButton(
          onPressed: () {
            setState(() {
              count++;
            });
          },
          child: Text('Increment'),
        ),
      ],
    );
  }
}
```

---

## 6️⃣ Passing Data to Custom Widgets
```dart
class GreetingWidget extends StatelessWidget {
  final String name;

  GreetingWidget({required this.name});

  @override
  Widget build(BuildContext context) {
    return Text('Hello, $name');
  }
}
```

**Usage:**
```dart
GreetingWidget(name: 'Shivam')
```

---

## 7️⃣ Advantages of Custom Widgets

- Keeps main.dart clean
- Reduces code duplication
- Easy UI updates
- Encourages component-based architecture

---

## 8️⃣ Common Mistakes

- ❌ Not using parameters for dynamic content
- ❌ Putting too much logic in StatelessWidget
- ❌ Not reusing widgets properly

---

## 9️⃣ Best Practices

- One widget = one responsibility
- Keep widgets small and readable
- Use meaningful names
- Pass data via constructor

---

## 🔟 Interview Questions

- What is a custom widget?
- Difference between StatelessWidget and StatefulWidget?
- How to pass data to custom widget?
- Why use custom widgets?

---

## 1️⃣1️⃣ Quick Revision Points

- Custom widgets = reusable UI components
- Stateless = static UI
- Stateful = dynamic UI
- Pass data using constructor
- Keep code clean & modular

---
