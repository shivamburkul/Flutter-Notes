# AnimatedContainer in Flutter (Implicit Animation)

## 1️⃣ What is Animation in Flutter?

Animation means smooth transition between values.

**Example:**

- Size change smoothly
- Color change smoothly
- Shape change smoothly

---

## 2️⃣ What is AnimatedContainer?

`AnimatedContainer` is a widget that automatically animates changes.

It animates when its properties change.

**Simple meaning:**

> Container + Animation

---

## 3️⃣ Why Use AnimatedContainer?

- No need to write animation controller
- Easy to use
- Best for beginners

---

## 4️⃣ AnimatedContainer is an Implicit Animation

Flutter has two types of animations:

1. **Implicit Animation** (easy)
2. **Explicit Animation** (advanced)

`AnimatedContainer` comes under Implicit Animation.

---

## 5️⃣ Requirement

`AnimatedContainer` requires `StatefulWidget` because values change.

---

## 6️⃣ Basic AnimatedContainer Example
```dart
class AnimatedBox extends StatefulWidget {
  @override
  State<AnimatedBox> createState() => _AnimatedBoxState();
}

class _AnimatedBoxState extends State<AnimatedBox> {
  double boxWidth = 100;
  double boxHeight = 100;
  Color boxColor = Colors.blue;

  @override
  Widget build(BuildContext context) {
    return Column(
      mainAxisAlignment: MainAxisAlignment.center,
      children: [
        AnimatedContainer(
          duration: Duration(seconds: 1),
          width: boxWidth,
          height: boxHeight,
          color: boxColor,
        ),
        SizedBox(height: 20),
        ElevatedButton(
          onPressed: () {
            setState(() {
              boxWidth = 200;
              boxHeight = 200;
              boxColor = Colors.red;
            });
          },
          child: Text('Animate'),
        )
      ],
    );
  }
}
```

---

## 7️⃣ Important AnimatedContainer Properties

- `duration` → animation time
- `curve` → animation style
- `width` / `height`
- `color`
- `padding`
- `margin`
- `decoration`
- `alignment`

---

## 8️⃣ Using Curve in Animation
```dart
curve: Curves.easeInOut
```

**Common curves:**

- `ease`
- `easeIn`
- `easeOut`
- `bounceIn`
- `fastOutSlowIn`

---

## 9️⃣ AnimatedContainer with Decoration
```dart
AnimatedContainer(
  duration: Duration(seconds: 1),
  decoration: BoxDecoration(
    color: boxColor,
    borderRadius: BorderRadius.circular(20),
  ),
)
```

---

## 🔟 Common Mistakes

- ❌ Forgetting `duration`
- ❌ Using StatelessWidget
- ❌ Expecting animation without `setState`

---

## 1️⃣1️⃣ Best Practices

- Keep duration short (300–800ms)
- Use curves for smooth UX
- Avoid heavy animations

---

## 1️⃣2️⃣ Interview Questions

- What is AnimatedContainer?
- Difference between Container & AnimatedContainer?
- What is implicit animation?

---

## 1️⃣3️⃣ Quick Revision Points

- `AnimatedContainer` animates automatically
- Requires StatefulWidget
- Uses `duration` + `setState`
- Part of implicit animations
