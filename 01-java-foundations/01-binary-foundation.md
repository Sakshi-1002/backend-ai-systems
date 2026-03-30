# Binary & Computational Foundation

## Purpose

This document explains how data is represented and processed at the lowest level of a computer system, forming the foundation for Java execution, memory behavior, and system design.

---

## 1. Why Computers Use Binary

Computers operate using electrical signals:

* HIGH voltage → 1
* LOW voltage → 0

Binary is used because:

* it is reliable under noise
* easier to implement using transistors
* supports stable switching (ON/OFF)

---

## 2. Digital Logic Basics

At hardware level:

* Transistors act as switches
* Logic gates (AND, OR, NOT) combine signals
* Complex circuits are built using these gates

Mapping:

* AND → multiplication logic
* OR → addition-like logic
* NOT → inversion

---

## 3. Bits, Bytes, and Data Width

* 1 bit = smallest unit (0 or 1)
* 8 bits = 1 byte

Data width defines how many bits CPU processes at once:

* 8-bit, 16-bit, 32-bit, 64-bit

In Java:

* `int` → 32 bits
* `long` → 64 bits

---

## 4. Binary Number System

Binary uses base-2 representation.

Example:

```text
1011 = (1×2³) + (0×2²) + (1×2¹) + (1×2⁰) = 11
```

---

## 5. Bit Representation in Memory

Data is stored as sequences of bits in RAM.

Example (`int = 5`):

```text
00000000 00000000 00000000 00000101
```

Memory stores:

* raw binary values
* no inherent meaning (interpretation depends on type)

---

## 6. Signed vs Unsigned Numbers

Unsigned:

* all bits represent magnitude
* range: 0 to 2ⁿ - 1

Signed (Java uses signed types):

* most significant bit (MSB) = sign bit
* 0 → positive
* 1 → negative

---

## 7. Two’s Complement Representation

Used to represent negative numbers.

Steps:

1. Invert bits
2. Add 1

Example (-5):

```text
5  = 00000101
~5 = 11111010
+1 = 11111011  → -5
```

Advantage:

* simplifies arithmetic operations in hardware

---

## 8. Arithmetic at Bit Level (ALU View)

CPU uses ALU (Arithmetic Logic Unit):

* performs addition, subtraction, logic operations

Binary addition example:

```text
  0101 (5)
+ 0011 (3)
------
  1000 (8)
```

Carry is generated when sum exceeds bit capacity.

---

## 9. Overflow & Underflow

Occurs when value exceeds representable range.

Example (8-bit signed):

```text
127 + 1 = -128
```

Reason:

* extra carry bit is discarded

---

## 10. Bitwise Operations

Operate directly on bits:

* AND (&)
* OR (|)
* XOR (^)
* NOT (~)
* Shift (<<, >>)

Example:

```text
5 & 3 = 0101 & 0011 = 0001
```

---

## 11. Power-of-2 Logic

A number is power of 2 if:

```text
n & (n - 1) == 0
```

Example:

```text
8  = 1000
7  = 0111
AND = 0000
```

---

## 12. Floating Point Representation (IEEE 754)

Floating numbers are stored as:

* Sign bit
* Exponent
* Mantissa

Example (float = 32 bits):

* 1 bit sign
* 8 bits exponent
* 23 bits mantissa

---

## 13. Precision Loss & Rounding Errors

Floating point cannot represent all decimal values exactly.

Example:

```text
0.1 + 0.2 ≠ 0.3 (exact)
```

Reason:

* binary approximation of decimal fractions

---

## 14. Endianness (Memory Layout)

Defines byte order in memory:

* Little Endian → least significant byte first
* Big Endian → most significant byte first

Example:

```text
0x12345678
Little → 78 56 34 12
Big    → 12 34 56 78
```

---

## 15. Bridge to Java

All Java operations rely on this foundation:

* primitives → binary representation
* operators → ALU instructions
* memory → RAM storage

Understanding this layer explains:

* overflow behavior
* performance differences
* JVM execution mapping

---

## Summary

Binary representation is the fundamental layer connecting:

* hardware (transistors, logic gates)
* CPU execution (ALU, registers)
* memory storage (bits, bytes)
* Java programs (data types, operations)

This forms the base for all higher-level abstractions in software systems.
