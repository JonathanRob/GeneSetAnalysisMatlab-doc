# Human metabolic gene set collections

GSAM enables the generation of gene set collections (GSCs) from genome-scale metabolic models (GEMs) using the `extractMetabliteGSC` or `extractSubsystemGSC` functions.

For convenience, GSCs extracted from the latest version of the human genome-scale metabolic model [**Human-GEM**](https://github.com/SysBioChalmers/Human-GEM) are hosted on the [GSAM GitHub repository](https://github.com/JonathanRob/GeneSetAnalysisMatlab/tree/master/gsc) as `.gmt` files. This facilitates the use of Human-GEM-derived GSCs for use in other packages (e.g., [Piano](https://bioconductor.org/packages/release/bioc/html/piano.html) or [GSEA](https://www.gsea-msigdb.org/gsea/index.jsp)) without requiring GSAM or MATLAB.

The names of these GSCs indicate the version of Human-GEM from which they were extracted, as well as the format of the gene IDs (Ensembl ID or Gene Symbol).

## Metabolite GSC

The metabolite `.gmt` files contain metabolite-gene associations extracted from Human-GEM, where each metabolite is a gene set. Each metabolite is associated with the genes encoding the reaction(s) involving that metabolite. Such a metabolite GSC is employed in the [reporter metabolite](https://www.pnas.org/content/102/8/2685) approach.

## Subsystem GSC

The subsystem `.gmt` files contain subsystem-gene associations extracted from Human-GEM, where each subsystem (metabolic pathway) is a gene set. Each subsystem is associated with the genes encoding the reaction(s) comprising that subsystem.


