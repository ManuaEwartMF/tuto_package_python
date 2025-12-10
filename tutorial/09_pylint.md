Pylint (among others) allows you to maintain clean and consistent code,
which facilitates its maintenance and sharing.

You can manually run pylint with `pylint src/calculator`.

You can set up a GitHub workflow to automate this test and
ensure that it runs with every commit.
To do so, in your `.githubi/workflows` directory, you can create
the `pylint.yaml` file with the following content:
```
name: Pylint
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout repository
      uses: actions/checkout@v4
    - name: Install dependencies
      run: pip install pylint
    - name: Analysing the code with pylint
      run: pylint src/calculator
```

Note that you can define the pylint configuration in the
`tool.pylint` section of your `pyproject.toml` file.

Commit, push and check the result on github.

In addition to this code format test, functional tests can be run,
which are presented in the [next](10_pytest.md) section.
