video #1
*tidak disertakan karena saya sudah lihat videonya langsung

video #2
Berikut adalah panduan langkah demi langkah secara mendalam mengenai alur kerja Extract, Transform, Load (ETL) menggunakan Pentaho Data Integration (Spoon) berdasarkan tutorial tersebut:

1. Tahap Persiapan dan Ekstraksi (0:02 - 5:14)
Memulai Proyek: Anda harus membuka aplikasi Spoon dan membuat file baru dengan memilih File > New > Transformation (0:46). Lembar kerja kosong akan muncul sebagai wadah proses ETL Anda.
Menambahkan Input: Cari komponen CSV File Input di panel Design atau gunakan fitur search (1:20), lalu tarik (drag-and-drop) ke canvas (1:30).
Konfigurasi Sumber Data:
Dobel klik pada icon komponen untuk membuka jendela pengaturan (1:42).
Gunakan tombol Browse untuk memilih file CSV mahasiswa yang akan diolah (3:00).
Pastikan delimiter disesuaikan dengan isi file (standarnya adalah koma). Anda dapat mengubah nama langkah (misal: csv mahasiswa) agar lebih mudah diidentifikasi (1:55).
Mapping Field: Klik tombol Get Fields (3:39). Sistem akan secara otomatis membaca nama kolom, type data (Integer, String, Big Number), dan panjang karakter dari file CSV tersebut. Lakukan Preview (4:48) untuk memastikan data telah terbaca dengan benar sebelum melanjutkan.
2. Tahap Load (Ekstraksi ke Excel) (5:17 - 9:15)
Menghubungkan Komponen (Hops): Tarik garis penghubung dari CSV File Input ke komponen tujuan. Caranya: tekan tombol Shift dan tarik garis dari komponen asal ke komponen tujuan (6:21).
Konfigurasi Output: Pilih komponen Microsoft Excel Writer dari panel Output. Dobel klik untuk mengatur lokasi penyimpanan file output dan menentukan ekstensi file, seperti .xlsx atau .xls (6:46).
Eksekusi: Klik tombol Run pada bar toolbar (7:36). Anda akan diminta menyimpan file transformation (.ktr) terlebih dahulu. Jika konfigurasi benar, semua ikon akan ditandai dengan centang hijau, menandakan proses berhasil (8:05).
3. Tahap Transformasi (Select Values) (9:15 - 13:21)
Menyisipkan Transformasi: Untuk mengubah data sebelum dimuat, Anda bisa menghapus hop lama dan menyisipkan komponen Select Values yang berada di bawah kategori Transform (10:06).
Filtering Kolom:
Dobel klik pada Select Values, lalu buka tab Remove (11:05).
Masukkan nama kolom yang tidak diinginkan (seperti: tahun masuk, semester, status) agar dihapus dari dataset final (11:22).
Finalisasi: Hubungkan kembali dari Select Values ke Microsoft Excel Writer. Jalankan kembali (Run) proses tersebut. Hasil akhir file Excel Anda kini hanya akan berisi kolom yang dipilih, yaitu NIM, Nama, Jurusan, dan IPK (12:43).
Catatan Tambahan (13:21 - 14:30)
Teknik ini adalah fondasi dari seluruh proses integrasi data. Pemateri menegaskan bahwa alur yang sama (Input -> Transform -> Output) berlaku untuk berbagai sumber data lainnya, seperti koneksi Database atau Microsoft Excel Input, yang dapat ditemukan di panel toolbox aplikasi Spoon.

video #3
Berikut adalah rincian tahapan teknis penggunaan komponen **Data Grid** pada *Pentaho Data Integration* (PDI) sebagaimana dijelaskan dalam video:

### 1. Pendahuluan Mengenai Data Grid (0:02 - 2:03)
*   **Tujuan:** *Data Grid* digunakan untuk membuat *dummy data* (data statis) secara manual. Ini sangat membantu untuk keperluan latihan transformasi data tanpa harus memproses file eksternal seperti CSV atau koneksi database secara langsung.
*   **Fungsi Utama:** Memungkinkan pengguna untuk berfokus pada logika transformasi, seperti *select columns*, *sorting*, *agregasi*, atau penanganan data kosong.

### 2. Konfigurasi Data Grid (2:19 - 4:17)
*   **Langkah awal:** Buka *transformation* baru dan tarik komponen *Data Grid* ke dalam *canvas*.
*   **Definisi Metadata (Fields):** Klik dua kali pada *Data Grid* untuk mendefinisikan struktur kolom:
    *   **Name (NIM):** Tipe data *Integer*.
    *   **Nama:** Tipe data *String*.
    *   **Alamat:** Tipe data *String*.
    *   **Nomor HP:** Tipe data *Integer*.
