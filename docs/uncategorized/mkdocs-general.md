# Mkdocs and Mkdocs-Material

MkDocs is a static site generator suitable for building project documentation. This page is some notes covering the important bits for me. Mkdocs-Material is an addon that adds some flare to make the site look pretty. 

## Installing Material for Mkdocs

mkdocs-material is a python module installed using pip to install the package and all dependancies. The examples below are accurate for a Fedora based Linux development environment. 

```sh linenums="1"
export REPO_ROOT=/path/to/my/repo
cd $REPO_ROOT
python -V                 # confirm version is >= 3.x
pip -V                    # confirm version is >= 21.x
python -m venv venv       # set up python virt. environment.
source venv/bin/activate
pip install mkdocs-material 
```


## Creating a New Mkdocs Site

To get started, follow the code steps below to create a basic mkdocs site where you can start to publish documents: 

```sh linenums="1"
cd $REPO_ROOT
mkdocs new .
```

You will now have the following objects: 

* mkdocs.yml     => this is the configuration file. 
* docs/index.md  => example default site page. Think of this as like an index.html page. 

## Updating Mkdocs Configuration

All the site configuration is done inside the mkdocs.yml file. Full details can be read on the mkdocs site, but below is a common setup I am using. Replace your mkdocs.yml with the contents shown below. Update as necessary to suit your needs:

```yaml
site_name: My Site Name
theme:
  name: material
  features:
    - navigation.tabs
    - navigation.tabs.sticky
    - navigation.sections
    - navigation.expand
    - navigation.path
    - navigation.top
    - toc.integrate
    - navigation.top
    - navigation.tracking
    - search.suggest
    - search.highlight
    - content.tabs.link
    - content.code.annotation
    - content.code.annotate
    - content.code.copy
  language: en
  palette:
    - scheme: default
      toggle:
        icon: material/toggle-switch-off-outline
        name: Switch to dark mode
      primary: deep orange
      accent: purple
    - scheme: slate
      toggle: 
        icon: material/toggle-switch
        name: Switch to light mode
      primary: deep orange
      accent: lime 
  font:
    text: Roboto

markdown_extensions:
  - pymdownx.highlight:
      anchor_linenums: true
      line_spans: __span
      pygments_lang_class: true
  - pymdownx.inlinehilite
  - pymdownx.snippets
  - pymdownx.superfences
  - admonition
  - pymdownx.arithmatex:
      generic: true
  - footnotes
  - pymdownx.details
  - pymdownx.mark
  - attr_list
  - pymdownx.emoji:
      emoji_index: !!python/name:materialx.emoji.twemoji
      emoji_generator: !!python/name:materialx.emoji.to_svg

copyright: |
  &copy; 2023 <a href="https://me" target="_blank" rel="noopener">Somebody</a>

extra:
  consent:
    title: Cookie consent
    description: >- 
      We use cookies to recognize your repeated visits and preferences, as well
      as to measure the effectiveness of our documentation and whether users
      find what they're searching for. With your consent, you're helping us to
      make our documentation better.
  consent:
    actions:
      - accept
```

## Serving Mkdocs Locally

When developing the site locally, you will want to run a webserver so you can use a web browser to confirm your changes. Below is how to run a local webserver for your mkdocs site: 

```sh linenums="1"
cd $REPO_ROOT             # (1)
source venv/bin/activate  # (2)
mkdocs serve
```

1.  :man_raising_hand: replace $REPO_ROOT with the path to the root of your repo. e.g. /home/me/doc_repo
2.  :man_raising_hand: only needed if you are running python in a virtual environment.



## Build Final Site

When you are happy with your development efforts, you can now build your site to it's final static pages. Below is an example:

```sh
cd $REPO_ROOT
mkdocs build
```

You should now have a new folder in your $REPO_ROOT called "site". All the files in the "site" folder are your new website. Simply copy/upload those files inside the "site" folder to wherever you are hosting your website. 



## How to add your own content

Now that you have your initial site working, you will want to add your own pages. Below are some points to get you started: 

* All your documents live under the $REPO_ROOT/docs directory.
* Creating subfolders, translate to new tabs on your website navigation page.
* All docuements should be written in markdown format.
* The "header" for each document (e.g. the row that starts with '#') becomes the navigation link text.
* The document file_name is irrelevant and not shown on the website. 
* Update the $REPO_ROOT/docs/index.md to customize what your web page will look like.


## Formatting examples

Below are some snippets of commonly used formatting techniques I use. All of these and more can be found at the Material for Mkdocs reference below. 

### Code block

Below is a block of fake code to test stuff: 

```py linenums="1" title="example_python_script.py"
import os
import json

def golf():
    a = 3 * 4
    return a

def main():
    result = golf()
    print(result)

if name == '__main__'
    main()
```

This is the end of the example.


### Admonition

Below is an example of a note type block (a.k.a. Admonition)

!!! note

    This is an example of a note, but there are other types of callouts. 
    See the following URL for examples:  https://squidfunk.github.io/mkdocs-material/reference/admonitions/#supported-types


### Buttons

Here is an example of a button that points to a link: 

[Go to Google](https://google.com){ .md-button .md-button--primary }


### Tables

Here is an example of a table with center alignment: 

| Method      | Description                          |
| :---------: | :----------------------------------: |
| `GET`       | :material-check:     Fetch resource  |
| `PUT`       | :material-check-all: Update resource |
| `DELETE`    | :material-close:     Delete resource |

[More Table Examples](https://squidfunk.github.io/mkdocs-material/reference/data-tables/#center){ .md-button .md-button--primary }





## Reference

1. [Mkdocs home: this site is built on mkdocs](https://www.mkdocs.org/)

1. [Material for Mkdocs home: make mkdocs pretty](https://squidfunk.github.io/mkdocs-material/)

