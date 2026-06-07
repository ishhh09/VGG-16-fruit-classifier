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

# Data Exploration

The dataset was analyzed to determine class distribution.

Observations:

* Most fruit classes contained thousands of images.
* Some classes such as Apple, Guava and Kiwi had significantly fewer samples.
* The dataset exhibited class imbalance.

To visualize this distribution, a class distribution graph was generated and saved as:

class_distribution.png

---

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

# Custom Focal Loss

Formula:

L=−(1−pt)^γ(log(pt))+λ(1−pt)^2

pt= predicted probability of the true class
γ = focusing parameter (typically 2)
λ = confidence penalty weight (typically 0.2)
Benefits:

* Reduces the impact of easy examples
* Focuses learning on difficult samples
* Improves performance on minority classes

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

# Training Results

Epoch 1

* Training Accuracy: 50.44%
* Validation Accuracy: 72.39%

Epoch 2

* Training Accuracy: 72.89%
* Validation Accuracy: 81.91%

Epoch 3

* Training Accuracy: 79.99%
* Validation Accuracy: 85.73%

Final Validation Accuracy:

85.73%

Training curves are available in:

training_curves.png

---

# Evaluation Metrics

Classification Report Summary:

Accuracy: 86%

Macro Average F1 Score: 85%

Weighted Average F1 Score: 85%

Strongly Classified Fruits:

* Banana
* Carambola
* Guava
* Pitaya
* Muskmelon

More Challenging Fruits:

* Apple
* Tomatoes
* Peach

Possible Reasons:

* Visual similarity between fruits
* Class imbalance
* Limited samples in certain categories

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

* Focal Loss implementation research
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

# Future Improvements

* Fine-tuning deeper VGG16 layers
* Testing ResNet50 and EfficientNet architectures
* Class balancing techniques
* Deployment using Streamlit
* Real-time fruit recognition application

---

# Conclusion

This project successfully demonstrates the use of Transfer Learning with VGG16 and Focal Loss for multi-class fruit recognition. The model achieved approximately 86% validation accuracy and effectively classified 15 fruit categories while addressing dataset imbalance challenges.
