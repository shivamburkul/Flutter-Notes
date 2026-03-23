# Hero Animation in Flutter

## 1️⃣ What is Hero Animation?

Hero Animation is when a widget **flies smoothly** from one screen to another.

**Example:**

- Image on list screen → flies to detail screen
- Profile photo → small to large smoothly

> Same widget moves between two screens with animation

---

## 2️⃣ Why Use Hero Animation?

- Gives smooth screen transition
- No extra animation code needed
- Looks very professional
- Easy to implement

---

## 3️⃣ How Hero Animation Works

- Wrap widget in `Hero` on Screen 1
- Wrap same widget in `Hero` on Screen 2
- Give **same `tag`** to both
- Flutter handles the animation automatically on navigation

---

## 4️⃣ Hero Widget Syntax
```dart
Hero(
  tag: 'uniqueTag',  // must be same on both screens
  child: YourWidget(),
)
```

---

## 5️⃣ Important Properties

- `tag` → unique name, must match on both screens
- `child` → widget that will animate
- `flightShuttleBuilder` → custom animation during flight (optional)
- `placeholderBuilder` → widget shown at source while flying (optional)

---

## 6️⃣ Full Example
```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(home: HomeScreen());
  }
}

// ---- Screen 1 ----
class HomeScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Hero Animation')),
      body: Center(
        child: GestureDetector(
          onTap: () {
            Navigator.push(
              context,
              MaterialPageRoute(builder: (_) => DetailScreen()),
            );
          },
          child: Hero(
            tag: 'heroImage',  // tag same on both screens
            child: Image.network(
              'https://picsum.photos/100',
              width: 100,
              height: 100,
            ),
          ),
        ),
      ),
    );
  }
}

// ---- Screen 2 ----
class DetailScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Detail Screen')),
      body: Center(
        child: Hero(
          tag: 'heroImage',  // tag same on both screens
          child: Image.network(
            'https://picsum.photos/100',
            width: 300,
            height: 300,
          ),
        ),
      ),
    );
  }
}
```

---

## 7️⃣ Hero Animation Flow
```
Screen 1                     Screen 2
Hero(tag: 'heroImage')  →→→  Hero(tag: 'heroImage')
  small image                  large image
       ↓_______flies smoothly_______↑
```

---

## 8️⃣ Hero with Text Example
```dart
// Screen 1
Hero(
  tag: 'titleText',
  child: Text('Flutter', style: TextStyle(fontSize: 18)),
)

// Screen 2
Hero(
  tag: 'titleText',
  child: Text('Flutter', style: TextStyle(fontSize: 40)),
)
```

---

## 9️⃣ Common Mistakes

- ❌ Different `tag` on Screen 1 and Screen 2 → no animation
- ❌ Using same `tag` for two different heroes on same screen → error
- ❌ Forgetting to wrap widget in `Hero` on second screen
- ❌ Using Hero without Navigator → won't work

---

## 🔟 Common Use Cases

- Product image from list → detail page
- Profile picture → full view
- Card → expanded screen
- Thumbnail → full image viewer

---

## 1️⃣1️⃣ Best Practices

- Keep `tag` names unique and meaningful
- Use same `child` widget type on both screens
- Works with `Navigator.push` and `Navigator.pop` both
- Keep hero widget simple for smooth animation

---

## 1️⃣2️⃣ Interview Questions

- What is Hero Animation in Flutter?
- Why is `tag` important in Hero widget?
- What happens if `tag` is different on both screens?
- What type of animation is Hero Animation?
- Can Hero Animation be used with any widget?

---

## 1️⃣3️⃣ Quick Revision Points

- `Hero` widget creates shared element transition
- `tag` must be **same** on both screens
- Works automatically with `Navigator.push`
- Works on both push and pop navigation
- No animation controller needed
- Can be used with Image, Text, Container — any widget
