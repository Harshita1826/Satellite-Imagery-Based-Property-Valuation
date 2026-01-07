## Satellite Imagery Based Property Valuation
This project builds a multimodal regression system that predicts property prices by combining:

Tabular housing data (sqft, bedrooms, grade, etc.)

Satellite imagery (neighborhood + surroundings)

Deep learning + machine learning fusion

The goal is to understand how environment + house features together influence price.

**Project Overview**

The goal is to build a model that uses both images and structured features to improve prediction accuracy.

The workflow:

1️. Download satellite images for train + test
2. Clean & preprocess tabular data
3️. Build a multimodal model:

- CNN → processes satellite images

- Dense Network → processes tabular features

- Both are merged and trained together

4. Generate final predictions and create submission.csv

**Project Structure**
CDC_Project/
│
├── data_fetcher_train.ipynb        # Script used to download satellite images for train.csv
├── data_fetcher_test.ipynb         # Script used to download satellite images for test2.csv   
├── model_training.ipynb            # Data cleaning + feature engineering + Multimodal model training
├── final_model_multimodal.keras    # Saved CNN + Tabular model
├── final_model_rf.joblib           # Random Forest model
├── final_scaler.joblib             # Scaler for tabular features
├── images/                         # TRAIN satellite images
├── images_test/                    # TEST satellite images
├── train.csv
├── test2.csv
└── submission.csv                  # Final predictions file

Models Used
1️. Multimodal Deep Learning Model

Input 1: (128×128×3) satellite images

Input 2: normalized tabular features

Outputs price prediction

2️. Random Forest (Baseline)

Used for comparison and blending.
