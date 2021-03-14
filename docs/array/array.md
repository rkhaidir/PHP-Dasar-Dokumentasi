# Array PHP

Array adalah salah satu struktur data yang berisi sekumpulan data dan memiliki indeks. Indeks digunakan untuk mengakses nilai array. Indeks array selalu dimulai dari **0**.

**Contoh**

| "Asus" | "Acer" | "Lenovo" |
| ------ | ------ | -------- |
|  0 | 1 | 2 | 

Jadi apabila kita ingin menampilkan "Asus", maka kita harus mengambil indeks ke-0.

## Membuat Array pada PHP

Array pada PHP dapat kita buat dengan fungsi ```array()``` dan tanda kurung kotak ```[]```.

**Contoh:**
```php
<?php
// membuat array kosong
$buah = array();
$hewan = [];

// membuat array dengan mengisinya
$makanan = array("Soto", "Sate", "Mie Goreng", "Bubur");
$minuman = ["Teh", "Susu", "Jus Jeruk", "Kopi"];
```

Array dapat kita isi dengan berbagai tipe data, bahkan dapat dicampur

**Contoh:**
```php
<?php
$arr = ["Apel", 2, 3.14, true];
```

## Menampilkan Isi Array

Untuk menampilkan isi array, kita bisa mengaksesnya melalui indeks.

**Contoh:**
```php
<?php
// membuat array
$makanan = ["Soto", "Sate", "Bubur"];

// menampilkan isi array
echo $makanan[0]."<br>";
echo $makanan[1]."<br>";
echo $makanan[2]."<br>";
```

**Output**
```
Soto
Sate
Bubur
```

Tapi cara di atas kurang efektif, karena kita mencetaknya satu persatu. Apabila datanya ada 1000, kita akan mengetikan echo sebanyak 1000 kali. Untuk mengatasinya kita gunakan perulangan.

**Contoh**
```php
<?php
// membuat array
$makanan = ["Soto", "Sate", "Bubur"];

// menampilkan array dengan perulangan for
for($i=0; $i<count($makanan); $i++) {
    echo $makanan[$i]."<br>";
}
```

Kita menggunakan fungsi ```count()``` untuk menghitung isi array. Untuk outputnya sebagai berikut.

**Output**
```
Soto
Sate
Bubur
```

## Menambah Isi Array

Ada dua cara untuk menambah isi array

1. mengisi dinomor indeks yang diinginkan
2. mengisi indeks paling terakhir

Untuk contoh sebagai berikut:

**Contoh**

```php
<?php
// membuat array
$makanan = ["Soto", "Sate", "Bubur"];

// menambahkan array pada indeks ke-1
$makanan[3] = "Nasi Goreng";

// menambahkan array pada indeks terakhir
$makanan[] = "Ayam Goreng";
```

Apabila kita menambahkan pada indeks yang sudah memiliki isi, maka isinya akan ditimpa dengan yang baru.

## Array Asosiatif

Array asosiatif adalah array yang indeksnya tidak menggunakan nomer atau angka. Indeks array asosiatif berbentuk kata kunci.

**Contoh**

```php
<?php
// membuat array asosiatif
$siswa = [
    "nama"      => "Muhammad Ilham",
    "kelas"     => "XI",
    "sekolah"   => "SMK ISFI",
    "Jurusan"   => "RPL"
];

// mencetak isi array
echo "Nama : ".$siswa['nama']."<br>";
echo "Kelas : ".$siswa['kelas']."<br>";
echo "Sekolah : ".$siswa['sekolah']."<br>";
echo "Jurusan : ".$siswa['jurusan']."<br>";
```

**Output**
```
Nama : Muhammad Ilham
Kelas : XI
Sekolah : SMK ISFI
Jurusan : RPL
```