*   **Input Data:** Masukkan data statis secara manual sesuai kolom yang telah dibuat (contoh: 1112/Rian/Bandung, 1113/Dani/Bandung, dst).
*   **Validasi:** Anda bisa menekan tombol *preview* untuk memastikan data yang diinput sudah sesuai sebelum melanjutkan ke tahap berikutnya (4:10).

### 3. Transformasi dengan Select Values (4:21 - 5:25)
*   Gunakan komponen **Select Values** untuk memodifikasi *stream* data:
    *   **Menghapus Kolom (*Remove*):** Dalam video, kolom *Nomor HP* dipilih untuk dihapus agar tidak muncul di output akhir (4:44).
    *   **Mengubah Nama Kolom (*Rename to*):** Mengubah label kolom *Nama* menjadi *Nama Lengkap* agar lebih informatif (4:54).

### 4. Output Data (5:29 - 7:51)
*   **Destinasi Output:** Data yang telah ditransformasi dapat disimpan ke berbagai format. Dalam video, digunakan **Microsoft Excel Writer** (5:36).
*   **Proses Jalankan (Run):**
    *   Simpan *transformation* dengan nama (contoh: *materi_kedua_data_grid.ktr*).
    *   Tekan tombol *Run*.
    *   Perhatikan indikator status (ikon centang hijau) yang menandakan proses berhasil tanpa *error* (7:03).
*   **Verifikasi Hasil:** Buka file Excel yang dihasilkan di folder yang telah ditentukan untuk memastikan bahwa *Nomor HP* telah hilang dan kolom *Nama* sudah berubah menjadi *Nama Lengkap* (7:31).

video #5
Berikut adalah rincian tahapan dan langkah teknis penggunaan fitur **Filter Rows** pada *Pentaho Data Integration* (PDI) berdasarkan tutorial tersebut:

### 1. Persiapan Data (1:09 - 2:15)
*   **Input File:** Menggunakan komponen *CSV File Input* untuk memanggil sumber data, dalam contoh ini adalah file `data mahasiswa.csv`.
*   **Konfigurasi Input:** Melakukan *Get Fields* agar PDI dapat membaca struktur kolom dari file CSV tersebut.
*   **Validasi Awal:** Melakukan pengecekan data melalui fitur *Preview* untuk memastikan data telah terbaca dengan benar oleh sistem.

### 2. Implementasi Filter Rows (2:22 - 3:13)
*   **Menambahkan Komponen:** Menarik langkah *Filter Rows* ke dalam lembar kerja transformasi (*transformation*).
*   **Menghubungkan Jalur (*Hops*):** Menghubungkan *CSV File Input* dengan *Filter Rows*.
*   **Konfigurasi Kondisi:** 
    *   Masuk ke pengaturan *Filter Rows* untuk mendefinisikan logika filter.
    *   Memilih kolom yang akan difilter (misalnya: *IPK*).
    *   Memilih operator perbandingan (misalnya: *Greater than* / lebih besar).
    *   Menentukan nilai referensi (misalnya: *3.5*).

### 3. Pengaturan Output (4:37 - 8:03)
*   **Jalur Output True:** Menambahkan langkah *Excel Output* (atau komponen output lainnya) untuk menampung data yang memenuhi kriteria (IPK > 3.5). Hubungkan dari *Filter Rows* ke komponen output dan pilih opsi *Send 'true' data to this step*.
*   **Jalur Output False:** Menambahkan langkah *Excel Output* kedua untuk menampung data yang tidak memenuhi kriteria (IPK <= 3.5). Hubungkan dari *Filter Rows* ke komponen ini dan pilih opsi *Send 'false' data to this step*.
*   **Konfigurasi File Output:** Memberikan nama dan lokasi penyimpanan untuk masing-masing file hasil filter, misalnya `output_true.xls` dan `output_false.xls`.

### 4. Eksekusi dan Verifikasi (8:09 - 10:20)
*   **Menjalankan Transformasi:** Klik tombol *Run* pada toolbar untuk mengeksekusi rangkaian proses tersebut.
*   **Verifikasi Visual:** Setelah proses selesai (ditandai dengan centang hijau pada setiap komponen), lakukan *Preview* pada masing-masing *output* untuk memastikan data telah terbagi secara akurat sesuai kondisi yang telah ditentukan.
*   **Pengecekan File:** Membuka file hasil ekspor (*Excel*) untuk memastikan struktur data sudah sesuai dengan proses *filtering* yang dilakukan.