# 📦 SQFLite - Local Database in Flutter

> **Source:** WsCubeTech Flutter Course
> **Topic:** Database using sqflite package
> **Folder:** `09_database/`

---

## 📌 What is a Database?

- A **database** is a place where you store data permanently (even after app restart)
- In Flutter, for **local/offline storage** we use **SQLite** via the `sqflite` package
- SQLite = lightweight, file-based relational database
- Used in almost every mobile app that needs offline data

---

## 📌 Types of Storage in Flutter

| Type | Use Case | Example |
|------|----------|---------|
| SharedPreferences | Small key-value data | Settings, theme |
| SQLite (sqflite) | Structured/table data | Notes, contacts |
| Firebase | Cloud/online database | Chat apps |
| File Storage | Files, images | Documents |

> ✅ Use **sqflite** when you need to store **structured data** locally (like a table)

---

## 📌 What is sqflite?

- `sqflite` is a Flutter **plugin/package** for using SQLite database
- Works on **Android** and **iOS**
- Gives you methods to **Create, Read, Update, Delete (CRUD)** data
- Data is stored as a `.db` file on the device

---

## 📌 Step 1 — Add Dependencies

Open `pubspec.yaml` and add:

```yaml
dependencies:
  flutter:
    sdk: flutter
  sqflite: ^2.3.0
  path: ^1.9.0
```

Then run:

```bash
flutter pub get
```

> 📝 `path` package is needed to correctly find the database file location on device

---

## 📌 Step 2 — Import Packages

In your Dart file:

```dart
import 'package:sqflite/sqflite.dart';
import 'package:path/path.dart';
```

---

## 📌 Step 3 — Create a Model Class

A **model class** represents what data looks like (like a row in a table).

**Example — Note model:**

```dart
class Note {
  int? id;          // auto increment
  String title;
  String content;

  Note({
    this.id,
    required this.title,
    required this.content,
  });

  // Convert Note object → Map (for inserting into DB)
  Map<String, dynamic> toMap() {
    return {
      'id': id,
      'title': title,
      'content': content,
    };
  }

  // Convert Map → Note object (for reading from DB)
  factory Note.fromMap(Map<String, dynamic> map) {
    return Note(
      id: map['id'],
      title: map['title'],
      content: map['content'],
    );
  }
}
```

> 💡 `toMap()` = Object → Map (used when SAVING to DB)
> 💡 `fromMap()` = Map → Object (used when READING from DB)

---

## 📌 Step 4 — Create Database Helper Class

This is the **main class** that handles all database operations.
We use **Singleton pattern** so only ONE instance of the DB exists.

```dart
import 'package:sqflite/sqflite.dart';
import 'package:path/path.dart';

class DatabaseHelper {
  // Singleton instance
  static final DatabaseHelper instance = DatabaseHelper._init();

  static Database? _database;

  // Private constructor
  DatabaseHelper._init();

  // Getter — opens DB if not already open
  Future<Database> get database async {
    if (_database != null) return _database!;
    _database = await _initDB('notes.db');
    return _database!;
  }

  // Initialize / Open database
  Future<Database> _initDB(String fileName) async {
    final dbPath = await getDatabasesPath();           // Get device DB folder
    final path = join(dbPath, fileName);               // Full path to .db file

    return await openDatabase(
      path,
      version: 1,
      onCreate: _createDB,                             // Called first time only
    );
  }

  // Create table
  Future _createDB(Database db, int version) async {
    await db.execute('''
      CREATE TABLE notes (
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        title TEXT NOT NULL,
        content TEXT NOT NULL
      )
    ''');
  }
}
```

