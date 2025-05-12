# Stress Detection Using Physiological Signals (WESAD Dataset) 📊🧠

This project implements a deep learning approach to binary stress classification using the **WESAD** dataset. We focus specifically on three chest signals: **ECG**, **EDA**, and **RESP**, using a custom 1D CNN model and a segmentation-based preprocessing pipeline.

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
- Selected chest signals: `ECG`, `EDA`, and `RESP`.
- Applied MinMax scaling to normalize each signal independently.
- Segmented time-series data using:
  - Window size: **640 samples** (~5 seconds at 128 Hz)
  - Overlap: **50%**
- Converted original labels into binary:
  - **0** → Non-Stressed (`baseline` + `amusement` + `meditation`)
  - **1** → Stressed (`stress` only)

### 🔍 2. Data Analysis
- Visualized ECG patterns between classes.
- Examined subject-wise distributions.
- Checked for class imbalance and applied countermeasures.

### 🧠 3. Model Architecture
- **1D Convolutional Neural Network (CNN)** using **Keras**:
  - Several `Conv1D + BatchNorm` layers
  - `MaxPooling` + `Dropout` regularization
  - Dense output layer with `sigmoid` activation  
- Input shape: `(640, 3)` → 640 timesteps per window, 3 channels (signals)

### 🏋️ 4. Training Strategy
- Used stratified train-test split to preserve class balance.
- Applied class weights to handle imbalance during training.
- Employed callbacks (`EarlyStopping`, `ModelCheckpoint`) to prevent overfitting.

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
├── models/
│   └── final_binary_1dcnn_class_weights.h5      # Trained model file
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
