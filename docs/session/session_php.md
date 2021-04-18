# Session PHP

Session pada PHP merupakan data yang disimpan di sebuah server dan dapat digunakan / diakses secara global di server tersebut.

Session yang sering digunakan  untuk pembuatan fitur login, session digunakan untuk menyimpan data user yang sedang login, sehingga jika ada halaman pada aplikasi yang mengharuskan pengguna login, anda hanya perlu login sekali, dan data login tersebut akan disimpan di session, data session ini yang akan diperiksa oleh setiap halaman yang memerlukan authentikasi login user, contohnya pada aplikasi social media atau email anda.

Cara penggunaan session pada PHP

Untuk memulai Session di PHP anda dapat menggunakan function ```session_start()```.

Baik dalam contoh kita akan membuat sebuah file dengan nama ```set_session.php```, lalu tuliskan skrip seperti dibawah ini :

```php
<?php
session_start();
$_SESSION['username'] = "administrator";
$_SESSION['password'] = "12abc456";
?>
```

**Keterangan**
- Pada Line 2 kita menuliskan function session_start(); function ini digunakan untuk melakukan start pada session.
- Variabel session telah diset sebagai variabel global di PHP yaitu $_SESSION, sehingga untuk membuat session kita perlu menyimpannya di variabel $_SESSION.
- Pada Line 3 kita menuliskan ```$_SESSION['username'] = "administrator";``` yang artinya kita akan membuat session dengan nama “username” dengan nilai "administrator".
- Pada Line 4 kita menuliskan ```$_SESSION['password'] = "12abc456";``` yang artinya kita akan membuat session dengan nama “password” dengan nilai "12abc456"
- sehingga saat file set_session.php dijalankan akan maka akan membuat session dengan nama username dengan nilai "administrator" dan session dengan nama password dengan nilai "12abc456", session tersebut disimpan di server.

Berikutnya setelah anda belajar membuat,  berikutnya kita akan belajar bagaimana cara menghapus data session.

Silahkan buat file dengan nama ```delete_session.php```
lalu tuliskan skrip seperti dibawah ini :

```php
<?php

<?php 
session_start();
session_unset();
session_destroy();
?>
```

**Keterangan**

- Sebelum kita menghapus session kita perlu memanggil perintah ```session_start();```
- Pada Line 3 kita menuliskan ```session_unset();``` perintah ini digunakan untuk menghapus seluruh nama variabel session yang ada.
- Pada Line 4 kita menuliskan ```session_destroy();``` perintah ini digunakan untuk menghancurkan session yang ada.