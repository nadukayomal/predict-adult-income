For this project, the Adult Income Dataset (also known as the "Census Income" dataset) has been selected from the UCI Machine Learning Repository.

## 2.Data Description

- Dataset Name : Adult Income Dataset.
- Source Link : [https://archive.ics.uci.edu/dataset/2/adult](https://archive.ics.uci.edu/dataset/2/adult).
- Problem Statement : To build a classification model that predicts whether an individual’s  annual income exceeds $50,000 based on census attributes.
- Number of Records : 48,842.
- Number of Features : 14 features.

### 3.EDA

During the initial data inspection phase, a comprehensive evaluation of data quality was performed. This process identified several issues related to data integrity that must be addressed prior to model development

#### 3.1 Missing and Invalid Value Detection

A systematic analysis was conducted to identify missing values and inconsistent data representations across all features.

- Categorical Missing Values : workclass, occupation, and native-country — contain missing entries.
- Invalid Placeholder Values : In addition to standard null values, these same variables include the symbol "?" as   a  placeholder to  represent unknown or unavailable data.
- The target variable (income) exhibits formatting inconsistencies (e.g., <=50K. vs <=50K), resulting in redundant class labels

#### 4.Preprocessing

- features  workclass : 963, occupation : 966, and native-country : 274 has missing value
- same feature  workclass : 1836, occupation : 1843, and native-country : 583 has '?' character
- Target feature counts: <=50K (24,720), <=50K. (12,435), >50K (7,841), and >50K. (3,846). The 16,281 values with trailing periods ('.') require unification.

To address missing categorical values, listwise deletion was selected over mode imputation. While mode imputation is a standard technique, it risks introducing demographic bias by artificially inflating majority categories. Given the large sample size of 48,842 records, the removal of the relatively small number of affected rows ensures data integrity without compromising the model's statistical power.

Assumption : <=50K is similer to <=50K. and  >50K is similer to  >50K.



