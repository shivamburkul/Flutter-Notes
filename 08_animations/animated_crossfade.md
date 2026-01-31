# AnimatedCrossFade Widget (Flutter)

## What is AnimatedCrossFade?

`AnimatedCrossFade` is a Flutter widget used to smoothly switch (fade) between two widgets.

Instead of suddenly changing UI, it crossfades (one fades out while the other fades in).

**Example use-cases:**

- Show / hide details
- Login ↔ Signup UI
- Expand / collapse content
- Image switch with animation

---

## Why use AnimatedCrossFade?

- No `AnimationController` needed
- Easy to implement
- Built-in animation
- Clean & readable code

---

## Basic Syntax
```dart
AnimatedCrossFade(
  firstChild: Widget1,
  secondChild: Widget2,
  crossFadeState: CrossFadeState.showFirst,
  duration: Duration(milliseconds: 300),
)
```

---

## Important Properties

### 1. firstChild

Widget shown initially

### 2. secondChild

Widget shown after switch

### 3. crossFadeState

Controls which widget is visible

- `CrossFadeState.showFirst`
- `CrossFadeState.showSecond`

### 4. duration

Animation time
```dart
Duration(milliseconds: 300)
```

### 5. firstCurve / secondCurve

Controls animation style
```dart
firstCurve: Curves.easeIn,
secondCurve: Curves.easeOut,
```

### 6. sizeCurve

Controls size animation when widgets have different sizes
```dart
sizeCurve: Curves.easeInOut,
```

---

## Simple Example
```dart
class MyWidget extends StatefulWidget {
  @override
  State<MyWidget> createState() => _MyWidgetState();
}

class _MyWidgetState extends State<MyWidget> {
  bool showFirst = true;

  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        AnimatedCrossFade(
          firstChild: Container(
            height: 100,
            width: 100,
            color: Colors.red,
          ),
          secondChild: Container(
            height: 150,
            width: 150,
            color: Colors.green,
          ),
          crossFadeState: showFirst
              ? CrossFadeState.showFirst
              : CrossFadeState.showSecond,
          duration: Duration(milliseconds: 500),
        ),

        ElevatedButton(
          onPressed: () {
            setState(() {
              showFirst = !showFirst;
            });
          },
          child: Text("Switch"),
        ),
      ],
    );
  }
}
```

---

## AnimatedCrossFade vs AnimatedSwitcher

| AnimatedCrossFade | AnimatedSwitcher  |
|-------------------|-------------------|
| Only 2 widgets    | Multiple widgets  |
| Simple use-case   | More flexible     |
| Built-in logic    | Needs keys        |

---

## Common Mistakes

- ❌ Forgetting `StatefulWidget`
- ❌ Not toggling `crossFadeState`
- ❌ Huge size difference without `sizeCurve`
- ❌ Using it when more than 2 widgets are needed

---

## When NOT to use AnimatedCrossFade

- More than 2 widgets
- Complex animations
- Custom animation control needed

**Use `AnimatedSwitcher` instead.**

---

## Summary

- `AnimatedCrossFade` fades between two widgets
- No controller needed
- Perfect for simple UI switches
- Uses `CrossFadeState`
