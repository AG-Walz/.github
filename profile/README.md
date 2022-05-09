
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

#

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

#

| Pipeline | Description | Users | Developer(s) |
| --- | --- | --- | --- |
| [CLL_cocktail_definer](https://github.com/AG-Walz/CLL_cocktail_definer) | Code that is used for the cocktail definition | MW | MD |
| [easy_waterfall](https://github.com/AG-Walz/easy_waterfall) | Generates a nice waterfall plot | MW | MD |
| [frameshift_shuffle](https://github.com/AG-Walz/frameshift_shuffle) | Functionality that can be used where there are frameshift as a result of somatic alterations, ultimately translating to kmers surrounding the mutation site | MW | MD & SL |
| [gene_ontology_generator](https://github.com/AG-Walz/gene_ontology_annotator) | Annotates a list (of multiple conditions) to the gene functions and results in the generation of various figures (per condition and comparing conditions that are present in one file)  | MD | MD |
| [kmer_calculator](https://github.com/AG-Walz/kmer_calculator) | Generates the kmer (mutation/sequences) | MW, JB, AN | MD & SL |
| [mhcquant_report_generator](https://github.com/AG-Walz/mhcquant_report_generator) | Quality check report that can be generated after the MHCquant report | JB, MD | JS & MD |
| [MTB_sheet_writer](https://github.com/AG-Walz/MTB_sheet_writer) | This functionality can be used to obtain all of the information which is necessary for MTB related data | JB | MD |
| [organism retriever](https://github.com/AG-Walz/organism_retriever) | Determines in which species a peptide is identified | JB | MD |
| [protein_spotter](https://github.com/AG-Walz/protein_spotter) | Performs the detection of the hot and darkspot of proteins | MW, YM & TB | MD & SL |
| [uniform_file_writer](https://github.com/AG-Walz/uniform_file_writer) | Content that can be used with the protein discoverer output, making the outcome uniform (regardless of the version) | NHG, LM & AN | JS & MD |
| [Scripts](https://github.com/AG-Walz/smallScripts) | If your pipeline of interest is not present, then you might find it here (functionality too small to call it a pipeline)| MD | MD|
||||
| [Data management](https://github.com/AG-Walz/data-management) | This repository is reserved with all of the code and procedures that are necessary for the group's data management| HP, MD | MD |
| [Student](https://github.com/AG-Walz/students) | Work of the current and previous students saved in one repository | JS, CS | JS, CS |
