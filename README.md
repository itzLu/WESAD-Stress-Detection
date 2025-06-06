# Stress Detection Using Physiological Signals (WESAD Dataset) 📊🧠

This project implements a deep learning approach to binary stress classification using the **WESAD** dataset. We focus specifically on 8 chest signals: **ECG**, **EDA**, **EMG**, **RESP**, **TEMP**, and **ACC-3D**, using a custom 1D CNN model and a segmentation-based preprocessing pipeline.

> 🚀 **Achieved over 99% accuracy** with high generalization across subjects, even after final testing on a *balanced and unseen test set*.

---

## 📁 Dataset

We used the **WESAD** dataset (Wearable Stress and Affect Detection) published by Schmidt et al., containing multimodal physiological recordings from 15 participants.

🔗 [WESAD on Kaggle (Uploaded by us)](https://www.kaggle.com/datasets/mohamedasem318/wesad-full-dataset)  
🔗 [Original Dataset on UCI](https://archive.ics.uci.edu/dataset/465/wesad+wearable+stress+and+affect+detection)  
📄 [Official Paper](https://dl.acm.org/doi/10.1145/3242969.3242985)

---

## 🌐 Infrastructure Note

Due to internet access limitations in Egypt, we used a **Google Cloud VPS** to download and re-host the dataset on Kaggle for easier use in notebooks and pipelines.

---

## ⚙️ Methodology & Pipeline

### 🧹 1. Preprocessing
- **Selected chest signals**: `ECG`, `EDA`, `EMG`, `RESP`, `TEMP`, and `ACC-3D`.
- **Applied Standardization**: Used Z-score standardization (zero mean, unit variance) on the features.
- **Segmented time-series data**:
  - **Window size**: **3500 samples** (~5 seconds at 700 Hz)
  - **Overlap**: **50%** between consecutive windows
- **Converted original labels into binary**:
  - **0** → Non-Stressed (combination of `baseline`, `amusement`, and `meditation` labels)
  - **1** → Stressed (`stress` label only)

### 🔍 2. Data Analysis
- Visualized ECG patterns between classes.
- Examined subject-wise distributions.
- Checked for class imbalance and applied countermeasures.

### 🧠 3. Model Architecture
- **1D Convolutional Neural Network (CNN)** using **Keras**:
  - Several `Conv1D + BatchNorm + MaxPooling` layers
  - `GlobalAveragePooling1D + Dense + Dropout` regularization
  - Dense output layer with `sigmoid` activation  
- Input shape: `[num_windows, 3500, 8]` → 3500 timesteps per window, 8 channels (signals)

### 🏋️ 4. Training Strategy
- **Stratified Train-Test Split**: Used stratified splitting to preserve class balance in the training and validation sets.
- **Class Weighting**: Applied class weights to address class imbalance during training by using `compute_class_weight('balanced')`.
- **Model Compilation**: 
  - **Optimizer**: Used the `Adam` optimizer with a learning rate of **5e-4**.
  - **Loss Function**: Chose `binary_crossentropy` as the loss function for binary classification.
  - **Metrics**: Monitored **accuracy** during training.
- **Early Stopping**: Used `EarlyStopping` callback to monitor `val_loss`, with a patience of 3 epochs to prevent overfitting and restore the best weights.
- **Model Training**: 
  - **Epochs**: 20
  - **Batch size**: 64
  - **Validation Split**: 20% of the data used for validation during training

---

## ✅ Final Evaluation on Balanced Test Set

After training, we tested the final model on a **completely separate and balanced test set**:

- 50% stressed samples, 50% non-stressed.
- Ensured no overlap with training/validation data.
- Objective: confirm true model generalization without class distribution bias.

> 🟢 **The model retained high accuracy and F1-score on this unseen balanced set**, confirming its reliability beyond training assumptions.

---

## 📊 Results Summary

| Metric                  | Value   |
|-------------------------|---------|
| **Training Accuracy**   | ~99.2%  |
| **Validation Accuracy** | ~98.9%  |
| **F1 Score (macro)**    | ~99%    |
| **Balanced Test Set**   | ✅ Passed |

*Confusion matrices and classification reports are available in the notebook output.*

---

## 📂 Repository Structure

```bash
.
├── notebooks/
│   └── Stress-Detection-with-1D-CNN.ipynb       # Final notebook with full pipeline
├── data/
│   └── README.md                                # Dataset access notes
├── figures/
│   └── stressed_vs_notstressed_ecg.png          # ECG comparison plot
│   └── 1d_cnn_model.png                         # Model architecture
├── models/
│   └── Binary_1DCNN_Class_Weights.h5            # Trained model file
├── requirements.txt                             # Dependencies
└── README.md                                    # Project README
```

---

## ▶️ How to Run

```bash
pip install -r requirements.txt
jupyter notebook notebooks/Stress-Detection-with-1D-CNN.ipynb
```

---

## 📌 Credits

- **Dataset**: WESAD by Schmidt et al. (2018)
- **Cloud VPS**: Google Cloud Platform
- **Notebook & Upload**: Developed in Kaggle & pushed to GitHub

---

## 🧠 Authors

- **Amin Maher**  
  [GitHub](https://github.com/amin657) | [Kaggle](https://www.kaggle.com/aminmaher) | [LinkedIn](https://www.linkedin.com/in/amin-maher-0a075b242)
- **Ibrahim Khaled**  
  [GitHub](https://github.com/IbrahimKhaled47) | [Kaggle](https://www.kaggle.com/ibrahimkhaled474) | [LinkedIn](https://www.linkedin.com/in/ibrahimkhaled47)
- **Omar Eldash**  
  [GitHub](https://github.com/Omareldash) | [Kaggle](https://www.kaggle.com/omareldash75) | [LinkedIn](https://www.linkedin.com/in/omareldash7512)
- **Mohamed Asem**  
  [GitHub](https://github.com/itzLu) | [Kaggle](https://www.kaggle.com/mohamedasem318) | [LinkedIn](https://www.linkedin.com/in/mohamedasem318)


---
