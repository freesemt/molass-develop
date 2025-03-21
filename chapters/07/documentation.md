# Documentation

```{warning}
This page is in preparation to be publicly available in May, 2025.
```

## Documents to be maintained

We have the following documents, including this book, to maintain.

|No |   Document Name           | Source License | Used Tool |
|:-:|:--------------------------|:--------|:-----------|
| 1 |[Molass Legacy Reference](https://freesemt.github.io/molass-legacy/) |GPL-3.0 |Sphinx |
| 2 |[Molass Libray Reference](https://freesemt.github.io/molass-library/)|GPL-3.0 |Sphinx |
| 3 |[Molass Libray Essense](https://freesemt.github.io/molass-essense/)  |CC BY 4.0|Jupyter Book|
| 4 |[Molass Libray Tutorial](https://freesemt.github.io/molass-tutorial/)|CC BY 4.0|Jupyter Book|
| 5 |[Molass Developer's Handbook](https://freesemt.github.io/molass-develop/)|CC BY 4.0|Jupyter Book|

For the first two reference books, we use [Sphinx](https://github.com/sphinx-doc/sphinx) directly to generate function documents from their [docstrings](https://peps.python.org/pep-0257/). For others, [Jupyter Book](https://github.com/jupyter-book/jupyter-book), which depends on Sphinx, is used.

## How to use Jupyter Book

### Tool Package Installation

To use Jupyter Book, you need to install the following two packages.

```
pip install -U jupyter-book
pip install -U ghp-import
```

### Initial Book

Each initial book was created as follows.

    ・ jupyter-book create template-repo
    ・ create a repository on GitHub
    ・ git clone book-repo
    ・ copy the contents of template-repo to book-repo

```{note}
You need this procedure only when you create a new book.
```

### Manual Edit

When you edit the source files manually, first files to attend are the following two.

    ・ _config.yml
    ・ _toc.yml

These files are usually placed either at the root of the repository or the docs sub folder. Compare them with those of an existing book, then you should begin to know how to edit.

See also as you proceed:

* [Create your first book](https://jupyterbook.org/en/stable/start/your-first-book)
* [MyST syntax cheat sheet](https://jupyterbook.org/en/stable/reference/cheatsheet.html)

### Update Cycle

We repeat the following cycle to update.

    ・ edit manually
    ・ generate locally
    ・ synchronize master branch
    ・ deploy gh-pages branch

```{note}
For maintenance of the web page, the two branches, namely master and gh-pages, are involved. The former keeps the source and the latter the generated target.
```

After manual edit, generation will be achieved as follows in Command Prompt:

```none
cd book-repo
jupyter-book build .
```

After generation, check the generated local output in _build/html with the browser. Re-edit as needed until you are satisfied.

Synchronization of the master branch will be achieved as follows in VS Code:

    ・ commit in VS Code
    ・ synchronize with GitHub in VS Code

Update and deployment of the gh-pages branch will be achienved as follows in Command Prompt:

```none
ghp-import -n -p -f _build/html
```

The web page will be updated in a few minutes.

## How to use Sphinx

### Tool Package Installation

```none
pip install sphinx~=7.0 
pip install sphinx-book-theme
```

### Gererate Function Documents

At the repository root:

```none
mkdir docs
sphinx-apidoc --output-dir docs molass --separate
```

### Edit Manually



### Deployment

At docs:

```none
make html
ghp-import -n -p -f _build/html
```

The web page will be updated in a few minutes.