# Assembly, bin and annotate! 

## Workflow ## 
Note to self: can perform A-B-A either in Terminal CLI
*[Insert diagram here]* 

## 1. Quality check/read hygiene ## 
***If using KBase***

- Bulk uploading samples through importing your files onto KBase
  * Analyze window > Click on Arrow > Click on **Import**
  * Upload local files onto KBase *(NOTE: There is a upload limit to the sample size)*
  * For each sample, check off whether to import it as "Non-Interleaved" or "Interleaved" sample:
    
    * **Non-interleavened** : Samples presented as individual R1/R2 files
    * **Interleavened**: Samples presented as alternating read pairs (Read1_R1, Read1_R2, etc.)
    
  * Select if file is Forward (R1) or Reverse (R2) read. Additionally give a unique object name to differentiate it between forward/reverse.
    * This only matters to you. Make sure you understand it.
  * Select the "Sequencing Technology" used to process your reads, and check the box for "Single Genome".
  
### 1.2 FASTQC and Trimmomatic ### 
Want to know how good our sequencing was prior to cleaning it up (Rarely will be great). 

* FASTQC: Checks the quality of our reads and presents it with various formats. **Focus on Phred score**
* Trimmomatic: Trims adapter sequences and bad quality reads 

**Steps** 
Pre-trim FASTQC 
  1. Select read sequence
  2. x

Trimmomatic 

  1. 
  2. 

Post-Trim FASTQC
  
  1. 
  2. 

## 1.3 Assemble using two assemblers ## 
**Purpose**: To create a single contiguous read (i.e. contig) by using assessing k-mer length quality of our reads

*NOTE: There could be more assemblers that have been preferred and relevant in the sequencing community. 
We'll just be going with the more established of the bunch.*

### 1.3 Selecting our assemblers ### 
Here, we'll be using [MEGAHIT](https://academic.oup.com/bioinformatics/article/31/10/1674/177884) and [metaSPAdes](https://pmc.ncbi.nlm.nih.gov/articles/PMC5411777/) for our analysis.
KBase also provides additional assemblers to choose from but is beyond the scope of this introduction.

***Why would we want to use multiple assemblers?***

Essentially, have the most options in selecting for the *best* outputs for assembling our genome. 
Each assembler, though achieves the same result of creating contigs, does so through different methods. 
With each assembler, comes both pros and cons which are seen in the output files. Both assemblers we use involve the use of de Brujin graphs and k-mer overlaps to find the best scaffold for our samples.

***The relatiosnhip between k-mer edges and de Brujin graphs***:

> ***k-mer edges*** are n-length pieces of your original sequence that can overlap (an edge).
> ***de Brujin graphs*** are connected pieces of these k-mer overlaps that form a more complete picture of our original sequence (aka the contig)

  ***Using MEGAHIT***
  
  > MEGAHIT assemblies result from the use of an "memory-efficient" single-node (single-computer) assembler that works on larger and complex samples.
  > With MEGAHIT, we often provide a list of k-mers to the assembler, which iteratively produces a contig as a product from the list of k-mers we provided. 

  ***Using metaSPAdes***
 
  > metaSPAdes assemblies are often "higher-quality" (read: long contigs) at the trade-off of being computationally intensive (requires more RAM to process).
  > metaSPAdes assemblies also use de Brujin graphs but retains the best results from each k-mer used. 

***How do we know which is the best output to use***

While each assembler produces different results with different qualities, it essentially comes down to comparing our assemblies through using QUAST to find the best contigs produced. 
QUAST (Quality assessment tool) is designed to provide summary metrics of the assembly process/read. We can use these to compare each sample's assembled contigs to one another and select the best outputs for downstream analyses.
While there aren't perfect metrics to really assess the best contigs, here is starting list you can use:

  1) **N50, N75**: Tells you the length you've captured x% of your assembly. If the length of your assemble at x% is relatively high, we have a well-construct contig.
  2) **L50, L75**: The number of contigs that make up x% of our assembly
  3) **Contig length**: Sum of contig lengths

**Steps** 
1. Download the contigs and into our project folder we made at the beginning
2. Record the the N50, N75, L50, L75 and length per sample/assembler for metadata/supplementary figures

**We can stop here and proceed to [Resistance gene identification (RGI)](link here), or continue on to binning and annotation of our contigs (for MAG construction)**




  
