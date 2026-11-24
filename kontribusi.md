# Bukti Kontribusi Anggota: UTS Pembelajaran Mesin (Kelompok 14)

Catatan pembagian peran, tautan Pull Request (PR) di repositori [UTS-Machine-Learning-kelompok-14](https://github.com/mohamadnurtaufiq/UTS-Machine-Learning-kelompok-14), penggunaan alat AI, dan persetujuan anggota Kelompok 14.

## 1. Peran Anggota & Tautan Pull Request

| Nama Anggota | Akun GitHub | Peran & Cakupan Kontribusi | Bukti Pull Request / Commit |
| :--- | :--- | :--- | :--- |
| **Dwiki Diastoro** | [`dwikidias`](https://github.com/dwikidias) | Mengerjakan Tugas 1 Regresi (estimasi durasi kirim `P50` dan `P90`): audit kualitas data dan pembuangan fitur bocor (`jumlah_scan`), perbandingan *Time-Based Validation* dan *5-Fold CV*, *feature engineering* bebas kebocoran, pemodelan *Baseline*, *Ridge*, serta *Tuned LightGBM + CQR*, analisis error per segmen (`layanan`, `pulau_tujuan`, `mitra_kurir` `K07`), interpretasi SHAP, penataan folder `dataset/` dan `kode/`, serta penulisan laporan Bab I dan Bab II. | [PR #2](https://github.com/mohamadnurtaufiq/UTS-Machine-Learning-kelompok-14/pull/2), [PR #3](https://github.com/mohamadnurtaufiq/UTS-Machine-Learning-kelompok-14/pull/3), [PR #6](https://github.com/mohamadnurtaufiq/UTS-Machine-Learning-kelompok-14/pull/6), [PR #7](https://github.com/mohamadnurtaufiq/UTS-Machine-Learning-kelompok-14/pull/7) |
| **Mohamad Nur Taufiq** | [`mohamadnurtaufiq`](https://github.com/mohamadnurtaufiq) | | |
| **Irfan Rizky Maulana** | [`irfan060606`](https://github.com/irfan060606) | | |

## 2. Penggunaan Alat AI (*AI Tools Disclosure*)

Sesuai aturan tugas pada `UTS ML.xlsx`, tiap anggota mencatat alat AI yang dipakai beserta cara mengecek hasilnya.

### Dwiki Diastoro (Task 1: Regression)

Pada bagian ini, alat AI yang dipakai adalah Gemini (Google AI) untuk tiga keperluan:
1. Mengecek struktur kode Python serta *debugging* eror di Google Colab, pemuatan otomatis `dataset/` tanpa memilih file manual, dan kompatibilitas `align_categories`.
2. Menyusun draf awal `README.md`, `kontribusi.md`, serta kerangka Bab I dan Bab II laporan dari hasil notebook.
3. Membuat kode grafik evaluasi berdasarkan metrik eksperimen.

Setiap keluaran AI dicek langsung sebelum dipakai. Notebook `kode/01_regresi.ipynb` dijalankan ulang penuh (*Restart & Run All*) pada *runtime* baru dengan `dataset/` resmi dari dosen. Setelah itu, angka metrik, tabel, dan grafik di laporan dicocokkan ulang dengan hasil eksekusi notebook, lalu `hasil/prediksi_regresi.csv` divalidasi untuk memastikan kolom (`id_paket`, `p50`, `p90`), jumlah baris (`60.000`), bebas `NaN`, dan syarat `p90 >= p50`.

### Mohamad Nur Taufiq (Task 2: Classification)

Catatan alat AI, bagian yang dibantu, dan cara verifikasi akan diisi oleh anggota terkait.

### Irfan Rizky Maulana (Task 3: Clustering)

Catatan alat AI, bagian yang dibantu, dan cara verifikasi akan diisi oleh anggota terkait.

## 3. Persetujuan Anggota Kelompok

Seluruh anggota menyatakan memahami isi pengerjaan dan siap menjelaskan serta menjalankan ulang tugas pada ujian lisan:

- [x] **Dwiki Diastoro** (`dwikidias`): Menyetujui
- [ ] **Mohamad Nur Taufiq** (`mohamadnurtaufiq`): Menunggu pengisian dan persetujuan
- [ ] **Irfan Rizky Maulana** (`irfan060606`): Menunggu pengisian dan persetujuan
