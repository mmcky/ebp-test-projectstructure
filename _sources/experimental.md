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

the `xml`

```xml
<document source="/Users/matthewmckay/repos-collab/ebp-toc-testproject/experimental/sphinx/index.md">
    <section ids="title-of-project" names="title\ of\ project">
        <title>
            Title of Project
        <compound classes="toctree-wrapper">
            <toctree caption="True" entries="(None,\ 'chapter1') (None,\ 'chapter2')" glob="False" hidden="False" includefiles="chapter1 chapter2" includehidden="False" maxdepth="-1" numbered="999" parent="index" rawentries="" titlesonly="False">
```

Perhaps we could have a tagged item for `sphinx` based `toctree` projects

```yaml
sphinx:
  - file: index
```

```{note}
TODO: would need to figure out how to clear the `sphinx` warnings and recognise the
toctree listing in `index.md`
```