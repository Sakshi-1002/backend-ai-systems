# Java Memory Model & Execution — Stack, Heap, and Runtime Behavior

## Purpose

This document explains how Java programs are executed in memory, how variables are stored, and how method calls are managed at runtime.

---

## 1. High-Level Execution Flow

When a Java program runs:

1. Code → compiled to bytecode
2. Bytecode → executed by JVM
3. JVM → manages memory (stack + heap)
4. CPU executes instructions

---

## 2. Stack Memory

Stack is used for:

* method calls
* local variables
* primitive values
* references (addresses)

### Characteristics:

* LIFO (Last In First Out)
* fast access
* automatically managed
* thread-specific

---

### Example:

```java id="m1"
void func() {
    int a = 10;
}
```

Memory:

* `a` stored directly in stack frame

---

## 3. Heap Memory

Heap is used for:

* objects
* arrays
* dynamic allocation

### Characteristics:

* shared across threads
* larger than stack
* managed by Garbage Collector (GC)

---

### Example:

```java id="m2"
String s = new String("Hello");
```

Memory:

* `s` → reference in stack
* "Hello" object → heap

---

## 4. Reference Variables

A reference variable:

* stores memory address (not actual object)

Example:

```java id="m3"
int x = 10;
String s = "Hi";
```

Memory:

* `x` → actual value (stack)
* `s` → reference (stack) → object (heap)

---

## 5. Stack Frame

Each method call creates a **stack frame**.

Contains:

* local variables
* parameters
* return address

---

### Example:

```java id="m4"
void main() {
    int x = 5;
    foo(x);
}
```

Call stack:

```text id="m5"
[ foo() frame ]
[ main() frame ]
```

---

## 6. Method Call Stack

Execution is managed using stack frames.

### Flow:

1. main() pushed
2. foo() called → pushed
3. foo() finishes → popped
4. main() continues

---

## 7. Pass-by-Value (Java Truth)

Java is **always pass-by-value**.

---

### Case 1: Primitive

```java id="m6"
void change(int a) {
    a = 20;
}
```

👉 original value unchanged

---

### Case 2: Object Reference

```java id="m7"
void change(String s) {
    s = "New";
}
```

👉 reference copy passed, not object itself

---

### Important:

* object can be mutated
* reference cannot be reassigned outside

---

## 8. Memory Visualization

```text id="m8"
Stack:
  x → 10
  s → address → Heap

Heap:
  Object ("Hello")
```

---

## 9. Garbage Collection (Intro)

Heap memory is managed automatically.

GC removes:

* objects with no references

---

### Example:

```java id="m9"
String s = new String("Hello");
s = null;
```

👉 "Hello" becomes eligible for GC

---

## 10. Stack vs Heap (Comparison)

| Feature    | Stack            | Heap             |
| ---------- | ---------------- | ---------------- |
| Storage    | primitives, refs | objects          |
| Speed      | fast             | slower           |
| Scope      | method-level     | application-wide |
| Management | automatic        | GC managed       |

---

## 11. Common Mistakes

* Thinking variable = container ❌
* Confusing reference with object ❌
* Assuming Java is pass-by-reference ❌
* Ignoring memory leaks ❌

---

## 12. Performance Insight

* Stack access → faster (direct)
* Heap access → slower (indirection)
* Object creation → costly

---

## 13. Bridge to JVM

JVM manages:

* stack frames
* heap allocation
* garbage collection

---

## 14. Bridge to Hardware

* stack → RAM (fast access region)
* heap → RAM (dynamic region)
* references → memory addresses
* CPU → executes instructions using registers

---

## Summary

Java memory model defines:

* where data is stored
* how methods execute
* how objects are managed

Understanding this explains:

* performance behavior
* bugs related to references
* memory usage and optimization
