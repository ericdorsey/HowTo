## Demonstrate several different ways to import Python packages.
___

### Useful links

From:  
[Python relative imports for the billionth time](http://stackoverflow.com/questions/14132789/python-relative-imports-for-the-billionth-time/14132912#14132912)

> There are two ways to load a Python file: as the top-level script, or as a module. A file is loaded as the top-level script if you execute it directly, for instance by typing `python myfile.py` on the command line. It is loaded as a module if you do `python -m myfile`, or if it is loaded when an `import` statement is encounted inside some other file. There can only be one top-level script at a time; the top-level script is the Python file you ran to start things off.

___

### Examples


* `__init__.py`required at each level
* Comments in each show how it was called
  * `python -m` `each.folder` style without `.py`
  * `python` with `.py` using `sys.path.append()`


```
.
├── README.md
├── __init__.py
├── application.py
└── tests
    ├── __init__.py
    ├── test_application.py
    ├── test_four.py
    ├── test_three.py
    └── test_two.py
```

#### `tests/test_application.py`:

```python
# Need to run from the parent of imports_example/
#
# ~/PycharmProjects $ python -m imports_example.tests.test_application
# printed from application.py

from ..import application

application.app_printer()
```
#### `tests/test_two.py`:

```python
# Run from imports_example/
#
# ~/PycharmProjects/imports_example $ python -m tests.test_two
# printed from application.py

import application

application.app_printer()
```

#### `tests/test_three.py`:

```python
# Run from imports_example/
#
# ~/PycharmProjects/imports_example $ python -m tests.test_three
# printed from application.py

from application import app_printer

app_printer()
```

#### `tests/test_four.py`:

```python
import sys
sys.path.append('..')
import application

# Run from imports_example/tests/
#
# ~/HowTo/Python/imports_example/tests $ python test_four.py
# printed from application.py

application.app_printer()
```