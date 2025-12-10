We will start with a simple module:

 - Open a terminal window and move to a working directory (this directory
   will be called `WORDIR` during this tutorial
 - Create a file named `calculator.py` with the following content:
   ```
   """
   Calculator module
   """
   
   class Calculator():
       """
       Calculator class implementing simple operations
       """
   
       def add(self, a, b):
           """
           Returns the addition of a with b
           """
           return a-b
   ```
  - In another terminal, move to your home directory and try to import the
    newly created module with `python3 -c "import calculator"`.
  - Python is not able to found your module, now you can set
    `export PYTHONPATH=$PYTHONPATH:WORKDIR` and try again to import your module.

This technique is acceptable for small independent modules that belong to us and
that we can then place in a personal directory with a PYTHONPAH setting in the
`.bash_profile` file.
But how do we manage projects that are a little larger, or that we want to share?

Next step [here](02_init.md).
