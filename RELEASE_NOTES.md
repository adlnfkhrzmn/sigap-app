# Catatan Rilis SIGAP POS

Dokumen ini memuat catatan rilis resmi untuk aplikasi kasir **SIGAP POS** (*point-of-sale*) Android.

---

## Versi 1.1.0 (21 Oktober 2026)

### Ringkasan Rilis

- **Versi Aplikasi**: `1.1.0`
- **Kode Versi (Version Code)**: `2`
- **ID Paket (Application ID)**: `io.github.adlnfkhrzmn.sigap`
- **Persyaratan Sistem**: Minimum Android 8.0 (API level 26 / Oreo) atau versi yang lebih baru
- **Target SDK**: Android 14 (API level 34)
- **Ukuran Berkas APK**: `13.583.041` bytes (~`13,58 MB`)
- **Nama Berkas Rilis**: `SIGAP.apk`
- **Status Publikasi**: Calon rilis disiapkan secara lokal (*Prepared Locally*), menunggu konfirmasi rilis resmi.

### Pembaruan Utama pada Versi 1.1.0

#### 1. Manajemen Sesi Kasir & Laci Kas (Cash Drawer)
- **Pelacakan Sesi Kasir (Shift)**: Kasir dapat membuka dan menutup sesi kerja dengan pencatatan modal awal (*starting cash*), saldo kas akhir fisik saat tutup shift, perhitungan otomatis ekspektasi kas sistem, serta selisih kas (*cash difference*).
- **Pergerakan Kas Laci (Drawer Movement)**: Pencatatan arus kas masuk (*Cash In*) dan kas keluar (*Cash Out*) di luar penjualan langsung (misalnya setoran modal tambahan atau pengambilan uang tunai).
- **Penugasan Shift Fleksibel**: Transaksi penjualan kasir dapat dilakukan baik saat shift aktif sedang berjalan maupun tanpa membuka shift terlebih dahulu.
- **Pencatatan Pembayaran Terpisah (Split-Payment)**: Mendukung transaksi dengan kombinasi metode pembayaran Tunai dan QRIS secara bersamaan, lengkap dengan pencatatan alokasi nominal masing-masing tender pada entitas pembayaran terpisah (`TransactionPaymentEntity`).
- **Kompatibilitas Cadangan & Pemulihan**: Mekanisme backup dan restore SQLite lokal diperbarui ke skema Room versi 7 untuk mencadangkan dan memulihkan seluruh data shift, pergerakan laci, retur, pengeluaran, dan pembayaran split secara atomik.
- **Buku Besar Stok Awal (Stock Ledger)**: Pencatatan pergerakan mutasi stok barang (`StockMovementEntity`) sebagai fondasi pelacakan audit persediaan.

#### 2. Koreksi Transaksi & Integritas Finansial
- **Pembatalan Transaksi (Cancellation)**: Kasir dapat membatalkan transaksi yang keliru; sistem memulihkan stok produk kembali ke katalog, mencatat pengembalian kas laci jika transaksi menggunakan tunai, dan mencatat riwayat pembatalan secara terverifikasi.
- **Retur Produk Fleksibel**: Mendukung pengembalian barang per item dari transaksi yang sudah selesai, baik dengan pengembalian dana tunai langsung dari laci (*drawer cash refund*) maupun penyelesaian non-laci/eksternal.
- **Klasifikasi Barang Retur (Restock vs. Scrap)**: Barang yang diretur dapat dipilih untuk dimasukkan kembali ke persediaan toko (*restock*) jika kondisi masih baik, atau dicatat sebagai barang rusak/dibuang (*scrap*) tanpa menambah stok fisik.
- **Alokasi Nilai Rupiah Retur Sebagian yang Presisi**: Kalkulasi nilai pengembalian dana pada retur parsial memperhitungkan potongan diskon tingkat item secara proporsional berdasarkan harga efektif produk, memastikan jumlah uang yang dikembalikan tidak pernah melebihi nominal pembayaran riil pelanggan.
- **Rekonsiliasi Finansial Menyeluruh**: Rekapitulasi penjualan kotor, pengembalian dana, dan biaya pokok penjualan disesuaikan secara konsisten di seluruh laporan keuangan.

#### 3. Biaya Operasional & Laporan Laba Rugi
- **Pencatatan Pengeluaran (Expense Tracking)**: Mencatat biaya operasional toko (seperti listrik, air, sewa, bahan habis pakai) dilengkapi kategori, deskripsi, tanggal, dan opsi melampirkan foto nota/struk belanja dari galeri.
- **Pemisahan Sumber Dana Pengeluaran**: Sistem membedakan secara tegas antara pengeluaran yang memotong uang kas laci kasir (*affects drawer cash*) dan pengeluaran yang dibayar melalui rekening eksternal/transfer bank.
- **Laporan Laba Rugi Komprehensif**: Menghitung laba bersih operasional berdasarkan rumus: `Penjualan Bersih - Harga Pokok Penjualan (HPP) - Biaya Operasional`.
- **Indikator Estimasi Laba yang Jujur**: Apabila terdapat produk terjual yang belum memiliki data harga modal (HPP historis tidak diketahui), sistem menampilkan indikator estimasi/provisional dan tidak menampilkan laba bersih palsu seolah-olah bernilai definitif.

#### 4. Usabilitas Riwayat & Laporan
- **Filter Tanggal Konsisten & Ringkas**: Komponen pemfilter tanggal baru (`DateFilterRow`) yang rapi dan responsif, mendukung 4 pilihan standar pada Riwayat Transaksi maupun Laporan Penjualan: **Hari Ini**, **Kemarin**, **7 Hari Terakhir**, dan **Custom** (rentang tanggal kalender bebas). Filter yang tidak didukung (seperti opsi 30 hari) tidak disediakan untuk menjaga konsistensi data.
- **Tampilan Rincian Transaksi yang Lebih Informatif**: Menampilkan status pembatalan, riwayat retur, rincian pembayaran split tunai/QRIS, serta tautan ke transaksi asal.

