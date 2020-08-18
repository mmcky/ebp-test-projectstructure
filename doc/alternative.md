# Alternative Proposals

## Option 2: Add an Attribute

The current solution requires users to know there is a different between the first
`file` and remaining files in terms of how `sphinx` treats it internally.

We could add a `frontmatter` attribute requirement for the first `file` to be
treated as it is currently by default (as `frontmatter`)

````{panels}
Current
^^^^^^^
```yaml
- file: myintro

- file: firstchapter
- file: secondchapter
```
---
Proposed
^^^^^^^^
```yaml
- file: myintro
  frontmatter: true
- file: firstchapter
- file: secondchapter
```
````

## Option 3: Domain based Context for toc.yml

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
