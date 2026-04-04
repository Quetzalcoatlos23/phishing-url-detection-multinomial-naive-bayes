# phishing-url-detection-multinomial-naive-bayes
Implementasi algoritma Multinomial Naïve Bayes untuk deteksi phishing URL dengan membandingkan representasi fitur Bag of Words (BoW) dan TF-IDF. Proyek ini merupakan bagian dari penelitian skripsi di Program Studi Teknik Komputer, Universitas Amikom Yogyakarta.
# Phishing URL Detection using Machine Learning

## Ringkasan
Project ini merupakan implementasi sistem deteksi phishing URL menggunakan algoritma Machine Learning, yaitu Multinomial Naïve Bayes. Tujuan dari project ini adalah untuk mengklasifikasikan URL sebagai phishing atau legitimate.

---

## Tools yang digunakan
- Python
- Scikit-learn
- Pandas, NumPy
- Google Colab
- Text Classification Algorithm (Multinomial Naïve Bayes)

---

## Metodologi
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

## Hasil
Berdasarkan hasil pengujian menggunakan representasi fitur BoW, model Multinomial Naïve Bayes mampu melakukan klasifikasi URL ke dalam empat kelas dengan performa yang baik. Hasil ini menunjukkan bahwa pendekatan BoW efektif dalam menangkap pola karakteristik URL pada dataset phishing yang digunakan.

### Classification Report BoW
<img width="530" height="280" alt="Picture1" src="https://github.com/user-attachments/assets/8dabde46-4359-4be9-8d38-27117da8ebae" />

### Classification Report TF-IDF
<img width="525" height="280" alt="Picture2" src="https://github.com/user-attachments/assets/346bab3d-ac0e-4aca-8d49-e341b3fa2813" />

### Confusion Matrix BoW
<img width="460" height="407" alt="Picture3" src="https://github.com/user-attachments/assets/98af8381-42d7-4529-bf83-d67b94674bc0" />

### Confusion Matrix TF-IDF
<img width="482" height="426" alt="Picture4" src="https://github.com/user-attachments/assets/3622bd83-1b83-4231-852b-f09b5f4acb04" />


### Model Performance BoW
- Accuracy: ~78%
- F1 Score: ~78%
- Precision: ~79%
- Recall: ~78%

### Model Performance TF-IDF
- Accuracy: ~77%
- F1 Score: ~79%
- Precision: ~81%
- Recall: ~77%

<p>Meskipun kedua metode tersebut sama-sama kuat, BoW sedikit lebih baik pada ketepatan prediksi kelas mayoritas (benign), sedangkan TF-IDF menunjukkan keunggulan dalam meminimalisir false negative pada kelas phishing. Secara garis besar, kedua metode mampu mengenali seluruh kelas dengan baik, dan perbedaan performanya lebih terlihat pada distribusi jumlah kesalahan prediksi antar kelas, di mana TF-IDF cenderung lebih agresif dalam mendeteksi Phishing meskipun distribusi kesalahan pada kelas Benign sedikit lebih besar dibandingkan BoW.</p>

## Analisis Waktu Komputasi
Selain hal-hal mengenai keakuratan dan metrik klasifikasi, waktu yang dibutuhkan untuk menghitung juga merupakan faktor penting dalam menilai seberapa efisien suatu representasi fitur dalam memproses data dalam jumlah besar. 
<img width="661" height="139" alt="Picture5" src="https://github.com/user-attachments/assets/eb740ffc-c549-4a73-bd68-228dec6e9120" />

- BoW lebih unggul pada tahap ekstraksifitur (vektorisasi)
- TF-IDF sedikit lebih unggul pada tahap eksekusi model (Training+Prediction).

## Hasil Cross Validation
<img width="208" height="100" alt="Picture6" src="https://github.com/user-attachments/assets/125e6794-22a3-4fd0-a127-f511cddedf66" /> 

Hasil 5-Fold Cross Validation menunjukkan bahwa model Multinomial Naïve Bayes dengan representasi fitur BoW memiliki nilai rata-rata akurasi yang tinggi dengan standar deviasi yang rendah. Hal ini mengindikasikan bahwa model memiliki performa yang stabil dan tidak mengalami overfitting terhadap data latih.

## Perbandingan
Perbandingan antara metode BoW dan TF-IDF menunjukkan bahwa:
- Pada perbedaan metrik, BoW sedikit lebih unggul pada Accuracy & Recall. Dan pada waktu, BoW sedikit lebih cepat pada waktu ekstraksi fitur (Vectorization)
- Sedangkan TF-IDF lebih unggul pada Precision di beberapa Kelas, serta F1-Score. Lalu untuk waktu sendiri, TF-IDF lebih cepat pada waktu eksekusi model (Training+Prediction)
---

## How to Run
1. Clone repository:
```bash
git clone https://github.com/username/phishing-url-detection.git
