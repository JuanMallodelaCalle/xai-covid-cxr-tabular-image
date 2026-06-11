# Methodology

## 1. Dataset Preparation

The project starts from a public COVID-19 chest X-ray dataset containing image files and metadata. The original data is heterogeneous, with missing values, irrelevant columns, inconsistent image formats, and diagnosis labels that require cleaning before modeling.

Main preprocessing steps:

- filter relevant chest X-ray samples;
- clean metadata columns;
- remove uninformative or incomplete records;
- standardize image naming;
- convert images to grayscale where needed;
- resize images for CNN input;
- derive a simplified target variable with three classes:
  - COVID-19;
  - Normal;
  - Other Pneumonia.

## 2. Exploratory Data Analysis

The EDA studies the dataset from both image-level and patient-level perspectives.

Main analyses:

- class distribution;
- age distribution by class;
- sex distribution by class;
- X-ray view type distribution;
- number of images per patient;
- diagnosis transitions for patients with multiple images;
- clinical-note word clouds;
- artifact prevalence in a manually annotated image sample.

The artifact analysis is included to highlight possible shortcut learning: a model could incorrectly rely on non-lung information such as text overlays or medical devices.

## 3. Tabular Modeling

The tabular pipeline combines structured metadata with text-derived features.

Input features:

- age;
- sex;
- X-ray view type;
- TF-IDF representation of cleaned clinical notes.

Models:

- Random Forest Classifier;
- XGBoost Classifier.

Explainability:

- Random Forest feature importance;
- SHAP values;
- LIME explanations.

## 4. Image Modeling

A simple convolutional neural network is trained as an image baseline.

The goal of this model is not clinical-grade performance. Its main purpose is to provide a controlled image-classification setup for visual explainability with Grad-CAM.

## 5. Explainable AI

The project applies modality-specific XAI methods:

| Modality | Model Type | XAI Method |
|---|---|---|
| Tabular / text-derived features | Random Forest | Feature importance |
| Tabular / text-derived features | XGBoost | SHAP |
| Tabular / text-derived features | XGBoost | LIME |
| Chest X-ray images | Simple CNN | Grad-CAM |
| Chest X-ray images | Pretrained CXR models | Grad-CAM |

## 6. External Models

The project reviews open-source models and libraries for chest X-ray classification to contextualize the baseline models. These are treated as external references or pretrained tools, not as original architectures trained from scratch in this repository.
