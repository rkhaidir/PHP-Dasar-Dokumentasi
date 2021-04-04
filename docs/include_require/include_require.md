# Include dan Require

Pada PHP terdapat dua fungsi untuk melakukan modularitas perintah pada beberapa halaman. Kedua fungsi tersebut ```include()``` dan ```require()```, dengan kedua fungsi tersebut kita dapat menyisipkan file PHP ke file PHP lainnya. Adapun dengan penggunaan fungsi tersebut kita tidak perlu menuliskan kode berulang-ulang.

## Include

Adapun fungsi **include** terbagi dua yaitu  ```include()``` dan  ```include_once()```. Untuk perbedaan kedua fungsi tersebut adalah ```include()``` untuk menggabungkan beberapa file kode menjadi satu kesatuan kode sedangkan ```include_once()``` untuk menggabungkan beberapa file dengan ketentuan satu file hanya dapat digabungkan satu kali.

Contoh penulisan ```include()``` dan ```include_once()``` sebagai berikut.

**Contoh INCLUDE**
```php
<?php
// Contoh penulisan include jenis 1
include('koneksi.php');

// Contoh penulisan include jenis 2
include 'koneksi.php';
```

**CONTOH INCLUDE_ONCE**
```php
<?php
// Contoh penulisan include jenis 1
include_once('koneksi.php');

// Contoh penulisan include jenis 2
include_once 'koneksi.php';
```

# Require

Sama halnya seperti **include** untuk **require** terbagi dua yaitu  ```require()``` dan  ```require_once()```. Adapun perbedaan kedua fungsi tersebut adalah ```require()``` untuk menggabungkan beberapa file menjadi satu kesatuan kode, ketika terjadi error pembacaan kode dihentikan, sedangkan ```require_once()``` memiliki kegunaan yang sama seperti require, dengan ketentuan yan sama seperti include_once.

Contoh penulisan ```require()``` dan ```require_once()``` sebagai berikut.

**Contoh REQUIRE**
```php
<?php
// Contoh penulisan include jenis 1
require('koneksi.php');

// Contoh penulisan include jenis 2
require 'koneksi.php';
```

**CONTOH REQUIRE_ONCE**
```php
<?php
// Contoh penulisan include jenis 1
require_once('koneksi.php');

// Contoh penulisan include jenis 2
require_once 'koneksi.php';
```

## Contoh Penerapan Include dan Require

**index.php**

```php
<?php
// menyisipkan file php dengan include
include 'tes.php';

// syntax di bawah ini merupakan bagian dari file index.php
echo 'Belajar Include() dan Require()';
```

**tes.php**
```php
<?php
echo " ISI FILE TES.PHP <br>";
```

**Output**
```
ISI FILE TES.PHP

Belajar Include() dan Require();
```