Some metadata can be added to the `pyproject.toml` file.

These metadata are, for example, used by the PyPI repository to display
information on python packages.

This part of the tutorial does not cover dependencies or scripts, which
will be discussed later.

# Version #

First, let's go back to the version number entered in the `pyproject.toml`
file. Hard-coding it here is not ideal because we also want to be able to
access it from the python package (so that it can display its version
number, for example), but we don't want to duplicate the information
and risk inconsistencies. In the `pyproject.toml`, we delete the entry
`version = '0.0.0'` in the `project` section and replace it by
`dynamic = ["version"]` and we add:

```
[tool.setuptools.dynamic]
version = {attr = "calculator.__version__"}
```

We can now edit the `src/calculator/__init__.py` file and add the line
`__version__ = '0.0.1'`.

You can check the installed version with `pip list` and see that the version
number was not updated. You can do `pip uninstall calculator` and
`pip install -e .` and check again by `pip list`. This is a limitation
of the editable installation.

# README / LICENSE files #

The license used is defined in the `project` section with:

```
license = "CECILL-C"
license-files = ["LICENCE"]
```
where the `license-files` lists the file names containing the text of
the licence whereas the `license` keyword gives the standardised name
of the licence; the list of thoses names can be found
[here](https://spdx.org/licenses/).

The README.md file is referenced with `readme = "README.md"` still in
the `project` section.


# OTHER METADATA #

Other metadata can be provided, here are some examples:

 - In addition to the `authors` list, you can declare a `maintainers`
   list (with the same format, in the `project` section).
 - A list of keywords can be added with `keywords = []` in the `project`
   section.
 - The `classifiers` keyword (in the `project` section) can contain one
   or several classifiers, a list can be found
   [here](https://pypi.org/classifiers/). For example for our project
   we can add the folowing lines:
   ```
   classifiers = [
     'Development Status :: 5 - Production/Stable',
     'Intended Audience :: Science/Research',
     'Programming Language :: Python',
   ]
   ```
 - A section `project.urls` can be added with some urls, for example
   ```
   [project.urls]
     Bug = "https://github.com/USER/calculator/issues"
   ```
   The list of urls that can be added is
   [here](https://docs.pypi.org/project_metadata/#general-url).

# What next #

Don't forget to commit the modifications.
In the [Next](06_dependency) part of the tutorial, we will show how to add
dependency information to the `pyproject.toml` file.
