# Quis 1 Struktur Data: 

## 1. Karakteristik Memori dan Akses Data

Array memiliki akses data yang sangat cepat karena elemen-elemennya disimpan secara berurutan di memori. Setiap elemen memiliki indeks, sehingga alamat memorinya bisa langsung dihitung tanpa harus mencari satu per satu. Oleh karena itu, proses akses data pada array memiliki kompleksitas waktu O(1).

Contoh sederhana:

alamat_elemen = alamat_awal + (index × ukuran_data)

Berbeda dengan Singly Linked List, data pada struktur ini tidak disimpan secara berurutan di memori. Setiap node hanya menyimpan data dan pointer ke node berikutnya. Untuk mencari elemen tertentu, program harus menelusuri node mulai dari head sampai data ditemukan.

Akibatnya:

* Array memiliki akses data lebih cepat dengan kompleksitas O(1).
* Singly Linked List membutuhkan traversal sehingga kompleksitasnya O(n).

Dari sisi memori:

* Array membutuhkan memori yang kontinu.
* Linked List lebih fleksibel karena node dapat disimpan di lokasi memori yang berbeda.

---

## 2. Analisis Efisiensi Operasi Manipulasi

Linked List lebih unggul dibandingkan Array dalam operasi insertion dan deletion, terutama jika data sering ditambah atau dihapus.

Pada Array:

* Saat menyisipkan data di tengah, elemen setelahnya harus digeser.
* Saat menghapus data, elemen juga perlu dirapikan kembali.

Karena ada proses pergeseran elemen, kompleksitas waktunya menjadi O(n).

Sedangkan pada Linked List:

* Penambahan atau penghapusan data cukup mengubah pointer.
* Tidak perlu menggeser elemen lain.

Jika posisi node sudah diketahui, operasi insertion dan deletion dapat dilakukan dalam O(1).

Jadi, Linked List lebih cocok digunakan ketika:

* ukuran data sering berubah,
* proses tambah/hapus data lebih sering dilakukan,
* dan fleksibilitas memori lebih dibutuhkan.

Sementara Array lebih cocok jika program membutuhkan akses data yang cepat berdasarkan indeks.

---

## 3. Konsep Doubly Linked List

Pada Doubly Linked List, setiap node memiliki tiga bagian:

[prev | data | next]

Keterangan:

* prev menyimpan alamat node sebelumnya.
* data menyimpan nilai data.
* next menyimpan alamat node berikutnya.

Adanya pointer tambahan (prev) membuat traversal dapat dilakukan dua arah, yaitu maju dan mundur. Hal ini membuat proses pencarian atau penghapusan node menjadi lebih fleksibel dibandingkan Singly Linked List.

Kelebihan Doubly Linked List:

* Bisa traversal dua arah.
* Penghapusan node lebih mudah.
* Cocok untuk fitur undo/redo atau navigasi.

Kekurangannya:

* Membutuhkan memori lebih besar karena ada tambahan pointer.
* Pengelolaan pointer lebih kompleks.

---

## 4. Mekanisme Circular Linked List

Circular Linked List adalah Linked List yang node terakhirnya kembali menunjuk ke node pertama, sehingga membentuk lingkaran.

Linked List biasa:

Head → Node → Node → NULL

Circular Linked List:

Head → Node → Node ─┐
↑───────────┘

Perbedaan utamanya adalah pada node terakhir:

* Linked List biasa berakhir di NULL.
* Circular Linked List kembali ke head.

Struktur ini cocok digunakan pada proses yang berjalan terus menerus atau bergiliran.

Contoh penggunaan:

* Round Robin Scheduling pada sistem operasi.

Pada sistem tersebut, setiap proses mendapatkan giliran secara bergantian dan akan kembali ke proses pertama setelah proses terakhir selesai dijalankan.

---

## 5. Array Dinamis di Python

List pada Python sebenarnya menggunakan konsep Dynamic Array.

Saat melakukan append(), jika kapasitas array masih tersedia maka data langsung ditambahkan dan proses berjalan cepat dengan kompleksitas O(1).

Namun jika kapasitas penuh:

1. Python membuat array baru dengan ukuran lebih besar.
2. Semua data lama disalin ke array baru.
3. Data baru ditambahkan.
4. Array lama dihapus dari memori.

Karena ada proses penyalinan data, operasi resize membutuhkan waktu O(n).

Walaupun begitu, secara rata-rata operasi append() tetap dianggap O(1) karena proses resize tidak selalu terjadi setiap penambahan data.

Kelebihan Dynamic Array:

* ukuran lebih fleksibel,
* tetap memiliki akses indeks yang cepat,
* dan efisien digunakan untuk penambahan data di akhir list.
