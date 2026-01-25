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
```bash
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
```
Example of tabular format:
```bash
head -20 test.fna.blast
```
```bash
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
```
## EX4: Are there differences in the results retrieved in both searches?

To answer this, we need to compare the tabular files already created in Exe2 (test.faa.blast and test.fna.blast). 
```bash
head -n 5 test.faa.blast test.fna.blast
```
As showen below, if we looked at the second column, that these 5 first hits are the same for the both searches. Which is normal since the DNA (test.fna file) codes for the exact same protein as the protein file (test.faa). 
However, there some differnces due the file type (DNA or Protein). The query coordinates in columns  7 and 8, shows that for protein, the alignment ends  at position 935 Amino Acids, and for nucleotides at 2805, which is 3 times 935 because each amino acid is made of 3 nucleotides (a codon). Moreover, the scoring (column 12) shows that the top hit for blastp has a bit score of 1915 and a bit score of 1706 for blastx 
```bash
==> test.faa.blast <==
AT1G30330.2     sp|Q9ZTX8|ARFF_ARATH    100.000 935     0       0       1       935     1       935     0.0     1915
AT1G30330.2     sp|Q9FGV1|ARFH_ARATH    55.667  900     284     20      1       888     1       797     0.0     850
AT1G30330.2     sp|Q8RYC8|ARFS_ARATH    65.116  430     132     10      1       422     1       420     2.97e-174      534
AT1G30330.2     sp|Q8RYC8|ARFS_ARATH    48.889  135     67      1       776     910     938     1070    5.47e-32       134
AT1G30330.2     sp|P93022|ARFG_ARATH    64.871  427     132     10      4       422     5       421     1.23e-169      524

==> test.fna.blast <==
AT1G30330.2     sp|Q9ZTX8|ARFF_ARATH    100.000 935     0       0       1       2805    1       935     0.0     1706
AT1G30330.2     sp|Q9FGV1|ARFH_ARATH    75.584  471     100     4       1       1392    1       463     0.0     699
AT1G30330.2     sp|Q9FGV1|ARFH_ARATH    48.198  222     92      8       2020    2664    592     797     1.05e-43       170
AT1G30330.2     sp|Q8RYC8|ARFS_ARATH    65.116  430     132     10      1       1266    1       420     2.38e-170      527
AT1G30330.2     sp|Q8RYC8|ARFS_ARATH    48.889  135     67      1       2326    2730    938     1070    1.48e-31       132
```
## EX5: Can you explain the contents of the output file profile.out?
```bash
psiblast -db uniprot_Atha.fasta -query test.faa -num_iterations 3 -out_ascii_pssm profile.out
```
The profile.out file contains the PSSM (Position-Specific Scoring Matrix). Unlike standard BLAST, which uses a fixed scoring matrix (like BLOSUM62) for the entire sequence, this PSSM assigns a unique score to every position. 
For example if we look at the first row of the matrix and at the column for M (Methionine). It has a score of 6, which is a high positive score. It means that at position 1, being a Methionine is "good" and expected. In contrast, if we look at the column for D (Aspartic Acid). It has a score of -3, which means that replacing the Methionine with Aspartic Acid is evolutionarily "bad".
This shows a part of the matrix in the profile.out file:
```bash
Last position-specific scoring matrix computed, weighted observed percentages rounded down, information per position, and relative weight of gapless real matches to pseudocounts
            A   R   N   D   C   Q   E   G   H   I   L   K   M   F   P   S   T   W   Y   V   A   R   N   D   C   Q   E   G   H   I   L   K   M   F   P   S   T   W   Y   V
    1 M    -1  -1  -2  -3  -2  -1  -2  -3  -2   1   2  -1   6   0  -3  -2  -1  -2  -1   1    0   0   0   0   0   0   0   0   0   0   0   0 100   0   0   0   0   0   0   0  0.39 0.01
    2 R    -1   3   0  -1  -3   1   1  -2  -1  -3  -2   4  -1  -3  -1   0  -1  -3  -2  -2    0  25   0   0   0   0   0   0   0   0   0  75   0   0   0   0   0   0   0   0  0.53 0.01
    3 L     2  -2  -2  -3  -1  -1  -2  -2  -2   1   2  -2   3   0  -2  -1  -1  -2  -1   0   35   0   0   0   0   0   0   0   0   0  35   0  30   0   0   0   0   0   0   0  0.20 0.01
    4 S     0  -1   0   0  -2   0   1  -1  -1  -2  -3   0  -2  -3   3   3   2  -3  -2  -2    0   0   0   0   0   0  14   0   0   0   0   0   0   0  20  54  12   0   0   0  0.47 0.02
    5 S     0  -1   2  -1  -2  -1  -1   4  -1  -3  -3  -1  -2  -3  -2   2   1  -3  -2  -2    0   0  14   0   0   0   0  45   0   0   0   0   0   0   0  30  11   0   0   0  0.46 0.01
    6 A     0  -1   5   1  -2   0   0   0   0  -3  -3   0  -2  -3  -2   1   0  -4  -2  -3   10   0  79   0   0   0   0   0   0   0   0   0   0   0   0  11   0   0   0   0  0.60 0.03
    7 G     0  -3  -1  -2  -2  -2  -2   4  -3   1  -1  -2  -1  -2  -2  -1  -1  -3  -2   2    0   0   0   0   0   0   0  55   0  12   0   0   0   0   0   0   0   0   0  32  0.40 0.02
    8 F    -1  -2  -3  -3  -1  -2  -3  -3  -3   2   1  -2   2   3  -3  -2  -1  -1   0   3    0   0   0   0   0   0   0   0   0   0  11   0  14  20   0   0   0   0   0  56  0.27 0.02
    9 N    -1  -1   5   1  -2   0  -1   1   0  -2  -1  -1  -1  -3  -2   1   0  -3  -2  -2    0   0  68   0   0   0   0  11   0   0  10   0   0   0   0  11   0   0   0   0  0.46 0.02
   10 P     2  -2  -2  -2  -2   1  -1  -1  -2  -1  -2  -1  -1  -3   5   0   0  -3  -2   0   37   0   0   0   0   9   0   0   0   0   0   0   0   0  42   0   5   0   0   7  0.68 0.03
   11 Q     0   0   1   0  -2   5   1  -1   0  -3  -3   1  -1  -3  -1   2   0  -2  -2  -2    0   0   9   0   0  67   0   0   0   0   0   0   0   0   0  25   0   0   0   0  0.52 0.04
   12 P     1  -2  -1  -1  -2  -1  -1   1  -2  -3  -3  -1  -2  -3   6   1  -1  -3  -3  -2   17   0   0   0   0   0   0   9   0   0   0   0   0   0  60  15   0   0   0   0  1.08 0.03
   13 H    -1   0   1   1  -3   1   3  -2   3  -2  -2   1  -2  -2  -1   0   1  -3  -1  -2    1   0   8   0   0   0  45   1  17   0   1   6   0   0   0   1  17   0   0   1  0.35 0.02
```
## EX6:
### Create a FASTA file with the complete protein sequences of the matches of your protein search with bit score > 200. You might find one-liners useful for this.
```bash
awk '$12 > 200 {print $2}' test.faa.blast | sort -u | blastdbcmd -db uniprot_Atha.fasta -entry_batch - -out high_score_hits.fasta
```
This shows an error in the terminal. The issue goes back to the blast command run in Exercise 4.1.1 that needs the -parse_seqids flag because without it BLAST creates a simple database where it doesn't "understand" the complex ID structure (like sp|Q9ZTX8|...).

