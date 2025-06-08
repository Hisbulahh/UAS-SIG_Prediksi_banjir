# Prediksi Kerawanan Banjir di Provinsi Sumatera Selatan

Proyek ini bertujuan untuk membangun model machine learning yang dapat memprediksi tingkat kerawanan banjir di berbagai kabupaten/kota di Provinsi Sumatera Selatan. Prediksi didasarkan pada data penggunaan lahan sebagai fitur utama.

## Abstrak

Banjir merupakan salah satu bencana alam yang sering terjadi dan menimbulkan kerugian signifikan. Dengan menganalisis data spasial dan non-spasial, kita dapat membangun model prediktif untuk mengidentifikasi daerah-daerah yang berisiko tinggi. Proyek ini menggunakan data luas penggunaan lahan (misalnya, hutan, pemukiman, sawah) sebagai variabel independen untuk melatih model klasifikasi. Model yang telah dilatih kemudian digunakan untuk memprediksi status kerawanan banjir (Rawan atau Tidak Rawan) untuk setiap kabupaten/kota, yang hasilnya divisualisasikan dalam bentuk peta koroplet (choropleth map).

## Fitur Utama Proyek

* **Feature Engineering**: Membuat fitur baru berupa persentase luas lahan untuk meningkatkan akurasi model.
* **Perbandingan Model**: Menguji dan membandingkan beberapa model klasifikasi (Random Forest, Gradient Boosting, SVM, XGBoost) untuk menemukan yang paling optimal.
* **Hyperparameter Tuning**: Menggunakan `GridSearchCV` untuk mencari parameter terbaik dari model yang paling unggul.
* **Visualisasi Geospasial**: Menampilkan hasil prediksi akhir dalam bentuk peta geografis menggunakan GeoPandas.

## Visualisasi Hasil

Berikut adalah contoh output peta prediksi yang dihasilkan oleh notebook ini:

![Peta Prediksi Kerawanan Banjir](https://i.imgur.com/K5a0D6A.png)
*(Catatan: Gambar di atas adalah contoh. Hasil akhir akan bergantung pada data riwayat banjir yang digunakan)*

## Data yang Dibutuhkan

Untuk menjalankan notebook ini, Anda memerlukan tiga file data utama:

1.  `penggunaan_lahan_sumsel.csv`
    * **Isi**: Data luas penggunaan lahan untuk setiap kabupaten/kota di Sumatera Selatan.
    * **Kolom Contoh**: `Kabupaten/Kota`, `Lahan Sawah (ha)`, `Lahan Hutan (ha)`, `Total Luas Penggunaan Lahan (ha)`, dll.
    * **Peran**: Sebagai data fitur (X).

2.  `riwayat_banjir_sumsel.csv`
    * **Isi**: Data historis kejadian banjir di setiap kabupaten/kota.
    * **Kolom Contoh**: `Lokasi`, `Pernah Banjir` (dengan nilai 1 untuk ya, 0 untuk tidak).
    * **Peran**: Sebagai data target/label (y).

3.  `sumsel_admin.zip` (atau file shapefile sejenis)
    * **Isi**: Data geospasial (.shp dan file pendukungnya) yang berisi poligon batas administrasi kabupaten/kota di Sumatera Selatan.
    * **Peran**: Untuk visualisasi peta.

## Teknologi dan Library

Proyek ini dibangun menggunakan Python 3 dan library utama berikut:

* `pandas`: Untuk manipulasi dan analisis data.
* `geopandas`: Untuk memproses data geospasial (shapefile).
* `scikit-learn`: Untuk membangun, melatih, dan mengevaluasi model machine learning.
* `xgboost`: Untuk menggunakan model XGBoost Classifier.
* `matplotlib` & `seaborn`: Untuk visualisasi data, termasuk plot dan peta.
* `numpy`: Untuk operasi numerik.

## Cara Menjalankan

1.  **Lingkungan**: Disarankan untuk menjalankan notebook ini di Google Colaboratory untuk kemudahan manajemen library.
2.  **Buka Notebook**: Buka file `Prediksi-Banjir-Sumsel.ipynb` di Google Colab.
3.  **Jalankan Sel**: Jalankan setiap sel kode secara berurutan dari atas ke bawah.
4.  **Upload File**: Notebook akan meminta Anda untuk mengunggah file-file data (`.csv` dan `.zip`) pada sel yang telah ditentukan. Pastikan nama file yang di-upload sesuai dengan yang diminta oleh kode.
5.  **Hasil**: Output akhir berupa laporan evaluasi model dan sebuah peta prediksi kerawanan banjir akan ditampilkan di akhir notebook.

## Alur Kerja Proyek

1.  **Persiapan**: Instalasi dan import library yang diperlukan.
2.  **Memuat Data**: Memuat dataset penggunaan lahan dan riwayat banjir, lalu menggabungkannya menjadi satu DataFrame utama.
3.  **Feature Engineering**: Membuat fitur-fitur baru (persentase lahan) dari data mentah.
4.  **Eksplorasi Data (EDA)**: Menganalisis korelasi antar fitur untuk mendapatkan wawasan awal.
5.  **Pelatihan Model**: Membandingkan beberapa model machine learning dan memilih yang terbaik berdasarkan metrik akurasi.
6.  **Optimasi Model**: Melakukan tuning hyperparameter pada model terbaik untuk meningkatkan performanya.
7.  **Evaluasi**: Mengevaluasi model final menggunakan metrik seperti *classification report* dan *confusion matrix*.
8.  **Visualisasi**: Menggabungkan hasil prediksi dengan data shapefile dan membuat peta koroplet.
