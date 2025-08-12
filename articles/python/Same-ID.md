# Is it possible that two objects in python have the same ID?

In **Python**, the `id()` of an object is its **memory address (or a unique identifier for that object during its lifetime)**. Whether two objects can share the same `id()` depends on **when** and **what** objects we are talking about:

---

### 1. **While both objects are alive**

**No**, two different live objects **cannot** have the same `id`.

* `id()` is unique for each object during its lifetime.
* If two names point to the same object, their `id()` will be the same — but that’s because they’re not two separate objects, just two references to one object:

```python
a = [1, 2, 3]
b = a
print(id(a) == id(b))  # True (same object)
```

---

### 2. **After an object is destroyed (garbage collected)**

**Yes**, IDs can be reused.

When an object is no longer in use and is garbage collected, Python may reuse its memory address for a new object, giving it the **same id** as a previously destroyed one.

Example:
```python
x = 42
print(id(x))    # e.g., 140710982120336
del x
y = 43
print(id(y))    # Could be the same as x's id (reused)
```

---

### 3. **Small integers and strings (interning)**

Python **reuses** memory for certain immutable objects (like small integers `-5 to 256` and some strings) through a process called **interning**.
This means different variables can point to the same object:

```python
a = 100
b = 100
print(id(a) == id(b))  # True (both point to the same interned integer)
```

---

**In summary:**

* **Two *different live* objects** will **never** share the same `id`.
* **IDs can be reused** after objects are destroyed.
* **Interned objects** (like small integers and some strings) will share the same `id` because they’re actually the **same object**.

---

## Bonus: 🔁 What Is *Interning*?

**Interning** is a method used by Python to **store only one copy of an immutable object** (like certain strings or integers) to save memory and speed up comparisons.

* Instead of creating a new object each time, Python reuses existing ones.
* This means many variables can point to the **same object in memory**, so `id()` will be the same.

---

## 🧵 Interning of Small Strings

Python automatically interns:

* **Identifiers** (like variable names)
* **Strings that look like identifiers** (e.g., `"hello"`, `"name"`)
* **Short strings with only letters, digits, or underscores** (`a-z`, `A-Z`, `0-9`, `_`)
* Some **compile-time constant strings** (e.g., literals used in your code)

Python **does *not*** automatically intern:

* Strings with **spaces**, **special characters**, or strings created at runtime
* Long strings (beyond some length)

You can also manually intern strings using `sys.intern()`.

---

## 🧪 Examples

### ✅ Automatically Interned Strings

```python
a = "hello"
b = "hello"
print(a is b)        # True
print(id(a), id(b))  # Same id
```

### ❌ Not Automatically Interned

```python
a = "hello world"
b = "hello world"
print(a is b)        # Often False
print(id(a), id(b))  # Likely different
```

### 💡 Manually Interning

```python
import sys

a = sys.intern("hello world")
b = sys.intern("hello world")
print(a is b)        # True
```

---

## ⚙️ Why Does Python Do This?

Interning saves:

* **Memory** (one object instead of many)
* **Time** in comparisons (e.g., `a is b` is faster than `a == b`)

It’s especially helpful in situations like:

```python
for word in big_list_of_words:
    if word is "target":  # Faster than word == "target"
        ...
```

---

## 🔥 Fun Test with Runtime Strings

```python
x = ''.join(['py', 'thon'])
y = 'python'
print(x == y)  # True (contents are same)
print(x is y)  # False (not same object, unless interned)
```

Now manually intern:

```python
import sys
x = sys.intern(x)
print(x is y)  # Now True
```
