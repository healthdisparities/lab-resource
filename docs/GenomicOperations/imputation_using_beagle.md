# Imputation with Beagle

Imputation is the process of inferring missing genotypes in an assay from a haplotype panel or reference panel. One tool for imputation is Beagle. 

#### Input files

- phased input VCF
- reference `bref` file
- genetic map file

#### Command
`java -Xss5m -Xmx16g -jar ~/bin/beagle.27Jan18.7e1.jar 
gt=chr1_phased.vcf.gz 
ref=chr1_1000GP_reference.bref 
map=chr1_beagle_b38.map 
out=chr1_imputed nthreads=16 niterations=10 
ne=20000 impute=true gprobs=true seed=-99999`
