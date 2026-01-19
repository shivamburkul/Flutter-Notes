## Flutter Architecture

### What is Flutter Architecture?
Flutter architecture is the **structure of Flutter framework** showing how all layers work together to build an app.

It has **three main layers**:

---

### 1. Framework Layer (Dart)
- Written in **Dart** language
- Contains **Widgets, Rendering, Animation, and Material/Cupertino libraries**
- Developers mostly work in this layer
- Handles **UI, app logic, layouts, and animations**

**Key points:**
- Everything in Flutter is a **widget**
- StatelessWidget vs StatefulWidget exists here
- Hot Reload works mostly on this layer

---

### 2. Engine Layer (C++)
- Written in **C++**
- Provides **low-level rendering support**
- Uses **Skia graphics engine**
- Handles:
  - Drawing pixels on screen
  - Handling gestures
  - Animations
- Mostly invisible to developers

---

### 3. Platform Layer
- This is the **OS layer**
- Flutter apps run on:
  - **Android** → Java/Kotlin
  - **iOS** → Swift/Objective-C
  - **Web** → HTML/CSS/JS
  - **Desktop** → Windows/macOS/Linux
- Flutter uses **platform channels** to communicate with native features
  - Example: camera, GPS, storage

---

### How these layers work together
1. You write Dart code (Widgets, Layouts) → Framework Layer  
2. Framework passes rendering to Engine Layer → Skia draws pixels  
3. Engine communicates with Platform Layer → accesses device features  

---

### Flutter Architecture Diagram (Easy view)
