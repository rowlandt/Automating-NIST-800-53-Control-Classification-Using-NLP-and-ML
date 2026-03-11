# Automating-NIST-800-53-Control-Classification-Using-NLP-and-ML

# NIST SP 800-53r5 Control Family Classification
# INFD 645 — Final Project
**Automating NIST 800-53 Control Classification Using NLP and Machine Learning**


# Project Overview

This project develops an automated machine learning pipeline to classify NIST SP 800-53 Revision 5 security controls into their corresponding control families using Natural Language Processing (NLP). The system uses a three-stage progressive approach, moving from TF-IDF vectorization to sentence transformer embeddings, to map unstructured policy text to the correct NIST control family. The final champion model (Stage 3 SVM) achieves a Top-3 accuracy of 83.19%, making it viable as a human-in-the-loop compliance decision-support tool.


# Project Structure


INFD_645_Final_Project.ipynb   # Main Jupyter notebook (all code)
NIST_800_53r5.csv              # NIST SP 800-53r5 control catalog dataset
README.md                      # This file


# Dependencies

This project requires Python 3.8 or higher. Install all required libraries using the command below:


pip install pandas numpy matplotlib seaborn scikit-learn nltk sentence-transformers imbalanced-learn wordcloud


# How to Run

1. Clone or unzip the project folder
2. Ensure the dataset file `NIST_800_53r5.csv` is in the **same directory** as the notebook
3. Install all dependencies using the pip command above
4. Launch Jupyter Notebook or JupyterLab:
5. Run all cells in order from top to bottom using **Cell or Run All**

# Expected Output

Running the notebook top to bottom will produce the following:

**EDA Section**
- Bar chart showing the distribution of NIST control families
- Word clouds for the AC and IA control families
- LDA topic modeling output showing 5 latent topics with top keywords

**Stage 1 — Baseline TF-IDF**
- Accuracy, Precision, Recall, and F1-Score for all 4 classifiers

**Stage 2 — TF-IDF + SMOTE**
- Updated metrics for all 4 classifiers after SMOTE oversampling

**Stage 3 — Transformer Embeddings + SMOTE**
- Updated metrics for all 4 classifiers using sentence transformer embeddings
- Confusion matrix heatmap for the Stage 3 SVM

**Cross-Stage Comparison**
- Master comparison table showing F1-Score progression across all three stages
- Bar chart visualizing model performance evolution

**Champion Model Evaluation**
- Top-1 Accuracy: ~65%
- Top-3 Accuracy: ~83%
- Live predictions on custom policy statements


# Sample Predictions

The notebook includes a function `predict_nist_family_advanced()` that accepts any plain-language policy statement and returns the top 3 predicted NIST control families with confidence scores. Example:

```
Input: "All employees must use a hardware token to log into their workstations."
Primary Prediction: IA
--- Top 3 Alternatives ---
 - IA: 45.32%
 - AC: 28.17%
 - SC: 12.04%
```
