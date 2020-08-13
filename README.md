# ebp-test-projectstructure

A testing ground to explore jupyter-book project structures for `toc` and the matching of `html` and `latex` outputs.

## Configurations

The top level config relates to the primary entry points for
constructing the `_toc.yml` file.

| Configuration Set   |      Description      |
|---------------------|:---------------------:|
| files               | Using the `files` based _toc.yml structure |
| parts_chapters      | Using the `parts` based _toc.yml structure |
| experimental        | Alternative Configuration approaches |

Within each configuration approach is a **reference** `jupyterbook` test
pattern along with some other **common** patterns that uers may
expect to work.

### Files

| Configuration Set   |      Description      |
|---------------------|:---------------------:|
| jupyterbook         |  Reference jupyterbook structure |
| bookpattern         |  A common book pattern |

Relevant [docs](https://jupyterbook.org/customize/toc.html#defining-chapters-and-parts-in-toc-yml)

### Parts and Chapters

| Configuration Set   |      Description      |
|---------------------|:---------------------:|
| jupyterbook         |  Reference jupyterbook structure |
| bookpattern         |  A common book pattern |

Relevant [docs](https://jupyterbook.org/customize/toc.html#defining-chapters-and-parts-in-toc-yml)

### Experimental

| Configuration Set   |      Description      |
|---------------------|:---------------------:|
| sphinx              |  Using sphinx `toctree` setup |

**Notes:**

The `sphinx` setup currently will trigger warnings that `content` is missing from the `_toc.yml`

```bash
WARNING: Found a content page that is not in _toc.yml: chapter1.md.
WARNING: Found a content page that is not in _toc.yml: chapter2.md.
```