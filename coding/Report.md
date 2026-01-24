Session 1

EX 1

How many sequences have been formatted and how does this affect the E-value of BLAST searches?

```bash
makeblastdb -dbtype prot -in uniprot_Atha.fasta
```
# The total number of Sequences Formatted is 15,719.
The E-value (Expect value) represents the number of hits you can expect to find by pure chance.
If the number of sequences is high like our case, the number of matches you can expect to happen by chance increase so a high E-value, which is the contrary with few number of sequences where an obtained match would be hardly due to chance. 

Here is the code:

```bash
docker pull csicunam/bioinformatics_iamz:latest
