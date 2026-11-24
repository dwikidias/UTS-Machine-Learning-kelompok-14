# UTS Machine Learning — Kelompok 14

Repository ini berisi implementasi, dataset, dokumentasi, dan hasil pengerjaan Ujian Tengah Semester (UTS) mata kuliah Machine Learning oleh Kelompok 14.

Proyek ini menerapkan tiga pendekatan Machine Learning untuk menyelesaikan permasalahan pada bidang e-commerce dan logistik, yaitu:

1. **Regression** — Estimasi durasi pengiriman paket.
2. **Classification** — Deteksi fraud pada transaksi digital.
3. **Clustering** — Segmentasi pelanggan berdasarkan pola aktivitas dan transaksi.

Setiap tugas menggunakan pendekatan Machine Learning yang disesuaikan dengan tujuan analisis masing-masing. Seluruh tahapan pengerjaan didokumentasikan dalam notebook Python, mulai dari pemeriksaan dataset, preprocessing, pemodelan, evaluasi, hingga pembuatan file hasil.

---

## Anggota Kelompok dan Pembagian Tugas

| Anggota | Peran |
|---|---|
| Dwiki Diastoro | Task 1 — Regression |
| Mohamad Nur Taufiq | Task 2 — Classification dan Koordinator Kelompok |
| Irfan Rizky Maulana | Task 3 — Customer Clustering |

Informasi lebih lengkap mengenai pembagian kontribusi dan penggunaan alat bantu AI dapat dilihat pada file [`kontribusi.md`](kontribusi.md).

---

## Struktur Repository

Struktur direktori repository Kelompok 14 adalah sebagai berikut:

```text
UTS-Machine-Learning-kelompok-14/
│
├── dataset/
│   ├── clustering.csv.gz
│   ├── kamus_data.md
│   ├── klasifikasi_test.csv.gz
│   ├── klasifikasi_train.csv.gz
│   ├── regresi_test.csv.gz
│   └── regresi_train.csv.gz
│
├── hasil/
│   ├── cluster.csv
│   ├── prediksi_klasifikasi.csv
│   ├── prediksi_regresi.csv
│
├── kode/
│   ├── 01_regresi.ipynb
│   ├── 02_classification.ipynb
│   ├── 03_clustering.ipynb
│   └── requirements_regresi.txt
│
├── README.md
└── kontribusi.md
```

### Penjelasan Direktori dan File

| Direktori/File | Keterangan |
|---|---|
| `dataset/` | Menyimpan seluruh dataset yang digunakan dalam tiga tugas beserta dokumentasi kamus data. |
| `hasil/` | Menyimpan file hasil prediksi regresi, klasifikasi, dan label clustering. |
| `kode/` | Menyimpan tiga notebook utama dan file dependensi untuk tugas Regression. |
| `README.md` | Dokumentasi utama repository dan panduan pengerjaan proyek. |
| `kontribusi.md` | Dokumentasi pembagian tugas, kontribusi anggota, dan penggunaan alat AI. |

---

# Task 1 — Regression

## Estimasi Durasi Pengiriman Paket

Task Regression bertujuan untuk memperkirakan durasi pengiriman paket berdasarkan karakteristik dan informasi pengiriman yang tersedia.

Model menghasilkan dua estimasi kuantil, yaitu:

- **P50:** estimasi median durasi pengiriman.
- **P90:** estimasi batas atas durasi pengiriman pada kuantil ke-90.

### Dataset

| Dataset | Jumlah Baris | Jumlah Kolom |
|---|---:|---:|
| `regresi_train.csv.gz` | 250.000 | 77 |
| `regresi_test.csv.gz` | 60.000 | 76 |

Data latih mencakup periode Januari–Agustus 2025, sedangkan data uji mencakup September–Oktober 2025.

### Metode dan Tahapan Analisis

1. **Data Audit** — pemeriksaan kualitas data, nilai kosong, anomali, dan duplikasi.
2. **Data Leakage Detection** — pemeriksaan fitur `jumlah_scan` yang mengandung informasi setelah paket dijemput sehingga dikeluarkan dari fitur pelatihan.
3. **Feature Engineering** — penyiapan fitur numerik dan kategorikal untuk proses pemodelan.
4. **Time-Based Validation** — pembagian data berdasarkan urutan waktu untuk menghindari kebocoran informasi masa depan.
5. **Model Comparison** — perbandingan Baseline, Ridge Regression, dan LightGBM Quantile.
6. **Hyperparameter Tuning** — pencarian konfigurasi LightGBM yang sesuai.
7. **Uncertainty Calibration** — penerapan Conformalized Quantile Regression (CQR) untuk kalibrasi estimasi P90.
8. **Model Evaluation** — evaluasi menggunakan Pinball Loss dan P90 Coverage.
9. **SHAP Analysis** — analisis kontribusi fitur terhadap prediksi model.

### Model Akhir dan Hasil Evaluasi

Model yang digunakan sebagai model final adalah **Tuned LightGBM + CQR**.

Pada set evaluasi Agustus 2025, model memperoleh hasil:

