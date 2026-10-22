# Kebijakan Privasi SIGAP v2

Dokumen ini menjelaskan bagaimana SIGAP v2 mengelola, menyimpan, dan memproses data operasional toko, izin perangkat Android, serta fitur laporan kendala pengguna.

Pembaruan terakhir: Oktober 2026

---

## 1. Prinsip Penyimpanan Data Lokal (Offline-First)

SIGAP v2 dirancang sebagai aplikasi kasir (Point of Sale) yang bekerja secara luring (offline):

- **Data Operasional Toko:** Data katalog produk, stok inventaris, kategori, transaksi penjualan, catatan kas masuk/keluar, dan riwayat shift disimpan secara lokal di perangkat Anda menggunakan basis data SQLite/Room.
- **Tanpa Server Eksternal / Cloud:** Aplikasi tidak mengunggah data katalog maupun transaksi harian Anda ke peladen eksternal atau layanan analitik pihak ketiga secara otomatis.
- **Keterbatasan Keamanan Basis Data Lokal:** Berkas basis data tersimpan di penyimpanan internal aplikasi perangkat Android Anda. Aplikasi ini tidak menerapkan enkripsi kustom tingkat basis data internal di luar perlindungan sandbox bawaan sistem operasi Android.

---

## 2. Penggunaan Izin Akses Notifikasi (Notification Listener)

SIGAP v2 meminta izin khusus `Akses Notifikasi` (`android.permission.BIND_NOTIFICATION_LISTENER_SERVICE`) untuk mendukung fitur penyelesaian otomatis pesanan QRIS:

- **Tujuan Penggunaan:** Layanan `SigapNotificationListenerService` memantau teks notifikasi pembayaran masuk (seperti judul dan isi notifikasi) yang dikirimkan oleh aplikasi perbankan atau dompet digital ke perangkat kasir saat transaksi terjadi.
- **Pemrosesan di Dalam Perangkat:** Teks notifikasi diuraikan secara lokal untuk mengekstrak nominal transaksi dan indikator keberhasilan, kemudian dicocokkan dengan pesanan QRIS yang sedang aktif di kasir.
- **Ruang Lingkup dan Batasan:** SIGAP **bukan** merupakan gerbang pembayaran resmi dan **tidak** memiliki akses langsung ke saldo rekening, basis data transaksi lengkap, maupun kredensial perbankan penyedia pembayaran Anda. Aplikasi hanya membaca teks notifikasi yang ditampilkan oleh sistem Android.
- **Dukungan Penyedia Pembayaran:** Pengenalan notifikasi telah diverifikasi secara fisik pada perangkat langsung untuk aplikasi merchant Shopee Partner, GoPay Merchant, DANA Bisnis, dan ShopeePay. Notifikasi perbankan seperti BCA diuji melalui pengujian simulasi otomatis. Format notifikasi dari penyedia lain diproses menggunakan pengurai pola teks generik dan tidak menjamin kompatibilitas untuk seluruh format notifikasi aplikasi perbankan atau dompet digital.
- **Pencabutan Izin:** Anda dapat menonaktifkan izin ini kapan saja melalui menu `Pengaturan > Akses Notifikasi Pembayaran` atau langsung melalui menu `Pengaturan Sistem Android > Aplikasi > Akses Notifikasi Khusus`.

---

## 3. Fitur Laporkan Kendala / Bug (Pelaporan via Email)

SIGAP v2 menyediakan formulir `Laporkan Kendala` pada menu `Pengaturan` untuk memudahkan pengguna menyampaikan kendala teknis kepada pengembang (`adlanfakhruzzaman@gmail.com`):

### A. Pengiriman Dilakukan Secara Sadar oleh Pengguna
Aplikasi **tidak** mengirim laporan secara diam-diam di latar belakang. Saat Anda menekan tombol "Kirim Email", aplikasi akan memicu aplikasi email yang terpasang di perangkat Anda (menggunakan intent `ACTION_SENDTO` dengan skema `mailto:`) dan mengisi draf email dengan teks laporan. Anda memiliki kendali penuh untuk meninjau, menyunting, atau membatalkan pengiriman draf sebelum menekan tombol kirim di aplikasi email Anda.

### B. Informasi yang Disertakan
Jika Anda memilih untuk mengaktifkan opsi "Sertakan Informasi Teknis Perangkat", draf email akan menyertakan data teknis terbatas:
- Versi aplikasi SIGAP dan kode rilis (misal: v2.0.0, kode 1).
- Versi sistem operasi Android dan level API.
- Manufaktur dan model perangkat (misal: Xiaomi Redmi Note 12).
- Waktu pembuatan laporan.

### C. Informasi yang Dikecualikan Secara Tegas
Sistem pelaporan kendala SIGAP **tidak pernah** secara otomatis menyertakan:
- Basis data produk, riwayat transaksi, maupun catatan pelanggan.
- Laporan keuangan, omzet, dan saldo kas.
- Nomor rekening bank atau identitas finansial.
- Teks lengkap notifikasi sistem pribadi Anda.
- Kata sandi, token otentikasi, atau berkas backup basis data.

### D. Panduan Kolom Bebas
Pengguna dianjurkan untuk tidak menuliskan informasi rahasia perbankan, PIN, kata sandi, atau data pribadi pelanggan pada kolom isian bebas (ringkasan masalah, aktivitas, atau catatan tambahan).

---

## 4. Cadangkan Data (Backup), Pemulihan (Restore), dan Risiko Pencopotan Aplikasi

- **Berkas Cadangan (Backup):** Fitur pencadangan data menghasilkan berkas arsip lokal yang dapat Anda simpan ke folder perangkat atau dipindahkan ke media penyimpanan lain. Berkas cadangan ini memuat seluruh data produk, transaksi, dan riwayat operasional toko Anda. Harap simpan berkas cadangan di tempat yang aman.
- **Risiko Uninstall:** Mencopot (uninstall) aplikasi SIGAP dari perangkat Android Anda akan menghapus direktori internal aplikasi beserta seluruh data transaksi dan inventaris yang belum dicadangkan. Pastikan Anda selalu membuat berkas cadangan sebelum melakukan instalasi ulang atau pembersihan penyimpanan perangkat.

---

## 5. Kebutuhan Minimum Sistem

SIGAP v2 mendukung perangkat dengan sistem operasi **Android 8.0 (Oreo / API Level 26)** atau versi yang lebih baru.
