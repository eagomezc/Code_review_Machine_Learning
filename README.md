# Machine Learning models to predict response to DMARD treatment in rheumatoid arthritis patients using lipid mediator profiles

# Overview: 

This repository contains the **R scripts** used to create the machine learning models used to predict the response to DMARD treatment in rheumatoid arthritis patients using lipid mediator profiles and clinical scores.

These scripts were also used for the evaluation step of the models (using a test cohort) and the Receiver Operating Characteristic (ROC) curve. 

**NOTE:** **MetaboAnalyst web-based application** (more information [here](https://www.metaboanalyst.ca//faces/ModuleView.xhtml)) (version 4.0) was used to perform some statistical analyses such as partial least squares-discrimination analysis (PLS-DA), orthagonal partial least squares-discrimination analysis (oPLS-DA), variance importance in projection analysis (VIP).

# System Requirements: 

## Hardware requirements: 

All the scripts and software used for the **9 months report** were run in a standard computer (RAM: 8GB, CP$: 4 cores, 3.60 GHZ/core) with a maximum runtime of approx. 20 minutes for the more demanding script ([**1_classyfire_(SVM_models).R**](https://github.com/eagomezc/2020_Biomarkers_identification_ML_and_RA/blob/master/b_R_Scripts/1_classyfire_(SVM_models).R)). 

A computer with lower specs (e.g. 2GB of RAM) will work but some scripts will take longer to run. 

## System requirements:

All the R scripts were created and used on **Windows 10**:

**R version**: 3.5.1 

**R Studio version**: 1.1.456

The scripts should be compatible with Mac and Linux operating systems. 

For installing R and R Studio, follows the installation instructions [here](https://www.stats.bris.ac.uk/R/) and [here](https://www.rstudio.com/products/rstudio/download/). With typical installation times on a normal computer not exceeding 3h.

## Required R packages (libraries): 

The required packages to run all the scripts contained in this repository can be installed as follow: 

The last version of classyfire (0.1-2) package can be found [here](https://cran.r-project.org/src/contrib/Archive/classyfire/)

```
# Packages classyfire:
# After download the last version of classyfire (0.1-2), you can install the package as follow, specifying the directory of the zip: 
install.packages("C:pathToDirectory/classyfire_0.1-2.tar.gz", 
                  repos = NULL, 
                  type = "source")
                  
# Packages ggplot2, pROC, randomForest and caret:
install.packages(c('ggplot2', 'pROC', 'randomForest', 'caret'))

# Package edgeR from Bioconductor:
if (!requireNamespace("BiocManager", quietly = TRUE))
    install.packages("BiocManager")
BiocManager::install("edgeR")
```
# Content: 

The repository contains three folders: 

## [a_Data](https://github.com/eagomezc/2020_Biomarkers_identification_ML_and_RA/tree/master/a_Data)

This folder contains, separated by subfolders, the different file formats that has to be used to run the different R scripts. Each subfolder has the name of the specific script where they can be used, in addition to the number of the script, to make more clear what file is used in what folder. At the moment to download this repository in a local computer, it's important to remember that all the **input pathways in the scripts has to be changed**.

The subfolders are:

**1_classyfire_(SVM_models)**: Contains a tab-delimited table with the training dataset (Patients as columns and Lipid mediators as rows) and a tab-delimited table with the evaluation dataset (Patients as columns and Lipid mediators as rows).

**2_randomForest_(RF_models)**: Contains a tab-delimited table with the training dataset (Patients as rows and Lipid mediators as columns) and a tab-delimited table with the evaluation dataset (Patients as rows and Lipid mediators as columns).

More details about the format of this files can be seen in the comments of each script. 

## [b_R_Scripts](https://github.com/eagomezc/2020_Biomarkers_identification_ML_and_RA/tree/master/b_R_Scripts)

This folder contains the scripts used to create the support vector machine and random forest prediction models, in addition to the script used to run differential gene expression analysis of interested genes in the lipid mediator pathways. 

The scripts are: 

**1_classyfire_(SVM_models).R**: Using a training dataset, this script creates the machine learning models used to predict the response to DMARD treatment in rheumatoid arthritis patient. The script works with the package **classyfire** that uses support vector machine and bootstrapping for the model creation. It also uses the a test cohort to validate the models and estimate the MCC value. 

**2_randomForest_(RF_models).R**: Using a training dataset, this script creates the machine learning models used to predict the response to DMARD treatment in rheumatoid arthritis patient. The script works with the package **randomForest** that uses random forests and bootstrapping for the model creation. Besides that, estimate the **importance** of each lipid mediator in the improvement of the model's accuracy. Finally, it also uses the test cohort to evaluate the models and estimate the area under the receiver operating characteristic curves (AUC). 

More details of how the scripts works can be seen in the comments of each script. 

## [c_Expected_Output](https://github.com/eagomezc/2020_Biomarkers_identification_ML_and_RA/tree/master/c_Expected_Output)

This folder contains, separated by subfolders, the different expected outputs that can be obtain after running the R scripts. Each subfolder has the name of the specific script that generates it, in addition to the number of the script, to make more clear what file is the result of what script. At the moment to download this repository in a local computer, it's important to remember that all the **output pathways in the scripts has to be changed**.

The subfolders are:

**1_classyfire_(SVM_models)**: The expected results from this script are a tab-delimited file containing a table with the model's names, their accuracy percentages and their MCC values after validation with the test cohort; and the different models saved as an R object that can be used in the future.  

**2_randomForest_(RF_models)**: The expected results from this script are a tab-delimited file containing a table with the model's names, their accuracy percentages and their AUC values after evaluation with the test cohort; the different models saved as an R object that can be used in the future; and pdf files that contains plots associated with the performance of the models and the importance of each lipid mediator in the construction of the models. 

More details about how this files are generated can be seen in the comments of each script. 

 
 





