# Welcome to MkDocs

For full documentation visit [mkdocs.org](https://www.mkdocs.org).

## Commands

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.
* `mkdocs

## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.
--------------

Got it 🙂 — you want to generate a separate branch (usually gh-pages) using MkDocs so that your site can be built and deployed from that branch.

I'll explain step by step how to do this.


---

Scenario

You have a repository with MkDocs project files.

You want to build your documentation into site/.

You want the built HTML files to go to a separate branch (e.g., gh-pages).

Your source code stays on another branch (e.g., main).



---

1. Install MkDocs and the Deploy Tool

Make sure MkDocs is installed:

pip install mkdocs

To automatically create and push a separate branch (gh-pages):

pip install mkdocs-material   # optional if using Material theme
pip install mkdocs


---

2. Basic Build Command

Normally, MkDocs builds your docs like this:

mkdocs build

This creates a site/ directory with static HTML files.

By default, it stays on the same branch.


But if you want a separate branch, you shouldn’t push site/ manually — you should use mkdocs gh-deploy.


---

3. Deploy to a Separate Branch

MkDocs has a built-in command to create and push the built site to a separate branch:

mkdocs gh-deploy 

How It Works

It builds your docs.

Creates a temporary commit with the contents of site/.

Pushes it to the gh-pages branch.

Keeps your main branch clean.



---

4. Set Up GitHub Pages

1. Go to GitHub → Your Repo → Settings → Pages.


2. Under Build and deployment → Source, select Deploy from a branch.


3. Choose Branch = gh-pages and Folder = / (root).


4. Save.




---

5. If You Want a Custom Branch Name

You can specify another branch instead of gh-pages:

mkdocs gh-deploy --remote-branch docs-build

Then configure GitHub Pages to use docs-build.


---

6. Keep the Build Branch Separate

Make sure to ignore the site/ folder in your source branch:

In .gitignore:

site/

Because MkDocs automatically rebuilds it, you don’t want to commit it manually.


---

7. For Multiple Branch Docs (Optional)

If you want to build docs from multiple branches (e.g., main, dev, release), you'll need an extra plugin called mkdocs-multiversion.
I can guide you on that if needed.
