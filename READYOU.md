BAB III: DATA
3.1 Data Knapsack
Sistem harus memilih 12 paket pengiriman (A hingga L) untuk dimuat ke dalam armada yang memiliki kapasitas maksimum 30 kg. Data paket beserta bobot (Weight, kg) dan keuntungannya (Profit, dalam puluhan ribu rupiah) adalah sebagai berikut:

Paket A: W = 5, P = 100

Paket B: W = 3, P = 90

Paket C: W = 8, P = 160

Paket D: W = 2, P = 50

Paket E: W = 10, P = 140

Paket F: W = 4, P = 60

Paket G: W = 6, P = 110

Paket H: W = 7, P = 105

Paket I: W = 1, P = 40

Paket J: W = 5, P = 70

Paket K: W = 9, P = 135

Paket L: W = 3, P = 55

3.2 Data Graph (MST)
Terdapat 10 node (Fulfillment Center) dan 22 edge (jalur transfer stok). Bobot merepresentasikan biaya infrastruktur (dalam juta rupiah):

Node: 1(JKT), 2(BGR), 3(DPK), 4(TGR), 5(BKS), 6(KRW), 7(BDG), 8(CRB), 9(SMR), 10(YGY).

Daftar Edge & Bobot:
(2,3): 8, (1,2): 10, (1,4): 12, (1,5): 14, (1,3): 15, (3,4): 18, (3,5): 20, (2,4): 22, (2,5): 24, (5,6): 25, (1,6): 30, (3,6): 35, (7,8): 35, (6,7): 40, (6,8): 45, (2,7): 50, (9,10): 55, (8,9): 60, (5,7): 65, (7,9): 70, (8,10): 80, (7,10): 85.

BAB IV: KNAPSACK
Sesuai instruksi, berikut adalah implementasi 3 metode greedy untuk kapasitas 30 kg.

(1) Greedy by Profit
Memilih item dengan profit terbesar lebih dahulu.

Urutan prioritas: C(160), E(140), K(135), G(110), H(105), A(100), B(90), J(70), F(60), L(55), D(50), I(40).

Pemilihan:

Ambil C (W=8, Sisa Kapasitas=22, Total Profit=160)

Ambil E (W=10, Sisa Kapasitas=12, Total Profit=300)

Ambil K (W=9, Sisa Kapasitas=3, Total Profit=435)

Lewati G, H, A (Kapasitas tidak cukup)

Ambil B (W=3, Sisa Kapasitas=0, Total Profit=525)

Total Profit = 525, Total Weight = 30 kg.

(2) Greedy by Weight
Memilih item dengan weight terkecil lebih dahulu.

Urutan prioritas: I(1), D(2), B(3), L(3), F(4), A(5), J(5), G(6), H(7), C(8), K(9), E(10).

Pemilihan: Ambil I, D, B, L, F, A, J, dan G. Sisa kapasitas 1 kg, sisa barang tidak ada yang muat.

Total Profit = 575, Total Weight = 29 kg.

(3) Greedy by Density
Memilih item dengan rasio Profit/Weight terbesar lebih dahulu.

Urutan prioritas (Rasio): I(40), B(30), D(25), C(20), A(20), G(18.3), L(18.3), F(15), H(15), K(15), E(14), J(14).

Pemilihan: Ambil I, B, D, C, A, G, dan L. Total Weight mencapai 28 kg. Sisa kapasitas 2 kg, paket berikutnya (F, W=4) tidak muat.

Total Profit = 605, Total Weight = 28 kg.

BAB V: FRACTIONAL KNAPSACK
Menerapkan Fractional Knapsack yang mengizinkan pemecahan barang untuk dibandingkan dengan 0/1 Knapsack.

Menggunakan urutan prioritas Density yang sama: Ambil penuh I, B, D, C, A, G, dan L (W=28, P=605).

Sisa kapasitas = 2 kg. Ambil barang F (W=4, P=60) secara fraksional sebesar 2 kg (2/4 bagian). Profit tambahan = (2/4) * 60 = 30.

Total Profit = 635, Total Weight = 30 kg.

Perbandingan: Pendekatan Fractional (635) lebih optimal dibandingkan 0/1 Greedy by Density (605) karena mampu memanfaatkan sisa kapasitas ruang yang kosong (2 kg) secara penuh.

BAB VI: MINIMUM SPANNING TREE (MST)
Penyelesaian 2 algoritma wajib: Kruskal dan Prim.

6.1 Kruskal
Mengurutkan sisi dari bobot terkecil, tambahkan jika tidak membentuk siklus:

(2,3) bobot 8

(1,2) bobot 10

(1,4) bobot 12

(1,5) bobot 14

(5,6) bobot 25 (mengabaikan edge bernilai 15, 18, 20, 22, 24 karena membentuk siklus)

(7,8) bobot 35 (mengabaikan 30, 35 siklus)

(6,7) bobot 40

(9,10) bobot 55 (mengabaikan 45, 50 siklus)

(8,9) bobot 60

Total Bobot MST = 259 juta rupiah.

6.2 Prim
Dimulai dari titik acak (misal Node 1), mengambil sisi terkecil yang terhubung ke pohon saat ini:

Dari Node 1, ambil (1,2) bobot 10

Ambil (2,3) bobot 8

Ambil (1,4) bobot 12

Ambil (1,5) bobot 14

Ambil (5,6) bobot 25

Ambil (6,7) bobot 40

Ambil (7,8) bobot 35

Ambil (8,9) bobot 60

Ambil (9,10) bobot 55

Total Bobot MST = 259 juta rupiah.

BAB VII: ANALISIS HASIL
Berdasarkan data operasional spesifik yang telah dihitung di atas, diperoleh bukti nyata tentang kinerja masing-masing algoritma. Pada masalah Knapsack, pemilihan paket menggunakan pendekatan Greedy by Density memberikan revenue tertinggi sebesar 605 dibandingkan metode profit tunggal (525) maupun bobot tunggal (575). Namun, perhitungan Fractional Knapsack yang mencapai titik optimum matematis sebesar 635 menunjukkan batas maksimal utilitas ruang yang sebenarnya tidak mungkin diterapkan pada paket fisik yang utuh. Untuk persoalan jaringan gudang (MST), baik algoritma Kruskal maupun Prim membuahkan total biaya instalasi yang persis sama, yakni 259 juta rupiah, namun menghasilkan cara pandang evaluasi yang berbeda—Kruskal mengedepankan sisi termurah secara global terlebih dahulu, sedangkan Prim mengekspansi jaringan secara kontinyu dari pusat yang sudah ada.

BAB VIII: KESIMPULAN
Sistem Optimasi Operasional untuk distribusi berhasil dimodelkan. Penerapan pendekatan algoritmik mendedikasikan bahwa pengambilan keputusan berdasarkan rasio kepadatan nilai (Density) adalah strategi terkuat untuk operasional berkapasitas terbatas di dunia nyata. Untuk pengembangan infrastruktur, algoritma MST—baik Kruskal maupun Prim—secara mutlak memangkas opsi redundan dari 22 jalur koneksi logistik menjadi hanya 9 interkoneksi utama, yang secara drastis meminimalkan pengeluaran modal jaringan distribusi perusahaan dengan mempertahankan konektivitas penuh seluruh cabang.
