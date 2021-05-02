# CRUD PHP MYSQL BAGIAN 2

Pada materi sebelumnya kita telah membuat database untuk tempat penyimpanan data. Selanjutnya kita akan menampilkan data tersebut ke halaman web. Adapun kita akan menggunakan HTML untuk mengatur tampilan, dan PHP sebagai penghubung ke server dan database.

Langkah-langkahnya sebagai berikut.

1. Membuat koneksi ke database. Buat sebuah file dengan nama koneksi.php lalu tuliskan kode berikut.

```php
<?php
$con = mysqli_connect('localhost', 'root', '', 'db_crud');
?>
```

Pada kode di atas kita membuat sebuah variabel dengan nama ```$con``` yang artinya koneksi yang menampung entitas koneksi ke database, yang mana memanggil fungsi ```mysqli_connect()```. Fungsi ```mysqli_connect()``` memiliki 4 buah parameter yang wajib diisi yaitu hostname kedatabase, username, password, dan nama database.

Untuk hostname kedatabasenya kita isi dengan **localhost** karena kita menjalakan dilocal komputer kita, untuk usernamenya kita isikan sebagai **root**, passwordnya kita isi sebagai kosong karena kita masuk sebagai **root**, dan nama databasenya kita isi **db_crud** berdasarkan dari nama database yang kita buat sebelumnya.

2. Membuat tampilan awal halaman ```index.php``` yang akan terdapat sebuah table. adapun kode programnya dan tampilannya sebagai.

```html
<!DOCTYPE html>
<html>
<head>
	<title></title>
</head>
<body>
	<table border="1">
		<thead>
			<tr>
				<th>No</th>
				<th>Nama</th>
        <th>Alamat</th>
				<th>Email</th>
				<th>Aksi</th>
			</tr>
		</thead>
		<tbody>
			
		</tbody>
	</table>
</body>
</html>
```

Adapun tampilannya saat kita jalankan sebagai berikut.

![https://i.ibb.co/W06f96x/image.png](https://i.ibb.co/W06f96x/image.png)

2. Memasukkan file koneksi.php ke halaman index.php dengan fungsi require_once penjelasannya dapat kalian baca [disini](../include_require/include_require.md)

```php
<?php
require_once 'koneksi.php';
?>
<!DOCTYPE html>
<html>
<head>
	<title></title>
</head>
<body>
	<table border="1">
		<thead>
			<tr>
				<th>No</th>
				<th>Nama</th>
        <th>Alamat</th>
				<th>Email</th>
				<th>Aksi</th>
			</tr>
		</thead>
		<tbody>
			
		</tbody>
	</table>
</body>
</html>
```

3. Setelah kita memasukkan file koneksi.php kita dapat melakukan query SELECT untuk mengambil data kedatabase menggunakan fungsi ```mysqli_query()```. Fungsi ```mysqli_query()``` memliki dua parameter yang wajib diisi yaitu koneksi dan query. Untuk koneksi kita isi dengan variabel ```$con``` yang kita ambil dari file koneksi.php, query kita isi dengan query SELECT, kode programnya sebagai berikut.

```php
<?php
require_once 'koneksi.php';
$query = mysqli_query($con, "SELECT * FROM tb_karyawan");
?>
<html>
....
</html>
```

Pada paramenter query kita isi dengan ```SELECT * FROM tb_karyawan``` yang dimana kita mengambil data ke tabel **tb_karyawan** yang ada pada database. Hasil query tersebut kita tampung ke dalam variabel ```$query```.

3. Setelah kita melakukan query kita akan tampilkan data tersebut ke halaman web. Untuk kode program sebagai berikut.

```php
<?php
require_once 'koneksi.php';
$query = mysqli_query($con, "SELECT * FROM tb_karyawan");
?>
<!DOCTYPE html>
<html>
<head>
	<title></title>
</head>
<body>
	<table border="1">
		<thead>
			<tr>
				<th>No</th>
				<th>Nama</th>
				<th>Alamat</th>
				<th>Email</th>
				<th>Aksi</th>
			</tr>
		</thead>
		<tbody>
			<?php
      $no = 1;
			while($data = mysqli_fetch_array($query)) {
				echo "
				<tr>
					<td>$no</td>
					<td>$data[nama]</td>
					<td>$data[alamat]</td>
					<td>$data[email]</td>
				</tr>	
				";
				$no++
			}
      ?>
		</tbody>
	</table>
</body>
</html>
```

Kita menggunakan fungsi ```mysqli_fetch_array()``` untuk mengubah data hasil query ke dalam bentuk array. Setelah itu kita lakukan perulangan menggunakan perulangan **while** untuk menampilkan data yang ditampung di dalam variabel ```$data```

Adapun untuk tampilan di halaman web sebagai berikut.

![https://i.ibb.co/gS7Ymqm/image.png](https://i.ibb.co/gS7Ymqm/image.png)

Kita dapat mempercantik tampilan dengan menggunakan CSS. Pertama kita buat file ```style.css``` lalu kita masukkan dibagian head pada file ```index.php```

```html
<!DOCTYPE html>
<html>
<head>
	<title></title>
  <link rel="stylesheet" href="style.css">
</head>
````

Untuk kode css sebagai berikut.

```css
body {
  font-family: 'Arial', sans-serif;
}
table {
  border-collapse: collapse;
  margin: 25px 0;
  font-size: 0.9em;
  font-family: sans-serif;
  min-width: 100%;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.15);
}
table thead tr {
  background-color: #009879;
  color: #ffffff;
  text-align: left;
}
table th,
table td {
  padding: 12px 15px;
}
```

Adapun tampilan web setelah diberi css sebagai berikut.

![https://i.ibb.co/kgszpNh/image.png](https://i.ibb.co/kgszpNh/image.png)