# ClipRRect Widget in Flutter

## 1️⃣ What is ClipRRect?

- `ClipRRect` is a widget that **clips its child with rounded corners**.
- RRect = Rounded Rectangle
- It cuts/hides the parts of widget that go outside the rounded boundary.

**Simple meaning:**

> Kisi bhi widget ko rounded corners dena ho → use ClipRRect

---

## 2️⃣ Why Use ClipRRect?

- To make images with rounded corners
- To clip any widget into rounded shape
- Used in profile pictures, cards, thumbnails

---

## 3️⃣ Basic Syntax
```dart
ClipRRect(
  borderRadius: BorderRadius.circular(20),
  child: Image.network(
    'https://picsum.photos/200',
    width: 200,
    height: 200,
    fit: BoxFit.cover,
  ),
)
```

---

## 4️⃣ Important Properties

- `borderRadius` → how much to round the corners **(most important)**
- `child` → widget to be clipped
- `clipBehavior` → how clipping is done (default: `Clip.antiAlias`)

---

## 5️⃣ BorderRadius Options
```dart
// All corners same
borderRadius: BorderRadius.circular(20)

// All corners custom
borderRadius: BorderRadius.all(Radius.circular(20))

// Each corner different
borderRadius: BorderRadius.only(
  topLeft: Radius.circular(30),
  topRight: Radius.circular(30),
  bottomLeft: Radius.circular(0),
  bottomRight: Radius.circular(0),
)
```

---

## 6️⃣ ClipRRect with Image (MOST COMMON USE)
```dart
ClipRRect(
  borderRadius: BorderRadius.circular(15),
  child: Image.asset(
    'assets/images/photo.jpg',
    width: 150,
    height: 150,
    fit: BoxFit.cover,
  ),
)
```

---

## 7️⃣ ClipRRect with Container
```dart
ClipRRect(
  borderRadius: BorderRadius.circular(20),
  child: Container(
    width: 200,
    height: 100,
    color: Colors.blue,
    child: Center(
      child: Text(
        'Hello Flutter',
        style: TextStyle(color: Colors.white),
      ),
    ),
  ),
)
```

---

## 8️⃣ Full Example
```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: Text('ClipRRect Example')),
        body: Center(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [

              // Rounded Image
              ClipRRect(
                borderRadius: BorderRadius.circular(20),
                child: Image.network(
                  'https://picsum.photos/200',
                  width: 200,
                  height: 200,
                  fit: BoxFit.cover,
                ),
              ),

              SizedBox(height: 20),

              // Only top corners rounded
              ClipRRect(
                borderRadius: BorderRadius.only(
                  topLeft: Radius.circular(40),
                  topRight: Radius.circular(40),
                ),
                child: Container(
                  width: 200,
                  height: 100,
                  color: Colors.orange,
                  child: Center(child: Text('Top Rounded')),
                ),
              ),

            ],
          ),
        ),
      ),
    );
  }
}
```

---

## 9️⃣ ClipRRect vs BoxDecoration borderRadius

| Feature | ClipRRect | BoxDecoration borderRadius |
|---|---|---|
| Works on any widget | ✅ Yes | ❌ Only Container |
| Clips child widget | ✅ Yes | ❌ No (only border) |
| Use with Image | ✅ Best way | ⚠️ Image may overflow |

> **Tip:** For rounding images always use `ClipRRect`, not `BoxDecoration`

---

## 🔟 Other Clip Widgets in Flutter

| Widget | Shape |
|---|---|
| `ClipRRect` | Rounded Rectangle |
| `ClipOval` | Circle / Oval |
| `ClipRect` | Rectangle (straight) |
| `ClipPath` | Custom shape |

---

## 1️⃣1️⃣ ClipOval Example (Circle Image)
```dart
ClipOval(
  child: Image.network(
    'https://picsum.photos/100',
    width: 100,
    height: 100,
    fit: BoxFit.cover,
  ),
)
```

---

## 1️⃣2️⃣ Common Mistakes

- ❌ Using `BorderRadius` on Image directly → won't work
- ❌ Forgetting `fit: BoxFit.cover` on image → image looks stretched
- ❌ Using BoxDecoration borderRadius instead of ClipRRect for images → image overflows corners

---

## 1️⃣3️⃣ Interview Questions

- What is ClipRRect in Flutter?
- Difference between ClipRRect and BoxDecoration borderRadius?
- Which widget is best for circular image — ClipRRect or ClipOval?
- What does `clipBehavior` do?
- Name all Clip widgets in Flutter.

---

## 1️⃣4️⃣ Quick Revision Points

- `ClipRRect` clips widget with rounded corners
- `borderRadius` is the most important property
- Best for rounding images
- Works on any widget, not just Container
- `ClipOval` → circle shape
- `ClipRect` → straight rectangle clip
- `ClipPath` → custom shape clip
- Always use `fit: BoxFit.cover` with images inside ClipRRect
