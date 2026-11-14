# UTS-Machine-Learning-kelompok-14
UTS Machine Learning kelompok 14

# UTS Machine Learning — Kelompok 14

Repository ini berisi dokumentasi dan implementasi proyek Ujian Tengah Semester (UTS) mata kuliah Machine Learning Kelompok 14.

## Deskripsi Proyek

Proyek ini menerapkan metode Machine Learning untuk melakukan analisis terhadap data pelanggan. Pengerjaan dibagi menjadi beberapa tugas, yaitu Regression, Classification, dan Clustering.

Setiap tugas menggunakan pendekatan Machine Learning yang sesuai dengan tujuan analisis masing-masing.

## Anggota dan Pembagian Tugas

| Anggota | Tanggung Jawab |
|---|---|
| Dias | Regression |
| Mohamad Nur Taufiq | Classification dan Koordinator Kelompok |
| Irfan Rizky Maulana | Customer Clustering |

## Task 3 — Customer Clustering

Bagian clustering bertujuan untuk mengelompokkan pelanggan berdasarkan karakteristik dan pola aktivitas mereka, sehingga diperoleh segmentasi pelanggan yang dapat digunakan sebagai dasar penyusunan strategi pemasaran.

Dataset yang digunakan berisi sekitar 120.000 data pelanggan dengan informasi aktivitas dan transaksi dalam periode 90 hari.

### Metode yang Digunakan

Beberapa metode clustering yang dibandingkan dalam analisis ini adalah:

- **K-Means** — mengelompokkan data berdasarkan kedekatan terhadap centroid.
- **Gaussian Mixture Model (GMM)** — melakukan clustering menggunakan distribusi probabilitas.
- **HDBSCAN** — mengidentifikasi kelompok berdasarkan kepadatan data serta mendeteksi noise.

### Tahapan Analisis

1. **Data Preprocessing** — menangani nilai kosong, transformasi data, encoding fitur kategorikal, dan scaling.
2. **Feature Selection** — menentukan fitur yang digunakan dalam proses clustering.
3. **Model Comparison** — membandingkan beberapa metode clustering.
4. **Cluster Evaluation** — mengevaluasi jumlah cluster menggunakan metrik evaluasi yang sesuai.
5. **Stability Testing** — menguji kestabilan hasil clustering melalui 10 kali subsampling.
6. **Customer Profiling** — menganalisis karakteristik setiap cluster dan menyusun rekomendasi strategi pemasaran.
7. **Anomaly Detection** — memberikan label `-1` kepada data yang ditandai sebagai anomali berdasarkan aturan yang digunakan.

## Struktur Repository

```text
UTS-Machine-Learning-kelompok-14/
│
├── README.md
└── clustering.ipynb
```

Notebook `clustering.ipynb` berisi implementasi dan tahapan analisis customer clustering.

## Cara Menjalankan Notebook

Notebook dapat dijalankan menggunakan Google Colab.

1. Buka repository GitHub ini.
2. Pilih file `clustering.ipynb`.
3. Buka notebook melalui Google Colab atau unduh terlebih dahulu.
4. Siapkan dan unggah dataset sesuai kebutuhan notebook.
5. Jalankan setiap cell secara berurutan.
6. Periksa hasil preprocessing, evaluasi model, profiling cluster, dan hasil akhir clustering.

## Tools dan Library

Tools dan library yang digunakan dalam pengerjaan dapat mencakup:

- Python
- Google Colab
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- HDBSCAN

## Catatan

Hasil clustering merupakan segmentasi berdasarkan pola yang ditemukan pada dataset. Interpretasi setiap cluster dan rekomendasi pemasaran didasarkan pada karakteristik data yang diperoleh dari proses analisis.

---

**UTS Machine Learning — Kelompok 14**
