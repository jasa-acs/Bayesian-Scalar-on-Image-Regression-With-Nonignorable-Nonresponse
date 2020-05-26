# Bayesian Scalar on Image Regression With Nonignorable Nonresponse

# Author Contributions Checklist Form

## Data

### Abstract

The dataset we use comes from Phase 1 of the Alzheimer’s disease Neuroimaging Initiative (ADNI) --- the ADNI1, including the T1-weighted magnetic resonance image and demographic/clinical information like age, gender, race, education, APOE4, marriage status, disease status, and Rey auditory verbal learning test (RAVLT) scores at different time points for each subject. There are 802 subjects with 223 normal controls (NC), 391 MCI patients, and 188 AD patients. We preprocess the T1 images according to steps in Section 5 of the paper. 





### Availability 

Data obtained from the Alzheimer’s Disease Neuroimaging Initiative (ADNI) database are publicly available at adni.loni.usc.edu. 



### Description 

The dataset can be downloaded from adni.loni.usc.edu. We confirm that the authors have legitimate access to the dataset. After registering an account, T1 imaging dataset can be downloaded in .img/.hdr or .nii.gz format according to https://ida.loni.usc.edu/services/Menu/PDF/IDA_User_Manual.pdf, where the “original data” of “T1” for “ADNI Screening” and “ADNI1 baseline” is selected to be downloaded at the “Advanced search”. Demographic/clinical information can be downloaded in .tar.gz format and installed as an R package according to https://adni.loni.usc.edu/wp-content/uploads/2012/08/instruction-ADNIMERGE-packages.pdf. 



## Code

### Abstract

The computer program that conducts statistical inference for the proposed Bayesian scalar on image regression with non-ignorable non-response is written in the R language (R version 3.6.1, https://www.r-project.org/) with the aid of RcppArmadillo package (package version 0.9.700.2.0, see, Eddelbuettel and Sanderson, 2014) for speeding up loops in the code, and the main functions are summarized in the R package “BSOINN” (package version 1.0). The package contains three functions, BSOIFull(), BSOIIN(), and BSOINN(), which conduct Bayesian inference for a scalar on image regression with fully observed response, ignorable non-response, and non-ignorable non-response, respectively. 

Reference:
Eddelbuettel, D. and Sanderson, C. (2014). Rcpparmadillo: Accelerating r with highperformance c++ linear algebra. Computational Statistics & Data Analysis, 71:1054-1063.


### Description

The main functions, including BSOIFull(), BSOIIN() and BSOINN(), are summarized in the R package “BSOINN”, and their usage is demonstrated in the demo codes for the simulation study and the real data analysis. The R package and the demo codes can be found in the github page, https://github.com/BIG-S2/BSOINN. 

Please note that the brain images are too large to be included in the package or in the folder of demo code for the real data analysis. We therefore require the eigenscores from the functional principal component analysis (FPCA) on the images as inputs for the functions in the “BSOINN” package. The  FPCA in the paper can be implemented using matlab or the “fast.svd” function in the R ‘corpcor’ package (package version 1.6.9), which is demonstrated in the demo code for the simulation study. We also include a separate demo code to illustrate how to read imaging data and use the “fast.svd” function to perform FPCA on the images. 






## Instructions for Use

The demo codes for the simulation study and the real data analysis can be implemented to reproduce the results given in the paper. We evaluate the approximate runtimes for the demo codes on a computer with a 64-bit six-core 2.2 GHz Intel Core i7-8750H processor with 16 GB of main memory.

The demo code for the simulation study is the main program for reproducing the results in the simulations study. The estimation results in the simulation study can be obtained by setting the number of replication as 100 (N_REPS = 100) and sample size as 100, 500 or 1000 (N_subj = 1000) in the demo code of parameter estimation for the simulation study, and the results in Part 1 of Simulation 2 can be achieved through excluding the instrumental variable. The approximate runtime for the demo code is 85 seconds for one replication. The prediction results in the simulation study can be obtained using the demo code of out-of-sample prediction for the simulation study.  The approximate runtime for the demo code is 25 seconds for one replication. 

The demo code for the real data analysis is the main program for reproducing the results in the real data analysis. The estimation results in analyzing the ADNI data set can be obtained by implementing the demo code of parameter estimation for the real data analysis, and the results in Table 6 can be obtained by removing the instrumental variable, education level, from the analysis. The approximate runtime for the demo code is 45 seconds.  The prediction results in the real study analysis can be obtained using the demo code of out-of-sample prediction for the real data analysis. The approximate runtime for the demo code is 10 seconds for one random partition analysis.


