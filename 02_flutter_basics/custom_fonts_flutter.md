# Adding Custom Font to Text in Flutter

## 1️⃣ What is Custom Font?

Custom font means using your own font style instead of default Flutter fonts.

**Helps in:**

- Better UI design
- Brand identity
- Professional look

---

## 2️⃣ Why Custom Fonts are IMPORTANT

- Default font looks basic
- Custom fonts make app attractive
- Almost all production apps use custom fonts

---

## 3️⃣ Supported Font Formats

Flutter supports:

- `.ttf`
- `.otf`

---

## 4️⃣ Step 1: Add Font Files

Create folder structure:
```
assets/
└── fonts/
    ├── Poppins-Regular.ttf
    ├── Poppins-Bold.ttf
```

You can download fonts from:

- Google Fonts

---

## 5️⃣ Step 2: Register Font in pubspec.yaml (VERY IMPORTANT)
```yaml
flutter:
  fonts:
    - family: Poppins
      fonts:
        - asset: assets/fonts/Poppins-Regular.ttf
        - asset: assets/fonts/Poppins-Bold.ttf
          weight: 700
```

⚠️ YAML indentation is VERY IMPORTANT.

---

## 6️⃣ Step 3: Use Custom Font in Text Widget
```dart
Text(
  'Hello Flutter',
  style: TextStyle(
    fontFamily: 'Poppins',
    fontSize: 20,
    fontWeight: FontWeight.bold,
  ),
)
```

---

## 7️⃣ Applying Font Globally (Recommended)
```dart
MaterialApp(
  theme: ThemeData(
    fontFamily: 'Poppins',
  ),
  home: MyHomePage(),
)
```

Now the font applies to entire app.

---

## 8️⃣ Using Multiple Font Weights
```dart
Text(
  'Light Text',
  style: TextStyle(
    fontFamily: 'Poppins',
    fontWeight: FontWeight.w400,
  ),
)

Text(
  'Bold Text',
  style: TextStyle(
    fontFamily: 'Poppins',
    fontWeight: FontWeight.w700,
  ),
)
```

---

## 9️⃣ Common Mistakes

- ❌ Wrong font path
- ❌ Wrong indentation in pubspec.yaml
- ❌ Font family name mismatch
- ❌ Forgetting `flutter pub get`

---

## 🔟 Best Practices

- Use Google Fonts
- Register fonts once
- Apply globally if possible
- Keep font files organized

---

## 1️⃣1️⃣ Interview Questions

- How to add custom font in Flutter?
- Where do we register fonts?
- Difference between local and global font usage?

---

## 1️⃣2️⃣ Quick Revision Points

- Fonts stored in `assets/fonts/`
- Registered in `pubspec.yaml`
- Use via `fontFamily`
- Can be applied globally
