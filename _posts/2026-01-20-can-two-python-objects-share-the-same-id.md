---
title: Can two Python objects share the same ID?
category: python
tags:
  - Internals
---

In Python, the `id()` of an object is its memory address (or a unique identifier for that object during its lifetime). Whether two objects can share the same `id()` depends on when and what objects we are talking about.

## 1. While both objects are alive

No, two different live objects cannot have the same `id()`. If two names point to the same object, their `id()` will be the same -- but that is because they are not two separate objects.

```python
a = [1, 2, 3]
b = a
print(id(a) == id(b))  # True (same object)
```

## 2. After an object is destroyed (garbage collected)

Yes, IDs can be reused. When an object is no longer in use and is garbage collected, Python may reuse its memory address for a new object, giving it the same id as a previously destroyed one.

```python
x = 42
print(id(x))    # e.g., 140710982120336
del x
y = 43
print(id(y))    # Could be the same as x's id (reused)
```

## 3. Small integers and strings (interning)

Python reuses memory for certain immutable objects (like small integers -5 to 256 and some strings) through a process called interning. This means different variables can point to the same object.

```python
a = 100
b = 100
print(id(a) == id(b))  # True (both point to the same interned integer)
```

## In summary

* Two different live objects will never share the same `id()`.
* IDs can be reused after objects are destroyed.
* Interned objects (like small integers and some strings) will share the same `id()`.

## Bonus: what is interning?

Interning is a method used by Python to store only one copy of an immutable object (like certain strings or integers) to save memory and speed up comparisons. It is especially helpful in situations where identity checks are common.

### Interning of small strings

Python automatically interns:

* Identifiers (like variable names)
* Strings that look like identifiers (for example, `"hello"`, `"name"`)
* Short strings with only letters, digits, or underscores
* Some compile-time constant strings (literals used in your code)

Python does not automatically intern:

* Strings with spaces or special characters
* Strings created at runtime
* Long strings (beyond some length)

### Examples

#### Automatically interned strings

```python
a = "hello"
b = "hello"
print(a is b)        # True
print(id(a), id(b))  # Same id
```

#### Not automatically interned

```python
a = "hello world"
b = "hello world"
print(a is b)        # Often False
print(id(a), id(b))  # Likely different
```

#### Manually interning

```python
import sys

a = sys.intern("hello world")
b = sys.intern("hello world")
print(a is b)        # True
```

### Fun test with runtime strings

```python
x = "".join(["py", "thon"])
y = "python"
print(x == y)  # True (contents are same)
print(x is y)  # False (not same object, unless interned)

x = sys.intern(x)
print(x is y)  # Now True
```
