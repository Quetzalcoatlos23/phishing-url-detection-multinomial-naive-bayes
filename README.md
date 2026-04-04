# phishing-url-detection-multinomial-naive-bayes
Implementasi algoritma Multinomial Naïve Bayes untuk deteksi phishing URL dengan membandingkan representasi fitur Bag of Words (BoW) dan TF-IDF. Proyek ini merupakan bagian dari penelitian skripsi di Program Studi Teknik Komputer, Universitas Amikom Yogyakarta.
# Phishing URL Detection using Machine Learning

## Overview
Project ini merupakan implementasi sistem deteksi phishing URL menggunakan algoritma Machine Learning, yaitu Multinomial Naïve Bayes. Tujuan dari project ini adalah untuk mengklasifikasikan URL sebagai phishing atau legitimate.

---

## Technologies Used
- Python
- Scikit-learn
- Pandas, NumPy
- Google Colab
- Text Classification Algorithm (Multinomial Naïve Bayes)

---

## Methodology
1. Data Preprocessing
2. Feature Extraction:
   - Bag of Words (BoW)
   - Term Frequency-Inverse Document Frequency (TF-IDF)
3. Handling Imbalanced Data:
   - Synthetic Minority Oversampling Technique (SMOTE)
4. Model Training:
   - Multinomial Naïve Bayes
5. Evaluation:
   - Accuracy
   - Precision
   - Recall
   - F1-Score
   - Cross Validation

---

## Results
Berdasarkan hasil pengujian menggunakan representasi fitur BoW, model Multinomial Naïve Bayes mampu melakukan klasifikasi URL ke dalam empat kelas dengan performa yang baik. Hasil ini menunjukkan bahwa pendekatan BoW efektif dalam menangkap pola karakteristik URL pada dataset phishing yang digunakan.

### Classification Report BoW
![Classification Report BoW]
### Confusion Matrix
![Confusion Matrix](images/confusion_matrix.png)

### Model Performance
- Accuracy: ~78%
- F1 Score: (isi dari hasil kamu)

---

## 📈 Comparison
Perbandingan antara metode BoW dan TF-IDF menunjukkan bahwa:
- TF-IDF memberikan performa yang lebih stabil
- BoW lebih sederhana namun kurang optimal

---

## 🚀 How to Run
1. Clone repository:
```bash
git clone https://github.com/username/phishing-url-detecti<img width="530" height="280" alt="Picture1" src="https://github.com/user-attachments/assets/2c3a5acb-56a7-46b1-b6e0-b3bf672ee079" />
on.git
![Uploading Picture1.png…]()
