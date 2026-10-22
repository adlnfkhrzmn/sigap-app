# Panduan Instalasi dan Pembaruan SIGAP v2.0.0

Dokumen ini menjelaskan tata cara instalasi baru, pembaruan aplikasi, serta panduan penanganan dialog keamanan Google Play Protect pada perangkat kasir Android.

---

## 1. PENTING: Informasi Identitas Aplikasi (Package ID)

SIGAP v2.0.0 menggunakan identitas paket resmi:
- **Application ID:** `io.github.adlnfkhrzmn.sigapv2`
- **Nama Berkas APK:** `sigap-v2.0.0-release.apk` (atau `SIGAP.apk` pada paket rilis)

### Peringatan Keamanan Data Pengguna
1. **JANGAN mencopot pemasangan (uninstall)** aplikasi SIGAP jika Anda memiliki riwayat transaksi, katalog produk, atau data kasir yang belum dicadangkan.
2. Lakukan pencadangan basis data terlebih dahulu melalui menu:
   `Pengaturan -> Data dan File -> Buat Cadangan Baru`
3. Simpan berkas cadangan ke tempat yang aman di luar perangkat (misalnya kirim ke email atau salin ke flashdisk/komputer).
4. Pembaruan versi SIGAP v2 dapat dipasang langsung di atas versi sebelumnya tanpa menghapus data lokal.

---

## 2. Verifikasi Integritas dan Checksum Berkas APK

Sebelum memasang berkas APK, pastikan berkas diperoleh dari repositori resmi pengembang dan verifikasi nilai checksum SHA-256 resmi yang tercantum pada berkas `SHA256SUMS.txt`.

### Cara Memverifikasi Checksum:
- **Windows (PowerShell):**
  ```powershell
  Get-FileHash .\sigap-v2.0.0-release.apk -Algorithm SHA256
  ```
- **Linux / macOS:**
  ```bash
  sha256sum sigap-v2.0.0-release.apk
  ```

Bandingkan hasil kalkulasi hash dengan berkas `SHA256SUMS.txt`. Jika nilai hash berbeda, jangan pasang berkas tersebut dan unduh ulang dari sumber resmi.

---

## 3. Pemasangan APK dan Penanganan Google Play Protect

### A. Prosedur Pemasangan Standar
1. Salin berkas APK ke penyimpanan perangkat Android Anda.
2. Buka berkas APK melalui aplikasi Pengelola Berkas (File Manager).
3. Jika muncul dialog izin "Instal aplikasi yang tidak dikenal", izinkan pengelola berkas Anda untuk melanjutkan pemasangan.
4. Ketuk tombol **Pasang (Install)** atau **Perbarui (Update)**.

### B. Penjelasan Faktual Peringatan Google Play Protect
Pada perangkat Android tertentu (khususnya Android 14 ke atas di beberapa wilayah), saat memasang APK dari luar toko aplikasi resmi (sideloading), sistem Google Play Protect dapat menampilkan dialog pemblokiran:

`Aplikasi diblokir untuk melindungi perangkat Anda`
*(Aplikasi meminta akses ke data sensitif yang dapat meningkatkan risiko pencurian identitas atau penipuan finansial)*

#### Mengapa Peringatan Ini Muncul?
Sesuai dokumentasi resmi panduan pengembang Google Play Protect (`https://developers.google.com/android/play-protect/warning-dev-guidance?hl=id`), Google menerapkan pemblokiran otomatis pada pemasangan aplikasi dari sumber online jika aplikasi tersebut meminta izin sensitif berisiko tinggi. SIGAP v2 menggunakan izin `android.permission.BIND_NOTIFICATION_LISTENER_SERVICE` (Akses Notifikasi) untuk membaca notifikasi pembayaran QRIS masuk. Sistem keamanan Android mendeteksi kombinasi instalasi mandiri (sideload) dan deklarasi izin listener notifikasi sebagai profil izin sensitif.

#### Panduan dan Batasan Penting bagi Pengguna:
1. **Bukan Sekadar Peringatan Pengembang Baru:** Peringatan ini bukan sekadar peringatan aplikasi belum dikenal, melainkan perlindungan proaktif sistem terhadap izin akses notifikasi.
2. **Tidak Ada Garansi Mutlak:** Status APK yang ditandatangani secara valid dan kecocokan nilai hash SHA-256 membuktikan integritas berkas dari pembuatnya, namun bukan jaminan mutlak bahwa aplikasi bebas dari segala risiko sistem.
3. **Bedakan Jenis Notifikasi:**
   - *Pemberitahuan Pindai Aplikasi Belum Dikenal:* Mengajukan pemindaian berkas ke server Google. Pengguna dapat memilih untuk memindai.
   - *Peringatan Aplikasi Berbahaya Eksplisit (Malware Specific):* Jika Play Protect menyebutkan nama ancaman tertentu atau melabeli aplikasi sebagai berbahaya, **HENTIKAN** pemasangan dan hubungi pengembang untuk klarifikasi. Jangan memaksakan instalasi secara membabi buta.
4. **Pertahankan Play Protect Tetap Aktif:** Google Play Protect adalah lapisan keamanan penting Android. Pengguna tidak disarankan mematikan Play Protect secara permanen.
5. **Jika Mematikan Sementara untuk Instalasi Terkontrol:** Apabila pengguna secara sadar memahami sumber berkas dan memilih menonaktifkan Play Protect sementara guna menyelesaikan instalasi mandiri, segera aktifkan kembali Play Protect setelah aplikasi terpasang.
6. **Batasan Pengaktifan Kembali:** Mengaktifkan kembali Play Protect tidak menjamin peringatan pemblokiran akan hilang atau bahwa aplikasi tidak akan dibatasi oleh sistem Android di masa mendatang.
7. **Jalur Pengembang:** Pengembang bertanggung jawab meninjau minimasi izin dan mengajukan banding (appeal/review) ke pihak Google Play Protect sesuai prosedur panduan resmi Google.

---

## 4. Konfigurasi Izin Akses Notifikasi (Untuk QRIS Otomatis)

Fitur penyelesaian QRIS otomatis memerlukan izin akses notifikasi agar SIGAP dapat membaca notifikasi pembayaran dari aplikasi merchant:

1. Buka aplikasi **SIGAP v2**.
2. Masuk ke menu `Pengaturan -> Akses Notifikasi Pembayaran`.
3. Ketuk tombol **Buka Pengaturan Akses Notifikasi**.
4. Pada layar sistem Android, cari dan pilih **SIGAP v2 Layanan Pemantau Notifikasi**.
5. Aktifkan sakelar dan konfirmasikan dialog sistem Android.
6. Kembali ke SIGAP v2, status akan berubah menjadi aktif (hijau).

---

## 5. Pengaturan Identitas Usaha

Pada instalasi awal, data toko dimulai dalam kondisi bersih:
1. Buka menu `Pengaturan -> Pengaturan Usaha`.
2. Masukkan nama usaha Anda yang sebenarnya (teks `Nama Usaha` sebelum diisi hanyalah placeholder).
3. Masukkan alamat fisik toko dan nomor kontak/telepon.
4. Ketuk **Simpan Pengaturan Usaha**. Data ini akan otomatis tercetak pada struk belanja pelanggan.
