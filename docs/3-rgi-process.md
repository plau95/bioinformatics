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
```
mamba search --channel conda-forge --channel bioconda --channel defaults rgi
```
  > What the command is saying is "Check these channels (noted with the flag --"name") for the package 'rgi'". 
  
  2. Creating a new environment
  > An environment here refers to a separate space within our operating system that has its own packages, softwares, etc.
>  We can customize our environment with whatever software, its needed dependencies, for it to work.
```
mamba create --name rgi --channel conda-forge --channel bioconda --channel defaults rgi
```

The command provided is saying "Create a new environment named rgi, and search the available channels for any dependencies needed".

3. Install RGI version
   
     ```
     mamba install --channel conda-forge --channel bioconda --channel defaults rgi=5.1.1
     ```

4. Attempt to instantiate RGI
   ```
   conda activate rgi
   rgi --help 
   ```
   Should get a pop up window that looks like the following:
   <To be edited with a screenshot of RGI window>

	#### *Troubleshoot: Cannot create RGI environment* ####

	One issue we could encounter is not being able to create an environment, and will be getting
	a window such as the one below.  This is likely going to encounter is because the
	dependencies are written under Intel OS and not Apple Silicon. We'll create a workaround by
	performing the following:

	```
	CONDA_SUBDIR=osx64 mamba create --name rgi --channel conda-forge --channel bioconda --channel 	defaults rgi
	```

	The `CONDA_SUBDIR` is the key: we're essentially forcing mamba to look at file subdirectories 	`osx64` instead of going to our default (which usually is osx64-arch). After creating this 		environment, we can then go to `Step 2.3 Install RGI version`.

	#### *Troubleshoot: RGI will not instantiate* ####
	Check if system has Rosetta installed
    
    ```
	 /usr/bin/pgrep -q oahd && echo "Rosetta installed" || echo "Not installed"
	 ```
    
   If not installed, install Rosetta with the following:
		
   ```
   softwareupdate --install-rosetta --agree-to-license
   ```
   
	5. Install CARD database
    Pretty straight forward installation steps:
    * Download AMR reference database from CAR
      ```
      wget https://card.mcmaster.ca/latest/data
      tar -xvf data ./card.json
      ```
      > Saying "web get" from this website, and open the 		.tar datafile and put it in a subdirectory within 			our current working directory.
   * Load either locally or system wide
     ```
     rgi load --card_json /path/to/card.json --local
     ```
     > Here, the code is stating load the database JSON file and run it locally (for this user only).

	  > You can run the program system-wide by not instantiating the --local flag.
    




     





