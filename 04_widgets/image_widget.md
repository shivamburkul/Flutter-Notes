# Image Widget in Flutter

## 📍 Where to paste this file

- Folder: `04_widgets/`
- File name: `image_widget.md`

---

## 📌 What is Image Widget?

The `Image` widget is used to display images in a Flutter application.

Images can come from:

- Assets (local images)
- Network (internet images)
- File (device storage)
- Memory (bytes)

---

## 🧱 Common Image Constructors

### 1️⃣ Image.asset

Used to load images from your project assets.
```dart
Image.asset(
  'assets/images/logo.png',
)
```

### 2️⃣ Image.network

Used to load images from the internet.
```dart
Image.network(
  'https://example.com/image.png',
)
```

### 3️⃣ Image.file

Used to load images from device storage.
```dart
Image.file(
  File('/storage/emulated/0/image.png'),
)
```

### 4️⃣ Image.memory

Used when image is available as bytes.
```dart
Image.memory(bytes)
```

---

## 📁 Adding Image Assets (IMPORTANT)

### Step 1: Create folder structure
```
assets/
└── images/
```

### Step 2: Add image files

Example:
```
assets/images/logo.png
```

### Step 3: Register assets in `pubspec.yaml`
```yaml
flutter:
  assets:
    - assets/images/
```

⚠️ Indentation is VERY IMPORTANT in YAML.

---

## 🎨 Common Image Properties
```dart
Image.asset(
  'assets/images/logo.png',
  width: 100,
  height: 100,
  fit: BoxFit.cover,
  alignment: Alignment.center,
  color: Colors.red,
  colorBlendMode: BlendMode.colorBurn,
)
```

**Frequently Used Properties**

- `width`, `height`
- `fit`
- `alignment`
- `color`
- `opacity`

---

## 📐 BoxFit Options (VERY IMPORTANT)

| BoxFit Value        | Meaning                         |
|---------------------|---------------------------------|
| `BoxFit.cover`      | Covers entire space, may crop   |
| `BoxFit.contain`    | Fits image without cropping     |
| `BoxFit.fill`       | Stretches image                 |
| `BoxFit.fitWidth`   | Fits width                      |
| `BoxFit.fitHeight`  | Fits height                     |
| `BoxFit.none`       | Original size                   |
| `BoxFit.scaleDown`  | Scales down if needed           |

---

## 🧩 Image inside Container
```dart
Container(
  width: 150,
  height: 150,
  decoration: BoxDecoration(
    image: DecorationImage(
      image: AssetImage('assets/images/logo.png'),
      fit: BoxFit.cover,
    ),
  ),
)
```

---

## 🌐 Handling Network Image Errors
```dart
Image.network(
  'https://example.com/image.png',
  errorBuilder: (context, error, stackTrace) {
    return Icon(Icons.error);
  },
  loadingBuilder: (context, child, loadingProgress) {
    if (loadingProgress == null) return child;
    return CircularProgressIndicator();
  },
)
```

---

## ❌ Common Mistakes

- Forgetting to add image path in `pubspec.yaml`
- Wrong indentation in YAML
- Wrong image path or filename
- Not running `flutter pub get`
- Using large images without optimization

---

## ✅ Best Practices

- Use compressed images
- Prefer `BoxFit.cover` for UI
- Cache network images if needed
- Keep assets organized

---

## 🧠 Summary

- Use `Image.asset` for local images
- Use `Image.network` for internet images
- Register assets correctly
- Use `BoxFit` for proper scaling
- Images can be styled like any widget

---
