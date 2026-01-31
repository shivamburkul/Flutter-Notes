# AnimatedOpacity in Flutter

## 🔹 What is AnimatedOpacity?

`AnimatedOpacity` is an implicit animation widget in Flutter that automatically animates the opacity (visibility) of a widget when its value changes.

- Opacity range: `0.0` (fully invisible) → `1.0` (fully visible)
- No `AnimationController` required
- Very easy to use and beginner-friendly

---

## 🔹 Why use AnimatedOpacity?

- ✅ Smooth fade in / fade out effect
- ✅ No complex animation setup
- ✅ Clean UI transitions
- ✅ Used in splash screens, dialogs, buttons, images

---

## 🔹 Basic Syntax
```dart
AnimatedOpacity(
  opacity: 1.0,
  duration: Duration(seconds: 1),
  child: Widget,
)
```

---

## 🔹 Important Properties

| Property  | Description                        |
|-----------|------------------------------------|
| `opacity` | Controls visibility (0.0 – 1.0)    |
| `duration`| Animation time                     |
| `curve`   | Speed curve (ease, linear, etc.)   |
| `child`   | Widget to animate                  |
| `onEnd`   | Callback after animation ends      |

---

## 🔹 Simple Example (Fade In / Fade Out)
```dart
class MyOpacityDemo extends StatefulWidget {
  @override
  State<MyOpacityDemo> createState() => _MyOpacityDemoState();
}

class _MyOpacityDemoState extends State<MyOpacityDemo> {
  double _opacity = 1.0;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Animated Opacity")),
      body: Column(
        mainAxisAlignment: MainAxisAlignment.center,
        children: [
          AnimatedOpacity(
            opacity: _opacity,
            duration: Duration(seconds: 1),
            child: Container(
              width: 150,
              height: 150,
              color: Colors.blue,
            ),
          ),
          SizedBox(height: 20),
          ElevatedButton(
            onPressed: () {
              setState(() {
                _opacity = _opacity == 1.0 ? 0.0 : 1.0;
              });
            },
            child: Text("Toggle Opacity"),
          )
        ],
      ),
    );
  }
}
```

---

## 🔹 Using Curve
```dart
AnimatedOpacity(
  opacity: 0.5,
  duration: Duration(milliseconds: 800),
  curve: Curves.easeInOut,
  child: Text("Hello Flutter"),
)
```

---

## 🔹 Using onEnd Callback
```dart
AnimatedOpacity(
  opacity: 0.0,
  duration: Duration(seconds: 1),
  onEnd: () {
    print("Animation Completed");
  },
  child: Icon(Icons.favorite),
)
```

---

## 🔹 Common Use Cases

- ✔ Splash screen fade in
- ✔ Showing / hiding buttons
- ✔ Image transitions
- ✔ Alert dialogs
- ✔ Login / signup animations

---

## 🔹 AnimatedOpacity vs Opacity

| Opacity         | AnimatedOpacity   |
|-----------------|-------------------|
| No animation    | Smooth animation  |
| Instant change  | Gradual change    |
| Static          | Animated          |

---

## ⚠ Important Notes

- Widget still takes space even when `opacity` is `0.0`
- Use `Visibility` or `SizedBox.shrink()` if space removal is needed
- Must be inside a `StatefulWidget` to change opacity dynamically

---

## 🧠 Interview Tip

> AnimatedOpacity is an implicit animation widget used to smoothly animate visibility without animation controllers.

---

## ✅ Summary

- `AnimatedOpacity` animates visibility
- Easy and clean animation
- Best for beginner animations
- No controller required
