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
  - **HARGA**: Harga rumah (target)
  - **LT**: Luas Tanah (m²)
  - **LB**: Luas Bangunan (m²)
  - **JKT**: Jumlah Kamar Tidur
  - **JKM**: Jumlah Kamar Mandi
  - **GRS**: Ketersediaan Garasi (Ada/Tidak Ada → diubah ke binary)
  - **KOTA**: Nama Kota (semua entri adalah Jakarta Selatan, di-drop)


## **Data Exploration:**
### EDA Univariate
![download](https://github.com/user-attachments/assets/908bc468-a62f-4e66-a15a-ecdcce418c13)
Grafik ini menunjukkan penyebaran harga rumah yang ada di data. Dari grafik tersebut, kita bisa lihat bahwa sebagian besar harga rumah berada di kisaran yang cukup rendah hingga menengah. Semakin tinggi harga rumah, jumlahnya semakin sedikit. Ini artinya, rumah dengan harga terjangkau lebih banyak ditemukan di data dibandingkan rumah-rumah mewah yang harganya sangat mahal. Namun, ada juga beberapa rumah yang memiliki harga sangat tinggi, jauh di atas harga rata-rata. Rumah-rumah dengan harga sangat tinggi ini disebut sebagai outlier atau data pencilan. 

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
