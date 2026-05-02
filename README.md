# phishing-url-detection-multinomial-naive-bayes
Implementasi algoritma Multinomial Naïve Bayes untuk deteksi phishing URL dengan membandingkan representasi fitur Bag-of-Words (BoW) dan TF-IDF. Proyek ini merupakan bagian dari penelitian skripsi di Program Studi Teknik Komputer, Universitas Amikom Yogyakarta dengan judul Skripsi:
# "Multinomial Naïve Bayes untuk Deteksi Phishing Dengan Perbandingan Representasi Fitur Bag of Words dan TF-IDF"

## Ringkasan
Proyek ini merupakan penelitian tugas akhir yang berfokus pada deteksi keamanan siber, khususnya klasifikasi URL phishing. Mengingat ancaman serangan siber yang terus meningkat, sistem ini dikembangkan untuk secara otomatis mengidentifikasi URL berbahaya menggunakan pendekatan Machine Learning.

## Technical Workflow
1. **Preprocessing Data:** Pembersihan data URL mentah untuk menghilangkan *Noise*
2. **Feature Representation:** Mengonversi teks URL menjadi bentuk numerik menggunakan dua metode:
    - **Bag of Words (BoW):** Menghitung frekuensi kemunculan kata dalam dataset.
    - **Term Frequency-Inverse Document Frequency (TF-IDF):** Menghitung bobot kepentingan kata berdasarkan kelangkaannya di seluruh dokumen.
3. **Synthetic Minority Oversampling Technique (SMOTE):** Mengatasi masalah ketidakseimbangan dataset *(imbalanced dataset)* dengan menerapkan teknik SMOTE pada data yang telah di-vektorisasi (data numerik).
4. **Classification:** Menggunakan algoritma Multinomial Naive Bayes (MNB) yang sangat efektif untuk tugas klasifikasi teks dan data frekuensi.

---

## Tools yang digunakan
- Python
- Scikit-learn
- Pandas, NumPy
- Google Colab
- Text Classification Algorithm (Multinomial Naïve Bayes)

---
---

## Dataset yang Digunakan
Source: https://www.kaggle.com/datasets/sid321axn/malicious-urls-dataset

<img width="790" height="590" alt="image" src="https://github.com/user-attachments/assets/3d2239fd-c84c-4d20-a0a1-8dc88e33d63b" />

Terlihat bahwa jumlah data pada setiap kelas tidak merata. Kelas URL yang tidak berbahaya memiliki jumlah data yang jauh lebih banyak dibandingkan kelas URL phishing dan kategori URL lainnya. Situasi ini menunjukkan adanya masalah ketidakseimbangan data, yang bisa mengganggu kemampuan model klasifikasi, terutama dalam mengenali kelas dengan jumlah data lebih sedikit seperti phishing.
Ketidakseimbangan jumlah data bisa membuat model cenderung memprediksi kelas yang lebih banyak dan mengabaikan kelas yang sedikit. Meskipun akurasi model terlihat tinggi, kemampuannya dalam mendeteksi URL phishing mungkin belum cukup baik. Untuk mengatasi ini, digunakanlah metode SMOTE pada data latih untuk meningkatkan jumlah data kelas minoritas dan membantu model memahami pola URL phishing secara lebih baik.

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

## Alur Pengujian Model
<img width="294" height="560" alt="Picture7" src="https://github.com/user-attachments/assets/d2599589-ccfd-407f-b9d1-0099050c1c64" />

---

---

## Code Snippet
1. **Data Preprocessing:**

   Tahap text preprocessing dilakukan untuk membersihkan data URL sebelum masuk ke proses pembobotan dan klasifikasi. Data URL yang masih dalam bentuk mentah biasanya mengandung berbagai unsur yang tidak penting, seperti protokol HTTP/HTTPS, simbol khusus, angka, serta variasi penulisan huruf yang tidak konsisten.
   ```def clean_url(url):
    url = re.sub(r'^https?:\/\/', '', url)
    url = re.sub(r'www\.', '', url)
    url = re.sub(r'[\/:._=?\-&%]', ' ', url)
    url = re.sub(r'[^a-zA-Z]', ' ', url)
    url = re.sub(r'\s+', ' ', url).strip().lower()
    return url

   dataset["clean_url"] = dataset["url"].apply(clean_url)
   ```
