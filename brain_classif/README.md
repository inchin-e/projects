## RSNA-MICCAI Brain Tumor Radiogenomic Classification

### 1. Problem defition
A malignant tumor in the brain is a life-threatening condition. Known as glioblastoma, it's both the most common form of brain cancer in adults and the one with the worst prognosis, with median survival being less than a year. The presence of a specific genetic sequence in the tumor known as MGMT promoter methylation has been shown to be a favorable prognostic factor and a strong predictor of responsiveness to chemotherapy.

You have to predict the genetic subtype of glioblastoma using MRI (magnetic resonance imaging) scans to train and test your model to detect for the presence of MGMT promoter methylation.

### 2. Data
The data is downloaded from the Kaggle Bluebook for Bulldozers competition: https://www.kaggle.com/competitions/rsna-miccai-brain-tumor-radiogenomic-classification/data

#### Files
- train/ - folder containing the training files, with each top-level folder representing a subject. NOTE: There are some unexpected issues with the following three cases in the training dataset, participants can exclude the cases during training: [00109, 00123, 00709]. We have checked and confirmed that the testing dataset is free from such issues.
- train_labels.csv - file containing the target MGMT_value for each subject in the training data (e.g. the presence of MGMT promoter methylation)
- test/ - the test files, which use the same structure as train/; your task is to predict the MGMT_value for each subject in the test data. NOTE: the total size of the rerun test set (Public and Private) is ~5x the size of the Public test set
- sample_submission.csv - a sample submission file in the correct format

