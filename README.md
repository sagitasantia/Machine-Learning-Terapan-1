Baik! Saya sudah melihat isi notebook dan struktur proyek kamu di PDF tadi. Berikut saya bantu buatkan **Detail Laporan** lengkap mulai dari Domain hingga Evaluasi, disesuaikan dengan hasil ipynb dan kriteria submission.

---

# **Detail Laporan: Prediksi Harga Rumah Jakarta Selatan**

---

## **1. Domain Proyek**

Permasalahan harga properti di Jakarta, khususnya di Jakarta Selatan, menjadi salah satu tantangan yang dihadapi masyarakat saat ini. Berdasarkan data dari [Antara News](https://www.antaranews.com/berita/4632209/ingin-beli-rumah-di-jakarta-selatan-segini-harganya-di-tahun-2025), harga rumah di Jakarta Selatan pada tahun 2025 rata-rata mencapai **Rp 1,4 miliar hingga Rp 40 miliar**, tergantung pada lokasi, ukuran, dan fasilitas.

Selain itu, riset dari [Bisa.ai](https://bisa.ai/portofolio/detail/MjQzOA) menunjukkan bahwa harga rumah sangat dipengaruhi oleh berbagai faktor seperti luas tanah, luas bangunan, jumlah kamar, dan ketersediaan garasi.

Oleh karena itu, prediksi harga rumah secara akurat menggunakan machine learning dapat membantu masyarakat (baik pembeli maupun penjual) dalam menentukan harga properti yang sesuai.

**Sumber Data:**
Dataset diambil dari Kaggle:  
[Daftar Harga Rumah - Kaggle](https://www.kaggle.com/datasets/wisnuanggara/daftar-harga-rumah)

---

## **2. Business Understanding**

### **Problem Statement:**
- Bagaimana memprediksi harga rumah di Jakarta Selatan dengan akurat menggunakan fitur seperti luas tanah, bangunan, jumlah kamar, dll?
- Fitur apa saja yang paling berpengaruh terhadap harga rumah di Jakarta Selatan?

### **Goals:**
1. Membangun model machine learning yang dapat memprediksi harga rumah di Jakarta Selatan.
2. Mengidentifikasi variabel yang paling mempengaruhi harga rumah.

### **Solution Statements:**
1. Melakukan **EDA (Exploratory Data Analysis)** untuk melihat korelasi antara fitur (LT, LB, JKT, JKM, GRS) dengan harga rumah.
2. Membangun beberapa model Machine Learning:
   - **XGBoost Regressor**
   - **Random Forest Regressor**
   - **K-Nearest Neighbors (KNN)**
3. Melakukan **Hyperparameter Tuning** menggunakan GridSearchCV untuk meningkatkan performa model.
4. Mengukur performa model dengan metrik **Mean Absolute Error (MAE)** dan **R² Score**.

---

## **3. Data Understanding**

### **Dataset Overview:**
- Jumlah Data: **1001 entri**
- Fitur:
  - **HARGA**: Harga rumah (target)
  - **LT**: Luas Tanah (m²)
  - **LB**: Luas Bangunan (m²)
  - **JKT**: Jumlah Kamar Tidur
  - **JKM**: Jumlah Kamar Mandi
  - **GRS**: Ketersediaan Garasi (Ada/Tidak Ada → diubah ke binary)
  - **KOTA**: Nama Kota (semua entri adalah Jakarta Selatan, di-drop)

### **Data Exploration:**
- Distribusi harga sangat **right-skewed**, terdapat banyak outlier.
- Korelasi tinggi antara **LT, LB** dengan harga rumah.
- Visualisasi yang dilakukan: Histplot, Boxplot, Scatterplot, Korelasi Matriks (Heatmap).

---

## **4. Data Preparation**

### **Langkah yang dilakukan:**
1. **Data Cleaning:**
   - Kolom `HARGA` dibersihkan (hapus tanda titik, koma, diubah ke integer).
   - Kolom `GRS` diubah ke binary (1 = Ada Garasi, 0 = Tidak Ada).
2. **Handling Outliers:**
   - Menggunakan metode **IQR (Interquartile Range)** untuk menghapus outlier pada kolom `HARGA`.
3. **Feature Selection:**
   - Drop kolom `KOTA` karena tidak memberikan informasi variatif.
4. **Scaling:**
   - Menggunakan **StandardScaler** sebelum modeling karena beberapa model seperti KNN & SVR sensitif terhadap skala fitur.
5. **Splitting:**
   - Train-test split sebesar **70:30**.

---

## **5. Modeling**

### **Model yang digunakan:**

1. **XGBoost Regressor**
   - Parameter default: n_estimators=100, max_depth=5, learning_rate=0.1
2. **Random Forest Regressor**
   - Parameter default: n_estimators=100
3. **K-Nearest Neighbors (KNN)**
   - Default n_neighbors=5

### **Hyperparameter Tuning:**
Dilakukan GridSearchCV dengan parameter:

- **XGBoost:**
  - `n_estimators`: [100, 200, 300]
  - `max_depth`: [3, 5, 7]
  - `learning_rate`: [0.1, 0.01, 0.001]
  
- **Random Forest:**
  - `n_estimators`: [100, 200, 300]
  - `max_depth`: [None, 5, 10]
  - `min_samples_split`: [2, 5, 10]
  
- **KNN:**
  - `n_neighbors`: [3, 5, 7, 9]
  - `weights`: ['uniform', 'distance']
  - `metric`: ['euclidean', 'manhattan']

---

## **6. Evaluation**

### **Metrik Evaluasi:**
- **Mean Absolute Error (MAE)**: Mengukur rata-rata selisih absolut antara prediksi dan nilai aktual.
- **R² Score**: Mengukur seberapa besar variansi harga rumah dapat dijelaskan oleh model.

### **Hasil Evaluasi Akhir:**

| Model               | MAE             | R² Score |
|--------------------|----------------|---------|
| **XGBoost (Tuned)** | Rp 3.07 Miliar | 0.74    |
| **Random Forest (Tuned)** | Rp 2.91 Miliar | **0.76** |
| **KNN (Tuned)**     | Rp 3.31 Miliar | 0.68    |

**Kesimpulan:**
- **Random Forest Regressor** menghasilkan performa terbaik dengan R² Score tertinggi 0.76 dan MAE Rp 2.91 Miliar.
- Random Forest dipilih sebagai model terbaik karena kestabilannya terhadap outlier dan kemampuan menangkap hubungan non-linear.

---

## **Referensi:**

1. Bisa.ai Portofolio, Prediksi Harga Rumah: [https://bisa.ai/portofolio/detail/MjQzOA](https://bisa.ai/portofolio/detail/MjQzOA)
2. Antaranews, Harga Rumah Jakarta Selatan 2025: [https://www.antaranews.com/berita/4632209/ingin-beli-rumah-di-jakarta-selatan-segini-harganya-di-tahun-2025](https://www.antaranews.com/berita/4632209/ingin-beli-rumah-di-jakarta-selatan-segini-harganya-di-tahun-2025)
3. Dataset: [https://www.kaggle.com/datasets/wisnuanggara/daftar-harga-rumah](https://www.kaggle.com/datasets/wisnuanggara/daftar-harga-rumah)
