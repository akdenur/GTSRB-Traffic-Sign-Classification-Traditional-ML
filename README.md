# GTSRB Traffic Sign Classification — Traditional Machine Learning

A comparative analysis of traditional computer vision and machine learning pipelines on the **German Traffic Sign Recognition Benchmark (GTSRB)** dataset. This project establishes a strong classical baseline using handcrafted feature extraction, dimensionality reduction, and classical classifiers, achieving **98.72% test accuracy** with SVM.

## Project Overview

Traffic sign recognition is a critical task for autonomous driving and advanced driver-assistance systems (ADAS). In this study, raw traffic sign images are processed through a structured traditional machine learning pipeline to evaluate the capabilities and performance boundaries of manual feature engineering before transitioning to Deep Learning architectures.

### Dataset
- **Source:** German Traffic Sign Recognition Benchmark (GTSRB)
- **Classes:** 43 traffic sign categories (speed limits, prohibitory, danger, and mandatory signs)
- **Total Samples:** 39,209 labeled images

## Methodology

1. **Image Preprocessing (OpenCV):**
   - Standardization of varying image resolutions and aspect ratios.
   - Color space transformations and Canny edge detection.
2. **Hybrid Feature Extraction:**
   - **HOG (Histogram of Oriented Gradients):** Captures edge orientations and structural shapes.
   - **LBP (Local Binary Patterns):** Extracts local texture descriptors.
   - **Canny Edge Features:** Highlights structural boundaries.
3. **Dimensionality Reduction:**
   - **PCA (Principal Component Analysis):** Compresses high-dimensional feature vectors while preserving maximum variance to optimize training time and prevent overfitting.
4. **Classification Models:**
   - **Random Forest (RF)**
   - **Support Vector Machines (SVM)**

## Key Results & Findings

- **Best Model:** Support Vector Machines (SVM) with hybrid features (HOG + LBP + Canny) and PCA achieved **98.72% test accuracy**.
- **Performance Limitations:** Manual feature engineering reaches a natural performance ceiling on visually similar speed limit signs (e.g., Class 5) and under severe illumination, motion blur, or low-contrast distortions.
- **Next Step:** These results serve as the classical baseline for the follow-up study: *GTSRB Traffic Sign Classification with Deep Learning (Custom CNN & MobileNetV2)*.

## Tech Stack

- **Language:** Python
- **Environment:** Google Colab
- **Libraries:** Scikit-learn, OpenCV, NumPy, Pandas, Matplotlib, Seaborn

## Repository Structure

```text
├── GTSRB_Traditional_ML_Pipeline.ipynb   # End-to-end training & evaluation notebook
├── GTSRB_Traditional_ML_Report.pdf       # Detailed academic project report (IEEE style)
└── README.md                             # Project documentation