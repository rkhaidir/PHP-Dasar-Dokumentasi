# Cookie PHP

Cookie merupakan sebuah file text yang berisi data tertentu yang disimpan didalam browser.

Secara sederhana peran cookie ini hampir mirip dengan session, hanya saja kalau session itu disimpan di server, tapi kalau cookie ini disimpan di browser. 

## Perbedaan  Cookie dan Session

Sebelum kita membahas lebih detail mengenai cookie, kita akan bahas dulu apa perbedaan dari cookie dan session, perbedaannya antara lain :

|Cookie|Session|
|---|---|
|1. Cookie disimpan di sisi klien, lebih tepatnya di browser dari pengguna aplikasi |1. Session disimpan disisi server |
|2. Penggunaan Cookie tidak aman bagian klien, karena cookie disimpan di sisi klien (browser) sehingga memungkinkan klien (pengguna aplikasi) dapat menghapus mengedit serta melakukan disabled pada cookie. |2. Penyimpan data melalui session lebih aman karena data disimpan di sisi server, tidak seperti cookie yang datanya dimasukkan di sisi klien (browser) |
|3. Data yang disimpan di dalam cookie dapat disimpan lebih lama, karena waktu expired dari cookie dapat diatur. |3. Data Session otomatis terhapus ketika web browser klien dimatikan (diclose), selain itu data session tidak dapat diatur waktu expired. |

## Penggunaan Cookie

Coba perhatikan login pada facebook, atau web lain, biasanya terdapat checklist untuk mengingat password ( Remember Me ), nah jika ada menchecklist bagian itu, informasi akun anda akan disimpan di cookie browser, sehingga ketika anda membuka web tersebut akan otomatis melakukan login, meskipun browser sudah diclose sebelumnya.

Berbeda halnya jika anda tidak menchecklist bagian remember me, informasi akun anda hanya disimpan session, sehingga ketika browser di close dan anda masuk ke browser ulang untuk mengakses web, maka anda diharuskan untuk login ulang, karena data yang disimpan di session otomatis di hapus ketika browser pengguna (client) di tutup.

## Membuat Cookie di PHP

Untuk membuat cookie di php, anda perlu menggunakan fungsi ```setcookie()```, fungsi ini memiliki 7 argumen antara lain :
1. Nama Cookie : berisi nama dari cookie
2. Nilai Cookie : berisi nilai yang akan disimpan, sesuai nama cookie yang sudah ditulis di argumen pertama
3. Expire Time : berisi kapan waktu cookie berakhir, format waktu ini dapat berupa Unix Timestamp, sehingga anda dapat menggunakan fungsi time() di php, jika nilai expire dikosongkan atau bernilai 0, maka data cookie akan expire / dihapus ketika browser di tutup (sama seperti konsep session)
4. Path . Berisi Path / Lokasi server dimana cookie dapat digunakan, jika bagian path diisi tanda slash ‘/’, maka cookie dapat diakses diseluruh bagian website.
5. Domain dapat diisi subdomain yang dapat menggungkan cookie tersebut.
6. Secure : Secara Default akan bernilai false, jika anda mengganti nilainya menjadi true, maka browser akan mengirimkan cookie ke webserver hanya jika koneksinya https
7. HttpOnly : Secara Default akan bernilai false, Cookie hanya dapat diakses melalui protokol http

7 Argumen diatas seluruhnya tidak harus kita set saat menggunakan fungsi setcookie, biasanya yang digunakan adalah 4 argumen pertama, untuk argumen ke–5 (Domain) anda diharuskan menuliskan isinya dengan tanda dot (.), sehingga anda tidak bisa menggunakan nilai localhost untuk argumen ke–5.

Silahkan buat file dengan nama set_cookie.php, lalu isinya adalah seperti berikut ini :

```php
<?php
setcookie('username', 'administrator', time() + (60 * 60 * 24 * 5), '/');
setcookie('nama', 'dio tirta', time() + (60 * 60 * 24 * 15), '/');
?>
```

**Keterangan**
- Baris 2 digunakan untuk membuat cookie dengan nama username, dengan nilai "administrator" dengan waktu expire cookie selama 5 hari, dan dapat diakses diseluruh path dari dari direktori tempat menyimpan file php disimpan.
- Baris 3 digunakan untuk membuat cookie dengan nama nama, dengan nilai "Dio Tirta" dengan waktu expire cookie selama 15 hari, dan dapat diakses diseluruh path dari dari direktori tempat menyimpan file php disimpan.

### Perhitungan Waktu Expire Cookie
Perhitungan expire cookie pada baris code 2, (60 * 60 * 24 * 5) :

- 60 pertama adalah jumlah 60 detik yang artinya 1 menit
- 60 kedua adalah 60 menit yang artinya 1 jam
- 24 artinya 1 jam x 24 jadi hasilnya 24 jam atau 1 hari
- 5 artinya 24 jam x 5 jadi hasilnya 5 hari

## Membaca Data Cookie

Untuk dapat membaca data cookie gunakan variabel bawaan PHP yaitu $_COOKIE, variabel tersebut dapat diakses meskipun tidak terdapat cookie, hanya saja nilainya akan kosong jika belum ada cookie yang diset.

Kita akan membuat sebuah file php semisal namanya adalah get_cookie.php, dengan isi skrip sebagai berikut :

```php
<?php 
echo "Username ".$_COOKIE['username'];
echo "<br/>";
echo "Nama ".$_COOKIE['nama'];
?>
```