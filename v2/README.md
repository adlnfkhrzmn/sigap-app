# SIGAP v2 (Point of Sale & Otomasi QRIS)

Repositori dokumentasi dan distribusi berkas rilis untuk SIGAP v2.

SIGAP v2 adalah aplikasi kasir (Point of Sale) Android offline-first yang dirancang untuk operasional usaha mikro, kecil, dan menengah (UMKM). Pembaruan v2 menghadirkan kapabilitas deteksi dan penyelesaian transaksi QRIS otomatis berbasis notifikasi pembayaran merchant, perbaikan identitas usaha instalasi baru, pembersihan keranjang otomatis, serta fitur pelaporan bug mandiri via email.

---

## Status Distribusi & Unduhan

| Parameter | Informasi Rilis |
| :--- | :--- |
| **Versi Aplikasi** | 2.0.0 |
| **Kode Versi (Version Code)** | 1 |
| **Application ID** | `io.github.adlnfkhrzmn.sigapv2` |
| **Target Sistem** | Android 8.0 (API Level 26) hingga Android 14 (API Level 34) |
| **Status Publikasi** | **Tahap Pengujian Akhir & Persiapan Rilis (Release Candidate)** |
| **Tautan Unduhan** | Menunggu publikasi resmi di GitHub Releases (Tautan publik belum diaktifkan) |

> **Catatan Pengunduhan:** Berkas APK pada repositori ini disiapkan untuk tahap staging pra-publikasi. Tautan unduhan publik resmi akan diaktifkan segera setelah rilis GitHub v2.0.0 dipublikasikan secara resmi oleh pengembang.

---

## Fitur Utama SIGAP v2

1. **Penyelesaian Pesanan QRIS Otomatis**
   - Mendeteksi notifikasi pembayaran masuk dari aplikasi penyedia pembayaran (ShopeePay, Shopee Partner, DANA Bisnis, GoPay Merchant, dan notifikasi merchant lainnya).
   - Memvalidasi nominal secara presisi dengan pesanan QRIS aktif pada jendela toleransi waktu 5 menit.
   - Mengosongkan keranjang kasir secara otomatis setelah transaksi selesai sukses.
   - Pemrosesan berjalan 100% lokal di perangkat tanpa server perantara.

2. **Manajemen Kasir & Shift Lengkap**
   - Buka dan tutup shift kasir dengan pencatatan modal awal dan rekonsiliasi kas fisik.
   - Pencatatan arus kas masuk dan kas keluar (cash in / cash out).
   - Pembayaran tunai, QRIS dinamis, dan pembayaran terpisah (split payment).

3. **Katalog Produk & Inventaris**
   - Manajemen katalog produk, varian, kategori, harga modal, dan harga jual.
   - Pemantauan stok menipis dan riwayat mutasi stok.

4. **Retur, Pengeluaran & Laporan Keuangan**
   - Retur produk per item (masuk stok kembali atau scrap/rusak) dengan pengembalian dana proporsional.
   - Pencatatan biaya operasional toko.
   - Laporan ringkasan penjualan harian dan rekap laba/rugi bersih.

5. **Pelaporan Masalah Mandiri (In-App Bug Reporting)**
   - Akses mudah melalui menu Pengaturan > Tentang Aplikasi > Laporkan Bug.
   - Menyiapkan draf email terstruktur ke `adlanfakhruzzaman@gmail.com`.
   - Tidak menggunakan izin internet tambahan dan tidak menyertakan data keuangan privat.

---

## Verifikasi Integritas Berkas (SHA-256)

Sebelum memasang berkas APK, verifikasi keaslian dan integritas berkas menggunakan nilai hash resmi pada berkas `SHA256SUMS.txt`:

```powershell
Get-FileHash .\SIGAP.apk -Algorithm SHA256
```

Pastikan nilai hash yang dihasilkan cocok persis dengan nilai checksum resmi yang dipublikasikan.

---

## Panduan Instalasi & Google Play Protect

Pemasangan berkas APK di luar Google Play Store (sideload) dapat memicu dialog keamanan Android atau Google Play Protect. Hal ini wajar terjadi karena aplikasi menggunakan izin sensitif `NOTIFICATION_LISTENER` untuk membaca notifikasi pembayaran merchant secara lokal.

- Ikuti panduan langkah demi langkah pada [PANDUAN_INSTALASI_DAN_PEMBARUAN.md](PANDUAN_INSTALASI_DAN_PEMBARUAN.md).
- Tetap aktifkan Google Play Protect setelah proses verifikasi dan pemasangan selesai.

---

## Indeks Dokumentasi Resmi v2

- [Panduan Pengguna Lengkap](PANDUAN_PENGGUNA.md): Tata cara operasional kasir, inventaris, shift, transaksi QRIS, dan pelaporan bug.
- [Panduan Instalasi & Pembaruan](PANDUAN_INSTALASI_DAN_PEMBARUAN.md): Langkah instalasi mandiri, pembaruan aplikasi, dan penanganan Play Protect.
- [Kebijakan Privasi](KEBIJAKAN_PRIVASI.md): Komitmen perlindungan data, cakupan pembacaan notifikasi lokal, dan transparansi laporan bug.
- [Kompatibilitas & Izin Sistem](KOMPATIBILITAS_DAN_IZIN.md): Rincian izin Android, daftar penyedia pembayaran yang teruji, dan konfigurasi baterai perangkat.
- [Catatan Rilis v2.0.0](CATATAN_RILIS.md): Rincian teknis pembaruan dan perubahan pada rilis v2.0.0.
- [Alur Demonstrasi QRIS](DEMO.md): Penjelasan alur verifikasi langsung pada perangkat fisik dan pedoman redaksi privasi.
