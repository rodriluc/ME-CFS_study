# ME/CFS INMEST Study
ME/CFS study from Swedish clinical cohort (INMEST) for single-level analyses and omics integration.

## Table of contents
* [General info](#general-info)
* [Dependencies](#dependencies)
* [Repo description](#repo-description)
* [Single-level analyses](#single-level-analyses)
* [Omics integration](#omics-integration)
* [Setup](#setup)

## General info
This project used multiple omics data:
- Plasma protein expression (Olink panels - NPX)
- Cell abundance (CyTOF - Grid)
- mRNA sequencing (VST counts)

Single-level analyses and omics-integration was performed in order to characterize this heterogeneous ME/CFS cohort and the effects of the INMEST treatment throughout the clinical trial.
	
## Dependencies
Project is created with:
* RStudio version: 3.6.0
* Python version: 2.7
* Unix/Linux

## Repo description
- ```DESeq2/``` contains script to convert Kallisto estimates and run DESeq2
- ```MOFA/``` contains script to train MOFA model and some functions to uncover sources of variation 

## Single-level analyses
### Grid
- Grid is a supervised learning algorithm based on t-SNE implementation. Using the manual classification of cells in CyTOF samples and then the automatic classification of cells in new samples through the use of machine learning techniques based on these manual classifications.
- To run Grid, install it using:
```
$ pip install cellgrid
```
### DESeq2 (Differential Gene Expression Analysis)
- The principles behind DESeq2 is described in [Love et al. (2014)](https://dx.doi.org/10.1186%2Fs13059-014-0550-8)
- Used Kallisto outputs (estimates) that were converted into read counts using ```tximport``` before running DESeq2 with ```deseq_run.R``` 

## Omics integration
### MOFA
- Multi-Omics Factor Analysis (MOFA) was used in this study in order to deconvolute the main sources of variation in the differents sets of data mentioned above. For more information, read their published Methods paper [Argelaguet et al. (2018)](https://www.embopress.org/doi/10.15252/msb.20178124). 
- MOFA is publicly accessible here: https://github.com/bioFAM/MOFA 
- Trained MOFA models (.hdf5 files) made available for this study for direct use in downstream analysis	
	
## Setup
To run this project, install it locally using devtools:

```
$ install.packages('devtools')
$ library(devtools)
$ install_github('rodriluc/ME-CFS_study')
$ library(ME-CFS_study)
```
