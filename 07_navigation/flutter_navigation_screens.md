# Switching One Screen to Another in Flutter (Navigation)

## 1️⃣ What is Screen Navigation in Flutter?

Moving from one screen (page) to another screen.

Screens are also called **routes** in Flutter.

**Example:**

> Login Screen → Home Screen

---

## 2️⃣ What is a Route?

A route is a screen or page in Flutter.

Flutter manages routes using a **Navigator stack**.

---

## 3️⃣ Navigator Stack Concept

Works like a stack (LIFO)
```
Screen A (bottom)
Screen B
Screen C (top)
```

- New screen → pushed on stack
- Back button → pops screen

---

## 4️⃣ Basic Navigation Method

### Navigator.push()

Used to move to next screen.
```dart
Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => SecondScreen()),
);
```

---

## 5️⃣ Complete Example (Two Screens)

### First Screen
```dart
class FirstScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('First Screen')),
      body: Center(
        child: ElevatedButton(
          onPressed: () {
            Navigator.push(
              context,
              MaterialPageRoute(builder: (context) => SecondScreen()),
            );
          },
          child: Text('Go to Second Screen'),
        ),
      ),
    );
  }
}
```

### Second Screen
```dart
class SecondScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Second Screen')),
      body: Center(
        child: ElevatedButton(
          onPressed: () {
            Navigator.pop(context);
          },
          child: Text('Go Back'),
        ),
      ),
    );
  }
}
```

---

## 6️⃣ Going Back to Previous Screen

### Navigator.pop()
```dart
Navigator.pop(context);
```

Removes top screen from stack

---

## 7️⃣ Passing Data Between Screens

### Sending data
```dart
Navigator.push(
  context,
  MaterialPageRoute(
    builder: (context) => SecondScreen(name: 'Flutter'),
  ),
);
```

### Receiving data
```dart
class SecondScreen extends StatelessWidget {
  final String name;
  SecondScreen({required this.name});
}
```

---

## 8️⃣ Named Routes (Short Intro)

Cleaner way for large apps
```dart
routes: {
  '/second': (context) => SecondScreen(),
}

Navigator.pushNamed(context, '/second');
```

---

## 9️⃣ Common Mistakes

- ❌ Forgetting context
- ❌ Navigating without MaterialPageRoute
- ❌ Using pop without push

---

## 🔟 Best Practices

- Use push for next screen
- Use pop to go back
- Keep screens separate

---

## 1️⃣1️⃣ Interview Questions

- What is Navigator in Flutter?
- Difference between push and pop?
- What is route?

---

## 1️⃣2️⃣ Quick Revision Points

- Screens = routes
- Navigator manages stack
- `push` → next screen
- `pop` → previous screen
