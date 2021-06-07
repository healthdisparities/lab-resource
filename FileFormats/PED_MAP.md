# PED/MAP
The PED file is a white-space (space or tab) delimited file: the first six columns are mandatory:
```
     Family ID
     Individual ID
     Paternal ID
     Maternal ID
     Sex (1=male; 2=female; other=unknown)
     Phenotype
```
The IDs are alphanumeric: the combination of family and individual ID should uniquely identify a person. A PED file must have 1 and only 1 phenotype in the sixth column. The phenotype can be either a quantitative trait or an affection status column: PLINK will automatically detect which type (i.e. based on whether a value other than 0, 1, 2 or the missing genotype code is observed).

Genotypes (column 7 onwards) should also be white-space delimited; they can be any character (e.g. 1,2,3,4 or A,C,G,T or anything else) except 0 which is, by default, the missing genotype character. All markers should be biallelic. All SNPs (whether haploid or not) must have two alleles specified. Either Both alleles should be missing (i.e. 0) or neither. No header row should be given. For example, here are two individuals typed for 3 SNPs (one row = one person):
```
     FAM001  1  0 0  1  2  A A  G G  A C 
     FAM001  2  0 0  1  2  A A  A G  0 0 
     ...
```

The corresponding columns are defined in the MAP file. By default, each line of the MAP file describes a single marker and must contain exactly 4 columns:
```
     chromosome (1-22, X, Y or 0 if unplaced)
     rs# or snp identifier
     Genetic distance (morgans)
     Base-pair position (bp units)
```

The MAP file must therefore contain as many markers as are in the PED file. The markers in the PED file do not need to be in genomic order: (i.e. the order MAP file should align with the order of the PED file markers).
```
     1  rs123456  0  1234555
     1  rs234567  0  1237793
     1  rs224534  0  -1237697        <-- exclude this SNP
     1  rs233556  0  1337456
     ...
```
