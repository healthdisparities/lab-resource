# Phasing with Eagle
Phasing is the process of inferring haplotypes from genotype data. One tool to do phasing is Eagle. 

#### Input files
- reference genome
- genetic map file

#### Command

`eagle --vcfTarget <chr1_input.vcf.gz> --vcfRef <chr1_reference.vcf.gz> --geneticMapFile <chr1_eagle_b38.map> --numThreads 8 --Kpbwt 20000 --outPrefix <chr1_phased>`


