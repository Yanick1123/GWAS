# GWAS

## GAPIT

Genome wide association studies (GWAS) is a widely used analysis that allow association between genetic markers and phenotypic traits. It is performed on populations of unrelated individuals and uses the linkage disequilibirum (LD) between nearby markers to unravel the genetic regions explaining complex traits in genomes.
GAPIT is a R package that includes different statistical models to perform GWAS. You first need to download R and R studio using the following links: https://www.r-project.org/ and https://posit.co/download/rstudio-desktop/
The R package **devtools** and **GAPIT3** need to be downloaded to run the analysis.

##### Testing parameters
To obtain trustable results, the user need to know its dataset. Different test analysis can be performed to understand which parameters works best for a given dataset. 
First, you can use different level of compression to group you individuals.
The first block of codes under **analysis1** uses no compression at all. Every individual is a group, making them entirely distinct. No population strucure is taken into account.
Then, you can group individual (**analysis2**) to see how it affect the outcome of the analysis. By default, the algorythm uses 10 but you can test different numbers. 
Finally, **analysis3** uses kinship or relatedness of the individuals in your populaition to group them. Taking into account kinship reduce the rate of false association because of the presence of sub-population in your global population.
The choice of an optinal number of principal components (PCA) is critical. It relates to the complexity of your dataset regarding the variation of your markers/phenotypes, variation in your dataset can be broken in dimension to increase its interpretability.

##### Performing GWAS

Different statistical model are implemented in the GAPIT package. Simpler model detect association directly between marker and phenotype but more complex ones includes different cofactor such as population structure or kinship. 
**analysis4** uses the multi-locus mixed-model (MLMM) where the associated marker are included as cofactors for marker test. This model alse include kinship and population structure.

**analysis5** uses the FarmCPU model that include a triming step to remove marker in high LD with an associated marker. Iterative steps are performed to only keep the marker with the highest association and removing the ones in LD until no markers can be removed. 
This model is computing intensive when lots of individuals are present.

## rMVP

This R package allow you to perform GWAS analysis and implement three statistical model: General Linear Model (GLM), Mixed Linear Model (MLM) and FarmCPU.
As GAPIT you can input your genotype dataset in a hapmap format and your phenotypes in a text file where the first column is your Taxa and following ones are your phenotypes. The first step is to import your data using the first block of codes ```MVP.Data```. Then is to run the GWAS analysis, the FarmCPU is used in this example.
rMVP produces descriptive figures such as a phenotype histogram, a SNP-density plot, a PCA plot (2D and 3D), a Manhattan circular plot and a rectangular one showing association of individual SNPs according to a LOD score and a QQ plot showing a graphical representation of the deviation of P-value from the null hypothesis.   



