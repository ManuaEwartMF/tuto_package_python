Before proceeding, verify that the package name defined in
the `pyproject.toml` file will not cause any issues, as it
will be impossible for anyone else to use it later.

Instead of publishing on `pypi.org`, we will publish on `test.pypi.org`.

If not already done, in your account parameters, create a token and save
it in your `~/.pypirc` file like this:
```
[distutils]
  index-servers =
    pypitest

[pypitest]
  repository = https://test.pypi.org/legacy/
  username = __token__
  password = YOUR_PYPI_TOKEN_HERE
```

Then, you can install `pip install build twine` the needed packages
and build the wheel (version ready to be installed of your package)
with `python -m build`. The building process has created a `dist`
directory with a wheel (`*.whl` file) and a source distribution
(`*.tar.gz` file). In our case (no compiled library), the wheel
is the one to upload on pypi with
`python -m twine upload --repository pypitest dist/*-0.0.1-py3-none-any.whl`.

To check it, you can uninstall your editable version
(`pip uninstall calculator`i) and install the wheel. You can install
the local wheel with `pip install dist/tuto_calculator_sr-0.0.1-py3-none-any.whl` or
the one from pypi with `pip install --index-url https://test.pypi.org/simple YOUR_PACKAGE_NAME`
(`_` in your project name are replaced by `-`).

After having pushed your project on Pypi, you can go to the settings
associated to your package (on `test.pypi.org`) and create a token
specific to this package. This token is added to your `~/.pypirc`
which is now:
```
[distutils]
  index-servers =
    pypitest
    tuto

[pypitest]
  repository = https://test.pypi.org/legacy/
  username = __token__
  password = YOUR_PYPI_TOKEN_HERE

[tuto]
  repository = https://test.pypi.org/legacy/
  username = __token__
  password = YOUR_TUTO_TOKEN_HERE
```

Now, you can push new release with
`python -m twine upload --repository tuto ...`. This token can be
shared with other personns involved in the developpement of this
package.

In the [following](12_assets.md) part, we will include an asset.
