# Proposals

**Work In Progress**

This contains a proposal for `_toc.yml`. Given `LaTeX` is the more restrictive
medium -- this approach is based on support LaTeX in the _toc.yml structure and
relating it back to HTML in as flexible a way as possible.

## Option: Getting Current Solution to Work

To get knowledge of `frontmatter` demarcation:

````{panels}
Current
^^^^^^^
```yaml
- file: myintro

- part: My first part
  chapters:
  - file: part1_firstchapter
  - file: part1_secondchapter
- part: My second part
  chapters:
  - file: part2_firstchapter
```
---
Proposed
^^^^^^^^
```yaml
- front:
  - file: intro.md

- part: My first part
  chapters:
  - file: part1_firstchapter
  - file: part1_secondchapter
- part: My second part
  chapters:
  - file: part2_firstchapter
```
````

if we introduced a named item (i.e. `front`, `start`) for the first `element` we could know if
frontmatter exists or not. If it does **not** exist then we can assume all documents are chapters
as there is no frontmatter.

```yaml
# Front Matter (optional)
- front: 
  - file: preface
  - file: intro
# Main Matter Listing (Required)
- file: chapter1
- part: A Group of Chapters
  chapter:
    - file: chapter2
# abstract (optional)
- abstract: Abstract Group
  - file: abstract1
# Back Matter (optional)
- back:
  - file: 
```

we could also introduce optional markers for `abstract` and `backmatter`

## Option: Book

The `toc` is focused on content rather than front page of book 
which is contained in `_config.yml`. A useful reference for 
[latex book structure](https://en.wikibooks.org/wiki/LaTeX/Document_Structure#Book_structure)

```yaml
type: book
front:
  - file: preface.md

main:
- part: My first part
  chapters:
  - file: part1_firstchapter
  - file: part1_secondchapter
- part: My second part
  chapters:
  - file: part2_firstchapter

appendix:
  - file: appendixA.md

back: 
  - file: final_note.md
```

This would maps directly onto `LaTeX` structures for the `book` class.
