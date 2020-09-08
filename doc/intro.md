# JupyterBook TOC Configuration

A test repository for various `jupyter-book` project configurations.

A [proposal](proposal.md) for changes is available

**Key Aims:**
1. Review `_toc.yml` for `jupyter-book` to enable a higher degree of harmony
   between `html` and `latex`

**Issues/Enhancements:**
1. [Jupyter Book Issue #809](https://github.com/executablebooks/jupyter-book/issues/809) showed
   numbers for `:numbered:` headings to be reset in each `part` for `html` which
   could be improved as an `ENH`
2. [Jupyter Book Issue #847](https://github.com/executablebooks/jupyter-book/issues/847) Parts are
   not transferred correctly through to the `LaTeX` writer. However the core writer
   does include support for [parts](https://github.com/sphinx-doc/sphinx/blob/9d48cb9798a1f2eea8a800689dde6648e260916f/sphinx/writers/latex.py#L394)
3. [Jupyter Book Issue #546](https://github.com/executablebooks/jupyter-book/issues/546)
4. [TOC relative levels discussion](https://github.com/executablebooks/meta/discussions/108)
5. [Odd Numbering with file & sections](https://github.com/executablebooks/jupyter-book/issues/767)

## LaTeX References

An excellent resource for LaTeX document structures

1. [LaTeX Document Structure](https://en.wikibooks.org/wiki/LaTeX/Document_Structure)

## Sphinx Project References

1. [Adding Parts to Sphinx](https://github.com/sphinx-doc/sphinx/issues/3357) which has a gist with a [prototype](https://gist.github.com/tk0miya/25bd52887adea5314fe15f1e3afc0949)