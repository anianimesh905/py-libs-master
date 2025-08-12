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

NumPy will typically be much faster.

## 5. TL;DR (One-liner Summary)

NumPy is faster because it stores data in fixed-type, contiguous memory (ndarray) and processes it using optimized C code instead of slow Python loops.

---

# NumPy — Stage 2: Core Concepts — Array Creation

## 1. Creating Arrays from Lists

```python
import numpy as np

arr1 = np.array([1, 2, 3])  # 1D
arr2 = np.array([[1, 2, 3], [4, 5, 6]])  # 2D
# NumPy will automatically pick the best dtype
```

## 2. Using NumPy Functions

```python
np.arange(0, 10, 2)    # [0, 2, 4, 6, 8]
np.zeros((2, 3))       # 2x3 array of 0
np.ones((3, 3))        # 3x3 array of 1
np.full((2, 2), 7)     # 2x2 array filled with 7
np.eye(3)              # 3x3 identity matrix
```

## 3. Random Arrays

```python
np.random.rand(2, 3)               # Random floats in [0, 1)
np.random.randint(0, 10, (3, 3))   # Random integers
np.random.randn(2, 3)              # Normal distribution (mean=0, std=1)
```

## 4. Data Types (`dtype`)

```python
arr = np.array([1.2, 3.5], dtype=int)
print(arr.dtype)
# Common: int32, int64, float32, float64, bool
```
