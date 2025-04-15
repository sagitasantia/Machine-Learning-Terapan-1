# **Laporan Proyek Machine Learning Terapan**
# **Anggraini Sagita Santia Putri**
---

# **Detail Laporan: Prediksi Harga Rumah Jakarta Selatan🏠🏘️🏡**

---

## **1. Domain Proyek**

Permasalahan harga properti di Jakarta, khususnya di Jakarta Selatan, menjadi salah satu tantangan yang dihadapi masyarakat saat ini. Berdasarkan data dari Antara News[Antara News](https://www.antaranews.com/berita/4632209/ingin-beli-rumah-di-jakarta-selatan-segini-harganya-di-tahun-2025), harga rumah di Jakarta Selatan pada tahun 2025 rata-rata mencapai Rp 1,4 miliar hingga Rp 40 miliar, tergantung pada lokasi, ukuran, dan fasilitas.

Selain itu, riset dari Bisa.ai[Bisa.ai](https://bisa.ai/portofolio/detail/MjQzOA) menunjukkan bahwa harga rumah sangat dipengaruhi oleh berbagai faktor seperti luas tanah, luas bangunan, jumlah kamar, dan ketersediaan garasi.

Dalam penelitian sebelumnya yang dilakukan oleh Nuzuliarini Nuris menggunakan metode Regresi Linear untuk memprediksi harga rumah, ditemukan bahwa harga rumah sangat dipengaruhi oleh luas bangunan, dengan nilai korelasi antara luas bangunan dan harga rumah mencapai 0,80, menunjukkan hubungan yang sangat kuat. Penelitian ini juga menunjukkan bahwa harga rumah tidak dipengaruhi oleh jenis sertifikat, dengan korelasi sebesar 0,00. Metode yang digunakan dalam penelitian ini menunjukkan hasil yang baik, dengan tingkat akurasi mencapai 86,41% dan evaluasi metrik R² = 0.78 dan MAE = 313.000,83​ Nuris, N (2024).

Oleh karena itu, proyek ini mengembangkan model prediksi harga rumah dengan menggunakan algoritma machine learning yang lebih kompleks dan pendekatan yang lebih beragam dibandingkan dengan penelitian sebelumnya. Dengan menambahkan faktor-faktor seperti jumlah kamar, ketersediaan garasi, dan lokasi, model ini diharapkan dapat memberikan prediksi harga rumah yang lebih akurat dan lebih sesuai dengan kebutuhan pembeli serta penjual rumah di daerah Tebet, Jakarta Selatan.Oleh karena itu, prediksi harga rumah secara akurat menggunakan machine learning dapat membantu masyarakat (baik pembeli maupun penjual) dalam menentukan harga properti yang sesuai.

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
2. Membangun model Machine Learning untuk memprediksi harga rumah di daerah Tebet, Jakarta Selatan menggunakan algoritma, yaitu Random Forest, XGBOOST, KNN, Linear Regression
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
  
  ![image](https://github.com/user-attachments/assets/10322b27-0cbf-4644-bc94-12e9ca91220b)

2. **Handling Outliers:**
   - Menggunakan metode **IQR (Interquartile Range)** untuk menghapus outlier pada kolom 'LT', 'LB', 'JKT', 'JKM', 'HARGA'.

3. **Feature Selection:**
   - Drop kolom `KOTA` karena tidak memberikan informasi variatif.
  
  ![image](https://github.com/user-attachments/assets/5c8eaada-baae-46be-b3b9-26b53e2a95da)

4. **Splitting:**
   - Train-test split sebesar **90:10**.
  
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

4. Linear Regression

Linear Regression adalah model yang memprediksi nilai kontinu dengan mengasumsikan hubungan linier antara fitur dan target. Model ini mencari garis yang paling pas untuk memprediksi harga rumah berdasarkan fitur yang diberikan.

Kelebihan:

- Mudah dipahami dan cepat diimplementasikan.

- Efisien untuk data dengan hubungan linier.

Kekurangan:

- Tidak efektif untuk data dengan hubungan non-linier.

- Sensitif terhadap outlier.

Parameter yang digunakan:

- fit_intercept=True: Menghitung intercept (bias).

- positive=True: Koefisien regresi harus bernilai positif.

---

### **Hyperparameter Tuning**

**Hyperparameter tuning** adalah proses untuk mencari kombinasi parameter terbaik yang dapat meningkatkan performa model machine learning. Setiap algoritma memiliki parameter tertentu yang bisa diatur sebelum proses training, dan parameter ini disebut **hyperparameter**.

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

### **Linear Regression:**
- `fit_intercept`: Menentukan apakah model akan menghitung intercept (bias) atau tidak. Nilai yang dicoba adalah **[True, False]**.
- `positive`: Menentukan apakah koefisien regresi harus bernilai positif. Nilai yang dicoba adalah **[True, False]**.

---


## **6. Evaluation**

### **Metrik Evaluasi:**

- **Mean Absolute Error (MAE)**: Mengukur rata-rata selisih absolut antara hasil prediksi harga rumah dengan harga rumah yang sebenarnya. Semakin kecil nilai MAE, berarti prediksi model semakin akurat.
  
- **R² Score (Koefisien Determinasi)**: Menunjukkan seberapa baik model dapat menjelaskan variasi harga rumah. Nilainya antara 0 sampai 1. Semakin mendekati 1, semakin baik performa model.

---

### **Hasil Evaluasi Akhir:**

![image](https://github.com/user-attachments/assets/9b621ec5-2d14-44f9-b62c-179f87e3245d)

| **Model**            | **Best Params**                                                                 | **MAE**         | **R² Score** |
|----------------------|----------------------------------------------------------------------------------|------------------|--------------|
| **XGBoost**           | {'learning_rate': 0.1, 'max_depth': 3, 'n_estimators': 100}                      | 2.822069e+09     | 0.74         |
| **Random Forest**     | {'max_depth': None, 'min_samples_split': 5, 'n_estimators': 200}                 | 2.551921e+09     | 0.80         |
| **KNN**               | {'metric': 'euclidean', 'n_neighbors': 9, 'weights': 'distance'}                 | 3.051515e+09     | 0.71         |
| **Linear Regression** | {'fit_intercept': True, 'positive': False}                                      | 2.946421e+09     | 0.75         |
---

### Interpretasi Hasil:
Berdasarkan hasil evaluasi dari keempat model Machine Learning, dapat disimpulkan bahwa model terbaik adalah Random Forest. Hal ini didasarkan pada metrik evaluasi berikut:

R² Score tertinggi sebesar 0.80, yang berarti model dapat menjelaskan 80% variasi dalam data target (harga rumah). Ini menunjukkan bahwa Random Forest memiliki performa prediksi yang sangat baik dibanding model lainnya.

MAE (Mean Absolute Error) sebesar 2.55 miliar, yang merupakan nilai MAE terkecil kedua setelah XGBoost, menunjukkan kesalahan prediksi rata-rata yang relatif rendah dan stabil.

Sementara itu, XGBoost memiliki MAE sedikit lebih tinggi yaitu 2.82 miliar dan R² Score lebih rendah (0.74). Artinya, meskipun cukup akurat, XGBoost tidak sebaik Random Forest dalam menjelaskan variasi data secara keseluruhan.

Model KNN menunjukkan performa yang paling rendah, baik dari segi MAE (3.05 miliar) maupun R² Score (0.71). Sedangkan Linear Regression memiliki MAE sebesar 2.95 miliar dengan R² Score 0.75, namun masih kalah dibanding Random Forest.

--

### **Contoh Perbandingan Prediksi:**

![image](https://github.com/user-attachments/assets/5f65cbb2-3a92-4ddb-9576-3a41ef0f2899)

| **LT**     | **LB**     | **JKT**    | **JKM**    | **GRS** | **Actual Price** | **XGBoost Prediction** | **Random Forest Prediction** | **KNN Prediction** | **Linear Regression Prediction** |
|-----------|------------|------------|------------|--------|------------------|------------------------|------------------------------|--------------------|-------------------------------|
| 0.112156  | 0.216159   | 0.115385   | 0.076923   | 1      | Rp 7.90 Miliar   | Rp 15.72 Miliar        | Rp 10.78 Miliar              | Rp 8.14 Miliar     | Rp 12.34 Miliar               |
| 0.047683  | 0.053515   | 0.076923   | 0.076923   | 1      | Rp 5.20 Miliar   | Rp 3.24 Miliar         | Rp 2.59 Miliar               | Rp 3.01 Miliar     | Rp 5.53 Miliar                |
| 0.160510  | 0.504722   | 0.153846   | 0.153846   | 1      | Rp 15.00 Miliar  | Rp 26.07 Miliar        | Rp 18.55 Miliar              | Rp 23.68 Miliar    | Rp 23.24 Miliar               |
| 0.147079  | 0.189927   | 0.115385   | 0.076923   | 1      | Rp 14.00 Miliar  | Rp 14.00 Miliar        | Rp 16.00 Miliar              | Rp 13.63 Miliar    | Rp 12.73 Miliar               |
| 0.018133  | 0.048269   | 0.076923   | 0.076923   | 0      | Rp 1.45 Miliar   | Rp 1.79 Miliar         | Rp 1.80 Miliar               | Rp 2.33 Miliar     | Rp 3.79 Miliar                |
| 0.060779  | 0.032529   | 0.115385   | 0.076923   | 1      | Rp 4.50 Miliar   | Rp 3.44 Miliar         | Rp 3.14 Miliar               | Rp 4.55 Miliar     | Rp 5.11 Miliar                |
| 0.151108  | 0.321091   | 0.192308   | 0.153846   | 0      | Rp 20.00 Miliar  | Rp 16.64 Miliar        | Rp 15.30 Miliar              | Rp 18.16 Miliar    | Rp 16.61 Miliar               |
| 0.271323  | 0.189927   | 0.269231   | 0.115385   | 0      | Rp 28.00 Miliar  | Rp 18.96 Miliar        | Rp 21.05 Miliar              | Rp 20.23 Miliar    | Rp 15.84 Miliar               |
| 0.345198  | 0.504722   | 0.115385   | 0.115385   | 0      | Rp 25.00 Miliar  | Rp 32.49 Miliar        | Rp 28.34 Miliar              | Rp 31.12 Miliar    | Rp 28.70 Miliar               |
| 0.039624  | 0.111228   | 0.076923   | 0.038462   | 0      | Rp 5.10 Miliar   | Rp 4.68 Miliar         | Rp 5.27 Miliar               | Rp 3.64 Miliar     | Rp 5.97 Miliar                |

---

### **Hasil Prediksi dan Evaluasi Model**

#### Penjelasan Fitur

Beberapa ciri-ciri rumah yang digunakan dalam proses prediksi antara lain:

- **Luas Tanah (LT)** dan **Luas Bangunan (LB)** ditampilkan dalam skala antara 0 sampai 1.
- **JKT** menunjukkan wilayah rumah: 0.0 untuk Jakarta Barat, 0.5 untuk Jakarta Selatan, dan 1.0 untuk Jakarta Timur.
- **JKM** adalah kategori tambahan berdasarkan lokasi atau jenis rumah: 0.333 untuk Kategori A, 0.666 untuk Kategori B, dan 1.0 untuk Kategori C.
- **GRS** menunjukkan keberadaan garasi: 0 artinya tidak ada garasi, dan 1 artinya ada.

#### Kesimpulan

Dari pertanyaan awal tentang bagaimana cara memprediksi harga rumah di Jakarta, khususnya di daerah Tebet, kita bisa simpulkan bahwa model machine learning ini cukup membantu dan bisa digunakan oleh masyarakat luas.

Dari hasil pengujian, model **Random Forest** memberikan hasil paling akurat dibandingkan model lainnya. Model ini memiliki tingkat kesalahan paling kecil (MAE sekitar Rp 2,55 miliar) dan mampu menjelaskan sekitar 80% variasi harga rumah.

Model **XGBoost** juga menunjukkan performa yang cukup baik, dengan MAE sekitar Rp 2,82 miliar dan akurasi 74%, tapi masih kalah dari Random Forest.

Sementara itu, model **KNN** dan **Linear Regression** memiliki hasil prediksi yang kurang akurat. KNN menunjukkan kesalahan paling besar, sedangkan Linear Regression cenderung menghasilkan prediksi yang terlalu jauh dari harga aslinya.

Secara keseluruhan, model prediksi ini sudah cukup baik untuk memberikan perkiraan harga rumah di Jakarta, terutama di wilayah Tebet, hanya dengan melihat beberapa informasi dasar seperti luas bangunan, luas tanah, lokasi, dan keberadaan garasi.

---

## **Referensi:**

1. Bisa.ai Portofolio, Prediksi Harga Rumah: [https://bisa.ai/portofolio/detail/MjQzOA](https://bisa.ai/portofolio/detail/MjQzOA)
2. Antaranews, Harga Rumah Jakarta Selatan 2025: [https://www.antaranews.com/berita/4632209/ingin-beli-rumah-di-jakarta-selatan-segini-harganya-di-tahun-2025](https://www.antaranews.com/berita/4632209/ingin-beli-rumah-di-jakarta-selatan-segini-harganya-di-tahun-2025)
3. https://www.researchgate.net/publication/383157878_Analisis_Prediksi_Harga_Rumah_Pada_Machine_Learning_Metode_Regresi_Linear
4. Dataset: [https://www.kaggle.com/datasets/wisnuanggara/daftar-harga-rumah](https://www.kaggle.com/datasets/wisnuanggara/daftar-harga-rumah)
