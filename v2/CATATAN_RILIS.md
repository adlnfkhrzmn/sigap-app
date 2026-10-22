# Catatan Rilis SIGAP v2.0.0 (Release Candidate)

Versi: 2.0.0  
Kode Versi (Version Code): 1  
Application ID: `io.github.adlnfkhrzmn.sigapv2`  
Nama Tampilan: SIGAP v2  
Tanggal Rilis: 22 Oktober 2026  

---

## 1. Ikhtisar Rilis

SIGAP v2.0.0 merupakan pembaruan besar aplikasi Point of Sale (POS) offline-first untuk Android. Pembaruan ini membawa kapabilitas otomasi pembayaran QRIS melalui pemantauan notifikasi pembayaran transaksi pedagang (merchant payment notifications), sekaligus mempertahankan keandalan seluruh fitur kasir, inventaris, dan laporan keuangan dari versi sebelumnya.

---

## 2. Fitur Utama & Peningkatan

### A. Otomasi Penyelesaian Pesanan QRIS (Universal Notification Detection)
- Deteksi Notifikasi Universal: Aplikasi mendeteksi dan mengurai notifikasi transaksi pembayaran secara otomatis melalui layanan listener notifikasi Android.
- Dukungan Penyedia Pembayaran: Teruji langsung pada perangkat fisik untuk Shopee Partner, GoPay Merchant, DANA Bisnis, dan ShopeePay. Notifikasi perbankan (seperti BCA) diverifikasi melalui unit test otomatis, sedangkan aplikasi merchant lain didukung melalui pengurai pola teks generik.
- Pencocokan Presisi & Cepat: Memvalidasi nominal Rupiah secara eksak dengan pesanan QRIS aktif pada jendela waktu 5 menit.
- Transaksi Atomik: Penyelesaian pesanan, pencatatan pembayaran, dan pengurangan stok produk diproses dalam satu transaksi database Room yang konsisten.
- Proteksi Duplikasi & Ambiguitas: Mencegah pemrosesan ganda untuk notifikasi yang sama serta menolak transaksi yang tidak valid atau ambigu.
- Otomasi Pembersihan Keranjang: Keranjang kasir dikosongkan secara otomatis segera setelah pesanan QRIS selesai, tanpa mengganggu keranjang transaksi baru yang sedang disusun kasir.

### B. Perbaikan Default Identitas Usaha (Fresh Install Defaults)
- Instalasi Baru yang Bersih: Instalasi baru kini tidak lagi memuat data sampel "Kedai Kopi Laju" atau "Jl. Merdeka No. 45, Bandung".
- Nilai Default Kosong: Nama usaha, alamat toko, dan nomor kontak diinisialisasi sebagai string kosong, dengan placeholder informatif "Nama Usaha" pada layar pengaturan.
- Struk Transaksi Bersih: Pemformatan struk belanja, struk retur, dan laporan shift kasir beradaptasi secara elegan tanpa memunculkan label kosong atau data tiruan.
- Preservasi Data Pengguna: Preferensi dan profil usaha yang telah disimpan sebelumnya oleh pengguna lama tetap terlindungi dan tidak tereset.

### C. Antarmuka Modern & Ramah Kasir
- Tampilan Responsif: Layout kasir beradaptasi secara dinamis untuk smartphone dan tablet (reflow 2 hingga 5 kolom).
- Palet Warna Nusantara Teal: Tampilan default mengusung tema terang (Light Mode) dengan aksen warna Nusantara Teal yang profesional dan kontras tinggi.
- Audio Kasir: Suara konfirmasi transaksi kasir yang responsif dengan kendali aktif/nonaktif di menu pengaturan.

### D. Manajemen Kasir & Finansial Lengkap
- Shift Kasir & Laci Uang: Pencatatan modal awal, penerimaan kas, pengeluaran kas (cash drawer in/out), dan rekonsiliasi uang fisik.
- Metode Pembayaran Fleksibel: Tunai, QRIS otomatis/manual, dan Split Payment (Tunai + QRIS).
- Retur Barang & Pengembalian Dana: Pencatatan retur dengan status audit yang jelas (masuk stok kembali atau barang rusak/scrap).
- Laporan & Pembukuan: Laporan penjualan harian, rekap laba/rugi, dan pencatatan biaya operasional (expenses).
- Backup & Restore Crash-Safe: Pencadangan basis data lokal SQLite dengan mekanisme restore journal durabel untuk mencegah korupsi data.

### E. Fitur Pelaporan Masalah (In-App Bug Reporting)
- Pelaporan Mandiri via Email: Formulir pelaporan masalah terintegrasi di menu Pengaturan > Tentang Aplikasi > Laporkan Bug.
- Pengiriman Transparan: Menggunakan Android Intent standar (ACTION_SENDTO dengan skema mailto:) ke adlanfakhruzzaman@gmail.com tanpa SDK pihak ketiga dan tanpa izin INTERNET tambahan.
- Perlindungan Privasi: Data keuangan, transaksi, basis data, dan isi notifikasi tidak pernah disertakan. Pengguna memiliki kendali penuh untuk meninjau dan mengirim laporan.
- Opsi Cadangan (Fallback): Menyediakan tombol salin teks ke clipboard dan pemilih aplikasi berbagi jika perangkat belum memiliki klien email default.

---

## 3. Kompatibilitas Sistem & Keamanan

- Minimum Android: Android 8.0 (API Level 26, Oreo)
- Target Android: Android 14 (API Level 34, Upside Down Cake)
- Arsitektur Perangkat: Mendukung arsitektur arm64-v8a, armeabi-v7a, x86, dan x86_64.
- Kebutuhan Izin Khusus: Izin Notification Listener diperlukan khusus untuk fitur deteksi pembayaran QRIS otomatis.
- Google Play Protect: Memuat panduan penanganan peringatan keamanan Play Protect untuk instalasi mandiri (sideload) sesuai dokumentasi pengembang resmi Google.
