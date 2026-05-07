###1
This notebook implements an automated system for real-time road surface quality monitoring and risk assessment using computer vision and deep learning.

Key Features:
Live Stream Integration: Uses yt-dlp and OpenCV to stream and process video directly from YouTube.
AI-Powered Classification: Employs a pre-trained Keras model (asphalt_model.h5) to classify road segments into three categories: Good, Regular, and Bad.
Dynamic Risk Assessment: Calculates a real-time risk status (Low, Medium, or High) based on the frequency and severity of detected road conditions.
Interactive Visualization: Features a dual-panel UI showing the live video feed with an augmented reality (AR) overlay and a real-time bar chart tracking classification distribution.
Automated Preprocessing: Resizes and normalizes video frames on-the-fly to match the neural network's input requirements.

###2
Road Quality Classification
This project focuses on classifying asphalt surface conditions (Bad, Good, Regular) using deep learning. Below is a step-by-step summary of the work performed:

1. Data Preparation
Source: Images loaded from Google Drive, categorized into three classes: asphaltBad, asphaltGood, and asphaltRegular.
Pre-processing: Images were resized to 224x224 pixels and split into training (75%), validation (15%) and test(15%) sets.
Optimization: Used cache() and prefetch() to improve data pipeline efficiency during training.
2. Model Architecture (Transfer Learning)
Base Model: Utilized MobileNetV2 (pre-trained on ImageNet) for its efficiency on edge devices.
Customization: Freezed the base layers and added a Global Average Pooling layer, a Dropout layer (0.2), and a Softmax Dense layer for 3-class classification.
3. Training & Results
Compilation: Used the Adam optimizer and Sparse Categorical Crossentropy loss function.
Performance: The model was trained for 10 epochs, achieving a high validation accuracy of ~98%.
4. Evaluation
Visualization: Generated plots for training/validation accuracy and loss to monitor convergence.
Metrics: Created a Confusion Matrix and Classification Report. The model showed excellent F1-scores, particularly for the 'Good' class (99%), with minimal confusion between 'Bad' and 'Regular' types.
5. Deployment
Persistence: The trained model was saved to Google Drive in .h5 format and verified by reloading it for sample inference.
