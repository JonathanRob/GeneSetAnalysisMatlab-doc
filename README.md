# GeneSetAnalysisMatlab-doc
Documentation for the [GeneSetAnalysisMatlab](https://github.com/JonathanRob/GeneSetAnalysisMatlab) package. This repository contains the scripts, figures, and static pages for the package documentation - not the package itself.

## View the documentation
Visit: <https://jonathanrob.github.io/GeneSetAnalysisMatlab-doc/>

## Building the site
This documentation site is built using [MkDocs](https://www.mkdocs.org/).

### Developer notes
When re-building the static pages, run the following command (while in the `mkdocs/` directory) to build the site into the top-level `docs/` directory on the Master branch:

```
mkdocs build -d ../docs
```

Otherwise, the default `mkdocs build` command will place it in a `site/` subdirectory, which is not recognized by GitHub pages.
