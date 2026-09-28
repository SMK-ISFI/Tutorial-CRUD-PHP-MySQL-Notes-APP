# Latihan: Menyiapkan Proyek CRUD Notes App

Sebelum mulai membuat fitur **CRUD (Create, Read, Update, Delete)**, kita perlu menyiapkan folder proyek dan database terlebih dahulu. Pada latihan ini, kita akan membuat aplikasi sederhana bernama Notes App untuk menyimpan catatan.

Ikuti langkah-langkah berikut dengan teliti.

1. Buat folder baru dengan nama `notes-app` di dalam folder web server Laragon:

   ```
   C:\laragon\www\notes-app
   ```

   Folder ini nantinya digunakan untuk menyimpan seluruh file PHP aplikasi Notes App.

2. Buka folder `notes-app` menggunakan **Visual Studio Code**. Pastikan **Laragon** sudah dijalankan. Kemudian aktifkan layanan:

   ```
   - Apache
   - MySQL
   ```

3. Buka Terminal, kemudian masuk ke MySQL dengan perintah:

   ```
   mysql -u root
   ```

4. Setelah berhasil masuk ke MySQL, buat database baru dengan nama `notesapp_db`

5. Buat tabel baru dengan nama `notes`:

   ```mysql
   CREATE TABLE notes (
     id VARCHAR(20) PRIMARY KEY,
     title VARCHAR(255) NOT NULL,
     body TEXT NOT NULL,
     createdAt DATETIME,
     updatedAt DATETIME
   );
   ```

   Struktur tabel yang digunakan:

| Field       | Tipe Data    | Keterangan                               |
| ----------- | ------------ | ---------------------------------------- |
| `id`        | VARCHAR(20)  | ID unik catatan, dibuat melalui kode PHP |
| `title`     | VARCHAR(255) | Judul catatan                            |
| `body`      | TEXT         | Isi catatan                              |
| `createdAt` | DATETIME     | Waktu catatan dibuat                     |
| `updatedAt` | DATETIME     | Waktu terakhir catatan diperbarui        |
