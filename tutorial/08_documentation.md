Keeping documentation in the same repository as the source code is standard
practice. To do this, create a `docs` directory at the root of the repository.

# Documentation generation #

We will use doxygen to generate the doc from the source code and static
documents. Here, we choose to write our static document using the markdown
syntax, so that they can be directly read from github
(like the `README.md` file).

From the `docs` directory, we can run `doxygen -g doxygen_config` to create
a template for the doxigen configuration. In this tutorial, we will perform
only the modifications needed to make it functionnal:

 - modify the line with `PROJECT_NAME =` to get `PROJECT_NAME = "Calculator"`
 - replace the line with `INPUT =` by `INPUT = ../src/calculator ../README.md`
 - set `USE_MDFILE_AS_MAINPAGE` to `../README.md`
 - ste `GENERATE_LATEX` to `NO`
 - Optionaly, you can set `SOURCE_BROWSER` to `YES`
 - Optionaly, set `CALL_GRAPH` and `CALLER_GRAPH` to `YES`

Documentation is built with the command `doxygen doxygen_config` and the result
is in the newly created `html` directory. It can be seen with
`firefox html/index.html`.

We don't want to track this directory with git; then we add the line `docs/html`
to the `.gitignore` file.

# Documentation publication #

We will create a github workflow to automatically build the documentation when
a new commit is pushed; and publish it on github pages:

 - check your min branch name. By default git uses the name `master` for the main
   branch, but this can be modified by configuration. In this tutorial we use the
   name `master`.
 - create the file `.github/workflows/doxygen.yaml` at the root of your repository
   with the content
   ```
   name: Doxygen
   run-name: Updating online doc
   on:
     push:
       branches:
         - master
   jobs:
     deploy:
       runs-on: ubuntu-latest
       steps:
         - name: Checkout repository
           uses: actions/checkout@v4
           with:
             submodules: "true"
   
         - name: Install Doxygen
           run: sudo apt-get install doxygen
           shell: bash
   
         - name: Generate Doxygen Documentation
           run: cd docs; doxygen doxygen_config
           shell: bash
   
         - name: Create .nojekyll (ensures pages with underscores work on gh pages)
           run: touch docs/html/.nojekyll
           shell: bash
   
         - name: Deploy to GitHub Pages
           uses: JamesIves/github-pages-deploy-action@v4
           with:
             branch: gh-pages
             folder: docs/html
   ```
 - connect to your account on [https://github.com](https://github.com)
 - create a new repository (eg. `tuto_calculator`)
 - go to settings, and in `Actions/General` on the left, choose
   `Read and write permissions` in the `Workflow permissions` section
   at the end of the page.
 - copy the git url
 - in your local repository, `git remote add origin ` followed by the URL
 - commit your changes and `git push --set-upstream origin master`
 - go back to the github webpage of you repository
 - in addition to the `master` branch, you now have the `gh-pages` one
   that contains only the documentation
 - go back to the settings and choose `Pages` on the left and choose
   `gh-pages` in the `Branch` menu and save the configuration.
 - after a while, refresh, and click on the `Visit site` button on top
   of the page.

# What next #

Commit your changes and go to the [next](09_pylint.md) page to check if your
code is well written.
