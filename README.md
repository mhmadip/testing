# 🧪 Dart OOP Examples — Lab Class

A teaching example demonstrating **Object-Oriented Programming (OOP)** concepts in Dart.
Designed for students learning mobile development and OOP fundamentals.

![Dart](https://img.shields.io/badge/Dart-0175C2?style=flat&logo=dart&logoColor=white)
![Flutter](https://img.shields.io/badge/Flutter-02569B?style=flat&logo=flutter&logoColor=white)
![OOP](https://img.shields.io/badge/OOP-Fundamentals-green?style=flat)

---

## 📌 About

This repository contains simple, well-documented Dart examples that demonstrate
core OOP concepts including classes, constructors, encapsulation, and validation.

Intended for use in:
- Mobile Application Development courses
- OOP with Dart lectures
- Student lab exercises

---

## 🎯 OOP Concepts Covered

| Concept | Example |
|---------|---------|
| **Class** | `Lab` class definition |
| **Fields** | `labNo`, `labName` |
| **Immutability** | `final` keyword |
| **Constructor** | Default + named parameters |
| **Factory Constructor** | Input validation before object creation |
| **Encapsulation** | Private validation logic |
| **Method** | `displayInfo()` |
| **Override** | `toString()` |
| **Error Handling** | `try/catch` with `ArgumentError` |

---

## 📁 Files

```
├── lab.dart        # Lab class — main example
└── README.md       # Documentation
```

---

## 💻 Code Example

### v1 — Basic (Before Code Review)
```dart
class Lab {
  int labNo;
  String labName;

  Lab(this.labNo, this.labName);

  void displayInfo() {
    print('Lab Number: $labNo');
    print('Lab Name: $labName');
  }
}

void main() {
  Lab lab = Lab(101, 'Chemistry Lab');
  lab.displayInfo();
}
```

### v2 — Improved (After Code Review)
```dart
/// Represents a laboratory with its number and name.
class Lab {
  final int labNo;
  final String labName;

  /// Creates a [Lab] with the given [labNo] and [labName].
  const Lab({
    required this.labNo,
    required this.labName,
  });

  /// Validates input before creating a [Lab].
  factory Lab.create({required int labNo, required String labName}) {
    if (labNo <= 0) throw ArgumentError('Lab number must be positive');
    if (labName.trim().isEmpty) throw ArgumentError('Lab name cannot be empty');
    return Lab(labNo: labNo, labName: labName);
  }

  /// Displays lab information to the console.
  void displayInfo() {
    print('Lab Number: $labNo');
    print('Lab Name: $labName');
  }

  @override
  String toString() => 'Lab($labNo, $labName)';
}

void main() {
  try {
    final lab = Lab.create(labNo: 101, labName: 'Chemistry Lab');
    lab.displayInfo();
  } catch (e) {
    print('Error: $e');
  }
}
```

---

## 🔍 What Changed — v1 vs v2

| | v1 | v2 |
|-|----|----|
| Fields | Mutable `int`, `String` | Immutable `final` |
| Constructor | Positional parameters | Named parameters |
| Validation | None | Factory constructor with `ArgumentError` |
| Documentation | None | PHPDoc `///` comments |
| Error handling | None | `try/catch` in `main()` |
| `toString()` | Default | Custom override |

---

## 📖 Key Concepts Explained

### `final` — Immutability
```dart
final int labNo;  // cannot be changed after creation
```
Prevents accidental modification of object fields after construction.

### Named Parameters
```dart
const Lab({required this.labNo, required this.labName});
```
Makes code more readable — you always know what value is being passed.

### Factory Constructor
```dart
factory Lab.create({required int labNo, required String labName}) {
  if (labNo <= 0) throw ArgumentError('Lab number must be positive');
  ...
}
```
Validates input before creating the object — prevents invalid state.

### `toString()` Override
```dart
@override
String toString() => 'Lab($labNo, $labName)';
```
Makes debugging easier — `print(lab)` shows meaningful output.

---

## ▶️ How to Run

**Requirements:** Dart SDK installed

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git
cd YOUR_REPO

# Run the example
dart lab.dart
```

**Expected output:**
```
Lab Number: 101
Lab Name: Chemistry Lab
```

---

## 🎓 Teaching Notes

This example is designed to be taught in this order:

1. Start with **v1** — show students the basic class
2. Ask: *"What problems does this code have?"*
3. Introduce **v2** improvements one by one:
   - Why `final`?
   - Why named parameters?
   - Why a factory constructor?
   - Why `toString()`?
4. Show the **diff** using the Pull Request on GitHub

---

## 👨‍💻 Author

**Mohammad Salim Abdulrahman**
PhD Candidate in Cybersecurity — Universiti Kebangsaan Malaysia (UKM)
Lecturer & IT Specialist — Erbil, Kurdistan Region, Iraq

📧 mhmadip@gmail.com
🐙 [github.com/mhmadip](https://github.com/mhmadip)

---

## 📄 License

MIT License — free to use for teaching and learning purposes.
