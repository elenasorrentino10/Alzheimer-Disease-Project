# Alzheimer-Disease-Project

DATASET & Inspiration: https://www.kaggle.com/code/schorsi/classification-of-alzheimers-95-totw 

Details about the ADNI Dataset
The Alzheimer's Disease Neuroimaging Initiative (ADNI) is a landmark longitudinal study focused on understanding, identifying, and tracking biomarkers of Alzheimer's disease (AD) and related cognitive disorders. It aims to accelerate the development of treatments and interventions for AD by studying various stages of the disease and collecting extensive neuroimaging, clinical, genetic, and biomarker data.
Within the ADNI dataset, participants are typically classified into three main groups based on their cognitive status:
1. Alzheimer's Disease (AD) Group:
Individuals in this group have been diagnosed with Alzheimer's disease. They may exhibit progressive memory loss, cognitive decline, and behavioral changes characteristic of AD. Participants in this category usually have confirmed diagnoses of probable AD based on clinical assessments, cognitive tests, and sometimes neuroimaging biomarkers indicating AD-related changes in the brain.
2. Mild Cognitive Impairment (MCI) Group:
Participants in this group have mild cognitive impairment. MCI represents an intermediate stage between normal aging-related cognitive decline and more severe cognitive impairment associated with AD. Individuals with MCI might have noticeable memory problems or other cognitive issues that are more pronounced than typical age-related changes but do not meet the criteria for a diagnosis of AD.
There are two subcategories within the MCI group:
●	MCI Converter (MCIc): Individuals who have MCI at the baseline but progress to a diagnosis of AD during the study follow-ups.
●	MCI Stable (MCIs): Participants with MCI who do not progress to a diagnosis of AD during the study period and maintain stable cognitive functioning.
3. Normal Control (NC) Group:
This group consists of individuals without any significant memory or cognitive impairments. They serve as a comparison or control group against which researchers can evaluate cognitive changes and brain alterations observed in individuals with AD or MCI. Participants in this group typically exhibit normal cognitive function for their age.
The ADNI dataset collects comprehensive data from these different groups, including clinical assessments, neuroimaging (MRI, PET scans), genetic information, cerebrospinal fluid biomarkers, and cognitive tests. Analyzing these data helps researchers better understand the progression of AD, identify potential biomarkers, and develop diagnostic tools or treatments for the disease.

Subset of the Alzheimer’s Disease Neuroimaging Initiative (ADNI) database. This dataset consists of brain MRI scans with AD related findings as well as those without.

AD consisting of MRI scans having signs of early Alzheimer’s disease,
MCI consisting of MRI scans of patients having mild cognitive impairment,
NC consists of MRI scans presenting normal control.

MRI scans as labels to build a classifier to predict the belonging to a particular group of patients: AD/MCI, AD/NC, and MCI/NC. 
 
From Kaggle - > 3 separate models for a binary classification problem.

Actually following combinations are possible

AD	MCI	NC
0	0	0
0	0	1
0	1	0
0	1	1
1	0	0
1	0	1
1	1	0
1	1	1



6 category of classes are possible in the case of classification

1.	NC
2.	MCI
3.	AD
4.	MCI/NC
5.	AD/NC
6.	AD/MCI

While the ADNI dataset contains information for six potential classes, the three classifications—MCI/NC, AD/NC, and AD/MCI—are often of particular interest due to their significance in studying the progression and markers of Alzheimer's disease. Researchers might concentrate on these specific groups to gain deeper insights into disease progression, biomarkers, and potential interventions.

The classifications of Normal Cognition (NC), Mild Cognitive Impairment (MCI), and Alzheimer's Disease (AD) are indeed fundamental in understanding the spectrum of cognitive decline. These categories represent distinct stages of cognitive function, from normal to impaired states.
While these three categories (NC, MCI, and AD) are essential and form the basis of understanding cognitive health, in the context of the ADNI dataset and similar research studies, the focus on the combinations (such as MCI/NC, AD/NC, and AD/MCI) allows for a more specific investigation into the transitions between these stages and the associated biomarkers or predictors of disease progression.
The emphasis on combinations like MCI/NC, AD/NC, and AD/MCI enables researchers to explore specific transitions and changes between these stages. It's not that the NC, MCI, and AD categories are disregarded; rather, researchers often concentrate on the combinations to better understand the progression from normal cognition to mild impairment and then to Alzheimer's disease. These combinations provide a more nuanced understanding of how cognitive impairment develops and progresses, offering insights into potential markers or predictors for the advancement of the disease.

The ADNI dataset, with its multifaceted information including neuroimaging data (MRI, PET scans), clinical assessments, demographics, and biomarkers, allows for the development of various machine learning models. Here are some types of machine learning models commonly developed using the ADNI dataset:
1. Classification Models:
●	Alzheimer's Disease Prediction: Predicting the likelihood of an individual developing Alzheimer's disease based on demographic information, genetic markers, cognitive scores, and neuroimaging data.
●	Mild Cognitive Impairment (MCI) Classification: Identifying individuals with MCI who are more likely to progress to Alzheimer's disease.
●	Disease Subtype Classification: Classifying different subtypes or stages of Alzheimer's disease or other related cognitive disorders.
2. Regression Models:
●	Disease Progression Prediction: Predicting the rate of disease progression in individuals with Alzheimer's disease or MCI.
●	Cognitive Score Prediction: Predicting cognitive scores or changes in cognitive function based on various features from the dataset.
3. Clustering and Unsupervised Learning Models:
●	Disease Subgroup Identification: Discovering subgroups or clusters of patients based on similarities in neuroimaging data, clinical assessments, or biomarkers.
●	Biomarker Identification: Identifying potential biomarkers or patterns in the data that distinguish different groups of patients.
4. Deep Learning Models:
●	Neural Networks: Using deep learning architectures (e.g., CNNs - Convolutional Neural Networks, RNNs - Recurrent Neural Networks) for automatic feature extraction from neuroimaging data to predict disease status or progression.
●	Generative Models: Building generative models to synthesize neuroimaging data or generate disease-specific features.
5. Survival Analysis:
●	Time-to-Event Prediction: Analyzing time-to-event data to predict the progression from MCI to Alzheimer's disease or estimate survival time after diagnosis.
6. Ensemble Methods and Hybrid Models:
●	Ensemble Techniques: Employing ensemble methods like Random Forests, Gradient Boosting, or AdaBoost to combine multiple models for improved predictive performance.
●	Hybrid Models: Integrating multiple data modalities (e.g., combining neuroimaging data with clinical assessments) to build more comprehensive predictive models.
The ADNI dataset's multidimensional nature enables the development of models for various tasks, such as disease prediction, progression monitoring, biomarker identification, and patient stratification. The choice of model depends on the specific research questions, data characteristics, and the desired outcome.

