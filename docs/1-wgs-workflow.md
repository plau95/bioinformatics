# Workflow for whole genome sequencing (WGS)

*Made and distributed for work associated in Dr. Gabriel Perron* 

**Purpose:** To provide an overview of the necessary steps for performing whole genome sequencing and subsequent analyses such as antibiotic resistance. We will be using publicly available resources such as [K-Base](https://kbase.us) and [EU Galaxy](https://usegalaxy.eu). 

While this intended to be coding friendly, prior knowledge of BASH and a programming language (like R or Python) will be useful. 

Finally, this is an introduction for students and not a exhaustive overview of WGS. This introduction serves as a basis for students but encourages further exploration of tools beyond what is provided here. 

If you have not sampled or prepared your DNA sample library, 

## Table of Contents ## 
* <a name="url-name">Whole genome sequencing</a>
	- Quality filtering
 	- Assembly with metaSPAdes and MEGAHIT
 	- Binning
 	- Annotation with MG-RAST and SEED 
* <a name="url-name">Antibiotic Resistance (Ab-res) detection with CARD </a>
* <a name="url-name">Functional prediciton with InterProScan</a>
* <a name="url-name">**BONUS: Example plots for RStudio**</a>

## Prerequisites ## 


## What is whole genome sequencing? ## 
Why do this? Why bother with understanding WGS? 

We care because samples are often unculturable (samples cultured in the lab represent 1-2% of environmental samples). We implement WGS to remeedy this issue to attempt to understand what functional potential the microbes in our sample represent–– which is metagenomics analysis. 

*How is this different than 16S?*

16S amplicon sequencing is a targeted sequencing approach, often using a primer set (F-515 <> 806-R) to know what microbes exist in a sample (the who). Additionally, the portion that gets amplified may not be present in all microbes. That's where WGS comes in. In regards to WGS, it is limited in understanding the how and why these microbes exist.
