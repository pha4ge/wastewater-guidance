![PHA4GE logo](../phage-logo-thin.png)
## **Guidance Document \- Wastewater Surveillance Data Analysis**

Working with wastewater pathogen concentration measurement and sequencing data can be challenging, but community resources are available for researchers with all levels of bioinformatics and data analysis experience. The following guidance document is primarily geared towards targeted (often capture probe or amplicon-based) sequencing of pathogens in wastewater, though we provide guidance for metagenomic analyses as well. 

To get started with analyzing your data, it may be helpful to first determine your level of experience and preferred computing environment. That is, if you are: 

1. Using existing bioinformatics pipelines (with command line experience)  
2. Using existing bioinformatics pipelines (for non-bioinformaticians)  
3. Doing custom pipeline development using existing tools  
4. Doing custom tool development for wastewater-based analyses

In this document we provide the necessary references and resources to get up and running while adhering to the current best practices for wastewater surveillance. 

**Using Community-supported Bioinformatics Pipelines (Scenario 1 and 2\)**  
Many widely used workflows are already publicly available and standardized for use by the broader public health research community, for bioinformatics experts and non-bioinformaticians alike. 

**Using existing community bioinformatics pipelines (Scenario 1\)**  
If you are comfortable running your own pipelines using tools such as Nextflow, snakemake, and/or bash, we recommend considering the following widely used approaches. 

**Official Public Health Institute tools**  
The following are workflows developed and employed by leading government agencies performing wastewater genomic surveillance, including US CDC. 

