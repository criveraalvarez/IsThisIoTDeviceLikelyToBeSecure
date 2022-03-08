# Repository of the Dataset used in the paper "Is This IoT Device Likely to Be Secure? Risk Score Prediction for IoT Devices Using Gradient Boosting Machines"

**Authors**  
  Carlos A. Rivera A.(1), Arash Shaghaghi1(2), David D. Nguyen(1), and Salil S. Kanhere(1)  
   1. The University of New South Wales (UNSW) Sydney Australia.  
   2. RMIT University Melbourne Australia.
  
Part of the Lecture Notes of the Institute for Computer Sciences, Social Informatics and Telecommunications Engineering book series (LNICST, volume 419).
  
**Abstract**  
Security risk assessment and prediction are critical for organisations deploying Internet of Things (IoT) devices. An absolute minimum requirement for enterprises is to verify the security risk of IoT devices for the reported vulnerabilities in the National Vulnerability Database (NVD). This paper proposes a novel risk prediction for IoT devices based on publicly available information about them. Our solution provides an easy and cost-efficient solution for enterprises of all sizes to predict the security risk of deploying new IoT devices. After an extensive analysis of the NVD records over the past eight years, we have created a unique, systematic, and balanced dataset for vulnerable IoT devices, including key technical features complemented with functional and descriptive features available from public resources. We then use machine learning classification models such as Gradient Boosting Decision Trees (GBDT) over this dataset and achieve 71% prediction accuracy in classifying the severity of device vulnerability score.

**Keywords**  
IoT Security Risk Prediction | National Vulnerability Database (NVD) | CVE | IoT security | Machine learning

**Link**  
Publisher: Springer, Cham  
Link to the paper: https://link.springer.com/chapter/10.1007/978-3-030-94822-1_7
DOI: https://doi.org/10.1007/978-3-030-94822-1_7

**The Dataset**  
For this paper aim, we searched for datasets with content related to vulnerabilities and other information related to IoT devices. For it, we used the vulnerabilities database (NVD) of NIST (National Institute of Standards and Technology). This database is constructed from the CVE database and complemented with the vulnerability score (CVSS),  the technical specification of the affected software or hardware (Common Platform Enumeration - CPE), and a list of weaknesses related to the vulnerability disclosed (Common Weakness Enumeration - CWE). Note the CVE database contains the description of the vulnerability and affected product, a record id, references to web pages with detailed information of the vulnerability, and Date of record creation. We analysed the NVD and extracted information from the different elements to conform to an initial set of features. From this process and after processing several records we encounter several inconsistencies, for instance, the features expecting to receive information of devices had inconsistencies or were difficult to standardise. Because of these limitations, we concluded that using the NVD as the sole information provider was not ideal and decided to design a new dataset. This new dataset would use different sources, thus new features. This would resolve the limitations presented before. Note that the NVD would serve as the basis of our dataset but also have added information about IoT devices (affected by vulnerabilities disclosed at the NVD).  
We carried a thorough analysis and justification of use to select a final set of features for the new dataset. For instance, the feature "Brand", can be used to identify brands of vulnerable products or rate brands by the number of vulnerable products. We also realised that the combination of this feature with others like "Type of Product" can help with the identification of the most vulnerable products amongst brands. We assessed all the twenty-seven initial features, agreeing on accepting only nine. Being these, Brand, Product Type, Category, Price, Protocol, Data Storage, Personal Information, Location Management, Communication Capability, Authorisation Encryption and Risk Score. Note Risk Score is used as the output feature. The full description of the dataset features is shown in the Table 1.    

**Table 1. Dataset features.**  
| Feature Name | Data Type | Unique Values | Details |  
| --- | --- | --- | --- |
|Brand          |Categorical            |129      |Name of the device reported on the CVE.|
|Product Type   |Categorical            | 71      |Phrase describing the product.|
|Category       |Categorical            |  5      |SmartHome, Medical, Wearable, Telecomm, and Other.|
|Price          |Continuous             |Infinite |Reported in US Dollars.|
|Protocols      |Categorical            |8        |Protocols used in Communication Capability.|
|Data Storage   |Binary                 |2        |Location of data Locally or Remotely.|
|Personal Information |Binary           |2        |Personal information data used: Yes or No.|
|Location Track |Binary                 |2        |Tracks physical location: Yes or No.|
|Communication Capability |Categorical  |31       |Communication technology.|
|Authorisation Encryption |Categorical  |4        |Encryption used: Symmetric, Asymmetric, None, or Both.|
|Risk Score    |Categorical             |4        |From CVSS V3: Low, Medium, High, or  Critical.|
 

The records added from the NVD range from the year 2013 to the year 2021. And, to keep the dataset updated with the latest records, carried a sweep to the NVD over the year 2021 up to June. Noteworthy to mention that as a part of our measurement mechanism on the behaviour of the models in the different classes, we added eight synthetic records, one record per classification belonging to two specific products (A smart speaker and a smart camera). We report 1,153 as the final number of records collected, in the Table 2 we disclose the distribution among classes.  

**Table 2. Distribution of Dataset classes.**  
|Classification| Counts | Distribution %|
| --- | --- | --- |
|Low      |176        |15%|
|Medium   |138        |12%|
|High     |183        |16%|
|Critical |656        |57%|

The dataset can be found in the following [link](https://github.com/criveraalvarez/IsThisIoTDeviceLikelyToBeSecure-/Dataset_isthisiotlikelytobesecure.csv).
