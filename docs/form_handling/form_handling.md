# Form Handling PHP

Pada PHP terdapat dua metode untuk melakukan pengiriman data yaitu GET dan POST


## GET 
Merupakan metode dimana nilai dikirimkan melalui alamat website atau URL. Dikarenakan nilai dikirim melalui URL, nilai dapat dirubah langsung dari URL pada Web Browser tanpa melalui Form yang disediakan.

**Contoh Metode GET**

```html
<form action="terima.php" method="GET">
    <label>Username</label>
    <input type="text" name="username"><br>
    <label>Password</label>
    <input type="password" name="password"><br>
    <input type="submit" value="Login">
</form>
```

Untuk mengambil nilai dari metode GET dengan menggunakan global variabel ```$_GET```.

```php
<?php
$username = $_GET['username'];
$password = $_GET['password'];

echo "Username anda : $username";
echo "Password anda : $password";
```

## POST
Merupakan metode dimana nilai dikirimkan secara terpisah dari alamat Website. Nilai tidak dapat dirubah tanpa melalui form yang telah disediakan.

**Contoh Metode POST**

```html
<form action="terima.php" method="POST">
    <label>Username</label>
    <input type="text" name="username"><br>
    <label>Password</label>
    <input type="password" name="password"><br>
    <input type="submit" value="Login">
</form>
```

Untuk mengambil nilai dari metode POST dengan menggunakan global variabel ```$_POST```.

```php
<?php
$username = $_POST['username'];
$password = $_POST['password'];

echo "Username anda : $username";
echo "Password anda : $password";
```