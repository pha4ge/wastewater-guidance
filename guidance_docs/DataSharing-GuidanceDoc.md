![PHA4GE logo](../phage-logo-thin.png)
## **Guidance Document \- Wastewater Data Sharing**

Much like for clinical pathogen surveillance, sharing of wastewater quantification and genomic data is essential to enable timely and transparent public health responses, as well as more equitable access to health-related information across the globe. Sharing of pathogen data, in particular, requires careful accounting for the complex incentives and pressures, from academic to geopolitical, such that data is re-used only in line with submitter permissions. 

Wastewater provides a distinct type of genomic data that requires recording unique attributes to ensure data interpretability and re-use. For wastewater sequencing data, the appropriate data sharing platforms are also different, since assembled/consensus sequences poorly represent the complex pathogen mixtures present in wastewater.

**What wastewater data should I share?**   
In this section, we focus on sharing of combined quantification and sequencing wastewater data (at present, no repositories exist for sharing of only quantification data). As mentioned above, consensus sequences from wastewater are usually poorly defined, and consensus calling is *highly likely* to lead to incorrect genome characterization. We acknowledge that for pathogens with very low diversity, or samples with sufficient resolution (e.g., building level) to identify individual infections, consensus calling methods used for clinical surveillance are likely to be sufficient. In this case, we recommend following associated PHA4GE guidelines ([https://pha4ge.org/sars-cov-2/](https://pha4ge.org/sars-cov-2/)), in addition to the steps described below. Wastewater sequencing data can be grouped into two main categories:

1. Pathogen-specific: For pathogen-specific (e.g., amplicon or hybrid-capture based), we recommend sharing the raw reads that map to the reference of interest. Non-mapping reads can be discarded prior to sharing of read data.   
   1. Read mapping can be performed using tools such as BWA ([https://github.com/lh3/bwa](https://github.com/lh3/bwa)) for Illumina reads, or minimap2 (https://github.com/lh3/minimap2) for ONT reads, against a reference genome of the target pathogen. These tools are often incorporated into existing bioinformatics workflows, many of which are listed in the Data Analysis section, for ease of use by non-bioinformaticians.

2. Metagenomic: For metagenomic sequencing, both semi-targeted (e.g., multi-pathogen panels) and fully unbiased, we recommend removing all human reads by identifying reads that map to the hg38 genome, and excluding those from your sample.   
   1. De-hosting can be performed using tools such as NCBI Human Read Removal Tool (HRRT) ([https://github.com/ncbi/sra-human-scrubber](https://github.com/ncbi/sra-human-scrubber)) or Hostile ([https://github.com/bede/hostile](https://github.com/bede/hostile)). These tools are often incorporated into existing bioinformatics workflows, many of which are listed in the Data Analysis section, for ease of use by non-bioinformaticians.

After these filtering steps, remaining reads can then be shared either in fastq or bam format, and uploaded to the database of your choosing. 

**Where to deposit wastewater data, and associated positives/negatives**   
Nearly all wastewater sequencing data that is shared is made available via openly accessible data repositories, primarily INSDC databases which includes NCBI Sequence Read Archive (SRA), the European Nucleotide Archive (ENA), and the DNA Data Bank of Japan (DDBJ). Data is shared across these databases, and any data uploaded to one INSDC database should be available through all of them. Whenever possible, we highly recommend that users upload to one of these databases, as they promote open data access and transparent analyses. 

However, we note that for many public health purposes, especially when considering monitoring of stigmatized pathogens and socioeconomic repercussions of data sharing, fully public data sharing may not be possible. At present, no such avenues for sharing of wastewater sequencing data are available. For samples where consensus sequence generation may be justified, GISAID and more recently Pathoplexus can be used for restricted-use data sharing. Both of these databases provide open sharing of data, with permanent or temporary options to enforce restricted use of the data by others. 

**Metadata/Contextual data:**   
To ensure that wastewater data is re-usable and interpretable by others, we provide recommendations on the inclusion of basic attributes associated with the sample. These include information on the contributing catchment (e.g., population size, location), sample collection approach (e.g. grab, passive, composite), laboratory methods (e.g., sequencing platform), and other virus quantification (e.g., concentration of pathogen and fecal indicator for normalization).

PHA4GE has developed a list of essential and optional contextual data fields for wastewater genomic surveillance([PHA4GE Wastewater Contextual Data Specification](https://github.com/pha4ge/Wastewater_Contextual_Data_Specification)). This resource provides extensive discussion on the relevance of contextual data and its role in ensuring the utility of data for later analyses. 

**Dissemination and communication**  
While sharing of raw data is key to ensuring transparent and collaborative public health surveillance, perhaps the most important type of data sharing is sharing of results with stakeholders and the general public. One of the most effective ways to do this is to build a web dashboard that provides distilled data and visualizations. 

Depending on your needs, findings and visualizations can be inserted modularly into a web-page or as part of entirely separate dashboards. Although a number of approaches are used for dashboard development, two of the easiest and most flexible platforms are provided by the R Shiny and plotly dash packages. Both R Shiny and plotly dash are well documented, enable dashboard design directly in R/Python, and are easy to test and deploy without previous web programming experience. We provide a few example Dash based dashboards:

- NICD South African National Wastewater Dashboard: [https://wastewater.nicd.ac.za/](https://wastewater.nicd.ac.za/)  
- SEARCH Wastewater Dashboard:[https://searchcovid.info/dashboards/wastewater-surveillance/](https://searchcovid.info/dashboards/wastewater-surveillance/)  
- Austrian Wastewater Dashboard: [https://wavesdashboard.azurewebsites.net/](https://wavesdashboard.azurewebsites.net/)

As well as example R Shiny based dashboards:

- New York State Wastewater Surveillance Network: [https://nywastewatcher.io/](https://nywastewatcher.io/)
- Dhaka Wastewater Surveillance: [https://dhakaesforsars-cov-2.research.virginia.edu/](https://dhakaesforsars-cov-2.research.virginia.edu/)

Other commonly used dashboard development tools are PowerBI, Tableau, and ArcGIS, which tend to be primarily used for simple visualizations, such as longitudinal measurement of wastewater viral loads. While easy to develop, well-suited to geographic data, and requiring even less programming experience, these options offer far less flexibility in terms of the design and complexity of the analyses that can be shown on the dashboard. Example wastewater dashboards using these platforms include:

- Chicago Department of Public Health Wastewater Surveilllance (PowerBI): [https://www.chicago.gov/city/en/sites/covid-19/home/covid-19-wastewater-surveillance.html](https://www.chicago.gov/city/en/sites/covid-19/home/covid-19-wastewater-surveillance.html)  
- Oregon Respiratory Viral Pathogen Wastewater Monitoring Dashboard (Tableau): [https://public.tableau.com/app/profile/oregon.public.health.division.acute.and.communicable.disease.pre/viz/OregonsRVPWastewaterMonitoring/Mainpage](https://public.tableau.com/app/profile/oregon.public.health.division.acute.and.communicable.disease.pre/viz/OregonsRVPWastewaterMonitoring/Mainpage)
- Minnesota Wastewater Surveillance(ArcGIS, original - discontinued): [https://www.arcgis.com/apps/dashboards/fd0350c812334c5f9733ca5b6186db0d](https://www.arcgis.com/apps/dashboards/fd0350c812334c5f9733ca5b6186db0d)  
