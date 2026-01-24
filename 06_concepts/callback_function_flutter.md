# Callback Functions in Flutter

## 1️⃣ What is a Callback Function?

A callback function is a function that is passed as a parameter to another function.

It is called (executed) later, usually after some event.

**Simple meaning:**

> "You tell a function: when this work is done, call this function."

---

## 2️⃣ Why Callbacks are IMPORTANT in Flutter

Flutter is event-driven:

- Button click
- Text change
- API response
- Widget interaction

**Callbacks help to:**

- Handle user actions
- Communicate between widgets
- Write reusable widgets

---

## 3️⃣ Simple Callback Example (Dart)
```dart
void myCallback() {
  print('Callback called');
}

void executeFunction(Function callback) {
  callback();
}

void main() {
  executeFunction(myCallback);
}
```

---

## 4️⃣ Callback in Button (Most Common)
```dart
ElevatedButton(
  onPressed: () {
    print('Button clicked');
  },
  child: Text('Click Me'),
)
```

**Here:**

- `onPressed` is a callback function

---

## 5️⃣ Passing Callback to a Custom Widget

### Parent Widget
```dart
class ParentWidget extends StatelessWidget {
  void showMessage() {
    print('Hello from Parent');
  }

  @override
  Widget build(BuildContext context) {
    return ChildWidget(onTap: showMessage);
  }
}
```

---

### Child Widget
```dart
class ChildWidget extends StatelessWidget {
  final VoidCallback onTap;

  ChildWidget({required this.onTap});

  @override
  Widget build(BuildContext context) {
    return ElevatedButton(
      onPressed: onTap,
      child: Text('Call Parent Function'),
    );
  }
}
```

---

## 6️⃣ What is VoidCallback?

`VoidCallback = void Function()`

**Used when callback:**

- Takes no parameters
- Returns nothing

---

## 7️⃣ Callback with Parameters

### Parent
```dart
class Parent extends StatelessWidget {
  void receiveData(String value) {
    print(value);
  }

  @override
  Widget build(BuildContext context) {
    return Child(onSubmit: receiveData);
  }
}
```

---

### Child
```dart
class Child extends StatelessWidget {
  final Function(String) onSubmit;

  Child({required this.onSubmit});

  @override
  Widget build(BuildContext context) {
    return ElevatedButton(
      onPressed: () {
        onSubmit('Data from Child');
      },
      child: Text('Send Data'),
    );
  }
}
```

---

## 8️⃣ Callback with TextField
```dart
TextField(
  onChanged: (value) {
    print(value);
  },
)
```

- `onChanged` is also a callback

---

## 9️⃣ Real-Life Use Case

- Child widget sends data to parent
- Button triggers API call
- Form submit action

---

## 🔟 Common Mistakes

### ❌ Calling function instead of passing reference
```dart
// WRONG
onPressed: myFunction()

// CORRECT
onPressed: myFunction
```

### ❌ Not defining callback type

---

## 1️⃣1️⃣ Best Practices

- Use `VoidCallback` when possible
- Define proper function signatures
- Keep callbacks simple

---

## 1️⃣2️⃣ Interview Questions

- What is a callback function?
- Why callbacks are used in Flutter?
- Difference between function call and callback?

---

## 1️⃣3️⃣ Quick Revision Points

- Callback = function passed as parameter
- Used in buttons & widgets
- Helps parent-child communication

---
