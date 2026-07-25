# Automatic Waste Classification
Image classification project using traditional computer vision techniques and deep learning models to automatically classify household waste into six categories.

## Overview
This project explores different computer vision and machine learning approaches for automatic waste classification. The objective is to classify waste images into six categories (cardboard, glass, metal, paper, plastic and trash) using both handcrafted features and convolutional neural networks.

The project was developed as part of the Computer Vision course of the B.Sc. in Computational Mathematics and Data Analytics at Universitat Autònoma de Barcelona.

## Dataset
The project uses the **Trash Type Image Dataset** (derived from TrashNet), available on Kaggle.

| Property | Value |
| :--- | :--- |
| **Total Images** | 2,527 |
| **Classes** | 6 |
| **Resolution** | 512 × 384 pixels |
| **Format** | JPG |

#### Classes Distribution
* **cardboard**: 403 images
* **glass**: 501 images
* **metal**: 410 images
* **paper**: 594 images
* **plastic**: 482 images
* **trash**: 137 images


## Methods
### Feature Extraction
* HOG
* HSV Histograms
* LBP

### Classical Machine Learning
* Support Vector Machine
* Random Forest
* k-NN

### Deep Learning
* Convolutional Neural Network


## Results

The models were evaluated using the **F1-macro** metric (due to class imbalance) alongside standard accuracy on an 80/20 train/test split.

### Classical Machine Learning

| Features | Model | Accuracy | F1-macro | Precision | Recall |
| :--- | :--- | :---: | :---: | :---: | :---: |
| **HOG + HSV** | k-NN | 49.60% | 46.52% | 56.10% | 46.91% |
| **HOG + HSV** | Random Forest | 68.77% | 65.57% | 74.47% | 63.34% |
| **HOG + HSV** | SVM | 69.37% | 67.39% | 74.07% | 65.21% |
| **LBP + HSV** | k-NN | 74.11% | 71.17% | 72.30% | 70.46% |
| **LBP + HSV** | SVM | 74.31% | 73.92% | 75.66% | 72.88% |
| **LBP + HSV** | **Random Forest** | **82.21%** | **79.88%** | **83.76%** | **78.31%** |

*Note: Texture descriptors (LBP) significantly outperformed shape descriptors (HOG), demonstrating that surface texture is more key than shape when distinguishing materials.*

### Deep Learning Models

| Model | Strategy | Accuracy | F1-macro | Precision | Recall |
| :--- | :--- | :---: | :---: | :---: | :---: |
| **Basic CNN** | Trained from scratch | 69.76% | 68.26% | 69.15% | 68.42% |
| **MobileNetV2** | Frozen base layers | 80.04% | 77.86% | 78.25% | 78.10% |
| **MobileNetV2** | **Fine-tuning (top 30 layers)** | **83.79%** | **81.93%** | **82.93%** | **81.36%** |

*Note: Fine-tuned MobileNetV2 achieved the best overall performance across all models.*


## Repository Structure
automatic-waste-classification
│
├── README.md
├── notebooks
│   └── RESIDUS.ipynb
├── report.pdf
└── images
    ├── architecture1.png
    └── architecture2.png


## Technologies
Python
TensorFlow
OpenCV
Scikit-learn
NumPy
Matplotlib
