# Experimental

## Sphinx

This adds a basic `index` file to `_toc.yml` and then proceeds to use
the standard Sphinx `toctree` directives. 

This aligns closely with `sphinx` implement for LaTeX but `jupyter-book`
current issues a lot of warnings about missing content.

The `_toc.yml`:

```yaml
- file: index
```

with `index` containing:

````md
# Title of Project

```{toctree}
:numbered:
chapter1
chapter2
```
````