# Parts & Chapter

The `parts & chapters` listing approach in `_toc.yml`

## General Comments

This structure works pretty well when specifying books. The main issues are:

**General Issues:**

1.  on the `html` side numbering is restarted in each `part` as there are two separate `toctree` entries into
the Sphinx AST.
1. on the `latex` side Parts are ignored entirely but Chapter numbers are correct.

## jupyterbook

The following `_toc.yml`:

```yaml
- file: intro
  numbered: true

- part: part1
  chapters:
  - file: part1/chapter1
  - file: part1/chapter2

- part: part2
  chapters:
  - file: part2/chapter1
    sections:
      - file: part2/chapter1-section1
      - file: part2/chapter1-section2
```

produces [html](https://htmlpreview.github.io/?https://github.com/mmcky/ebp-test-projectstructure/blob/master/parts_chapters/jupyterbook/_build/html/intro.html) and [pdf](https://github.com/mmcky/ebp-test-projectstructure/blob/master/parts_chapters/jupyterbook/_build/latex/book.pdf).

**Sphinx AST:**

```xml
<document source="/Users/matthewmckay/repos-collab/ebp-test-projectstructure/parts_chapters/jupyterbook/intro.md">
    <section ids="intro" names="intro">
        <title>
            Intro
        <paragraph>
            This is the intro
        <compound classes="toctree-wrapper">
            <toctree caption="part1" entries="(None,\ 'part1/chapter1') (None,\ 'part1/chapter2')" glob="False" hidden="True" includefiles="part1/chapter1 part1/chapter2" includehidden="False" maxdepth="-1" numbered="999" parent="intro" rawcaption="part1" rawentries="" titlesonly="True">
        <compound classes="toctree-wrapper">
            <toctree caption="part2" entries="(None,\ 'part2/chapter1')" glob="False" hidden="True" includefiles="part2/chapter1" includehidden="False" maxdepth="-1" numbered="999" parent="intro" rawcaption="part2" rawentries="" titlesonly="True">
```

**Solutions:**

The current approach to building the `toc` elements in the `sphinx.ast` could to be updated to
be similar to how sphinx represents toctree elements using hierarchical toctree's. 

The [sphinx](https://github.com/mmcky/ebp-test-projectstructure/tree/master/sphinx) folder shows how `parts` and chapters can be structured and needs to be explored further.

```{note}

This sphinx example doesn't treat `parts` correctly in latex either:

```latex
\chapter{Part 1}
\label{\detokenize{part1:part-1}}\label{\detokenize{part1::doc}}
This is Part 1
```

```

## bookpattern

Most books would like `chapters` to be continuously numbered through `parts` structure

The following `_toc.yml` produces:

```yaml
- file: intro
  numbered: true

- part: part1
  chapters:
  - file: part1/chapter1
  - file: part1/chapter2

- part: part2
  chapters:
  - file: part2/chapter3
    sections:
      - file: part2/chapter3-section1
      - file: part2/chapter3-section2
```

with [html](https://htmlpreview.github.io/?https://github.com/mmcky/ebp-test-projectstructure/blob/master/parts_chapters/bookpattern/_build/html/intro.html) and [pdf](https://github.com/mmcky/ebp-test-projectstructure/blob/master/parts_chapters/bookpattern/_build/latex/book.pdf).

**Sphinx AST:**

A `toctree` is added to the end of the `chapter1` document which causes issues with `numbering`.

```xml
<document source="/Users/matthewmckay/repos-collab/ebp-test-projectstructure/parts_chapters/bookpattern/intro.md">
    <section ids="introduction" names="introduction">
        <title>
            Introduction
        <paragraph>
            This is the introduction
        <compound classes="toctree-wrapper">
            <toctree caption="part1" entries="(None,\ 'part1/chapter1') (None,\ 'part1/chapter2')" glob="False" hidden="True" includefiles="part1/chapter1 part1/chapter2" includehidden="False" maxdepth="-1" numbered="999" parent="intro" rawcaption="part1" rawentries="" titlesonly="True">
        <compound classes="toctree-wrapper">
            <toctree caption="part2" entries="(None,\ 'part2/chapter3')" glob="False" hidden="True" includefiles="part2/chapter3" includehidden="False" maxdepth="-1" numbered="999" parent="intro" rawcaption="part2" rawentries="" titlesonly="True">

```




