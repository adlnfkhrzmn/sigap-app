# Panduan Instalasi Berkas APK SIGAP

Panduan ini disusun untuk membantu pengguna dan mitra UMKM dalam memasang aplikasi kasir **SIGAP POS** pada perangkat ponsel atau tablet Android melalui berkas instalasi APK (*Android Package Kit*).

---

## 1. Sebelum Memulai Instalasi

Harap perhatikan informasi identitas resmi aplikasi sebelum mengunduh dan melakukan instalasi:

### Identitas Resmi Aplikasi
- **Nama Aplikasi**: SIGAP
- **Nama Paket (Application ID)**: `io.github.adlnfkhrzmn.sigap`
- **Versi Rilis**: `1.0.0` (Version Code: `1`)
- **Nama Berkas Instalasi**: `SIGAP.apk`
- **Persyaratan Sistem**: Android 8.0 (API level 26 / Oreo) atau versi yang lebih baru (Target SDK: API level 34)
- **Ukuran Berkas**: Sekitar `13,29 MB` (`13.288.129` bytes)

### Sumber Unduhan Resmi
Unduh berkas instalasi hanya dari saluran resmi distribusi SIGAP:
- **Repositori Distribusi**: `https://github.com/adlnfkhrzmn/sigap-app`
- **Tautan Unduhan Langsung**: **[Unduh SIGAP.apk](https://github.com/adlnfkhrzmn/sigap-app/releases/latest/download/SIGAP.apk)**

> [!NOTE]
> **Status Tautan Unduhan**: Setelah rilis resmi diterbitkan, tautan ini akan mengarah ke berkas `SIGAP.apk` dari rilis resmi terbaru. Jika berkas belum tersedia, periksa halaman [Releases](https://github.com/adlnfkhrzmn/sigap-app/releases).

> [!IMPORTANT]
> Jangan pernah mengunduh berkas APK SIGAP dari situs web pihak ketiga yang tidak dikenal, tautan pendek acak di media sosial, atau pesan grup obrolan yang tidak terpercaya. Berkas dari sumber tidak resmi berisiko dimanipulasi atau disisipi program berbahaya.

---

## 2. Langkah-Langkah Unduh dan Instalasi

Berikut adalah langkah-langkah standar pemasangan APK SIGAP di perangkat Android:

### Langkah 1: Unduh Berkas APK
1. Buka peramban (*browser*) bawaan ponsel (seperti Google Chrome) dan akses halaman rilis resmi SIGAP.
2. Unduh berkas `SIGAP.apk` melalui tautan unduhan resmi.
3. Jika peramban memunculkan pesan peringatan *"File ini mungkin berbahaya, tetap ingin mengunduh?"* (*File might be harmful*), periksa kembali alamat sumber unduhan. Jika sudah sesuai dengan domain resmi repositori SIGAP di GitHub, pilih **Tetap Download** (*Download anyway*). Pesan ini merupakan dialog standar keamanan Android untuk setiap pengunduhan berkas instalasi dari luar toko aplikasi.

### Langkah 2: Buka Berkas Hasil Unduhan
1. Setelah unduhan selesai, ketuk berkas melalui bilah notifikasi di bagian atas layar ponsel Anda.
2. Jika notifikasi unduhan telah tertutup, buka aplikasi **Pengelola Berkas** (*File Manager*) bawaan ponsel, masuk ke folder **Download** / **Unduhan**, lalu ketuk berkas `SIGAP.apk`.

### Langkah 3: Mengaktifkan Izin Pemasangan Sumber Tidak Dikenal
Sistem operasi Android membatasi instalasi aplikasi dari luar toko aplikasi demi keamanan perangkat. Anda hanya perlu memberikan izin satu kali untuk aplikasi peramban atau pengelola berkas yang Anda gunakan:

1. Sistem akan menampilkan dialog konfirmasi:
   *"Demi keamanan Anda, ponsel saat ini tidak diizinkan memasang aplikasi tidak dikenal dari sumber ini."*
2. Ketuk tombol **Setelan** (*Settings*).
3. Cari opsi **Izinkan dari sumber ini** (*Allow from this source*), lalu ubah posisinya menjadi **Aktif**.
4. Tekan tombol **Kembali** (*Back*) untuk melanjutkan proses pemasangan aplikasi.

> [!NOTE]
> Letak dan istilah menu ini dapat bervariasi bergantung pada merek dan antarmuka perangkat:
> - **Samsung (One UI)**: Masuk ke *Instal aplikasi tidak dikenal* -> pilih browser/file manager -> aktifkan toggle izin.
> - **Xiaomi / Redmi / POCO (MIUI / HyperOS)**: Layar peringatan risiko 10 detik -> centang *"Saya menyadari kemungkinan risiko"* -> ketuk *Oke*.
> - **OPPO / Realme / Vivo (ColorOS / Funtouch OS)**: Masuk ke *Instal sumber tidak dikenal* -> aktifkan toggle izin untuk aplikasi pengelola berkas.

### Langkah 4: Selesaikan Pemasangan
1. Layar akan menampilkan dialog instalasi dengan logo dan nama **SIGAP**.
2. Tekan tombol **Instal** (*Install*).
3. Tunggu proses pemasangan selama beberapa detik hingga muncul keterangan **Aplikasi terinstal** (*App installed*).
4. Tekan tombol **Buka** (*Open*) untuk langsung mulai menggunakan SIGAP, atau ketuk **Selesai** (*Done*). Ikon SIGAP kini telah tersedia di laci aplikasi atau layar utama perangkat Anda.

---

## 3. Peringatan Keamanan Google Play Protect

Saat memasang berkas APK secara mandiri, fitur pemindai keamanan Android (*Google Play Protect*) dapat menampilkan dialog verifikasi atau peringatan keamanan pada layar perangkat.

### Panduan Penanganan Play Protect:
- **Tetap Aktifkan Google Play Protect**: Jangan mematikan Google Play Protect pada perangkat Anda. Fitur ini merupakan sistem perlindungan penting untuk mendeteksi potensi ancaman keamanan pada ponsel Android.
- **Pemberitahuan Aplikasi Tidak Dikenal (*Unrecognized App*)**:
  Sistem Android dapat menampilkan konfirmasi bahwa pengembang aplikasi belum terdaftar di katalog massal Google Play Store. Jika dialog yang muncul hanya berupa verifikasi pengembang tidak dikenal:
  1. Pastikan berkas APK diunduh langsung dari repositori distribusi resmi SIGAP (`https://github.com/adlnfkhrzmn/sigap-app`).
  2. Periksa kesesuaian nilai *checksum* SHA-256 berkas terhadap tabel verifikasi resmi di bagian akhir panduan ini untuk memastikan berkas utuh dan tidak mengalami kerusakan saat pengunduhan.
  3. Apabila sumber dan integritas berkas telah dipastikan, Anda dapat memilih **Rincian Lainnya** (*More details*) lalu memilih **Tetap instal** (*Install anyway*).
- **Peringatan Aplikasi Berbahaya atau Pemblokiran Instalasi (*Harmful App / Installation Blocked*)**:
  > [!CAUTION]
  > Apabila Google Play Protect secara eksplisit mengidentifikasi aplikasi sebagai berbahaya (*harmful app*) atau memblokir proses instalasi demi keamanan:
  > 1. **Segera hentikan proses instalasi** dan jangan abaikan atau lewati peringatan keamanan tersebut secara membabi buta.
  > 2. Periksa kembali apakah berkas berasal dari repositori distribusi resmi SIGAP dan cocok dengan nilai *checksum* SHA-256 yang dipublikasikan (perlu dipahami bahwa kesesuaian *checksum* hanya membuktikan keutuhan berkas dari sumber rilis, bukan jaminan bahwa aplikasi bebas dari kendala yang dideteksi oleh sistem).
  > 3. **Tunggu klarifikasi resmi** melalui halaman repositori distribusi SIGAP (`https://github.com/adlnfkhrzmn/sigap-app`) sebelum mencoba melakukan instalasi kembali.

---

## 4. Pembaruan Aplikasi dan Pemecahan Masalah

### Cara Memperbarui Aplikasi di Masa Depan
1. Unduh berkas APK versi terbaru dari repositori resmi SIGAP yang sama.
2. Pasang berkas baru tersebut langsung di atas aplikasi yang sedang terpasang tanpa mencopot (*uninstall*) versi lama.
3. Sistem Android akan mengenali berkas sebagai pembaruan dan menampilkan dialog konfirmasi **Perbarui** (*Update*). Seluruh database produk dan riwayat transaksi toko akan tetap terjaga.

### Kendala: "Aplikasi tidak terinstal" atau "Paket bentrok dengan versi yang ada"
Penyebab umum kegagalan instalasi meliputi:
1. **Perbedaan Kunci Sertifikat (*Signature Mismatch*)**:
   Jika perangkat sebelumnya pernah dipasangi versi pengujian internal (*debug build*), sistem Android akan menolak pemasangan versi rilis resmi karena perbedaan tanda tangan digital.
2. **Kapasitas Penyimpanan Internal Kurang**:
   Pastikan ponsel memiliki ruang penyimpanan kosong minimal 100 MB sebelum memulai pemasangan.
3. **Versi Android di Bawah Persyaratan Minimum**:
   SIGAP memerlukan minimal Android 8.0 (API level 26 / Oreo) atau versi yang lebih baru. Perangkat dengan Android 7.1 atau versi yang lebih lama tidak dapat memasang aplikasi ini.

### Peringatan Terkait Penghapusan Aplikasi dan Data Toko
> [!WARNING]
> **Menghapus (*uninstall*) aplikasi SIGAP dari perangkat dapat menghapus seluruh database lokal toko Anda** (katalog produk, stok barang, riwayat transaksi nota, dan pengaturan usaha).<br>
> Jangan jadikan pencopotan aplikasi (*uninstall*) sebagai langkah rutin pemecahan masalah. Apabila pencopotan terpaksa harus dilakukan:
> 1. Buka aplikasi SIGAP.
> 2. Buka menu **Pengaturan** -> **Cadangkan Data**.
> 3. Tekan **Cadangkan Data Sekarang** dan simpan berkas cadangan ke memori eksternal atau penyimpanan cloud pribadi Anda.
> 4. Setelah aplikasi baru terpasang, gunakan menu **Pulihkan Data** untuk memulihkan seluruh data toko Anda.

---

## 5. Izin Perangkat dan Verifikasi Berkas

### Izin Perangkat yang Digunakan
Aplikasi SIGAP mengedepankan efisiensi dan membatasi permintaan izin:
- **Kamera (Opsional)**: Hanya diminta ketika kasir menggunakan fitur pemindai barcode / SKU fisik produk via kamera belakang. Izin ini dapat ditolak tanpa menghentikan fungsi kasir inti (pencarian produk manual dan input barcode via keyboard tetap dapat digunakan).
- **Penyimpanan (Storage Access Framework)**: Hanya digunakan saat Anda secara sadar menjalankan fungsi ekspor/impor katalog via Excel/CSV atau mencadangkan basis data lokal.
- SIGAP **tidak** meminta izin akses internet (`android.permission.INTERNET`), lokasi perangkat, kontak telepon, riwayat panggilan, maupun SMS pada manifest aplikasi.

### Tabel Verifikasi Integritas Berkas Resmi
Sebelum memasang, Anda dapat mencocokkan integritas berkas unduhan dengan nilai resmi berikut:

| Parameter | Nilai Resmi |
| :--- | :--- |
| **Nama Berkas Rilis** | `SIGAP.apk` |
| **Ukuran Berkas** | `13.288.129` bytes (~`13,29 MB`) |
| **SHA-256 Berkas APK** | `fa4bba7ac8b7ca0712641e267dfaf2a10294a61c29d72f37c6ca5b7209868ce6` |
| **SHA-256 Sertifikat Rilis** | `fd7f2e9f46f9f6422df79e8189d5c35b8d2706ddf306e42f3af780f4fc588673` |