Thus before running the previuos command, we ran the following code:
```bash
makeblastdb -dbtype prot -in uniprot_Atha.fasta -parse_seqids
```
to confirm the file isn't empty:
```bash
ls -sh high_score_hits.fasta
```
The file looks:
```bash
>O23661 Auxin response factor 3 OS=Arabidopsis thaliana OX=3702 GN=ARF3 PE=1 SV=2
MGGLIDLNVMETEEDETQTQTPSSASGSVSPTSSSSASVSVVSSNSAGGGVCLELWHACAGPLISLPKRGSLVLYFPQGH
LEQAPDFSAAIYGLPPHVFCRILDVKLHAETTTDEVYAQVSLLPESEDIERKVREGIIDVDGGEEDYEVLKRSNTPHMFC
KTLTASDTSTHGGFSVPRRAAEDCFPPLDYSQPRPSQELLARDLHGLEWRFRHIYRGQPRRHLLTTGWSAFVNKKKLVSG
DAVLFLRGDDGKLRLGVRRASQIEGTAALSAQYNQNMNHNNFSEVAHAISTHSVFSISYNPKASWSNFIIPAPKFLKVVD
YPFCIGMRFKARVESEDASERRSPGIISGISDLDPIRWPGSKWRCLLVRWDDIVANGHQQRVSPWEIEPSGSISNSGSFV
TTGPKRSRIGFSSGKPDIPVSEGIRATDFEESLRFQRVLQGQEIFPGFINTCSDGGAGARRGRFKGTEFGDSYGFHKVLQ
GQETVPAYSITDHRQQHGLSQRNIWCGPFQNFSTRILPPSVSSSPSSVLLTNSNSPNGRLEDHHGGSGRCRLFGFPLTDE
TTAVASATAVPCVEGNSMKGASAVQSNHHHSQGRDIYAMRDMLLDIAL
>P93022 Auxin response factor 7 OS=Arabidopsis thaliana OX=3702 GN=ARF7 PE=1 SV=2
MKAPSSNGVSPNPVEGERRNINSELWHACAGPLISLPPAGSLVVYFPQGHSEQVAASMQKQTDFIPSYPNLPSKLICMLH
NVTLNADPETDEVYAQMTLQPVNKYDRDALLASDMGLKLNRQPNEFFCKTLTASDTSTHGGFSVPRRAAEKIFPALDFSM
QPPCQELVAKDIHDNTWTFRHIYRGQPKRHLLTTGWSVFVSTKRLFAGDSVLFIRDGKAQLLLGIRRANRQQPALSSSVI
SSDSMHIGVLAAAAHANANNSPFTIFYNPRAAPAEFVVPLAKYTKAMYAQVSLGMRFRMIFETEECGVRRYMGTVTGISD
LDPVRWKNSQWRNLQIGWDESAAGDRPSRVSVWDIEPVLTPFYICPPPFFRPRFSGQPGMPDDETDMESALKRAMPWLDN
SLEMKDPSSTIFPGLSLVQWMNMQQQNGQLPSAAAQPGFFPSMLSPTAALHNNLGGTDDPSKLLSFQTPHGGISSSNLQF
NKQNQQAPMSQLPQPPTTLSQQQQLQQLLHSSLNHQQQQSQSQQQQQQQQLLQQQQQLQSQQHSNNNQSQSQQQQQLLQQ
QQQQQLQQQHQQPLQQQTQQQQLRTQPLQSHSHPQPQQLQQHKLQQLQVPQNQLYNGQQAAQQHQSQQASTHHLQPQLVS
GSMASSVITPPSSSLNQSFQQQQQQSKQLQQAHHHLGASTSQSSVIETSKSSSNLMSAPPQETQFSRQVEQQQPPGLNGQ
NQQTLLQQKAHQAQAQQIFQQSLLEQPHIQFQLLQRLQQQQQQQFLSPQSQLPHHQLQSQQLQQLPTLSQGHQFPSSCTN
NGLSTLQPPQMLVSRPQEKQNPPVGGGVKAYSGITDGGDAPSSSTSPSTNNCQISSSGFLNRSQSGPAILIPDAAIDMSG
NLVQDLYSKSDMRLKQELVGQQKSKASLTDHQLEASASGTSYGLDGGENNRQQNFLAPTFGLDGDSRNSLLGGANVDNGF
VPDTLLSRGYDSQKDLQNMLSNYGGVTNDIGTEMSTSAVRTQSFGVPNVPAISNDLAVNDAGVLGGGLWPAQTQRMRTYT
KVQKRGSVGRSIDVNRYRGYDELRHDLARMFGIEGQLEDPQTSDWKLVYVDHENDILLVGDDPWEEFVNCVQSIKILSSA
EVQQMSLDGNFAGVPVTNQACSGGDSGNAWRGHYDDNSATSFNR
```
### Compute a multiple alignment of these sequences with Clustal Omega. Check the available output formats:
```bash
clustalo -i high_score_hits.fasta -o aligned_sequences.sto --outfmt=st
```
```bash
#=GS O23661 DE    Auxin response factor 3 OS=Arabidopsis thaliana OX=3702 GN=ARF3 PE=1 SV=2
#=GS P93022 DE    Auxin response factor 7 OS=Arabidopsis thaliana OX=3702 GN=ARF7 PE=1 SV=2
#=GS P93024 DE    Auxin response factor 5 OS=Arabidopsis thaliana OX=3702 GN=ARF5 PE=1 SV=3
#=GS Q84WU6 DE    Auxin response factor 17 OS=Arabidopsis thaliana OX=3702 GN=ARF17 PE=2 SV=1
#=GS Q8L7G0 DE    Auxin response factor 1 OS=Arabidopsis thaliana OX=3702 GN=ARF1 PE=1 SV=2
#=GS Q8RYC8 DE    Auxin response factor 19 OS=Arabidopsis thaliana OX=3702 GN=ARF19 PE=1 SV=2
#=GS Q93YR9 DE    Auxin response factor 16 OS=Arabidopsis thaliana OX=3702 GN=ARF16 PE=1 SV=1
#=GS Q94JM3 DE    Auxin response factor 2 OS=Arabidopsis thaliana OX=3702 GN=ARF2 PE=1 SV=2
#=GS Q9C5W9 DE    Auxin response factor 18 OS=Arabidopsis thaliana OX=3702 GN=ARF18 PE=1 SV=1
#=GS Q9C7I9 DE    Auxin response factor 20 OS=Arabidopsis thaliana OX=3702 GN=ARF20 PE=2 SV=3
#=GS Q9C8N7 DE    Auxin response factor 22 OS=Arabidopsis thaliana OX=3702 GN=ARF22 PE=2 SV=2
#=GS Q9C8N9 DE    Putative auxin response factor 21 OS=Arabidopsis thaliana OX=3702 GN=ARF21 PE=3 SV=2
#=GS Q9FGV1 DE    Auxin response factor 8 OS=Arabidopsis thaliana OX=3702 GN=ARF8 PE=1 SV=2
#=GS Q9FX25 DE    Auxin response factor 13 OS=Arabidopsis thaliana OX=3702 GN=ARF13 PE=2 SV=3
#=GS Q9LQE3 DE    Putative auxin response factor 15 OS=Arabidopsis thaliana OX=3702 GN=ARF15 PE=3 SV=2
#=GS Q9LQE8 DE    Putative auxin response factor 14 OS=Arabidopsis thaliana OX=3702 GN=ARF14 PE=3 SV=2
#=GS Q9SKN5 DE    Auxin response factor 10 OS=Arabidopsis thaliana OX=3702 GN=ARF10 PE=2 SV=1
#=GS Q9XED8 DE    Auxin response factor 9 OS=Arabidopsis thaliana OX=3702 GN=ARF9 PE=1 SV=1
#=GS Q9XID4 DE    Auxin response factor 12 OS=Arabidopsis thaliana OX=3702 GN=ARF12 PE=2 SV=2
#=GS Q9ZPY6 DE    Auxin response factor 11 OS=Arabidopsis thaliana OX=3702 GN=ARF11 PE=2 SV=3
#=GS Q9ZTX8 DE    Auxin response factor 6 OS=Arabidopsis thaliana OX=3702 GN=ARF6 PE=1 SV=2
#=GS Q9ZTX9 DE    Auxin response factor 4 OS=Arabidopsis thaliana OX=3702 GN=ARF4 PE=1 SV=1

O23661  ---------MGGLIDLNVMETEEDETQTQTPS--------SA--------
P93022  --------------------------------------------------
P93024  --------------MMASLSCVEDKMKTSCLVNGGGTITTTTSQSTL---
Q84WU6  --------------------------------------------------
Q8L7G0  --------------------------------------------------
Q8RYC8  --------------------------------------------------
Q93YR9  --------------------------------------------------
Q94JM3  ---------------MASSEVS-------MKGNRGGDNFSSSGFSDPKET
Q9C5W9  -----------------------------MASVEGDDDFGS---------
Q9C7I9  --------------------------------------------------
Q9C8N7  --------------------------------------------------
Q9C8N9  --------------------------------------------------
Q9FGV1  --------------------------------------------------
Q9FX25  --------------------------------------------------
Q9LQE3  --------------------------------------------------
```
### Build a HMM out of these aligned sequences with hmmbuild:
```bash
hmmbuild ARF_profile.hmm aligned_sequences.sto
```
### Scan the HMM against your sequence collection with hmmerscan and write a short report on the results. This should be deliverable Exe6:
```bash
hmmsearch --tblout exe6_report.txt ARF_profile.hmm uniprot_Atha.fasta
```

