# About Mkdocs

# Manager
* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.

# Setting Themes
```angular2html
project
    docs
    mkdocs.yml # the are the configuration file
```
## mkdocs.yml
```angular2html
site_name: title
theme:
  name: material
nav:
  ...
```