| Metrik | Hasil |
|---|---:|
| Pinball Loss P50 | 10,7390 |
| Pinball Loss P90 | 11,3658 |
| P90 Coverage | 90,54% |

Model menggunakan konstanta kalibrasi P90 sebesar +5,8094 jam.

### Output

File hasil prediksi disimpan pada:

`hasil/prediksi_regresi.csv`

File tersebut memiliki tiga kolom:

| Kolom | Keterangan |
|---|---|
| `id_paket` | Identitas paket |
| `p50` | Estimasi median durasi pengiriman |
| `p90` | Estimasi batas atas durasi pengiriman |

Hasil prediksi berisi 60.000 baris dan telah diperiksa terhadap nilai kosong, duplikasi, serta ketentuan `p90 >= p50`.

Notebook: [`kode/01_regresi.ipynb`](kode/01_regresi.ipynb)

---

# Task 2 — Classification

## Deteksi Fraud Transaksi Digital

Task Classification bertujuan untuk mengidentifikasi transaksi yang berpotensi fraud berdasarkan karakteristik transaksi, pengguna, merchant, perangkat, dan sinyal keamanan.

Model menghasilkan probabilitas fraud dan keputusan apakah transaksi perlu ditandai untuk ditinjau.

### Dataset

| Dataset | Jumlah Baris | Jumlah Kolom |
|---|---:|---:|
| `klasifikasi_train.csv.gz` | 403.077 | 85 |
| `klasifikasi_test.csv.gz` | 106.674 | 84 |

Data latih mencakup periode Januari–Agustus 2025, sedangkan data uji mencakup September–Oktober 2025.

Data latih memiliki ketidakseimbangan kelas yang tinggi, dengan tingkat fraud sekitar 0,65%.

### Metode dan Tahapan Analisis

1. **Exploratory Data Analysis (EDA)** — pemeriksaan distribusi transaksi dan proporsi kelas fraud.
2. **Data Audit** — pemeriksaan nilai kosong, duplikasi, serta kualitas data.
3. **Feature Engineering** — pembentukan fitur waktu dan rasio perilaku transaksi.
4. **Feature Selection** — mengeluarkan fitur identitas dan fitur yang berisiko menyebabkan data leakage.
5. **Time-Based Validation** — pemisahan data berdasarkan waktu transaksi.
6. **Data Preprocessing** — imputasi nilai kosong, scaling fitur numerik, dan One-Hot Encoding untuk fitur kategorikal.
7. **Model Comparison** — membandingkan tiga pendekatan:
   - Logistic Regression dengan class weighting.
   - Random Forest dengan class weighting.
   - Logistic Regression dengan random undersampling.
8. **Probability Calibration** — kalibrasi probabilitas menggunakan metode sigmoid (Platt).
9. **Cost-Based Threshold Selection** — pemilihan threshold berdasarkan total biaya peninjauan dan kerugian akibat fraud yang tidak terdeteksi.
10. **Model Evaluation** — evaluasi menggunakan Precision, Recall, F1-Score, PR-AUC, ROC-AUC, Brier Score, dan total biaya.
11. **Pattern Shift Analysis** — pemeriksaan perubahan pola fraud berdasarkan waktu, kanal pembayaran, dan kategori merchant.

### Aturan Perhitungan Biaya

Evaluasi model mempertimbangkan dua komponen biaya:

- Biaya peninjauan manual sebesar Rp25.000 untuk setiap transaksi yang ditandai.
- Kerugian sebesar nominal transaksi untuk fraud yang tidak ditandai.

Model dan threshold dipilih berdasarkan total biaya validasi terendah.

### Output

File hasil prediksi disimpan pada:

`hasil/prediksi_klasifikasi.csv`

File tersebut memiliki tiga kolom:

| Kolom | Keterangan |
|---|---|
| `id_transaksi` | Identitas transaksi |
| `prob` | Probabilitas fraud |
| `tandai` | Keputusan penandaan transaksi (0 atau 1) |

Notebook: [`kode/02_classification.ipynb`](kode/02_classification.ipynb)

---

# Task 3 — Clustering

## Customer Segmentation

Task Clustering bertujuan untuk mengelompokkan pelanggan berdasarkan karakteristik, aktivitas, dan pola transaksi tanpa menggunakan label target.

Hasil segmentasi digunakan untuk memahami karakteristik pelanggan serta menyusun rekomendasi strategi pemasaran.

### Dataset

Dataset yang digunakan adalah:

`dataset/clustering.csv.gz`

Dataset terdiri dari sekitar 120.000 pelanggan dengan 60 kolom.

### Metode dan Tahapan Analisis

