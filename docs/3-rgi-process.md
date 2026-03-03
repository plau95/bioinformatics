# Resistance gene identifier (RGI) process workflow #
**Purpose:** To identify potential genes associated with antibiotic resistance from a database ([Comprehensive Antibiotic Resistance Database [CARD]](https://card.mcmaster.ca/)). 

## Pre-requisites ## 
* Contigs produced from 1-WGS-Process
* Python, conda, mamba installed via CLI (Listed in 1. Installing RGI)

**Note about Installation** 

I've run into the issue of installing RGI due to the dependencies RGI requires being written for Intel-based systems. 
If your computer runs on Apple Silicon (M1-based; early-2020 purchase), follow the troubleshooting steps outlined in the *Troubleshoot* portion.

### 1. Pre-installation ### 

   1. Install conda
   
   *Conda is an open-source package and environment manager that downloads, updates and installs various software and their dependencies. (More on this later)*

   * Install miniconda through following the Installation process and prompts listed on the miniconda website 
     
     > miniconda provides the bare essentials for getting through our analyses. 
     > Down the road, if you choose to explore other packages (such as those for data analysis or machine learning), you may install Anaconda.

  * Check conda installation through prompting `conda info` in CLI/Terminal. 

      Will provide detail information about the installation of your conda package. 

   2. Install miniforge
      > Miniforge is
      
   3. Install mamba

### 2. Installing RGI ### 
We essentially will follow the installation steps as noted in [arpcard/rgi](https://github.com/arpcard/rgi?tab=readme-ov-file). 
Here, however, I'll be provided a non-technical intepretation of the code. 

  1. Search for RGI version through channels
  > We'll be looking for the most recent version of RGI through the channels available on our system.
  > "Channels" refer to available software package distributors that may have RGI available to download and install.
  >
  > What the command is saying is "Check these channels (noted with the flag --"name") for the package 'rgi'". 
  
  2. Creating a new environment
  > An environment here refers to a separate space within our operating system that has its own packages, softwares, etc.
  > We can customize our environment with whatever software, its needed dependencies, for it to work.
  >
  > The command provided is saying "Create a new environment named rgi, and search the available channels for any dependencies needed"
     





