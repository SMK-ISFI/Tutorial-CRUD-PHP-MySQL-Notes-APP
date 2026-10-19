# PRAKTIKUM PEMROGRAMAN WEB DAN OBJEK

**Materi: CRUD Menggunakan PHP dan MySQL dengan Validasi Form**  
**Bentuk Tugas: Individu (Mandiri)**

## Tujuan Praktikum

Pada praktikum ini, setiap siswa diminta membuat sebuah aplikasi web sederhana untuk mengelola data menggunakan PHP dan MySQL. Aplikasi harus memiliki empat fitur utama, yaitu **Create, Read, Update, dan Delete (CRUD)**, serta validasi untuk memastikan data yang dimasukkan sesuai ketentuan.

Melalui praktikum ini, siswa diharapkan mampu menghubungkan aplikasi PHP dengan database MySQL, mengelola data melalui halaman web, menerapkan validasi input, dan membuat antarmuka yang rapi menggunakan Bootstrap 5.

Teknologi yang digunakan:

- **PHP Native** sebagai bahasa pemrograman backend.
- **MySQL** sebagai database.
- **HTML dan CSS** untuk struktur dan tampilan halaman.
- **Bootstrap 5** untuk antarmuka aplikasi.

Selain memastikan seluruh fitur berjalan dengan baik, siswa harus memperhatikan kemudahan penggunaan aplikasi.

## A. Ketentuan Umum

Buatlah satu aplikasi web berdasarkan salah satu tema yang tersedia pada soal ini. **Tugas dikerjakan secara mandiri oleh setiap siswa**, mulai dari perancangan database, pembuatan fitur, validasi, pengujian, hingga pengumpulan.

Ketentuan aplikasi:

1. Aplikasi menggunakan PHP Native dan MySQL dengan koneksi `mysqli`.
2. Database menggunakan **1 tabel utama** yang memiliki minimal **6 kolom**, termasuk `id`.
3. Kolom `id` harus memiliki nilai unik sebagai identitas setiap data.
4. Aplikasi wajib memiliki fitur **Create, Read, Update, dan Delete**.
5. Form tambah dan edit data wajib dilengkapi validasi.
6. Pesan kesalahan validasi ditampilkan di bawah input yang bermasalah.
7. Proses tambah, ubah, dan hapus data harus menggunakan metode `POST`.
8. Aplikasi menggunakan Bootstrap 5 dengan tampilan yang rapi dan responsif.
9. Setiap aplikasi wajib memiliki minimal **5 data contoh**.
10. Fitur CRUD harus benar-benar terhubung dengan database, bukan menggunakan data statis.

## B. Struktur File Project

Pisahkan file tampilan, proses pengolahan data, dan koneksi database. Berikut contoh struktur file minimal:

```text
nama-project/
├── index.php
├── create.php
├── process-create.php
├── edit.php
├── process-update.php
├── process-delete.php
└── config/
    └── database.php
```

Keterangan:

| File | Fungsi |
|---|---|
| `index.php` | Menampilkan daftar data. |
| `create.php` | Menampilkan form tambah data. |
| `process-create.php` | Memproses penyimpanan data baru. |
| `edit.php` | Menampilkan form ubah data. |
| `process-update.php` | Memproses perubahan data. |
| `process-delete.php` | Memproses penghapusan data. |
| `config/database.php` | Menyimpan koneksi database MySQL. |

Siswa boleh menambahkan file atau folder sesuai kebutuhan. Nama file dapat disesuaikan selama pemisahan tampilan dan proses tetap diterapkan.

## C. Fitur yang Wajib Dibuat

### 1. Menampilkan Data (Read)

Buat halaman utama yang menampilkan seluruh data dari database.

Ketentuan:

- Data ditampilkan menggunakan **Bootstrap Table** atau **Bootstrap Card**.
- Menampilkan informasi sesuai tema aplikasi.
- Terdapat tombol **Tambah Data** untuk menuju form penambahan.
- Setiap data memiliki tombol **Edit** dan **Hapus**.
- Jika belum ada data, tampilkan pesan, misalnya *"Belum ada data yang tersedia"*.
- Data harus berasal dari database MySQL.

### 2. Menambahkan Data (Create)

Buat halaman form untuk menambahkan data baru.

Ketentuan:

- Form memiliki input sesuai kebutuhan tema.
- Menggunakan komponen form Bootstrap 5.
- Seluruh input penting wajib diisi.
- Data diperiksa sebelum disimpan.
- Jika validasi gagal, data tidak boleh disimpan.
- Jika berhasil, pengguna diarahkan ke halaman daftar data dan mendapatkan pesan keberhasilan.

