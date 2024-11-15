# Dokumen Kebutuhan Bisnis (BRD) untuk Aplikasi Guru

---

## 1. Pendahuluan

### Tujuan
Aplikasi Guru dirancang untuk mengelola data guru secara efisien. Aplikasi ini menyediakan fitur untuk membuat, memperbarui, dan melihat data guru, serta menetapkan peran seperti `super_admin` kepada pengguna untuk tugas administrasi.

### Ruang Lingkup
Aplikasi ini mendukung institusi pendidikan dalam mengelola data terkait guru, termasuk nama, NIP (Nomor Induk Pegawai), dan mata pelajaran yang diajarkan.

---

## 2. Tujuan Bisnis
- **Pengelolaan Data Guru Terpusat:** Memastikan semua data guru disimpan dalam satu basis data terpusat.
- **Kemudahan Akses:** Menyediakan antarmuka web bagi administrator untuk mengelola informasi guru.
- **Manajemen Peran:** Memungkinkan pemberian peran tertentu, seperti `super_admin`, untuk pengawasan administratif.

---

## 3. Kebutuhan Fungsional

### 3.1 Manajemen Guru
- **Tambah Data Guru Baru:**
  - **Field:** Nama, NIP, Mata Pelajaran (`mata_pelajaran`).
  - **Contoh:** File `GuruSeeder` menunjukkan penambahan data untuk "Shinta" dengan mata pelajaran "Matematika."
- **Perbarui Data Guru:**
  - Memodifikasi informasi guru, seperti mengubah mata pelajaran atau memperbaiki nama/NIP.
- **Hapus Data Guru:**
  - Menghapus data yang sudah tidak relevan atau duplikat.

### 3.2 Manajemen Peran
- Menetapkan peran kepada pengguna, terutama peran `super_admin`, untuk memberikan hak administratif.
  - **Contoh:** File `DatabaseSeeder` membuat pengguna "Admin" dengan peran `super_admin`.

### 3.3 Autentikasi Pengguna
- Menyediakan autentikasi untuk akses aman ke sistem.

### 3.4 Manajemen Basis Data
- Menjaga struktur basis data untuk catatan guru menggunakan file migrasi.
  - **Tabel:** `gurus`
  - **Kolom:** `id`, `name`, `NIP`, `mata_pelajaran`, timestamps.

---

## 4. Kebutuhan Teknis
- **Tech Stack:** Framework Laravel dengan basis data MySQL.
- **Model Data:**
  - Model `Guru` merepresentasikan data guru dengan kolom-kolom yang dapat diisi secara massal (`fillable`).
  - Seeder (`GuruSeeder` dan `DatabaseSeeder`) mengisi basis data dengan data awal.
- **Migrasi:** Mengelola pembuatan dan struktur tabel `gurus`.

---

## 5. Asumsi dan Kendala

### Asumsi
- Setiap guru memiliki NIP yang unik.
- Field `mata_pelajaran` (mata pelajaran) adalah wajib diisi.

### Kendala
- Basis data harus sesuai dengan struktur yang didefinisikan di file migrasi.
- Penetapan peran bergantung pada peran yang sudah ada dalam sistem (misalnya, `super_admin` harus didefinisikan sebelumnya).

---

## 6. Kasus Penggunaan

### Kasus Penggunaan 1: Menambah Data Guru
- **Aktor:** Admin
- **Deskripsi:** Admin menambahkan data guru baru melalui antarmuka aplikasi.
- **Input:** Nama, NIP, Mata Pelajaran
- **Output:** Data baru ditambahkan ke tabel `gurus`.

### Kasus Penggunaan 2: Menetapkan Peran
- **Aktor:** Admin
- **Deskripsi:** Admin menetapkan peran `super_admin` kepada pengguna.
- **Input:** Email pengguna, nama peran
- **Output:** Pengguna diberikan hak akses `super_admin`.

---

## 7. Risiko
- Masalah integritas data jika NIP tidak diterapkan sebagai unik.
- Kontrol akses berbasis peran mungkin tidak efektif jika peran salah dikonfigurasi.

---

## 8. Pengembangan di Masa Depan
- Menambahkan fitur pencarian dan filter lanjutan untuk data guru.
- Mendukung pengunggahan foto guru atau metadata tambahan.
- Integrasi dengan sistem manajemen sekolah untuk fungsionalitas yang lebih luas.

---
