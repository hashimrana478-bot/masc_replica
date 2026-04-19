MASC Paper Replication — Mobile App Screen Classification
Replication of: MASC: A Dataset for the Development and Classification of Mobile Applications Screens
Original Authors: Girgis, Zaki, Elgeldawi, Abdallah & Ahmed — Minia University, Egypt
Published in: International Journal of Computing, Vol. 24(3), 2025
DOI: https://doi.org/10.47839/ijc.24.3.4183

What This Is
This repository replicates the MASC paper, which introduces a dataset of 7,065 manually labeled mobile UI screenshots classified into 10 screen types (Login, Home, Chat, Map, etc.) and tests 10 machine learning classifiers on them. The original paper claims above 93% accuracy using classical ML with a custom 11-feature extraction pipeline — this replication verifies that claim.

Results Summary
ClassifierPaper AccuracyReplicated AccuracyGradient Boosting93.48%94.19% ✅SVM Linear93.20%94.05% ✅Logistic Regression ⭐92.63%93.91% ✅Multi-Layer Perceptron ⭐93.20%93.91% ✅Random Forest93.06%93.77% ✅XGBoost93.20%93.63% ✅Naive Bayes ⭐90.65%91.22% ✅Decision Tree ⭐92.35%90.93% ⚠️Adaboost83.29%85.69% ✅SVM RBF81.16%83.71% ✅
⭐ = Course algorithm  |  ✅ = Met or exceeded paper  |  ⚠️ = Slightly below (within margin)
All results are within ±2.55% of the paper's reported values.

Dataset
The MASC dataset contains 7,065 Android UI screenshots from 3,400+ apps, split into 10 classes:
ClassScreensDescriptionWelcome1,084Onboarding screensList960Scrollable contentLogin889AuthenticationHome866App dashboardsSearch725Search interfacesSetting629Configuration screensMenu557Navigation menusProfile526User profilesMap500Geographic viewsChat329Messaging screens
Download: https://doi.org/10.5281/zenodo.14783065

How to Run
bash# 1. Clone this repository
git clone https://github.com/hashimrana478-bot/masc_replica
cd masc_replica

# 2. Install dependencies
pip install -r code/requirements.txt

# 3. Download MASC dataset from Zenodo,kaggle and place in data/ folder

# 4. Run classification
python code/masc_classification.py

Bugs Fixed From Original Code
The original code had 9 bugs that needed fixing before it would run:

run_masc() called on class instead of instance — fixed with obj = Manage_MASC(); obj.run_masc()
Missing list arguments in get_all_features() — initialized and passed all 3 lists
Placeholder file paths not replaced — set correct MASC_Json, Semantic, and Full paths
Details.txt treated as a folder — added os.path.isdir() filter
Encoding errors on JSON files — added encoding='utf-8', errors='ignore'
Boolean clickable field crashing .lower() — added str() conversion
Syntax errors in ManageKeywords.py — fixed braces, colons, and brackets
NLTK stopwords not downloaded — added nltk.download() calls
Mixed int/str column names — added X.columns = X.columns.astype(str) before fit()


Dependencies
numpy==1.23.5
pandas==1.5.3
scikit-learn==1.2.2
xgboost==1.7.6
matplotlib==3.7.1
seaborn==0.12.2
nltk==3.8.1
joblib==1.2.0

References

Original paper: https://doi.org/10.47839/ijc.24.3.4183
Original code: https://github.com/Ali-Aahmed/MASC-Dataset
MASC dataset: https://doi.org/10.5281/zenodo.14783065
Rico dataset: https://doi.org/10.1145/3126594.3126651
Kaggle dataset:https://www.kaggle.com/datasets/aliahmed458/masc-dataset

👤 Author
Hashim Rana GitHub: https://github.com/hashimrana478-bot Mahad Bashir Github: https://github.com/mahadbashir1



