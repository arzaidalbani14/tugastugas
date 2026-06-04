video #5
Video ini merupakan tutorial mengenai penggunaan fitur **Replace in String** pada *Pentaho Data Integration* (PDI). Berikut adalah rangkuman langkah-langkah yang dilakukan dalam video:

### 1. Pendahuluan dan Kasus (0:02 - 3:13)
*   Penjelasan fungsi **Replace in String**: Mengganti nilai teks atau karakter tertentu dalam kolom data agar seragam (misalnya, menyamakan singkatan 'SI' menjadi 'Sistem Informasi').
*   Tujuan: Menyeragamkan data mahasiswa yang memiliki variasi penulisan untuk mempermudah proses agregasi data di kemudian hari.

### 2. Implementasi di Pentaho (3:13 - 6:00)
*   Membuat *transformation* baru dan memasukkan *step* **Replace in String** ke dalam *workspace*.
*   Menghubungkan *input* data mahasiswa ke *step* tersebut.
*   Mengonfigurasi *rule* pencarian: Mencari teks **'si'** dan menggantinya dengan **'sistem informasi'** pada kolom 'jurusan'.
*   Menyiapkan *output* data ke dalam format file *Excel* (XLSX).

### 3. Pengujian dan Perbaikan (6:00 - 10:24)
*   **Percobaan pertama (6:00 - 7:27):** Menjalankan *transformation*. Hasilnya ditemukan masalah, yaitu teks yang mengandung 'si' di dalam kata lain (seperti pada kata 'sistem informasi' itu sendiri) ikut berubah, sehingga data menjadi tidak akurat.
*   **Solusi:** Menambahkan pengaturan **Whole word = Yes** di dalam konfigurasi *Replace in String*. Hal ini memastikan hanya kata 'si' yang berdiri sendiri (utuh) yang akan diganti, bukan bagian dari kata lain (7:31 - 8:54).
*   **Pengujian Akhir:** Menjalankan ulang proses dan memverifikasi hasilnya. Data mahasiswa dengan jurusan 'si' berhasil berubah menjadi 'sistem informasi' tanpa merusak data lain (9:17 - 10:13).

video #6

Video ini membahas implementasi **Merge Join** dalam *Pentaho Data Integration* untuk menggabungkan dua dataset yang berbeda. Berikut adalah langkah-langkah lengkap yang dilakukan dalam video:

**1. Persiapan Data (0:01 - 5:00)**
*   **Studi Kasus:** Menggunakan dua file (CSV/Excel), yaitu data **Dosen** dan data **Program Studi (Prodi)**.
*   **Relasi Data:** Menjelaskan konsep *Foreign Key*, di mana kolom 'jurusan' pada data dosen akan dihubungkan dengan 'kode prodi' pada data Master Prodi.

**2. Konfigurasi Awal di Pentaho (3:24 - 6:20)**
*   Membuat *transformation* baru dan memasukkan file input untuk data Dosen dan data Prodi menggunakan *CSV file input*.
*   Melakukan pengecekan data (*Get Fields* dan *Preview*) untuk memastikan struktur tabel sudah benar.

**3. Implementasi Merge Join (6:21 - 10:20)**
*   Menggunakan *step* **Merge Join** untuk menghubungkan kedua file tersebut berdasarkan atribut yang sama (jurusan).
*   Memilih tipe join yang diinginkan (Inner, Left, Right, atau Full).
*   Menyimpan hasil *join* ke dalam format file Excel menggunakan *Microsoft Excel Writer*.

**4. Pentingnya Sorting (11:00 - 14:10)**
*   Penjelasan bahwa *Merge Join* di Pentaho memerlukan data yang sudah diurutkan terlebih dahulu agar hasilnya akurat.
*   Menambahkan *step* **Sort Rows** sebelum *Merge Join* pada kedua aliran data (Dosen dan Prodi) untuk mengurutkan berdasarkan kolom kunci (*jurusan/kode prodi*) secara *ascending*.

**5. Pembersihan Data dengan Select Values (14:45 - 16:50)**
*   Menggunakan *step* **Select Values** untuk memfilter kolom yang akan ditampilkan.
*   Menghapus kolom duplikat (seperti 'jurusan' dan 'kode prodi' yang ganda) serta kolom lain yang tidak diperlukan agar *output* lebih rapi.

**6. Pengujian Akhir (16:30 - 17:32)**
*   Menjalankan transformasi (*Run*) dan memverifikasi hasil akhir di mana data dosen kini sudah dilengkapi dengan nama program studi yang sesuai.

