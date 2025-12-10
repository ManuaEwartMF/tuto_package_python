Until now, our project is usable only from a python interpreter
or a script, but not from the command line.

We will add a command line tool in two steps. Fisrt, we add
the file `src/calculator/cli.py` with the following content:
```
"""
Calculator command line client
"""

import argparse
from calculator.basics import Calculator

def main():
    """
    Performs an addition
    """
    parser = argparse.ArgumentParser(description='Calculator')
    parser.add_argument('a', type=int)
    parser.add_argument('b', type=int)
    args = parser.parse_args()
    calc = Calculator()
    print(calc.add(args.a, args.b))
```

Then, in the `pyproject.toml` file, we add the section
```
[project.scripts]
'calculator_add' = "calculator.cli:main"
```

We can try it on the command line with `calculator_add -h` to see that
we need to reinstall the package (`pip uninstall calculator; pip install -e .`).
We can use it by `calculator_add 5 3`.

Now that our package is perfect, we must add a [documentation](08_documentation.md)
after having commited our changes.
