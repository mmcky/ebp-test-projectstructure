# Sphinx

This documents current Sphinx behaviour for `html` and `latex`
using the current implementation of `toctree`.

## Parts and Chapters

The following `toctree` is contained in `master_doc`

```rst
.. toctree::
   :maxdepth: 2
   :caption: Contents:
   :numbered:

   intro
   part1
   part2
```

with additional `toctree` directives in `part1.md` and `part2.md`

```rst
.. toctree::

    chapter1
    chapter2
```

produces the following [html](https://htmlpreview.github.io/?https://github.com/mmcky/ebp-test-projectstructure/blob/master/sphinx/parts_chapters/_build/html/index.html) and [pdf](https://github.com/mmcky/ebp-test-projectstructure/blob/master/sphinx/parts_chapters/_build/latex/partschapterssphinx.pdf) output

and `conf.py` contains `latex_toplevel_sectioning = "part"`

**Limitations:**

1. The `intro` document is interpreted as a part and doesn't seem to be any direct support for `frontmatter` in the current sphinx approach. This is despite the `top` header being marked as `level=1` using `====` rather than a `level=0` using double `====` markup.

**Important Notes:**

1. Section levels seem to be inferred at the **document level** -- so for each document the section level is set to the base level for the first header of the document regardless of any relative relationship outside of the document.
   
   this means that `chapter1.rst` with:

   ```rst
   Chapter 1
   =========

   Section1
   --------
   ```

   and a `chapter2.rst` with

   ```rst
   Chapter 2
   ---------

   Section 1
   ~~~~~~~~~
   ```

   have the same level for `Chapter 1` and `Chapter 2` (and `Sections`) in the output.