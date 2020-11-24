# __Cancer dashboard tutorial document__

> This document aims to explain all the content presented on the **UFHCC Trial Enrollment Dashboard**

## Table of content

- [Headings](#headings)
  - [Protocol Enrollment Review](#protocol-enrollment-review)
  - [Recruitment Feasibility Assessment](#recruitment-feasibility-assessment)
  - [Disease Site Group](#disease-site-group)
  - [Eligibility Criteria](#eligibility-criteria)
  - [Patient Enrollment Progress Diagram](#patient-enrollment-progress-diagram)
  - [Data Visualization](#data-visualization)
  - [Filters](#filters)

- [Buttons](#buttons)
  - [Comparison Method](#comparison-method)
  - [Within Catchment Area](#within-catchment-area)
  - [Apply Eligibility Criteria](#apply-eligibility-criteria)
 
- [Other important components](#other-important-components)
  - [Data Sources](#data-sources)
  - [Comparison Datasets](#comparison-datasets)
  
  
## Headings
#### Protocol Enrollment Review

**Protocol Enrollment Review entry** aims to facilitate recruitment/enrollment progress review.  In this entry, user can explore following thing for each trial protocol (OnCore)
- [Patient enrollment progress diagram](#patient-enrollment-progress-diagram)
- Patients’ demographic information, geographic distribution (on an interactive map), disease characteristics (e.g., tumor information, chronic conditions) and other information of interest (e.g., BMI, smoking status)

Further, this entry allows users to compare the OnCore patients (enrolled) with the potential eligible patients (based on eligibility criteria) from [larger datasets](#comparison-datasets).  

#### Recruitment Feasibility Assessment
Recruitment Feasibility Assessment entry aims to let user apply customized eligibility criteria to explore following things:
- Eligible patients’ demographic information, geographic distribution (on an interactive map), disease characteristics (e.g., tumor information, chronic conditions) and other information of interest (e.g., BMI, smoking status)
- Compare the eligible patients across [different datasets](#comparison-datasets).  


#### Disease Site Group
UF Heath Cancer Center has 12 Disease Site Groups that consist of both research and clinical leaders. More details can be found: https://cancer.ufl.edu/research/clinical-trials-office-2/disease-site-groups/
#### Eligibility Criteria
Each study’s protocol has guidelines for who can or cannot participate in the study. These guidelines, called eligibility criteria, describe characteristics that must be shared by all participants. The criteria differ from study to study. They may include age, gender, medical history, and current health status.  For example, a study might only accept participants who are above or below certain ages

#### Patient Enrollment Progress Diagram
Below is the Patient Enrollment Progress Diagram that is summarized based on [CONCSORT](http://www.consort-statement.org/consort-statement/flow-diagram) (CONsolidated Standards of Reporting Trials), and further refined based on [OnCore data](#data-sources).


![Patient enrollment progress diagram](https://raw.githubusercontent.com/YeechingTiger/CancerClinicalTrialDashboard-Wiki/main/images/Figure1.png)
    
#### Data Visualization
    Patient information are presented in 4 sections below:
    • Demographic table: Frequency distribution of demographic variables (e.g., age, gender race, etc.)
    • Tumor table: Cancer stage and Cancer site
    • Patient distribution map view: The map shows the geographic distribution based on patients' residency informaiton. The geographic distribution can be set at either county level or census-tract level
    • Individual trait view: User can explore each individual trait (e.g., age, gender) in a Bar chart.  For each individual trait, a patient distribution map is also available.

#### Filters
Filters are used for defining patient cohort using customized eligibility criteria (filters). These criteria are further decomposed in to 5 sections below:

- Cancer/Tumor traits filter
   - Cancer site (ICD-O-3)
   - Cancer stage (AJCC vs TMN)
   
- Demographic filter
   - Age 
   - Gender
   - Race
   - Ethnicity
   - Rural/urban Status
   
- Clinical/Behavioral Variables filter
   - Smoking
   - BMI (Obesity)
   - Chronic conditions
  
- Common Patterns filter
   - Adequate Renal Function
   - Adequate Marron Function
   - Adequate Hepatic Function
   - Adequate Organ Function
   - Treatment Naive
   - Immunotherapy Candidacy





## Buttons

#### Comparison Method
In general, when user adding a [comparison dataset](#comparison-datasets), there are two different ways to apply [eligibility criteria](#eligibility-criteria) for selected protocols:
- Comparison method I: <b>Apply all computable criteria</b>
    - For each protocol, we analyze all eligibility criteria. The returned patients are identify based on all computable eligibility criteria.
    - <Mark>Note</Mark>: Each eligibility criterion can be further decomposed into unique criterion patterns, (e.g., <i>“Prior chemotherapy, radiation therapy, \
    or immunotherapy is NOT allowed for the treatment of this lung cancer”</i> can be decomposed into prior “chemotherapy”,“radiation therapy” and “immunotherapy”). \
    If the decomposed criterion patterns can be found (queried) in our EHR datasets, we consider the eligibility criteria as computable.
    
- Comparison method II: <b>Apply demographic criteria</b>
    - For each protocol, we only analyze demographic criteria. The returned patients are identified based on demographic criteria.

#### Apply Eligibility Criteria

Once user click <b>"Apply Eligibility Criteria"</b> button, based on the <b>Comparison Method</b> selected above, corresponding criteria (all computable criteria  vs. demographic criteria ) will be applied for the selected comparison dataset.

#### Within Catchment Area

Once user click <b>"Within Catchment Area"</b> button, it only return patients live within pre-defined catchment area based on their residency information in the data source (i.e., zipcode).

## Other important components

#### Data Sources

- <b>OneFlorida</b>: a statewide clinical research network and database, provide health care to more than 40 percent of Floridians in the nation’s third-largest state (all disease)
- <b>Florida Cancer Data System (FCDS)</b>: a broader view of the cancer burden across the state (all cancer patients in Florida)
- <b>Linked UFHealth EHRs and tumor registry data</b> (NOT AVALIABLE YET): Currently, we extract UFHealth EHRs and tumor registry data from OneFlorida dataset as a substitute. 
- <b>OnCore data</b>: OnCore is a web-based clinical research management system that manages multiple aspects of clinical research, including protocols, participants, sponsor invoicing, billing, data, and specimens.

<b>Note</b>: Overlap 1 represents cancer population in UFHealth EHRs, Overlap 2 represents cancer population in OnFlorida data.


![Patient enrollment progress diagram](https://raw.githubusercontent.com/YeechingTiger/CancerClinicalTrialDashboard-Wiki/main/images/Figure2.png)

#### Comparison datasets
- UFHealth (OneFlorida) linked with tumor registry
    - Cancer patients in UFHealth that also have records in tumor registry
- UFHealth (OneFlorida)
    - All cancer patients in UFHealth identified using ICD9/ICD10 codes
- OneFlorida linked with tumor registry
    - Cancer patients in OneFlorida data that also have records in tumor registry.
- OneFlorida patients (Overall)
    - All cancer patients in OneFlorida identified using ICD9/ICD10 codes
- Florida Cancer Data System (FCDS)
- Interventional trial
    - All patients in OnCore from interventional trials
- Interventional treatment trial
    - All patients in OnCore from treatment trials (interventional)
- Interventional non-treatment trial
    - All patients in OnCore from non-treatment trials (interventional)

