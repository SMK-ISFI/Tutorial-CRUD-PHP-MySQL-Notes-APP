# Latihan: Menambahkan Data Notes ke Database (Create)

Setelah berhasil menampilkan data dari database, langkah berikutnya adalah membuat fitur **Create**.
Pada latihan ini kita akan membuat halaman `create.php` yang berisi form untuk menambahkan catatan baru ke tabel `notes`.
Data yang akan dimasukkan adalah:

- `title`
- `body`

Sedangkan `id`, `createdAt`, dan `updatedAt` akan dibuat secara otomatis melalui kode dan database.

1.  Di dalam folder proyek `notes-app`, buat file baru `create.php` dan `create-process.php`

2.  Membuat Tampilan Form. Buka file `create.php` Kemudian tuliskan kode berikut:

    ```html
    <!doctype html>

    <html lang="id">
      <head>
        <meta charset="UTF-8" />

        <meta name="viewport" content="width=device-width, initial-scale=1.0" />

        <title>Tambah Note</title>

        <link
          href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
          rel="stylesheet"
        />
      </head>

      <body class="bg-light">
        <div class="container py-5">
          <div class="mb-4">
            <h1 class="fw-bold">Tambah Note</h1>

            <p class="text-secondary">Tambahkan catatan baru ke Notes App.</p>
          </div>

          <div class="card shadow-sm">
            <div class="card-body">
              <form action="create-process.php" method="POST">
                <div class="mb-3">
                  <label for="title" class="form-label"> Judul </label>

                  <input
                    type="text"
                    name="title"
                    id="title"
                    class="form-control"
                    placeholder="Masukkan judul catatan"
                    required
                  />
                </div>

                <div class="mb-3">
                  <label for="body" class="form-label"> Isi Catatan </label>

                  <textarea
                    name="body"
                    id="body"
                    class="form-control"
                    rows="5"
                    placeholder="Tuliskan isi catatan"
                    required
                  ></textarea>
                </div>

                <button type="submit" class="btn btn-primary">Simpan</button>

                <a href="index.php" class="btn btn-secondary"> Kembali </a>
              </form>
            </div>
          </div>
        </div>
      </body>
    </html>
    ```

3.  Buka file `create-process.php` Kemudian tuliskan:

    ```php
    require "connection.php";

    if ($_SERVER["METHOD_REQUEST"] === "POST") {
      $id = "note-" . random_int(10000000, 99999999);

      $title = $_POST["title"];
      $body = $_POST["body"];

      $createdAt = date("Y-m-d H:i:s");
      $updatedAt = date("Y-m-d H:i:s");

      $query = "INSERT INTO notes
                (id, title, body, createdAt, updatedAt)
                VALUES
                ('$id', '$title', '$body', '$createdAt', '$updatedAt')";

      mysqli_query($conn, $query);

      header("Location: index.php");

      exit;
    }
    ```

4.  Pada halaman `index.php`, tambahkan tombol untuk membuka halaman Create.

    ```html
    ....

    <div class="d-flex justify-content-between align-items-center mb-4">
      <div>
        <h1 class="fw-bold">Notes App</h1>

        <p class="text-secondary mb-0">Daftar catatan yang tersimpan.</p>
      </div>

      <a href="create.php" class="btn btn-primary"> Tambah Note </a>
    </div>

    ....
    ```

  </div>
    ```

## Bedah Kode

### Form Mengarah ke File Proses

```html
<form action="create-process.php" method="POST"></form>
```

menentukan file yang akan menerima dan memproses data dari form. Artinya, ketika tombol Simpan ditekan, data akan dikirim ke `create-process.php`. Sedangkan `method="POST"` berarti data dikirim menggunakan method POST.

### Input Judul dan Isi Catatan

```html
<input
  type="text"
  name="title"
  id="title"
  class="form-control"
  placeholder="Masukkan judul catatan"
  required
/>
```

Input ini digunakan untuk memasukkan judul catatan. Bagian yang sangat penting adalah `name="title"`, Nilai name digunakan sebagai nama data yang akan diterima oleh PHP. Nantinya dapat diambil menggunakan `$_POST["title"]`.

```html
<textarea
  name="body"
  id="body"
  class="form-control"
  rows="5"
  required
></textarea>
```

`textarea` digunakan untuk memasukkan teks yang lebih panjang. Bagian `name="body"` nantinya dapat diambil melalui `$_POST["body"]`

### Menghubungkan Database

`require "connection.php";` Kode tersebut digunakan untuk mengambil file koneksi database. Dengan begitu, variabel `$conn` dapat digunakan pada proses penyimpanan data.

### Membuat ID Note

```php
$id = "note-" . random_int(10000000, 99999999);
```

Kode tersebut digunakan untuk membuat ID unik untuk setiap catatan. Bagian `"note-"` merupakan awalan ID. Sedangkan `random_int(10000000, 99999999)` digunakan untuk membuat angka acak sebanyak 8 digit. Contoh hasil: `note-47291835`.

### Mengambil Data dari Form

```php
$title = $_POST["title"];
$body = $_POST["body"];
```

Variabel `$_POST` digunakan untuk mengambil data yang dikirim dari form. Bagian `$_POST["title"]` mengambil data dari `name="title"`. Sedangkan `$_POST["body"]` mengambil data dari `name="body"`.

### Membuat `createdAt`

```php
$createdAt = date("Y-m-d H:i:s");
```

Variabel `$createdAt` digunakan untuk menyimpan tanggal dan waktu ketika catatan dibuat. Format: `Y-m-d H:i:s`, Contoh: `2026-10-08 10:20:45`. memiliki arti:

```
Y = Tahun
m = Bulan
d = Tanggal
H = Jam
i = Menit
s = Detik
```

### Membuat Query INSERT

```php
$query = "INSERT INTO notes
          (id, title, body, createdAt, updatedAt)
          VALUES
          ('$id', '$title', '$body', '$createdAt', '$updatedAt')";
```

Bagian `INSERT INTO notes` berarti data akan dimasukkan ke tabel `notes`. Kolom yang akan diisi `(id, title, body, createdAt, updatedAt)`. Nilainya berasal dari:

```php
$id
$title
$body
$createdAt
$updatedAt
```

### Menjalankan Query

```php
mysqli_query($conn, $query);
```

Fungsi `mysqli_query()` digunakan untuk menjalankan perintah SQL.

### Kembali ke Halaman Utama

`header("Location: index.php");` Setelah data berhasil ditambahkan, pengguna akan diarahkan kembali ke `index.php`. Halaman `index.php` kemudian membaca kembali seluruh data sehingga note yang baru ditambahkan langsung tampil.
