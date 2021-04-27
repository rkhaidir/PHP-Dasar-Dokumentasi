# CRUD PHP MYSQL BAGIAN 1

Setelah kita belajar dasar-dasar dari bahasa pemrograman PHP, kali ini kita akan menerapkan untuk membuat sebuah aplikasi sederhana menggunakan database mysql yang menerapkan konsep CRUD yaitu ***create***, ***read***, ***update***, dan ***delate***. Adapun pengertian dari istilah di atas sebagai berikut:
- ***create***, menambahkan data ke database
- ***read***, mengambil data dari database dan menampilkannya
- ***update***, mengubah data dari database
- ***delete***, menghapus data dari databse

## Persiapan awal

Adapun persiapan awal sebelum kita membuat CRUD yaitu menyiapkan struktru folder di ```htdocs``` sebagai berikut.

```
CRUD_PHP
|--koneksi.php
|--index.php
|--tambah.php
|--tambah_proses.php
|--edit.php
|--edit_proses.php
|--hapus.php
```

Setelah kita membuat struktur folder selanjutnya kita membuat database dengan aturan sebagai berikut
1. nama database ```db_crud```

```sql
CREATE DATABASE db_crud
```

2. buat tabel di dalam database dengan nama ```tb_karyawan``` dengan kolomnya yaitu id, nama, alamat, email

```sql
CREATE TABLE tb_karyawan (
  'id' int(11) NOT NULL AUTO_INCREMENT,
  'nama' varchar(32) NOT NULL,
  'alamat' varchar(64) NOT NULL,
  'email' varchar(64) NOT NULL,
  PRIMARY KEY('id')
);
```
**Keterangan**
pertama kita membuat table dengan nama ```tb_karyawan```, selanjutnya kita membuat kolom ```id``` dengan tipe ```int``` (integer) dengan panjang karakter 11, Not Null yang artinya tidak boleh kosong serta AUTO_INCREMENT yang dimana nanti akan terisi otomatis dari 1 sampai seterusnya saat kita menambahkan data ke database.

selanjutnya terdapat kolom ```nama```, ```alamat```, ```email``` yang tipenya varchar (bisa memuat huruf, angka, simbol yang ada dikeyboard) dengan panjang karakter masing-masing, ```nama``` 32 karakter, ```alamat``` 64 karakter, ```email``` 64 karakter, serta diberikan not null (tidak boleh kosong)

dibagian akhir kita set ```id``` sebagai ```primary key``` (menjadi bagian unik dari setiap data).

3. kita isi data di database secara manual melalui database sebagai berikut.

```sql
INSERT INTO tb_karyawan('nama', 'alamat', 'email') VALUES 
('Ilham', 'Jl Bali No. 24', 'ilham@yahoo.com'),
('Akbar', 'Jln A Yani No. 100', 'akbar@hotmail.com'),
('Aldi', 'Jln Sultan Adam No. 30', 'aldi@gmail.com');
```

Jalankan query tersebut data akan otomatis tertambah di tb_karyawan.

Sampai disini dulu bagian satu membuat CRUD menggunakan PHP dan MYSQL selanjutkan kita akan mebuat tampilan menggunakan html dan css serta menampilkan data dari database yang sudah kita buat.


