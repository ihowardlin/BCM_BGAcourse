# BCM_BGAcourse
github repository with useful information for Bioinformatics &amp; Genomic Analysis taught at Baylor College of Medicine

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
Now open another terminal. This can be done by using the navigation bar (Shell > New Window > New Window with Profile - Basic) or by using the hotkey (command ⌘ + N).

Run the following command, substituting your student number and port number:

```
ssh -v student##@sphere.grid.bcm.edu -NL 199##:localhost:199##
```

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

### Analyzing Genomic FASTA Files (genomic.fna.gz)

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
