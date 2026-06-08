# VGG16 Fruit Recognition using Transfer Learning and Focal Loss

## Project Overview

This project implements a Fruit Recognition System using Deep Learning. The objective is to classify fruit images into 15 different categories using a pretrained VGG16 Convolutional Neural Network and a custom Focal Loss function to address class imbalance.

The model was trained on the Fruit Recognition dataset available on Kaggle and achieved approximately **86% validation accuracy**.

---

## Team Members

| Member        | GitHub Username  | Role                                        |
| ------------- | ---------------- | ------------------------------------------- |
| Ishank Dixit  | ishhh09          | Model Architecture & Training Pipeline      |
| Sristy Kumari | sristy09agr-ctrl | Evaluation, Documentation & Result Analysis |
| Mahi Jain     | ad25b1017-cloud  | Data Analysis & Preprocessing               |

---

# Problem Statement

Fruit classification is an important computer vision task with applications in:

* Smart agriculture
* Automated fruit sorting systems
* Retail inventory management
* Food quality inspection

The goal of this project is to classify fruit images into one of 15 categories using transfer learning.

---

# Dataset Information

Dataset: Fruit Recognition Dataset (Kaggle)

Number of Classes: 15

Classes:

* Apple
* Banana
* Carambola
* Guava
* Kiwi
* Mango
* Orange
* Peach
* Pear
* Persimmon
* Pitaya
* Plum
* Pomegranate
* Tomatoes
* Muskmelon

Total Images: Approximately 70,000+

Training Images: 56,445

Validation Images: 14,104

---

# Data Exploration and Dataset Complexity
The fruit dataset was analyzed to understand its distribution and challenges. The dataset contains multiple fruit classes with thousands of images captured under different lighting conditions, backgrounds, orientations, and viewpoints. Some classes, such as Apple, Guava, and Kiwi, contain fewer samples, leading to class imbalance.

The classification task is challenging due to:

Class imbalance across categories.

High intra-class variation (differences within the same fruit class).

Visual similarity between different fruit classes.

Variations in lighting, background, and image quality.

A class distribution graph was generated to visualize the dataset and saved as class_distribution.png. The complexity of the dataset motivated the use of VGG16, which can learn robust features for accurate fruit classification.

# Data Preprocessing

The following preprocessing techniques were applied:

* Image resizing to 224 × 224 pixels
* Pixel normalization using rescaling
* Data augmentation

Augmentation methods:

* Rotation
* Width shifting
* Height shifting
* Horizontal flipping
* Zooming

Training/Validation Split:

* Training: 80%
* Validation: 20%

---

# Model Architecture

Transfer learning was implemented using the pretrained VGG16 model.

Base Model:

* VGG16 pretrained on ImageNet
* Top classification layer removed
* Convolutional layers frozen during Phase 1 training

Custom Classification Head:

* GlobalAveragePooling2D
* Dense Layer (512 neurons, ReLU)
* Dropout (0.5)
* Dense Layer (256 neurons, ReLU)
* Dropout (0.3)
* Dense Layer (15 neurons, Softmax)

Total Parameters: 15,112,527

Trainable Parameters: 397,839

Non-Trainable Parameters: 14,714,688

---

Modified Custom Loss Function

L = -log(pt) + λ(1 - pt)^3

where:

pt = predicted probability of the true class
λ = regularization/confidence penalty parameter

Benefits:

- Places stronger emphasis on difficult samples.
- Increases penalty for low-confidence predictions.
- Improves class discrimination.
- Contributed to improved validation accuracy.
---

# Training Configuration

Optimizer:

Adam

Learning Rate:

0.0001

Callbacks:

* EarlyStopping
* ModelCheckpoint
* ReduceLROnPlateau

Hardware:

* Kaggle Notebook
* Tesla T4 GPU

Training Strategy:

Phase 1:

* Frozen VGG16 layers
* Train only custom classification head

---

Training Results

Epoch 1 Training Accuracy: 49.97% Validation Accuracy: 69.54%

Epoch 2 Training Accuracy: 73.21% Validation Accuracy: 78.76%

Epoch 3 Training Accuracy: 80.63% Validation Accuracy: 83.61%

Epoch 4 Training Accuracy: 84.31% Validation Accuracy: 84.63%

Epoch 5 Training Accuracy: 86.75% Validation Accuracy: 87.35%

Final Validation Accuracy: 87.35%

Final Evaluation Accuracy: 88%

Training curves are available in:

training_curves.png
---

# Evaluation Metrics

Classification Report Summary:

Accuracy: 88%

Macro Average F1 Score: 88%

Weighted Average F1 Score: 87%

Strongly Classified Fruits:

Banana (F1: 0.98)
Carambola (F1: 0.97)
Guava (F1: 0.96)
Pitaya (F1: 0.99)
Muskmelon (F1: 0.91)
Mango (F1: 0.93)

More Challenging Fruits:

Apple (F1-Score: 0.64)
Pomegranate (F1-Score: 0.78)
Tomatoes (F1-Score: 0.74)
Peach (F1-Score: 0.77)
Pear (F1-Score: 0.84)

Possible Reasons:

- Visual similarity among fruit categories.
- Variations in lighting and viewpoint.
- Residual class imbalance.
---

# Confusion Matrix Analysis

A confusion matrix was generated to analyze prediction behavior.

File:

confusion_matrix.png

Observations:

* Most fruit classes were correctly classified.
* Misclassifications occurred primarily among visually similar fruits.
* The model demonstrated strong generalization capability.

---

# Project Structure

VGG-16-fruit-classifier/

├── README.md

├── best_model.h5

├── class_distribution.png

├── training_curves.png

├── confusion_matrix.png



---

# Individual Contributions

## Ishank Dixit (ishhh09)

* Repository creation and GitHub integration
* VGG16 architecture implementation
* Transfer learning pipeline development
* Custom classifier design
* Model training and hyperparameter tuning

## Sristy Kumari (sristy09agr-ctrl)

* Custom Loss Function Generation
* Model evaluation and metric analysis
* Classification report interpretation
* Confusion matrix generation
* Documentation, result analysis and project reporting


## Mahi Jain (ad25b1017-cloud)

* Dataset acquisition and exploration
* Dataset analysis and class distribution study
* Image preprocessing pipeline
* Data augmentation strategy design
* Validation data preparation and verification

All team members participated equally in project planning, experimentation, testing and final review.

---

Conclusion

This project successfully demonstrates the application of Transfer Learning using VGG16 combined with a Modified Custom Loss Function for multi-class fruit recognition.

The final model was trained on more than 70,000 fruit images belonging to 15 categories and achieved:

- Validation Accuracy: 86.56%
- Final Evaluation Accuracy: 88%
- Macro F1 Score: 0.88
- Weighted F1 Score: 0.87

The modified loss function improved classification performance compared to the earlier focal-loss implementation and enabled better handling of difficult samples and class imbalance.

The project demonstrates the effectiveness of transfer learning for agricultural image classification and provides a strong foundation for automated fruit recognition systems.
