# Session 3: BY Fatima Zahra AMGHAR and Nesrine BEN RHOUMA

Based on the Practical_WGCNA_W_dataset.Rmd file codes:

## 3.1) How many samples & isoforms are included in TPM_counts_Drought_W_dataset.csv? 
There are 39 samples and 9,940 isoforms.
## 3.2) How many samples are discarded after outlier analysis? 
13 samples were discarded.

The original dataset had 39 samples. After clustering and applying a cutHeight of 300,000, the analysis kept 26 samples.

<img width="787" height="486" alt="image" src="https://github.com/user-attachments/assets/264e448e-059f-484e-baa8-a32fd0aaed1f" />

## 3.3) What power value have you set as appropriate for calculating adjacency? 
The power value set is 6.This was chosen because the Scale-free topology fit index (signed $R^2$) reaches the 0.85 threshold at this power level.

<img width="787" height="486" alt="image" src="https://github.com/user-attachments/assets/8475fc28-8173-4d9a-9bf1-07ccff12be7e" />

## 3.4) How many co-expression modules are established before and how many after the module merging process? 
Before merging: 40 original modules.


After merging: 36 merged modules.
## 3.5) What is the hub isoform (or hub gene) of the cyan module? 
The hub isoform for the cyan module is Bradi1g00700.3.
## 3.6) According to the module-trait association heat map, which module has the highest positive correlation with the "blwgrd (below ground biomass)" trait? 
