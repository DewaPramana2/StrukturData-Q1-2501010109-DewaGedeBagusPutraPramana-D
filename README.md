# Quis 1 Struktur Data:

## 1. Karakteristik Memori dan Akses Data

Array memiliki kemampuan akses elemen dengan kompleksitas waktu **O(1)** karena data disimpan secara **kontinu (berurutan)** di memori. Setiap elemen array memiliki alamat memori yang dapat dihitung langsung menggunakan rumus:

```
alamat_elemen = alamat_awal + (index × ukuran_data)
```

Karena alamat elemen dapat dihitung secara langsung, maka proses mengambil data pada indeks tertentu tidak perlu menelusuri elemen lain terlebih dahulu.

Sebaliknya, pada Singly Linked List, data disimpan secara **non-kontinu** di memori. Setiap node terdiri dari data dan pointer yang menunjuk ke node berikutnya. Untuk mengakses elemen tertentu, program harus menelusuri node satu per satu mulai dari head hingga node tujuan ditemukan.

Akibatnya:

* Array → akses data cepat dengan kompleksitas **O(1)**
* Singly Linked List → akses data membutuhkan traversal sehingga kompleksitasnya **O(n)**

Dari sisi memori:

* Array lebih efisien dalam akses karena lokasi data berdekatan.
* Linked List lebih fleksibel karena tidak membutuhkan blok memori berurutan.

---

## 2. Analisis Efisiensi Operasi Manipulasi

Linked List lebih unggul dibandingkan Array pada operasi **penyisipan (insertion)** dan **penghapusan (deletion)**, terutama ketika operasi dilakukan di awal atau tengah data.

### Pada Array

Ketika menyisipkan atau menghapus elemen:

* Elemen-elemen setelah posisi target harus digeser.
* Proses pergeseran membutuhkan waktu linear.

Kompleksitas:

* Insertion/Delete Array → **O(n)**

### Pada Linked List

Pada Linked List, proses insertion atau deletion cukup dengan:

* Mengubah pointer node.
* Tidak perlu menggeser elemen lain.

Kompleksitas:

* Insertion/Delete Linked List → **O(1)** jika posisi node sudah diketahui.

### Kesimpulan

Linked List lebih cocok digunakan ketika:

* Data sering berubah ukuran.
* Operasi tambah/hapus lebih sering dilakukan dibanding akses indeks.
* Dibutuhkan fleksibilitas alokasi memori.

Sedangkan Array lebih cocok untuk:

* Akses data cepat berdasarkan indeks.
* Data relatif tetap ukurannya.

---

## 3. Konsep Doubly Linked List

Pada Doubly Linked List, setiap node memiliki tiga bagian:

```
[prev | data | next]
```

Keterangan:

* `prev` → pointer ke node sebelumnya.
* `data` → menyimpan nilai/data.
* `next` → pointer ke node berikutnya.

### Dampak Pointer Tambahan

#### Kelebihan

1. Traversal dapat dilakukan dua arah:

   * maju (forward)
   * mundur (backward)

2. Operasi penghapusan node lebih mudah karena node mengetahui elemen sebelumnya.

3. Lebih fleksibel untuk implementasi:

   * browser history
   * undo/redo
   * navigasi playlist

#### Kekurangan

1. Membutuhkan memori lebih besar karena ada tambahan pointer `prev`.
2. Proses manipulasi pointer lebih kompleks dibanding Singly Linked List.

### Perbandingan

* Singly Linked List:

  * memori lebih hemat
  * traversal satu arah

* Doubly Linked List:

  * memori lebih besar
  * traversal dua arah lebih fleksibel

---

## 4. Mekanisme Circular Linked List

Circular Linked List adalah Linked List yang node terakhirnya tidak menunjuk ke `NULL`, melainkan kembali menunjuk ke node pertama (head).

### Perbedaan dengan Linked List Biasa

#### Linked List Biasa

```
Head → Node → Node → NULL
```

#### Circular Linked List

```
Head → Node → Node ─┐
        ↑───────────┘
```

Pada Circular Linked List:

* tidak ada node akhir yang bernilai NULL,
* traversal dapat berlangsung terus menerus secara melingkar.

### Keunggulan

* Cocok untuk proses yang berulang secara siklus.
* Tidak perlu kembali ke head secara manual.

### Contoh Use Case

Salah satu contoh penggunaan adalah **Round Robin Scheduling** pada sistem operasi.

Pada metode ini:

* setiap proses mendapatkan giliran eksekusi,
* setelah proses terakhir selesai, giliran kembali ke proses pertama.

Circular Linked List efektif karena alur data bersifat berulang/melingkar.

---

## 5. Array Dinamis di Python

`Python list` diimplementasikan menggunakan Dynamic Array.

Ketika operasi `append()` dilakukan dan kapasitas array masih tersedia:

* elemen langsung ditambahkan,
* kompleksitasnya **O(1)**.

Namun ketika kapasitas penuh, Python melakukan proses berikut:

### Mekanisme di Balik Layar

1. Python membuat array baru dengan kapasitas lebih besar.
2. Biasanya kapasitas diperbesar beberapa kali lipat (over-allocation).
3. Semua elemen lama disalin ke array baru.
4. Elemen baru ditambahkan.
5. Array lama dilepas dari memori.

### Dampak Kompleksitas

* Append normal → **O(1)**
* Saat resize → **O(n)** karena perlu menyalin seluruh elemen.

Namun secara rata-rata (amortized complexity), operasi `append()` tetap dianggap **O(1)** karena resize tidak terjadi setiap saat.

### Keuntungan Dynamic Array

* Ukuran fleksibel.
* Tetap memiliki akses indeks cepat seperti array biasa.
* Efisien untuk penambahan data di akhir list.