2. **Feature Extraction (BoW & TF-IDF):**

   Bagian ini menunjukkan bagaimana mesin mengubah teks URL mentah menjadi data numerik. Ini adalah langkah krusial sebelum masuk ke pemrosesan data lainnya.
   ```
   from sklearn.feature_extraction.text import CountVectorizer, TfidfVectorizer

   vectorizers = {
    "BoW": CountVectorizer(analyzer='char', ngram_range=(3,5), max_features=10000),
    "TF-IDF": TfidfVectorizer(analyzer='char', ngram_range=(3,5), max_features=10000)
   }
   ```
   
3. **Menangani Imbalanced Dataset (SMOTE):**

   SMOTE diterapkan hanya pada data latih hasil vektorisasi dengan tujuan untuk mengatasi ketidakseimbangan jumlah data antar kelas URL
   ```
   from imblearn.over_sampling import SMOTE
   smote = SMOTE(random_state=42)
    X_train_bal, y_train_bal = smote.fit_resample(X_train_vec, y_train)
   ```

   

## Hasil
Berdasarkan hasil pengujian menggunakan representasi fitur BoW, model Multinomial Naïve Bayes mampu melakukan klasifikasi URL ke dalam empat kelas dengan performa yang baik. Hasil ini menunjukkan bahwa pendekatan BoW efektif dalam menangkap pola karakteristik URL pada dataset phishing yang digunakan.

### Classification Report BoW
<img width="530" height="280" alt="Picture1" src="https://github.com/user-attachments/assets/8dabde46-4359-4be9-8d38-27117da8ebae" />

### Classification Report TF-IDF
<img width="525" height="280" alt="Picture2" src="https://github.com/user-attachments/assets/346bab3d-ac0e-4aca-8d49-e341b3fa2813" />

### Confusion Matrix BoW
<img width="531" height="470" alt="image" src="https://github.com/user-attachments/assets/9b8493f2-96d2-4613-b3bb-1c0e5f8e0a8e" />


### Confusion Matrix TF-IDF
<img width="531" height="470" alt="image" src="https://github.com/user-attachments/assets/41de6d75-082e-4ab6-be8e-b2304602d4bf" />



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

---

## Analisis Waktu Komputasi
Selain hal-hal mengenai keakuratan dan metrik klasifikasi, waktu yang dibutuhkan untuk menghitung juga merupakan faktor penting dalam menilai seberapa efisien suatu representasi fitur dalam memproses data dalam jumlah besar. 
<img width="661" height="139" alt="Picture5" src="https://github.com/user-attachments/assets/eb740ffc-c549-4a73-bd68-228dec6e9120" />

- BoW lebih unggul pada tahap ekstraksifitur (vektorisasi)
- TF-IDF sedikit lebih unggul pada tahap eksekusi model (Training+Prediction).

---
## Hasil Cross Validation
<img width="208" height="100" alt="Picture6" src="https://github.com/user-attachments/assets/125e6794-22a3-4fd0-a127-f511cddedf66" /> 

Hasil 5-Fold Cross Validation menunjukkan bahwa model Multinomial Naïve Bayes dengan representasi fitur BoW memiliki nilai rata-rata akurasi yang tinggi dengan standar deviasi yang rendah. Hal ini mengindikasikan bahwa model memiliki performa yang stabil dan tidak mengalami overfitting terhadap data latih.

---
## Perbandingan F1-Score
<img width="889" height="490" alt="image" src="https://github.com/user-attachments/assets/1dc7ea5d-8b8b-4b92-9dc7-82a6aa744678" />

---
## Perbandingan
Perbandingan antara metode BoW dan TF-IDF menunjukkan bahwa:
- Pada perbedaan metrik, BoW sedikit lebih unggul pada Accuracy & Recall. Dan pada waktu, BoW sedikit lebih cepat pada waktu ekstraksi fitur (Vectorization)
- Sedangkan TF-IDF lebih unggul pada Precision di beberapa Kelas, serta F1-Score. Lalu untuk waktu sendiri, TF-IDF lebih cepat pada waktu eksekusi model (Training+Prediction)
---

## How to Run
1. Clone repository:
```bash
git clone https://github.com/Quetzalcoatlos23/phishing-url-detection-multinomial-naive-bayes.git
