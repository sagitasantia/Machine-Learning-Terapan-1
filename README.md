# **Laporan Proyek Machine Learning Terapan**
# **Anggraini Sagita Santia Putri**
---

# **Detail Laporan: Prediksi Harga Rumah Jakarta Selatan🏠🏘️🏡**

---

## **1. Domain Proyek**

Permasalahan harga properti di Jakarta, khususnya di Jakarta Selatan, menjadi salah satu tantangan yang dihadapi masyarakat saat ini. Berdasarkan data dari [Antara News](https://www.antaranews.com/berita/4632209/ingin-beli-rumah-di-jakarta-selatan-segini-harganya-di-tahun-2025), harga rumah di Jakarta Selatan pada tahun 2025 rata-rata mencapai **Rp 1,4 miliar hingga Rp 40 miliar**, tergantung pada lokasi, ukuran, dan fasilitas.

Selain itu, riset dari [Bisa.ai](https://bisa.ai/portofolio/detail/MjQzOA) menunjukkan bahwa harga rumah sangat dipengaruhi oleh berbagai faktor seperti luas tanah, luas bangunan, jumlah kamar, dan ketersediaan garasi.

Oleh karena itu, prediksi harga rumah secara akurat menggunakan machine learning dapat membantu masyarakat (baik pembeli maupun penjual) dalam menentukan harga properti yang sesuai.

---

## **2. Business Understanding**

### **Problem Statement:**
# **Bussiness Understanding**

## Problem Statement:

Saat ini, menentukan harga rumah yang sesuai cukup sulit karena ada banyak faktor yang mempengaruhinya. Setiap rumah memiliki kondisi yang berbeda, seperti luas bangunan, jumlah kamar tidur, jumlah kamar mandi, dan ketersediaan garasi. Hal ini membuat masyarakat, baik pembeli maupun penjual, kesulitan mengetahui apakah harga rumah tersebut terlalu mahal atau terlalu murah. Pembeli tidak ingin membeli rumah yang kemahalan, sedangkan penjual tidak ingin rugi karena menjual rumah di bawah harga pasaran.

## Goals:

1. Membuat model prediksi harga rumah di daerah Tebet, Jakarta Selatan.
2. Mengetahui faktor apa saja yang paling berpengaruh terhadap harga rumah.

## Solution Statements:

1. Melakukan Exploratory Data Analysis (EDA) untuk mengetahui hubungan antara fitur-fitur seperti luas bangunan, jumlah kamar, dan fasilitas lainnya terhadap harga rumah.
2. Membangun model Machine Learning untuk memprediksi harga rumah di daerah Tebet, Jakarta Selatan menggunakan dua algoritma, yaituRandom Forest Regressor, XGBoost Regressor ,KNN Regressor
---

## **3. Data Understanding**
Adapun dataset yang digunakan diperoleh melalui situs kaggle yang dapat diunduh melalui [Daftar Harga Rumah - Kaggle](https://www.kaggle.com/datasets/wisnuanggara/daftar-harga-rumah)

### **Dataset Overview:**
![image](https://github.com/user-attachments/assets/2ee3215b-9aff-4093-96e0-e9e9a6ec25e3)

- Jumlah Data: **1001 entri**
- Fitur:
  - **HARGA**: Harga rumah 
  - **LT**: Luas Tanah (m²)
  - **LB**: Luas Bangunan (m²)
  - **JKT**: Jumlah Kamar Tidur
  - **JKM**: Jumlah Kamar Mandi
  - **GRS**: Ketersediaan Garasi 
  - **KOTA**: Nama Kota 


## **Data Exploration:**
### EDA Univariate
![download](https://github.com/user-attachments/assets/908bc468-a62f-4e66-a15a-ecdcce418c13)

Grafik ini menunjukkan penyebaran harga rumah yang ada di data. Dari grafik tersebut, bisa dilihat bahwa sebagian besar harga rumah berada di kisaran yang cukup rendah hingga menengah. Semakin tinggi harga rumah, jumlahnya semakin sedikit. Ini artinya, rumah dengan harga terjangkau lebih banyak ditemukan di data dibandingkan rumah-rumah mewah yang harganya sangat mahal. Namun, ada juga beberapa rumah yang memiliki harga sangat tinggi, jauh di atas harga rata-rata. Rumah-rumah dengan harga sangat tinggi ini disebut sebagai outlier atau data pencilan. 

![download](https://github.com/user-attachments/assets/15f893a1-5ec0-4b5a-b107-0fa3264dfc20)

1. Distribusi Harga Rumah: Grafik menunjukkan bahwa sebagian besar harga rumah berada di kisaran harga rendah sampai menengah. Namun, ada beberapa rumah yang harganya sangat tinggi dan jumlahnya jauh lebih sedikit dibandingkan rumah-rumah lainnya.
2. Distribusi Luas Tanah dan Luas Bangunan: Kedua grafik ini menunjukkan bahwa kebanyakan rumah memiliki luas tanah dan luas bangunan di ukuran yang relatif kecil hingga sedang. Hanya ada sedikit rumah dengan ukuran tanah dan bangunan yang sangat besar.
   
![download](https://github.com/user-attachments/assets/45fa2aa8-6601-4d04-9222-809e4c82441c)

Kebanyakan rumah memiliki sekitar 3 sampai 4 kamar tidur dan 3 sampai 4 kamar mandi. Sangat sedikit rumah yang memiliki kamar tidur atau kamar mandi dalam jumlah sangat banyak (lebih dari 10 kamar).

![download](https://github.com/user-attachments/assets/bd699e23-d4c7-4093-8834-7a8cabdc67c2)

Gambar ini menunjukkan bahwa sebagian besar rumah memiliki garasi, sementara sisanya tidak memiliki garasi. Artinya, keberadaan garasi adalah salah satu fitur umum pada rumah-rumah di dataset ini.

### EDA Multivariate
![download](https://github.com/user-attachments/assets/8b759702-8632-474b-8bd2-724a99b6e869)
![download](https://github.com/user-attachments/assets/fa222d15-46c5-44bf-974b-add5fe5c01b6)
![download](https://github.com/user-attachments/assets/9812368f-9ee9-4c5e-8614-a914e40e5ff8)

Secara umum, data menunjukkan bahwa luas tanah dan luas bangunan memiliki hubungan positif dengan harga rumah—semakin besar luas tanah atau bangunan, harga rumah cenderung lebih tinggi. Namun, terlihat juga beberapa outlier, di mana rumah dengan luas yang sangat besar tidak selalu diikuti dengan harga yang proporsional, mengindikasikan adanya faktor lain yang mempengaruhi harga, seperti lokasi atau fasilitas tambahan.

Selain itu, mayoritas rumah memiliki jumlah kamar tidur dan kamar mandi di kisaran 3-4, menunjukkan preferensi pasar yang umum. Terkait keberadaan garasi, baik rumah yang memiliki garasi maupun yang tidak, memiliki distribusi harga yang cukup mirip, meskipun rumah dengan garasi cenderung memiliki variasi harga yang lebih tinggi.

**Korelasi Matriks**
![download](https://github.com/user-attachments/assets/5f182429-4fa9-4e8d-9131-9d7c5318a13e)

Luas Tanah (LT) dan Luas Bangunan (LB) memiliki korelasi cukup kuat dengan Harga Rumah (HARGA), masing-masing sebesar 0.74 dan 0.65. Artinya, semakin besar luas tanah atau bangunan, harga rumah cenderung lebih tinggi.
Korelasi antara Jumlah Kamar Tidur (JKT) dan Jumlah Kamar Mandi (JKM) sangat tinggi (0.85), menunjukkan bahwa rumah dengan banyak kamar tidur biasanya juga memiliki banyak kamar mandi.
Faktor Garasi (GRS) memiliki korelasi yang sangat rendah dengan harga maupun fitur lainnya, artinya keberadaan garasi tidak terlalu mempengaruhi harga rumah di dataset ini.
Secara keseluruhan, tidak ada indikasi multikolinearitas ekstrem (korelasi mendekati 1) antar fitur kecuali antara JKT dan JKM, yang perlu diperhatikan saat modeling.

---

## **4. Data Preparation**

### **Langkah yang dilakukan:**
1. **Data Cleaning:**
   - Kolom `HARGA` dibersihkan (hapus tanda titik, koma, diubah ke integer).
   - Kolom `GRS` diubah ke binary (1 = Ada Garasi, 0 = Tidak Ada).
   - 
  ![image](https://github.com/user-attachments/assets/10322b27-0cbf-4644-bc94-12e9ca91220b)

2. **Handling Outliers:**
   - Menggunakan metode **IQR (Interquartile Range)** untuk menghapus outlier pada kolom `HARGA`.
   - 
![image](https://github.com/user-attachments/assets/7c83db07-4a86-4b92-bd10-2500056c02c9)

3. **Feature Selection:**
   - Drop kolom `KOTA` karena tidak memberikan informasi variatif.
  
  ![image](https://github.com/user-attachments/assets/5c8eaada-baae-46be-b3b9-26b53e2a95da)

4. **Splitting:**
   - Train-test split sebesar **70:30**.
  
![image](https://github.com/user-attachments/assets/a94b8f53-5350-46c5-b0c3-c294c3e443d3)

5. **Scaling:**
   - Menggunakan **StandardScaler** sebelum modeling karena beberapa model sensitif terhadap skala fitur.
  
  ![image](https://github.com/user-attachments/assets/a8a47cfb-88e2-4f47-aa83-6347328ec65f)


---

## **5. Modeling**

### **Model yang digunakan:**
pada tahap ini, kita akan mengembangkan model machine learning dengan 3 algoritma. Kemudian, kita akan mengevaluasi performa masing-masing algoritma dan menentukan algoritma mana yang memberikan hasil prediksi terbaik. Ketiga algoritma yang akan kita gunakan, antara lain:

1. **XGBoost Regressor**
![image](https://github.com/user-attachments/assets/99643065-3748-4b62-9ce8-ff3f3b558521)

XGBoost adalah algoritma machine learning berbasis ensemble boosting yang digunakan untuk prediksi regresi maupun klasifikasi. XGBoost membangun model secara bertahap dengan menambahkan pohon keputusan (decision tree) baru untuk memperbaiki kesalahan dari model sebelumnya.

Kelebihan dari XGBoost yaitu:

Cepat dan efisien (menggunakan parallel computing)
Mampu menangani data dengan jumlah besar
Dapat mengurangi overfitting dengan parameter regularisasi
Pada tahap ini, saya menggunakan parameter:

n_estimators=100 → jumlah pohon sebanyak 100
max_depth=5 → kedalaman maksimum tiap pohon adalah 5
learning_rate=0.1 → kecepatan pembelajaran model

2. **Random Forest Regressor**
![image](https://github.com/user-attachments/assets/f8491e4a-d358-4160-be4d-70d4ddb1ced7)

Random Forest adalah algoritma ensemble yang membangun banyak decision tree kemudian menggabungkan hasil prediksi dari masing-masing pohon untuk mendapatkan hasil akhir. Pada regresi, hasil akhirnya adalah rata-rata dari prediksi semua pohon.

Kelebihan Random Forest:

Akurat dan stabil (tidak mudah overfitting)
Bisa menangani data dengan banyak fitur
Di sini saya menggunakan parameter default:

n_estimators=100 → membangun 100 pohon keputusan untuk memprediksi harga rumah.

3. **K-Nearest Neighbors (KNN)**
![image](https://github.com/user-attachments/assets/69b87c55-6b0e-4e4c-8d31-d21196aad36a)

KNN merupakan algoritma yang memprediksi nilai sebuah data berdasarkan k tetangga terdekatnya. Jarak antara data dihitung (biasanya dengan Euclidean Distance), kemudian hasil prediksi diambil dari rata-rata nilai tetangga terdekat.

Kelebihan KNN:

Mudah dipahami & diimplementasikan
Tidak memerlukan proses pelatihan model (lazy learning)
Namun, KNN kurang efektif untuk data berukuran besar karena proses pencarian tetangga dilakukan berulang kali.

Pada tahap ini saya menggunakan parameter:

n_neighbors=5 → mempertimbangkan 5 tetangga terdekat untuk memprediksi harga rumah.
---

### **Hyperparameter Tuning**

Hyperparameter tuning adalah proses untuk mencari kombinasi parameter terbaik yang dapat meningkatkan performa model machine learning. Setiap algoritma memiliki parameter tertentu yang bisa diatur sebelum proses training, dan parameter ini disebut **hyperparameter**.

Pada tahap ini, saya menggunakan teknik **GridSearchCV**, yaitu metode pencarian sistematis untuk mencoba semua kombinasi parameter yang telah ditentukan, kemudian memilih kombinasi yang memberikan hasil terbaik berdasarkan evaluasi model.

Berikut parameter yang dicoba untuk masing-masing algoritma:

---

### **XGBoost Regressor:**
- `n_estimators`: jumlah pohon yang digunakan dalam model (100, 200, 300)
- `max_depth`: kedalaman maksimal pohon (3, 5, 7)
- `learning_rate`: kecepatan pembelajaran model (0.1, 0.01, 0.001)

---

### **Random Forest Regressor:**
- `n_estimators`: jumlah pohon (100, 200, 300)
- `max_depth`: batas kedalaman pohon (None, 5, 10)
- `min_samples_split`: jumlah minimal sampel untuk memisah node (2, 5, 10)

---

### **K-Nearest Neighbors (KNN):**
- `n_neighbors`: jumlah tetangga terdekat yang dipertimbangkan (3, 5, 7, 9)
- `weights`: cara pemberian bobot ke tetangga ('uniform' → semua tetangga sama, 'distance' → tetangga yang lebih dekat punya bobot lebih tinggi)
- `metric`: metode pengukuran jarak antar data ('euclidean', 'manhattan')

---


## **6. Evaluation**

### **Metrik Evaluasi:**

- **Mean Absolute Error (MAE)**: Mengukur rata-rata selisih absolut antara hasil prediksi harga rumah dengan harga rumah yang sebenarnya. Semakin kecil nilai MAE, berarti prediksi model semakin akurat.
  
- **R² Score (Koefisien Determinasi)**: Menunjukkan seberapa baik model dapat menjelaskan variasi harga rumah. Nilainya antara 0 sampai 1. Semakin mendekati 1, semakin baik performa model.

---

### **Hasil Evaluasi Akhir:**
![image](https://github.com/user-attachments/assets/15fa3591-607d-4023-bd9c-3766d3b5310e)

| Model               | Best Params                                                                 | MAE           | R² Score |
|--------------------|-----------------------------------------------------------------------------|--------------|---------|
| **XGBoost**         | {'learning_rate': 0.01, 'max_depth': 5, 'n_estimators': 100}                 | 3,071,323,000 | 0.74    |
| **Random Forest**   | {'max_depth': None, 'min_samples_split': 5, 'n_estimators': 300}             | **2,913,505,000** | **0.76** |
| **KNN**             | {'metric': 'euclidean', 'n_neighbors': 9, 'weights': 'distance'}             | 3,316,559,000 | 0.68    |

---

### **Interpretasi Hasil:**

- Model **Random Forest Regressor** memiliki nilai MAE paling rendah sekitar **2.91 miliar**, yang berarti rata-rata prediksi harga rumah meleset sekitar angka tersebut dari harga aslinya. Nilai **R² Score sebesar 0.76** menunjukkan model ini dapat menjelaskan sekitar 76% variasi harga rumah berdasarkan fitur yang tersedia. Oleh karena itu, Random Forest menjadi model terbaik pada proyek ini.

- Model **XGBoost** menunjukkan performa cukup baik dengan MAE sekitar **3.07 miliar** dan R² Score **0.74**. Prediksi model ini juga cukup dekat dengan harga asli, namun masih sedikit di bawah Random Forest.

- Model **K-Nearest Neighbors (KNN)** memiliki performa paling rendah di antara ketiganya. Nilai MAE-nya lebih tinggi, yaitu sekitar **3.31 miliar**, dan R² Score sebesar **0.68**, yang artinya model ini kurang mampu menjelaskan variasi harga rumah dengan baik.

---

### **Contoh Perbandingan Prediksi:**
![image](https://github.com/user-attachments/assets/77e74caf-3002-405d-9d8b-a3e3dabb53cb)

| Actual Price     | XGBoost Prediction | Random Forest Prediction | KNN Prediction |
|------------------|-------------------|--------------------------|---------------|
| Rp 25.00 Miliar  | Rp 22.66 Miliar   | Rp 22.90 Miliar          | Rp 22.06 Miliar|
| Rp 8.00 Miliar   | Rp 10.05 Miliar   | Rp 9.02 Miliar           | Rp 8.00 Miliar |
| Rp 20.00 Miliar  | Rp 18.79 Miliar   | Rp 17.26 Miliar          | Rp 16.23 Miliar|
| Rp 39.00 Miliar  | Rp 31.61 Miliar   | Rp 33.38 Miliar          | Rp 23.45 Miliar|
| Rp 16.00 Miliar  | Rp 17.38 Miliar   | Rp 16.67 Miliar          | Rp 15.41 Miliar|
| Rp 11.98 Miliar  | Rp 12.91 Miliar   | Rp 12.26 Miliar          | Rp 12.34 Miliar|
| Rp 15.00 Miliar  | Rp 12.50 Miliar   | Rp 13.69 Miliar          | Rp 12.26 Miliar|
| Rp 20.00 Miliar  | Rp 16.98 Miliar   | Rp 16.40 Miliar          | Rp 16.16 Miliar|
| Rp 19.50 Miliar  | Rp 16.07 Miliar   | Rp 17.69 Miliar          | Rp 12.35 Miliar|
| Rp 15.00 Miliar  | Rp 12.56 Miliar   | Rp 14.90 Miliar          | Rp 15.00 Miliar|

---

### **Kesimpulan:**

Berdasarkan evaluasi di atas, **Random Forest Regressor** dipilih sebagai model terbaik untuk prediksi harga rumah, karena:

- Memiliki MAE paling rendah (prediksi lebih dekat ke harga asli).
- Memiliki R² Score tertinggi (mampu menjelaskan sebagian besar variasi harga rumah).
- Lebih stabil dalam menghadapi variasi data dan outlier dibandingkan model lain.

---

## **Referensi:**

1. Bisa.ai Portofolio, Prediksi Harga Rumah: [https://bisa.ai/portofolio/detail/MjQzOA](https://bisa.ai/portofolio/detail/MjQzOA)
2. Antaranews, Harga Rumah Jakarta Selatan 2025: [https://www.antaranews.com/berita/4632209/ingin-beli-rumah-di-jakarta-selatan-segini-harganya-di-tahun-2025](https://www.antaranews.com/berita/4632209/ingin-beli-rumah-di-jakarta-selatan-segini-harganya-di-tahun-2025)
3. Dataset: [https://www.kaggle.com/datasets/wisnuanggara/daftar-harga-rumah](https://www.kaggle.com/datasets/wisnuanggara/daftar-harga-rumah)
