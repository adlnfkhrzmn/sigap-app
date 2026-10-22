# Alur Demonstrasi Penyelesaian QRIS Otomatis SIGAP v2

Dokumen ini mendokumentasikan urutan pengujian langsung (real-device demonstration) fitur deteksi notifikasi pembayaran dan penyelesaian pesanan QRIS secara otomatis pada SIGAP v2.

---

## 1. Berkas Video Demonstrasi Terverifikasi

Berkas rekaman layar pengujian langsung pada perangkat fisik telah diverifikasi dan disiapkan pada direktori aset distribusi:

- **Nama Berkas:** `qris-automatic-completion-demo.mp4`
- **Tautan Berkas:** [Unduh / Putar Video Demonstrasi](assets/demo/qris-automatic-completion-demo.mp4)
- **Durasi & Resolusi:** 22,2 detik (576 x 1296 piksel, orientasi potret smartphone)
- **Ukuran Berkas:** `2.370.668` bytes (~2,37 MB)
- **Checksum SHA-256:** `86dec5e61d8479f8ad23867a375c52fb8fe89a69cbe420a33effc123d9afdd4f`

---

## 2. Alur Pengujian yang Ditampilkan dalam Video

Rekaman video memperlihatkan siklus lengkap pengujian di perangkat fisik Android:

1. **Pembuatan Pesanan Kasir (00:00 - 00:04)**
   - Kasir memilih produk "Tes 100p" nominal Rp 100 pada katalog toko Exousiastore.id.
   - Kasir memilih metode pembayaran **QRIS** dan menekan tombol **Tampilkan QRIS (Rp 100)**.
   - Sistem menghasilkan pesanan aktif dengan kode `QORD-20261022-D8BFA153` dan menampilkan kode QRIS dinamis.

2. **Dialog Menunggu Pembayaran (00:05 - 00:09)**
   - Status dialog berada pada `STATUS: MENUNGGU PEMBAYARAN QRIS` disertai indikator hijau "Mendengarkan notifikasi pembayaran otomatis".
   - Layar menampilkan QR code, total tagihan Rp 100, dan nama merchant.

3. **Notifikasi Masuk dari GoPay Merchant (00:10 - 00:12)**
   - Notifikasi resmi dari GoPay Merchant muncul pada bilah status Android:
     `Pembayaran QRIS statis diterima - Rp 100 di Joeragans, CIMAUNG.`

4. **Pencocokan Presisi & Konfirmasi Berhasil (00:13 - 00:15)**
   - SIGAP v2 membaca notifikasi secara instan di dalam perangkat (100% lokal).
   - Dialog secara otomatis beralih menampilkan ikon centang hijau:
     - Judul: **Pembayaran Berhasil** (Pembayaran terverifikasi otomatis)
     - Nominal: **Rp 100**
     - Metode: **QRIS (GoPay Merchant)**
     - Status: **Lunas (Otomatis)**
     - Nomor Pesanan: **QORD-20261022-D8BFA153**

5. **Pembersihan Keranjang & Rekonsiliasi Riwayat (00:16 - 00:22)**
   - Tombol **Selesai** ditekan dan dialog tertutup.
   - Tampilan kembali ke layar kasir; lencana keranjang pada produk "Tes 100p" terbukti otomatis kosong (bersih).
   - Kasir membuka tab **Riwayat** dan memeriksa nota transaksi yang baru selesai (`TRX-20261022-0007`) berstatus **LUNAS** dengan metode pembayaran QRIS Rp 100.

---

## 3. Hasil Audit Privasi & Keamanan Rekaman

Pemeriksaan privasi menyeluruh terhadap rekaman video `qris-automatic-completion-demo.mp4` menunjukkan:

- **Tidak Ada Data Pribadi Pelanggan:** Tidak terdapat nama, nomor telepon, identitas rekening bank pembeli, maupun data pribadi pembeli yang terekspos.
- **Transaksi Simulasi Uji Coba:** Nilai transaksi merupakan pengujian internal berbiaya minimal (Rp 100).
- **Data Merchant Bersifat Publik/Uji Coba:** Nama merchant "Joeragans, CIMAUNG - BANDUNG" dan NMID yang tampil merupakan data merchant uji coba pengembang.
- **Bilah Status Bersih:** Tidak ada pesan instan pribadi (seperti WhatsApp, SMS, atau email privat) yang muncul di bilah notifikasi selama perekaman.
- **Kesimpulan Audit:** Berkas video aman untuk disertakan sebagai materi demonstrasi publik pada rilis distribusi resmi.
