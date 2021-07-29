# Polygenic Risk Scores (PRS)
## About
A polygenic risk score (PRS) is genetic score which quantifies an individual's polygenic contribution to a trait. There are a number of methods to calculate it, but all will use the individual's allelic dosage at significantly associated SNPs and the effect sizes of the significantly associated SNPs. 

Read more here: https://www.prsice.info/step_by_step/

## Tools
### PLINK
Both versions of PLINK can be used to calculate PRS. 
#### PLINK 1.9
Allelic scoring

    plink --bfile chr1to22 --score summary_statistics_file.gz 13 4 7 header no-mean-imputation --allow-extra-chr --output chr1to22.prs
    
in which:
- chr1to22 is the prefix of the bed, fam, bim file
- summary_statistics_file.gz is the file containing the statistically associated SNPs
- 13 refers to the column of rsIDs 
- 4 refers to the column of effect alleles
- 7 refers to the column of effect sizes 
- *header* means there is a column header in the summary statistics file
- *no-mean-imputation* means to throw out missing observations
- allow-extra-chr is if there are additional chromosomes besides 1 through 22 (e.g. pseudoautosomal regions are sometimes coded as PAR1, PAR2, etc.)

    
#### PLINK 2.0
Linear scoring

    plink2 --bfile chr1to22 --score summary_statistics_file.gz 13 4 7 header no-mean-imputation ignore-dup-ids list-variants --allow-extra-chr --output chr1to22.prs
    
in which:
- chr1to22 is the prefix of the bed, fam, bim file
- summary_statistics_file.gz is the file containing the statistically associated SNPs
- 13 refers to the column of rsIDs 
- 4 refers to the column of effect alleles
- 7 refers to the column of effect sizes 
- *header* means there is a column header in the summary statistics file
- *no-mean-imputation* means to throw out missing observations
- *ignore-dup-ids* means to ignore duplicate SNPs in the summary statistics file
- *list-variants* lists the variants used in the actual score
- allow-extra-chr is if there are additional chromosomes besides 1 through 22 (e.g. pseudoautosomal regions are sometimes coded as PAR1, PAR2, etc.)

or

    plink2 --pfile chr1to22 vzs --score summary_statistics_file.gz 13 4 7 header no-mean-imputation ignore-dup-ids list-variants --allow-extra-chr --output chr1to22.prs
    
(which is the same as before, except PLINK 2 binary files are being used (psam, pvar, pgen))

### PRSice-2

