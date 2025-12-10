When using a simple module, we cannot use sub-modules as in
numerous packages; for example ma is a sub-module of numpy
and we can import it with `import numpy.ma`.

In `WORDIR`:

 - Create the directory calculator (`mkdir calculator`)
 - Move and rename the module (`mv calculator.py calculator/basics.py`)
 - In the another terminal (with the exported PYTHONPATH), you can import
   the package with `python3 -c "import calculator"`.
 - This technically works but is not exactly what we want. We must create
   an ` __init__.py` file (`touch calculator/__init__.py`) so that this
   directory is fully recognised as a package by python
 - We can import basics with `python3 -c "import calculator.basics"`

Note that you could add subdirectories inside `calculator`. It is a way
of organising your source code by grouping together codes that deal
with the same aspect in a directory. If you add a directory named
`advanced` in calculator with the file `subtraction.py` inside, you can
import it by `import calculator.advanced.subtraction` or
`from calculator.advanced import subtraction`.

Before going any further, we need to commit this first working version
to history:

 - `cd calculator`
 - `git init`
 - `git status`
 - `echo __pycache__ > .gitignore`
 - `git add .gitignore *.py`
 - `git commit`

We now have a directory with our source code but where can we
put the documentation, the tests, LICENSE...?

Next step [here](03_src_layout.md).
