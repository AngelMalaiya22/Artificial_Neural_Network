# Iris Flower Classification using Artificial Neural Network (ANN)

This repository contains a Python implementation of an Artificial Neural Network (ANN) built with **Keras/TensorFlow** to classify Iris flower species based on their morphological features.

---

## 📌 Project Overview

The goal of this project is to build a multi-class classification model using a multi-layer perceptron (ANN). The model takes continuous physical measurements of Iris flowers as inputs and predicts their corresponding species.

### Dataset Overview
- **Dataset**: `Iris.csv`
- **Total Samples**: 150 (50 samples per class)
- **Features**: 4 input attributes
  1. `SepalLengthCm`
  2. `SepalWidthCm`
  3. `PetalLengthCm`
  4. `PetalWidthCm`
- **Target Classes**: 3 species
  - `Iris-setosa` (Encoded as `0`)
  - `Iris-versicolor` (Encoded as `1`)
  - `Iris-virginica` (Encoded as `2`)

---

## 🛠️ Data Preprocessing & Workflow

1. **Feature Selection**:
   - Dropped non-informative columns (`Id`) and separated features ($X$) from the target variable ($y$).
2. **Label Encoding**:
   - Transformed categorical target strings (`Iris-setosa`, `Iris-versicolor`, `Iris-virginica`) into numeric labels (`0`, `1`, `2`) using `scikit-learn`'s `LabelEncoder`.
3. **Data Splitting**:
   - Stratified train-test split (80% training, 20% testing) to ensure equal class proportions across sets.
   - **Train set size**: 120 samples
   - **Test set size**: 30 samples
4. **Feature Scaling**:
   - Applied `StandardScaler` to standardize input features ($\mu = 0, \sigma = 1$). Fitted on training data and applied transformation to both train and test sets.

---

## 🧠 Model Architecture

The neural network is built using `tensorflow.keras.Sequential`:

| Layer (type) | Output Shape | Neurons | Activation Function |
| :--- | :--- | :--- | :--- |
| **Dense** (Input/Hidden 1) | `(None, 8)` | 8 | ReLU |
| **Dense** (Hidden 2) | `(None, 4)` | 4 | ReLU |
| **Dense** (Output) | `(None, 3)` | 3 | Softmax |

- **Total Trainable Parameters**: 91
- **Optimizer**: `adam`
- **Loss Function**: `sparse_categorical_crossentropy`
- **Metrics**: `accuracy`

---

## 🚀 Training & Evaluation

- **Epochs**: 100
- **Batch Size**: 8
- **Validation Split**: 20% of training data

### Results

- **Test Accuracy**: `~93.33%`
- **Test Loss**: `~0.2389`

### Classification Report

```text
                 precision    recall  f1-score   support

    Iris-setosa       1.00      1.00      1.00        10
Iris-versicolor       0.90      0.90      0.90        10
 Iris-virginica       0.90      0.90      0.90        10

       accuracy                           0.93        30
      macro avg       0.93      0.93      0.93        30
   weighted avg       0.93      0.93      0.93        30
