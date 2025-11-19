# Lab8Web: Praktikum PHP dan Database MySQL (CRUD Sederhana)

Repository ini berisi hasil pengerjaan Modul Praktikum 8 Mata Kuliah Pemrograman Web, yang berfokus pada implementasi **CRUD (Create, Read, Update, Delete)** sederhana menggunakan bahasa pemrograman **PHP** dan database **MySQL**.

---

## 🛠️ Langkah-Langkah dan Implementasi

### 1. Persiapan Database (MySQL)

Langkah awal adalah menyiapkan database `latihan1` dan tabel `data_barang` menggunakan PHP MyAdmin.

#### A. SQL: Membuat Database dan Tabel

```sql
-- Membuat Database
CREATE DATABASE latihan1;

-- Membuat Tabel data_barang
CREATE TABLE data_barang (
    id_barang int(10) auto_increment Primary Key,
    kategori varchar(30),
    nama varchar(30),
    gambar varchar(100),
    harga_beli decimal(10,0),
    harga_jual decimal(10,0),
    stok int(4)
);
```

````

#### B. SQL: Menambahkan Data Awal

```sql
INSERT INTO data_barang (kategori, nama, gambar, harga_beli, harga_jual, stok)
 VALUES ('Elektronik', 'HP Samsung Android', 'hp_samsung.jpg', 2000000, 2400000,5),
 ('Elektronik', 'HP Xiaomi Android', 'hp_xiaomi.jpg', 1000000, 1400000, 5),
 ('Elektronik', 'HP OPPO Android', 'hp_oppo.jpg', 1800000, 2300000, 5);
```

**[Screenshot 1: Tampilan Tabel `data_barang` di PHPMyAdmin setelah diisi data awal]**

<img src="/docs/phpmyadmin.png" alt="Tampilan tabel data_barang di PHPMyAdmin"\>

---

### 2\. Implementasi Koneksi dan Read (Tampil Data)

#### A. File `koneksi.php`

Digunakan untuk membuat _connection string_ ke database `latihan1`.

```php
<?php
$host = "localhost";
// ... (variabel $user, $pass, $db)
$conn = mysqli_connect($host, $user, $pass, $db);
if ($conn == false)
{
    echo "Koneksi ke server gagal.";
    die();
}
?>
```

#### B. File `index.php` (READ)

File ini mengambil seluruh data dari tabel `data_barang` dan menampilkannya dalam format tabel HTML.

**[Screenshot 2: Tampilan `index.php` (Read)]**

\<img src="path/to/screenshot/index_read.png" alt="Tampilan halaman utama index.php"\>

---

### 3\. Implementasi Create (Tambah Data)

#### A. File `tambah.php`

File ini berisi form input dan logika PHP untuk memproses data yang dikirimkan, termasuk _upload_ gambar, lalu menjalankan _query_ `INSERT INTO`.

**[Screenshot 3: Tampilan Form `tambah.php` kosong]**

\<img src="path/to/screenshot/tambah_form.png" alt="Tampilan form tambah.php"\>

**[Screenshot 4: Tampilan `index.php` setelah berhasil menambah satu data baru]**

\<img src="path/to/screenshot/index_after_create.png" alt="Tampilan data baru di index.php"\>

---

### 4\. Implementasi Update (Ubah Data)

#### A. File `ubah.php`

File ini mengambil `id_barang` dari URL, menampilkan data lama di form, dan menjalankan _query_ `UPDATE` setelah form disubmit.

**[Screenshot 5: Tampilan Form `ubah.php` yang sudah terisi data lama]**

\<img src="path/to/screenshot/ubah_form.png" alt="Tampilan form ubah.php yang terisi data lama"\>

**[Screenshot 6: Tampilan `index.php` setelah data berhasil diubah]**

\<img src="path/to/screenshot/index_after_update.png" alt="Tampilan data di index.php setelah diubah"\>

---

### 5\. Implementasi Delete (Hapus Data)

#### A. File `hapus.php`

File ini menerima `id_barang` dari URL dan menjalankan _query_ `DELETE FROM` tanpa menampilkan _output_ HTML.

```php
<?php
// ...
$id = $_GET['id'];
$sql = "DELETE FROM data_barang WHERE id_barang = '{$id}'";
$result = mysqli_query($conn, $sql);
header('location: index.php');
?>
```

**[Screenshot 7: Tampilan konfirmasi sebelum penghapusan data]**

\<img src="path/to/screenshot/confirm_delete.png" alt="Dialog konfirmasi penghapusan data"\>

**[Screenshot 8: Tampilan `index.php` setelah data berhasil dihapus]**

\<img src="path/to/screenshot/index_after_delete.png" alt="Tampilan index.php setelah data dihapus"\>

---

## 📦 Struktur Direktori

```
lab8_php_database/
├── koneksi.php
├── index.php         // READ
├── tambah.php        // CREATE
├── ubah.php          // UPDATE
├── hapus.php         // DELETE
├── style.css         // Styling (Custom CSS)
└── gambar/           // Folder untuk menyimpan file gambar
```

```

```
````
