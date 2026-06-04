---
author: Marian Guceanu
date: Why Everything Is Written in C
---
# Why Everything Is Written in C
Most used languages are Python, JavaScript, Java, C#.

All are built on top of C, or have libraries / core dependencies at least.

---
# Why Was C Created?
Look at this:
```asm
// setup for writing to stdout
mov $1,  %%eax      // 1 is the syscall number for write
mov $1,  %%edi      // 1 is also the stdout, because fd = 1
lea 0,   %%esi      // address of message, 0 for assumption
mov $1,  %%edx      // length, 1 for assumption
syscall
```

This is very close to machine code, but hard to read and maintain.

C was created as a simpler way to write low-level software.

---
# Why is C so important
Look at this language hierarchy: ```Rust -> C -> Assembly -> Machine Code```
- The closer we get to the bottom:
    - More control
    - More speed
    - More responsibility

---
# Why Do Computers Like C?
- C compiler translates pretty directly into those instructions
- From source code, straight to assembly as intermediary language
- For example, below code:
```c
    int add(int a, int b) { return a + b; }
```

---
- May turn (without any optimization) at compile phase to: 
```asm
add:
    push    rbp
    mov     rbp, rsp
    mov     DWORD PTR [rbp-4], edi
    mov     DWORD PTR [rbp-8], esi
    mov     edx, DWORD PTR [rbp-4]
    mov     eax, DWORD PTR [rbp-8]
    add     eax, edx
    pop     rbp
    ret
```

---
# The Operating System Problem
OS must:
- Talk to hardware
- Manage memory
- Control processes
- Handle keyboards
- Handle disks
- ...
Languages that require an existing OS cannot easily build an OS.
C can.

---
# Example: Linux kernel

Contains millions of lines of C code.
Why?
Because kernel must directly control:
- CPUs
- RAM
- Hard drives
- USB devices
- Graphics hardware

---
# Direct Memory Access Importance
Allows for **manipulation** as one sees fit, so **optimization** is at dev hands.

Some software must be extremely efficient. *(OS's, DB's, Browsers, Video games, Embedded devices, etc.)*

## *Every unnecessary operation costs time.*

Due to the specified reasons so far, we'll see most of the base code is actually implemented in C.

---
# Example: Python
Most people think Python is written in Python.

The most common (the standard) Python implementation is **CPython** which is written in C.

So when Python runs your code:

```python
print("Hello")
```

C code is doing most of the work behind the scenes.

---
# Why Is C Everywhere?

Three reasons: 
- *Speed*           -   highest low level language
- *Portability*     -   can run anywhere
- *Age*             -   been here for more than 50 years

A huge amount of software was built with it.

---
# The Network Effect

Imagine everyone in a city speaks the same language.

New people will adapt and learn the language to communicate.

The same happened with C.

New projects, libraries and even languages used C.

This created a cycle.

---
# *Q:* Can Other Languages Use C? 
# *A:* Yes

This is one of the most important reasons C survived.

Many languages can directly call C functions.

One library can be used everywhere.

---
# Real Example: SQLite

The same SQLite library can be used with *C, Python, Java, C#, JavaScript*.

Developers write a binding.

The actual database engine stays the same.

---
# Why Not Use C++ Instead?

C++ is extremely powerful.

However, C++ introduces complications:

- Templates
- Name mangling
- Exceptions
- Compiler differences

C provides a simpler interface.

Because of this, many C++ projects expose a C-compatible API.

---
# Why Not Rewrite Everything?

Rebuilding every road in the world can take decades.

The software world has the same problem.

Many C projects:
- Work well and are battle-tested
- Have been maintained for decades

There is little reason to replace them.

---
# *Q:* Is C Perfect?
# *A:* No

C gives programmers a lot of power. That can turn to risks.

Common problems:
- Memory leaks 
    - 70% of Microsoft security leaks are because of this
    - [](https://www.zdnet.com/article/microsoft-70-percent-of-all-security-bugs-are-memory-safety-issues/)
- Buffer overflows, crashes, undefined behavior

---
# What Is Actually Written In C Today?

Many important systems:
- OS's / Kernels
- DB engines
- Device drivers
- Language runtimes
- Networking software

---
# The Layer Cake

```text
Your Application
      ↓
Python / JavaScript / Java
      ↓
Language Runtime
      ↓
C Libraries
      ↓
Operating System
      ↓
Hardware
```

The deeper we go, the more likely we are to find C.

---
# Key Takeaway

Most software is not entirely written in C.

Instead:

- The foundations are often written in C.
- Higher-level languages build on top of those foundations.
- Performance-critical parts are frequently written in C or C++.

This is why developers often say:

"Everything is written in C."

It is not literally true.

But it is surprisingly close.

---
# How can YOU use C independently of itself

## DEMO
