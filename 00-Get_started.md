## Contents
- [Logging on to the server](#logging-on-to-the-server)
- [Installing and using software on a Linux system](#installing-and-using-software-on-a-linux-system)
- [Setting up your working environment](#setting-up-your-working-environment)


## Logging on to the server
For this part of the course we will be using a common server with a Linux operating system.
A 'server' is a computer that is located elsewhere, and that you can access remotely over the internet.
Servers are often more powerful, and/or have more memory and storage space than desktop or laptop computers.
Using such Linux servers is thus common in bioinformatics.

### Step 1: logging on to login.uio.no

For security reasons, we cannot log into the the server directly. First, we need to log in to another server called `login.uio.no`.
From there, we can log in to the course server.

Depending on your operating system there are different ways to log on to the `login.uio.no` server.

**Mac/Linux**  
If you have a Mac or a Linux PC, these already run on a Linux-like Operating System and you can open a program called the **Terminal**. The Terminal gives you access to all Linux commands.

When you have that program open, type

```
ssh username@login.uio.no
```

Replace *username* with your UiO username and hit Enter. Type in your UiO password (NB: you will not see anything happen when you type. This is normal).

<img src="/images/terminal.png" width="600" height="300">

You should see a message `Welcome to login.uio.no!`

Next, see below under "Logging on to the course server".

**Windows**  
On windows we recommend that you install [GitBash](https://gitforwindows.org/). This gives you a terminal with unix-style commands available on your local machine. You can then log on to the `login.uio.no` server with the same commands as above.  

You can also use [Putty](https://putty.org/) to log on, but this will not let you use unix-commands locally. In Putty,

* enter the name of the server in "Host Name"

<img src="/images/putty.png" width="250">  

  * click "Open"
* press "Accept" if you get a security alert

<img src="/images/putty2.png" width="250">  

* write your UiO username after "login as" and then your password (you will not see anything typing).

You should see a message `Welcome to login.uio.no!`

## Logging on to the course server

Once you are logged in to `login.uio.no`, you can log in to the course server:

* **group 1-5** do this: `ssh username@itf-appn-test01.hpc.uio.no`
* **group 6-10** do this `ssh username@itf-appn-test02.hpc.uio.no`

Again, write your password when asked for it.

When you have logged on to the server, type the command `pwd`. You should see something like this
<img src="/images/terminal_2.png" width="500" height="300">  

[Back to top](#contents)

## Installing and using software on a Linux system
Installing software on a Linux server like the ones we are using in this class can sometimes be difficult. Many programs have "dependencies", other programs or libraries, that needs to be installed in a specific way in order for the program to run properly. On the servers that we are using in this course there are many programs that have been pre-installed. The command `module avail` will give you a list of all pre-installed software. To activate a specific program, run `module load software name`.

It is common these days to use so-called "package managers", software that can help us install programs and all necessary dependencies for us. Common package managers for the Unix environments are [Homebrew](https://brew.sh/) and [Conda](https://anaconda.org/). Software can also be run using so-called containers. Containers provide a package with all necessary software and dependencies, which makes your programs run and work the same on all computer platforms. Common containers are [Docker](https://www.docker.com/) and [Singularity](https://sylabs.io/guides/3.0/user-guide/index.html#).  
[Back to top](#contents)

## Setting up your working environment
In these exercises we will use Conda to install the necessary software for us. Conda is already installed on the server, so just type `module load Anaconda3/2020.11` to activate it. If you now type `cond` and then press the TAB-button, the command `conda` should be "auto completed" (auto completion is the cornerstone of working in a Linux system. You simply *must* be able to know and use the TAB-button if you want to do bioinformatics). If you press TAB twice you should see other available commands starting with `conda`.  

It's good practice to have different "conda environments" for different projects. These environments will contain only the software that you need for that specific project. For these exercises we will create a Conda environment called "HTS". We specify what kinds of software we want in an "environment file".  

Run these commands:
```
cp /storage/BIOS3010/jonbra/HTS/environment.yml .  # copy the conda environment file from my shared directory
cat environment.yml # display the content of the file
```

You should see something like this:
```
name: HTS

channels:
    - defaults
    - bioconda

dependencies:
    - fastqc=0.11.9
    - trimmomatic=0.39
```
These are instructions that tells Conda to create an environment named "HTS" and that it should install the software fastqc version 0.11.9 and trimmomatic version 0.39 and that it can find these in the conda channels "defaults" and "bioconda".   

You now need to create the environment. *You only have to do this once.* Run this command:  
```
conda env create -f environment.yml
```


Now you can activate the conda environment by typing `conda activate HTS`.   

You should now have the command `fastqc` available. Try typing `fas` and then use autocomplete. What happens?  

To deactivate the environment type `conda deactivate`. Fastqc and trimmomatic will no longer be available.

[Back to top](#contents)
