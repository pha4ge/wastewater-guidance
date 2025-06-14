**Case Study \#4 \- [Respiratory virus infection dynamics and genomic surveillance to detect seasonal influenza subtypes in wastewater: a longitudinal study in Bengaluru, India](https://www.medrxiv.org/content/10.1101/2025.01.13.25320458v1)**

The aim of the study was to track the prevalence and evolution of common respiratory viruses \[SARS Cov-2, Influenza and Respiratory Syncytial virus (RSV)\]  in longitudinal wastewater surveillance in Bengaluru, India, using both qPCR-based quantification and a combination of amplicon and metagenomic sequencing. 

**Surveillance Strategy/System Design:** 

* **Sampling location**: 28 sites within Bengaluru, India.  
* **Sampling site**: Influent wastewater from 28 centralized sewage treatment plants (STPs). Catchment area sizes: eight small (serving 10,000 − 60,000 people), nine medium (serving 100,000 – 119 350,000 people), and nine large (serving 400,000 − 2,480,000 people) STPs.  
* **Sampling frequency**: Monthly sampling for 28 months from August 2021 \- December 2023, between 08:00-14:00.  
* **Sample collection method:** Grab samples collected in 200 mL plastic bottles, tightly sealed upon collection, and stored at 124 4°C in the field.  
* **Reason for sampling method(s):** This was a cost-effective method for settings with limited resources and was carried out in partnership with researchers from the Bangalore Life Science Cluster and the local city utility or municipality.  
* **Detection & sequencing approach:**  RT-qPCR of SARS-CoV-2 (N-gene, RdRp-gene, and E-gene 140 and a human control gene (RNAase P gene) and Influenza-A (M gene), and Influenza-B (non-structural gene). For Influenza, also RT-qPCR using the CDC FluSC2 assay was used to distinguish between IAV and IBV or their subtypes  
  They also did metagenomic shotgun sequencing for Influenza, and targeted sequencing of SARS-CoV-2.   
* **How data will be used:** The sequencing data can supplement PCR-based test (which does not deal well with low viral load) to understand what pathogen is driving the seasonal illness patterns at a community level, and to therefore help with testing priorities and vaccination drives.

Data Analysis Approach:

* **Viral load modelling**: daily viral load was calculated for SARS-CoV-2, influenza A, influenza B, and RSV by normalizing the raw viral load to the average daily STP flow, using an equation, VL \= (C x Q x 10^3)/P, where VL \= viral load, C \= copies/ml, Q \= average daily STP flow, and P \= population within the catchment of the sewershed site. Associations between viral concentrations were measured using Kendall’s tau statistic.  
* **Influenza read processing and subtyping (first pipeline):** Trimmomatic (v.0.39), Kraken (v.2.1.3), Bowtie2 (v.2.2.5), and SAMtools coverage/bedcov were used for quality control and mapping to an influenza genome database ([https://ftp.ncbi.nih.gov/genomes/INFLUENZA/influenza.fna](https://ftp.ncbi.nih.gov/genomes/INFLUENZA/influenza.fna)). Sample metadata from NCBI was used to annotate putative subtypes.   
* **Influenza read processing and subtyping (second pipeline)**: iav\_serotype (v.0.1.4) used for read processing and subtyping using an average nucleotide identity (ANI) approach.  
* **SARS-CoV-2 variant detection**: raw reads aligned with the SARS-CoV-2 reference genome (MN908947) using BWA, followed by single nucleotide variant (SNV) calling with iVar (versions not specified).   
* **Lineage abundance:** Freyja (version and barcode file not specified)

**Data sharing strategy**: The preprint has a placeholder NCBI BioProject ID, suggesting that the authors plan to make the sequences publicly available eventually. The data availability statement indicated that consensus sequences from clinical surveillance are available on GISAID, but accession numbers are not included.