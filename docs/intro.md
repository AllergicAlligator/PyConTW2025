# Intro to MkDocs

## 1️⃣ What is MkDocs?

* MkDocs is a static site generator!
* MkDocs is written in Python!
* MkDocs converts .md to .html

## 2️⃣ What is Material for MkDocs?

* Material for MkDocs is a popular theme for MkDocs!
* Material for MkDocs provides cool features out of box!
* Material for MkDocs convert plain MkDocs websites to stylish doc websites1

!!! Tip
    Pay attention to **TWO** things:  
    :material-numeric-1-circle: Configuration.  
    :material-numeric-2-circle: Syntax 


### :material-numeric-1-circle: Code Blocks

* [Code Blocks](https://squidfunk.github.io/mkdocs-material/reference/code-blocks/)

```py title="prime.py"
def is_prime(n):
    if n < 2:
        return False
    for i in range(2, int(n ** 0.5) + 1):
        if n % i == 0:
            return False
    return True
```

```py linenums="1"
def is_prime(n):
    if n < 2:
        return False
    for i in range(2, int(n ** 0.5) + 1):
        if n % i == 0:
            return False
    return True
```

```py linenums="1" hl_lines="2-4"
def is_prime(n):
    if n < 2:
        return False
    for i in range(2, int(n ** 0.5) + 1):
        if n % i == 0:
            return False
    return True
```


### :material-numeric-2-circle: Icons

* [Icons, Emojis](https://squidfunk.github.io/mkdocs-material/reference/icons-emojis/)

### :material-numeric-3-circle: Admonitions

* [Admonitions](https://squidfunk.github.io/mkdocs-material/reference/admonitions/)

!!! Note
    This is important!

!!! tip
    Do this! Don't do that!

### :material-numeric-4-circle: Math

* [Math](https://squidfunk.github.io/mkdocs-material/reference/math/)


```
\[
\int_{0}^{\infty} \frac{x^{a-1}}{1+e^x} \, dx 
= \left(1 - 2^{1-a}\right) \Gamma(a) \zeta(a), \quad \Re(a) > 0
\]
```

\[
\int_{0}^{\infty} \frac{x^{a-1}}{1+e^x} \, dx 
= \left(1 - 2^{1-a}\right) \Gamma(a) \zeta(a), \quad \Re(a) > 0
\]


### :material-numeric-5-circle: Diagrams

* [Mermaid Live Editor](https://mermaid.live/edit)
* [Mermaid Tutorial](https://mermaid.js.org/intro/)


````
``` mermaid
graph LR
  A[Start] --> B{Error?};
  B -->|Yes| C[Hmm...];
  C --> D[Debug];
  D --> B;
  B ---->|No| E[Yay!];
```
````

``` mermaid
graph LR
  A[Start] --> B{Error?};
  B -->|Yes| C[Hmm...];
  C --> D[Debug];
  D --> B;
  B ---->|No| E[Yay!];
```

