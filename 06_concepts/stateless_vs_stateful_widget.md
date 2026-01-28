# StatelessWidget vs StatefulWidget in Flutter

## 1️⃣ What is a Widget in Flutter?

Everything in Flutter is a widget.

Buttons, text, images, screens → all are widgets.

**Simple meaning:**

> Widget = building block of Flutter UI

---

## 2️⃣ Types of Widgets in Flutter

Flutter mainly has two types of widgets:

1. **StatelessWidget**
2. **StatefulWidget**

---

## 3️⃣ What is StatelessWidget?

A widget whose UI never changes after it is built.

No internal state (data does not change).

**Simple meaning:**

> Static UI (fixed content)

---

## 4️⃣ StatelessWidget Example
```dart
class MyText extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Text('Hello Flutter');
  }
}
```

---

## 5️⃣ When to Use StatelessWidget

- Static text
- Icons
- Images
- UI that does not change

---

## 6️⃣ What is StatefulWidget?

A widget whose UI can change dynamically.

Uses state to update UI.

**Simple meaning:**

> Dynamic UI (changes on user action or data)

---

## 7️⃣ StatefulWidget Structure
```dart
class MyCounter extends StatefulWidget {
  @override
  State<MyCounter> createState() => _MyCounterState();
}

class _MyCounterState extends State<MyCounter> {
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
          child: Text('Increase'),
        )
      ],
    );
  }
}
```

---

## 8️⃣ What is setState()?

`setState()` tells Flutter that state has changed.

Flutter rebuilds the UI with new data.
```dart
setState(() {
  count++;
});
```

---

## 9️⃣ Stateless vs Stateful (Comparison)

| StatelessWidget | StatefulWidget  |
|-----------------|-----------------|
| Static UI       | Dynamic UI      |
| No state        | Has state       |
| Faster          | Slightly heavier|
| Simple          | More complex    |

---

## 🔟 Common Mistakes

- ❌ Using StatelessWidget for dynamic UI
- ❌ Forgetting `setState()`
- ❌ Writing logic in build method

---

## 1️⃣1️⃣ Best Practices

- Default to StatelessWidget
- Use StatefulWidget only when needed
- Keep state minimal

---

## 1️⃣2️⃣ Interview Questions

- Difference between StatelessWidget and StatefulWidget?
- What is state in Flutter?
- What does setState() do?

---

## 1️⃣3️⃣ Quick Revision Points

- Stateless = static UI
- Stateful = dynamic UI
- `setState()` updates UI
- Widgets are UI building blocks
