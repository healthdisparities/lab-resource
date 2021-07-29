# VCF File Format
VCF is a text file format (most likely stored in a compressed manner). It contains meta-information lines, a header line, and then data lines containing information about a position in the genome.

There is an option whether to contain genotype information on samples for each position or not.
Example:
```
##fileformat=VCFv4.1
##fileDate=20090805
##source=myImputationProgramV3.1
##reference=file:///seq/references/1000GenomesPilot-NCBI36.fasta
##contig=
##phasing=partial
##INFO=
##INFO=
##INFO=
##INFO=
##INFO=
##INFO=
##FILTER=
##FILTER=
##FORMAT=
##FORMAT=
##FORMAT=
##FORMAT=
#CHROM POS     ID        REF    ALT     QUAL FILTER INFO                              FORMAT      NA00001        NA00002        NA00003
2014370rs6054257 GA29PASSNS=3;DP=14;AF=0.5;DB;H2GT:GQ:DP:HQ 0|0:48:1:51,51 1|0:48:8:51,51 1/1:43:5:.,.
2017330.TA3q10NS=3;DP=11;AF=0.017GT:GQ:DP:HQ 0|0:49:3:58,50 0|1:3:5:65,30/0:41:3
201110696 rs6040355 AG,T67PASSNS=2;DP=10;AF=0.333,0.667;AA=T;DB GT:GQ:DP:HQ 1|2:21:6:23,27 2|1:2:0:18,22/2:35:4
201230237 .T.47PASSNS=3;DP=13;AA=TGT:GQ:DP:HQ 0|0:54:7:56,60 0|0:48:4:51,51 0/0:61:2
201234567 microsat1 GTCG,GTCT50PASSNS=3;DP=9;AA=GGT:GQ:DP0/1:35:40/2:17:21/1:40:3
```

## Meta information lines
File meta-information is included after the ## string and must be key=value pairs.
A single 'fileformat' field is always required, must be the first line in the file, and details the VCF format version number. For example, for VCF version 4.1, this line should read:

> ##fileformat=VCFv4.1

It is strongly encouraged that information lines describing the INFO, FILTER and FORMAT entries used in the body of the VCF file be included in the meta-information section. Although they are optional, if these lines are present then they must be completely well-formed.

INFO fields should be described as follows (all keys are required):

> ##INFO=

Possible Types for INFO fields are: Integer, Float, Flag, Character, and String.

The Number entry is an Integer that describes the number of values that can be included with the INFO field. For example, if the INFO field contains a single number, then this value should be 1; if the INFO field describes a pair of numbers, then this value should be 2 and so on. If the field has one value per alternate allele then this value should be 'A'; if the field has one value for each possible genotype (more relevant to the FORMAT tags) then this value should be 'G'. If the number of possible values varies, is unknown, or is unbounded, then this value should be '.'. The 'Flag' type indicates that the INFO field does not contain a Value entry, and hence the Number should be 0 in this case. The Description value must be surrounded by double-quotes. Double-quote character can be escaped with backslash (\") and backslash as \\.

FILTERs that have been applied to the data should be described as follows:

> ##FILTER=

Likewise, Genotype fields specified in the FORMAT field should be described as follows:

> ##FORMAT=

## Header line

The header line names the 8 fixed, mandatory columns. These columns are as follows:
```
#CHROM
POS
ID
REF
ALT
QUAL
FILTER
INFO
```
If genotype data is present in the file, these are followed by a FORMAT column header, then an arbitrary number of sample IDs. The header line is tab-delimited.

## Data lines
There are 8 fixed fields per record. All data lines are tab-delimited. In all cases, missing values are specified with a dot (”.”). Each column has been listed above.


Taken and modified from http://www.1000genomes.org/wiki/Analysis/Variant%20Call%20Format/vcf-variant-call-format-version-41 