Summary: 

A Profile Hidden Markov Model (HMM) was constructed using the aligned sequences of high-scoring BLAST hits (Bit score > 200). This model was then used to scan the complete Arabidopsis thaliana proteome (15,719 sequences) using hmmsearch. The HMM search identified 74 significant hits (proteins) belonging to this family. The top hits correspond to known Auxin Response Factors (ARFs) with extremely high bit scores. The search successfully detected more distant relatives (such as B3 domain-containing proteins) that might share structural features despite lower sequence identity. This demonstrates the superior sensitivity of HMMs compared to single-sequence BLAST searches for detecting full protein families.
## EX7: Produce a table with i) domains defined by the boundaries of matched entries from the Protein Data Bank and Pfam and ii) similar sequences in AlphaFoldDB.
To resolve this questions, i asked Gemini to explain for me first some concepts that i didn't get well, difference between PDB and Pfam, the boundaries, the AlphaFoldDB. and then i asked him to give me the steps to use the websites needed. When i got the results on the website, i was confused about the examples to choose, is it based on the probability or the E value or... so based on the explanation gave by the AI, I chose the examples based on coverage of the entire protein, not just the lowest E value. If I only selected the hits with the "best" (lowest) E-values, I would have listed five identical copies of the start of the protein and completely missed the rest. I chose the absolute best match (4LDU). I chose the best available matches for those specific regions (PF06507 and 6L5K), even though their E-values were slightly higher, to ensure your table described the full length of the protein.