video #7
Video ini membahas cara menangani data yang bernilai `null` atau kosong menggunakan **Pentaho Data Integration (PDI)** dengan memanfaatkan *step* **If field value is null**. Berikut adalah langkah-langkah yang dilakukan dalam video:

**1. Persiapan Data (0:02 - 2:35)**
* Penjelasan awal mengenai pentingnya menangani *missing value* dalam sebuah dataset agar data menjadi lengkap (0:02 - 1:03).
* Membuat transformasi baru dengan nama "Handling missing value" (1:13 - 1:34).
* Menggunakan *step* **Data Grid** untuk membuat data contoh (*dummy data*) yang berisi kolom **Nama** dan **Alamat** (1:40 - 2:35).
* Memasukkan data contoh di mana salah satu baris (Jaka) memiliki nilai `null` pada kolom Alamat (2:07 - 2:35).

**2. Implementasi Step 'If field value is null' (2:50 - 4:24)**
* Menghubungkan *step* **Data Grid** ke *step* **If field value is null** (2:50 - 3:13).
* Mengonfigurasi *step* untuk memilih kolom yang akan diperbaiki, dalam hal ini kolom **Alamat** (3:32 - 3:46).
* Menentukan nilai pengganti untuk data `null`. Contoh yang diberikan adalah memberikan keterangan "undefined" jika alamat tidak ditemukan (3:46 - 4:24).

**3. Eksekusi dan Output (4:24 - 5:17)**
* Menjalankan transformasi dan melihat hasil melalui *preview data*. Nilai yang tadinya `null` berhasil berubah menjadi "undefined" (4:24 - 4:37).
* Menunjukkan cara menyimpan hasil tersebut ke dalam file *Excel* sebagai bentuk *output* data yang sudah bersih (4:40 - 5:17).

**4. Penanganan Data Numerik (5:25 - 6:58)**
* Menambahkan kolom baru yaitu **Umur** (tipe *integer*) ke dalam data grid untuk skenario berbeda (5:25 - 5:58).
* Menjelaskan pendekatan menangani `null` pada data numerik dengan cara mengisi nilai rata-rata (*average*). Dalam contoh, nilai `null` diisi dengan angka 20 (6:06 - 6:42).
* Menjalankan kembali transformasi dan memastikan kolom umur yang kosong sudah terisi dengan nilai 20 (6:42 - 6:58).

Video ditutup dengan kesimpulan bahwa teknik ini adalah cara sederhana untuk membersihkan data, dan pengguna disarankan untuk bereksplorasi lebih lanjut dengan skenario data yang berbeda (7:02 - 7:25).

video #8
Video ini membahas penggunaan fitur **Calculator** pada *Pentaho Data Integration* (PDI) untuk melakukan operasi data sederhana. Berikut adalah rangkuman langkah-langkah dan fungsi yang dipraktikkan dalam video:

1. **Pengenalan Fungsi Calculator (0:13 - 1:25):**
   Penjelasan mengenai peran *step* Calculator untuk operasi matematika (penjumlahan, pembagian), pembulatan (*round*), serta ekstraksi data waktu (*date/time extraction*).

2. **Operasi Aritmatika Sederhana (1:30 - 4:10):**
   - Pembuatan data simulasi berupa tabel mahasiswa dengan kolom *nama* (string), *tugas 1* (integer), dan *tugas 2* (integer).
   - Penggunaan Calculator untuk menambahkan kolom baru bernama **jumlah** yang menghitung hasil penjumlahan antara *tugas 1* dan *tugas 2*.

3. **Ekstraksi Data Waktu (4:10 - 8:15):**
   - Penggunaan file data penjualan (*simple sales*) yang berisi tanggal, produk, dan jumlah.
   - Praktik mengekstrak informasi spesifik dari data tanggal, yaitu:
     - **Day of the Year**: Mengambil urutan hari dalam setahun (contoh: 1 Oktober adalah hari ke-275).
     - **Month of the Date**: Mengambil informasi bulan dari tanggal yang tersedia.

4. **Manipulasi String (8:15 - 9:45):**
   - Demonstrasi penggunaan fungsi **Upper Case** pada kolom *produk*.
   - Menjelaskan kegunaan fungsi ini untuk menstandarisasi format data (misalnya mengubah teks menjadi huruf kapital semua) agar data lebih konsisten saat diproses.