### Case studies for deployment of wastewater surveillance

**Case Study \#1 \- “[Wastewater sequencing reveals early cryptic SARS-CoV-2 variant transmission](https://www.nature.com/articles/s41586-022-05049-6)”**

The aim of the study was to identify community spread of SARS-CoV-2 on a university campus, as well as broader San Diego county using wastewater sequencing, and to develop the laboratory and computational methods needed to track virus evolution and spread. 

**Surveillance Strategy/System Design:** 

* **Sampling location:** San Diego (University of California San Diego campus, greater San Diego metropolitan area)  
* **Sampling site**: For on campus samples, sewage from manholes or sewer cleanouts; for greater San Diego area, Point Loma wastewater treatment plant  
* **Sampling frequency**: For on-campus residential buildings, once daily for 1 year; for on-campus non-residential buildings, once every Monday-Friday from 2020-11-23 to 2021-11-20; for great San Diego area, three times a week from 2021-02-24 to 2022-02-07  
* **Sample collection method:** On campus, composite sampling using autosamplers collecting 24-hour time-weighted composites. At WWTPs, flow weighted composite sampling.   
* **Reason for sampling method(s):** The time-weighted sampling on campus was used to capture the average viral shedding over a day in small, well-controlled areas. Sampling was daily for residences and weekdays for other buildings to rapidly detect changes and transmission events. The main pump station at the Point Loma WWTP serves 2.3 million people. The flow-weighted sampling method accounted for daily fluctuations in wastewater flow, ensuring representative viral load estimates for the large population, and to provide a broad community snapshot of viral prevalence and variant trends over time.  
* **Detection & sequencing approach:** qPCR-based detection, and viral load quantification at regional WWTPs. All SARS-CoV-2 positive samples sequenced.   
* **How data will be used:** Comparison of lineage prevalence in wastewater to those in clinical samples, determining that wastewater can detect emerging variants of concern up to two weeks earlier

**Ethical/Legal Considerations and Approvals:**   
**Core ethical considerations:**

* Beneficience and non-maleficence: Wastewater surveillance was implemented in response to the ongoing COVID-19 pandemic, to monitor spread on the university campus, as well as the broader metropolitan area. Wastewater detections led to notifications for campus residents to test themselves, in order to identify and minimize virus spread in the community. Given the high density of university housing and facilities, building level surveillance enabled timely notification of individuals of nearby spread, without revealing any identifiable information. Community surveillance expanded variant tracking, while only using large regional wastewater catchments (\>\>100k individuals).   
* Distributive Justice: All residential and most academic buildings were monitored on campus, with no apparent biases. Community monitoring covered nearly the entire metro area in San Diego, using a catchment of \>2.3 million individuals.   
* Privacy and Autonomy: Campus surveillance, while performed at individual building resolution, was anonymous, and detection trends were made available (with clear community awareness and public health mandate) via a public web dashboard. Broader metro area trends were fully anonymized, and disseminated publicly via a web dashboard, in collaboration with county public health.   
* Data Custodianship, Distribution, and Communication: All raw data was made publicly available via NCBI SRA. Campus testing and wastewater testing and sequencing were made available in real time on web dashboards via public health and research institution partnerships.   
* Transparency and accountability: Separate public health dashboards were used for campus and broader metro area surveillance. On campus, individuals were notified if buildings that they lived in were known to have positive detections via wastewater. 


**Core legal considerations:**

* Legal authorization: Study was a collaboration among academic and public health (university and county), with a clear mandate to provide real-time surveillance to the community.   
* Mandatory Reporting Requirements: No legal reporting mandate specific to COVID-19.   
* Data Protection and Privacy: All data is de-identified and only simple positive/negative information is made available at the building level for campus surveillance, in line with the university public health mandate. Metro area surveillance focuses only on large catchment areas, ensuring anonymity of results.    
* Public Health Integration: Data was integrated directly into public health monitoring and dashboards, both at the university level and at the metro area level, in near real-time. Metro area results were also included in county public health weekly reports.   
* Community and Indigenous Rights: Campus surveillance was performed in close contact with community members and leadership, and did not specifically target any group. Metro area surveillance included all groups, including some indigenous communities, but was performed at a large-scale resolution, so that no group could be specifically identified or targeted from surveillance. 

**Data Analysis:** 

* **Virus diversity**: richness was defined as the total number of single nucleotide variants (SNVs) called with iVar, and mean Shannon entropy calculated using an equation provided in the manuscript. Statistical associations were measured using a Mann-Whitney U-test.  
* **Lineage abundance estimation**: Freyja  
* **Phylogenetic analysis**: masking of homoplasic sites, followed by maximum likelihood reconstruction for each major Variant of Concern  
* **Temporal delay detection**: estimation of lag time between epidemiological curves from wastewater and clinical surveillance of the Epsilon variant

**Data Sharing Strategy:** raw sequence data available on NCBI Sequence Read Archive under the BioProject ID [PRJNA819090](http://www.ncbi.nlm.nih.gov/bioproject/?term=PRJNA819090); consensus sequences available on GISAID; publicly available dashboards ([https://returntolearn.ucsd.edu/dashboard/](https://returntolearn.ucsd.edu/dashboard/) ; [https://searchcovid.info/dashboards/wastewater-surveillance/](https://searchcovid.info/dashboards/wastewater-surveillance/) ; [https://searchcovid.info/dashboards/sequencing-statistics/](https://searchcovid.info/dashboards/sequencing-statistics/))