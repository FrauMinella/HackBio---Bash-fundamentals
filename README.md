# HackBio---Bash-fundamentals
This repository documents my first task in the Coding for Bio: Linux &amp; BASh Fundamentals with HackBio: Through this project, I gained hands-on experience in Linux command-line operations. I also learned to set up and manage conda environments, and successfully installed bioinformatics tools.

### Project 1: Bash Basics

#Print name
echo 'Minella'

#Create a folder with my name 
mkdir Minella

#Create a `biocomputing` directory and change into it (one line)
mkdir biocomputing  && cd biocomputing

#Download dataset files (`wildtype.fna`, `wildtype.gbk`)
#https://raw.githubusercontent.com/josoga2/dataset-repos/main/wildtype.fna
#https://raw.githubusercontent.com/josoga2/dataset-repos/main/wildtype.gbk
#https://raw.githubusercontent.com/josoga2/dataset-repos/main/wildtype.gbk
wget https://raw.githubusercontent.com/josoga2/dataset-repos/main/wildtype.fna
wget https://raw.githubusercontent.com/josoga2/dataset-repos/main/wildtype.gbk
wget https://raw.githubusercontent.com/josoga2/dataset-repos/main/wildtype.gbk

#Move `.fna` file into my name folder 
mv wildtype.fna ~/Minella/

#Delete duplicate `.gbk` file  
rm wildtype.gbk.1

#Confirm if `.fna` file is mutant (`tatatata`) or wild type (`tata`) 
grep 'tatatata' wildtype.fna
#The wildtype.fna file is a mutant

#Save all mutant-matching lines into a new file
grep 'tatatata' wildtype.fna >  matching_lines.txt

#Count number of lines (excluding header) in `.gbk`  
tail -n+2 wildtype.gbk | wc -l
#number of lines is 5749

#Print sequence length from `.gbk` (LOCUS tag)
grep 'LOCUS' wildtype.gbk
grep 'LOCUS' wildtype.gbk | awk '{print $3, $4}'
#sequence length is 197394 bp
 
#Print source organism from `.gbk` (SOURCE tag) 
grep 'SOURCE' wildtype.gbk
grep 'SOURCE' wildtype.gbk | awk '{print $2, $3}'
#source organism is Staphylococcus aureus

#List all gene names in `.gbk`
grep '/gene=' wildtype.gbk
#There are 107 genes in the file

#Clear terminal and print command history
clear && history

#List files in both folders  
ls -lh Minella
ls -lh biocomputing

## Project 2: Installing Bioinformatics Software

#Activate base conda environment 
conda --version

#Create new environment `funtools`
conda create -n funtools python=3.10

#Activate `funtools`
conda activate funtools

#Install `figlet` (via conda/apt-get) 

#Run `figlet <my_name>`
figlet Minella

#Install tools from **bioconda** channel;(`bwa`, `blast`, `samtools`, `bedtools`, `spades`, `bcftools`)
conda install bwa
conda install blast
conda install samtools
conda install bedtools bcftools
conda install fastp multiqc
conda install spades

