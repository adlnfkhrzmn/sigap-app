# Catatan Rilis SIGAP POS - Versi 1.0.0

Dokumen ini memuat catatan rilis resmi untuk peluncuran perdana aplikasi kasir **SIGAP POS** (*point-of-sale*) Android versi 1.0.0.

---

## Ringkasan Rilis

- **Versi Aplikasi**: `1.0.0`
- **Kode Versi (Version Code)**: `1`
- **ID Paket (Application ID)**: `io.github.adlnfkhrzmn.sigap`
- **Persyaratan Sistem**: Minimum Android 8.0 (API level 26 / Oreo) atau versi yang lebih baru
- **Target SDK**: Android 14 (API level 34)
- **Ukuran Berkas APK**: `13.288.129` bytes (~`13,29 MB`)
- **Nama Berkas Rilis**: `SIGAP.apk`

---

## Fitur Utama pada Versi 1.0.0

### 1. Kasir Cepat dan Manajemen Keranjang
- **Pencarian Produk Instan**: Memilih dan memasukkan produk ke keranjang kasir secara cepat dengan pencarian nama produk atau kode SKU secara real-time.
- **Navigasi Kategori Dinamis**: Mengelompokkan dan memfilter katalog produk di kasir menggunakan tombol *chip* kategori dengan pengguliran horizontal dan filter "Semua".
- **Pengaturan Kuantitas dan Catatan**: Menyesuaikan jumlah item pesanan dengan tombol kuantitas (+/-) serta menambahkan catatan pesanan khusus per item.
- **Validasi Ketersediaan Stok**: Membatasi penambahan jumlah belanja agar tidak melampaui sisa stok barang dan memberi penanda visual apabila stok habis.
- **Suara Bip Kasir**: Menghasilkan konfirmasi audio singkat setiap kali produk berhasil dimasukkan ke keranjang kasir (dapat diaktifkan atau dinonaktifkan melalui menu Pengaturan).

### 2. Diskon Per-Produk
- **Dua Pilihan Jenis Diskon**: Mendukung penerapan diskon persentase (0%–100%) maupun potongan nominal tetap Rupiah (Rp) pada setiap item belanja.
- **Kalkulasi Transparan**: Menghitung potongan harga per unit secara presisi dengan pembulatan standar, menampilkan harga asli tercoret, harga setelah diskon, dan total penghematan pada rincian transaksi.

### 3. Pemindai Barcode dan SKU Kamera
- **Pemindaian On-Device**: Mengintegrasikan kamera belakang perangkat untuk memindai barcode fisik produk secara langsung tanpa memerlukan koneksi internet.
- **Pencocokan Katalog Lokal**: Mencocokkan barcode hasil pemindaian langsung ke database produk di perangkat.
- **Penanganan Barcode Baru**: Jika barcode belum terdaftar di katalog toko, aplikasi menyediakan opsi untuk membuka formulir pendaftaran produk baru dengan kode barcode terisi otomatis tanpa melakukan penyimpanan otomatis sebelum pengguna mengonfirmasi seluruh data produk.
- **Input Manual**: Menyediakan opsi pengetikan nomor barcode secara manual apabila perangkat tidak memiliki kamera atau barcode fisik mengalami kerusakan.

### 4. Katalog Produk dan Pengelolaan Kategori
- **Manajemen Katalog Lengkap**: Menambah, memperbarui, dan menghapus data produk (nama, kategori, harga jual, harga modal opsional, stok awal, batas peringatan stok menipis, nomor SKU/barcode, dan ikon atau foto produk).
- **Pengelolaan Kategori**: Menambah kategori baru, mengubah nama kategori, serta menghapus kategori dengan opsi memindahkan produk-produk terkait ke kategori lain secara aman.
- **Indikator Stok**: Penanda visual informatif untuk stok barang yang menipis dan stok habis.

### 5. Pembayaran Tunai dan QRIS Dinamis Lokal
- **Pembayaran Tunai**: Menghitung total belanja, nominal pembayaran, dan uang kembalian secara otomatis, dilengkapi tombol cepat pecahan uang pas dan pecahan nominal Rupiah umum.
- **QRIS Dinamis Lokal**: Menghasilkan kode QR dinamis berisi nominal belanja sesuai isi keranjang yang dibuat secara lokal di perangkat dari gambar QRIS statis merchant yang diimpor dari galeri.
- **Penguncian Pesanan (*Pending QRIS*)**: Mengunci pesanan aktif selama kasir menunggu pelanggan menyelesaikan pembayaran agar stok produk tidak digunakan ganda pada pesanan lain.

