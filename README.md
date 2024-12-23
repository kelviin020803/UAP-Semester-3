## APK Laundry
 
**APK Laundry** adalah aplikasi manajemen laundry berbasis Java yang dirancang untuk membantu mengelola transaksi pelanggan, paket laundry, outlet, dan laporan secara efisien.

### Fitur Utama
- **Login dan Logout**: Autentikasi pengguna berdasarkan peran (admin, kasir, owner).
- **Manajemen Data**:
  - Anggota (Member)
  - Outlet
  - Paket Laundry
  - Pengguna (User)
- **Transaksi**:
  - Input dan kelola transaksi pelanggan.
  - Kelola status laundry (proses, selesai, diambil).
  - Status pembayaran (dibayar, belum dibayar).
- **Laporan**:
  - Cetak laporan transaksi dengan JasperReports.

### Teknologi yang Digunakan
- **Bahasa Pemrograman**: Java
- **Database**: MySQL
- **IDE**: NetBeans IDE
- **Library**:
  - MySQL Connector/J
  - JasperReports
  - JCalendar

### Cara Menjalankan
1. **Persiapkan Database**:
   - Jalankan database MySQL dan buat tabel-tabel yang diperlukan. Gunakan skrip SQL berikut:
     ```sql
     CREATE DATABASE laundry;

     USE laundry;

     CREATE TABLE member (
         id_member INT PRIMARY KEY AUTO_INCREMENT,
         nama VARCHAR(100),
         alamat TEXT,
         jenis_kelamin ENUM('L', 'P'),
         tlp VARCHAR(15)
     );

     CREATE TABLE outlet (
         id_outlet INT PRIMARY KEY AUTO_INCREMENT,
         nama VARCHAR(100),
         alamat TEXT,
         tlp VARCHAR(15)
     );

     CREATE TABLE user (
         id_user INT PRIMARY KEY AUTO_INCREMENT,
         nama VARCHAR(100),
         username VARCHAR(30),
         password VARCHAR(30),
         id_outlet INT,
         role ENUM('admin', 'kasir', 'owner'),
         FOREIGN KEY (id_outlet) REFERENCES outlet(id_outlet)
     );

     CREATE TABLE paket (
         id_paket INT PRIMARY KEY AUTO_INCREMENT,
         id_outlet INT,
         jenis ENUM('kiloan', 'selimut', 'bed cover', 'kaos', 'lainnya'),
         nama_paket VARCHAR(100),
         harga INT,
         FOREIGN KEY (id_outlet) REFERENCES outlet(id_outlet)
     );

     CREATE TABLE transaksi (
         id_transaksi INT PRIMARY KEY AUTO_INCREMENT,
         id_outlet INT,
         kode_invoice VARCHAR(100),
         id_member INT,
         tgl DATETIME,
         batas_waktu DATETIME,
         tgl_bayar DATETIME,
         biaya_tambahan INT,
         diskon DOUBLE,
         pajak INT,
         status ENUM('proses', 'selesai', 'diambil'),
         dibayar ENUM('dibayar', 'belum dibayar'),
         id_user INT,
         id_paket INT,
         qty DOUBLE,
         keterangan TEXT,
         FOREIGN KEY (id_outlet) REFERENCES outlet(id_outlet),
         FOREIGN KEY (id_member) REFERENCES member(id_member),
         FOREIGN KEY (id_user) REFERENCES user(id_user),
         FOREIGN KEY (id_paket) REFERENCES paket(id_paket)
     );
     ```

2. **Konfigurasi Proyek**:
   - Tambahkan file JAR berikut ke proyek NetBeans Anda:
     - MySQL Connector/J
     - JasperReports
     - JCalendar
   - Pastikan file laporan `.jasper` tersedia di folder `src/Laporan/`.

3. **Jalankan Aplikasi**:
   - Buka proyek di NetBeans.
   - Klik **Run Project** atau tekan `F6`.

### Troubleshooting
- **Koneksi Database Gagal**:
  - Periksa file `koneksi.java` untuk memastikan username, password, dan URL database sudah benar.

- **File Laporan Tidak Ditemukan**:
  - Pastikan file laporan (`.jasper`) ada di folder yang sesuai dan path sudah benar di kode.

### Lisensi
Proyek ini ditujukan untuk UAP dari Kelompok 8
1. Kelvin Pratama (202310370311382)
2. Erwin Dinata   (202310370311370)
3. M Alfa Rizky   (202310370311379)
4. Dandy F        (202310370311341)

---



