# UTS - Applied Data Science for Innovation
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/87173adee17848bb9dcc12cf495135d4)](https://app.codacy.com/gh/rudecat/UTS-adsi?utm_source=github.com&utm_medium=referral&utm_content=rudecat/UTS-adsi&utm_campaign=Badge_Grade)

This repository is to document course projects using CRISP-DM framework, and to demonstrate what I have learned and how I approached challenges.

==============================
# Assignment-1 Predict Cancer Mortality Rate
==============================
## Objective
The goal of this experiment is to accurately predict cancer mortality based on information related to US counties.The dataset contains 33 different features (demography, medical information).

Being able to accurately predict cancer mortality can help to uncover some key correlation between features, and assist further discussion around how to manage and reduce cancer mortality.
## Approach
### Select Data
- Exclude **PctSomeCol18_24** as too much missing data
- Exclude **PctPrivateCoverageAlone** & **PctEmployed16_Over** as there are some missing data, and there’s no apparent matching trend with TARGET_deathRate.
### Clean Data
- **AvgHouseholdSize** has some value between 0 and 1, which doesn’t make sense. Hence, bring those value from float to integer by multiplying 100.
- **MedianAge** has some value larger than 100, which doesn’t make sense. Hence, bring those value to number between 1 and 100 by dividing by 10.
### Feature Engineering
- Split **Geography** into **State** and **County**, and do one-hot encoding on State feature to transform into dummy variables. Once it’s done, exclude geography, state and county features.
- Map **binnedInc** into integers that scale from 1 to 10 based on the bracket.
### Format Data
- Feature scaling using **StandardScaler** to standardize all features on
training set only.
- Standardize testing set using the StandardScaler fitted by training set to avoid data leakage.
## Model Selection
Select a number of regression models as candidates, and pick the final champion in evaluation stage based on performance. Also fine tune these models further using hyperparameters.
- **Multivariate Linear Regression**
- **Random Forest Regression**
  - max_depth
  - max_leaf_nodes
  - min_samples_leaf
- **Support Vector Regression**
  - Kernel
  - C
  - Epsilon
## Links
- [Full Project](assignment-1/)
- [Detailed README](assignment-1/README.md)
- [Complete Report](assignment-1/reports/Assignment%20D%20-%20KaiPing%20Wang.pdf)

==============================
# Assignment-2 Predict Car Buying Owners
==============================
## Objective
The goal of this experiment is to accurately predict if an existing customer is more likely to buy a new car. The dataset contains 16 different features (age_band, gender, car_model ... etc).

The result of this model can be used for targeting leads of a marketing campaign.
## Approach
### Select Data
- Select all feautres and data
### Clean Data
- Some missing data in age_band and gender. Due to the potential feature significance, instead of replacing missing value with existing value, we are using ‘OTHERS’ for missing value. By doing this, we don’t contaminate the importance of existing value.
### Feature Engineering
- Label encoding all categorical data.
## Model Selection
Select a number of classifier models as candidates, and pick the final champion in evaluation stage based on performance. Fine tune these models further using hyperparameters.
- LogisticRegression
- KNeighborsClassifier
- RandomForestClassifier
  - random_state
  - criterion
  - n_estimators
  - max_depth
## Links
- [Full Project](assignment-2/)
- [Detailed README](assignment-2/README.md)
- [Complete Report](assignment-2/reports/Assignment%202%20-%20KaiPing%20Wang.pdf)
