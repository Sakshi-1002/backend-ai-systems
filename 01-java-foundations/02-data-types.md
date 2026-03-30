# Java Data Types — Memory & System-Level View

## Purpose

This document explains how Java data types are defined, stored, and processed, connecting high-level syntax with memory representation and CPU execution.

---

## 1. Classification of Data Types

Java data types are divided into:

### 1. Primitive Types

* byte
* short
* int
* long
* float
* double
* char
* boolean

### 2. Non-Primitive Types

* Class
* Interface
* Array
* Enum
* Record

---

## 2. Primitive Types (Core Understanding)

Primitive types store **actual values directly in memory (stack or registers)**.

| Type    | Size          | Range (approx)           |
| ------- | ------------- | ------------------------ |
| byte    | 8-bit         | -128 to 127              |
| short   | 16-bit        | -32K to 32K              |
| int     | 32-bit        | ~±2 billion              |
| long    | 64-bit        | very large               |
| float   | 32-bit        | decimal (approximate)    |
| double  | 64-bit        | higher precision decimal |
| char    | 16-bit        | Unicode character        |
| boolean | JVM dependent | true / false             |

---

## 3. Memory Representation

### Integer Example:

```text
int a = 5
```

Stored as:

```text
00000000 00000000 00000000 00000101
```

### Floating Point:

* stored using IEEE 754
* consists of sign, exponent, mantissa

---

## 4. Why Primitives Exist

Primitives are:

* fast (no object overhead)
* memory-efficient
* directly handled by CPU registers

Objects (non-primitives):

* stored in heap
* accessed via references

---

## 5. Non-Primitive Types (Reference Types)

These store **memory addresses (references), not actual data**.

Example:

```java
String s = "Hello";
```

Memory:

* `s` → reference (stack)
* actual object → heap

---

## 6. Wrapper Classes

Each primitive has a corresponding wrapper:

| Primitive | Wrapper   |
| --------- | --------- |
| int       | Integer   |
| float     | Float     |
| double    | Double    |
| char      | Character |
| boolean   | Boolean   |

---

### Autoboxing

Automatic conversion:

```java
Integer x = 10;
```

---

### Unboxing

```java
int y = x;
```

---

## 7. Type Conversion

### 7.1 Widening (Implicit)

Safe conversion:

```java
int → long → float → double
```

No data loss (generally)

---

### 7.2 Narrowing (Explicit)

Risky conversion:

```java
double → int
```

Example:

```java
int x = (int) 5.7;  // 5
```

---

### 7.3 Numeric Promotion

During expressions:

```java
byte + byte → int
```

Reason:

* CPU operates efficiently on standard register size (32-bit)

---

### 7.4 Explicit Casting

Forcing conversion:

```java
(int) value
```

---

## 8. boolean Reality

Important:

* boolean is NOT clearly defined in bits in Java
* JVM decides internal representation

---

## 9. char Representation

* 16-bit unsigned
* supports Unicode

Example:

```java
char c = 'A';  // 65
```

---

## 10. Stack vs Heap Mapping

| Type      | Storage                   |
| --------- | ------------------------- |
| Primitive | Stack (direct value)      |
| Object    | Heap (reference in stack) |

---

## 11. Performance Insight

Primitive:

* faster access
* no garbage collection

Object:

* slower (indirection)
* managed by GC

---

## 12. Common Pitfalls

* Overflow not detected automatically
* float precision errors
* unnecessary boxing/unboxing
* incorrect casting

---

## 13. Bridge to JVM & Hardware

* Primitives → CPU registers / ALU operations
* Objects → heap memory + pointer dereferencing
* Type conversion → instruction-level casting

---

## Summary

Java data types define how data:

* is stored in memory
* is processed by CPU
* behaves during computation

Understanding this layer explains:

* performance differences
* memory usage
* runtime behavior

