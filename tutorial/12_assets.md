Sometimes, you want to include in your package a file
which is not a python script: an image, a text file... but
preferably not a compiled binary that may not be executable
once copied to a different system.

We add a file `foo.txt` in the `src/calculator` directory
and build again the wheel.

We can check that the new wheel file doens't contain the
file newly created (the wheel file is a zip archive that
your file explorer can certainly open). By default the build
process extract only files that are needed.

We have to modify the `pyproject.toml` file to add this section:
```
[tool.setuptools.package-data]
calculator = ['foo.txt']
```

Build again the wheel and check its content.