### 🔍 Key Points:
- `getDatabasesPath()` → finds the correct folder on Android/iOS to store DB
- `join()` → builds the full file path correctly for all platforms
- `openDatabase()` → opens the DB (creates file if it doesn't exist)
- `onCreate` → runs only the **first time** the app opens (creates table)
- `version: 1` → used for migrations when schema changes

---

## 📌 Step 5 — CRUD Operations

### ➕ CREATE — Insert Data

```dart
Future<int> insertNote(Note note) async {
  final db = await instance.database;
  return await db.insert('notes', note.toMap());
}
```

- `db.insert(tableName, data)` → inserts a row
- Returns the **id** of inserted row

---

### 📖 READ — Get All Data

```dart
Future<List<Note>> getAllNotes() async {
  final db = await instance.database;
  final result = await db.query('notes');               // SELECT * FROM notes
  return result.map((map) => Note.fromMap(map)).toList();
}
```

- `db.query(tableName)` → returns a `List<Map<String, dynamic>>`
- We convert each Map to a Note using `fromMap()`

---

### 📖 READ — Get Single Note by ID

```dart
Future<Note?> getNoteById(int id) async {
  final db = await instance.database;
  final result = await db.query(
    'notes',
    where: 'id = ?',           // condition
    whereArgs: [id],           // value for ?
  );
  if (result.isNotEmpty) {
    return Note.fromMap(result.first);
  }
  return null;
}
```

> ⚠️ Always use `whereArgs` (never put values directly in `where`) — prevents **SQL injection**

---

### ✏️ UPDATE — Update Existing Data

```dart
Future<int> updateNote(Note note) async {
  final db = await instance.database;
  return await db.update(
    'notes',
    note.toMap(),
    where: 'id = ?',
    whereArgs: [note.id],
  );
}
```

- Returns number of rows affected

---

### 🗑️ DELETE — Delete a Row

```dart
Future<int> deleteNote(int id) async {
  final db = await instance.database;
  return await db.delete(
    'notes',
    where: 'id = ?',
    whereArgs: [id],
  );
}
```

---

## 📌 Step 6 — Using in UI (main.dart / screen)

```dart
import 'database_helper.dart';
import 'note_model.dart';

void main() async {
  WidgetsFlutterBinding.ensureInitialized(); // MUST call before using DB
  runApp(MyApp());
}
```

> ⚠️ `WidgetsFlutterBinding.ensureInitialized()` — Must call this in `main()` before using async DB operations

### In your screen/widget:

```dart
// Insert
await DatabaseHelper.instance.insertNote(
  Note(title: 'My Note', content: 'Hello World'),
);

// Get all
List<Note> notes = await DatabaseHelper.instance.getAllNotes();

// Update
await DatabaseHelper.instance.updateNote(
  Note(id: 1, title: 'Updated', content: 'New content'),
);

// Delete
await DatabaseHelper.instance.deleteNote(1);
```

---

## 📌 Raw Queries (SQL directly)

Sometimes you want to write raw SQL:

```dart
// Raw Insert
await db.rawInsert(
  'INSERT INTO notes(title, content) VALUES(?, ?)',
  ['My Title', 'My Content'],
);

// Raw Query
List<Map> result = await db.rawQuery('SELECT * FROM notes WHERE id = ?', [1]);

// Raw Update
await db.rawUpdate('UPDATE notes SET title = ? WHERE id = ?', ['New Title', 1]);

// Raw Delete
await db.rawDelete('DELETE FROM notes WHERE id = ?', [1]);
```

---

## 📌 Close Database

```dart
Future close() async {
  final db = await instance.database;
  db.close();
}
```

> Usually not needed for simple apps — DB closes when app closes

---

## 📌 Complete File Structure for This Topic

```
09_database/
├── sqflite_notes.md        ← This file (notes)
├── note_model.dart         ← Model class
├── database_helper.dart    ← DB helper (CRUD methods)
└── notes_screen.dart       ← UI using the DB
```

---

## 📌 Full database_helper.dart (Complete File)

```dart
import 'package:sqflite/sqflite.dart';
import 'package:path/path.dart';
import 'note_model.dart';

class DatabaseHelper {
  static final DatabaseHelper instance = DatabaseHelper._init();
  static Database? _database;

  DatabaseHelper._init();

  Future<Database> get database async {
    if (_database != null) return _database!;
    _database = await _initDB('notes.db');
    return _database!;
  }

  Future<Database> _initDB(String fileName) async {
    final dbPath = await getDatabasesPath();
    final path = join(dbPath, fileName);
    return await openDatabase(path, version: 1, onCreate: _createDB);
  }

  Future _createDB(Database db, int version) async {
    await db.execute('''
      CREATE TABLE notes (
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        title TEXT NOT NULL,
        content TEXT NOT NULL
      )
    ''');
  }

  // INSERT
  Future<int> insertNote(Note note) async {
    final db = await instance.database;
    return await db.insert('notes', note.toMap());
  }

  // READ ALL
  Future<List<Note>> getAllNotes() async {
    final db = await instance.database;
    final result = await db.query('notes');
    return result.map((map) => Note.fromMap(map)).toList();
  }

  // READ ONE
  Future<Note?> getNoteById(int id) async {
    final db = await instance.database;
    final result = await db.query('notes', where: 'id = ?', whereArgs: [id]);
    if (result.isNotEmpty) return Note.fromMap(result.first);
    return null;
  }

  // UPDATE
  Future<int> updateNote(Note note) async {
    final db = await instance.database;
    return await db.update('notes', note.toMap(), where: 'id = ?', whereArgs: [note.id]);
  }

  // DELETE
  Future<int> deleteNote(int id) async {
    final db = await instance.database;
    return await db.delete('notes', where: 'id = ?', whereArgs: [id]);
  }

  // CLOSE
  Future close() async {
    final db = await instance.database;
    db.close();
  }
}
```

---

## 📌 Full note_model.dart (Complete File)

```dart
class Note {
  int? id;
  String title;
  String content;

  Note({
    this.id,
    required this.title,
    required this.content,
  });

  Map<String, dynamic> toMap() {
    return {
      'id': id,
      'title': title,
      'content': content,
    };
  }

  factory Note.fromMap(Map<String, dynamic> map) {
    return Note(
      id: map['id'],
      title: map['title'],
      content: map['content'],
    );
  }
}
```

---

## 📌 Quick Revision — Key Points

| Concept | What it does |
|---------|-------------|
| `sqflite` package | Provides SQLite for Flutter |
| `path` package | Finds correct file path on device |
| `getDatabasesPath()` | Gets the DB folder on device |
| `openDatabase()` | Opens/creates the `.db` file |
| `onCreate` | Runs once when DB is created |
| `db.insert()` | Add a new row |
| `db.query()` | Read rows (SELECT) |
| `db.update()` | Update existing row |
| `db.delete()` | Delete a row |
| `toMap()` | Object → Map (for DB) |
| `fromMap()` | Map → Object (from DB) |
| Singleton pattern | Only 1 DB instance in whole app |
| `whereArgs` | Safe way to pass conditions |
| `WidgetsFlutterBinding.ensureInitialized()` | Required in main() for DB |

---

## ⚠️ Common Mistakes to Avoid

1. ❌ Forgetting `WidgetsFlutterBinding.ensureInitialized()` in `main()`
2. ❌ Not using `whereArgs` (leads to SQL injection risk)
3. ❌ Creating multiple DB instances (always use singleton)
4. ❌ Forgetting `await` on database operations (they are all `async`)
5. ❌ Not calling `flutter pub get` after adding packages

---
