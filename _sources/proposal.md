# Main Proposal

**Work In Progress**

This contains a proposal for `_toc.yml`. Given `LaTeX` is the more restrictive
medium -- this approach is based on support LaTeX in the _toc.yml structure and
relating it back to HTML in as flexible a way as possible.

## Introduce Categories

Introduce **optional** named sections in the `yml` such as `frontmatter`, `abstract`, `backmatter`). This
could extend the current `toctree` directive to include wrappers
for different content types for neater alignment with `LaTeX` and
`html` themes built to support `book` style qualities.

```yaml
# [optional] Front Matter
frontmatter:
  - file: preface
  - file: intro
# [required] Main Matter (Current Implementation
# but main file is a generated index file and first file
# is a standard chapter / document equivalent to other files)
- file: chapter1
- part: A Group of Chapters
  chapter:
    - file: chapter2
# [optional] Abstracts
abstract: Abstract Group
  - file: abstract1
# [optional] Back Matter
backmatter:
  - file: bibliography
```

### Implementation Ideas:

This essentially needs to be supported by `Sphinx` and could be organised by an updated
sphinx `toctree` that wraps documents inside appropriate document nodes providing
the contextual information needed for formatting more like traditional `book` structures:

1. `frontmatter`,
2. `backmatter`,
3. `abstract`

**Simple Chapter Structure:**

```rst
.. toctree::
   :frontmatter: preface
   :appendix: appendixA

   preface
   chapter1
   chapter2
   appendixA
```

would wrap the contents of the `preface` document within a `frontmatter` document node in the
 `Sphinx.AST` and `appendixA` within an `appendix` document node.

This additional information in the `AST` would provide the opportunity to adjust section numbering based
on these structural positions in a document.

**Parts/Chapter Document Structure:**

To implement `parts and chapter` structure would include

```rst
.. toctree::
  :frontmatter: preface
  :appendix: appendixA

  preface
  part1
  part2
  appendixA
```

`part1` would have its own toctree and `title` in `part1.md` document

```rst
.. toctree::

  chapter1
  chapter2
```

`part2` would have its own toctree and `title` in `part2.md` document

```rst
.. toctree::

   chapter3
   chapter4
```

## Alternative Options

Use a list approach that would
enable multiple files to be classified as `frontmatter`.
This could be useful when building books with `preface` and
secondary `frontmatter` sections.

````{panels}
Current
^^^^^^^
```yaml
- file: myintro

- part: My first part
  chapters:
  - file: part1_chapter1
  - file: part1_chapter2
- part: My second part
  chapters:
  - file: part2_chapter1
```
---
Proposed
^^^^^^^^
```yaml
- front:
  - file: intro.md

- part: My first part
  chapters:
  - file: part1_chapter1
  - file: part1_chapter2
- part: My second part
  chapters:
  - file: part2_chapter1
```
````

## Sphinx `toctree` Resources:

1. [sphinx/directives/other.py](https://github.com/mmcky/sphinx/blob/3.x/sphinx/directives/other.py) contains `toctree` directive definitions
2. [sphinx/environment/collectors/toctree.py](https://github.com/mmcky/sphinx/blob/3.x/sphinx/environment/collectors/toctree.py)
3. [sphinx/environment/adaptors/toctree.py](https://github.com/mmcky/sphinx/blob/3.x/sphinx/environment/adapters/toctree.py) contains 

## Other Ideas:

For `html` perhaps we should write an inliner for `toctree` to get the numbering correct. A single `toc` may aslo be a useful way to generate  `sitemap.xml`?

