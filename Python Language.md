# Python Language – Production Cheat Sheet

> **Purpose**: Zero-theory, high-utility Python cheat sheet.
> Built for **real coding**, **data work**, **AI/ML**, and **backend systems**.
> Optimized for **speed**, **clarity**, and **safe production usage**.
> Aligned with **OWASP Top 10** and **ISO/IEC 27001:2022**.

---

## 1. Python Mental Model (Internalize This)

* Python is **interpreted**, **dynamic**, and **duck-typed**
* Readability beats cleverness
* Explicit > implicit
* Errors are signals, not annoyances

If your code is hard to read, it is wrong.

---

## 2. Environment Setup (Mandatory Discipline)

```bash
python --version
python -m venv .venv
source .venv/bin/activate   # Linux/Mac
.venv\\Scripts\\activate  # Windows
pip install -U pip
```

Freeze dependencies:

```bash
pip freeze > requirements.txt
```

---

## 3. Core Syntax (Daily Use)

### Variables & Types

```python
x = 10
name = "Navi"
pi = 3.14
is_valid = True
```

### Type Checking

```python
type(x)
isinstance(x, int)
```

---

## 4. Collections (Use Correctly)

### List

```python
nums = [1, 2, 3]
nums.append(4)
```

### Tuple (Immutable)

```python
point = (10, 20)
```

### Set

```python
s = {1, 2, 3}
s.add(4)
```

### Dict

```python
user = {"id": 1, "name": "Alice"}
user["role"] = "admin"
```

---

## 5. Control Flow

```python
if x > 5:
    print("High")
elif x == 5:
    print("Equal")
else:
    print("Low")
```

```python
for i in range(5):
    print(i)
```

```python
while condition:
    break
```

---

## 6. Functions (Write Clean Ones)

```python
def add(a: int, b: int) -> int:
    return a + b
```

### Default Arguments

```python
def connect(host="localhost", port=5432):
    pass
```

---

## 7. Lambda & Comprehensions (Use Sparingly)

```python
square = lambda x: x * x
```

```python
squares = [x*x for x in range(5)]
```

Readable > clever.

---

## 8. Error Handling (Non-Negotiable)

```python
try:
    risky()
except ValueError as e:
    log.error(e)
finally:
    cleanup()
```

Never silence exceptions blindly.

---

## 9. Files & I/O

```python
with open("data.txt", "r") as f:
    data = f.read()
```

```python
import json
json.dump(obj, open("out.json", "w"))
```

---

## 10. Modules & Imports

```python
import os
from datetime import datetime
```

Never use `import *`.

---

## 11. Virtual Environments & Packaging

```bash
pip install requests
pip uninstall package
```

```python
import requests
```

---

## 12. Object-Oriented Python (Use When Needed)

```python
class Agent:
    def __init__(self, name):
        self.name = name

    def act(self):
        return f"{self.name} acting"
```

Avoid deep inheritance trees.

---

## 13. Dataclasses (Use This Instead of Boilerplate)

```python
from dataclasses import dataclass

@dataclass
class Product:
    id: int
    name: str
    demand: int
```

---

## 14. Type Hinting (Production Standard)

```python
from typing import List, Dict

def process(data: List[int]) -> Dict[str, int]:
    return {"count": len(data)}
```

---

## 15. Logging (Never Use print in Prod)

```python
import logging
logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

logger.info("Started")
```

---

## 16. Testing (Minimum Viable Discipline)

```python
def test_add():
    assert add(2, 3) == 5
```

Use pytest.

---

## 17. Security Basics (OWASP Aligned)

* Never trust user input
* Validate types and ranges
* Use `secrets` for tokens
* Avoid `eval` and `exec`
* Keep dependencies updated

---

## 18. Performance Basics

* Prefer generators for large data
* Avoid nested loops
* Use built-in functions
* Profile before optimizing

---

## 19. Common Anti-Patterns (Stop Doing These)

* God functions
* Global mutable state
* Silent exceptions
* Hardcoded paths
* No virtualenv

---

## 20. Absolute Emergency Snippets

```python
import sys
print(sys.path)
```

```python
import traceback
traceback.print_exc()
```

```bash
pip freeze | grep package
```

---

## 21. Mental Model to Remember

> Python rewards clarity.
> If it looks clever, it is probably wrong.

---

