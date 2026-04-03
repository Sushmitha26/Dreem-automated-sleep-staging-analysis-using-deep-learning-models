# Dreem Automated Sleep Staging

This project focuses on automated sleep stage classification using physiological signals collected from the Dreem Headband dataset. The goal is to classify 30-second sleep epochs into five stages: Wake, N1, N2, N3, and REM using EEG and accelerometer data. The project explores both classical machine learning and deep learning approaches, including transfer learning for improved performance.

## Project Overview

Sleep staging is an important task in sleep analysis and healthcare. Manual scoring is time-consuming and depends on expert interpretation, so this project builds an end-to-end pipeline to automate the process using signal preprocessing, feature extraction, model training, and evaluation. The work compares multiple approaches to understand which methods perform best on wearable EEG data.

## Dataset

The project uses the Dreem Automated Sleep Staging dataset. Each recording corresponds to one night of sleep and contains multimodal sensor data:

- 5 EEG channels sampled at 250 Hz
- 3 accelerometer channels sampled at 50 Hz
- labels for five sleep stages: Wake, N1, N2, N3, and REM

The dataset is organized into 30-second epochs, with labels provided in a CSV file that maps each epoch to its target sleep stage.

## Workflow

The overall pipeline includes the following steps:

1. **Data preprocessing**
   - Resampling signals to a uniform frequency
   - Band-pass filtering to remove drift and noise
   - Interpolation and normalization where required

2. **Feature extraction**
   - Time-domain features such as mean, standard deviation, RMS, and zero-crossing rate
   - Frequency-domain features such as dominant frequency, spectral energy, and entropy

3. **Model development**
   - Classical ML models: Decision Tree, Random Forest, SVM, Naive Bayes, Logistic Regression, AdaBoost, and XGBoost
   - Deep learning models: CNN, RNN, MobileNetV2-based transfer learning, and CNN-BiLSTM hybrid

4. **Evaluation**
   - Standard train/test splits
   - LOEO and LOSO validation
   - Metrics: Accuracy, Precision, Recall, F1-score, and Cohen’s kappa

## Models Explored

### Classical Machine Learning

Classical models were trained on handcrafted EEG and accelerometer features. Among these, ensemble methods performed best, especially XGBoost and Random Forest.

### Deep Learning

Deep learning experiments included CNN and RNN models trained from scratch, but these showed limited generalization and strong effects of class imbalance. Transfer learning with MobileNetV2 improved performance significantly over scratch models.

## Key Results

- Ensemble ML models outperformed most single models on handcrafted features
- XGBoost gave the best overall classical ML performance
- Transfer learning clearly improved deep learning performance over scratch CNN/RNN models
- EEG-based features were more informative than accelerometer features for sleep-stage prediction
- Minority classes such as N1 remained the hardest to classify because of class imbalance

## Main Takeaways

This project shows that automated sleep staging can be effectively performed using wearable EEG data. Classical ensemble models like XGBoost achieved the strongest results on extracted features, while transfer learning provided the best deep learning performance and showed strong potential for scalable wearable health applications.

## Tech Stack

- Python
- NumPy
- pandas
- SciPy
- scikit-learn
- XGBoost
- TensorFlow / Keras
- Matplotlib

## Future Work

- Apply class-balanced or focal loss
- Use attention or Transformer-based temporal modeling
- Improve multimodal fusion of EEG and accelerometer signals
- Add data augmentation for better minority-class generalization