| Category | Database Source | Hit ID / Accession | Description / Function | Boundaries / Identity |
| :--- | :--- | :--- | :--- | :--- |
| **i) Domains** | **PDB** (via HHPred) | **4LDU_A** | Auxin Response Factor 5 (DNA Binding) | Residues **16 – 363** |
| | **Pfam** (via HHPred) | **PF02362** (B3) | B3 DNA Binding Domain | Residues **129 – 208** |
| | **Pfam** (via HHPred) | **PF06507** (ARF_AD) | ARF Ancillary Domain | Residues **278 – 357** |
| | **PDB** (via HHPred) | **6L5K_A** | Auxin Response Factor 5 (PB1 / Oligomerization) | Residues **793 – 888** |
| | **Pfam** (via HHPred) | **PF02309** (AUX_IAA) | AUX/IAA Family (PB1 domain) | Residues **795 – 854** |
| **ii) Similar Seqs** | **AlphaFoldDB** | **Q9ZTX8** | Auxin Response Factor 6 (*Arabidopsis thaliana*) | **100% Identity** |
| | **AlphaFoldDB** | **Q6H6V4** | Auxin Response Factor 6 (*Oryza sativa*) | **63.0% Identity** |
| | **AlphaFoldDB** | **Q653U3** | Auxin Response Factor 17 (*Oryza sativa*) | **62.6% Identity** |

