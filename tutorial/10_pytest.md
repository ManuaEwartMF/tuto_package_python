We need to install `pytest` in our virtual environment by
`pip install pytest`.

In the root directory of our project, we create the `tests` subdirectory
and add, inside it, a file named `test_simple.py` with this content:
```
"""
Tests for the package calculator
"""

from calculator.basics import Calculator

def test_add():
    """
    Tests the add method
    """
    c = Calculator()
    assert c.add(1, 2) == 3
```

The test is manually run with the command (from the root directory)
`python3 -m pytest`.

The test fails, we can modify the `basics.py` file and check again.

We can now automate the check on github by adding the `pytest.yaml`
file in the `.github/workflows` directory with the content:
```
name: Pytest
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout repository
      uses: actions/checkout@v4
    - name: Install dependencies
      run: pip install . pytest
    - name: Checking with pytest
      run: pytest
```

In the [next](11_pypi.md) part we will upload our package on Pypi.
