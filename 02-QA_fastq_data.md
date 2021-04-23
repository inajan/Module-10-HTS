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
  
FastQC will produce two types of files. `.html` files and `.zip` files. We only need the html files. But since we can't view these files in the terminal you need to download them to your computer. If you have a windows machine and use Putty instead of GitBash you should download [WinSCP](https://winscp.net/eng/download.php) to transfer the files. If you have GitBash, or you have a Mac or Linux machine, you need to open a new terminal window. In this window you will be on your local computer. 

First, on the server terminal, type `pwd` to display the path to you location. Then, in the other terminal window which is on your local machine, type the following command (replace *username* with your uio username (group 6-10 use test02 instead of test01) and *path/to/fastq/file* with the output from `pwd`):    

```bash
scp username@itf-appn-test01.hpc.uio.no:path/to/fastq/file/*.html .
```

Type your UiO password. You should see something like this:  

<img src="/images/scp.png">  


## FastQC

## Trimmomatic  
trimmomatic PE SRR14253446_1.fastq SRR14253446_2.fastq SRR14253446_1_trimmed.fastq SRR14253446_1_single.fastq SRR14253446_2_trimmed.fastq SRR14253446_2_single.fastq ILLUMINACLIP:$HOME/.conda/pkgs/trimmomatic-0.39-hdfd78af_2/share/trimmomatic-0.39-2/adapters/TruSeq3-PE.fa:2:30:10 SLIDINGWINDOW:4:20

## FastQC again

## Download from server
