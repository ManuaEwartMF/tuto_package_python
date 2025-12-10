Requirements also go to the `pyproject.toml` file.
Firstly, the python version is defined in the `project`
section with, for example, `requires-python = ">= 3.6"`.

In addition, the package can rely on third party packages.
In `src/calculator/basics.py` we can add the line
`import f90nml` after the docstring and check that we cannot
import anymore our project with
`python3 -c "import calculator.basics"`.

In the `pyproject.toml` we add (in the `project` section
```
dependencies=[
    "f90nml",
            ]
```

If you wish to publish these packages with several configurations on PyPI,
you can also indicate optional dependencies by adding the following lines:

```
[project.optional-dependencies]
efficient = ["numpy", "scipy"]
graphics = ["tkinter"]
```

When downloading the package with pip it will now be possible to specify
which configuration you wish to install using brackets:
```
pip install calculator[efficient]  <- Will also install numpy and scipy
```

As for the version number, we must re-install the package to
take this modification into account:
`pip uninstall calculator; pip install -e .`.

Moreover, it is possible to deliver a `requirements.txt`
containing the list of packages to install. This file can be used
with `pip install -r requirements.txt`. But this file is not used
when issuing `pip install calculator`.

Dependencies are listed with as few constraints as possible on
version numbers so as not to limit the risk of making the
installation incompatible with other packages already installed.
Unlike the `requirements.txt` file, it is possible to fix all
versions in order to guarantee the reproducibility of results.

One can also encounter the `requirements_dev.txt` that contains
requirements for developpers.

Commit your change and in the [next](07_scripts.md) part,
we will add a command line client.
