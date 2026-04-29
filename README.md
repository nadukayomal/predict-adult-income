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



-----------------------------------------------------------------
8.1 Analysis of ResultsOverall Performance: Both models achieved a high overall accuracy of approximately 84%. However, because the dataset is imbalanced (more instances of $\le 50\text{K}$ than $>50\text{K}$), accuracy alone does not tell the full story.Logistic Regression: This model demonstrated higher Precision (0.74) for the high-income class. This means that when the model predicts an individual earns over $50\text{K}$, it is correct $74\%$ of the time. However, it had a lower Recall (0.57), meaning it missed a significant portion of high earners.Random Forest: While the overall accuracy was slightly lower, the Random Forest model achieved a better Recall (0.60) and a higher F1-Score (0.65) for the high-income class. This indicates that the ensemble method is more effective at identifying complex patterns and correctly catching more individuals in the $>50\text{K}$ category.8.2 ConclusionFor this specific task, Random Forest is considered the superior model. Despite the marginal difference in accuracy, its higher Recall and F1-Score make it more robust for predicting the minority class (high-income earners). The model's ability to handle non-linear relationships and feature interactions provided a more balanced predictive performance compared to the linear baseline.Tips for your Document:The F1-Score is key: In your presentation, emphasize the F1-Score. It is the "harmonic mean" of Precision and Recall, and since Random Forest has the higher F1-Score (0.65 vs 0.64), it is technically the "winner."Confusion Matrix: You can mention that the Random Forest correctly identified 1,349 high earners, while Logistic Regression only caught 1,281. This proves the Random Forest is better at finding the "rich" candidates.

--------------------------------------------------------

