It's time to add a READM.md file and a LICENCE file.

For the licence, the CeCILL one is a good choice for
a software developped in France, and in particular
the CeCILL-C version is well adapted to software
components.

In the terminal, in WORKDIR/calculator:

 - `wget -O LICENCE http://www.cecill.info/licences/Licence_CeCILL-C_V1-en.txt`
 - Edit the `README.md` file to include a description of the package
   ```
   Calculator
   ==========
   
   A powerfull calculator which handles additions.
   
   Usage:
   from calculator.basics import Calculator
   c = Calculator()
   print(c.add(4, 5))
   ```

Then `git add README.md LICENCE; git commit`.

In the [next](05_metadata.md) part we will add metadata to the package.
