# Vision-Based Driver Behavior Detection for Enhanced Road Safety

This repository presents a deep learning-based system designed to detect distracted driver behaviors in real-time using computer vision. The system uses multiple state-of-the-art convolutional neural networks (CNNs) and an ensemble model to classify driver activities into six categories.

## 🚗 Project Objective

Distracted driving is a leading cause of road accidents globally. This project aims to:

- Detect unsafe driver behaviors in real-time from in-cabin video data.
- Classify driver actions into six categories:
  - ✅ Safe Driving
  - 📞 Talking on the Phone
  - 💬 Texting on the Phone
  - 🔄 Turning
  - 😴 Sleepy (Drowsy)
  - 📦 Other Activities

## 📊 Dataset

- **Base Dataset**: Kaggle Driver Behavior dataset.
- **Augmented with**: Custom class `Sleepy` using frames from YouTube and public repositories.
- **Preprocessing**:
  - Resized to 240×240
  - RGB color space
  - Normalized pixel values [0, 1]
  - Train/Val/Test Split: 70/15/15

## 🧠 Models

### 1. DenseNet121
- Fine-tuned with ImageNet weights.
- Achieved **98.42% test accuracy**.
- Lightweight and suitable for real-time deployment.

### 2. U-Net with EfficientNetB7
- Combines U-Net spatial localization with EfficientNetB7 feature extraction.
- Achieved **91% test accuracy**, strong on detecting 'Sleepy' behavior.
- Struggled with differentiating similar actions like 'Turning'.

### 3. Ensemble Model (Best)
- Combines **AlexNet-like, VGG19, ResNet50**.
- Uses concatenated features + dropout + dense layers.
- Achieved **99.51% test accuracy** and perfect F1-scores for most classes.
- Selected for final deployment.

## 🔔 Distraction Score and Alarm System

- **Distraction Score** = % of distracted frames in video
- **Alarm Triggered**: If any frame is classified as `Sleepy`
- Real-time feedback system with frame-by-frame predictions

## 💻 Real-Time Implementation

- Video processed at 3-second frame intervals
- Frame-wise classification with confidence overlay
- Immediate alerts for dangerous behavior
- Scalable to real-world in-vehicle monitoring systems

## 📈 Results Summary

| Model                | Accuracy | Notable Strengths            |
|---------------------|----------|------------------------------|
| DenseNet121         | 98.42%   | Efficient, high accuracy     |
| U-Net + EfficientNet| 91%      | High precision for drowsiness|
| Ensemble Model       | 99.51%   | Best performer across all classes |

## 👩‍💻 Team Contribution

- **Tanmay Bankar**: Ensemble model development, distraction score, and alarm system
- **Mihika Sanghvi**: UNet-EfficientNetB7 implementation, dataset preprocessing
- **Anushka Agarwal**: DenseNet121 implementation and performance tuning

## 📚 References

- WHO Road Safety Reports
- NHTSA Distracted Driving Statistics
- Deep learning models: AlexNet, ResNet, VGG, EfficientNet, YOLO
- Key Papers on driver monitoring systems and gaze tracking

## 🛠️ Future Work

- Integrate temporal models (e.g., LSTM, TCNs) for smoother transitions
- Deploy on edge devices with optimized inference
- Expand dataset diversity (age, ethnicity, environment)

---

**Columbia University - COMS W4995: Deep Learning for Computer Vision**  
*Spring 2025*
