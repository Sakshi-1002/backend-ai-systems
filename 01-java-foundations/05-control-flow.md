# Java Control Flow — Branching, Loops, and Execution Behavior

## Purpose

This document explains how control flow structures direct program execution, how they map to JVM instructions, and how CPUs handle branching and looping.

---

## 1. What is Control Flow?

Control flow determines:

* which statements execute
* in what order
* how many times

At system level:

* control flow → branch instructions
* branch → CPU decision (jump / continue)

---

## 2. if / else

Basic decision-making construct.

```java id="c1"
if (a > b) {
    max = a;
} else {
    max = b;
}
```

---

### Nested Conditions

```java id="c2"
if (a > b) {
    if (a > c) {
        max = a;
    }
}
```

---

## 3. switch Statement

Used for multi-way branching.

```java id="c3"
switch(day) {
    case 1: System.out.println("Mon"); break;
    case 2: System.out.println("Tue"); break;
}
```

---

## 4. Modern switch (Expression)

```java id="c4"
int result = switch(day) {
    case 1 -> 10;
    case 2 -> 20;
    default -> 0;
};
```

---

## 5. Loops

Used for repetition.

---

### for Loop

```java id="c5"
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}
```

---

### while Loop

```java id="c6"
while (i < 5) {
    i++;
}
```

---

### do-while Loop

```java id="c7"
do {
    i++;
} while (i < 5);
```

👉 executes at least once

---

## 6. break & continue

### break

* exits loop

```java id="c8"
break;
```

---

### continue

* skips current iteration

```java id="c9"
continue;
```

---

### Labeled break / continue

```java id="c10"
outer:
for (...) {
    for (...) {
        break outer;
    }
}
```

---

## 7. Recursion

A method calling itself.

```java id="c11"
int fact(int n) {
    if (n == 1) return 1;
    return n * fact(n - 1);
}
```

---

### Key Concepts:

* base case
* recursive call
* stack usage

---

## 8. Tail Recursion

Recursive call is last operation:

```java id="c12"
return fact(n - 1);
```

👉 Java does NOT optimize tail recursion automatically

---

## 9. StackOverflowError

Occurs when:

* recursion depth exceeds stack size

Example:

```java id="c13"
void infinite() {
    infinite();
}
```

---

## 10. Hardware Mapping (Critical Insight)

Control flow → CPU branch instructions:

| Java Construct | CPU Behavior     |
| -------------- | ---------------- |
| if / else      | conditional jump |
| switch         | jump table       |
| loop           | repeated branch  |
| recursion      | stack push/pop   |

---

## 11. Branch Prediction (Performance Insight)

Modern CPUs:

* predict branch outcomes
* optimize execution

Poor branching:

* causes pipeline stalls
* reduces performance

---

## 12. JVM Mapping

Example:

```java id="c14"
if (a > b)
```

JVM bytecode:

* compare values
* conditional jump

---

## 13. Common Pitfalls

* infinite loops
* missing break in switch
* deep recursion
* incorrect loop conditions
* misuse of labeled statements

---

## 14. Performance Considerations

* loops → efficient but must terminate
* recursion → expensive (stack overhead)
* branch-heavy logic → slower

---

## 15. Bridge to System Design

Control flow affects:

* execution efficiency
* scalability
* algorithm design

---

## Summary

Control flow defines how programs execute:

* decisions → branching
* repetition → loops
* recursion → stack-based execution

Understanding this helps:

* optimize performance
* debug logic
* design efficient algorithms
