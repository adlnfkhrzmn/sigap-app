<p align="center">
  <img src="assets/logo.png" alt="Ikon SIGAP POS" width="160">
</p>

# SIGAP POS

**SIGAP** adalah aplikasi kasir (*point-of-sale*) Android berbasis *offline-first* yang dirancang untuk membantu pelaku Usaha Mikro, Kecil, dan Menengah (UMKM) mengelola transaksi penjualan, memantau persediaan barang, dan mencatat arus kas usaha secara praktis, cepat, dan mandiri.

Aplikasi ini ditujukan untuk usaha mandiri seperti warung kopi, kedai minuman, kios makanan, kedai makan, dan toko kelontong. Seluruh catatan transaksi dan data katalog produk disimpan secara lokal di perangkat Android Anda, sehingga alur kerja operasional kasir inti dapat terus digunakan secara penuh tanpa memerlukan koneksi internet.

---

## Unduh Berkas Instalasi (APK)

Aplikasi SIGAP didistribusikan secara mandiri melalui berkas instalasi APK resmi:

| Informasi Rilis | Rincian |
| :--- | :--- |
| **Versi Aplikasi** | `1.0.0` (Version Code: `1`) |
| **Nama Berkas** | `SIGAP.apk` |
| **Ukuran Berkas** | `13.288.129` bytes (~`13,29 MB`) |
| **Persyaratan Sistem** | Android 8.0 (API level 26) atau versi yang lebih baru (Target SDK: API level 34) |
| **Status Distribusi** | Rilis resmi v1.0.0 tersedia melalui GitHub Releases |

### Tautan Unduhan Resmi

