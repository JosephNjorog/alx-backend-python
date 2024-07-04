# Python Variable Annotations

## Project Overview
This project focuses on Python variable annotations, which are used to specify the expected types of variables, function arguments, and return values. The goal is to practice type annotations and ensure the code is both readable and maintainable. Throughout this project, I implemented various functions and variables with type annotations, adhering to the requirements and best practices.

## Requirements
- Allowed editors: vi, vim, emacs
- All files interpreted/compiled on Ubuntu 18.04 LTS using Python 3 (version 3.7)
- All files should end with a new line
- The first line of all files should be exactly `#!/usr/bin/env python3`
- A README.md file, at the root of the folder of the project, is mandatory
- Code should use the `pycodestyle` style (version 2.5)
- All files must be executable
- File length will be tested using `wc`
- All modules should have documentation
- All classes should have documentation
- All functions (inside and outside a class) should have documentation

## Tasks

### Task 0: Basic annotations - add
**File:** `0-add.py`

I implemented a function `add` that takes two float arguments and returns their sum as a float. Using type annotations, I specified that both arguments and the return value are of type `float`.

```python
def add(a: float, b: float) -> float:
    return a + b
```

### Task 1: Basic annotations - concat
**File:** `1-concat.py`

I created a function `concat` that takes two string arguments and returns their concatenated result as a string. Type annotations were used to indicate the argument and return types.

```python
def concat(str1: str, str2: str) -> str:
    return str1 + str2
```

### Task 2: Basic annotations - floor
**File:** `2-floor.py`

In this task, I defined a function `floor` that takes a float argument and returns the largest integer less than or equal to the float. Type annotations specify the argument as a float and the return value as an integer.

```python
import math

def floor(n: float) -> int:
    return math.floor(n)
```

### Task 3: Basic annotations - to string
**File:** `3-to_str.py`

I implemented a function `to_str` that takes a float argument and returns its string representation. Type annotations were used to indicate the argument as a float and the return value as a string.

```python
def to_str(n: float) -> str:
    return str(n)
```

### Task 4: Define variables
**File:** `4-define_variables.py`

I defined and annotated several variables with specified values:
- `a`: an integer with a value of 1
- `pi`: a float with a value of 3.14
- `i_understand_annotations`: a boolean with a value of True
- `school`: a string with a value of "Holberton"

```python
a: int = 1
pi: float = 3.14
i_understand_annotations: bool = True
school: str = "Holberton"
```

### Task 5: Complex types - list of floats
**File:** `5-sum_list.py`

I wrote a function `sum_list` that takes a list of floats and returns their sum as a float. I used the `List` type from the `typing` module to annotate the argument and specified the return type as a float.

```python
from typing import List

def sum_list(input_list: List[float]) -> float:
    return sum(input_list)
```

### Task 6: Complex types - mixed list
**File:** `6-sum_mixed_list.py`

For this task, I created a function `sum_mixed_list` that takes a list of integers and floats and returns their sum as a float. I used `Union` from the `typing` module to indicate that the list can contain both `int` and `float`.

```python
from typing import List, Union

def sum_mixed_list(mxd_lst: List[Union[int, float]]) -> float:
    return sum(mxd_lst)
```

### Task 7: Complex types - string and int/float to tuple
**File:** `7-to_kv.py`

I implemented a function `to_kv` that takes a string and an int or float as arguments and returns a tuple. The tuple contains the string and the square of the int/float, annotated as a float. I used `Tuple` and `Union` from the `typing` module.

```python
from typing import Union, Tuple

def to_kv(k: str, v: Union[int, float]) -> Tuple[str, float]:
    return (k, float(v ** 2))
```

### Task 8: Complex types - functions
**File:** `8-make_multiplier.py`

In this task, I wrote a function `make_multiplier` that takes a float multiplier as an argument and returns a function. This returned function multiplies a float by the given multiplier. I used `Callable` from the `typing` module to annotate the return type.

```python
from typing import Callable

def make_multiplier(multiplier: float) -> Callable[[float], float]:
    def multiplier_function(value: float) -> float:
        return value * multiplier
    return multiplier_function
```

### Task 9: Let's duck type an iterable object
**File:** `9-element_length.py`

I annotated the function `element_length` which takes an iterable of sequences and returns a list of tuples. Each tuple contains a sequence and its length. I used `Iterable`, `Sequence`, `List`, and `Tuple` from the `typing` module.

```python
from typing import Iterable, Sequence, List, Tuple

def element_length(lst: Iterable[Sequence]) -> List[Tuple[Sequence, int]]:
    return [(i, len(i)) for i in lst]
```

### Task 10: Augment code with duck-typed annotations
**File:** `100-safe_first_element.py`

I augmented the function `safe_first_element` with the correct duck-typed annotations. The function takes a sequence and returns the first element if it exists, otherwise `None`. I used `Sequence`, `Any`, and `Union` from the `typing` module.

```python
from typing import Sequence, Any, Union

def safe_first_element(lst: Sequence[Any]) -> Union[Any, None]:
    if lst:
        return lst[0]
    else:
        return None
```

### Task 11: More involved type annotations
**File:** `101-safely_get_value.py`

I added type annotations to the function `safely_get_value`. This function takes a dictionary, a key, and an optional default value, returning the value associated with the key if it exists, otherwise the default value. I used `Mapping`, `Any`, `TypeVar`, and `Union` from the `typing` module.

```python
from typing import Mapping, Any, Union, TypeVar

T = TypeVar('T')

def safely_get_value(dct: Mapping, key: Any, default: Union[T, None] = None) -> Union[Any, T]:
    if key in dct:
        return dct[key]
    else:
        return default
```

### Task 12: Type Checking
**File:** `102-type_checking.py`

I used `mypy` to validate the code and applied necessary changes. The function `zoom_array` takes a tuple and an integer factor (default is 2), and returns a list where each element in the tuple is repeated `factor` times. I used `Tuple` and `List` from the `typing` module.

```python
from typing import Tuple, List

def zoom_array(lst: Tuple, factor: int = 2) -> List:
    zoomed_in: List = [
        item for item in lst
        for i in range(factor)
    ]
    return zoomed_in

array = (12, 72, 91)

zoom_2x = zoom_array(array)

zoom_3x = zoom_array(array, 3)
```

## Conclusion
Throughout this project, I enhanced my understanding and application of Python variable annotations. By using type hints, I improved code readability and maintainability, ensuring that function signatures and variable types are clear and explicit.
