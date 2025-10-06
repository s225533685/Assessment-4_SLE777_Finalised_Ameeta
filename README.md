
Assessment 4_SLE777_R Project

Author: Ameeta
Date: 2025-10-05

This repository contains the R Markdown project for gene expression analysis, tree growth data interpreation, and biological sequence diversity analysis for E.coli and saprospirales (organism of interest). The project is divided into several scritps and steps, each performing a specific analysis. 

GENE EXPRESSION ANALYSIS

Purpose: The main purpose of gene expression analysis is to download, process, and analyze gene expression data to identify the genes with the highest and lowest mean expression and to visualize the distribution. 

Input: The input includes gene_expression.tsv which was downloaded from github. 

Steps and outputs
 
1. Download and read data
Step: To download the file and read data, the download.file()and read.table() function is used.

Output: The output obtained is gene_data dataframe containing gene expression values 

2. Calculate mean expression per gene:

Step: The mean value of other columns are calculated using rowMeans() function and saved as meanexpression in a new column 

Output: The updated gene_data data frame is obtained. 

3. Identify top expressed genes 

Step: The meanexpression is ordered in the descending order using order (-) function. 

Output: The genes with high expression are obtained in the decreasing order. 

4. Count genes with low expression(<10)

step: The logical vector and sum() are used to count the genes with low expression 

Output: The total number of genes with low meanofexpression is obtained 

5. Histogram of mean expression values:

Step: The hist() function is used to visualise the mean data distributions

Output: The histogram plot showing low and high expression patterns are obtained 


TREE GROWTH DATA ANALYSIS

Purpose: The purpose of running this script is to analyse tree circumference at different sites over different time periods and to calculate the growth over the years and to visualise the differences between different study time periods and at different sites. 

Input: The input file is growth_data.csv (downloaded from GitHub)

Steps / Outputs:

1. Import growth data

Step: The growth data is imported using download.file() and read using read.csv function. The column names are displayed using colnames() function. 

Output: The growth_data dataframe and the column names are obtained. 


2. Calculate mean and standard deviation for each site and year:

step: The mean and standard deviation for different sites at the start and end of study period is calculated using mean() and sd() function respectively. The outputs are displayed using the data frame. 

Output:The summary_table showing mean and SD for different study time periods at at different sites is generated. 

3. Boxplot of tree circumference:

Step : The data is split into  different sites and boxplot() function is used for comparison of data. The  boxplots are placed side by side by entering the dataset for both the sites in the same boxplot() function. 

Output: Side-by-side box plots comparing start and end measurements of 2 different sites are obtained.

4. Calculate 10-year growth:

Step: The 10- year growth values is determined by finding the difference in growth between two time periods and the output is saved in the new column. The mean value is obtained using mean() function. 

Output: Mean growth for different sites are obtained

5. t-test to compare sites:

Step: The t-test function is used to determine the p-value for the different sites to compare the growth between the sites. 

Output: P-value at 5% significance is achieved. 

BIOLOGICAL SEQUENCE DIVERSITY ANALYSIS

Purpose: The purpose of the script is to download CDS sequences for organism of interest or target organism, analyze genome features, amino acid composition, codon usage, and k-mer distribution.

Input:FASTA files are used as input. 

Steps / Outputs:

1. Download and read CDS sequences:

Step: The function such as download.file() is used to download file, gunzip() to uncompress the file and read.fasta() to read the file. 

Output: The list of organisms cds is obtained 

2. Count number of coding sequences and total coding DNA:

step: The length() function is used to count the number of coding sequences and data.frame() is used to generate a table. 

Output: The cds_table showing the count of coding sequences is obtained.

3. Determining and comparing total codin DNA between organisms 

Step: The summary() function is used to extract the length of coding sequences and the specific column containing the length is converted to numeric value using as.numeric() function. The total length of all the genes are calculated by using sum() function. The table is generated using data.frame to disolay the result. 

Output: The table containing data on total length of CDS is obtained. 

4. Plotting boxplot of CDS length 

Step: The boxplot () is used to display the cds length distribution. The mean() and median() functions are used to fine the mean and median value, and results are displayed in the tables. 

Output: Distribution plot comparing both organisms is obtained.

5. Base and amino acid frequency analysis:

Step: The unlist() function is used to list the CDS into a single long vectors of single character and count() is used to calculate the frequency, and values are displayed in the table, followed by visualisation using the plot. The lapply is used translate the dna to protein and unlist() is used to give a long aminoacid vector. Following that, the aminoacids frequency are counted using the count() function and table is generated for aa frequency of both organisms. Then, the barplot is generated for the aminoacid frequency. 

Output: Side-by-side barplots for nucleotide and amino acid frequencies are obtained. 

6. Codon usage bias analysis:

Step: The uco() function is used calculate the codon usage and RSCU values. The order() is used to sort the codons to ensure the codon table contains consistent values for the organisms to be compared. The index="rscu" is employed to compute relative synonymous codon usage which is a measure of codon usage bias. The data.frame is kept TRUE to convert the result into plotting. 

Output: Barplot of codon usage bias for both organisms are generated

7. K-mer analysis (length 3-5):

Step: The k-mer frequnecy in protein sequence is calculatedusing count() function. The top-kmers() function is used to identify top over- and under-expressed k-mers of organism of interest. The barplot() function is used to create side-by-side bars for each k-mer. 

Output: Side-by-side barplots comparing k-mers of of organism of interest and other organism is displayed. 

Comparison and interpretation: The k-mers that are common or unique are identified between the organisms.The difference in K-mer representation due to codon usage bias, GC conten and protein function adaaptation is observed. 

Dependencies

The following R packages are used in the project:

install.packages(c("seqinr", "R.utils"))

File Structure
Assessment4/
│
├── geneexpression.tsv           # Raw gene expression file
├── growth_data.csv              # Raw tree growth data
├── ecoli_cds.fa.gz              # Compressed E.coli CDS
├── saprospirales_cds.fa.gz      # Compressed Saprospirales CDS
├── Assessment_4_R-Project_SLE777.Rmd       # R Markdown file containing all scripts and analysis
├── README.md                    # Project README file

Usage

Open Assessment4_SLE777.Rmd in RStudio.

Run all chunks sequentially to reproduce analyses and figures.

All plots and summary tables will be generated in the PDF output.

This README provides clear guidance on purpose, inputs, steps, outputs, and file organization for anyone accessing the repository.






















