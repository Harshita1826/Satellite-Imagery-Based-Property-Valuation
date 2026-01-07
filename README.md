# Satellite Imagery Based Property Valuation
This project predicts property prices using:

- Satellite Images
- Tabular features (area, bedrooms, etc.)
- A combined multimodal deep learning model

### Project Overview

The goal is to build a model that leverages both images and structured features to improve property price prediction accuracy.

The workflow:

1️. Download satellite images for train + test (or use pre-downloaded images, see note below)
2️. Clean & preprocess tabular data
3️. Build a multimodal model:

- CNN → processes satellite images

- Dense Network → processes tabular features

- Both are merged and trained together

4️. Generate final predictions and create submission.csv

### About Image Downloading

Originally, the project included two notebooks meant to download satellite images automatically:

data_fetcher_train.ipynb

data_fetcher_test.ipynb

However, due to account / access issues:

I downloaded the images using another Google account and manually copied them into the project folders.

So currently:

**Folder	                    What it contains**
images/	                Satellite images for train.csv
images_test/	          Satellite images for test2.csv

The fetcher notebooks are kept in the repo because they show the intended pipeline and can still be reused if API keys/access are available.

**Note: Images are not re-downloaded when running the project — they are already placed inside the folders.**

**Note: Due to GitHub size limits, pretrained models are not uploaded. Run model_training.ipynb to generate final_model_multimodal.keras and final_model_rf.joblib locally.**

**Note: Due to GitHub size limits, folders named images/ and images_test/ are also not uploaded locally**

`Download the pretrained model and the images folder from the drive link given
**[Drive link](https://drive.google.com/drive/folders/19cQPC8beWk2Arot8iW51v3sJLtFegK8V?usp=sharing)**`

### Project Structure

CDC_Project/

│

├── data_fetcher_train.ipynb        # Script used to download satellite images for train.csv

├── data_fetcher_test.ipynb         # Script used to download satellite images for test2.csv  

├── model_training.ipynb            # Data cleaning + feature engineering + Multimodal model 
training

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

- Input 1: (128×128×3) satellite images

- Input 2: normalized tabular features

- Outputs price prediction

2️. Random Forest (Baseline)

Used for comparison and blending.

### How to Run

1️. Install dependencies

`pip install tensorflow pandas numpy scikit-learn joblib matplotlib`

2️. Prepare satellite images

If you don’t have images/ and images_test/, run:

data_fetcher_train.ipynb
data_fetcher_test.ipynb


This will download images into the respective folders.

If folders already exist (from manual copy), you can skip this step.

3️. Train the model

model_training.ipynb

This will generate:

- `final_model_multimodal.keras`

- `final_model_rf.joblib`

- `final_scaler.joblib`

- `submission.csv`

### Result

- Multimodal model performed better than tabular-only baseline

- Satellite images helped capture neighborhood effects
