## Contents
- [Logging on to the server](#logging-on-to-the-server)
- [Installing and using software on a Linux system](#installing-and-using-software-on-a-linux-system)
- [Setting up your working environment](#setting-up-your-working-environment)


## Logging on to the server
For this part of the course we will be using a common server with a Linux operating system. Using such Linux servers is common in bioinformatics. This gives you access to powerful computers with lots of storage space and you don't need to worry about loosing your data. Depending on your operating system there are different ways to log on to the server:  

**Mac/Linux**
If you have a Mac or a Linux PC, these already run on a Linux-like OS and you can open a program called the **Terminal**. The Terminal gives you access to all Linux commands. Type either: `ssh username@itf-appn-test01.hpc.uio.no` or `ssh username@itf-appn-test02.hpc.uio.no` (replace *username* with your UiO username) and hit Enter. Type in your UiO password (NB: you will not see anything happen when you type. This is normal).
[Back to top](#contents)

## Installing and using software on a Linux system
Installing software on a Linux server like the ones we are using in this class can sometimes be difficult. Many program have "dependencies", other programs of libraries, that needs to be installed in a specific way in order for the program to run properly. On the servers that we are using this course there are many programs that have been pre-installed. The command `module avail` will give you a list of all pre-installed software. To activate a specific program, run `module load software name`. 

It is common these days to use so-called "package managers", software that can help us install programs and all necessary dependencies for us. Common package managers for the Unix environments are [Homebrew](https://brew.sh/) and [Conda](https://anaconda.org/). Software can also be run using so-called containers. Containers provide a package with all necessary software and dependencies, which makes your programs run and work the same on all computer platforms. Common containers are [Docker](https://www.docker.com/) and [Singularity](https://sylabs.io/guides/3.0/user-guide/index.html#).  
[Back to top](#contents)

## Setting up your working environment
In these exercises we will use Conda to install the necessary software for us. Conda is already installed on the server, so just type `module load Anaconda3/2020.11` to activate it. If you now type `cond` and then press the TAB-button, the command `conda` should be "auto completed" (auto completion is the cornerstone of working in a Linux system. You simply must be able to know and use the TAB-button if you want to do bioinformatics). If you press TAB twice you should see other available commands starting with `conda`.  

It's good practice to have different "conda environments" for different projects. These environments will contain only the software that you need for that specific project. For these exercises we will create a Conda environment called "HTS". We specify what kinds of software we want in an "environment file". 

```
cp /storage/BIOS3010/HTS/environment.yml .
cat environment.yml
```

You should see something like this:
```
name: HTS

channels:
    - defaults
    - bioconda

dependencies:
    - fastqc=0.11.9
```

These are instructions that tells Conda to create an environment named "HTS" and that it should install the software "fastqc" version 0.11.9 and that it can find this software in the channels "defaults" and "bioconda".   

To create the environment run:
```
conda env create -f environment.yml
```
This installs the necessary software and you only need to run this command once. 

To activate the environment run `conda activate HTS`.  
[Back to top](#contents)