#### 5. Peningkatan Integritas Spreadsheet & Impor-Ekspor
- **Skema Ekspor Penjualan Lengkap**: Berkas ekspor penjualan (Excel multi-lembar dan paket CSV) kini menyertakan kolom `Subtotal`, `Diskon`, `Nominal Tunai`, dan `Nominal QRIS` berdasarkan alokasi tender riil.
- **Rincian Diskon Tingkat Item**: Lembar rincian produk memuat kolom `Diskon Satuan` dan `Diskon Baris` untuk transparansi pelaporan diskon per barang.
- **Pembedaan Nominal Alokasi Tender vs Uang Diserahkan**: Ekspor mencatat nominal pasti yang menjadi hak bayar tender, bukan uang fisik diserahkan pelanggan sebelum dikurangi kembalian.
- **Filter Otomatis Lembar Kerja yang Aman**: AutoFilter Excel hanya diaktifkan bila tabel memiliki baris data, mencegah kesalahan pembacaan berkas pada tabel kosong.
- **Validasi Ketat Relasional Impor Penjualan**: Pemeriksaan integritas data mencakup kecocokan kuantitas item, harga satuan, diskon baris, subtotal transaksi, total diskon, total akhir, serta alokasi pembayaran tender menggunakan aritmatika integer yang aman dari luapan (*overflow-safe*).
- **Penolakan Format CSV Ringkasan Datar Tanpa Rincian**: Sistem secara tegas menolak impor CSV ringkasan satu lembar tanpa rincian item (*flat summary CSV*) guna mencegah fabrikasi harga produk atau pembagian nominal transaksi secara acak.
- **Penolakan Impor Bersifat Atomik**: Jika ditemukan ketidaksesuaian data pada berkas yang diimpor, seluruh proses dibatalkan tanpa mengimpor sebagian transaksi, menjaga basis data tetap bersih dari data korup.
- **Unduh Template Impor & Lembar Kerja**: Tersedia berkas template Excel/CSV siap pakai untuk impor katalog produk (`Template_Impor_Produk_SIGAP.xlsx`) dan lembar kerja stock opname fisik (`Lembar_Kerja_Stock_Opname_SIGAP.xlsx`).

#### 6. Perbaikan Lainnya
- **Optimalisasi Tampilan Foto Produk**: Komponen gambar `ProductArtwork` dengan rasio aspek terjaga, penanganan caching memori, dan placeholder ikon cadangan yang konsisten.
- **Penyelarasan Tata Letak Responsif**: Tampilan dialog dan tata letak menu Data & Berkas dioptimalkan untuk berbagai resolusi layar Android.

### Integritas Berkas dan Verifikasi Keamanan v1.1.0

| Parameter | Nilai Resmi |
| :--- | :--- |
| **Nama Berkas Rilis** | `SIGAP.apk` |
| **Versi Aplikasi** | `1.1.0` (Version Code: `2`) |
| **ID Paket** | `io.github.adlnfkhrzmn.sigap` |
| **Ukuran Berkas** | `13.583.041` bytes (~`13,58 MB`) |
| **SHA-256 Berkas APK** | `1cd255abc749bd25a46610a9d12fcd954c9cf0fca62f98fd040741acb0267573` |
| **SHA-256 Sertifikat Penandatangan** | `fd7f2e9f46f9f6422df79e8189d5c35b8d2706ddf306e42f3af780f4fc588673` |
| **Algoritma Kunci Sertifikat** | RSA 2048-bit |
| **Skema Tanda Tangan APK** | APK Signature Scheme v2 |

---

## Riwayat Rilis Sebelumnya

### Versi 1.0.0 (18 Oktober 2026)

- **Versi Aplikasi**: `1.0.0`
- **Kode Versi (Version Code)**: `1`
- **ID Paket (Application ID)**: `io.github.adlnfkhrzmn.sigap`
- **Ukuran Berkas APK**: `13.288.129` bytes (~`13,29 MB`)
- **Nama Berkas Rilis**: `SIGAP.apk`
- **SHA-256 Berkas APK**: `fa4bba7ac8b7ca0712641e267dfaf2a10294a61c29d72f37c6ca5b7209868ce6`

#### Fitur Utama pada Versi 1.0.0
- **Kasir Cepat dan Manajemen Keranjang**: Pencarian produk instan, navigasi kategori, pengaturan kuantitas/catatan, validasi ketersediaan stok, dan suara bip kasir.
- **Diskon Per-Produk**: Diskon persentase maupun potongan nominal tetap Rupiah per produk.
- **Pemindai Barcode Kamera**: Pemindaian on-device menggunakan CameraX dan ZXing.
- **Katalog Produk & Kategori**: Manajemen produk, harga jual dan modal awal, serta indikator stok menipis.
- **Pembayaran Tunai & QRIS Dinamis Lokal**: Pembayaran tunai otomatis dan pembuatan QRIS dinamis lokal tanpa internet.
- **Riwayat Transaksi & Struk**: Filter periode transaksi, rincian nota, dan pencetakan Android Print Spooler / PDF / WhatsApp.
- **Laporan Penjualan Harian**: Rekapitulasi omset kotor, estimasi laba kotor, dan komparasi metode bayar.
- **Impor, Ekspor, & Pencadangan**: Ekspor katalog produk Excel/CSV dan backup/restore SQLite lokal.


