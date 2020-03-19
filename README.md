# BCM_BGAcourse
github repository with useful information for Bioinformatics &amp; Genomic Analysis taught at Baylor College of Medicine

## Table of Contents
  * [Getting Started](#getting-started)
    + [Accessing the CIBR Cluster (MAC)](#accessing-the-cibr-cluster-mac)
    + [Accessing the CIBR Cluster (Windows)](#accessing-the-cibr-cluster-windows)
  * [Moving Files Around (scp)](#moving-files-around-scp)
  * [Using vcftools](#using-vcftools)
  * [Analyzing Genomic FASTA Files (genomic.fna.gz)](#analyzing-genomic-fasta-files-genomicfnagz)
  * [Useful Information](#useful-information)
    + [Bash Commands in Jupyter](#bash-commands-in-jupyter)
  
## Getting Started
### Accessing the CIBR Cluster (MAC)
Open a terminal window on your laptop/computer and using your assigned student# account (the example below assumes that your assigned student # is 14) and eight character password enter the following:
```
ssh student14@sphere.grid.bcm.edu
```
and enter the password when prompted.

```
student14@sphere.grid.bcm.edu's password: 
```
Run the command hard-reset to do the account set up for this class. Among other things, this will provide an initial set of files and directories. NOTE: you will need to put in the full path to the /home/student20/bin/ location for this file. So run it like this:

Log out using the exit command and then log back in. This allows the changes you made above to take effect. 

You should be able to run jupyter now by typing the start-jupyter command. 
```
start-jupyter
```
Run the command check-jupyter you will see the process running jupyter.
```
check-jupyter
```
You should get an output that shows your localhost and your port number separated by a :. The token is a long string of numbers and characters that will be used to authenticate your browser and will serve sort of like a password
```
http://localhost:199##/?token=3c116039b63162941f286cf8a626047018d500514d80714
```
Now open another terminal. This can be done by using the navigation bar (Shell > New Window > New Window with Profile - Basic) or by using the hotkey (command ⌘ + N). IMPORTANT: You should have TWO terminals running at this time.

In the new terminal, run the following command, substituting your student number and port number:
```
ssh -v student##@sphere.grid.bcm.edu -NL 199##:localhost:199##
```
Now open your browser and type in http://localhost:199##/ where ## is equal to your student number. In this case it would be http://localhost:19914/

### Accessing the CIBR Cluster (Windows)

Download your preferred SSH client or terminal emulator. Some popular choices include:

[MobaXterm free Xserver and tabbed SSH client for Windows](https://mobaxterm.mobatek.net/)

[PuTTY: a free SSH and Telnet client](https://www.chiark.greenend.org.uk/~sgtatham/putty/)

Open a terminal window on your laptop/computer and using your assigned student# account (the example below assumes that your assigned student # is 14) and eight character password enter the following:
```
ssh student14@sphere.grid.bcm.edu
```
and enter the password when prompted.

```
student14@sphere.grid.bcm.edu's password: 
```
Run the command hard-reset to do the account set up for this class. Among other things, this will provide an initial set of files and directories. NOTE: you will need to put in the full path to the /home/student20/bin/ location for this file. So run it like this:

Log out using the exit command and then log back in. This allows the changes you made above to take effect. 

You should be able to run jupyter now by typing the start-jupyter command. 
```
start-jupyter
```
Run the command check-jupyter you will see the process running jupyter.
```
check-jupyter
```
You should get an output that shows your localhost and your port number separated by a :. The token is a long string of numbers and characters that will be used to authenticate your browser and will serve sort of like a password
```
http://localhost:199##/?token=3c116039b63162941f286cf8a626047018d500514d80714
```
Now open another terminal. This can be done by using the navigation bar (Shell > New Window > New Window with Profile - Basic) or by using the hotkey (command ⌘ + N). IMPORTANT: You should have TWO terminals running at this time.

In the new terminal, run the following command, substituting your student number and port number:
```
ssh -v student##@sphere.grid.bcm.edu -NL 199##:localhost:199##
```
Now open your browser and type in http://localhost:199##/ where ## is equal to your student number. In this case it would be http://localhost:19914/

## Moving Files Around (scp)

To move files to the sphere you can use the scp command. If you are moving a file from your local machine to the cluster, open a terminal and navigate to the directory of the file on your local machine. Then enter the following:
```
scp sample.txt student14@sphere.grid.bcm.edu:/home/student14
```
The previous command will place the file sample.txt into the /home/student14 directory on the cluster. If you want to move a file sample.txt from the cluster to a folder on your local machine you can use the following command.

```
scp student14@sphere.grid.bcm.edu:/home/student14/Lab1/sample.txt /drives/c/Users/Userman/Folder
```
This command will move the file sample.txt from the /home/student14/Lab1 directory on the cluster into a Folder under the user Userman on the C drive of a Windows machine.

If you want to move an entire directory, all you need to do is include the -r flag. With -r specified, the directory tree is recursively traversed and each file encountered is downloaded.

```
scp -r /drives/c/Users/Userman/Folder student14@sphere.grid.bcm.edu:/home/student14
```

## Using vcftools
Begin by copying the files in /home/student20/Lab1_2019_Unix/ to your Lab1 directory.

```
cp /home/student20/Lab1_2020_Unix/Lab1_2019_Unix/HG002-HG003-HG004.jointVC.filter_Annotated.vcf.gz /home/student14/Lab1
```
You can check that the HG002-HG003-HG004.jointVC.filter_Annotated.vcf.gz file is complete by using md5sum and typing the following command into your terminal.

```
md5sum /home/student20/Lab1_2020_Unix/Lab1_2019_Unix/HG002-HG003-HG004.jointVC.filter_Annotated.vcf.gz
```
You should get something that looks like the following
```
c98fc778c5aad6c459d485cae129aebc  /home/student20/Lab1_2020_Unix/Lab1_2019_Unix/HG002-HG003-HG004.jointVC.filter_Annotated.vcf.gz
```
Now run the same md5sum command but using the location to which you just copied the 'HG002-HG003-HG004.jointVC.filter_Annotated.vcf.gz' file. If you are already in that specific directory you can just type:

```
md5sum HG002-HG003-HG004.jointVC.filter_Annotated.vcf.gz
```
You should get the same output, confirming that the download completed correctly.

Use vcftools to examine the file.  From the https://vcftools.github.io/man_latest.html guide, do the examples using your student account # as the chromosome (for accounts 1 to 22), chromosome X for accounts 23 and 33, chromosome Y for accounts 24 and 34, chromosome 20 for account 25 and chromosome 2 for account 26.  Accounts 27 to 32 should use chromosomes N-10 (i.e. account 27 uses chromosome 17).



## Analyzing Genomic FASTA Files (genomic.fna.gz)

Begin by copying the files in /home/student20/Lab1_2019_Unix/ to your Lab1 directory. Check that the HG002-HG003-HG004.jointVC.filter_Annotated.vcf.gz file is complete.

These are the accessions for the new genomes assemblies we discussed in class: GCA_001524155, GCA_002180035, GCA_002077035, GCA_002208065, GCA_002209525, GCA_002872155, GCA_003070785, GCA_003574075, GCA_003601015, GCA_003086635. You can search for the list at NCBI by combining them with OR: GCA_001524155 OR GCA_002180035 OR GCA_002077035 OR GCA_002208065 OR GCA_002209525 OR GCA_002872155 OR GCA_003070785 OR GCA_003574075 OR GCA_003601015 OR GCA_003086635 and searching using Entrez, they are in the Assembly section. Look at the linked data and descriptions, but you don’t need to download the files. I downloaded the Fasta sequences and other files and will put them in:

```
/home/student20/Lab1_2020_Unix/Lab1_2019_Unix/NewHumanGenomes/FastaFiles/ncbi-genomes-2019-03-15
```

First start by copying those FASTA files into your own student directory using:
```
cp -R /home/student20/Lab1_2020_Unix/Lab1_2019_Unix/NewHumanGenomes/FastaFiles/ncbi-genomes-2019-03-15/ /home/student14/Lab1/
```
Next you want to uncompress the files using gunzip by using the following command. This command will gunzip every file in the directory that ends with .fna.gz.

```
gunzip *.fna.gz
```
## Useful Information

### Bash Commands in Jupyter
Most bash commands need to have an exclamation point (or bang sign) in front to be properly interpreted in jupyter notebook. 

<img src="https://github.com/ihowardlin/BCM_BGAcourse/blob/master/bashcmds_jupyter.png" width="1000" height="400">

A second alternative is to put %%bash at the beginning of the code bloc so that all the code in the block will be interpreted as bash commands.

<img src="https://github.com/ihowardlin/BCM_BGAcourse/blob/master/bashcmds_jupyternotebook2.png" width="1000" height="225">
