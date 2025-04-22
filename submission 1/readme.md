# Laporan Proyek Machine Learning - Nama Anda

# Domain Proyek

---

Diabetes merupakan salah satu penyakit kronis paling umum di dunia yang dapat menyebabkan komplikasi serius seperti penyakit jantung, gagal ginjal, gangguan penglihatan, bahkan kematian jika tidak ditangani sejak dini. Menurut World Health Organization (WHO), sekitar 422 juta orang di seluruh dunia menderita diabetes, dan jumlah ini terus meningkat setiap tahunnya [1].

Pendeteksian dini dan intervensi berbasis data dapat membantu mengurangi beban sistem kesehatan dan meningkatkan kualitas hidup pasien. Oleh karena itu, dibutuhkan sistem cerdas berbasis pembelajaran mesin (machine learning) yang mampu memprediksi kemungkinan seseorang mengidap diabetes berdasarkan data klinis dan demografis yang mudah dikumpulkan.

# Business Understanding

---

### Problem Statements

Menjelaskan pernyataan masalah latar belakang:

- Bagaimana memprediksi apakah seseorang berisiko mengidap diabetes berdasarkan data seperti usia, BMI, tekanan darah, dan kadar glukosa darah?

- Dapatkah kita membangun model prediktif yang akurat dan berguna untuk membantu tenaga medis dalam mendeteksi diabetes secara dini?

### Goals

- Membangun model klasifikasi yang mampu memprediksi diabetes (ya/tidak) berdasarkan fitur-fitur seperti usia, jenis kelamin, riwayat merokok, tekanan darah, dan kadar HbA1c.

- Menyediakan alat bantu keputusan berbasis AI/ML untuk dokter atau penyedia layanan kesehatan guna melakukan skrining awal.

### Solution statements

- Membuat beberapa model machine learning, diantaranya:
  - Decision tree
  - Random Forest
  - Support Vector Machine (SVM)
- Menggunakan hypermeter tuning untuk meningkatkan performa akurasi.

# Data Understanding

Jenis | Keterangan
Sumber | : [Kaggle](https://www.kaggle.com/datasets/iammustafatz/diabetes-prediction-dataset)
Kategori | Kesehatan
Ukuran File | CSV (3,7MB)

---

### Variabel-variabel pada Diabetes Prediction dataset adalah sebagai berikut:

- gender: Jenis kelamin
- age: Usia
- hypertension: Riwayat hipertensi
- heart_disease: Riwayat penyakit jantung
- smoking_history: Riwayat merokok
- bmi: Body Mass Index
- HbA1c_level: Level HbA1c
- blood_glucose_level: Kadar glukosa dalam darah
- diabetes: Label target (0 = tidak diabetes, 1 = diabetes)

---

## Exploratory Data Analysis (EDA)

Untuk memahami data prediksi diabetes dilakukan analisis eksploratif menggunakan grafik dan visualisasi:

1. Distribusi nilai age, bmi, HbA1c_level, dan blood_glucose_level
![distribution_data]( "Gambar Sebaran Dataset")

> Gambar 3.1 Korelasi umur dengan fitur lainnya

2. Proporsi jumlah penderita diabetes vs tidak
3. Korelasi antar fitur numerik terhadap label diabetes

![correlation_label]( "Gambar Korelasi antar label")

> Gambar 3.2 Korelasi umur dengan fitur lainnya

# Data Preparation

---

## Tahap preparation

1. Menangani data kategori (gender, smoking_history) menggunakan teknik encoding.
2. Menormalisasi fitur numerik (age, bmi, dll) untuk memastikan kesetaraan skala.
3. Membagi data menjadi training dan test dengan rasio 80:20.

# Modeling

---

Algoritma yang digunakan pada model klasifikasi ini adalah sebagai berikut:

1. Decision Tree
   Membagi data berdasarkan fitur yang paling informatif menggunakan struktur pohon. Kelebihan: Mudah diinterpretasi, depat dalam melakukan pelatihan model. Kekurangan: Rentan terhadap overfitting jika tidak dilakukan pengeliminasian.
2. Random Forest
   Menggunakan banyak pohon keputusan dan melakukan voting untuk hasil akhir.
3. Support Vector Machine (SVM)
   Memisahkan kelas hyperplane optimal di ruang vektor tinggi.

# Evaluation

---

Pada proyek ini menggunakan model _deep learning_ bertipe _classification_ yang berarti jika mendekati 100% accuracy, performanya baik, sedangkan jika dibawah 75%, maka performanya buruk.
Metrik yang akan kita gunakan pada prediksi ini adalah _Accuracy_, metrik ini menghitung jumlah prediksi yang benar selisih total prediksi yang dilakukan. Accuracy didefinisikan dalam persamaan berikut:  
$\text{Accuracy} = \frac{TP+TN}{TP+TN+FP+FN}$

Selain metrik _accuracy_ akan digunakan _precision, recall, dan f1-score_ yang dibuat dengan fungsi _classification_report_ yang disediakan oleh _library sklearn_

Presisi digunakan untuk mengukur seberapa dapat diandalkan sebuah model ketika memberikan prediksi terhadap suatu kelas/_target_. Presisi dapat didefinisikan sebagai berikut:  
$\text{Precision} = \frac{TP}{TP+FP}$

_Recall_ digunakan untuk mengukur kemampuan model untuk memprediksi kelas _True Positive. Recall_ dapat didefinisikan sebagai berikut:  
$\text{Recall} = \frac{TP}{TP+FN}$

_F1-Score_ digunakan untuk mencari titik seimbang antara Presisi dan _Recall_, _F1-Score_ didefinisikan sebagai berikut:  
$\text{F1-Score} = \frac{2 \* Precision \* Recall}{Precision+Recall}$

Dengan:

- TP: True Positive
- TN: True Negative
- FP: False Positive
- FN: False Negative
  ![Comparison_model]("Perbandingan performa model")

# Referensi

---

1. World Health Organization (WHO). (2021). Diabetes Fact Sheet. Retrieved from: https://www.who.int/news-room/fact-sheets/detail/diabetes

2. Chaki, J., Ganatra, A., & Pethakar, M. (2019). Machine Learning and Artificial Intelligence Based Diabetes Diagnosis: A Review. In Advances in Computer Vision and Artificial Intelligence. Springer.

3. Kavakiotis, I., Tsave, O., Salifoglou, A., Maglaveras, N., Vlahavas, I., & Chouvarda, I. (2017). Machine Learning and Data Mining Methods in Diabetes Research. Computational and Structural Biotechnology Journal, 15, 104-116. https://doi.org/10.1016/j.csbj.2016.12.005

4. American Diabetes Association. (2022). Standards of Medical Care in Diabetes. Diabetes Care, 45(Supplement_1):S1–S2.
