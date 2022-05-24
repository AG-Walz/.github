
# Hey 👋!

If you are new to this repository then I would like to **"show"** you around. It is of importance to behave on our GitHub page. Below you can find a set up that you might need for the call of scripts that are in the `lib` in order to run some of the pipelines, so prepare this. This GitHub page consists of the different pipelines that can be used for various purposes in Arbeitsgruppe Walz. If there is a request for a new pipeline, then you can make the request in the pipeline channel in slack.

## Rules
* When using a repository, keep the folder structure as it is, meaning download the whole directory and dont move the content after downloading it
* In case of an error
  1. [RTFM](https://nl.wikipedia.org/wiki/Read_the_fucking_manual) 🤦: you are an adult, therefore, we assume that the bioinformaticians don't have to do this for you 🤷‍♀️
  2. Check if a similar issue already exists or has been closed before in the pipeline.
  3. *Google, google, google*: check if the error might occur from your side (a library which is not installed or maybe a non-existant file is used) ✅
  4. Notify your bioinformatician if there is a problem with the code (error, enhancements, etc) by making an issue in the respective repository and fill in the `bug` or `feature` report properly (I mean come on we are academics here... 😅). It is helpfull to also give an indication here how **urgent** your issue is ⏲️
* When something is not working, the matter is urgent, and the bioinformaticiancs are busy: `use another version`. We are doing over-hours as it is without the external pressure, however, you catch more flies with honey than vinegar 😇
* If there is information missing in the README, then please contribute to improve it teamwork makes the dream work 💪


## How to use - first timers edition
If this is the first time that you are running pipelines, it is of importance to check the content below. 

<details>
<summary>Installing R (and Rstudio)</summary>

\
The first thing (if you are here for the first time) is to install [R](https://cran.r-project.org/bin/windows/base/) and if you want to make you life easy [Rstudio](https://www.rstudio.com/). Please be kind to you friendly neighborhood bioinformatician (🕷️) and install everything in English 😅.
 
</details>

<details markdown="1">

<summary>Set up GitHub access code</summary>

## General purpose
Since copy-pasting is a **sin**, script stored in the library can be accessed in other scripts easily. 
Before this is possible, you need to make sure that your personalized access token and github email address are stored on your computer in an external file. 
How this is done, can be read below.

1. Generate a new token on [GitHub](https://github.com/settings/tokens/new)
2. Add a note, describing where you are using this token for (example; `GITHUB_PAT`)
3. Fill in the expiration date (example; `90 days` or `No expiration`)
4. Select the following scopes:

    - [x] **repo**
      - [x] repo:status
      - [x] repo_deployment
      - [x] public_repo
      - [x] repo:invite
      - [x] security_events
    - [ ] **workflow**
    - [ ] **write:packages**
      - [ ] read:packages
    - [ ] **delete:packages**
    - [ ] **admin:org**
      - [ ] write:org
      - [ ] read:org
    - [ ] **admin:public_key**
      - [ ] write:public_key
      - [ ] read:public_key
    - [X] **admin:repo_hook**
      - [X] write:repo_hook
      - [X] read:repo_hook
    - [ ] **admin:org_hook**
    - [ ] **gist**
    - [ ] **notifications**
    - [ ] **user**
      - [ ] read:user
      - [ ] user:email
      - [ ] user:follow
    - [X] **delete_repo**
    - [ ] **write:discussion**
      - [ ] read:discussion
    - [ ] **admin:enterprise**
      - [ ] manage_billing:enterprise
      - [ ] read:enterprise
    - [ ] **admin:gpg_key**
      - [ ] write:gpg_key
      - [ ] read:gpg_key

5. Click on `Generate token`
6. Copy-paste the code which is highlighted in the green bar (this is your personalized access code) 

### Problems

If you want to have an overview about with codes are made, or if you want to remove or generate one, then you can go to the [Personalized access tokens] (https://github.com/settings/tokens) overview
Additionally, a detailed overview is provided in the GitHub [documents](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).

</details>

<details markdown="1">

<summary>Create an Renviron file</summary>

### Mac and Linux
1. Open the terminal (Control + Option + Shift + T / Ctrl+Alt+T) and type `touch $HOME/.Renviron`
2. To open the file you just created in the terminal using `open $HOME/.Renviron`

3. Then write the following information:
```
GITHUB_MAIL=[github email] 
GITHUB_PAT=[personalized access code]
```

4. This will save and store the content in an `.Renviron` file which is located in the Home folder.
5. If you opened RStudio, then reopen this.
6. As a test, run `Sys.getenv('GITHUB_MAIL')` to access the variable in R.

### Windows

1. Press Windows+R to open the Run dialog box, and then type `powershell` in the text box and open this. 
2. Copy this code into powershell

```
Add-Content c:\Users\$env:USERNAME\Documents\.Renviron "GITHUB_MAIL=[github email]"
Add-Content c:\Users\$env:USERNAME\Documents\.Renviron "GITHUB_PAT=[personalized access code]"
```
3. This will save and store the content in an `.Renviron` file in the Documents folder. 
4. If you opened RStudio, then reopen this. 
5. As a test, run `Sys.getenv('GITHUB_MAIL')` to access the variable in R.

### Problems
If you dont see anything when you run `Sys.getenv('GITHUB_MAIL')`, then the first rule when something goes wrong is [RTFM](https://en.wikipedia.org/wiki/RTFM), however you can also try to bribe your favorite bioinformatician (maybe this works).

</details>

<details>
<summary>Using Bioconductor</summary>

 \
The next important thing is to install bioconductor, since you might need this to install some of the functionalities. You can do this bu runing the following piece of code:

```
install.packages("BiocManager")
```
Make sure that no errors occur, then you are ready to proceed
 
</details>
 
<details>
<summary>Checking libraries</summary>

\
The most important thing is to check if all of the different libraries are there. When you stumble accross the following piece of code pay close attention!

```
################################################################################
###                             Load libraries                               ###
################################################################################
## Load the libraries
necessaryLibs <- c("example")

## Load the necessary libraries()
invisible(lapply(necessaryLibs, library, character.only = T))
```

All of the libraries in the list of `necessaryLibs` needs to be installed since we need these packages for some of the functionalities to run. It could happen that you did not install a package yet, then you will get the following error:
```
library(example)
Error in library(example) : there is no package called ‘example’
```
To resolve this problem we have to install the packages, which we do using the following command
```install.packages("example")```
If that does not work, then we can use 
```BiocManager::install("example")```
Make sure that you put the qoutation marks around the package of interest.

If everything is installed, and `invisible(lapply(necessaryLibs, library, character.only = T))` runs without errors, then we can finally run the rest of the code
> Note, it could be that you see red text, and **error** is only an error when it is mentioned explicity!

</details>
 
---

<!--
# How to use
Since this pipeline depends on different r packages that are developed by external parties, it is of importance to consider that you follow the steps in this paragraph. Enabling the corresponding libraries is completely dependent on [conda](https://docs.conda.io/en/latest/). Make sure that you install  conda on your device: [Windows](https://docs.conda.io/projects/conda/en/latest/user-guide/install/windows.html) or [Mac](https://docs.conda.io/projects/conda/en/latest/user-guide/install/macos.html). If you already ran this pipeline before you can skip to [run the pipeline](#run-the-pipeline), otherwise check out how to setup Conda below.

## Conda setup
If this is the first time that you are running this pipeline, it is of importance to generate the correct environment.

**1. Open a terminal**: check out the [getting started](https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html#starting-conda) paragraph which shows you to open the prompt terminal.
 
**2. Add channels**: to make sure that we can install all of the packages that we need.
 Copy-paste the following lines in the terminal that you opened in the previous step.
 
```
conda config --add channels conda-forge
conda config --add channels bioconda
conda config --add channels r
```
 
To check if this step was successful you can use `conda config --show channels` to retrieve a list with all of the channels that you have installed. This should look something like this:

```
- r
- bioconda
- conda-forge
- defaults
```
 
**3. Create environment**: you have to run the following command in the prompt terminal to make sure that we have all of the right libraries that are necessary to run our pipeline.

```
conda create -n uniform_file_writer r-doparallel r-dplyr r-foreach r-future r-openxlsx r-plyr r-readxl r-tuple r-rstudioapi
```

After you ran this line, you will be asked whether you want to proceed, type `y` (of course 🤷‍♀️). Now, all of the necessary libraries are going to be installed in the environment `uniform_file_writer`. At the end, you will get a message with the text that everything is done and that you can activate and deactivate the environment with the belonging commands (see example below). 
 
```
done
Executing transaction: | 
| 
done
#
# To activate this environment, use
#
#     $ conda activate uniform_file_writer
#
# To deactivate an active environment, use
#
#     $ conda deactivate 
```

Now you can start with the next step to make sure that you can perform the analysis 💪!

### Run pipeline
If you already have the `uniform_file_writer` environment, then we don't have to do a lot anymore! You already have the environment which is necessary to run the pipeline with 🙌!

The first step is to `open the prompt terminal`. If you have forgotten how to do this, then check out [getting started](https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html#starting-conda). Next, we are going to activate the conda environment with all of the libraries that are necessary to run the pipeline with `conda activate uniform_file_writer`. The last part is to open [RStudio](https://www.rstudio.com/) with the following command for Windows `open Rstudio` or Mac `open -na Rstudio`. In **RStudio**, you can open an `existing file`, where you can open up the main.R script.
From here on, you can run the pipeline 🎉!!
-->



#

| Pipeline | Description | Users | Developer(s) |
| --- | --- | --- | --- |
| [CLL_cocktail_definer](https://github.com/AG-Walz/CLL_cocktail_definer) | Code that is used for the cocktail definition | MW | MD |
| [easy_waterfall](https://github.com/AG-Walz/easy_waterfall) | Generates a nice waterfall plot | MW | MD |
| [frameshift_shuffle](https://github.com/AG-Walz/frameshift_shuffle) | Functionality that can be used where there are frameshift as a result of somatic alterations, ultimately translating to kmers surrounding the mutation site | MW | MD & SL |
| [gene_ontology_generator](https://github.com/AG-Walz/gene_ontology_annotator) | Annotates a list (of multiple conditions) to the gene functions and results in the generation of various figures (per condition and comparing conditions that are present in one file)  | MD | MD |
| [kmer_calculator](https://github.com/AG-Walz/kmer_calculator) | Generates the kmer (mutation/sequences) | MW, JB, AN | MD & SL |
| [ligandomat](https://github.com/AG-Walz/ligandomat) | Functionality to predict the binders | All | JS |
| [mhcquant_report_generator](https://github.com/AG-Walz/mhcquant_report_generator) | Quality check report that can be generated after the MHCquant report | JB, MD | JS & MD |
| [MTB_sheet_writer](https://github.com/AG-Walz/MTB_sheet_writer) | This functionality can be used to obtain all of the information which is necessary for MTB related data | JB | MD |
| [organism retriever](https://github.com/AG-Walz/organism_retriever) | Determines in which species a peptide is identified | JB | MD |
| [protein_spotter](https://github.com/AG-Walz/protein_spotter) | Performs the detection of the hot and darkspot of proteins | MW, YM & TB | MD & SL |
| [uniform_file_writer](https://github.com/AG-Walz/uniform_file_writer) | Content that can be used with the protein discoverer output, making the outcome uniform (regardless of the version) | NHG, LM & AN | JS & MD |
| [Scripts](https://github.com/AG-Walz/smallScripts) | If your pipeline of interest is not present, then you might find it here (functionality too small to call it a pipeline)| MD | MD|
||||
| [Data management](https://github.com/AG-Walz/data-management) | This repository is reserved with all of the code and procedures that are necessary for the group's data management| HP, MD | MD |
| [Student](https://github.com/AG-Walz/students) | Work of the current and previous students saved in one repository | JS, CS | JS, CS |
