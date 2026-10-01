# Epilepsy Detection Using Machine Learning

EEG-based epilepsy detection using signal processing and deep learning to classify normal and seizure EEG activity.

## Overview

This project explores automated epilepsy/seizure detection from EEG (Electroencephalogram) recordings.

The workflow processes EEG recordings in `.edf` format using **MNE-Python**, applies filtering and **Independent Component Analysis (ICA)** for signal processing and artifact analysis, prepares normal and abnormal EEG segments, and trains a **Gated Recurrent Unit (GRU)** neural network for binary seizure classification.

## Project Workflow

```text
EEG (.edf) Recordings
        ↓
EEG Signal Loading
        ↓
Band-pass Filtering
        ↓
Channel Mapping & Standard Montage
        ↓
ICA-based Signal Processing
        ↓
Normal / Abnormal EEG Segmentation
        ↓
Data Annotation
        ↓
Feature / Input Preparation
        ↓
GRU Deep Learning Model
        ↓
Binary Seizure Classification
        ↓
Model Evaluation
```

## Technologies Used

* **Python**
* **MNE-Python** – EEG signal processing
* **NumPy** – numerical computing
* **Pandas** – data manipulation
* **Matplotlib** – visualization
* **Scikit-learn** – preprocessing and machine learning utilities
* **TensorFlow / Keras** – deep learning
* **GRU (Gated Recurrent Unit)** – sequence classification
* **ICA (Independent Component Analysis)** – EEG artifact analysis

## Dataset

The project works with EEG recordings stored in **EDF (European Data Format)** files.

The notebook loads EEG recordings using MNE-Python and works with multi-channel EEG signals sampled at **512 Hz**.

The data is divided into:

* Normal EEG segments
* Abnormal/seizure EEG segments

The segments are subsequently labeled for binary classification:


0 → Normal EEG
1 → Seizure / Abnormal EEG


> The raw EEG/EDF files are not included in this repository. Please obtain and use the dataset according to its original licensing and usage conditions.

## EEG Signal Processing

### 1. EEG Loading

EEG recordings are loaded using MNE's EDF reader.

### 2. Filtering

The EEG signal is filtered to reduce unwanted frequency components and prepare the recording for further processing.

### 3. Channel Standardization

EEG channel names are mapped to standardized channel labels and an EEG montage is applied using MNE.

### 4. Independent Component Analysis

ICA is applied to decompose the EEG signal into independent components and investigate artifacts such as:

* Eye-related artifacts
* ECG-related artifacts
* Other signal components

The reconstructed signal is then used for subsequent analysis.

### 5. EEG Segmentation

The processed recording is divided into normal and abnormal EEG regions.

The resulting segments are combined into a unified dataset and assigned binary seizure labels.

## Deep Learning Model

A **Gated Recurrent Unit (GRU)** neural network is used for binary classification.

The implemented architecture contains:


Input EEG Data
      ↓
GRU Layer
64 Units
      ↓
Dense Layer
Sigmoid Activation
      ↓
Binary Classification


The model uses:

* Binary Cross-Entropy loss
* Adam optimizer
* Accuracy as an evaluation metric
* 10 training epochs
* 20% validation split

## Results

The implemented model achieved perfect training accuracy during the experiment.

However, the validation loss increased during training while validation accuracy remained comparatively stable, indicating **overfitting**.

This highlights the importance of further work such as:

* Improved train/test separation
* Regularization
* Hyperparameter tuning
* Additional validation
* Model comparison
* More robust evaluation metrics

## Key Learning Outcomes

This project provided practical experience with:

* EEG signal processing
* Biomedical time-series data
* EDF file handling
* MNE-Python
* EEG channel standardization
* ICA-based artifact analysis
* Data segmentation and annotation
* Sequential deep learning
* GRU-based classification
* Model validation and overfitting analysis

## Project Team

**Anand Patwa**
**Anurag Rai**

**Guide:** Miss. Raheel Hassan

## Future Improvements

Potential improvements include:

* Implementing a proper subject-wise train/test split
* Comparing GRU with LSTM and other deep learning architectures
* Applying additional EEG feature extraction techniques
* Performing hyperparameter optimization
* Addressing class imbalance where applicable
* Using precision, recall, F1-score and ROC-AUC for evaluation
* Adding an inference pipeline for unseen EEG recordings

## Disclaimer

This project is an academic/research implementation for EEG signal classification and is **not a medical diagnostic system**. Model outputs should not be used for clinical diagnosis or treatment decisions.
