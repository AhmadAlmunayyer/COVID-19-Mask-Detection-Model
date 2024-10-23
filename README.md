# COVID-19 Mask Detection Model

**Prepared by:** Ahmad AL-Munayyer   
**Date:** 13 August 2024  

## Table of Contents
- [Objective](#objective)
- [Dataset](#dataset)
- [Model](#model)
- [Challenges](#challenges)
- [Results](#results)

---

## Objective
The aim of this project was to develop an object detection model to identify whether individuals in images are wearing masks, using a state-of-the-art object detection framework.

---

## Dataset
The dataset was collected from two sources: Pexels and other online websites. Efforts were made to ensure the dataset was diverse, covering various environments, lighting conditions, and perspectives.

- **Total Images:** 159
- **Training Set:** 103 images (including 15 background images without masks)
- **Validation Set:** 28 images
- **Test Set:** 28 images
- **Annotations:** Bounding boxes drawn around individuals to indicate whether they were wearing masks or not.

---

## Model
The model was developed using **YOLOv8 (Large Pre-trained Model)** with transfer learning to enhance performance.

### Model Settings
- **Framework:** YOLOv8 (Large Model)
- **Epochs:** 250  
- **Optimizer:** AdamW  
- **Frozen Layers:** First 5 layers of the backbone  
- **Image Size:** 640 pixels  
- **Learning Rate:** 0.0001  
- **Batch Size:** 32  
- **Auto Augmentation:** Disabled  
- **Classification Loss Gain:** 0.2  
- **Weight Decay:** 0.005  
- **Label Smoothing:** 0.1  
- **Mixup Augmentation:** Enabled (probability: 0.1)  
- **Early Stopping Patience:** 50 epochs  
- **Mosaic Augmentation:** Disabled during the last 20 epochs  

---

## Challenges
### 1. Overfitting  
Initial training revealed overfitting issues, which were mitigated through the following actions:
- Reduced the learning rate to prevent fast convergence to suboptimal solutions.
- Applied **weight decay** and **label smoothing** for regularization.
- Lowered the classification loss gain to reduce sensitivity to misclassifications.

These adjustments improved the model's ability to generalize, leading to better performance on unseen data.

### 2. Data Collection  
Creating a diverse and well-annotated dataset was challenging, especially ensuring variety in environments and perspectives. However, the final dataset was sufficiently diverse, contributing to the model's robust performance.

---

## Results
The final model achieved high precision and recall, minimizing both false positives and false negatives. Below are the key metrics from the evaluation on the test set:

- **Precision:** 0.989  
- **Recall:** 0.946  
- **F1-Score:** 0.967  

---

