# Java Operators — Execution & Bit-Level Understanding

## Purpose

This document explains how Java operators work at code level, how they translate to JVM instructions, and how they map to CPU-level operations.

---

## 1. What Are Operators?

Operators perform operations on data:

* arithmetic
* logical
* relational
* bit-level manipulation

At system level:

* operators → JVM bytecode
* bytecode → CPU instructions
* CPU → ALU operations

---

## 2. Unary Operators

Operate on a single operand.

### Increment / Decrement

#### Prefix

```java id="p1"
int a = 5;
++a;  // 6
```

#### Postfix

```java id="p2"
int a = 5;
a++;  // value used first, then increment
```

👉 Difference:

* prefix → increment first
* postfix → use first, increment later

---

### Logical NOT

```java id="p3"
!true → false
```

---

### Bitwise NOT

```java id="p4"
~5  // flips all bits
```

Example:

```text id="p5"
5  = 00000101
~5 = 11111010
```

---

### Type Cast

```java id="p6"
int x = (int) 5.7;
```

---

### Object Creation

```java id="p7"
new Object();
```

---

## 3. Arithmetic Operators

```java id="p8"
+  -  *  /  %
```

Example:

```java id="p9"
int x = 10 / 3;  // 3
```

👉 Integer division truncates decimal.

---

## 4. Relational Operators

```java id="p10"
==  !=  >  <  >=  <=
```

Return:

* boolean value

---

## 5. Logical Operators (Short-Circuit)

```java id="p11"
&&  ||
```

### Short-circuit behavior:

```java id="p12"
false && (expensiveOperation()) → skipped
```

👉 Important:

* saves computation
* avoids unnecessary execution

---

## 6. Bitwise Operators (ENTC Core)

```java id="p13"
&  |  ^
```

Example:

```text id="p14"
5 & 3 = 0101 & 0011 = 0001
```

---

## 7. Shift Operators

```java id="p15"
<<   >>   >>>
```

### Left Shift

```java id="p16"
5 << 1 = 10
```

👉 multiplies by 2

---

### Right Shift (Signed)

```java id="p17"
-8 >> 1
```

Preserves sign bit.

---

### Unsigned Right Shift

```java id="p18"
>>> 
```

Fills with zeros.

---

## 8. Assignment Operators

```java id="p19"
= 
```

---

### Compound Assignment

```java id="p20"
+=  -=  *=  /=  %=
&=  |=  ^=
<<= >>= >>>=
```

Example:

```java id="p21"
x += 5  → x = x + 5
```

---

## 9. Type Operator

```java id="p22"
instanceof
```

Checks:

* object type at runtime

---

## 10. Ternary Operator

```java id="p23"
condition ? expr1 : expr2
```

Example:

```java id="p24"
int min = (a < b) ? a : b;
```

---

## 11. Operator Precedence & Associativity

Defines execution order.

Example:

```java id="p25"
int x = 2 + 3 * 4;  // 14
```

Priority:

* `*` before `+`

---

## 12. Hardware Mapping (Critical)

Operators map to CPU ALU:

| Operator | Hardware Action           |
| -------- | ------------------------- |
| +        | Addition circuit          | 
| -        | Two’s complement addition |   
| &        | AND gate                  | 
| |        | OR gate                   | 
| ^        | XOR gate                  |  
| <<       | Bit shift register        |  
| >>       | Arithmetic shift          |  

---

## 13. Performance Insights

* Bitwise operations → faster than arithmetic
* Short-circuit → avoids computation
* Shifts → faster than multiply/divide (in many cases)

---

## 14. Common Pitfalls

* Confusing `==` vs `.equals()`
* Integer division loss
* Overflow in arithmetic
* Misusing `>>` vs `>>>`
* Ignoring short-circuit behavior

---

## 15. Bridge to JVM

Example:

```java id="p26"
int a = 5 + 3;
```

JVM bytecode:

* load 5
* load 3
* add

👉 maps directly to CPU addition

---

## Summary

Operators are not just syntax:

* they represent CPU-level instructions
* define how data is processed
* directly impact performance and correctness

Understanding operators builds:

* strong debugging skills
* efficient coding habits
* system-level clarity
