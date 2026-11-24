# Bukti Kontribusi Anggota — UTS Pembelajaran Mesin (Kelompok 14)

Dokumen ini merangkum pembagian peran, bukti Pull Request (PR) pada repositori [UTS-Machine-Learning-kelompok-14](https://github.com/mohamadnurtaufiq/UTS-Machine-Learning-kelompok-14), penggunaan alat AI, serta persetujuan seluruh anggota kelompok.

---

## 1. Peran Anggota & Tautan Pull Request

| Nama Anggota | Akun GitHub | Peran & Cakupan Kontribusi | Bukti Pull Request / Commit |
| :--- | :--- | :--- | :--- |
| **Dwiki Diastoro** | [dwikidias](https://www.google.com/search?q=https://github.com/dwikidias) | **Task 1 — Regression (Estimasi Durasi Pengiriman `P50` & `P90`):** audit kualitas data & kebocoran fitur (`jumlah_scan`), desain *Time-Based Validation* vs *5-Fold CV*, *feature engineering* bebas kebocoran, pemodelan *Baseline*, *Ridge*, dan *Tuned LightGBM + CQR*, *error breakdown* (`layanan`, `pulau_tujuan`, `mitra_kurir` `K07`) & interpretasi SHAP. | [PR #2](https://github.com/mohamadnurtaufiq/UTS-Machine-Learning-kelompok-14/pull/2), [PR #3](https://github.com/mohamadnurtaufiq/UTS-Machine-Learning-kelompok-14/pull/3),  [PR #6](https://github.com/mohamadnurtaufiq/UTS-Machine-Learning-kelompok-14/pull/6), [PR #7](https://github.com/mohamadnurtaufiq/UTS-Machine-Learning-kelompok-14/pull/7). |
| **Mohamad Nur Taufiq** | [`mohamadnurtaufiq`](https://github.com/mohamadnurtaufiq) | | |
| **Irfan Rizky Maulana** | [irfan060606](https://www.google.com/search?q=https://github.com/irfan060606) | | |

---

## 2. Penggunaan Alat AI (*AI Tools Disclosure*)

Sesuai ketentuan tugas (`UTS ML.xlsx`), penggunaan alat bantu AI selama pengerjaan proyek dicatat secara transparan per anggota:

### Dwiki Diastoro (Task 1 — Regression)
* **Alat AI yang Digunakan:** Gemini (Google AI).
* **Bagian yang Dibantu:**
  1. Penelaahan struktur kode Python dan pemecahan masalah teknis (*debugging* eror Google Colab, pemuatan otomatis `dataset/` tanpa *Choose Files*, dan perbaikan kompatibilitas `align_categories`).
  2. Penyusunan draf dokumentasi (`README.md`, `kontribusi.md`) serta kerangka teks akademik Bab I–II laporan berdasarkan keluaran aktual notebook.
  3. Pembuatan grafik evaluasi dari metrik hasil eksperimen yang telah dijalankan.
* **Cara Memverifikasi Keluaran AI:**
  1. Menjalankan ulang `kode/01_regresi.ipynb` secara penuh (*Restart & Run All*) pada *runtime* baru dengan `dataset/` resmi dari dosen.
  2. Mencocokkan seluruh angka metrik, tabel, dan grafik pada laporan dengan keluaran eksekusi notebook.
  3. Memvalidasi `hasil/prediksi_regresi.csv` secara terprogram untuk memastikan kolom (`id_paket, p50, p90`), jumlah baris (`60.000`), ketiadaan `NaN`, serta aturan `p90 >= p50`.

### Mohamad Nur Taufiq (Task 2 — Classification)
* **Alat AI yang Digunakan:** *(diisi oleh anggota terkait)*
* **Bagian yang Dibantu:** *(diisi oleh anggota terkait)*
* **Cara Memverifikasi Keluaran AI:** *(diisi oleh anggota terkait)*

### Irfan Rizky Maulana (Task 3 — Clustering)
* **Alat AI yang Digunakan:** *(diisi oleh anggota terkait)*
* **Bagian yang Dibantu:** *(diisi oleh anggota terkait)*
* **Cara Memverifikasi Keluaran AI:** *(diisi oleh anggota terkait)*

---

## 3. Persetujuan Anggota Kelompok

Seluruh anggota menyatakan bertanggung jawab memahami dan mampu mereproduksi seluruh tugas pada ujian lisan:

- [x] **Dwiki Diastoro** (`dwikidias`) — Menyetujui
- [ ] **Mohamad Nur Taufiq** (`mohamadnurtaufiq`) — Menunggu pengisian & persetujuan
- [ ] **Irfan Rizky Maulana** (`irfan060606`) — Menunggu pengisian & persetujuan
