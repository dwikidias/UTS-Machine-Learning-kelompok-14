# Bukti Kontribusi Anggota: UTS Pembelajaran Mesin (Kelompok 14)

Catatan pembagian peran, tautan Pull Request (PR) di repositori [UTS-Machine-Learning-kelompok-14](https://github.com/mohamadnurtaufiq/UTS-Machine-Learning-kelompok-14), penggunaan alat AI, dan persetujuan anggota Kelompok 14.

## 1. Peran Anggota & Tautan Pull Request

| Nama Anggota | Akun GitHub | Peran & Cakupan Kontribusi | Bukti Pull Request / Commit |
| :--- | :--- | :--- | :--- |
| **Dwiki Diastoro** | [`dwikidias`](https://github.com/dwikidias) | Mengerjakan Tugas 1 Regresi (estimasi durasi kirim `P50` dan `P90`): audit kualitas data dan pembuangan fitur bocor (`jumlah_scan`), perbandingan *Time-Based Validation* dan *5-Fold CV*, *feature engineering* bebas kebocoran, pemodelan *Baseline*, *Ridge*, serta *Tuned LightGBM + CQR*, analisis error per segmen (`layanan`, `pulau_tujuan`, `mitra_kurir` `K07`), interpretasi SHAP, penataan folder `dataset/` dan `kode/`, serta penulisan laporan Bab I dan Bab II. | [PR #2](https://github.com/mohamadnurtaufiq/UTS-Machine-Learning-kelompok-14/pull/2), [PR #3](https://github.com/mohamadnurtaufiq/UTS-Machine-Learning-kelompok-14/pull/3), [PR #6](https://github.com/mohamadnurtaufiq/UTS-Machine-Learning-kelompok-14/pull/6), [PR #7](https://github.com/mohamadnurtaufiq/UTS-Machine-Learning-kelompok-14/pull/7) |
| **Mohamad Nur Taufiq** | [`mohamadnurtaufiq`](https://github.com/mohamadnurtaufiq) | Mengerjakan Tugas 2 Klasifikasi (prediksi kategori/kelas target pada `02_classification.ipynb`): eksplorasi data (EDA) dan pemeriksaan distribusi kelas, pembersihan data serta penanganan *missing values* dan encoding fitur kategorikal, *feature engineering* dan pembagian data latih-uji (*train-test split* / validasi silang), perbandingan dan *hyperparameter tuning* beberapa model klasifikasi, evaluasi performa menggunakan metrik klasifikasi (*Accuracy*, *Precision*, *Recall*, *F1-Score*, *ROC-AUC*, dan *Confusion Matrix*), analisis *feature importance* serta error prediksi, ekspor file hasil prediksi klasifikasi, penulisan laporan bagian Tugas 2 Klasifikasi, serta pengelolaan repositori utama GitHub Kelompok 14 (*review* dan *merge* Pull Request). | [Commit f95cb53](https://github.com/mohamadnurtaufiq/UTS-Machine-Learning-kelompok-14/commit/f95cb53), [Commit ac8b3a1](https://github.com/mohamadnurtaufiq/UTS-Machine-Learning-kelompok-14/commit/ac8b3a1) |
| **Irfan Rizky Maulana** | [`irfan060606`](https://github.com/irfan060606) | Mengerjakan Tugas 3 Clustering: pemeriksaan dan eksplorasi data, pemilihan fitur untuk pemodelan clustering, preprocessing data numerik dan kategorikal, transformasi fitur serta scaling, reduksi dimensi menggunakan PCA, pemodelan dan perbandingan algoritma K-Means, Gaussian Mixture Model (GMM), dan HDBSCAN, evaluasi hasil clustering menggunakan metrik yang sesuai, analisis profil cluster dan interpretasi karakteristik pelanggan, deteksi anomali berdasarkan jarak terhadap centroid, pengujian stabilitas clustering menggunakan Adjusted Rand Index (ARI), perbaikan error pada evaluasi Silhouette, penyesuaian mekanisme pemuatan dataset otomatis dari GitHub dengan alternatif file lokal/unggah manual, pengujian eksekusi notebook dari awal hingga akhir (*Run All*), serta pembuatan dan pemeriksaan file hasil clustering. | [Repositori Fork](https://github.com/irfan060606/UTS-Machine-Learning-kelompok-14) (Pull Request ke repositori utama: diisi setelah PR dibuat) |

## 2. Penggunaan Alat AI (*AI Tools Disclosure*)

Sesuai aturan tugas pada `UTS ML.xlsx`, tiap anggota mencatat alat AI yang dipakai beserta cara mengecek hasilnya.

### Dwiki Diastoro (Task 1: Regression)

Pada bagian ini, alat AI yang dipakai adalah Gemini (Google AI) untuk tiga keperluan:
1. Mengecek struktur kode Python serta *debugging* eror di Google Colab, pemuatan otomatis `dataset/` tanpa memilih file manual, dan kompatibilitas `align_categories`.
2. Menyusun draf awal `README.md`, `kontribusi.md`, serta kerangka Bab I dan Bab II laporan dari hasil notebook.
3. Membuat kode grafik evaluasi berdasarkan metrik eksperimen.

Setiap keluaran AI dicek langsung sebelum dipakai. Notebook `kode/01_regresi.ipynb` dijalankan ulang penuh (*Restart & Run All*) pada *runtime* baru dengan `dataset/` resmi dari dosen. Setelah itu, angka metrik, tabel, dan grafik di laporan dicocokkan ulang dengan hasil eksekusi notebook, lalu `hasil/prediksi_regresi.csv` divalidasi untuk memastikan kolom (`id_paket`, `p50`, `p90`), jumlah baris (`60.000`), bebas `NaN`, dan syarat `p90 >= p50`.

### Mohamad Nur Taufiq (Task 2: Classification)

Pada bagian ini, alat AI yang dipakai adalah Gemini (Google AI) untuk beberapa keperluan:
1. Membantu *debugging* kode Python di Google Colab, termasuk penyesuaian jalur pembacaan dataset langsung dari tautan *raw* GitHub agar notebook dapat dijalankan tanpa unggah file manual.
2. Membantu menyusun struktur *preprocessing*, pemilihan fitur, pelatihan, serta evaluasi model klasifikasi pada notebook `02_classification.ipynb`.
3. Membantu penyusunan dokumentasi kontribusi dan pelacakan riwayat commit pada `kontribusi.md`.

Setiap keluaran AI diperiksa dan diuji ulang secara mandiri. Notebook `02_classification.ipynb` dijalankan ulang secara penuh (*Restart & Run All*) di Google Colab untuk memastikan seluruh sel berjalan bebas eror, metrik evaluasi valid, serta format file hasil prediksi klasifikasi sesuai dengan ketentuan dataset dan bebas nilai kosong (`NaN`).

### Irfan Rizky Maulana (Task 3: Clustering)

Pada bagian ini, alat AI yang dipakai adalah ChatGPT (OpenAI) untuk beberapa keperluan:
1. Membantu penelaahan dan perbaikan kode Python pada notebook Clustering, termasuk *debugging* error pada evaluasi Silhouette dan penanganan sampel evaluasi yang tidak mencakup seluruh label cluster.
2. Membantu meninjau preprocessing, pemilihan fitur, reduksi dimensi menggunakan PCA, serta implementasi dan evaluasi algoritma K-Means, Gaussian Mixture Model (GMM), dan HDBSCAN.
3. Membantu menyesuaikan mekanisme pemuatan dataset otomatis dari repositori GitHub dengan alternatif file lokal atau unggahan manual, serta perbaikan bagian kode agar notebook dapat dijalankan secara menyeluruh.
4. Membantu menyusun analisis hasil clustering, interpretasi profil cluster, evaluasi stabilitas menggunakan Adjusted Rand Index (ARI), dan dokumentasi hasil reproduksi notebook.

Setiap keluaran AI diperiksa melalui eksekusi dan peninjauan hasil notebook. Notebook Clustering dijalankan dari awal hingga akhir (*Run All*) untuk memastikan seluruh sel kode dapat dieksekusi tanpa error. Pada pengujian yang dilakukan, seluruh 19 sel kode berhasil dijalankan. Hasil preprocessing, evaluasi clustering, distribusi anggota cluster, profil cluster, dan hasil deteksi anomali diperiksa berdasarkan keluaran aktual notebook. File hasil clustering, termasuk `cluster.csv`, juga diperiksa untuk memastikan berhasil dihasilkan. Pengujian pemuatan dataset menggunakan file lokal sebagai fallback dilakukan ketika koneksi GitHub mengalami kendala pada lingkungan pengujian.

## 3. Persetujuan Anggota Kelompok

Seluruh anggota menyatakan memahami isi pengerjaan dan siap menjelaskan serta menjalankan ulang tugas pada ujian lisan:

- [x] **Dwiki Diastoro** (`dwikidias`): Menyetujui
- [x] **Mohamad Nur Taufiq** (`mohamadnurtaufiq`): Menyetujui
- [x] **Irfan Rizky Maulana** (`irfan060606`): Menyetujui
