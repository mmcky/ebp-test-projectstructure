# File

The `file` listing approach in `_toc.yml`

## jupyterbook

The following `_toc.yml` produces:

```yaml
- file: intro
  numbered: true
- file: chapter1
- file: chapter2
  title: Chapter2 Alternate Title
- file: chapter3
  sections:
    - file: chapter3section2
- file: references
```

with [html](https://htmlpreview.github.io/?https://github.com/mmcky/ebp-test-projectstructure/blob/master/files/jupyterbook/_build/html/intro.html) and [pdf](https://github.com/mmcky/ebp-test-projectstructure/blob/master/files/jupyterbook/_build/latex/book.pdf).

**Sphinx AST:**

The `toctree` is added to the end of the `intro` document that contains `frontmatter`

```xml
<document source="/Users/matthewmckay/repos-collab/ebp-test-projectstructure/files/jupyterbook/intro.md">
    <section ids="book-title" names="book\ title">
        <title>
            Book Title
        <paragraph>
            This is the frontmatter
        <compound classes="toctree-wrapper">
            <toctree caption="True" entries="(None,\ 'chapter1') ('Chapter2\ Alternate\ Title',\ 'chapter2') (None,\ 'chapter3') (None,\ 'references')" glob="False" hidden="True" includefiles="chapter1 chapter2 chapter3 references" includehidden="False" maxdepth="-1" numbered="999" parent="intro" rawentries="Chapter2\ Alternate\ Title" titlesonly="True">
```

the `latex` is parsed

```latex
\title{File List (jupyterbook)}
\date{Aug 13, 2020}
\release{}
\author{EBP}
\newcommand{\sphinxlogo}{\vbox{}}
\renewcommand{\releasename}{}
\makeindex
\begin{document}

\pagestyle{empty}
\sphinxmaketitle
\pagestyle{plain}
\sphinxtableofcontents
\pagestyle{normal}
\phantomsection\label{\detokenize{intro::doc}}

This is the frontmatter

\chapter{Chapter 1}
\label{\detokenize{chapter1:chapter-1}}\label{\detokenize{chapter1::doc}}
This is the first Chapter

\section{Chapter1,Section1}
\label{\detokenize{chapter1:chapter1-section1}}
This is the first sectioni in chapter 1
```


## bookpattern

This could be a common build pattern for books that wish to just write `chapters`.

The following `_toc.yml` produces:

```yaml
- file: chapter1
  numbered: true
- file: chapter2
  title: Chapter2 Alternate Title
- file: chapter3
  sections:
    - file: chapter3section2
- file: references
```

with [html](https://htmlpreview.github.io/?https://github.com/mmcky/ebp-test-projectstructure/blob/master/files/bookpattern/_build/html/intro.html) and [pdf](https://github.com/mmcky/ebp-test-projectstructure/blob/master/files/bookpattern/_build/latex/book.pdf).

**Sphinx AST:**

A `toctree` is added to the end of the `chapter1` document which causes issues with `numbering`.

```xml
<document source="/Users/matthewmckay/repos-collab/ebp-test-projectstructure/files/bookpattern/chapter1.md">
    <section ids="chapter-1" names="chapter\ 1">
        <title>
            Chapter 1
        <paragraph>
            This is the first Chapter
        <section ids="chapter1-section1" names="chapter1,section1">
            <title>
                Chapter1,Section1
            <paragraph>
                This is the first sectioni in chapter 1
        <section ids="chapter1-section2" names="chapter1,section2">
            <title>
                Chapter1,Section2
            <paragraph>
                This is the second section in chapter 1
            <section ids="chapter1-section2-subsection1" names="chapter1,section2,subsection1">
                <title>
                    Chapter1,Section2,SubSection1
                <paragraph>
                    This is a subsection in Section 2 of Chapter 1
        <section ids="chapter1-section3" names="chapter1,\ section3">
            <title>
                Chapter1, Section3
            <paragraph>
                This is section 3 of Chapter 1
            <compound classes="toctree-wrapper">
                <toctree caption="True" entries="('Chapter2\ Alternate\ Title',\ 'chapter2') (None,\ 'chapter3') (None,\ 'references')" glob="False" hidden="True" includefiles="chapter2 chapter3 references" includehidden="False" maxdepth="-1" numbered="999" parent="chapter1" rawentries="Chapter2\ Alternate\ Title" titlesonly="True">
```

with the `latex` output:

```latex
\title{File Listing (bookpattern)}
\date{Aug 13, 2020}
\release{}
\author{EBP}
\newcommand{\sphinxlogo}{\vbox{}}
\renewcommand{\releasename}{}
\makeindex
\begin{document}

\pagestyle{empty}
\sphinxmaketitle
\pagestyle{plain}
\sphinxtableofcontents
\pagestyle{normal}
\phantomsection\label{\detokenize{chapter1::doc}}

This is the first Chapter

\chapter{Chapter1,Section1}
\label{\detokenize{chapter1:chapter1-section1}}
This is the first sectioni in chapter 1

\chapter{Chapter1,Section2}
\label{\detokenize{chapter1:chapter1-section2}}
This is the second section in chapter 1

...
```

**Comments:**

1. the `toctree` element appears to be part of `chapter1-section3` in the `AST` structure.

