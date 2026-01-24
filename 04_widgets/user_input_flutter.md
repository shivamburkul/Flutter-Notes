# Getting User Input in Flutter

## 1️⃣ What is User Input?

User input means taking data from user.

**Examples:**

- Name
- Email
- Password
- Search text

In Flutter, user input is mainly taken using `TextField` and `TextFormField`.

---

## 2️⃣ TextField Widget (MOST IMPORTANT)

Basic example:
```dart
TextField()
```

---

## 3️⃣ TextField with Decoration
```dart
TextField(
  decoration: InputDecoration(
    labelText: 'Enter Name',
    hintText: 'Name',
    border: OutlineInputBorder(),
  ),
)
```

---

## 4️⃣ Getting Value using TextEditingController
```dart
TextEditingController nameController = TextEditingController();

TextField(
  controller: nameController,
)
```

**Access value:**
```dart
print(nameController.text);
```

---

## 5️⃣ Password Input Field
```dart
TextField(
  obscureText: true,
  decoration: InputDecoration(
    labelText: 'Password',
  ),
)
```

---

## 6️⃣ Keyboard Types
```dart
TextField(
  keyboardType: TextInputType.emailAddress,
)
```

**Common types:**

- `text`
- `number`
- `phone`
- `emailAddress`

---

## 7️⃣ onChanged & onSubmitted
```dart
TextField(
  onChanged: (value) {
    print(value);
  },
  onSubmitted: (value) {
    print('Submitted: $value');
  },
)
```

---

## 8️⃣ TextFormField (Used in Forms)
```dart
TextFormField(
  decoration: InputDecoration(
    labelText: 'Email',
  ),
)
```

**Difference:**

- `TextField` → simple input
- `TextFormField` → form + validation

---

## 9️⃣ Form & GlobalKey (Validation)
```dart
final _formKey = GlobalKey<FormState>();

Form(
  key: _formKey,
  child: Column(
    children: [
      TextFormField(
        validator: (value) {
          if (value!.isEmpty) {
            return 'Enter value';
          }
          return null;
        },
      ),
    ],
  ),
)
```

---

## 🔟 Submit Button with Validation
```dart
ElevatedButton(
  onPressed: () {
    if (_formKey.currentState!.validate()) {
      print('Valid Input');
    }
  },
  child: Text('Submit'),
)
```

---

## 1️⃣1️⃣ Common Mistakes

- ❌ Forgetting controller dispose
- ❌ Not validating inputs
- ❌ Using TextField instead of TextFormField in forms

---

## 1️⃣2️⃣ Best Practices

- Use controllers for important inputs
- Dispose controllers in `dispose()`
- Use validation for forms

---

## 1️⃣3️⃣ Interview Questions

- Difference between TextField & TextFormField?
- What is TextEditingController?
- How to validate user input?

---

## 1️⃣4️⃣ Quick Revision Points

- TextField → basic input
- Controller → get value
- TextFormField → validation
- Form → group inputs

---