- [Aquascope](https://github.com/CDCgov/aquascope) is a “ bioinformatics best-practice pipeline for early detection of SARS-CoV-2 variants of concern, sequenced through shotgun metagenomic sequencing, from wastewater”, developed by the US CDC. The package does all necessary read alignment and trimming, quality control, and provides lineage prevalence estimates using Freyja. Aquascope supersedes the now deprecated C-WAP project. 

**STaPH-B Bioinformatic Toolkit**  
The state public health bioinformatics (STaPH-B) consortium is dedicated to providing easy access to open-source bioinformatic software, without the need for local management and installation of package dependencies. 

- [Cecret](https://github.com/UPHL-BioNGS/Cecret)  is an end-to-end workflow that can be customized to handle both clinical and wastewater SARS-CoV-2 sequencing data, originally developed by Erin Young (Utah PHL). Cecret accepts fastq inputs, performs alignment, trimming, consensus calling (not recommended in general for wastewater samples) and lineage prevalence inference with Freyja. Cecret is easily installed via the [staph-b toolkit](https://staphb.org/staphb_toolkit/), which provides a docker container that can be used to run the Nextflow pipeline.


  
**Nf-core**  
Nf-core ([https://nf-co.re/](https://nf-co.re/))  is a collection of community maintained bioinformatics pipelines developed using the Nextflow workflow language. Nextflow provides seamless integration with Docker, Singularity, Conda and other container solutions, allowing pipelines to be deployed to a variety of computational settings and maintain reproducible results. 

1. [nf-core/viralrecon](https://github.com/nf-core/viralrecon) is used for viral metagenomic sequencing to perform genome assembly and intrahost variant calling. The pipeline supports both Illumina and Nanopore sequencing data, typically obtained from shotgun sequencing (e.g. directly from clinical samples) or enrichment-based library preparation methods (e.g. amplicon-based: ARTIC SARS-CoV-2 enrichment protocol; or probe-capture-based).. For Nanopore data the pipeline only supports amplicon-based analysis obtained from primer sets created and maintained by the ARTIC Network. Certain steps (e.g. host read filtering, primer trimming) can be omitted, allowing the workflow to generalize well to different experimental approaches. Relevant to wastewater sequencing, viralrecon supports downstream analysis with Freyja.  
2. [nf-core/mag](https://nf-co.re/mag/3.0.2/) can be used to visualize the relative abundance of organisms in complex samples. It can use only short reads or a mixture of short and long reads to perform hybrid assembly.  
3. [nf-core/funcscan](https://nf-co.re/funcscan/1.1.6/)  is a bioinformatics analysis pipeline which currently features mining for antimicrobial peptides, antibiotic resistance genes and biosynthetic gene clusters. It performs the screening of contigs for antibiotic resistant gene-like sequences with ABRicate, AMRFinderPlus, fARGene, RGI, DeepARG.  
4. [nf-core/taxprofiler](https://github.com/nf-core/taxprofiler) is a bioinformatics best-practice analysis pipeline for taxonomic classification and profiling of shotgun short- and long-read metagenomic data. It allows for in-parallel taxonomic identification of reads or taxonomic abundance estimation with multiple classification and profiling tools against multiple databases, and produces standardised output tables for facilitating results comparison between different tools and databases.  
   

For more information on the specific tools being used within these pipelines, we recommend you check out the **Gold-Standard Methods for Wastewater Genomic Surveillance** section. 

**Resources for non-bioinformaticians (Scenario 2\)**  
If you are not interested in running your own analyses via the command line, you can still do the same analyses via drag and drop style web platforms. There are two commonly used platforms, Terra and Galaxy, each with their own advantages and disadvantages. 

1. [Galaxy](https://usegalaxy.org/) is an “open source, web-based platform for data intensive biomedical research”. Galaxy is entirely free to use and allows users to choose from a curated list of workflows, but jobs may queue for extended periods, and workflows are broken into individual steps.   
1. Quality control:   
   1.  The US FDA has prepared an open source [Wastewater QC workflow in GalaxyTrakr (SSQuAWK4)](https://www.protocols.io/view/wastewater-qc-workflow-in-galaxytrakr-ssquawk4-kxygxzk5dv8j/v9?step=6.2), available via protocols.io.   
   2. For more general quality control, we recommend [this tutorial](https://training.galaxyproject.org/training-material/topics/sequence-analysis/tutorials/quality-control/tutorial.html) from Batut et al. which provides step by step instructions and tips.   
2. Read alignment and trimming: A handful of tutorials exist for doing alignment and trimming in Galaxy. We recommend considering [this one](https://training.galaxyproject.org/training-material/topics/variant-analysis/tutorials/sars-cov-2-variant-discovery/tutorial.html) from Wolfgang Meier and Bérénice Batut.   
3. Lineage Prevalence Inference:   
   1. Freyja’s core variant calling ([variants](https://toolshed.g2.bx.psu.edu/repository/display_tool?repository_id=b19ef9d65efded99&tool_config=%2Fsrv%2Ftoolshed-repos%2Fmain%2F006%2Frepo_6312%2Ffreyja_variants.xml&changeset_revision=08c2d81e7942&render_repository_actions_for=tool_shed)) and deconvolution ([demix](https://toolshed.g2.bx.psu.edu/repository/display_tool?repository_id=931612620d3e0257&tool_config=%2Fsrv%2Ftoolshed-repos%2Fmain%2F006%2Frepo_6311%2Ffreyja_demix.xml&changeset_revision=c0a0e79d7196)) functions are available directly through Galaxy. 

      

2. [Terra](https://terra.bio/): Terra is a cloud computing platform that uses configurable workflow development language (WDL) workflows to perform end-to-end bioinformatic analyses. Workflows for use in Terra can be obtained freely via Dockstore, and is free to use for individuals, but cloud computing is performed via google cloud and can incur costs.  
1. [Freyja\_FASTQ](https://dockstore.org/workflows/github.com/theiagen/public_health_bioinformatics/Freyja_FASTQ_PHB:main?tab=info): End to end pipeline to perform lineage prevalence estimation for SARS-CoV-2.  
2. [Freyja\_Plot](https://dockstore.org/workflows/github.com/theiagen/public_health_bioinformatics/Freyja_Plot_PHB:main?tab=info): Plots outputs from Freyja FASTQ/demix

**Custom pipeline development using existing tools (Scenario 3\)**  
If you are building your own pipeline based on current state of the art tools, we recommend doing so with common pipeline tools such as Nextflow and snakemake. Both Nextflow and snakemake contain standalone modules,  which can be used to execute individual processing steps. For Nextflow, [nf-core/modules](https://nf-co.re/modules/) contains a large collection of standalone modules (i.e. workflow steps) used in other publicly available nf-core pipelines. This resource can serve as a useful starting point for building custom analysis pipelines tailored to your specific needs.

**Gold-Standard Methods for Wastewater Genomic Surveillance**  
Depending on the sequencing approach used, researchers and practitioners should select the appropriate data processing and analyses to characterize their samples. The following are our recommended practices for analyses of targeted (e.g., amplicon-based sequencing) and non-targeted sequencing data (e.g. shotgun metagenomic sequencing). 

**Data Pre-Processing Guidelines**  
Quality Assessment and Control: Since the quality of raw sequencing data is extremely important in downstream wastewater sequencing data analyses, we strongly recommend evaluating read quality before performing any analyses. Read quality assessment should be performed regardless of the sample type, with a particular focus on mean per base quality score across reads, mean and standard deviation of the read length. For SARS-CoV-2, PHA4GE has provided some basic quality [guidelines](https://pha4ge.org/resource/qc-solutions-for-sars-cov-2-genomic-analysis/) for sequencing data, which can be calculated using tools including FastQC and samtools. We note however that these QC parameters may not be appropriate for all sequencing platforms, samples, and pathogens, especially when considering pathogens like bacteria with large genomes.

* Read quality assessment:   
  FastQC can be used to measure the quality of the sequencing reads with both CLI and GUI options through Conda and Galaxy. You may find examples of good and bad quality reports for Illumina reads [here](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/).  
* PCR primer, sequencing adapter trimming:  
  Once the read quality is assessed, users should make sure to trim PCR primers and sequencing adapters with lower quality since these sequences have higher error rates. For trimming primers, tools such as iVar can be used by simply providing a primer bed file. It is available both through Conda and Galaxy and more information on iVar can be found [here](https://andersen-lab.github.io/ivar/html/manualpage.html). To remove sequencing adapters and remove the contaminations, Bbduk can be used.  It is available both on Conda and Galaxy, for more information read [this](https://jgi.doe.gov/data-and-tools/software-tools/bbtools/bb-tools-user-guide/bbduk-guide/).   
* Implications and approaches needed for lower quality/higher error rate data

**Lineage Prevalence Inference Methods**  
A handful of methods are used for the inference of lineage prevalence from wastewater sequencing data. Of these, Freyja is field standard and is the most widely used. We provide a description of each of the most commonly employed approaches in the field here, along with links to relevant papers and package repositories. To examine the differences between these methods we recommend considering ([Sutcliffe et al. 2024](https://doi.org/10.1099/mgen.0.001249); [Ferdous et al. 2024](https://doi.org/10.1016/j.scitotenv.2024.174515); [Kayikcioglu et al. 2023](https://doi.org/10.7717/peerj.14596)). 

* Viral lineage quantification(VLQ)[(Baaijens et al. 2021\)](https://doi.org/10.1101/2021.08.31.21262938): A RNA transcript quantification method leveraging multi-lineage references using Kallisto transcript abundance quantification program. More information found in the [publication](https://link.springer.com/article/10.1186/s13059-022-02805-9) and the GitHub [repository](https://github.com/baymlab/wastewater_analysis), and a nextflow pipeline for VLQ is available [here](https://github.com/rki-mf1/vlq-nf).  
* Freyja[(Karthikeyan et al. 2022\)](https://www.nature.com/articles/s41586-022-05049-6): A depth-weighted demixing method used to quantify lineage abundance in wastewater samples. Used in most standard wastewater analysis pipelines, including Aquascope and Cecret. More information can be found in the [publication](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8996633/) and the GitHub [repository](https://github.com/andersen-lab/Freyja) and associated [documentation](https://andersen-lab.github.io/Freyja/index.html#).    
* V-pipe/lollipop: A Kernel-based deconvolution method taking time series nature of samples into account. More information can be found in the [publication](https://www.medrxiv.org/content/10.1101/2022.11.02.22281825v1) and the GitHub [repository](https://github.com/cbg-ethz/LolliPop).  
* Other methods including Alcov, Gromstole, Lineagespot, and LCS may also present some advantages, but are not in widespread use. 

**Detection of novel haplotypes**  
Physical linkage of mutations can be used to detect novel or rare haplotypes. Two methods are currently available for doing this: 

1. [Crykey](https://www.nature.com/articles/s41467-024-48334-w) screens for rare linked mutations using a static database of observed SARS-CoV-2 genomes, allowing for detection of previously unobserved genomic variation[(Liu et al. 2024\)](https://doi.org/10.1038/s41467-024-48334-w).   
2. [Freyja’s covariants function](https://andersen-lab.github.io/Freyja/src/usage/covariants.html) parses aligned sequencing reads for physically linked mutations, which can be queried against large public databases of clinical sequencing data, such as [via Outbreak.info](https://outbreak-info.github.io/python-outbreak-info/cryptic_vars.html), to enable the detection of potential cryptic circulation of viral lineages in wastewater.[(Gangavarapu et al. 2023\)](https://doi.org/10.1038/s41592-023-01769-3)  
   

**Metagenomic Sequencing Methods**  
Although metagenomic sequencing of wastewater has great potential for unbiased surveillance of diverse pathogens, wet-lab pathogen concentration protocols are not yet capable in general of obtaining significant read depth and coverage for many pathogens. In many cases, the vast majority of reads are associated with host and enteric bacterial reads, which are of minimal use for pathogen surveillance. However, some recent studies using virome hybridization capture panels have suggested that this sort of metagenomic surveillance may be possible. When working with this data, or other metagenomic wastewater sequencing data, we recommend the following tools: 

* Kraken: Kraken is a widely used k-mer based match taxonomic classification tool that is used to classify reads to the most specific possible taxonomic label (genus,species, etc.), using the lowest common ancestor (LCA). [(Wood, Lu, and Langmead 2019\)](https://doi.org/10.1186/s13059-019-1891-0)  
* Bracken: Bayesian Reestimation of Abundance after Classification with KrakEN, or Bracken, is used as a post-processing step after Kraken that leverages the small numbers of reads that may be able to distinguish between species present in a sample, even if the vast majority of multiple species’ genomes are identical.[(Lu et al. 2017\)](https://doi.org/10.7717/peerj-cs.104)  
* Sourmash: This tool is used for a variety of metagenomic analyses purposes such as identification of the reference genome for read mapping, sequence querying and taxonomic classification of reads.  
* Targeting of specific genes of interest  
  * AMR markers: There is a continuous effort to develop methods for detection of antibiotic resistance through wastewater sequencing. For example, Mycobacterium tuberculosis(MTB) drug resistance markers that have been [catalogued by the World](https://www.who.int/publications/i/item/9789240082410) Health Organization and are most commonly detected using [tb-profiler](https://github.com/jodyphelan/TBProfiler). 

**Guidelines for researchers developing new tools (Scenario 4\)**  
Wastewater-based genomic pathogen surveillance, much like clinical genomic surveillance, relies on transparent accounting of the specific information (e.g., metadata, methods, libraries) used while performing an analysis. Enabling consistent and interpretable outcomes for bioinformatics analyses requires the use of standardized resources for sample analyses.   
When building new tools for community use, we recommend that developers adhere to the following standards. These approaches maximize tool usability, transparency, reproducibility, and access across contexts.

**Index/Database Versioning**  
Over the course of an outbreak, available information on circulating strains will often change on a daily basis, requiring public health researchers to integrate the most up-to-date sources of data possible. As such, it is important for analyses to be performed using real-time resources that are versioned and/or timestamped. We provide a few examples of this as examples:

1. Kraken2, the popular metagenomic read classifier, provides dates and descriptions for each of the reference databases it provides[(Wood, Lu, and Langmead 2019\)](https://doi.org/10.1186/s13059-019-1891-0). They are openly available [here](https://benlangmead.github.io/aws-indexes/k2).   
2. Freyja maintains a separate [Freyja-data](https://github.com/andersen-lab/Freyja-data) repository to store previous barcodes and metadata needed to exactly reproduce results[(Karthikeyan et al. 2022\)](https://www.nature.com/articles/s41586-022-05049-6).   
3. For lineage classification of virus genomes, PangoUShER is now the preferred approach[(de Bernardi Schneider et al. 2024\)](https://doi.org/10.1093/ve/vead085). The method relies on the global phylogenetic tree maintained by UShER, which is dated and publicly available [here](https://hgdownload.soe.ucsc.edu/goldenPath/wuhCor1/UShER_SARS-CoV-2/).[(McBroome et al. 2021\)](https://doi.org/10.1093/molbev/msab264)

### **Containerization**

In order to ensure reproducibility and accessibility, wastewater workflows should ideally be containerized using standard container management systems (e.g. Docker, Singularity). Doing so allows for software dependencies to be packaged together with a workflow, ensuring that they can be run reliably regardless of the selected compute platform. 

Further, all containers should be made publicly available via container registries such as Docker Hub or Quay.io to ensure that software can be readily deployable and accessible for all public health researchers. 

As mentioned in the section concerning Index/Database Versioning, it is critical that analyses be performed with the most up-to-date resources possible as more information becomes available during the course of an outbreak. It is therefore advised to regularly build and push the most recent data to public container registries.

**Making tools available for non-bioinformaticians**  
As many of the users of analysis packages, especially those used for pathogen surveillance, are not bioinformaticians and may require a click interface to analyze their data, it’s important to consider development options that facilitate this. A few different standards exist, but the most commonly used is Workflow Description Language (WDL). 

We recommend making workflows available to the public via dockstore, which provides a user friendly interface that allows users to directly add the workflow to their computing resource of choice, including Terra and Elwazi. 

**Analyses of Wastewater Pathogen Concentration Measurements**  
Although wastewater sequencing data has the benefit of providing information on the specific mutations and lineages circulating in the population, estimates of the virus concentration in wastewater are often equally, if not more important to inform public health guidance. Using the appropriate analytical methods ensures proper interpretation of results, and is especially important for wastewater surveillance programs with multiple sites. 

**Measurement normalization**  
Since wastewater is a complex mixture that may be diluted by other contributing sources, it is important to perform proper normalization to ensure that measurements are comparable across sites and over time. In addition to measuring the concentration of the pathogen, it is important to also measure the concentration of a fecal indicator, with PMMoV or Crassphage being the most robust and highly shed in stool and urine. The resulting measurement is generally unitless, with pathogen concentration divided by indicator concentration. If an amplification control is available, it is often good practice to further scale by the estimated concentration of the amplification control.

Since even normalized measurements can be difficult to compare across collection sites, we recommend performing statistical normalization of longitudinal samples (i.e. site specific mean-subtraction and variance scaling). However, it is worth noting that this approach requires sampling of the same site with the same collection and wet-lab techniques over an extended period of time, in which viral loads are able to vary over a considerable range. 

**Aggregation of samples across sites**  
To aggregate samples across sites, the catchment population and viral load are often used as a weighting factor to perform weighted averaging. Using a binning approach, samples can be grouped using the form average \= sum(p\*c)/sum(p), where c is generally the catchment population, or the product of the catchment population and normalized (and potentially standardized by site) viral load. 

**Smoothing approaches for longitudinal data**  
When analyzing sequential measurements, we recommend first considering basic convolutional smoothing filters, with moving average and binomial filters being the most commonly used. These simple smoothers are remarkably efficient, and can explicitly accommodate sample weighting by factors including catchment population. 

Local regression filtering, using methods including Savitzky-Golay or LOESS/LOWESS, can provide more effective smoothing but require more sophisticated implementations, and may be more difficult to interpret. When using these approaches, we recommend using 1st order polynomial approximations, in order to preserve signal norm.   
