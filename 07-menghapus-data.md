# Latihan: Menghapus Data Notes (Delete)

Setelah fitur Create, Read, Detail, dan Update selesai, langkah berikutnya adalah membuat fitur Delete.

1. Buat file baru di dalam folder proyek: `delete-process.php`

2. Tambahkan Form Hapus pada `index.php`. Pada setiap card note, tambahkan form berikut:

   ```html
   <form action="delete-process.php" method="POST" class="d-inline">
     <input type="hidden" name="id" value="<?= $note["id"]; ?>">

     <button type="submit" class="btn btn-danger">
         Hapus
     </button>
   </form>
   ```

3. Buka file `delete-process.php` Kemudian tuliskan:

   ```php
   <?php

   require "connection.php";

   if ($_SERVER["METHOD_REQUEST"] === "POST") {
      $id = $_POST["id"];
      $query = "DELETE FROM notes WHERE id = '$id'";
      mysqli_query($conn, $query);
      header("Location: index.php");
      exit;
   }
   ?>
   ```

## Bedah Kode

### Membuat Query DELETE

```php
$query = "DELETE FROM notes WHERE id = '$id'";
```

Perintah `DELETE FROM notes` digunakan untuk menghapus data dari tabel notes. Sedangkan `WHERE id = '$id'` digunakan untuk menentukan data yang akan dihapus.
