# Contents 
- [Find data](#find-data)
- [Download data to the server](#download-data-to-the-server)
- [Inspect the fastq files](#inspect-the-fastq-files)

## Find data  
First, make sure you have done the instructions described in [00-Get_started.md](00-Get_started.md) and that the "HTS" conda environment is active.  

As you have probably learned, there are many databases for HTS data. The two most common and comprehensive are probably [ENA - the Europoean Nucleotide Archive](https://www.ebi.ac.uk/ena/browser/home) and the [NCBI SRA database](https://www.ncbi.nlm.nih.gov/sra).

We will use SRA today and download some public HTS data from SARS-CoV-2. Click on the link above to get to the main page. There is a separate SARS-CoV-2 version of the database. Find the link called "SARS-CoV-2 data (NCBI)" at the top of the page, in the pink region. Then click on the link on the middle of the page with a number and "SRA runs" under it. You should now be on a page looking something like this (if not, click [here](https://www.ncbi.nlm.nih.gov/sra/?term=txid2697049%5BOrganism:noexp%5D%20NOT%200[Mbases)):  
<img src="/images/SRA.png" width="700" height="500">   

On the left side it's possible to filter the data. Click the following links:  
Library layout "paired"  
Platform "Illumina"  
Source "RNA" (SARS-CoV-2 is an RNA virus)  
File type "fastq"  
Strategy "other"  

Click on one of the results. Probably called something with "PCR tiled amplification" (the SARS-CoV-2 genome is usually amplified with a PCR protocol) (Click [here](https://www.ncbi.nlm.nih.gov/sra/?term=SRR14253446) if you have trouble finding any relevant data):  


Answer these questions:  
```diff
! What does "paired" library layout mean? 
! How many sequence files can you expect from "paired" data?
! What is the "Run" accession for the sample you have selected? (begins with SRR...). Write it down.
! "Spots" is the number of sequenced reads (it refers to the read clusters on the sequencing array). Write down how many reads (spots) have been sequenced for your sample and the size of the file.
````  

[Back to top](#contents)

## Download data to the server 
Click on the file starting with "SRR...". This takes you to the SRA run browser. Here you can see more information about the data files. Click on the tab "Data access". Here you can find download links to the two paired fastq files:  

<img src="/images/sra_run_browser.png" width="700" height="500">   

Click [here](https://trace.ncbi.nlm.nih.gov/Traces/sra/?run=SRR14253446) if you can't find the right links.  

Right click on the first link to the fastq file (ending with .gz) and copy the link. Go to the server and type the command `wget` and paste the link. Something like this: `wget https://sra-download.ncbi.nlm.nih.gov/traces/sra2/SRZ/014289/SRR14289348/TX-UTA-000521_L001_R1.fastq.gz`. Hit enter. This should download the first fastq file. Do the same for the second. After this is done type `ls`. You should now have two new files ending with `.fastq`.  

[Back to top](#contents)

## Inspect the fastq files

Use basic Linux commands and your knowledge about the fastq file forma to answer the following questions (and save screen shots of how you found the answer):
```diff
! How may lines does the two fastq files contain?
! How many paired reads are in your files? Does this match with the number you found in the previous exercise?
! What is the quality symbol (ASCII character) for the first nucleotide in the first read in the SRR..._1.fastq file?
````
See [this table](https://support.illumina.com/help/BaseSpace_OLH_009008/Content/Source/Informatics/BS/QualityScoreEncoding_swBS.htm)   
```diff
! Can you trust that this nucleotide has been called correctly?
```

Now we will run the program [FastQC](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/) which is a quick and easy way to get basic statistics and lots of useful information about our sequence data. Simply run the command `fastqc SRR*.fastq` (you know what the wildcard (\*) does right?)  

You should see an output like this:  
```
Started analysis of SRR14253446_1.fastq
Approx 5% complete for SRR14253446_1.fastq
Approx 10% complete for SRR14253446_1.fastq
Approx 15% complete for SRR14253446_1.fastq
Approx 20% complete for SRR14253446_1.fastq
```
  
FastQC will produce two types of files. `.html` files and `.zip` files. We only need the html files. But since we can't view these files in the terminal you need to download them to your computer. If you have a windows machine and use Putty instead of GitBash you should download [WinSCP](https://winscp.net/eng/download.php) to transfer the files (download and install the program and log on to the server similar to what you did in Putty). If you have GitBash, or you have a Mac or Linux machine, you need to open a new terminal window. In this window you will be on your local computer. 

First, on the server terminal, type `pwd` to display the path to you location. Then, in the other terminal window which is on your local machine, type the following command (replace *username* with your uio username (group 6-10 use test02 instead of test01) and *path/to/fastq/file* with the output from `pwd`):    

```bash
scp username@itf-appn-test01.hpc.uio.no:path/to/fastq/file/*.html .
```

Type your UiO password. You should see something like this:  

<img src="/images/scp.png">  
