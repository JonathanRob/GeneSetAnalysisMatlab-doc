# GSAM User Guide

The following examples demonstrate the use of the GSAM package for common analysis scenarios.

The data files used for these examples can be retrieved from the `data/` directory on the associated [documentation repository](https://github.com/JonathanRob/GeneSetAnalysisMatlab-doc/tree/master/data). If you wish you run these examples yourself, first download the files in that directory to your local machine and ensure that they are on your current MATLAB path.

## Example 1: Single GSA, Liver hepatocellular carcinoma

### Load the data and gene set collection file

Load the differential expression (DE) results for hepatocellular carcinoma (LIHC) (paired-normal tissue vs. primary tumor tissue).
```matlab
DEdata = readtable('DEresults_LIHC.txt');
```

Take a look at the table contents.
```matlab
head(DEdata)

% ans =
% 
%   8×4 table
% 
%          gene_IDs           gene_names       logFC         PValue  
%     ___________________    ____________    __________    __________
% 
%     {'ENSG00000000003'}    {'TSPAN6'  }      -0.26345      0.050906
%     {'ENSG00000000419'}    {'DPM1'    }    -0.0030857       0.97084
%     {'ENSG00000000457'}    {'SCYL3'   }      0.044663       0.63024
%     {'ENSG00000000460'}    {'C1orf112'}        0.7297    0.00021919
%     {'ENSG00000000938'}    {'FGR'     }       -1.2409    3.6644e-15
%     {'ENSG00000000971'}    {'CFH'     }      -0.72639    0.00069828
%     {'ENSG00000001036'}    {'FUCA2'   }      0.050749       0.66557
%     {'ENSG00000001084'}    {'GCLC'    }      -0.60349    1.1461e-06
```

Extract the data into individual variables
```matlab
geneIDs   = DEdata.gene_IDs;     % gene Ensembl IDs
geneNames = DEdata.gene_names;   % gene abbreviations
log2FC    = DEdata.logFC;        % log2(fold-changes) (normal vs. tumor)
pvals     = DEdata.PValue;       % fold-change significance (p-values)
```

Load the `KEGG_GSC.gmt` gene set collection (GSC) file using the `importGSC` function, and look at the first few lines to see how it's formatted.
```matlab
gsc = importGSC('KEGG_GSC.gmt');
gsc(1:5,:)

% ans =
%
%   5×2 cell array
%
%     {'KEGG-GLYCOLYSIS-GLUCONEOGENESIS'}    {'ACSS2'}
%     {'KEGG-GLYCOLYSIS-GLUCONEOGENESIS'}    {'GCK'  }
%     {'KEGG-GLYCOLYSIS-GLUCONEOGENESIS'}    {'PGK2' }
%     {'KEGG-GLYCOLYSIS-GLUCONEOGENESIS'}    {'PGK1' }
%     {'KEGG-GLYCOLYSIS-GLUCONEOGENESIS'}    {'PDHB' }
```

!!! note
	The `KEGG_custom_GSC.gmt` file used in this example is a modified version of the KEGG gene set collection retrieved from [MSigDB](http://software.broadinstitute.org/gsea/msigdb/genesets.jsp?collection=CP:KEGG), where all disease-related gene sets were removed.

Run the gene set analysis using the `geneSetAnalysis` function.
```matlab
GSAres = geneSetAnalysis(geneNames, pvals, log2FC, gsc, 'Wilcoxon', 50000, [20, Inf]);

% Gene set collection contains 146 gene sets and 4966 unique genes.
% Checking for empty gene sets... Removed 0 empty sets.
% Checking for duplicated rows in GSC... Removed 0 duplicated rows.
% Checking gene set sizes... Removed 27 gene sets not satisfying size limits.
% Final number of gene sets remaining: 119
% Subsetting data for mixed-directional calculations... Done.
% Calculating test statistic... Done.
% Calculating significance via gene shuffling... Done.
```
Here, we chose the Wilcoxon rank-sum test as the method for combining gene-level statistics, set the number of permutations for significance calculation to 50000, and excluded gene sets that contained less than 20 genes.

!!! important
	We used `geneNames` (instead of e.g. `geneIDs`) as input to the `geneSetAnalysis` function because gene names are used in the `gsc` that was loaded. It is important that the gene names or IDs in the gene list are of the same type as those used in the GSC file.

Generate a heatmap to visualize the GSA results using the `GSAheatmap` function.
```matlab
GSAheatmap(GSAres, true, 'pval', 0.01);
```
![LIHC GSA heatmap](img/GSAheatmap_LIHC.png)

Here, we chose to use the adjusted gene-set p-values (as specified with the second input `true`), and filtered the gene sets to only show those with an adjusted p-value ≤ 0.01 for at least one of the five directionality types.

!!! note
	For more information on the meaning and interpretation of the different p-value classes (distinct directional down and up, mixed-directinal down and up, and non-directional), see the [publication](https://www.ncbi.nlm.nih.gov/pubmed/23444143) where they were introduced. 












