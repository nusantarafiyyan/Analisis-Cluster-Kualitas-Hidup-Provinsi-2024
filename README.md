# 📊 Analisis Klasterisasi Provinsi Indonesia Menuju Indonesia Emas 2045

## 📌 Tentang Proyek

Proyek ini bertujuan untuk mengelompokkan 38 provinsi di Indonesia berdasarkan indikator kualitas hidup, guna mengevaluasi kesiapan masing-masing provinsi dalam mencapai target **Indonesia Emas 2045**. Pengelompokan ini diharapkan dapat menjadi dasar rekomendasi kebijakan yang lebih tepat sasaran dalam upaya pemerataan pembangunan dan peningkatan kualitas sumber daya manusia antar daerah.

## 🎯 Tujuan Cluster

- Mengelompokkan provinsi berdasarkan indikator kualitas hidup (ekonomi, pendidikan, kesehatan, sanitasi, akses digital, dan kepemilikan aset).
- Mengevaluasi kesiapan provinsi menuju visi Indonesia Emas 2045.
- Memberikan rekomendasi kebijakan berdasarkan karakteristik masing-masing cluster.

## 📊 Variabel yang Digunakan

| Variabel | Satuan | Indikator |
|----------|--------|------------|
| Pengeluaran per Kapita | Rupiah (Rp) | Ekonomi / Kesejahteraan Materi |
| Tamat SMA/SMK | Persen (%) | Pendidikan |
| BPJS Kesehatan | Persen (%) | Kesehatan |
| Toilet pribadi | Persen (%) | Sanitasi |
| Akses Internet | Persen (%) | Digital |
| Rumah Pribadi | Persen (%) | Kepemilikan Aset |

## 🛠️ Metode yang Digunakan

- **Metode Utama**: Hierarchical Clustering (Ward's linkage)
- **Metode Pembanding**: K-Means Clustering
- **Sumber Data**: BPS 2024 (38 provinsi)

## 📁 Struktur Notebook

Notebook ini terdiri dari beberapa tahapan utama:

1. **Import Library** dan pengaturan awal.
2. **Upload dataset** dari pengguna.
3. **Preprocessing data** (pembersihan, normalisasi, deteksi outlier).
4. **Hierarchical Clustering** dengan dendrogram untuk menentukan jumlah cluster optimal.
5. **K-Means Clustering** sebagai baseline.
6. **Evaluasi kinerja** (Silhouette Score, Davies-Bouldin Index, Adjusted Rand Index).
7. **Visualisasi hasil** dengan PCA.
8. **Interpretasi karakteristik cluster**.
9. **Analisis kesiapan menuju Indonesia Emas 2045**.
10. **Penyimpanan hasil** dalam file Excel.

## 📈 Hasil Utama

### Jumlah Cluster (AHC)
- **3 cluster** berdasarkan dendrogram (potongan pada jarak 10).

### Distribusi Provinsi per Cluster (setelah pengurutan berdasarkan kualitas hidup)

| Cluster | Status | Jumlah Provinsi | Contoh Provinsi |
|---------|--------|----------------|------------------|
| **Cluster 0** | ⚠️ PRIORITAS DARURAT (Kualitas Hidup Sangat Rendah) | 2 (5.3%) | Papua Tengah, Papua Pegunungan |
| **Cluster 1** | 📌 KETERTINGGALAN STRUKTURAL (Perlu Pembenahan Sistemik) | 19 (50.0%) | Jambi, Jawa Tengah, NTT, Maluku, dll. |
| **Cluster 2** | ✅ SIAP AKSELERASI (Benchmark) | 17 (44.7%) | DKI Jakarta, Bali, Riau, Kalimantan Timur, dll. |

### Evaluasi Kinerja Clustering

| Metode | Jumlah Cluster | Silhouette Score | Davies-Bouldin Index |
|--------|----------------|------------------|------------------------|
| AHC (Utama) | 3 | 0.2794 | 1.0190 |
| K-Means (Pembanding) | 2 | 0.5850 | 0.5583 |

- **Adjusted Rand Index (ARI)**: 0.1634 → hasil kedua metode **sangat berbeda** (wajar karena AHC tidak memaksakan bentuk cluster bulat seperti K-Means).

### Skor Kesiapan Menuju Indonesia Emas 2045

- **Rata-rata skor per cluster** (skala 0–100):
  - Cluster 0: 37.1 (Kurang Siap)
  - Cluster 1: 49.2 (Kurang Siap)
  - Cluster 2: 59.4 (Cukup Siap)

- **Top 5 Provinsi** dengan skor tertinggi:
  1. DKI Jakarta (78.4) – 🟢 Sangat Siap
  2. Kepulauan Riau (69.1) – 🟡 Cukup Siap
  3. Kalimantan Timur (66.7) – 🟡 Cukup Siap
  4. Bali (62.6) – 🟡 Cukup Siap
  5. DI Yogyakarta (62.2) – 🟡 Cukup Siap

- **5 Provinsi dengan skor terendah**:
  1. Papua Tengah (34.9) – 🔴 Kurang Siap
  2. Papua Pegunungan (39.4) – 🔴 Kurang Siap
  3. Nusa Tenggara Timur (42.5) – 🔴 Kurang Siap
  4. Kalimantan Tengah (45.6) – 🔴 Kurang Siap
  5. Papua Selatan (45.7) – 🔴 Kurang Siap

## 💡 Rekomendasi Kebijakan

- **Cluster 0 (Prioritas Darurat)**:
  Intervensi darurat pada pendidikan dasar, layanan kesehatan, dan infrastruktur internet.
- **Cluster 1 (Ketertinggalan Struktural)**:
  Program percepatan pembangunan SDM dan peningkatan akses internet secara masif.
- **Cluster 2 (Siap Akselerasi)**:
  Pertahankan kualitas, jadikan role model bagi provinsi lain.

## 📂 Output yang Dihasilkan

- File Excel: `hasil_clustering_provinsi_2024_FIXED.xlsx`  
  Berisi data lengkap provinsi beserta label cluster dan skor kesiapan.

## 🧠 Kesimpulan

- Mayoritas provinsi Indonesia (50%) masih berada dalam kategori **ketertinggalan struktural** dengan skor kesiapan di bawah 50.
- **Gap terbesar** antar cluster terdapat pada indikator **Akses Internet** (selisih hingga 57.9%).
- Target **Indonesia Emas 2045** masih jauh dari capaian saat ini; diperlukan intervensi kebijakan yang lebih agresif dan tepat sasaran.

## 🧰 Library yang Digunakan

- `pandas`, `numpy`
- `matplotlib`, `seaborn`
- `scikit-learn` (clustering, preprocessing, metrics, decomposition)
- `scipy.cluster.hierarchy`
- `google.colab` (upload & download file)

## 📎 Cara Menjalankan

1. Buka notebook di Google Colab atau Jupyter Notebook.
2. Jalankan semua sel secara berurutan.
3. Upload file dataset Excel dengan format sesuai permintaan.
4. Hasil clustering akan ditampilkan dalam bentuk visualisasi dan file Excel siap diunduh.

## 📄 Lisensi

Proyek ini dibuat untuk keperluan edukasi dan analisis kebijakan publik. Dataset bersumber dari BPS 2024.
