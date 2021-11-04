# Clumping and thresholding

### Commands
`plink --bfile <bfile> --clumping <summary_statistics_file> --clump-r2 <r2 column index> --clump-field <p-value column index> --clump-snp-field <rsID column index> --allow-extra-chr` <br> 
  
### Notes
  - thresholding sort snps based on pvalue threshold
  - clumping, look at the correlation of SNps within  certain distance
