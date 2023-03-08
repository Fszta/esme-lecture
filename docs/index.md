# Git practical session - Introduction

For full documentation visit [mkdocs.org](https://www.mkdocs.org).

## What we have seen last week

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.


## Commands
* `git init` Initialize a git repository
* `git add <file_name>` add a file to staging area
* `git commit -m "an explicit message"` 
* `git push origin <branch_name>` 
* `git branch <branch_name>` create a new branch
* `git checkout <branch_name>` switch to branch `<branch_name>`
* `git checkout -b <branch_name` create and switch to new branch `<branch_name>`
## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.
