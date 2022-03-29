## Mechanisms of Action (MoA) Prediction

### 1. Problem defition

In the past, scientists derived drugs from natural products or were inspired by traditional remedies. Very common drugs, such as paracetamol, known in the US as acetaminophen, were put into clinical use decades before the biological mechanisms driving their pharmacological activities were understood. Today, with the advent of more powerful technologies, drug discovery has changed from the serendipitous approaches of the past to a more targeted model based on an understanding of the underlying biological mechanism of a disease. In this new framework, scientists seek to identify a protein target associated with a disease and develop a molecule that can modulate that protein target. As a shorthand to describe the biological activity of a given molecule, scientists assign a label referred to as mechanism-of-action or MoA for short.
 
### 2. Data

The data is downloaded from the Kaggle : https://www.kaggle.com/competitions/lish-moa/data
 
You have to predicting multiple targets of the Mechanism of Action (MoA) response(s) of different samples (sig_id), given various inputs such as gene expression data and cell viability data.
 
#### File descriptions

- train_features.csv - Features for the training set. Features g- signify gene expression data, and c- signify cell viability data. cp_type indicates samples treated with a compound (cp_vehicle) or with a control perturbation (ctrl_vehicle); control perturbations have no MoAs; cp_time and cp_dose indicate treatment duration (24, 48, 72 hours) and dose (high or low).
- train_drug.csv - This file contains an anonymous drug_id for the training set only.
- train_targets_scored.csv - The binary MoA targets that are scored.
- train_targets_nonscored.csv - Additional (optional) binary MoA responses for the training data. These are not predicted nor scored.
- test_features.csv - Features for the test data. You must predict the probability of each scored MoA for each row in the test data.
- sample_submission.csv - A submission file in the correct format.

### 3. Libraries and frameworks
- numpy
- pandas
- matplotlib
- lightgbm
