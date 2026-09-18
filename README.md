# RealWaste Image Classification

Deep learning-based image classification of waste materials using transfer learning and MobileNetV2.

## 📌 Project Overview

This project develops an image classification system for automated waste categorisation using the RealWaste dataset.

The system classifies waste images into nine categories and investigates different deep learning configurations to identify an effective classification pipeline. The final model uses MobileNetV2 transfer learning with class weights.

The project also includes model evaluation, class-level performance analysis and Grad-CAM explainability.

## 🎯 Business Problem

Recycling facilities often rely on manual waste sorting, which can be time-consuming and may lead to inconsistent classification.

An automated computer vision system could assist the sorting process by classifying waste items before they are directed to the appropriate recycling or disposal stream.

This project investigates whether deep learning-based image classification can provide a useful prototype for automated waste sorting.

## 📊 Dataset

The project uses the **RealWaste** image dataset.

The dataset contains **4,752 images** across nine waste categories:

- Cardboard
- Food Organics
- Glass
- Metal
- Miscellaneous Trash
- Paper
- Plastic
- Textile Trash
- Vegetation

The dataset is used as a proxy for camera-based waste sorting data.

## 🔬 Methodology

The overall pipeline consists of:

1. Data exploration
2. Data preprocessing
3. Image preparation
4. Model development
5. Model configuration experiments
6. Validation-based model comparison
7. Final model training
8. Independent test evaluation
9. Class-level performance analysis
10. Grad-CAM explainability

## 🧪 Model Experiments

Ten different pipeline configurations were evaluated using validation accuracy and validation loss.

| Configuration | Validation Accuracy | Validation Loss |
|---|---:|---:|
| Baseline CNN | 62.82% | 2.5303 |
| CNN + Dropout (0.5) | 63.24% | 1.1493 |
| CNN + Batch Normalisation | 27.04% | 2.0349 |
| Batch Normalisation + Dropout | 64.51% | 1.1859 |
| Batch Normalisation + Dropout + Strong Augmentation | 55.21% | 1.3440 |
| Batch Normalisation + Dropout + Light Augmentation | 56.06% | 1.2295 |
| Batch Normalisation + Dropout + Class Weights | 65.49% | 1.1892 |
| Light Augmentation + Batch Normalisation + Dropout + Class Weights | 59.72% | 1.4024 |
| Batch Normalisation + Dropout + Class Weights + Early Stopping | 65.77% | 1.0797 |
| MobileNetV2 Transfer Learning + Class Weights | **75.92%** | **0.7088** |

## 🏆 Final Model

The final selected configuration was:

**MobileNetV2 Transfer Learning + Class Weights**

The model uses a pretrained MobileNetV2 feature extractor with a task-specific classification head. Class weights were used to account for differences in class frequency.

### Validation Performance

- Validation Accuracy: **75.92%**
- Validation Loss: **0.7088**

## 📈 Test Performance

The final model was evaluated on **719 unseen test images**.

| Metric | Result |
|---|---:|
| Test Accuracy | **76.77%** |
| Test Loss | **0.6870** |
| Macro F1-Score | **0.7752** |

The test results show similar performance to the validation results on unseen data.

## 📋 Class-Level Performance

The class-level evaluation showed differences in performance between waste categories.

- Highest class F1-score: **Vegetation — 0.9130**
- Lowest class F1-score: **Miscellaneous Trash — 0.6176**

This demonstrates why class-level metrics are useful in addition to overall accuracy.

## 🔍 Explainability with Grad-CAM

Grad-CAM was used to investigate which regions of an image influenced the model's predictions.

For a correctly classified **Plastic** image, the activation was concentrated around the bottle, indicating that the model focused on relevant object features.

For an incorrectly classified **Metal** image, the model predicted **Cardboard**. The activation remained concentrated around the waste item, but the model did not distinguish the metal can correctly.

Grad-CAM therefore provides a qualitative explanation of both correct and incorrect predictions.

## 🛠️ Technologies Used

- Python
- TensorFlow / Keras
- MobileNetV2
- NumPy
- Pandas
- Matplotlib
- Scikit-learn
- Jupyter Notebook
- Grad-CAM
- Transfer Learning

## 💡 Business Implications

The results indicate that image classification could support automated waste sorting.

A camera-based system could potentially classify waste items before they are directed to the appropriate recycling or disposal stream. This could help reduce manual sorting effort and improve sorting consistency and throughput.

However, the current model should be considered a **prototype rather than a production-ready system**.

## ⚠️ Limitations

The RealWaste dataset has a relatively controlled image environment, with many images containing isolated objects and relatively consistent backgrounds.

Real-world waste sorting environments may contain:

- Overlapping waste items
- Cluttered backgrounds
- Different camera viewpoints
- Variable lighting conditions
- Objects with visually similar characteristics

Performance also varies between waste categories.

## 🚀 Future Improvements

Future work could include:

- Collecting more diverse real-world waste images
- Using conveyor-belt sorting data
- Comparing additional transfer-learning architectures
- Applying targeted data augmentation
- Investigating commonly confused waste categories
- Improving performance on visually similar classes
- Evaluating the system in a real sorting environment

## 📁 Project Contents

The main project implementation is provided in the uploaded Jupyter Notebook export:

`MOP_Final_html`

The notebook contains the complete analysis, experiments, final model evaluation and Grad-CAM explainability.
