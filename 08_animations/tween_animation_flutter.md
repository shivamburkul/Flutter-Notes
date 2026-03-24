# Tween Animation in Flutter (Explicit Animation)

## 1️⃣ What is Tween Animation?

- **Tween** = **In Between** → animation between two values
- It animates from a **start value** to an **end value**
- This is an **Explicit Animation** — we control it manually

**Simple meaning:**

> Tween = value 0 se value 1 tak smoothly change karo

**Examples:**

- Size 100 → 300 smoothly
- Opacity 0.0 → 1.0 smoothly
- Color red → blue smoothly

---

## 2️⃣ Implicit vs Explicit Animation

| Implicit | Explicit |
|---|---|
| Flutter handles automatically | We control manually |
| AnimatedContainer, AnimatedOpacity | Tween + AnimationController |
| Easy | More control |
| Less code | More code |

> Tween Animation = Explicit Animation

---

## 3️⃣ Parts of Tween Animation (IMPORTANT)

Tween Animation needs 4 things:

1. **AnimationController** → controls the animation (start, stop, repeat)
2. **Tween** → defines start and end value
3. **Animation** → holds the current animated value
4. **AnimatedBuilder / setState** → rebuilds UI with new value

---

## 4️⃣ AnimationController

- Controls the animation
- Needs `TickerProviderStateMixin` (or `SingleTickerProviderStateMixin`)
- Has `duration` property
- Methods: `.forward()`, `.reverse()`, `.repeat()`, `.stop()`
```dart
AnimationController controller = AnimationController(
  vsync: this,
  duration: Duration(seconds: 2),
);
```

> `vsync: this` → requires `SingleTickerProviderStateMixin`

---

## 5️⃣ Tween

- Defines the range of values (start → end)
```dart
Tween<double>(begin: 0, end: 300)
```

---

## 6️⃣ Connecting Tween with Controller
```dart
Animation<double> animation = Tween<double>(
  begin: 0,
  end: 300,
).animate(controller);
```

---

## 7️⃣ Basic Setup (Step by Step)
```dart
class MyAnimation extends StatefulWidget {
  @override
  State<MyAnimation> createState() => _MyAnimationState();
}

// Step 1: Add SingleTickerProviderStateMixin
class _MyAnimationState extends State<MyAnimation>
    with SingleTickerProviderStateMixin {

  // Step 2: Declare controller and animation
  late AnimationController controller;
  late Animation<double> animation;

  @override
  void initState() {
    super.initState();

    // Step 3: Initialize controller
    controller = AnimationController(
      vsync: this,
      duration: Duration(seconds: 2),
    );

    // Step 4: Connect Tween with controller
    animation = Tween<double>(begin: 50, end: 250).animate(controller);

    // Step 5: Start animation
    controller.forward();
  }

  // Step 6: Dispose controller (very important)
  @override
  void dispose() {
    controller.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Tween Animation')),
      // Step 7: Use AnimatedBuilder
      body: AnimatedBuilder(
        animation: animation,
        builder: (context, child) {
          return Center(
            child: Container(
              width: animation.value,   // animated value
              height: animation.value,
              color: Colors.blue,
            ),
          );
        },
      ),
    );
  }
}
```

---

## 8️⃣ AnimatedBuilder

- Rebuilds only the part that needs animation
- More efficient than `setState`
- Takes `animation` and `builder`
```dart
AnimatedBuilder(
  animation: animation,
  builder: (context, child) {
    return Container(
      width: animation.value,
      height: animation.value,
    );
  },
)
```

---

## 9️⃣ AnimationController Methods
```dart
controller.forward();   // play animation start → end
controller.reverse();   // play animation end → start
controller.repeat();    // loop forever
controller.stop();      // stop animation
controller.reset();     // go back to start
```

---

## 🔟 Using Curves with Tween

