# Catatan Kompatibilitas dan Perizinan Aplikasi SIGAP v2.0.0

Dokumen ini memuat rincian persyaratan sistem, model perizinan aplikasi, penanganan keamanan Google Play Protect, serta batasan kapabilitas platform Android pada SIGAP v2.

---

## 1. Persyaratan Sistem & Perangkat Keras

- **Sistem Operasi Minimum:** Android 8.0 (API Level 26, Oreo)
- **Sistem Operasi Target:** Android 14 (API Level 34, Upside Down Cake)
- **RAM:** Minimal 2 GB (disarankan 3 GB atau lebih untuk kelancaran multi-tasking kasir)
- **Penyimpanan:** Minimal 100 MB ruang kosong untuk aplikasi dan basis data transaksi lokal
- **Kamera (Opsional):** Digunakan untuk pemindaian barcode/SKU produk fisik langsung dari perangkat
- **Bluetooth:** Digunakan untuk koneksi printer kasir thermal Bluetooth

---

## 2. Model Perizinan Android (Least Privilege)

Aplikasi SIGAP v2 dirancang dengan prinsip minimasi izin untuk menjaga privasi pengguna:

### A. Izin Akses Notifikasi (`android.permission.BIND_NOTIFICATION_LISTENER_SERVICE`)
- **Kategori:** Layanan Akses Khusus Perangkat (Special App Access).
- **Tujuan:** Membaca judul dan teks notifikasi pembayaran yang masuk ke bilah status Android agar sistem dapat mencocokkan nominal transaksi dengan pesanan QRIS aktif.
- **Pemrosesan Lokal:** Teks notifikasi diuraikan secara lokal di perangkat tanpa koneksi ke server luar mana pun.
- **Batasan Akses:** SIGAP tidak memiliki akses ke akun perbankan, saldo rekening, maupun riwayat transaksi lengkap pada aplikasi bank atau dompet digital Anda.
- **Implikasi Google Play Protect:** Google Play Protect pada Android 14 ke atas secara proaktif membatasi instalasi mandiri (sideload) berkas APK yang meminta izin sensitif ini, memunculkan dialog `Aplikasi diblokir untuk melindungi perangkat Anda`. Rujukan panduan resmi: `https://developers.google.com/android/play-protect/warning-dev-guidance?hl=id`.

### B. Izin Kamera (`android.permission.CAMERA`)
- **Kategori:** Izin Waktu Proses (Runtime Permission).
- **Penggunaan:** Pemindaian barcode produk pada modul katalog dan kasir.
- **Sifat:** Dideklarasikan dengan atribut `android:required="false"`, sehingga perangkat tanpa kamera tetap dapat menjalankan seluruh fitur kasir dan QRIS secara normal.

### C. Ketiadaan Izin Internet
- SIGAP v2 **tidak mendeklarasikan** izin `android.permission.INTERNET` di dalam berkas manifest.
- Fitur pelaporan bug (`Laporkan Bug`) memanfaatkan komponen sistem Android `Intent.ACTION_SENDTO` dengan skema `mailto:`, sehingga proses transmisi email dilakukan sepenuhnya oleh aplikasi email pihak ketiga yang telah dipilih dan disetujui pengguna.

---

## 3. Kompatibilitas Penyedia Pembayaran QRIS

### A. Teruji Langsung pada Perangkat Fisik
Pengujian alur transaksi dan penerimaan notifikasi pada perangkat fisik Android telah dikonfirmasi untuk aplikasi merchant berikut:
- **Shopee Partner:** Notifikasi transaksi pembayaran pedagang diterima.
- **GoPay Merchant:** Notifikasi pembayaran QRIS statis merchant diterima.
- **DANA Bisnis:** Notifikasi transaksi pembayaran masuk merchant.
- **ShopeePay:** Notifikasi pembayaran masuk yang teruji pada iterasi pengujian alur otomasi sebelumnya.

### B. Cakupan Pengujian Otomatis (Fixture & Unit Test)
Format notifikasi berikut tercakup dalam rangkaian pengujian unit otomatis kode sumber menggunakan data sampel (fixture), namun belum melalui pengujian transaksi fisik langsung oleh pengguna:
- **BCA (Bank Central Asia):** Format teks notifikasi penerimaan dana/QRIS masuk diverifikasi secara terprogram dalam unit test parser.

### C. Penyedia Pembayaran Lain (Parser Generik)
Aplikasi menyediakan mesin pengurai generik (`UniversalPaymentParser`) yang mendeteksi pola mata uang Rupiah (`Rp`, `IDR`, angka nominal) dan kata kunci keberhasilan transaksi (`diterima`, `berhasil`, `sukses`, `masuk`) dari aplikasi bank atau dompet digital lain (seperti SeaBank, Livin' by Mandiri, OVO, dsb.).

**Peringatan & Keamanan:**
1. Membaca notifikasi penerimaan dana tidak serta-merta membuktikan bahwa pembayaran tersebut milik pesanan kasir tertentu. Sistem hanya memproses penyelesaian otomatis jika nominal dan waktu notifikasi cocok secara unik dengan satu pesanan aktif dalam toleransi waktu 5 menit.
2. Fitur otomatisasi tidak dijamin berfungsi pada seluruh aplikasi bank atau dompet digital di Indonesia, terutama jika penyedia tidak menampilkan nominal pada teks notifikasi atau mematikan fitur notifikasi sistem Android. Jika notifikasi tidak terdeteksi, kasir tetap dapat menyelesaikan transaksi secara manual melalui tombol **Pesanan Selesai**.

---

## 4. Manajemen Baterai Produsen Perangkat (OEM Battery Optimization)

Beberapa antarmuka kustom Android (seperti MIUI/HyperOS Xiaomi, ColorOS Oppo, FuntouchOS Vivo, dan One UI Samsung) memiliki sistem manajemen daya agresif yang dapat menonaktifkan layanan listener latar belakang:

- **Saran Konfigurasi:** Masuk ke menu `Pengaturan Sistem Android -> Aplikasi -> Kelola Aplikasi -> SIGAP v2`.
- Pilih menu **Penghemat Baterai** dan ubah status menjadi **Tidak Ada Pembatasan (No Restrictions)**.
- Aktifkan opsi **Mulai Otomatis (Auto-start)** jika tersedia.

---

## 5. Tata Cara Pencabutan Izin

Pengguna memiliki hak penuh untuk mencabut izin kapan saja:
- **Akses Notifikasi:** Buka menu `Pengaturan Sistem Android -> Aplikasi -> Akses Khusus Aplikasi -> Akses Notifikasi`, lalu nonaktifkan sakelar untuk SIGAP v2.
- **Kamera:** Buka `Pengaturan Sistem Android -> Aplikasi -> SIGAP v2 -> Izin`, lalu nonaktifkan izin Kamera.