## EX9
In this exercise we will use the GO-web browser QuickGo as it is an intuitive and weekly updated resource. Although we won’t be using them in this session, there are many other related tools out there, such as UniProt or Ensembl Plants.

The goal of this task is to learn how to: - Search for GO annotations using different inputs (protein IDs, gene IDs and GO terms). - Search for all products annotated to specific GO term or GO ID. - Customize the research to better fit the user preferences.
### Search for the GO terms and the functional categories of the following GO IDs GO:0009414, GO:0035618, GO:0016491. Tip : For multiple search GO IDs needs to be separated by a space.
GO:0016491 : oxidoreductase activity (Category: Molecular Function, marked with an F)

GO:0035618 : root hair (Category: Cellular Component, marked with a C)

GO:0009414 : response to water deprivation (Category: Biological Process, marked with a P)
### What are the GO ID and the functional category corresponding to photosynthesis?
GO ID: GO:0015979 

Functional Category: Biological Process.


### What are the immediate parent(s) and children of the photosynthesis GO term?
Immediate Parent: metabolic process (GO:0008152).
Immediate Children:
   photosynthesis, light reaction (GO:0019684) 
   photosynthesis, dark reaction (GO:0019685) 
   regulation of photosynthesis (GO:0010109)
   photosystem (GO:0009521)
   negative regulation of photosynthesis	(GO:1905156)
   positive regulation of photosynthesis (GO:1905157)
   photosynthetic membrane (GO:0034357)