### 3. Mengubah Data (Update)

Buat fitur untuk mengubah data yang sudah tersimpan.

Ketentuan:

- Tombol **Edit** tersedia pada setiap data.
- Form edit menampilkan nilai lama dari database.
- Pengguna dapat mengubah informasi sesuai kebutuhan.
- Validasi tetap diterapkan pada form edit.
- Perubahan hanya dilakukan pada data yang dipilih berdasarkan `id`.
- Setelah berhasil diperbarui, tampilkan pesan keberhasilan.

### 4. Menghapus Data (Delete)

Buat fitur untuk menghapus data dari database.

Ketentuan:

- Tombol **Hapus** tersedia pada setiap data.
- Sebelum menghapus, tampilkan konfirmasi menggunakan JavaScript atau Bootstrap Modal.
- Penghapusan wajib menggunakan form dengan metode `POST`, **bukan tautan `href`**.
- Hapus data sesuai `id` yang dipilih.
- Setelah berhasil, tampilkan pesan keberhasilan.
- Data yang dihapus tidak boleh muncul kembali pada daftar data.

### 5. Validasi Form

Setiap aplikasi wajib menerapkan validasi pada halaman tambah dan edit data. Validasi **tidak cukup** hanya menggunakan atribut HTML seperti `required`, tetapi juga harus diperiksa melalui PHP sebelum data disimpan ke database.

Ketentuan:

1. Input wajib tidak boleh kosong.
2. Input angka harus berisi angka dengan batas nilai yang sesuai.
3. Panjang teks diperiksa jika terdapat ketentuan jumlah karakter.
4. Input pilihan, seperti kategori atau status, hanya menerima nilai yang diperbolehkan.
5. Pesan kesalahan muncul tepat di bawah input yang bermasalah.
6. Jika validasi gagal, nilai yang telah dimasukkan tetap ditampilkan pada form.
7. Jika seluruh input valid, data dapat disimpan atau diperbarui.
8. Gunakan `session` untuk membantu menyimpan dan menampilkan pesan validasi setelah pengalihan halaman.

**Contoh pesan validasi:**

- Nama barang wajib diisi.
- Jumlah barang tidak boleh kurang dari 0.
- Harga harus lebih dari 0.
- Deskripsi minimal 10 karakter.
- Pilih status yang tersedia.

## D. Pilihan Tema Project

Setiap siswa memilih **satu tema aplikasi**. Tema di bawah ini memiliki tingkat kesulitan yang relatif setara.

### Opsi 1 — Sistem Pendataan Peminjaman Alat Sekolah

Buat aplikasi untuk mencatat peminjaman peralatan sekolah seperti kamera, tripod, laptop, dan proyektor.

| Kolom | Contoh Data |
|---|---|
| Nama Peminjam | Ahmad Fauzi |
| Nama Alat | Kamera Canon |
| Jumlah | 2 |
| Tanggal Pinjam | 19 Oktober 2026 |
| Tanggal Kembali | 22 Oktober 2026 |
| Status | Dipinjam |

**Validasi khusus:** Jumlah minimal 1, nama peminjam wajib diisi, dan tanggal kembali tidak boleh lebih awal daripada tanggal pinjam.

### Opsi 2 — Sistem Pendataan Pesanan Kantin

Buat aplikasi untuk mencatat pesanan makanan dan minuman di kantin sekolah.

| Kolom | Contoh Data |
|---|---|
| Nama Pemesan | Siti Rahma |
| Nama Menu | Nasi Ayam |
| Kategori | Makanan |
| Harga | 15000 |
| Jumlah | 2 |
| Status | Diproses |

**Validasi khusus:** Harga dan jumlah harus lebih dari 0, nama pemesan wajib diisi, dan kategori hanya boleh Makanan atau Minuman.

### Opsi 3 — Sistem Pendataan Jadwal Servis Kendaraan

Buat aplikasi untuk mencatat kendaraan yang masuk ke bengkel untuk mendapatkan layanan servis.

| Kolom | Contoh Data |
|---|---|
| Nama Pemilik | Budi Santoso |
| Jenis Kendaraan | Motor |
| Nomor Polisi | DA 1234 AB |
| Jenis Servis | Ganti Oli |
| Tanggal Servis | 19 Oktober 2026 |
| Status | Menunggu |

**Validasi khusus:** Nomor polisi wajib diisi, tanggal servis harus berupa tanggal yang valid, dan status hanya boleh Menunggu, Dikerjakan, atau Selesai.

