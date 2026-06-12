1. https://www.youtube.com/watch?v=dRjHw0Tpiw0
Berikut adalah tutorial langkah demi langkah yang rinci tentang proses ETL menggunakan Pentaho Data Integration, tanpa bagian pengantar:

1. Membuat Transformasi Baru
Buka Pentaho Data Integration.
Pilih opsi untuk membuat transformasi baru.
2. Menambahkan Input File CSV
Tambahkan langkah Input File CSV ke dalam transformasi.
Klik dua kali pada langkah tersebut untuk membuka pengaturannya.
Di bagian File, telusuri dan pilih file CSV yang berisi data transaksi ritel.
3. Mengonfigurasi Input File CSV
Setelah memilih file, lihat pratinjau data untuk memastikan kolom yang diperlukan (seperti ID pelanggan, transaksi, dan jumlah transaksi) ada.
Pastikan untuk memeriksa pengaturan delimiter dan encoding sesuai dengan file Anda.
4. Mengubah Tipe Data
Tambahkan langkah Select Values untuk mengubah tipe data.
Klik dua kali pada langkah tersebut.
Di tab MetaData, pilih kolom yang ingin diubah (misalnya, "ID pelanggan").
Ubah nama kolom menjadi "pelanggan" dan tipe data menjadi "String".
Pastikan format kapitalisasi sudah benar sebelum menyimpan perubahan.
5. Menambahkan Kalkulator
Tambahkan langkah Calculator ke dalam transformasi.
Klik dua kali pada langkah tersebut.
Konfigurasikan kalkulator untuk menghitung tahun dari tanggal transaksi.
Tambahkan perhitungan menggunakan 'Years of Date' untuk kolom tanggal transaksi.
Simpan pengaturan kalkulator.
6. Menambahkan Komponen Select Value
Tambahkan langkah Select Values lainnya untuk memilih kolom yang relevan.
Hapus kolom yang tidak diperlukan (misalnya, kolom yang tidak ingin Anda simpan).
Pastikan hanya kolom yang diinginkan yang tersisa, seperti 'pelanggan', 'transmount', dan 'Year'.
7. Menambahkan Baris Pendek
Tambahkan langkah Row Shortening untuk memfilter data berdasarkan kriteria tertentu.
Pilih bidang tertentu seperti pelanggan, bulan, dan tahun.
Ganti nama kolom yang dihasilkan menjadi 'data pendek' untuk kejelasan.
8. Kelompok Berdasarkan (Aggregation)
Tambahkan langkah Group By untuk mengagregasi data.
Klik dua kali pada langkah tersebut untuk mengonfigurasinya.
Pilih bidang yang ingin dikelompokkan (misalnya, pelanggan, bulan, dan tahun).
Tambahkan kolom baru yang disebut 'total', dan pilih kolom 'transmount' dengan tipe agregasi sebagai 'jumlah'.
9. Mengonfigurasi Keluaran Tabel
Tambahkan langkah Output Table untuk menyimpan data ke dalam database.
Buat koneksi baru ke database MySQL.
Masukkan informasi koneksi (seperti nama pengguna dan kata sandi).
Uji koneksi untuk memastikan berhasil.
Atur skema dan tabel target, misalnya mencari tabel 'fakta penjualan' di database MySQL lokal.
Petakan kolom yang akan disimpan (seperti 'customer', 'mount', dan 'total transaksi').
10. Penyimpanan dan Verifikasi Data
Setelah semua langkah selesai, jalankan transformasi.
Periksa hasil di SQL Yog atau alat database lain untuk memastikan data tersimpan dengan benar.
Lakukan penyegaran database untuk melihat data yang baru saja disimpan.
11. Ulang Proses jika Diperlukan
Jika Anda perlu melakukan penyesuaian, ulangi langkah-langkah yang diperlukan untuk memperbaiki atau mengubah data.
Dengan mengikuti langkah-langkah ini, Anda dapat melakukan proses ETL menggunakan Pentaho Data Integration secara efektif. Jika Anda memiliki pertanyaan lebih lanjut atau memerlukan detail tambahan, jangan ragu untuk bertanya!


2. https://www.youtube.com/watch?v=0XF3nZUyw1M&t=460s
Video ini adalah tutorial tentang penggunaan Pentaho Data Integration untuk proses ETL (Extract, Transform, Load). Berikut adalah langkah-langkah dan rincian dari video tersebut:

Pengantar Pentaho Data Integration:

Video dimulai dengan memperkenalkan Pentaho Data Integration sebagai alat untuk proses ETL.
Pentaho adalah alat gratis yang kaya fitur dan mudah digunakan untuk integrasi data.
Pengguna perlu mengunduh Pentaho dari tautan yang disediakan, dengan ukuran sekitar 1GB.
Java Runtime Environment (JRE) perlu diinstal terlebih dahulu karena Pentaho berbasis Java.
Memasang Java dan Memeriksa Pemasangan:

Pengguna diinstruksikan untuk mengunduh konektor PostgreSQL secara manual.
Setelah mengunduh JRE, pembicara menunjukkan cara memeriksa pemasangan Java melalui command prompt.
Mempersiapkan Data dan Konektor:

Pembicara menyiapkan dataset yang akan digunakan, yaitu dataset lagu Spotify dari Kaggle.com.
File arsip yang diunduh perlu diekstrak untuk mendapatkan data yang diperlukan.
Konektor MySQL kemudian disalin ke dalam folder 'lib' di direktori Pentaho Data Integration.
Menyiapkan Pentaho dan Basis Data:

Pengguna membuka Pentaho dengan menjalankan file eksekutabel Spoon sebagai administrator.
Pembicara membuat basis data baru di MySQL melalui phpMyAdmin untuk menyimpan data.
Antarmuka Pentaho Data Integration dan Ekstraksi Data:

Antarmuka Pentaho ditampilkan, dan pengguna memilih 'transformation' untuk memulai proses transformasi.
Pengguna memilih input dari file CSV untuk ekstraksi data dan mengganti nama langkah ekstraksi.
Transformasi Data di Pentaho:

Setelah pratinjau data, pengguna melakukan transformasi dengan menghapus tabel yang tidak perlu dan merapikan data.
Pengguna mengganti nama kolom dan menghubungkan aliran data dengan langkah-langkah yang sesuai.
Transformasi dan Keluaran Data:

Pengguna menghapus kolom yang tidak diinginkan dan mengurutkan data berdasarkan tahun.
Data yang ditransformasi disiapkan untuk diekspor ke dalam file Microsoft Excel, dan pengguna memverifikasi hasilnya.
Mengekspor Data ke MySQL:

Pengguna menunjukkan cara mengunduh data dari Excel ke dalam database MySQL menggunakan opsi "Table output".
Koneksi database baru dibuat dan tabel baru bernama "music" dibuat untuk menerima data.
Setelah menjalankan transformasi, data dari file CSV berhasil diimpor ke tabel "music" di MySQL, diatur berdasarkan tahun.
Video ini memberikan panduan lengkap dan praktis untuk melakukan proses ETL menggunakan Pentaho Data Integration, mulai dari instalasi hingga ekspor data ke database MySQL.


3. https://www.youtube.com/watch?v=KMWKKE6sS0g