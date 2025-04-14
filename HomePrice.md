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
  
  ![image](https://github.com/user-attachments/assets/10322b27-0cbf-4644-bc94-12e9ca91220b)

2. **Handling Outliers:**
   - Menggunakan metode **IQR (Interquartile Range)** untuk menghapus outlier pada kolom `HARGA`.

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

4. Linear Regression
   
![image](https://github.com/user-attachments/assets/0c3fea65-ea52-4b5d-aea8-1776988b1c95)


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

![image](https://github.com/user-attachments/assets/df4ebecb-f940-4669-93ad-bca8c8d8d58f)


| Model               | Best Params                                                                 | MAE           | R² Score |
|--------------------|-----------------------------------------------------------------------------|--------------|---------|
| **XGBoost**         | {'learning_rate': 0.01, 'max_depth': 3, 'n_estimators': 100}                 | 2.161057e+09	 | 0.74    |
| **Random Forest**   | {'max_depth': None, 'min_samples_split': 2, 'n_estimators': 300}             | 2.250124e+09 | 0.67 |
| **KNN**             | {'metric': 'euclidean', 'n_neighbors': 9, 'weights': 'distance'}             | 2.365660e+09 | 0.66   |
| **Linear Regression**             |{'fit_intercept': True, 'positive': False}             | 2.256256e+09	 | 0.74    |
---

### **Interpretasi Hasil:**

Berdasarkan hasil evaluasi di atas, model terbaik adalah XGBoost karena:

Memiliki MAE terkecil (2,16 miliar / 21,6%), menunjukkan prediksi paling akurat.
Mendapatkan R² Score tertinggi (0.74), yang berarti model dapat menjelaskan 74% variasi dalam data.
Dengan hasil tersebut, XGBoost menjadi model yang paling direkomendasikan untuk digunakan dalam tahap prediksi akhir.

--

### **Contoh Perbandingan Prediksi:**

![image](https://github.com/user-attachments/assets/3ce91e33-79be-470f-b114-05a1e4707a60)


| No. | LT        | LB        | JKT  | JKM      | GRS | Harga Aktual       | XGBoost Prediction  | Random Forest Prediction | KNN Prediction       | Linear Regression Prediction |
|-----|-----------|-----------|------|----------|-----|--------------------|---------------------|---------------------------|----------------------|------------------------------|
| 1   | 0.519573  | 0.43750   | 0.5  | 0.333333 | 1   | Rp 14.00 Miliar    | Rp 13.08 Miliar     | Rp 10.18 Miliar           | Rp 12.83 Miliar      | Rp 12.90 Miliar              |
| 2   | 0.806643  | 0.50125   | 0.5  | 0.666667 | 1   | Rp 15.00 Miliar    | Rp 20.39 Miliar     | Rp 22.97 Miliar           | Rp 22.04 Miliar      | Rp 17.77 Miliar              |
| 3   | 0.173191  | 0.15000   | 0.0  | 0.333333 | 0   | Rp 5.70 Miliar     | Rp 3.79 Miliar      | Rp 3.85 Miliar            | Rp 3.39 Miliar       | Rp 4.56 Miliar               |
| 4   | 0.252669  | 0.71625   | 0.5  | 0.666667 | 0   | Rp 13.00 Miliar    | Rp 12.55 Miliar     | Rp 12.56 Miliar           | Rp 12.97 Miliar      | Rp 12.35 Miliar              |
| 5   | 0.539739  | 0.58750   | 0.5  | 0.333333 | 1   | Rp 17.50 Miliar    | Rp 17.09 Miliar     | Rp 17.09 Miliar           | Rp 13.85 Miliar      | Rp 14.97 Miliar              |
| 6   | 0.098458  | 0.09250   | 0.0  | 0.333333 | 1   | Rp 2.20 Miliar     | Rp 2.49 Miliar      | Rp 2.77 Miliar            | Rp 3.07 Miliar       | Rp 3.84 Miliar               |
| 7   | 0.450771  | 0.23250   | 0.0  | 0.333333 | 1   | Rp 10.00 Miliar    | Rp 11.17 Miliar     | Rp 11.33 Miliar           | Rp 13.49 Miliar      | Rp 10.04 Miliar              |
| 8   | 0.211151  | 0.31250   | 1.0  | 0.666667 | 1   | Rp 9.00 Miliar     | Rp 6.17 Miliar      | Rp 6.57 Miliar            | Rp 9.18 Miliar       | Rp 7.35 Miliar               |
| 9   | 0.246738  | 0.31250   | 1.0  | 0.666667 | 1   | Rp 12.00 Miliar    | Rp 7.06 Miliar      | Rp 6.47 Miliar            | Rp 8.69 Miliar       | Rp 7.81 Miliar               |
| 10  | 0.447212  | 0.37500   | 0.5  | 0.333333 | 1   | Rp 6.50 Miliar     | Rp 13.90 Miliar     | Rp 19.88 Miliar           | Rp 22.40 Miliar      | Rp 11.22 Miliar              |


---

### Hasil Prediksi dan Evaluasi Model

#### Penjelasan Fitur (Setelah Encoding)
Sebelum masuk ke bagian kesimpulan, berikut adalah penjelasan mengenai fitur-fitur yang digunakan dalam model prediksi harga rumah yang telah melalui proses encoding:

- **LT (Luas Tanah)** dan **LB (Luas Bangunan)**: Merupakan nilai numerik hasil normalisasi.
- **JKT (Wilayah Jakarta)**: Fitur kategorikal yang telah diubah menjadi numerik menggunakan label encoding.
  - 0.0 = Jakarta Barat
  - 0.5 = Jakarta Selatan
  - 1.0 = Jakarta Timur
- **JKM (Jenis Kategori Rumah atau Lokasi Khusus)**: Kategori lain berdasarkan lokasi atau jenis bangunan, juga hasil encoding.
  - 0.333 = Kategori A
  - 0.666 = Kategori B
  - 1.0 = Kategori C
- **GRS (Garasi)**:
  - 0 = Tidak memiliki garasi
  - 1 = Memiliki garasi

### Kesimpulan dan Evaluasi

Dari pertanyaan bisnis mengenai bagaimana memprediksi harga rumah di Jakarta, khususnya daerah Tebet, dapat disimpulkan bahwa sistem prediksi yang dikembangkan dengan pendekatan machine learning mampu memberikan estimasi harga yang cukup akurat dan bermanfaat. Sistem ini memanfaatkan data sederhana seperti luas tanah, bangunan, lokasi, dan keberadaan garasi untuk menghasilkan prediksi harga rumah, sehingga dapat digunakan oleh berbagai kalangan.

Bagi masyarakat umum, solusi ini dapat membantu memberikan gambaran harga rumah tanpa harus berkonsultasi langsung dengan agen properti. Cukup memasukkan beberapa informasi dasar, sistem sudah bisa memberikan estimasi harga. Sedangkan bagi pelaku properti seperti agen atau pengembang, model ini bisa menjadi alat bantu dalam menetapkan harga jual yang kompetitif berdasarkan tren dan data historis.

Bagi pengembang sistem, hasil evaluasi terhadap berbagai algoritma juga memberikan wawasan terkait kelebihan dan kekurangan masing-masing model, sehingga dapat dijadikan dasar dalam memilih metode yang paling sesuai dengan kebutuhan, baik dari sisi akurasi maupun kestabilan hasil prediksi.

### Observasi dan Analisis:

**KNN:**
Secara keseluruhan, KNN cenderung memberikan prediksi yang paling mendekati harga rumah yang sebenarnya. Contohnya pada baris pertama, di mana KNN memprediksi harga Rp 12.83 Miliar, yang sangat dekat dengan harga aktual Rp 14.00 Miliar.

**XGBoost dan Random Forest:**
Kedua model ini lebih cenderung memberikan prediksi yang lebih tinggi, terutama pada rumah dengan luas tanah dan bangunan yang lebih besar. Misalnya pada baris kedua, XGBoost memprediksi harga sebesar Rp 20.39 Miliar, yang jauh lebih tinggi dibandingkan harga aktual Rp 15.00 Miliar.

**Linear Regression:**
Hasil prediksi Linear Regression cenderung lebih konservatif dibandingkan model lainnya. Misalnya pada baris pertama, harga yang diprediksi oleh Linear Regression adalah Rp 12.90 Miliar, yang sedikit lebih rendah dari harga aktual. Namun, Linear Regression memberikan prediksi yang lebih stabil dengan deviasi yang lebih kecil pada rumah-rumah dengan karakteristik ekstrem.

### Kesimpulan:
Secara keseluruhan, KNN tampaknya memberikan prediksi yang paling akurat dibandingkan dengan model lainnya, dengan prediksi yang paling mendekati harga aktual di sebagian besar sampel.

XGBoost dan Random Forest memberikan prediksi yang lebih tinggi pada rumah dengan luas tanah dan bangunan yang besar, yang mungkin menunjukkan kecenderungan untuk overestimate pada beberapa kasus.

Linear Regression memberikan hasil yang lebih konservatif, meskipun tidak selalu mendekati harga aktual, hasil prediksinya cukup stabil.

Dokumentasi ini memberikan wawasan tentang bagaimana masing-masing model bekerja dalam memprediksi harga rumah berdasarkan data input tertentu dan seberapa baik mereka mencocokkan harga rumah yang sebenarnya.

---

## **Referensi:**

1. Bisa.ai Portofolio, Prediksi Harga Rumah: [https://bisa.ai/portofolio/detail/MjQzOA](https://bisa.ai/portofolio/detail/MjQzOA)
2. Antaranews, Harga Rumah Jakarta Selatan 2025: [https://www.antaranews.com/berita/4632209/ingin-beli-rumah-di-jakarta-selatan-segini-harganya-di-tahun-2025](https://www.antaranews.com/berita/4632209/ingin-beli-rumah-di-jakarta-selatan-segini-harganya-di-tahun-2025)
3. https://www.researchgate.net/publication/383157878_Analisis_Prediksi_Harga_Rumah_Pada_Machine_Learning_Metode_Regresi_Linear
4. Dataset: [https://www.kaggle.com/datasets/wisnuanggara/daftar-harga-rumah](https://www.kaggle.com/datasets/wisnuanggara/daftar-harga-rumah)
