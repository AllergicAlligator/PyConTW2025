---
title: set up
---

# **SET UP**

## **<span style="font-size: 0.9em;">BASIC COMMANDS</span>**

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.

## **<span style="font-size: 0.9em;">THEMES</span>**

#### text

```yaml
theme:
    font: 
        text: Crimson Pro #mkdocs supports all google fonts!!
```

#### light and dark color palettes

```yaml

theme:
  palette: 

    # Palette toggle for light mode
    - scheme: default
      toggle:
        icon: material/brightness-7 
        name: Switch to dark mode

    # Palette toggle for dark mode
    - scheme: slate
      toggle:
        icon: material/brightness-4
        name: Switch to light mode

```

#### icon and logos

```yaml

icon:
    logo: material/robot-angry  

```