**[DOWNLOAD APK SIGAP](https://github.com/adlnfkhrzmn/sigap-app/releases/latest/download/SIGAP.apk)**

> [!NOTE]
> **Status Tautan Unduhan**: Rilis resmi SIGAP POS v1.0.0 sudah tersedia. Tautan unduhan di atas mengarah langsung ke berkas `SIGAP.apk` dari rilis resmi terbaru. Jika berkas tidak dapat diunduh, buka halaman [Releases](https://github.com/adlnfkhrzmn/sigap-app/releases) untuk memeriksa ketersediaan aset.

Untuk panduan lengkap mengenai langkah-langkah pengunduhan, perizinan instalasi aplikasi dari luar toko aplikasi, serta penanganan dialog Google Play Protect, silakan baca:
**[Panduan Instalasi APK Android](INSTALASI_APK.md)**

---

## Verifikasi Integritas Berkas (SHA-256)

Demi keamanan perangkat Anda, disarankan untuk memverifikasi nilai *checksum* SHA-256 berkas yang telah diunduh sebelum memasangnya:

| Parameter | Nilai Resmi |
| :--- | :--- |
| **SHA-256 Berkas APK** | `fa4bba7ac8b7ca0712641e267dfaf2a10294a61c29d72f37c6ca5b7209868ce6` |
| **SHA-256 Sertifikat Rilis** | `fd7f2e9f46f9f6422df79e8189d5c35b8d2706ddf306e42f3af780f4fc588673` |

### Cara Memeriksa Checksum Mandiri:
- **Windows (PowerShell)**:
  ```powershell
  Get-FileHash SIGAP.apk -Algorithm SHA256
  ```
- **Linux / macOS / Android Termux**:
  ```bash
  sha256sum SIGAP.apk
  ```

Pastikan nilai hash heksadesimal yang dihasilkan sama persis dengan tabel di atas. Berkas `SHA256SUMS.txt` juga disertakan pada repositori ini untuk keperluan verifikasi otomatis.

---

## Fitur Utama

- **Kasir Cepat & Manajemen Keranjang**: Pencarian nama/SKU produk instan secara real-time, filter kategori dinamis, penyesuaian kuantitas pesanan, catatan khusus per item, pembatasan otomatis sesuai stok fisik, dan konfirmasi audio bip kasir opsional.
- **Diskon Per-Produk Fleksibel**: Pilihan diskon berbasis persentase (0%–100%) maupun nominal Rupiah tetap (Rp) per item, dilengkapi perhitungan transparan pada nota.
- **Pemindai Barcode & SKU Kamera**: Pemindaian barcode produk fisik menggunakan kamera belakang perangkat secara langsung di perangkat (on-device) serta opsi pengetikan nomor barcode manual.
- **Katalog Produk & Kategori Dinamis**: Manajemen data produk lengkap (harga jual, harga modal opsional, stok awal, batas peringatan stok menipis, foto/ikon) dan pengelolaan kategori dengan relokasi produk aman.
- **Pembayaran Tunai & QRIS Dinamis Lokal**: Pembayaran tunai dengan hitung otomatis kembalian serta pembuatan kode QRIS dinamis langsung di perangkat dari gambar QRIS toko merchant. Dilengkapi penguncian pesanan pending agar stok tidak digunakan ganda.
- **Riwayat Transaksi & Cetak Struk**: Penyaringan transaksi berdasarkan periode (Hari Ini, Kemarin, 7 Hari Terakhir, Custom), cetak nota melalui Android Print Spooler sistem (printer jaringan atau simpan PDF), dan berbagi teks nota ke WhatsApp.
- **Laporan Penjualan Harian**: Rekapitulasi omset kotor, estimasi laba kotor, total produk terjual, perbandingan transaksi Tunai vs QRIS, dan daftar produk terlaris.
- **Ekspor, Impor, dan Pencadangan Data**: Ekspor-impor katalog produk via Excel (.xlsx) dan CSV (.csv), ekspor riwayat penjualan, serta pencadangan dan pemulihan database SQLite lokal melalui Storage Access Framework (SAF).
- **Pengaturan Usaha & Tema**: Kustomisasi identitas toko (nama, alamat, kontak, catatan penutup struk) dan tema tampilan (Terang, Gelap, Sistem) dengan 4 pilihan palet warna aksen.

---

## Catatan dan Batasan Operasional

1. **Perangkat Kasir Mandiri (*Single-Store*)**:
   Dirancang untuk satu toko fisik dengan satu perangkat kasir mandiri (*offline-first*). Aplikasi belum mendukung sinkronisasi otomatis antar-perangkat berbasis cloud multi-cabang.
2. **Verifikasi Pembayaran QRIS Bersifat Manual**:
   SIGAP menghasilkan visual kode QR dinamis secara mandiri di perangkat tanpa integrasi payment gateway pihak ketiga dan tidak menerima webhook perbankan otomatis. Kasir **wajib memverifikasi penerimaan dana secara manual** melalui aplikasi merchant (seperti GoPay Merchant, Shopee Partner, atau mutasi bank) sebelum menyelesaikan transaksi.
3. **Pencetakan Struk Thermal**:
   Pencetakan nota mengandalkan sistem Android Print Spooler (printer sistem atau simpan PDF) serta pembagian teks ke WhatsApp. Integrasi langsung melalui driver Bluetooth printer POS ESC/POS belum tersedia.

---

## Keamanan dan Penyimpanan Data

- **Penyimpanan Lokal (Offline-First)**: Seluruh data katalog produk, stok barang, dan catatan transaksi disimpan secara lokal di dalam basis data perangkat Android kasir. Alur kerja operasional kasir inti dirancang untuk berfungsi penuh tanpa koneksi internet.
- **Izin Akses Internet**: Berkas instalasi resmi SIGAP tidak meminta izin Android `INTERNET` (`android.permission.INTERNET`) pada manifest aplikasi.
- **Peringatan Penghapusan Aplikasi**: Mengingat basis data disimpan secara lokal pada perangkat, mencopot pemasangan (*uninstall*) aplikasi SIGAP dapat menghapus seluruh data usaha yang tersimpan. Pengguna disarankan untuk melakukan pencadangan data secara berkala melalui menu Pengaturan.
- **Sumber Unduhan Resmi**: Unduh berkas APK hanya dari repositori resmi `https://github.com/adlnfkhrzmn/sigap-app`. Jangan mengunduh berkas instalasi dari situs pihak ketiga yang tidak terafiliasi.
- **Pemasangan Mandiri (*Sideloading*)**: Sistem operasi Android menampilkan dialog konfirmasi keamanan saat memasang aplikasi dari luar Google Play Store. Ikuti panduan instalasi untuk memverifikasi keaslian berkas sebelum melanjutkan pemasangan.