### Opsi 4 — Sistem Pendataan Penyewaan Lapangan

Buat aplikasi untuk mengelola pemesanan atau penyewaan lapangan olahraga.

| Kolom | Contoh Data |
|---|---|
| Nama Penyewa | Rizky Pratama |
| Jenis Lapangan | Futsal |
| Tanggal Sewa | 21 Oktober 2026 |
| Jam Mulai | 16:00 |
| Durasi | 2 jam |
| Biaya | 150000 |
| Status | Dipesan |

**Validasi khusus:** Durasi minimal 1 jam, biaya harus lebih dari 0, dan nama penyewa wajib diisi.

### Opsi 5 — Sistem Pendataan Pengeluaran Kegiatan Kelas

Buat aplikasi untuk mencatat pengeluaran uang kas yang digunakan dalam kegiatan kelas.

| Kolom | Contoh Data |
|---|---|
| Nama Pengeluaran | Membeli Spidol |
| Kategori | Perlengkapan |
| Jumlah Uang | 25000 |
| Tanggal | 19 Oktober 2026 |
| Penanggung Jawab | Nur Aisyah |
| Keterangan | Spidol untuk kelas |

**Validasi khusus:** Jumlah uang harus lebih dari 0, nama pengeluaran wajib diisi, dan kategori harus dipilih dari pilihan yang tersedia.

### Opsi 6 — Sistem Pendataan Peserta Lomba

Buat aplikasi untuk mengelola pendaftaran peserta pada kegiatan perlombaan sekolah.

| Kolom | Contoh Data |
|---|---|
| Nama Peserta | Dimas Saputra |
| Kelas | XI PPLG 2 |
| Nama Lomba | Desain Poster |
| Kategori | Individu |
| Tanggal Daftar | 19 Oktober 2026 |
| Status | Terdaftar |

**Validasi khusus:** Nama peserta wajib diisi, kelas harus dipilih, dan kategori hanya boleh Individu atau Kelompok.

### Opsi 7 — Sistem Pendataan Paket Pengiriman

Buat aplikasi untuk mencatat paket yang diterima dan dikirim melalui layanan ekspedisi sederhana.

| Kolom | Contoh Data |
|---|---|
| Nama Pengirim | Andi Wijaya |
| Nama Penerima | Rina Putri |
| Alamat Tujuan | Banjarbaru |
| Jenis Paket | Elektronik |
| Berat | 2,5 kg |
| Status | Dalam Pengiriman |

**Validasi khusus:** Nama pengirim dan penerima wajib diisi, alamat tujuan minimal 10 karakter, serta berat paket harus lebih dari 0.

### Opsi 8 — Sistem Pendataan Pemesanan Jasa Desain

Buat aplikasi untuk mengelola pesanan jasa desain grafis, seperti poster, logo, banner, atau konten media sosial.

| Kolom | Contoh Data |
|---|---|
| Nama Pelanggan | Fajar Ramadhan |
| Jenis Desain | Poster |
| Deskripsi | Poster acara sekolah |
| Harga | 75000 |
| Deadline | 25 Oktober 2026 |
| Status | Dikerjakan |

**Validasi khusus:** Deskripsi minimal 10 karakter, harga harus lebih dari 0, dan status hanya boleh Menunggu, Dikerjakan, atau Selesai.

> Siswa diperbolehkan memilih tema lain di luar delapan pilihan tersebut dengan persetujuan guru. Tema harus memungkinkan penerapan seluruh fitur CRUD dan validasi.

## E. Petunjuk Pengerjaan Mandiri

**Praktikum ini merupakan tugas individu.** Setiap siswa wajib menghasilkan satu aplikasi miliknya sendiri dan bertanggung jawab atas seluruh proses pembuatannya.

Langkah pengerjaan:

1. Pilih satu tema project dari pilihan yang disediakan atau usulkan tema lain kepada guru.
2. Tentukan kebutuhan data dan buat satu tabel utama dengan minimal 6 kolom, termasuk `id`.
3. Buat database MySQL dan file koneksi menggunakan `mysqli`.
4. Buat halaman **Read** untuk menampilkan data dari database.
5. Buat fitur **Create** untuk menambahkan data melalui form.
6. Buat fitur **Update** untuk mengubah data yang sudah tersimpan.
7. Buat fitur **Delete** untuk menghapus data dengan konfirmasi.
8. Terapkan validasi pada form tambah dan edit, termasuk pesan kesalahan di bawah input.
9. Rapikan tampilan aplikasi menggunakan Bootstrap 5.
10. Tambahkan minimal **5 data contoh**.
11. Uji seluruh fitur dan perbaiki kesalahan yang ditemukan.
12. Kumpulkan source code aplikasi dan file ekspor database sesuai ketentuan.

