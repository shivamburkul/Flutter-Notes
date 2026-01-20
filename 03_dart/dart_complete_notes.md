# Dart Complete Notes

This file contains **all important Dart concepts** required for Flutter development.  
Covers basics to advanced topics, suitable for long-term reference.

---

## 1. Introduction to Dart

- Dart = programming language by Google  
- Used for **Flutter development**  
- Compiles to **native code** (mobile/web)  
- Supports **OOP, null safety, async programming**

---

## 2. Variables & Data Types

### 2.1 Variables

- `var` → type inferred by compiler  
- `dynamic` → variable can hold any type  
- `final` → assigned once, runtime constant  
- `const` → compile-time constant
```dart
var name = "Shivam";
dynamic age = 21;
final pi = 3.14;
const gravity = 9.8;
```

### 2.2 Data Types

- `int` → integers
- `double` → decimals
- `String` → text
- `bool` → true/false
- `List` → array
- `Map` → key-value pair
- `Set` → unique collection
```dart
int age = 25;
double price = 99.99;
String name = "Flutter";
bool isActive = true;
List<int> numbers = [1,2,3];
Map<String,int> scores = {"Math":90};
Set<String> fruits = {"Apple","Banana"};
```

---

## 3. Operators

### 3.1 Arithmetic

- `+`, `-`, `*`, `/`, `~/` (integer division), `%` (modulus)

### 3.2 Assignment

- `=`, `+=`, `-=`, `*=`, `/=`, `%=`

### 3.3 Comparison

- `==`, `!=`, `>`, `<`, `>=`, `<=`

### 3.4 Logical

- `&&`, `||`, `!`

### 3.5 Null-aware Operators

- `??` → default value if null
- `?.` → access member if not null
- `??=` → assign value only if null
```dart
String? name;
print(name ?? "Guest"); // Guest
```

---

## 4. Control Flow

### 4.1 Conditional Statements
```dart
if(condition) { }
else if(condition) { }
else { }
```

### 4.2 Switch Case
```dart
switch(day){
  case 1: print("Monday"); break;
  case 2: print("Tuesday"); break;
  default: print("Other Day");
}
```

### 4.3 Loops

**for**
```dart
for(int i=0; i<5; i++){ print(i); }
```

**for-in** → iterates list
```dart
List<String> names = ["A","B"];
for(var n in names){ print(n); }
```

**while / do-while**
```dart
int i=0;
while(i<5){ print(i); i++; }
```

---

## 5. Functions

### 5.1 Basic Functions
```dart
int add(int a, int b){
  return a+b;
}
```

### 5.2 Arrow Functions
```dart
int square(int x) => x*x;
```

### 5.3 Optional & Named Parameters
```dart
void greet(String name, [String? message]){
  print("Hello $name ${message??""}");
}

void greetNamed({required String name, String message="Hi"}){
  print("$message $name");
}
```

### 5.4 Anonymous Functions
```dart
var list = [1,2,3];
list.forEach((n){ print(n); });
```

---

## 6. Object-Oriented Programming (OOP)

### 6.1 Classes & Objects
```dart
class Person{
  String name;
  int age;
  
  Person(this.name, this.age); // Constructor
  
  void info(){
    print("$name, $age years old");
  }
}

void main(){
  var p = Person("Shivam", 21);
  p.info();
}
```

### 6.2 Inheritance
```dart
class Employee extends Person{
  String role;
  Employee(String name,int age,this.role) : super(name,age);
}
```

### 6.3 Abstract Class & Interface
```dart
abstract class Animal{
  void sound();
}

class Dog implements Animal{
  void sound(){ print("Woof"); }
}
```

### 6.4 Getters & Setters
```dart
class Circle{
  double radius;
  Circle(this.radius);
  
  double get area => 3.14*radius*radius;
  
  set updateRadius(double r) => radius = r;
}
```

---

## 7. Collections

### 7.1 List
```dart
List<int> numbers = [1,2,3];
numbers.add(4);
numbers.removeAt(0);
```

### 7.2 Set
```dart
Set<String> fruits = {"Apple","Banana"};
fruits.add("Orange");
```

### 7.3 Map
```dart
Map<String,int> scores = {"Math":90};
scores["Science"]=95;
```

### 7.4 Iterating Collections
```dart
for(var item in numbers){ print(item); }
numbers.forEach((n){ print(n); });
```

---

## 8. Null Safety

- All variables non-nullable by default
- Nullable → add `?`
- Null-aware operators: `??`, `?.`, `??=`, `!`
```dart
String? name;
print(name ?? "Guest"); // Guest
```

---

## 9. Exception Handling
```dart
try{
  int result = 10 ~/0;
} catch(e){
  print("Error: $e");
} finally {
  print("Done");
}
```

---

## 10. Asynchronous Programming

### 10.1 Future
```dart
Future<String> fetchData() async{
  await Future.delayed(Duration(seconds:2));
  return "Data Loaded";
}

void main() async{
  String data = await fetchData();
  print(data);
}
```

### 10.2 Async/Await

- Use `async` in function
- Use `await` to wait for Future

### 10.3 Stream
```dart
Stream<int> counter() async*{
  for(int i=1;i<=5;i++){
    yield i;
  }
}

void main() async{
  await for(var i in counter()){
    print(i);
  }
}
```

---

## 11. Importing Packages
```dart
import 'dart:math';
import 'package:flutter/material.dart';
```

- `dart:` → built-in packages
- `package:` → external / Flutter packages

---

## 12. Key Points

- Dart = main language for Flutter
- Null safety ensures safer code
- Functions, classes, collections are used everywhere in Flutter
- Async programming required for API calls / Firebase
- OOP concepts → necessary for large apps

---

## 13. Common Mistakes

- Forgetting `?` for nullable types
- Using `var` when type clarity is needed
- Ignoring async/await for Futures → causes runtime errors
- Modifying const values
- Not adding packages to `pubspec.yaml`

---

## 14. Summary

- Learn variables, data types, operators
- Control flow: if/else, loops, switch
- Functions: named, optional, arrow, anonymous
- OOP: classes, inheritance, abstract, interface, getters/setters
- Collections: List, Map, Set
- Null safety, exception handling, async/await, Streams
- Import packages correctly
