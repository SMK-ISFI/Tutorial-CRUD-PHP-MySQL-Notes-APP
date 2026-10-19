# Latihan: Mengubah Data Notes (Update)

Setelah berhasil membuat fitur Create, Read, dan Detail, langkah berikutnya adalah membuat fitur Update.

1. Di dalam folder notes-app, buat dua file baru

   ```
   edit.php
   edit-process.php
   ```

2. Tambahkan tombol Edit pada card di `index.php`.

   ```html
   <a href="edit.php?id=<?= $note["id"]; ?>" class="btn btn-warning">
     Edit
   </a>
   ```

3. Buka file `edit.php` Hubungkan dengan database dan ambil ID dari URL.

   ```php
   <?php

   require "connection.php";

   $id = $_GET["id"];
   $query = "SELECT * FROM notes WHERE id = '$id'";
   $result = mysqli_query($conn, $query);
   $note = mysqli_fetch_assoc($result);

   ?>
   ```

   Kode tersebut digunakan untuk mengambil data lama berdasarkan ID.

4. Membuat Form Edit, Lengkap `edit.php`

   ```html
   <?php
   ...
   ?>
   <!doctype html>
   <html lang="id">
   <head>
       <meta charset="UTF-8">

       <meta
           name="viewport"
           content="width=device-width, initial-scale=1.0"
       >

       <title>Edit Note</title>

       <link
           href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
           rel="stylesheet"
       >
   </head>

   <body class="bg-light">

       <div class="container py-5">

           <div class="mb-4">
               <h1 class="fw-bold">
                   Edit Note
               </h1>

               <p class="text-secondary">
                   Ubah data catatan yang sudah tersimpan.
               </p>
           </div>

           <?php if ($note) : ?>

               <div class="card shadow-sm">
                   <div class="card-body">

                       <form
                           action="edit-process.php"
                           method="POST"
                       >

                           <input
                               type="hidden"
                               name="id"
                               value="<?= $note["id"]; ?>"
                           >

                           <div class="mb-3">
                               <label
                                   for="title"
                                   class="form-label"
                               >
                                   Judul
                               </label>

                               <input
                                   type="text"
                                   name="title"
                                   id="title"
                                   class="form-control"
                                   value="<?= htmlspecialchars($note["title"]); ?>"
                                   required
                               >
                           </div>

                           <div class="mb-3">
                               <label
                                   for="body"
                                   class="form-label"
                               >
                                   Isi Catatan
                               </label>

                               <textarea
                                   name="body"
                                   id="body"
                                   class="form-control"
                                   rows="5"
                                   required
                               ><?= htmlspecialchars($note["body"]); ?></textarea>
                           </div>

                           <button
                               type="submit"
                               class="btn btn-primary"
                           >
                               Simpan Perubahan
                           </button>

                           <a
                               href="index.php"
                               class="btn btn-secondary"
                           >
                               Kembali
                           </a>

                       </form>

                   </div>
               </div>

           <?php else : ?>

               <div class="alert alert-warning">
                   Data note tidak ditemukan.
               </div>

               <a
                   href="index.php"
                   class="btn btn-secondary"
               >
                   Kembali
               </a>

           <?php endif; ?>

       </div>

   </body>
   </html>
   ```

5. Buka file `edit-process.php` Kemudian tuliskan

   ```php
   <?php

   require "connection.php";
   if ($_SERVER["METHOD_REQUEST"] === "POST") {
       $id = $_POST["id"];
       $title = $_POST["title"];
       $body = $_POST["body"];

       $updatedAt = date("Y-m-d H:i:s");

       $query = "UPDATE notes
                   SET
                       title = '$title',
                       body = '$body',
                       updatedAt = '$updatedAt'
                   WHERE id = '$id'";
       mysqli_query($conn, $query);

       header("Location: index.php");
       exit;
   }
   ?>
   ```

### Bedah Kode

### Membuat Query UPDATE

```php
$query = "UPDATE notes
          SET
              title = '$title',
              body = '$body',
              updatedAt = '$updatedAt'
          WHERE id = '$id'";
```

Perintah `UPDATE notes` berarti kita akan mengubah data pada tabel notes. Bagian `SET` digunakan untuk menentukan kolom yang akan diperbarui. Dalam kasus ini

```
title
body
updatedAt
```

Sedangkan `WHERE id = '$id'` digunakan untuk menentukan data yang akan diperbarui.

---

## [Selanjutnya: Menghapus Data](/07-menghapus-data.md)
