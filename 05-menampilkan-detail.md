# Latihan: Menampilkan Detail Data Notes

Setelah berhasil membuat fitur Read dan Create, langkah berikutnya adalah membuat halaman Detail Note. Pada latihan ini, kita akan membuat file `show.php` untuk menampilkan satu catatan berdasarkan `id`.

Contohnya, ketika pengguna memilih catatan dengan ID: `note-12345678`.

maka halaman detail akan dibuka melalui URL: `show.php?id=note-12345678`

1.  Di dalam folder proyek `notes-app`, buat file baru `show.php`.

2.  Agar pengguna dapat membuka halaman detail, tambahkan tombol pada setiap card. Pada bagian card di `index.php`, tambahkan:

    ```php
    <a href="show.php?id=<?= $note["id"]; ?>" class="btn btn-outline-primary">
        Detail
    </a>
    ```

    Contoh bagian card menjadi:

    ```html
    <div class="card mb-3 shadow-sm">
      <div class="card-body">

        <h5 class="card-title">
          <?= htmlspecialchars($note["title"]); ?>
        </h5>

        <p class="card-text">
          <?= htmlspecialchars($note["body"]); ?>
        </p>

        <small class="text-secondary d-block mb-3">
          Dibuat:
          <?= $note["createdAt"]; ?>
        </small>

        <a href="show.php?id=<?= $note["id"]; ?>" class="btn btn-outline-primary">
          Detail
        </a>

      </div>
    </div>
    ```

3.  Sekarang buka file `show.php`. Pertama, hubungkan file dengan database. Kemudian ambil nilai `id` dari URL.

    ```php
    <?php

    require "connection.php";

    $id = $_GET["id"];
    ```

4.  Mengambil Satu Data Berdasarkan ID, Buat query Lalu jalankan `mysqli_query()`.

    ```php
    <?php

    require "connection.php";
    $id = $_GET["id"];

    $query = "SELECT * FROM notes WHERE id = '$id'";
    $result = mysqli_query($conn, $query);
    $note = mysqli_fetch_assoc($result);

    ?>
    ```

5.  Setelah data berhasil diambil, buat tampilan menggunakan Bootstrap. Lengkapi kode di `show.php`

    ```html
    <?php
    ...
    ?>
    <!doctype html>
    <html lang="id">
      <head>
        <meta charset="UTF-8" />

        <meta name="viewport" content="width=device-width, initial-scale=1.0" />

        <title>Detail Note</title>

        <link
          href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
          rel="stylesheet"
        />
      </head>

      <body class="bg-light">
        <div class="container py-5">
          <div class="mb-4">
            <h1 class="fw-bold">Detail Note</h1>

            <p class="text-secondary">Informasi lengkap catatan.</p>
          </div>

          <?php if ($note) : ?>

          <div class="card shadow-sm">
            <div class="card-body">
              <h2 class="card-title mb-3">
                <?= htmlspecialchars($note["title"]); ?>
              </h2>

              <p class="card-text">
                <?= nl2br(htmlspecialchars($note["body"])); ?>
              </p>

              <hr />

              <div class="text-secondary">
                <p class="mb-1">
                  <strong>ID:</strong>
                  <?= $note["id"]; ?>
                </p>

                <p class="mb-1">
                  <strong>Dibuat:</strong>
                  <?= $note["createdAt"]; ?>
                </p>

                <p class="mb-0">
                  <strong>Diperbarui:</strong>
                  <?= $note["updatedAt"]; ?>
                </p>
              </div>
            </div>
          </div>

          <div class="mt-3">
            <a href="index.php" class="btn btn-secondary"> Kembali </a>
          </div>

          <?php else : ?>

          <div class="alert alert-warning">Data note tidak ditemukan.</div>

          <a href="index.php" class="btn btn-secondary"> Kembali </a>

          <?php endif; ?>
        </div>
      </body>
    </html>
    ```

## Bedah Kode

### Mengirim ID Melalui URL

Pada `index.php` terdapat:

```php
href="show.php?id=<?= $note["id"]; ?>"
```

Kode tersebut digunakan untuk mengirim ID note melalui URL. maka URL yang terbentuk adalah: `show.php?id=note-12345678`.

### Mengambil ID dengan `$_GET`

Di dalam `show.php` terdapat `$id = $_GET["id"];`. `$_GET` digunakan untuk mengambil data yang dikirim melalui URL. Jika URL `show.php?id=note-12345678`.

### Membuat Query Berdasarkan ID

```php
$query = "SELECT * FROM notes WHERE id = '$id'";
```

Query ini digunakan untuk mengambil satu data tertentu.

## [Selanjutnya: Mengubah Data](/06-mengubah-data.mdd)
