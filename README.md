Another python package tutorial
===============================

This tutorial starts with a simple module and gradually develops
it into a complete Python package. The tutorial covers the following topics:

 - [use of PYTHONPATH](tutorial/01_PYTHONPATH.md)
 - [role of `__init__.py`](tutorial/02_init.md)
 - [the src layout, installation with pip](tutorial/03_src_layout.md)
 - [README and LICENSE files](tutorial/04_README_LICENSE.md)
 - [dependency management](tutorial/06_dependency)
 - [adding a command line client](tutorial/07_scripts)
 - [documentation: automatic generation and deployment on github pages](tutorial/08_documentation.md)
 - [linting with pylint](tutorial/09_pylint.md)
 - [tests with pytests](tutorial/10_pytest.md)
 - [publication on PyPI, wheel, sdists](tutorial/11_pypi.md)
 - [assets](tutorial/12_assets.md)

Not all aspects of packaging are covered in this tutorial; in particular,
it does not cover the creation of compiled extensions. Furthermore, a choice
has been made regarding the tools used (git, github, pylint, pytest, doxygen,
etc.), but other choices are perfectly valid.

In addition to this tutorial, a package skeleton has been
[proposed](https://gitlab.meteo.fr/cnrm-gmap/python-project-example) with
other choices regarding tools (it uses gitlab, doxygen and ruff).

Some prerequisites for this tutorial:

 - a linux computer with network
 - a github acount
 - python >= 3.8
 - an account on test.pypi.org (and the associated devide for the two
   factor authentification)

Tutorial begins [here](tutorial/01_PYTHONPATH.md).
