# Session 1

## EX1: How many sequences have been formatted and how does this affect the E-value of BLAST searches?

```bash
makeblastdb -dbtype prot -in uniprot_Atha.fasta
```
The total number of Sequences Formatted is 15,719.
The E-value (Expect value) represents the number of hits you can expect to find by pure chance.
If the number of sequences is high like our case, the number of matches you can expect to happen by chance increase so a high E-value, which is the contrary with few number of sequences where an obtained match would be hardly due to chance.
## EX2: Can you redirect the output to separate files called test.faa.blast and test.fna.blast?

Yes. In the command line, we can use the standard shell redirection (>) :
```bash
blastp -db uniprot_Atha.fasta -query test.faa -outfmt 6> test.faa.blast
blastx -db uniprot_Atha.fasta -query test.fna -outfmt 6 > test.fna.blast
```
And like this we saved the outputs of the blastp and blastx into two differents files.
## EX3: What is the default alignment format, can you show an example?
In the previous command we used -outfmt 6, which is Tabular format. However, if we remove the -outfmt flag entirely, the default format for BLAST+ is Pairwise (Format 0). 
```bash
blastp -db uniprot_Atha.fasta -query test.faa
blastx -db uniprot_Atha.fasta -query test.fna 
```
Example of default format:
>Q9ZTX8 Auxin response factor 6 OS=Arabidopsis thaliana OX=3702 GN=ARF6
PE=1 SV=2
Length=935

 Score = 1915 bits (4962),  Expect = 0.0, Method: Compositional matrix adjust.
 Identities = 935/935 (100%), Positives = 935/935 (100%), Gaps = 0/935 (0%)

Query  1    MRLSSAGFNPQPHEVTGEKRVLNSELWHACAGPLVSLPPVGSRVVYFPQGHSEQVAASTN  60
            MRLSSAGFNPQPHEVTGEKRVLNSELWHACAGPLVSLPPVGSRVVYFPQGHSEQVAASTN
Sbjct  1    MRLSSAGFNPQPHEVTGEKRVLNSELWHACAGPLVSLPPVGSRVVYFPQGHSEQVAASTN  60

Query  61   KEVDAHIPNYPSLHPQLICQLHNVTMHADVETDEVYAQMTLQPLNAQEQKDPYLPAELGV  120
            KEVDAHIPNYPSLHPQLICQLHNVTMHADVETDEVYAQMTLQPLNAQEQKDPYLPAELGV
Sbjct  61   KEVDAHIPNYPSLHPQLICQLHNVTMHADVETDEVYAQMTLQPLNAQEQKDPYLPAELGV  120

Example of tabular format:
```bash
head -20 test.fna.blast
```
AT1G30330.2     sp|Q9ZTX8|ARFF_ARATH    100.000 935     0       0       1       2805    1       935     0.0     1706
AT1G30330.2     sp|Q9FGV1|ARFH_ARATH    75.584  471     100     4       1       1392    1       463     0.0     699
AT1G30330.2     sp|Q9FGV1|ARFH_ARATH    48.198  222     92      8       2020    2664    592     797     1.05e-43       170
AT1G30330.2     sp|Q8RYC8|ARFS_ARATH    65.116  430     132     10      1       1266    1       420     2.38e-170      527
AT1G30330.2     sp|Q8RYC8|ARFS_ARATH    48.889  135     67      1       2326    2730    938     1070    1.48e-31       132
AT1G30330.2     sp|P93022|ARFG_ARATH    64.871  427     132     10      10      1266    5       421     6.79e-166      518
AT1G30330.2     sp|P93022|ARFG_ARATH    63.043  92      34      0       2389    2664    1038    1129    3.68e-30       128
AT1G30330.2     sp|P93024|ARFE_ARATH    62.078  385     141     3       55      1209    48      427     5.22e-154      479
AT1G30330.2     sp|P93024|ARFE_ARATH    49.635  137     66      1       2284    2685    756     892     5.56e-33       137
AT1G30330.2     sp|Q94JM3|ARFB_ARATH    55.710  359     155     4       61      1134    57      412     1.37e-122      395
AT1G30330.2     sp|Q94JM3|ARFB_ARATH    46.154  91      47      2       2383    2652    732     821     1.38e-17       87.4
AT1G30330.2     sp|Q8L7G0|ARFA_ARATH    53.930  369     161     6       61      1155    18      381     9.60e-119      379
AT1G30330.2     sp|Q8L7G0|ARFA_ARATH    33.962  106     68      2       2368    2682    536     640     2.55e-14       76.6
AT1G30330.2     sp|Q9ZTX9|ARFD_ARATH    52.105  380     161     8       64      1152    62      437     1.26e-114      371
AT1G30330.2     sp|Q9ZTX9|ARFD_ARATH    34.395  157     96      5       2227    2685    611     764     1.71e-18       90.1
AT1G30330.2     sp|Q9C5W9|ARFR_ARATH    48.883  403     188     11      64      1236    22      418     5.80e-108      348
AT1G30330.2     sp|Q9C5W9|ARFR_ARATH    38.835  103     60      2       2353    2661    480     579     9.54e-13       71.2
AT1G30330.2     sp|Q9ZPY6|ARFK_ARATH    51.852  351     160     7       64      1110    39      382     4.55e-107      346
AT1G30330.2     sp|Q9ZPY6|ARFK_ARATH    39.130  92      53      2       2395    2667    514     603     2.40e-12       70.1
AT1G30330.2     sp|O23661|ARFC_ARATH    47.558  389     180     8       73      1194    54      433     3.19e-101      330

