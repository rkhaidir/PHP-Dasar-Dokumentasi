# CRUD PHP MYSQL BAGIAN 3

Pada materi sebelumnya kita telah menampilkan data dari database ke halaman web. Selanjutnya kita akan menambahkan data ke database melalui halaman web. 

Pertama kita buat sebuah tombol di halaman index.php untuk berpindah halaman ke halaman tambah.php, sebagai berikut.

```php
<body>
	<a href="tambah.php" class="btn btn-primary">Tambah Data</a>
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
					<td></td>
				</tr>	
				";
				$no++;
			}
			?>
		</tbody>
	</table>
</body>
```

lalu kita berikan css agar terlihat bagus.

```css
.btn {
	background-color: #fff;
  	border: 2px solid #009879;
  	color: #000;
  	padding: 10px 25px;
  	text-align: center;
  	text-decoration: none;
  	display: inline-block;
  	font-size: 16px;
  	box-shadow: 0 0 20px rgba(0, 0, 0, 0.15);
}
.btn:hover {
	background-color: #009879;
	color: #fff;
}
```

Kedua kita buat file tambah.php dan isinya sebagai berikut.

```html
<!DOCTYPE html>
<html>
<head>
	<title></title>
</head>
<body>
	<h1>Tambah Data Siswa</h1>
  <form action="tambah_proses.php" method="POST">
    <div>
      <label>NAMA SISWA</label>
      <input type="text" name="nama" class="form-control" required>
    </div>
    <div>
      <label>ALAMAT SISWA</label>
      <textarea name="alamat" class="form-control" required></textarea>
    </div>
    <div>
      <label>EMAIL SISWA</label>
      <input type="text" name="email" class="form-control" required>
    </div>
    <input type="submit" name="simpan" value="Simpan" class="btn">
  </form>
</body>
</html>
```

Adapun untuk tampilannya sebagai berikut

![img](https://i.ibb.co/k30Hvg1/image.png)

Agar terlihat lebih bagus masukkan file style.css ke halaman tambah.php di bagian head.

```html
<!DOCTYPE html>
<html>
<head>
	<title>Tambah Data Siswa</title>
  <link rel="stylesheet" href="style.css">
</head>
```

Lalu tambahkan css berikut di file style.css

```css
label {
	font-size: 11pt;
	font-weight: bold;
}
.form-control {
	box-sizing: border-box;
	width: 100%;
	padding: 10px;
	font-size: 11pt;
	margin-bottom: 20px;
	border: 1px solid grey;
	border-radius: 5px;
}
```

Maka tampilannya akan seperti berikut

![img](https://i.ibb.co/LrHJWJ8/image.png)

Selanjutkan kita buat logika penyimpanan ke database. pertama buat file tambah_proses.php lalu tuliskan kode berikut.

```php
<?php
// memasukkan file koneksi
require_once 'koneksi.php';

if(isset($_POST['simpan'])) 
{
	// mengambil nilai dari inputan
	$name 		= $_POST['nama'];
	$address 	= $_POST['alamat'];
	$email 		= $_POST['email'];

	// mengeksekusi kueri insert dengan menyimpan data berdasarkan nilai dari inputan
	$query = mysqli_query($con, "INSERT INTO tb_karyawan SET 
		nama 		= '$name',
		alamat		= '$address',
		email 		= '$email'
	");

	
	if($query) 
	{
		echo "<script>alert('Data Berhasil Diinput');window.location='index.php'; </script>";
	}
	else
	{
		echo "<script>alert('Data Gagal Diinput');window.location='tambah.php'; </script>";
	}
}
```

Silahkan lakukan uji coba penyimpanan ke database melalui halaman web.