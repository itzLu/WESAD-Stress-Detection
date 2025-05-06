# Stress Detection Using Physiological Signals (WESAD Dataset) 📊🧠

This project explores the use of deep learning models for binary classification of stress using the WESAD dataset. It focuses on ECG, EDA, and RESP signals to determine whether a subject is stressed or not.

---

## 📁 Dataset

We use the **WESAD** dataset (Wearable Stress and Affect Detection) by Schmidt et al., which contains physiological signals from 15 participants. Since this dataset is not available on Kaggle by default, we uploaded it to a public Kaggle dataset:

🔗 [WESAD on Kaggle (Uploaded by us)](https://www.kaggle.com/datasets/mohamedasem318/wesad-full-dataset)

📌 **Original dataset citation**:
> Philipp Schmidt, Attila Reiss, Robert Duerichen, Claus Marberger, and Kristof Van Laerhoven. "Introducing WESAD, a Multimodal Dataset for Wearable Stress and Affect Detection." In Proceedings of the 20th ACM International Conference on Multimodal Interaction, 2018.  
> [Link to paper](https://dl.acm.org/doi/10.1145/3242969.3242985)  
> [Original WESAD Dataset on UCI](https://archive.ics.uci.edu/dataset/465/wesad+wearable+stress+and+affect+detection)

---

## 🌐 Infrastructure

To upload the dataset to Kaggle (due to internet limitations in Egypt), we created a **Google Cloud VPS** instance. This made it possible to download the original dataset from UCI and re-upload it to Kaggle.

---

## 🧪 Methodology

1. **Data Preprocessing**
   - Extracted chest-related signals (ECG, EDA, RESP) for all subjects.
   - Normalized signals using MinMaxScaler.
   - Segmented time-series data into overlapping windows.
   - Created binary labels (0 = Not Stressed, 1 = Stressed).

2. **Visualization**
   - Plotted ECG samples for stressed vs. non-stressed participants.
   - Graphed class distribution to ensure balanced training.

3. **Modeling**
   - Used a fully connected deep learning model via **Keras**.
   - Input shape: 900 (segmented data across the 3 signals).
   - Binary classification with sigmoid activation.

4. **Evaluation**
   - Accuracy, precision, recall, and F1 score calculated.
   - Confusion matrix and classification report provided.

---

## 📊 Results

The model achieved high accuracy and solid performance metrics across multiple subjects. The results confirm that even with a simple architecture, stress can be predicted using physiological signals.

---

## 📂 Repository Structure

```bash
.
├── notebooks/
│   └── Stress-Detection-with-1D-CNN.ipynb       # Final Jupyter Notebook
├── data/
│   └── README.md                              # Instructions on accessing the dataset
├── figures/
│   └── stressed_vs_notstressed_ecg.png        # Visual comparison
├── models/
│   └── final_binary_1dcnn_class_weights.h5    # Exported model (including architecture and weights)
├── requirements.txt                           # Required Python packages
└── README.md                                  # Project description
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
- **Ibrahim Khaled**
- **Omar Mohamed**  
  [GitHub](https://github.com/Omareldash) | [Kaggle](https://www.kaggle.com/omareldash75) | [LinkedIn](https://www.linkedin.com/in/omareldash7512)
- **Mohamed Asem**  
  [GitHub](https://github.com/itzLu) | [Kaggle](https://www.kaggle.com/mohamedasem318) | [LinkedIn](https://www.linkedin.com/in/mohamedasem318)


---
