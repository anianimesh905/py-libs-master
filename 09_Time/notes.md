# ⏳ Python `time` Module — Full Cheatsheet (Data Science & ML/DL Focus)

## 📌 Overview

The `time` module provides functions for:

- Working with timestamps
- Converting between human-readable time and epoch time
- Pausing execution
- Measuring performance

In **ML/DL**, you’ll use it for:

- Logging timestamps in training runs
- Measuring execution time for optimization
- Creating unique file/checkpoint names
- Adding controlled delays (API calls, batch intervals)

---

## 1️⃣ Getting Current Time

```python
import time

time.time()       # Seconds since epoch (float)
time.ctime()      # Human-readable current time
time.ctime(1700000000)  # Human-readable from timestamp
```

🔹 Unix Epoch = January 1, 1970, 00:00:00 UTC.
All timestamps in time are measured in seconds since this point.

---

## 2️⃣ Delays

```python
time.sleep(2)  # Pause for 2 seconds
```

💡 **Use Cases**: rate-limiting requests, pacing training loops.

---

## 3️⃣ Measuring Execution Time

**Basic:**

```python
start = time.time()
# Code block
end = time.time()
duration = end - start
```

**High-precision:**

```python
start = time.perf_counter()
# Code block
end = time.perf_counter()
duration = end - start
```

| Function              | Precision | Purpose                               |
| --------------------- | --------- | ------------------------------------- |
| `time.time()`         | \~1ms     | General timing                        |
| `time.perf_counter()` | High      | Benchmarking, performance measurement |

---

## 4️⃣ Struct Time (Local & UTC)

`struct_time` has attributes:

```
.tm_year, .tm_mon, .tm_mday, .tm_hour, .tm_min, .tm_sec, .tm_wday
```

```python
time.localtime()   # Local time as struct
time.gmtime()      # UTC as struct
```

---

## 5️⃣ Formatting & Parsing

**Format → String (`strftime`):**

```python
now_struct = time.localtime()
formatted = time.strftime("%Y-%m-%d %H:%M:%S", now_struct)
```

**String → Struct (`strptime`):**

```python
t_struct = time.strptime("2025-08-12 15:30:00", "%Y-%m-%d %H:%M:%S")
```

| Code | Meaning             |
| ---- | ------------------- |
| `%Y` | Year (2025)         |
| `%m` | Month (01–12)       |
| `%d` | Day (01–31)         |
| `%H` | Hour (00–23)        |
| `%M` | Minute              |
| `%S` | Second              |
| `%A` | Weekday name        |
| `%a` | Abbreviated weekday |
| `%B` | Month name          |
| `%b` | Abbreviated month   |

---

## 6️⃣ Convert Between Time Representations

```python
# Struct → Timestamp
ts = time.mktime(time.localtime())

# Timestamp → Struct
struct = time.localtime(ts)
```

---

## 7️⃣ ML/DL Practical Examples

**Training Loop Timing:**

```python
for epoch in range(3):
    start = time.perf_counter()
    # Training simulation
    time.sleep(1.2)
    print(f"Epoch {epoch+1} time:", round(time.perf_counter() - start, 2), "s")
```

**Unique Checkpoint Name:**

```python
filename = f"model_{time.strftime('%Y%m%d_%H%M%S')}.pt"
```

**Rate Limiting API Calls:**

```python
for _ in range(5):
    print("Fetching...")
    time.sleep(1)  # Wait 1 second between calls
```

---

## 8️⃣ Quick Reference Table

| Function                     | Purpose                  |
| ---------------------------- | ------------------------ |
| `time.time()`                | Seconds since epoch      |
| `time.ctime()`               | Human-readable timestamp |
| `time.sleep(s)`              | Pause execution          |
| `time.perf_counter()`        | High-precision timer     |
| `time.localtime()`           | Local time struct        |
| `time.gmtime()`              | UTC time struct          |
| `time.strftime(fmt, struct)` | Format struct → string   |
| `time.strptime(str, fmt)`    | Parse string → struct    |
| `time.mktime(struct)`        | Struct → timestamp       |

---

✅ **Tip:** For working with dates in ML pipelines (e.g., time-series), the `datetime` module is often better. Use `time` for **timing & delays**, `datetime` for **date manipulation**.