Setiap siswa boleh mempelajari dokumentasi, buku, dan materi pembelajaran. Namun, source code yang dikumpulkan harus dikerjakan dan dipahami sendiri, bukan menyalin project milik siswa lain.

## F. Pengujian Aplikasi

Sebelum dikumpulkan, setiap siswa wajib menguji aplikasinya menggunakan skenario berikut.

| No. | Skenario Pengujian | Hasil yang Diharapkan |
|---|---|---|
| 1 | Membuka halaman utama | Data dari database ditampilkan. |
| 2 | Menambah data dengan input valid | Data berhasil disimpan. |
| 3 | Menambah data dengan input kosong | Muncul pesan validasi. |
| 4 | Memasukkan angka di luar ketentuan | Input ditolak dan muncul pesan. |
| 5 | Mengedit data yang sudah ada | Form menampilkan data lama. |
| 6 | Menyimpan perubahan yang valid | Data berhasil diperbarui. |
| 7 | Mengedit data dengan input tidak valid | Perubahan ditolak dan muncul pesan. |
| 8 | Menghapus data dan menyetujui konfirmasi | Data berhasil dihapus. |
| 9 | Membatalkan konfirmasi penghapusan | Data tidak terhapus. |
| 10 | Membuka aplikasi saat database kosong | Muncul informasi bahwa data belum tersedia. |

Seluruh skenario harus diuji langsung pada aplikasi yang dibuat.

## G. Ketentuan Pengumpulan

Setiap siswa mengumpulkan **satu folder project miliknya sendiri**, tidak digabungkan dengan project siswa lain.

Format nama folder:

```text
nama_siswa-judul_project/
```

Contoh:

```text
Ahmad-peminjaman_alat/
├── index.php
├── create.php
├── process-create.php
├── edit.php
├── process-update.php
├── process-delete.php
├── config/
│   └── database.php
└── database.sql
```

Ketentuan pengumpulan:

1. Folder berisi seluruh source code aplikasi.
2. Sertakan file `.sql` hasil ekspor database.
3. Database harus memiliki minimal 5 data contoh.
4. Pastikan aplikasi dapat dijalankan kembali setelah file SQL diimpor ke MySQL dan pengaturan koneksi disesuaikan.
5. Pastikan semua fitur CRUD dan validasi bekerja sebelum dikumpulkan.

## H. Kriteria Penilaian

Penilaian dilakukan **secara individu** berdasarkan hasil aplikasi dan kemampuan siswa menjelaskan alur kode yang dibuat.

| Aspek Penilaian | Bobot |
|---|---:|
| Struktur database dan koneksi MySQL | 10% |
| Fitur Create | 15% |
| Fitur Read | 10% |
| Fitur Update | 15% |
| Fitur Delete | 15% |
| Validasi form dan pesan kesalahan | 20% |
| Tampilan dan kemudahan penggunaan | 10% |
| Kerapian struktur kode | 5% |
| **Total** | **100%** |

Guru dapat meminta siswa mendemonstrasikan aplikasi dan menjelaskan bagian kode tertentu untuk memastikan pemahaman terhadap hasil pekerjaannya.

## I. Aturan Pengerjaan Individu

1. Seluruh pengerjaan, mulai dari database hingga antarmuka aplikasi, menjadi tanggung jawab masing-masing siswa.
2. Tidak diperbolehkan menyalin project siswa lain kemudian hanya mengganti nama project, judul, atau isi data.
3. Siswa dapat berdiskusi mengenai konsep atau cara menemukan kesalahan, tetapi implementasi kode tetap dilakukan secara mandiri.
4. Siswa harus memahami fungsi setiap file dan alur proses CRUD yang dibuat.
5. Siswa bertanggung jawab melakukan pengujian dan memastikan aplikasi berjalan dengan baik saat diperiksa.

## Penutup

Melalui praktikum ini, siswa berlatih mengembangkan aplikasi yang mampu menyimpan, menampilkan, mengubah, dan menghapus data, sekaligus memeriksa input sebelum diproses.

Aplikasi dinyatakan selesai apabila seluruh fitur CRUD berjalan dengan baik, validasi diterapkan pada form tambah dan edit, serta data tersimpan dengan benar di database MySQL.

**Hasil akhir praktikum adalah satu aplikasi CRUD PHP dan MySQL yang dibuat secara mandiri, memiliki validasi input, dan dapat digunakan sesuai kebutuhan tema yang dipilih.**
