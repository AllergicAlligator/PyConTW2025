---
title: code blocks
---
# **CODE BLOCKS**

Code blocks are the heart of technical documentation. They transform abstract ideas into something readers can see, copy, and play with. In Material for MkDocs, code blocks aren’t just static boxes—they’re powerful, interactive teaching tools.

---

## PURPOSE

- Show readers **how things actually work** through examples  
- Make examples **copy-paste ready**, saving time and effort  
- 


## FEATURES

- **Syntax Highlighting** – Beautiful color-coded support for many languages  
- **Line Numbers** – Refer to specific lines easily  
- **Line Highlights** – Draw attention to what matters most  
- **Copy-to-Clipboard** – One-click copy, no messy drag selection  
- **Annotations** – Add inline explanations directly inside code  

---

## CONFIGURATION

In your `mkdocs.yml`, copy and paste this to ______:

```yaml
markdown_extensions:
  - pymdownx.highlight:
      anchor_linenums: true
      line_spans: __span
      pygments_lang_class: true
  - pymdownx.inlinehilite
  - pymdownx.snippets
  - pymdownx.superfences

```

## CODE... 

### to add line numbers

```py linenums="1"
def add(a, b):
    return a + b 
```


### to highlight inline code

```py


```

### to annotate