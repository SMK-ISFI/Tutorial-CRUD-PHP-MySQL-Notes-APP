# Latihan: Membuat Koneksi Database dengan MySQLi

Setelah folder proyek dan database selesai dibuat, langkah berikutnya adalah menghubungkan aplikasi PHP dengan database `notesapp_db`.

1. Buka **Visual Studio Code**, Buat file baru dengan nama `connection.php`

2. Buka file connection.php, tuliskan kode di bawah ini:

   ```php
   <?php

   $hostname = "localhost";
   $username = "root";
   $password = "";
   $database = "notesapp_db";

   $conn = mysqli_connect(
     $hostname,
     $username,
     $password,
     $database
   );

   if (!$conn) {
     die("Koneksi database gagal: " . mysqli_connect_error());
   }
   ```

## Bedah Kode

### Variabel untuk menyimpan informasi database

```php
<?php

$hostname = "localhost";
$username = "root";
$password = "";
$database = "notesapp_db";
```

Kode di atas digunakan untuk menyimpan informasi yang diperlukan agar PHP dapat terhubung ke database MySQL.

`$hostname` berisi alamat server database. Karena database berjalan di komputer yang sama, kita menggunakan.

`$username` berisi nama pengguna MySQL Pada instalasi Laragon, secara default biasanya menggunakan username root.

`$password` digunakan untuk menyimpan password MySQL. Pada konfigurasi default Laragon, password biasanya masih kosong.

Nama database yang akan digunakan disimpan pada variabel `$database`

### Membuat Koneksi dengan `mysqli_connect()`

```php
$conn = mysqli_connect(
  $hostname,
  $username,
  $password,
  $database
);
```

`mysqli_connect()` digunakan untuk membuat koneksi antara PHP dengan server MySQL. Fungsi tersebut menerima beberapa informasi penting, yaitu: `Hostname`, `Username`, `Password`, `Nama Database`.

Hasil koneksi kemudian disimpan ke dalam variabel `$conn`. Variabel $conn nantinya akan digunakan ketika aplikasi menjalankan perintah SQL seperti `SELECT`, `INSERT`, `UPDATE`, `DELETE`.

### Mengecek Koneksi Database

```php
if (!$conn) {
  die("Koneksi database gagal: " . mysqli_connect_error());
}
```

Kode tersebut digunakan untuk mengecek apakah koneksi ke database berhasil atau tidak. Jika koneksi gagal, maka kode berikut akan dijalankan `die()`. Fungsi `mysqli_connect_error()` digunakan untuk mengambil informasi kesalahan ketika PHP gagal terhubung ke MySQL.

Contohnya jika nama database salah, aplikasi dapat menampilkan pesan seperti:

```
Unknown database 'notesapp_db'
```
