A full package includes a documentation, an installer, tests,
a licence file, a README.md file... To add all these files in
an orderly manner, we will modify the tree structure to use
the src layout.

From a terminal window inside the WORKDIR/calculator directory:

 - Create the `src/calculator` directory (`mkdir -p src/calculator`)
 - Move the source code inside (`mv *.py src/calculator`)
 - Remove the `__pycache__` directory (`rm -rf __pycache__`)

Import is now broken (from the other terminal window), but now that
we have a true package, we can install it; we just need to inform
`pip` how install it.

 - Create a file name `pyproject.toml` with the following content
   (choose a unique project name that won't clash with a serious package name):
   ```
   [build-system]
   requires = ["setuptools"]
   build-backend = "setuptools.build_meta"
   
   [project]
   name = "my_tuto_calculator_XXXX"
   authors = [
       {name = "Firstname Lastname", email = "firstname.lastname@domain.x"},
   ]
   description = "Extreme calculator"
   version = '0.0.0'
   ```
   In a normal use case, your project name is the same as the directory created in
   the `src` directory (`calculator`). Here we choose a different name to allow
   every one to push the same package on PyPI.
 - In `WORKDIR`, create a virtual environment and activate it
   (`python3 -m venv calcenv; . calcenv/bin/activate`)
 - From `WORKDIR/calculator`, install the package with
   `pip install -e .`

You can now import again your package with
`python3 -c "import calculator.basics"`.

And you can even test it: `python3 -c "from calculator.basics import
Calculator; c = Calculator(); print(c.add(4, 5))`.

The result is false, we can update the source code in
`src/calculator/basics.py` and run again the test. The important point
is to note that we don't need to install the package again. With the `-e`
(editable) option, you can edit and test rapidly your source code.

Git stuff:

 - `git status`
 - `echo '*.egg-info' >> .gitignore`
 - `git add src .gitignore *.py pyproject.toml`
 - `git commit`
 - and because we set a version number, we can add an annotated tag
   with `git tag -a`

README and LICENCE files will be added in the next [step](04_README_LICENSE.md).
