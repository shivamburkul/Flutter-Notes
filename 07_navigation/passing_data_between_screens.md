# Passing Data from One Screen to Another in Flutter

## 1️⃣ What does Passing Data mean?

Sending values from one screen to another screen.

**Example:**

- Username from Login → Home
- Product ID from List → Details page

---

## 2️⃣ Why Passing Data is Needed?

- To show dynamic content
- To personalize UI
- To share user selections

---

## 3️⃣ Most Common Way (Constructor Method)

Flutter uses constructor parameters to pass data.

---

## 4️⃣ Passing Data (Sender Screen)
```dart
Navigator.push(
  context,
  MaterialPageRoute(
    builder: (context) => SecondScreen(name: 'Shivam', age: 21),
  ),
);
```

---

## 5️⃣ Receiving Data (Receiver Screen)
```dart
class SecondScreen extends StatelessWidget {
  final String name;
  final int age;

  SecondScreen({required this.name, required this.age});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Second Screen')),
      body: Center(
        child: Text('Name: $name, Age: $age'),
      ),
    );
  }
}
```

---

## 6️⃣ Passing Object (Advanced but Important)
```dart
class User {
  String name;
  int age;
  User(this.name, this.age);
}

Navigator.push(
  context,
  MaterialPageRoute(
    builder: (context) => ProfileScreen(user: user),
  ),
);
```

---

## 7️⃣ Receiving Object
```dart
class ProfileScreen extends StatelessWidget {
  final User user;
  ProfileScreen({required this.user});
}
```

---

## 8️⃣ Passing Data Back to Previous Screen
```dart
Navigator.pop(context, 'Success');
```

**Receiving data:**
```dart
final result = await Navigator.push(...);
```

---

## 9️⃣ Common Mistakes

- ❌ Forgetting `required` keyword
- ❌ Not using `final` variables
- ❌ Passing null values

---

## 🔟 Best Practices

- Use `final` for received data
- Pass only required data
- Use models for complex data

---

## 1️⃣1️⃣ Interview Questions

- How do you pass data between screens?
- Can we pass objects in Flutter?
- How to return data from a screen?

---

## 1️⃣2️⃣ Quick Revision Points

- Data passed using constructor
- `Navigator.push` sends data
- `Navigator.pop` can return data