### 6. Riwayat Transaksi dan Struk Penjualan
- **Penyaringan Riwayat Transaksi**: Menyaring daftar riwayat transaksi berdasarkan periode waktu: Hari Ini, Kemarin, 7 Hari Terakhir, atau rentang tanggal khusus (Custom) melalui dialog kalender.
- **Rincian Transaksi Lengkap**: Menampilkan informasi nota, waktu transaksi, kasir, rincian produk, potongan diskon, subtotal, total akhir, nominal bayar, dan uang kembalian.
- **Pencetakan dan Pembagian Struk**: Mencetak nota melalui sistem cetak Android (*Android Print Spooler* ke printer terhubung atau simpan sebagai dokumen PDF) serta membagikan ringkasan nota dalam format teks ke WhatsApp atau aplikasi lain.

### 7. Laporan Penjualan Harian
- **Ringkasan Indikator Usaha**: Menampilkan total omset penjualan kotor, estimasi laba kotor (berdasarkan selisih harga jual dan harga modal yang diisi), jumlah transaksi berhasil, dan total produk terjual.
- **Komparasi Metode Bayar**: Rekapitulasi perbandingan transaksi Tunai dibandingkan transaksi QRIS serta daftar produk terlaris.

### 8. Impor, Ekspor, dan Pencadangan Data
- **Ekspor dan Impor Katalog Produk**: Mendukung ekspor dan impor katalog produk beserta kategorinya menggunakan format berkas Excel (.xlsx) dan CSV (.csv).
- **Ekspor Riwayat Penjualan**: Mengekspor riwayat transaksi penjualan ke dalam format berkas Excel (.xlsx) atau arsip ZIP berisi berkas CSV.
- **Pencadangan dan Pemulihan Mandiri**: Menyediakan fitur cadangan (backup) dan pemulihan (restore) database SQLite lokal ke penyimpanan perangkat menggunakan Android Storage Access Framework (SAF).

### 9. Pengaturan Usaha dan Tampilan
- **Identitas Usaha**: Pengaturan nama toko, alamat gerai, nomor telepon/WhatsApp, dan catatan penutup nota belanja.
- **Personalisasi Tampilan**: Dukungan tema Terang (Light), Gelap (Dark), atau Mengikuti Sistem perangkat, serta pilihan palet warna aksen kasir (Teal, Navy, Olive, Slate).

---

## Batasan Operasional dan Arsitektur Data

1. **Penyimpanan Lokal dan Operasional Offline**:
   Catatan transaksi dan katalog produk disimpan secara lokal di perangkat Android. Alur kasir inti beroperasi secara *offline-first*. Aplikasi tidak meminta izin jaringan `android.permission.INTERNET` pada manifest aplikasi.
2. **Perangkat Kasir Mandiri (*Single-Store*)**:
   Dirancang untuk satu toko fisik dengan satu perangkat kasir mandiri. Sinkronisasi multi-cabang berbasis cloud belum tersedia pada rilis ini.
3. **Verifikasi Pembayaran QRIS Bersifat Manual**:
   SIGAP menghasilkan visual kode QR dinamis secara mandiri di perangkat tanpa integrasi *payment gateway* perbankan pihak ketiga. SIGAP tidak memotong saldo secara otomatis dan tidak menerima *webhook* perbankan. Kasir **wajib memverifikasi penerimaan dana secara manual** melalui aplikasi merchant (seperti GoPay Merchant, Shopee Partner, atau mutasi bank) sebelum menyelesaikan transaksi.
4. **Pencetakan Struk Thermal**:
   Pencetakan nota saat ini mengandalkan sistem Android Print Spooler atau pembagian teks struk. Integrasi langsung melalui driver Bluetooth printer POS ESC/POS belum tersedia.
5. **Perlindungan Data Lokal**:
   Pencopotan (*uninstall*) aplikasi dari perangkat dapat menghapus database lokal transaksi. Pengguna dianjurkan mencadangkan data berkala via menu Pengaturan sebelum melakukan tindakan pemeliharaan perangkat.

---

## Integritas Berkas dan Verifikasi Keamanan

Sebelum memasang berkas instalasi pada perangkat Android, pastikan integritas berkas telah diverifikasi:

| Parameter | Nilai Resmi |
| :--- | :--- |
| **Nama Berkas Rilis** | `SIGAP.apk` |
| **SHA-256 Berkas APK** | `fa4bba7ac8b7ca0712641e267dfaf2a10294a61c29d72f37c6ca5b7209868ce6` |
| **SHA-256 Sertifikat Penandatangan** | `fd7f2e9f46f9f6422df79e8189d5c35b8d2706ddf306e42f3af780f4fc588673` |
| **Algoritma Kunci Sertifikat** | RSA 2048-bit |
| **Skema Tanda Tangan APK** | APK Signature Scheme v2 |
