# Function pada PHP

Function adalah sekumpulan pernyataan yang dapat digunakan berulang kali dalam suatu program. Suatu function tidak akan dijalankan secara otomatis saat halaman dimuat.  

Di dalam function terdapat sekumpulan intruksi yang dibungkus dalam sebuah blok. Function dapat digunakan ulang tanpa harus menulis ulang instruksi di dalamnya.

Function pada PHP dapat dibuat dngan kata kunci function, lalu diikuti dengan nama fungsinya.

**Syntax**
```
function [nama_function]() {
    // kode yang akan dieksekusi
}
```

**Contoh**
```php
<?php
function perkenalan(){
    echo "Perkenalkan, nama saya Ardianta<br/>";
    echo "Senang berkenalan dengan anda<br/>";
}
```

Function yang sudah dibuat tidak akan menghasilkan apapun kalau tidak dipanggil. Kita dapat memanggil function dengan menuliskan namanya.

```php
<?php
perkenalan();
```

untuk kode lengkapnya sebagai berikut
```php
<?php
// membuat function
function perkenalan(){
    echo "Perkenalkan, nama saya Ardianta<br/>";
    echo "Senang berkenalan dengan anda<br/>";
}

// memanggil function
perkenalan();
```

**Output**
```
Perkenalkan, nama saya Ardianta
Senang berkenalan dengan anda
```

## Function dengan Parameter

Supaya intruksi yang di dalam function lebih dinamis, kita dapat menggunakan parameter untuk memasukkan sebuah nilai ke dalam function. Nilai tersebut akan diolah di dalam function.

Misalkan, pada contoh fungsi yang tadi, tidak mungkin nama yang dicetak adalah ardianta saja. Maka, kita dapat menambahkan parameter menjadi seperti ini:

```php
<?php
// membuat function
function perkenalan($nama){
    echo "Perkenalkan, nama saya $nama<br/>";
    echo "Senang berkenalan dengan anda<br/>";
}

// memanggil function
perkenalan("Muhardian");

echo "<hr>";
$saya = "Akbar";
// memanggil function
perkenalan($saya);
```

**Output**
```
Perkenalkan, nama saya Muhardian
Senang berkenalan dengan anda
______________________________________________
Perkenalkan, nama saya Akbar
Senang berkenalan dengan anda
```

## Parameter dengan Nilai Default

Nilai default dapat kita berikan di parameter. Nilai default berfungsi untuk mengisi nilai sebuah parameter, kalau parameter tersebut tidak diisi nilainya.

Misalnya: saya lupa mengisi parameter salam, maka program akan error. Oleh karena itu, kita perlu memberikan nilai default supaya tidak error.

```php
<?php
// mmbuat fungsi
function perkenalan($nama, $salam="Assalamualaikum"){
  echo "$salam, <br/>";
  echo "Perkenalkan, nama saya $nama<br/>";
  echo "Senang berkenalan dengan anda<br/>";
}

// memanggil fungsi yang sudah dibuat
perkenalan("Muhardian", "Hi");

echo "<hr>";

$saya = "Indry";
$ucapanSalam = "Selamat pagi";
// memanggilnya lagi tanpa mengisi parameter salam
perkenalan($saya);
```
**Output**
```
Hi
Perkenalkan, nama saya Muhardian
Senang berkenalan dengan anda
______________________________________________
Assalamualaikum
Perkenalkan, nama saya Akbar
Senang berkenalan dengan anda
```

## Function yang Mengembalikan Nilai

Hasil pengolahan nilai dari function mungkin saja kita butuhkan untuk pemrosesan berikutnya. Oleh karena itu, kita harus membuat fungsi yang dapat mengembalikan nilai.

Pengembalian nilai dalam fungsi dapat menggunakan kata kunci return.

```php
<?php
// membuat fungsi
function hitungUmur($thn_lahir, $thn_sekarang){
  $umur = $thn_sekarang - $thn_lahir;
  return $umur;
}

echo "Umur saya adalah ". hitungUmur(1994, 2015) ." tahun";
```
**Output**
```
Umur saya adalah 21 tahun
```