1. **Data Audit** — pemeriksaan struktur data, nilai kosong, duplikasi, dan nilai numerik tidak valid.
2. **Feature Selection** — pemilihan fitur yang relevan serta pengeluaran identitas pelanggan dan fitur anonim `n01–n15` dari model utama.
3. **Data Preprocessing** — imputasi nilai kosong, transformasi fitur komposisi menggunakan CLR, transformasi `log1p`, One-Hot Encoding, dan RobustScaler.
4. **Principal Component Analysis (PCA)** — reduksi dimensi untuk membantu proses pemodelan.
5. **Model Comparison** — membandingkan K-Means, Gaussian Mixture Model (GMM), dan HDBSCAN.
6. **Cluster Evaluation** — evaluasi menggunakan Silhouette Score dan Davies-Bouldin Index.
7. **Stability Testing** — pengujian kestabilan hasil clustering menggunakan Adjusted Rand Index (ARI) melalui tiga pengulangan subsampling.
8. **Customer Profiling** — analisis karakteristik dan perilaku masing-masing cluster.
9. **Anomaly Detection** — penandaan pelanggan anomali berdasarkan jarak terhadap centroid cluster.

### Model dan Hasil Segmentasi

Model akhir menggunakan **MiniBatch K-Means dengan dua cluster**. Setelah proses clustering, pelanggan dengan jarak terhadap centroid di atas persentil ke-99 di dalam cluster masing-masing diberi label `-1` sebagai anomali.

Hasil segmentasi akhir:

| Label | Jumlah Pelanggan | Persentase | Interpretasi |
|---|---:|---:|---|
| `-1` | 1.201 | 1,00% | Pelanggan dengan Aktivitas Digital Ekstrem (Anomali) |
| `0` | 112.131 | 93,44% | Pelanggan Aktif Bertransaksi |
| `1` | 6.668 | 5,56% | Pelanggan Tanpa Transaksi dalam 90 Hari |

Label `0` dan `1` merupakan hasil pengelompokan K-Means, sedangkan label `-1` merupakan label tambahan dari proses deteksi anomali.

### Output

File hasil clustering disimpan pada:

`hasil/cluster.csv`

File tersebut memiliki dua kolom:

| Kolom | Keterangan |
|---|---|
| `id_pelanggan` | Identitas pelanggan |
| `cluster` | Label hasil clustering |

File hasil berisi 120.000 baris dan telah diperiksa terhadap jumlah data, keunikan ID pelanggan, serta tipe data label cluster.

Notebook: [`kode/03_clustering.ipynb`](kode/03_clustering.ipynb)

---

# Cara Menjalankan Notebook

Ketiga notebook dapat dijalankan menggunakan Google Colab atau lingkungan Python yang mendukung Jupyter Notebook.

## Menjalankan melalui Google Colab

1. Buka repository GitHub Kelompok 14.
2. Masuk ke folder `kode/`.
3. Pilih notebook yang ingin dijalankan:
   - `01_regresi.ipynb`
   - `02_classification.ipynb`
   - `03_clustering.ipynb`
4. Unduh notebook atau buka melalui Google Colab.
5. Pastikan dataset yang diperlukan tersedia.
6. Jalankan seluruh cell notebook secara berurutan menggunakan **Runtime → Run all**.
7. Periksa hasil analisis dan file keluaran pada folder `hasil/`.

## Dependensi

Repository menyediakan file:

`kode/requirements_regresi.txt`

File tersebut berisi dependensi untuk pengerjaan Regression dan dapat dipasang dari direktori utama repository menggunakan:

```bash
pip install -r kode/requirements_regresi.txt
```

Untuk Classification dan Clustering, pastikan seluruh library yang diimpor pada notebook terkait tersedia pada lingkungan Python yang digunakan.

## Reproducibility

Setiap notebook memuat tahapan analisis dari pembacaan dataset hingga pembuatan file hasil.

Untuk menjaga reproducibility:

- Gunakan dataset yang tersedia pada folder `dataset/`.
- Jalankan notebook dari awal hingga akhir.
- Ikuti pembagian data dan konfigurasi eksperimen yang telah ditetapkan pada masing-masing notebook.
- Periksa kembali file hasil pada folder `hasil/`.
- Cocokkan metrik dan tabel hasil dengan dokumentasi laporan.

Mekanisme pemuatan dataset dapat berbeda antar-notebook. Ikuti instruksi pemuatan data yang tersedia di dalam masing-masing notebook.

---

## Dokumentasi Tambahan

| Dokumen | Keterangan |
|---|---|
| [`dataset/kamus_data.md`](dataset/kamus_data.md) | Dokumentasi definisi dan informasi fitur dataset. |
| [`kontribusi.md`](kontribusi.md) | Pembagian peran, kontribusi anggota, dan penggunaan alat AI. |
| [`kode/requirements_regresi.txt`](kode/requirements_regresi.txt) | Daftar dependensi untuk Task Regression. |

---

## Penutup

Repository ini merupakan dokumentasi pengerjaan UTS Machine Learning Kelompok 14 yang mencakup proses pengolahan data, penerapan algoritma Machine Learning, evaluasi model, interpretasi hasil, dan pembuatan keluaran untuk tiga permasalahan yang berbeda.

Seluruh hasil analisis didasarkan pada implementasi dan keluaran notebook masing-masing tugas.

---

**UTS Machine Learning — Kelompok 14**
