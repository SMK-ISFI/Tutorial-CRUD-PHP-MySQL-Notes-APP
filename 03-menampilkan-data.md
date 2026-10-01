# Latihan: Menampilkan Data Notes dari Database

Setelah aplikasi berhasil terhubung ke database, langkah berikutnya adalah menampilkan data yang tersimpan di tabel `notes`.

Pada latihan ini kita akan membuat halaman utama index.php yang menampilkan seluruh data catatan dalam bentuk card Bootstrap. Setiap catatan akan ditampilkan satu card per baris agar tampilannya rapi dan mudah dibaca.

1. Membuat File `index.php`

   Di dalam folder proyek notes-app, buat file baru `index.php`. Struktur proyek sementara menjadi:

   ```
   notes-app/
   ├── connection.php
   └── index.php
   ```

2. Hubungkan `index.php` dengan Database.

   Buka file `index.php`, kemudian panggil file `connection.php`.

   ```php
   <?php

   require "connection.php";
   ```

   Dengan cara ini, variabel `$conn` yang sudah dibuat di `connection.php` dapat digunakan di halaman `index.php`.

3. Mengambil Data dari Tabel `notes`

   Tambahkan query untuk mengambil seluruh data notes.

   ```php
   <?php

   require "connection.php";

   $query = "SELECT * FROM notes ORDER BY createdAt DESC";

   $results = mysqli_query($conn, $query);
   ```

4. Membuat Tampilan dengan Bootstrap

   Selanjutnya tambahkan struktur HTML dan Bootstrap.

   ```php
   <?php

   require "connection.php";

   $query = "SELECT * FROM notes ORDER BY createdAt DESC";
   $result = mysqli_query($conn, $query);

   ?>

   <!doctype html>
   <html lang="id">
   <head>
       <meta charset="UTF-8">

       <meta
           name="viewport"
           content="width=device-width, initial-scale=1.0"
       >

       <title>Notes App</title>

       <link
           href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
           rel="stylesheet"
       >
   </head>

   <body class="bg-light">

       <div class="container py-5">

           <div class="mb-4">
               <h1 class="fw-bold">Notes App</h1>

               <p class="text-secondary">
                   Daftar catatan yang tersimpan.
               </p>
           </div>

           <?php if (mysqli_num_rows($results) > 0) : ?>

               <?php while ($note = mysqli_fetch_assoc($results)) : ?>

                   <div class="card mb-3 shadow-sm">
                       <div class="card-body">

                           <h5 class="card-title">
                               <?= htmlspecialchars($note["title"]); ?>
                           </h5>

                           <p class="card-text">
                               <?= htmlspecialchars($note["body"]); ?>
                           </p>

                           <small class="text-secondary">
                               Dibuat:
                               <?= $note["createdAt"]; ?>
                           </small>

                       </div>
                   </div>

               <?php endwhile; ?>

           <?php else : ?>

               <div class="alert alert-info">
                   Belum ada catatan yang tersimpan.
               </div>

           <?php endif; ?>

       </div>

   </body>
   </html>
   ```

5. Simpan file `index.php`, kemudian buka melalui browser:

   ```
   http://localhost/notes-app
   ```

   Jika tabel `notes` masih kosong, akan tampil pesan:

   `Belum ada catatan yang tersimpan.`

## Bedah Kode

### Menghubungkan File Koneksi

```php
require "connection.php";
```

Kode tersebut digunakan untuk memanggil file `connection.php`. File tersebut sebelumnya sudah berisi koneksi ke database. Dengan begitu, variabel `$conn` dapat langsung digunakan pada index.php. Tanpa kode ini, halaman `index.php` tidak dapat berkomunikasi dengan database.

### Membuat Query SQL

```sql
$query = "SELECT * FROM notes ORDER BY createdAt DESC";
```

Variabel $query digunakan untuk menyimpan perintah SQL. `SELECT * FROM notes` berarti mengambil seluruh data diambil dari tabel `notes`. `ORDER BY createdAt DESC` digunakan untuk mengurutkan data berdasarkan `createdAt`, `DESC` berarti data diurutkan dari yang terbaru ke yang paling lama.

### Menjalankan Query

```php
$result = mysqli_query($conn, $query);
```

Fungsi `mysqli_query()` digunakan untuk menjalankan query SQL. Fungsi tersebut membutuhkan dua informasi utama Koneksi database, Query SQL. Pada kode `$conn` merupakan koneksi database. Sedangkan `$query` merupakan perintah SQL yang ingin dijalankan.

### Mengecek Apakah Data Tersedia

```php
if (mysqli_num_rows($results) > 0) :
```

Fungsi `mysqli_num_rows()` digunakan untuk menghitung jumlah data yang ditemukan dari hasil query. Jika jumlah data lebih dari `0`, berarti terdapat data notes.

### Mengambil Data Satu per Satu

```php
while ($note = mysqli_fetch_assoc($results)) :
```

Fungsi `mysqli_fetch_assoc()` digunakan untuk mengambil satu data dari hasil query dalam bentuk array asosiatif.
Contoh satu data yang diperoleh:

```php
[
    "id" => "note-12345678",
    "title" => "Belajar PHP",
    "body" => "Hari ini belajar CRUD.",
    "createdAt" => "2026-09-28 08:30:00",
    "updatedAt" => "2026-09-28 08:30:00"
]
```

Karena hasilnya berupa array asosiatif, data dapat diakses berdasarkan nama kolom.

Contoh:

```php
$note["title"]
```

digunakan untuk mengambil judul catatan.

Sedangkan:

```php
$note["body"]
```

digunakan untuk mengambil isi catatan.

Perulangan `while` digunakan karena jumlah catatan di database bisa berubah-ubah. Misal terdapat 5 catatan, maka card akan ditampilkan 5 kali. Dengan demikian, kita tidak perlu menulis card secara manual untuk setiap data.
