# Panduan Pengguna SIGAP v2

Panduan resmi penggunaan aplikasi kasir (Point of Sale) SIGAP v2 berbasis Android.

---

## DAFTAR ISI

1. [Pengaturan Awal & Konfigurasi Toko](#1-pengaturan-awal--konfigurasi-toko)
2. [Manajemen Produk & Inventaris](#2-manajemen-produk--inventaris)
3. [Operasional Kasir & Pengelolaan Shift](#3-operasional-kasir--pengelolaan-shift)
4. [Alur Pembayaran QRIS Otomatis](#4-alur-pembayaran-qris-otomatis)
5. [Riwayat Transaksi, Struk, Retur, & Laporan](#5-riwayat-transaksi-struk-retur--laporan)
6. [Cadangkan & Pulihkan Data (Backup & Restore)](#6-cadangkan--pulihkan-data-backup--restore)
7. [Melaporkan Kendala / Bug](#7-melaporkan-kendala--bug)

---

## 1. PENGATURAN AWAL & KONFIGURASI TOKO

### A. Instalasi dan Izin Aplikasi
Setelah memasang berkas APK SIGAP v2:
1. Buka aplikasi SIGAP di perangkat Android Anda.
2. Berikan izin yang diminta saat diperlukan:
   - **Akses Notifikasi:** Diperlukan agar SIGAP dapat mendeteksi notifikasi pembayaran masuk untuk menyelesaikan pesanan QRIS secara otomatis. Aktifkan melalui menu `Pengaturan > Akses Notifikasi Pembayaran`.
   - **Kamera:** Diperlukan hanya jika Anda menggunakan fitur pemindai barcode produk melalui kamera perangkat.

### B. Konfigurasi Tampilan Bawaan
Pada instalasi baru:
- **Tema Bawaan:** Mode Terang (Light Mode).
- **Palet Warna:** Nusantara Teal (aksen hijau kebiruan khas Nusantara).
- **Format Regional:** Bahasa Indonesia dengan format mata uang Rupiah (`Rp`) menggunakan tanda titik sebagai pemisah ribuan (contoh: `Rp15.000`), serta format tanggal Indonesia.

Anda dapat mengubah tema ke Mode Gelap atau memilih palet warna lain melalui menu `Pengaturan > Tampilan`.

### C. Mengatur Identitas Usaha Anda
1. Buka tab **Pengaturan** pada bilah navigasi bawah.
2. Pilih menu **Pengaturan Usaha**.
3. **Penting diperhatikan:** Pada instalasi awal, data nama usaha, alamat, dan nomor kontak toko berada dalam kondisi **kosong**. Teks bertuliskan `Nama Usaha` pada kolom input hanyalah petunjuk placeholder, bukan nama usaha yang tersimpan.
4. Masukkan nama toko Anda yang sebenarnya, alamat lengkap, dan nomor kontak/telepon.
5. Ketuk tombol **Simpan Pengaturan Usaha**. Data ini akan dicetak pada kepala struk transaksi belanja pelanggan.

### D. Impor QRIS Statis Merchant
Agar dapat menghasilkan kode QRIS dinamis untuk pembayaran pelanggan:
1. Siapkan gambar/foto kode QRIS statis toko Anda (diterbitkan oleh bank atau dompet digital berizin Bank Indonesia) di galeri foto perangkat.
2. Di menu **Pengaturan**, ketuk tombol **Impor QRIS dari Galeri**.
3. Pilih gambar QRIS toko Anda. Sistem akan memindai data merchant (Nama Merchant, Kota, NMID).
4. Periksa dialog konfirmasi data merchant. Jika data sudah sesuai, ketuk **Simpan QRIS**.

---

## 2. MANAJEMEN PRODUK & INVENTARIS

### A. Menambah Produk Baru
1. Buka tab **Produk** pada bilah navigasi bawah.
2. Ketuk tombol tambah produk (`+ Tambah Produk`).
3. Isi informasi produk:
   - **Nama Produk:** Nama barang yang dijual (wajib diisi).
   - **Kategori:** Pilih kategori yang ada atau tambahkan kategori baru.
   - **Harga Jual:** Nominal harga jual kepada pelanggan (wajib diisi).
   - **Harga Pokok (Modal):** Harga perolehan barang untuk perhitungan laba kotor toko.
   - **Stok Saat Ini:** Jumlah unit fisik yang tersedia di toko.
   - **Kode Barcode / SKU:** Masukkan kode manual atau gunakan tombol pemindai barcode kamera.
4. Ketuk tombol **Simpan**.

### B. Mengubah atau Menghapus Produk
- **Ubah Data:** Ketuk salah satu produk pada daftar katalog untuk membuka formulir penyuntingan, lalu ketuk **Perbarui**.
- **Hapus Produk:** Dari formulir rincian produk, ketuk tombol ikon tempat sampah untuk menghapus produk dari katalog toko.

---

## 3. OPERASIONAL KASIR & PENGELOLAAN SHIFT

### A. Membuka Shift Kasir
Sebelum memulai transaksi penjualan pada hari operasional baru:
1. Buka tab **Kasir**.
2. Masukkan nominal **Modal Awal Kas** (uang kembalian yang ada di laci kasir).
3. Ketuk tombol **Buka Shift**.

### B. Menambahkan Produk ke Keranjang Belanja
1. Pada layar kasir, telusuri produk berdasarkan kategori atau gunakan kolom pencarian di bagian atas.
2. Anda juga dapat mengetuk tombol ikon pemindai barcode untuk memindai barcode fisik barang menggunakan kamera kasir.
3. Ketuk kartu produk untuk memasukkannya ke dalam keranjang.
4. Ketuk item di keranjang untuk menyesuaikan jumlah kuantitas (`+` atau `-`) atau menghapus item dari keranjang.

### C. Pembayaran Tunai (Cash)
1. Ketuk tombol **Bayar Tunai** di bagian bawah keranjang.
2. Masukkan jumlah uang tunai yang diterima dari pelanggan (tersedia tombol nominal cepat seperti pas, 10.000, 20.000, 50.000, 100.000).
3. Layar akan menampilkan jumlah uang kembalian secara otomatis.
4. Ketuk **Konfirmasi Pembayaran Tunai**.
5. Pesanan selesai, stok produk terpotong otomatis, dan keranjang belanja dibersihkan. Anda dapat langsung mencetak struk atau menyelesaikan transaksi.

### D. Pencatatan Kas Masuk dan Kas Keluar
Untuk mencatat pergerakan uang tunai di luar penjualan:
1. Di tab kasir atau menu shift, gunakan tombol **Kas Masuk** atau **Kas Keluar**.
2. Masukkan nominal uang dan keterangan (misal: "Beli kantong plastik", "Setor ke pemilik").
3. Mutasi ini akan diperhitungkan pada laporan rekonsiliasi akhir shift.

### E. Menutup Shift Kasir
1. Di akhir jam kerja atau pergantian petugas kasir, buka menu **Kelola Shift**.
2. Ketuk tombol **Tutup Shift**.
3. Masukkan jumlah uang tunai fisik yang dihitung di dalam laci kasir.
4. Sistem akan membandingkan uang kas riil dengan catatan sistem (total modal awal + penjualan tunai + kas masuk - kas keluar) untuk mendeteksi apakah ada selisih kas (lebih/kurang).
5. Konfirmasi penutupan shift.

---

## 4. ALUR PEMBAYARAN QRIS OTOMATIS

SIGAP v2 memiliki fitur unggulan pendeteksian pembayaran QRIS secara otomatis tanpa perlu kasir memeriksa mutasi bank secara manual pada aplikasi eksternal.

### Alur Kerja 10 Langkah:
1. **Pilih Produk:** Kasir memasukkan item belanja pelanggan ke keranjang.
2. **Buat Pesanan QRIS:** Kasir mengetuk tombol metode pembayaran **QRIS**.
3. **Tampilkan Kode QR:** Layar kasir menampilkan kode QRIS dinamis yang telah memuat nominal belanja persis beserta penghitung mundur kedaluwarsa pesanan.
4. **Pelanggan Membayar:** Pelanggan memindai kode QRIS menggunakan aplikasi perbankan atau dompet digital apa pun yang mendukung standar QRIS nasional.
5. **Notifikasi Masuk ke Android:** Saat pembayaran berhasil diselesaikan, aplikasi merchant pedagang yang terpasang di perangkat kasir (seperti Shopee Partner atau GoPay Merchant) mengirimkan notifikasi resmi transaksi masuk ke perangkat Android kasir (contoh: *"Pembayaran sebesar Rp15.000 diterima"*).
6. **Pemrosesan Lokal:** Layanan pendengar notifikasi SIGAP v2 membaca judul dan teks notifikasi secara lokal di perangkat tanpa mengirim data ke internet.
7. **Pencocokan Unik & Aman:** Mesin pencocokan memverifikasi bahwa nominal notifikasi cocok persis dengan satu pesanan QRIS aktif yang sedang menunggu pembayaran dalam batas waktu toleransi 5 menit. Membaca notifikasi penerimaan dana tidak serta-merta membuktikan kepemilikan pesanan kasir kecuali seluruh aturan validasi nominal dan keunikan terpenuhi.
8. **Penyelesaian Otomatis:** Sistem secara otomatis menandai pesanan selesai, menampilkan kartu hijau konfirmasi berhasil, memotong stok inventaris barang, dan mencatat transaksi penjualan.
9. **Keranjang Belanja Dibersihkan:** Keranjang kasir dikosongkan secara otomatis sehingga kasir siap melayani transaksi pembeli berikutnya tanpa risiko pesanan ganda.
10. **Struk dan Riwayat:** Transaksi otomatis tercatat pada tab **Riwayat**, siap untuk dicetak atau ditinjau ulang.

> **Catatan Kompatibilitas Penyedia:** Pengujian langsung pada perangkat fisik telah dikonfirmasi untuk Shopee Partner, GoPay Merchant, DANA Bisnis, dan ShopeePay. Notifikasi perbankan lain seperti BCA diuji melalui simulasi pengujian otomatis, sedangkan aplikasi perbankan atau dompet digital lainnya diproses menggunakan pengurai pola teks generik (regex). Fitur otomatisasi sangat bergantung pada kejelasan informasi nominal pada notifikasi sistem penyedia. Jika notifikasi tidak terdeteksi, kasir tetap dapat menyelesaikan pesanan secara manual dengan menekan tombol **Pesanan Selesai**.

---

## 5. RIWAYAT TRANSAKSI, STRUK, RETUR, & LAPORAN

### A. Melihat Riwayat Transaksi
Buka tab **Riwayat** untuk melihat daftar transaksi penjualan yang telah selesai, diurutkan dari yang paling baru.

### B. Cetak dan Bagikan Struk
1. Ketuk salah satu transaksi dari daftar riwayat.
2. Ketuk tombol **Cetak Struk** untuk mencetak ke printer thermal Bluetooth (pastikan printer Bluetooth telah dipasangkan ke perangkat Android).
3. Anda juga dapat memilih opsi **Bagikan Teks Struk** untuk mengirim rincian tanda terima transaksi via aplikasi pesan teks.

### C. Retur Transaksi
Jika terjadi pembatalan transaksi oleh pelanggan:
1. Buka rincian transaksi terkait di tab Riwayat.
2. Pilih menu **Retur Transaksi**.
3. Konfirmasikan alasan retur. Sistem akan mengembalikan jumlah unit barang ke stok inventaris secara otomatis dan mencatat mutasi pengembalian dana.

### D. Laporan Keuangan Toko
Buka tab **Laporan** untuk melihat:
- Ringkasan omzet penjualan harian, mingguan, dan bulanan.
- Estimasi laba kotor berdasarkan selisih harga jual dan harga modal.
- Pembagian metode pembayaran (porsi Tunai vs QRIS).
- Riwayat pergerakan shift kasir.

---

## 6. CADANGKAN & PULIHKAN DATA (BACKUP & RESTORE)

Karena SIGAP v2 beroperasi luring (data disimpan secara lokal di memori perangkat), menjaga berkas cadangan secara berkala adalah hal yang sangat penting.

### A. Membuat Berkas Cadangan (Backup)
1. Buka tab **Pengaturan**, lalu pilih **Data dan File**.
2. Ketuk tombol **Buat Cadangan Baru**.
3. Sistem akan membuat berkas cadangan data berformat arsip `.sigap` / JSON yang mencakup katalog produk, stok, riwayat transaksi, dan pengaturan toko.
4. Simpan berkas cadangan tersebut ke folder aman di perangkat Anda, atau kirimkan salinannya ke penyimpanan luar (email/flashdisk).

### B. Memulihkan Data (Restore)
1. Di menu **Pengaturan > Data dan File**, pilih **Pulihkan Data dari Berkas**.
2. Pilih berkas cadangan yang sebelumnya telah dibuat.
3. Konfirmasikan proses pemulihan. Seluruh data transaksi dan produk akan diperbarui sesuai isi berkas cadangan.

> **PERINGATAN RISIKO UNINSTALL:** Jangan mencopot (uninstall) aplikasi SIGAP dari perangkat Android sebagai langkah coba-coba saat mengalami kendala teknis. Menghapus aplikasi dari sistem Android akan menghapus seluruh data transaksi lokal yang belum dicadangkan.

---

## 7. MELAPORKAN KENDALA / BUG

Jika Anda menemukan kendala teknis, kerusakan (bug), atau perilaku aplikasi yang tidak wajar:

1. Buka tab **Pengaturan**.
2. Pada bagian bawah kartu **TENTANG APLIKASI**, ketuk menu **Laporkan Kendala / Bug**.
3. Formulir pelaporan akan terbuka:
   - **Ringkasan Masalah (Wajib):** Tuliskan judul singkat kendala yang terjadi (minimal 5 karakter).
   - **Aktivitas yang Dilakukan (Opsional):** Jelaskan apa yang sedang Anda lakukan saat kendala terjadi.
   - **Langkah-langkah Mereproduksi (Opsional):** Tuliskan langkah urut agar pengembang dapat mengulangi masalah tersebut.
   - **Hasil Diharapkan & Hasil Sebenarnya (Opsional):** Perbedaan antara hasil yang Anda inginkan dan apa yang sebenarnya terjadi pada layar.
   - **Catatan Tambahan (Opsional):** Merek bank/aplikasi yang digunakan atau informasi relevan lainnya.
   - **Sakelar Info Teknis Perangkat:** Diaktifkan secara bawaan untuk menyertakan versi Android, model perangkat, dan versi SIGAP. Informasi ini tidak memuat data transaksi maupun saldo toko.
4. Anda dapat mengetuk tombol **Pratinjau** untuk melihat isi draf lengkap laporan.
5. Ketuk **Kirim Email**.
6. Aplikasi email di perangkat Anda (seperti Gmail) akan terbuka dengan draf yang telah terisi lengkap ke alamat `adlanfakhruzzaman@gmail.com`.
7. Periksa draf email Anda, lalu tekan tombol **Kirim** pada aplikasi email Anda.

> **Catatan Penting:** SIGAP v2 tidak mengirimkan laporan secara otomatis di latar belakang. Laporan hanya akan terkirim ke pengembang jika Anda menyelesaikan langkah pengiriman melalui aplikasi email Anda.
