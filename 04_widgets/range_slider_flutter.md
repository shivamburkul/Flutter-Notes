# Range Slider in Flutter 

## 1️⃣ What is a Range Slider?

A Range Slider allows user to select a range between two values.

It has two thumbs (handles).

**Example:**

> Price range: ₹1000 – ₹5000

---

## 2️⃣ Why Use Range Slider?

- Selecting minimum & maximum values
- Filters (price, age, distance)
- Better UX than text input

---

## 3️⃣ Difference Between Slider & RangeSlider

| Slider        | RangeSlider      |
|---------------|------------------|
| One value     | Two values       |
| Single thumb  | Two thumbs       |
| Example: volume | Example: price range |

---

## 4️⃣ Basic Requirement

`RangeSlider` requires `StatefulWidget` because values change.

---

## 5️⃣ Basic RangeSlider Example
```dart
class RangeSliderExample extends StatefulWidget {
  @override
  State<RangeSliderExample> createState() => _RangeSliderExampleState();
}

class _RangeSliderExampleState extends State<RangeSliderExample> {
  RangeValues values = RangeValues(20, 80);

  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        Text('Range: ${values.start} - ${values.end}'),
        RangeSlider(
          values: values,
          min: 0,
          max: 100,
          divisions: 10,
          labels: RangeLabels(
            values.start.round().toString(),
            values.end.round().toString(),
          ),
          onChanged: (RangeValues newValues) {
            setState(() {
              values = newValues;
            });
          },
        ),
      ],
    );
  }
}
```

---

## 6️⃣ Important Properties

- `values`: current range values
- `min`: minimum value
- `max`: maximum value
- `divisions`: steps between values
- `labels`: text shown on slider
- `onChanged`: updates values

---

## 7️⃣ Styling RangeSlider
```dart
RangeSlider(
  activeColor: Colors.blue,
  inactiveColor: Colors.grey,
  values: values,
  min: 0,
  max: 100,
  onChanged: (newValues) {
    setState(() {
      values = newValues;
    });
  },
)
```

---

## 8️⃣ Disabling RangeSlider
```dart
onChanged: null
```

---

## 9️⃣ Common Mistakes

- ❌ Using StatelessWidget
- ❌ Forgetting `setState()`
- ❌ min value greater than max

---

## 🔟 Best Practices

- Always show selected values
- Use divisions for better UX
- Validate range logic

---

## 1️⃣1️⃣ Interview Questions

- Difference between Slider & RangeSlider?
- Why RangeSlider needs StatefulWidget?
- What is RangeValues?

---

## 1️⃣2️⃣ Quick Revision Points

- RangeSlider selects range
- Uses `RangeValues`
- Needs StatefulWidget
- `setState` updates UI
