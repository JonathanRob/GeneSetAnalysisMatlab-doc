# Human metabolic gene set collections

GSAM enables the generation of gene set collections (GSCs) from genome-scale metabolic models (GEMs) using the `extractMetabliteGSC` or `extractSubsystemGSC` functions.

For convenience, GSCs extracted from the latest version of the human genome-scale metabolic model [**Human-GEM**](https://github.com/SysBioChalmers/Human-GEM) are hosted on the [GSAM GitHub repository](https://github.com/JonathanRob/GeneSetAnalysisMatlab/tree/master/gsc) as `.gmt` files. This facilitates the use of Human-GEM-derived GSCs for use in other packages (e.g., [Piano](https://bioconductor.org/packages/release/bioc/html/piano.html) or [GSEA](https://www.gsea-msigdb.org/gsea/index.jsp)) without requiring GSAM or MATLAB.

## Metabolite GSC

The [`Human-GEM-metabolites.gmt`](https://github.com/JonathanRob/GeneSetAnalysisMatlab/blob/master/gsc/Human-GEM-metabolites.gmt) file contains metabolite-gene associations extracted from Human-GEM, where each metabolite is a gene set. Each metabolite is associated with the genes encoding the reaction(s) involving that metabolite. Such a metabolite GSC is employed in the [reporter metabolite](https://www.pnas.org/content/102/8/2685) approach.

## Subsystem GSC

The [`Human-GEM-subsystems.gmt`](https://github.com/JonathanRob/GeneSetAnalysisMatlab/blob/master/gsc/Human-GEM-subsystems.gmt) file contains subsystem-gene associations extracted from Human-GEM, where each subsystem (metabolic pathway) is a gene set. Each subsystem is associated with the genes encoding the reaction(s) comprising that subsystem.


