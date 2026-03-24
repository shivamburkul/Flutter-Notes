# ScrollView Widgets in Flutter (Scrolling & Its Types)

## 1️⃣ What is ScrollView?

- A ScrollView allows content to scroll when it does not fit on the screen.
- Without ScrollView, Flutter throws overflow errors.
- Used when content is larger than screen size.

---

## 2️⃣ Why ScrollView is IMPORTANT

**Without scrolling:**

- UI overflow (yellow/black stripes)
- App looks broken

**With ScrollView:**

- Smooth scrolling
- Better user experience
- Handles large content

---

## 3️⃣ Types of ScrollView in Flutter

- 🔹 SingleChildScrollView
- 🔹 ListView
- 🔹 GridView
- 🔹 CustomScrollView
- 🔹 ListWheelScrollView

---

## 4️⃣ SingleChildScrollView (MOST BASIC)

- Used when you have single large content
- Scrolls one child widget

**Example:**
```dart
SingleChildScrollView(
  child: Column(
    children: [
      Text('Item 1'),
      Text('Item 2'),
      Text('Item 3'),
    ],
  ),
)
```

**Direction:**
```dart
SingleChildScrollView(
  scrollDirection: Axis.horizontal,
  child: Row(
    children: [
      Container(width: 200, height: 100, color: Colors.red),
      Container(width: 200, height: 100, color: Colors.blue),
    ],
  ),
)
```

---

## 5️⃣ ListView (MOST USED)

- Scrollable list of widgets
- Efficient for large lists

### Simple ListView
```dart
ListView(
  children: [
    ListTile(title: Text('Item 1')),
    ListTile(title: Text('Item 2')),
  ],
)
```

### ListView.builder (IMPORTANT)
```dart
ListView.builder(
  itemCount: 10,
  itemBuilder: (context, index) {
    return ListTile(title: Text('Item $index'));
  },
)
```

---

## 6️⃣ GridView

- Displays items in grid format

### GridView.count
```dart
GridView.count(
  crossAxisCount: 2,
  children: [
    Container(color: Colors.red),
    Container(color: Colors.blue),
  ],
)
```

### GridView.builder
```dart
GridView.builder(
  gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
    crossAxisCount: 2,
  ),
  itemCount: 6,
  itemBuilder: (context, index) {
    return Container(color: Colors.green);
  },
)
```

---

## 7️⃣ CustomScrollView (ADVANCED)

- Used for complex scrolling UI
- Works with Slivers
```dart
CustomScrollView(
  slivers: [
    SliverAppBar(
      title: Text('App Bar'),
      pinned: true,
    ),
    SliverList(
      delegate: SliverChildListDelegate([
        ListTile(title: Text('Item 1')),
        ListTile(title: Text('Item 2')),
      ]),
    ),
  ],
)
```

---

## 8️⃣ Scroll Direction
```dart
ListView(
  scrollDirection: Axis.horizontal,
)
```

---

## 9️⃣ Common Scroll Errors & Fixes

### ❌ Vertical viewport was given unbounded height

**Cause:**

- ListView inside Column

**Fix:**

- Use `Expanded`
```dart
Expanded(
  child: ListView(),
)
```

---

## 🔟 ScrollView Comparison

| Widget                  | Use Case      |
|-------------------------|---------------|
| SingleChildScrollView   | Small content |
| ListView                | Long lists    |
| GridView                | Grid layout   |
| CustomScrollView        | Advanced UI   |
| ListWheelScrollView     | 3D wheel/picker |

---

## 1️⃣1️⃣ Best Practices

- Prefer `ListView.builder` for large data
- Avoid nesting scroll views
- Use `Expanded` inside Column

---

## 1️⃣2️⃣ ListWheelScrollView (3D Scroll Effect)

- Creates a **3D cylinder/wheel** style scrolling list
- Items appear to rotate on a 3D wheel
- Looks very cool and different from normal list

**Simple meaning:**

> ListView + 3D Rotation Effect = ListWheelScrollView

---

## 1️⃣3️⃣ ListWheelScrollView Basic Example
```dart
ListWheelScrollView(
  itemExtent: 80,   // height of each item (required)
  children: [
    Container(color: Colors.red, child: Text('Item 1')),
    Container(color: Colors.blue, child: Text('Item 2')),
    Container(color: Colors.green, child: Text('Item 3')),
    Container(color: Colors.orange, child: Text('Item 4')),
  ],
)
```

---

## 1️⃣4️⃣ ListWheelScrollView Important Properties

- `itemExtent` → height of each item **(required)**
- `children` → list of widgets
- `diameterRatio` → how curved the wheel looks (default: 2.0)
- `perspective` → 3D depth effect (small value = more 3D)
- `offAxisFraction` → tilt the wheel left or right
- `squeeze` → spacing between items
- `onSelectedItemChanged` → callback when item changes
- `physics` → scroll behavior

---

## 1️⃣5️⃣ Full ListWheelScrollView Example
```dart
class WheelExample extends StatefulWidget {
  @override
  State<WheelExample> createState() => _WheelExampleState();
}

class _WheelExampleState extends State<WheelExample> {
  int selectedIndex = 0;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('3D Scroll - ListWheelScrollView')),
      body: Column(
        children: [
          Text('Selected: Item $selectedIndex'),
          SizedBox(height: 20),
          SizedBox(
            height: 300,
            child: ListWheelScrollView(
              itemExtent: 80,
              diameterRatio: 1.5,
              perspective: 0.005,
              onSelectedItemChanged: (index) {
                setState(() {
                  selectedIndex = index;
                });
              },
              children: List.generate(10, (index) {
                return Container(
                  margin: EdgeInsets.all(8),
                  decoration: BoxDecoration(
                    color: Colors.blue,
                    borderRadius: BorderRadius.circular(12),
                  ),
                  child: Center(
                    child: Text(
                      'Item $index',
                      style: TextStyle(color: Colors.white, fontSize: 22),
                    ),
                  ),
                );
              }),
            ),
          ),
        ],
      ),
    );
  }
}
```

---

## 1️⃣6️⃣ ListWheelScrollView vs ListView

| Feature | ListView | ListWheelScrollView |
|---|---|---|
| Look | Flat 2D | 3D Wheel/Cylinder |
| Use Case | Normal lists | Pickers, selectors |
| itemExtent | Optional | Required |
| Performance | High | Good |

---

## 1️⃣7️⃣ Common Use Cases of ListWheelScrollView

- Time picker (hours / minutes)
- Age / date selector
- Country or city picker
- Product size selector

---

## 1️⃣8️⃣ Common Mistakes

- ❌ Forgetting `itemExtent` → required, app will crash
- ❌ Not wrapping in `SizedBox` with fixed height → unbounded height error
- ❌ Using too high `perspective` value → distorted look

---

## 1️⃣9️⃣ Interview Questions

- What is ListWheelScrollView?
- What is the difference between ListView and ListWheelScrollView?
- Which property is required in ListWheelScrollView?
- What does `diameterRatio` control?
- How to fix unbounded height error in ListWheelScrollView?

---

## 2️⃣0️⃣ Quick Revision Points

- ScrollView prevents overflow
- SingleChildScrollView → single child
- ListView → lists
- GridView → grid layout
- CustomScrollView → slivers
- ListWheelScrollView → 3D wheel scroll
- `itemExtent` is **required** in ListWheelScrollView
- `diameterRatio` controls the curve
- `onSelectedItemChanged` gives selected index
- Must wrap ListWheelScrollView in fixed height widget like `SizedBox`

---
