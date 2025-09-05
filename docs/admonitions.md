---
title: admonitions
---
# ADMONITIONS

Admonitions are callout blocks that help you highlight important information.  
They break up long walls of text and draw attention to tips, warnings, notes, and more.  

---

## PURPOSE

- Highlight **critical details** (e.g., warnings, requirements, gotchas)  
- Provide **extra context** without interrupting the main flow  
- Improve **scannability** so readers can find what matters quickly  

---

## FEATURES

- **Multiple Types** – note, warning, info, tip, example, and more  
- **Theming** – styled automatically to match your site’s theme  
- **Collapsible** – expandable sections for extra details  
- **Custom Icons + Titles** – personalize callouts to your content  
- **Nested Content** – even code blocks and lists work inside  

---

## CONFIGURATION

Enable admonitions in your `mkdocs.yml`:

```yaml
markdown_extensions:
  - admonition
  - pymdownx.details
  - pymdownx.superfences
```