### Search for the GO annotation terms of the following protein A0A068LKP4,A0A097PR28, A0A059Q6N8? What do you observe?
A0A068LKP4
   Name: RPW8 domain-containing protein
   Organism (Taxon): Arabidopsis thaliana (Thale cress)

A0A097PR28
   Name: General transcription factor IIH subunit 2
   Organism (Taxon): Prunus persica (Peach)

A0A059Q6N8
   Name: Photosystem II reaction center protein M
   Organism (Taxon): Zea mays subsp. mays (Corn/Maize)

We observe that all the three proteins come from the Plant Kingdom (Viridiplantae), but they are from three different species (Arabidopsis, Peach, and Maize) and perform different functions (Defense/Resistance, Transcription, and Photosynthesis).This demonstrates that Gene Ontology (GO) allows scientists to compare biology between different types of plants.

### How many gene products are involved in leaf development? Give the GO ID corresponding to this term.
The results show 21,805 annotations to 21,009 distinct gene products.

Leaf development: GO:0048366
### How many proteins of Arabidopsis thaliana, Prunus perisca and Zea mays are assigned to the leaf development GO term. Tip : Zea mays. Taxonomy ID=4577
   Arabidopsis thaliana: 638 annotations
   Prunus perisca: 59 annotations
   Zea mays: 178 annotations

### Check the total number of BP annotations and proteins supported by the experimental evidence codes in both Arabidopsis thaliana and Prunus persica. (see the evidence codes) Tip : check the ‘Statistics’ box.
   Arabidopsis thaliana: 423 annotations to 332 distinct gene products
   Prunus perisca: No matching annotations have been found
