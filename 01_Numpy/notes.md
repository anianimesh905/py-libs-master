# NumPy — Stage 1: Overview

## 1. What is NumPy?

- NumPy (**Num**erical **Py**thon) is a Python library for fast numerical computing.
- It introduces the **ndarray** (N-dimensional array) for storing and processing numerical data efficiently.

## 2. Why NumPy instead of Python lists?

- **Lists** are flexible but slow for large-scale numerical operations.
- NumPy arrays:
  - Store a single data type (homogeneous) → more memory efficient.
  - Store data in contiguous memory → faster access.
  - Use optimized C code under the hood → much faster than Python loops.

## 3. Key Advantages

1. **Speed** — up to 10–100x faster for large datasets.
2. **Memory efficiency** — compact storage.
3. **Vectorization** — operations on entire arrays without explicit loops.
4. **Broadcasting** — combining arrays of different shapes without extra code.
5. **Rich functionality** — math, stats, linear algebra, random numbers, etc.

## 4. Quick Example (Speed Test)

```python
import numpy as np
import time

# Python list
lst = list(range(10_000_000))
start = time.time()
lst = [x + 1 for x in lst]
print("Python list:", time.time() - start, "seconds")

# NumPy array
arr = np.arange(10_000_000)
start = time.time()
arr = arr + 1
print("NumPy array:", time.time() - start, "seconds")
```
