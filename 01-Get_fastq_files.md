# Contents 

## Find data  
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


## Download data to the server 
Click on the file starting with "SRR...". This takes you to the SRA run browser. Here you can see more information about the data files. Click on the tab "Data access". Here you can find download links to the two paired fastq files (these are gzipped so they end with the extension .gz):  

<img src="/images/sra_run_browser.png" width="700" height="500">   

Click [here](https://trace.ncbi.nlm.nih.gov/Traces/sra/?run=SRR14253446) if you can't find the right links.  

Right click on the first link to the fastq file (ending with .gz) and copy the link. Go to the server and type the command `wget` and paste the link. Something like this: `wget https://sra-download.ncbi.nlm.nih.gov/traces/sra2/SRZ/014289/SRR14289348/TX-UTA-000521_L001_R1.fastq.gz`. Hit enter. This should download the first fastq file. Do the same for the second. After this is done type `ls`. Do you have two new files ending with `.gz`?

### Download directly to the server  
`/storage/BIOS3010/jonbra/HTS/sratoolkit.2.11.0-centos_linux64/bin/fastq-dump --split-files SRR14253446`

### Download via your computer  
De kan velge om de vil bruke wget, WinSCP eller FileZilla eller hvilken som helst annen metode. 
NCBI har en egen samleside for Corona-data. (click on the link called "SARS-CoV-2 data (NCBI)".

We will go to the SRA database of NCBI. The Short Read Archive. Scroll down to find the link called "SARS-CoV-2 next-generation sequencing runs in SRA". SI TO ORD OM SRA.

TWO WORDS ABOUT THE LEFT SIDE. ASK THE STUDENTS TO EXPLORE THE DIFFERENT DATA TYPES. HVA ER DET DE KJENNER IGJEN FRA FORELESNINGEN?

STILLE NOEN SPØRSMÅL OM DATA TYPES SOM DE MÅ SVARE PÅ I OPPGAVENE.



SELECT ANY LINK THEY WANT AFTER THAT?

Use SRA DUMP? Part of Conda?

Use basic Unix commands to inspect the fastq-files and answer the questions:  
!How many lines does each file consist of?  
!And how many sequences are that?
