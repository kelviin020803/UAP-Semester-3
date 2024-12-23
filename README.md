# APK Laundry

**APK Laundry** adalah aplikasi manajemen laundry berbasis Java yang membantu mengelola transaksi, anggota, paket laundry, dan laporan.

## Fitur Utama
- **Login dan Logout**: Sistem autentikasi pengguna.
- **Manajemen Data**:
  - Anggota (Member)
  - Outlet
  - Paket Laundry
- **Transaksi**:
  - Kelola status laundry (proses, selesai, diambil).
  - Status pembayaran (dibayar, belum dibayar).
- **Cetak Laporan**: Laporan transaksi menggunakan JasperReports.

## Teknologi yang Digunakan
- Java
- MySQL
- JasperReports
- NetBeans IDE

## Cara Menjalankan
1. **Konfigurasi Database**:
   - Pastikan database MySQL berjalan.
   - Sesuaikan konfigurasi koneksi di file `koneksi.java`.

2. **Jalankan Aplikasi**:
   - Buka proyek di NetBeans.
   - Klik **Run Project** atau tekan `F6`.

## Struktur Database
Tabel utama:
- **outlet**
- **user**
- **member**
- **paket**
- **transaksi**

## Lisensi
Proyek ini dibuat untuk keperluan pembelajaran.