- Add `CurvedAnimation` between controller and tween
```dart
Animation<double> curvedAnimation = CurvedAnimation(
  parent: controller,
  curve: Curves.bounceOut,
);

animation = Tween<double>(begin: 50, end: 250).animate(curvedAnimation);
```

**Common Curves:**

- `Curves.easeIn`
- `Curves.easeOut`
- `Curves.bounceOut`
- `Curves.elasticOut`
- `Curves.fastOutSlowIn`

---

## 1️⃣1️⃣ Tween Types
```dart
Tween<double>()         // for size, opacity, position
ColorTween()            // for color
BorderRadiusTween()     // for border radius
EdgeInsetsTween()       // for padding/margin
```

**ColorTween Example:**
```dart
Animation<Color?> colorAnimation = ColorTween(
  begin: Colors.blue,
  end: Colors.red,
).animate(controller);
```

---

## 1️⃣2️⃣ Full Example with Button Control
```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(home: TweenExample());
  }
}

class TweenExample extends StatefulWidget {
  @override
  State<TweenExample> createState() => _TweenExampleState();
}

class _TweenExampleState extends State<TweenExample>
    with SingleTickerProviderStateMixin {

  late AnimationController controller;
  late Animation<double> animation;

  @override
  void initState() {
    super.initState();
    controller = AnimationController(
      vsync: this,
      duration: Duration(seconds: 1),
    );
    animation = Tween<double>(begin: 50, end: 200).animate(
      CurvedAnimation(parent: controller, curve: Curves.easeInOut),
    );
  }

  @override
  void dispose() {
    controller.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Tween Animation')),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            AnimatedBuilder(
              animation: animation,
              builder: (context, child) {
                return Container(
                  width: animation.value,
                  height: animation.value,
                  decoration: BoxDecoration(
                    color: Colors.blue,
                    borderRadius: BorderRadius.circular(12),
                  ),
                );
              },
            ),
            SizedBox(height: 30),
            Row(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                ElevatedButton(
                  onPressed: () => controller.forward(),
                  child: Text('Grow'),
                ),
                SizedBox(width: 10),
                ElevatedButton(
                  onPressed: () => controller.reverse(),
                  child: Text('Shrink'),
                ),
                SizedBox(width: 10),
                ElevatedButton(
                  onPressed: () => controller.repeat(reverse: true),
                  child: Text('Loop'),
                ),
              ],
            ),
          ],
        ),
      ),
    );
  }
}
```

---

## 1️⃣3️⃣ dispose() is VERY IMPORTANT

- Always call `controller.dispose()` in `dispose()` method
- If not disposed → memory leak in app
```dart
@override
void dispose() {
  controller.dispose();  // always do this
  super.dispose();
}
```

---

## 1️⃣4️⃣ Common Mistakes

- ❌ Forgetting `SingleTickerProviderStateMixin` → vsync error
- ❌ Not calling `controller.dispose()` → memory leak
- ❌ Not calling `controller.forward()` → animation won't start
- ❌ Forgetting `.toList()` after `.animate()` → wrong usage
- ❌ Using in StatelessWidget → AnimationController needs StatefulWidget

---

## 1️⃣5️⃣ Interview Questions

- What is Tween Animation in Flutter?
- What is the difference between Implicit and Explicit animation?
- What is AnimationController and why do we need it?
- What is `vsync` in AnimationController?
- Why is `dispose()` important in Tween Animation?
- What is `AnimatedBuilder` and why use it?
- What does `CurvedAnimation` do?

---

## 1️⃣6️⃣ Quick Revision Points

- Tween = animates between two values (begin → end)
- Tween Animation = Explicit Animation
- Needs `SingleTickerProviderStateMixin`
- `AnimationController` → controls play, stop, repeat
- `Tween.animate(controller)` → connects both
- `AnimatedBuilder` → rebuilds UI efficiently
- Always `dispose()` the controller
- Use `CurvedAnimation` for curve effects
- `controller.forward()` → starts animation
- `controller.reverse()` → reverses animation
- `controller.repeat()` → loops animation
