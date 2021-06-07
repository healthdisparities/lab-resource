# TPED/TFAM
Another possible file-format called a transposed fileset, containing two text files: one (TPED) containing SNP and genotype information where one row is a SNP; one (TFAM) containing individual and family information, where one row is an individual.
The first 4 columns of a TPED file are the same as a standard 4-column MAP file. Then all genotypes are listed for all individuals for each particular SNP on each line. The TFAM file is just the first six columns of a standard PED file. In otherwords, we have just taken the standard PED/MAP file format, but swapped all the genotype information between files, after rotating it 90 degrees. For each, the above example PED/MAP fileset
```
     <---- normal.ped ---->                  <--- normal.map --->
     1 1 0 0 1  1  A A  G T                  1  snp1   0  5000650
     2 1 0 0 1  1  A C  T G                  1  snp2   0  5000830
     3 1 0 0 1  1  C C  G G
     4 1 0 0 1  2  A C  T T
     5 1 0 0 1  2  C C  G T
     6 1 0 0 1  2  C C  T T
```

would be represented as TPED/TFAM files:
```
     <------------- trans.tped ------------->      <- trans.tfam ->
     1 snp1 0 5000650 A A A C C C A C C C C C      1  1  0  0  1  1
     1 snp2 0 5000830 G T G T G G T T G T T T      2  1  0  0  1  1
                                                   3  1  0  0  1  1
                                                   4  1  0  0  1  2
                                                   5  1  0  0  1  2
                                                   6  1  0  0  1  2
```

This kind of format can be convenient to work with when there are very many more SNPs than individuals (i.e. WGAS data). In this case, the TPED file will be very long (as opposed to the PED file being very wide).

For more information, please refer to http://pngu.mgh.harvard.edu/~purcell/plink/data.shtml 


