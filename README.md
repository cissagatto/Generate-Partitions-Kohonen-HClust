# Generate Hybrid Partitions with Kohonen and HClust
This code is part of my PhD at PPG-CC/DC/UFSCar. The aim is generate hybrid partitions for multilabel classification using Kohonen to modeling the label correlations, and HClust to partitioning the label space (accordingly with the modeled label correlations).

The figure bellow shows the fluxogram for this code:

## Scripts
This source code consists of an R project for R Studio and the following R scripts:

1. libraries.R
2. utils.R
3. processKohonen.R
4. run.R
5. partitionsKohonen.R

## Preparing your experiment

### Step-1
This code is executed in X-fold cross-validation (mandatory!). First, you have to obtain the X-fold cross-validation files using this code: https://github.com/cissagatto/CrossValidationMultiLabel (all the instructions to use the code are in the Github). After that, put the results generated in the *datasets* folder in this project. The folder structure generated by the code *CrossValidationMultilabel* is used here.

<img src="https://github.com/cissagatto/Generate-Partitions-Kohonen/blob/main/folder_structure_cv.png" width="500">

### Step-2
Place a copy of this code in _"C:/Users/[username]/Generate-Partitions-Kohonen"_ or _"/home/username/Generate-Partitions-Kohonen_. Our files are configured to obtain the paths of the folders from the root. You can change this in the code if you want.

### Step-3
A file called *datasets-hpmlk.csv* must be in the root project folder. This file is used to read information about the datasets and they are used in the code. All 74 datasets available in cometa (https://cometa.ujaen.es/) are in this file. If you want to use another dataset, please, add the following information about the dataset in the file:

*Id, Name, Domain, Labels, Instances, Attributes, Inputs, Labelsets, Single, Max freq, Card, Dens, MeanIR, Scumble, TCS, AttStart, AttEnd, LabelStart, LabelEnd, xn, yn, gridn*

The _"Id"_ of the dataset is a mandatory parameter in the command line to run all code. The fields are used in a lot of internal functions. Please, make sure that this information is available before running the code. 

### Step-4
Confirms if the folder UTILS contains the following files: Clus.jar, R_csv_2_arff.jar, and weka.jar. Without these jars, the code not runs. Also, confirms if the folder _libs_ is present with the jars: Clus.jar, commons-math-1.0.jar, jgap.jar and weka.jar.

NOTE: Please, pay attention to the datasets file names and the names in the CSV file. They must be the same, on the contrary, an error may occur.

## GPKH Folder Strucutre

<img src="https://github.com/cissagatto/Generate-Partitions-Kohonen/blob/main/folder_strcutre_gpkh.png" width="500">

## Software Requirements
This code was develop in *RStudio Version 1.4.1106 © 2009-2021 RStudio, PBC "Tiger Daylily" (2389bc24, 2021-02-11) for Ubuntu Bionic Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) QtWebEngine/5.12.8 Chrome/69.0.3497.128 Safari/537.36*. The R Language version was: *R version 4.1.0 (2021-05-18) -- "Camp Pontanezen" Copyright (C) 2021 The R Foundation for Statistical Computing Platform: x86_64-pc-linux-gnu (64-bit)*. Please make sure all the dependencies are installed (verify libraries.R). This code does not provide any installation of the packages.

## Hardware Requirements
This code may or may not be executed in parallel, however, it is highly recommended that you run it in parallel. The number of cores can be configured via the command line (_number_cores_). If *number_cores = 1* the code will run sequentially. In our experiments, we used ten cores. For reproducibility, we recommend that you also use ten cores.

## Results
The results stored in the folder _OUTPUT_ it will be used in the next phase: Best-Partition-Silhoute or Best-Partition-MacroF1. The result for a dataset must be put in the folder _PARTITIONS_.

<img src="https://github.com/cissagatto/Generate-Partitions-Kohonen/blob/main/results_structure_gpk.png" width="500">

## RUN
To run the code, open the terminal, enter */home/[username]/Generate-Partitions-Kohonen/scripts/* folder, and type:

```
Rscript partitionsKohonen.R [number_dataset] [number_cores] [number_folds] [name_folder_results]
```

Where:

_number_dataset_ is the dataset number in the datasets.csv file

_number_cores_ is the total cores you want to use in parallel execution.

_number_folds_ is the number of folds you want for cross-validation

_name_folders_results is the name of the folder to save the results

All parameters are mandatory. Example:

```
Rscript partitionsKohonen.R 17 5 10 /dev/shm/results/flags
```

This will execute the code for the dataset number 17 in the _dataset-hpmlk.csv_, with 5 cores, 10 folds and the process will be store in the _/dev/shm/results/flags_. This code automatically saves the results process in this folder to other folder in the root folder of the project. This is necessary to run faster.


## Acknowledgment
This study is financed in part by the Coordenação de Aperfeiçoamento de Pessoal de Nível Superior - Brasil (CAPES) - Finance Code 001

## Links

[Post-Graduate Program in Computer Science](http://ppgcc.dc.ufscar.br/pt-br)

[Biomal](http://www.biomal.ufscar.br/)

[Computer Department](https://site.dc.ufscar.br/)

[CAPES](https://www.gov.br/capes/pt-br)

[Embarcados](https://www.embarcados.com.br/author/cissa/)

[Linkedin](https://www.linkedin.com/in/elainececiliagatto/)

[Linkedin](https://www.linkedin.com/company/27241216)

[Instagram](https://www.instagram.com/professoracissa/)

[Facebook](https://www.facebook.com/ProfessoraCissa/)

[Twitter](https://twitter.com/professoracissa)

# Thanks
