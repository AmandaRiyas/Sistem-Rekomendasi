# Laporan Proyek Machine Learning - Amanda Riyas Utami

## Project Overview

Dalam era digital saat ini, jumlah buku yang tersedia di pasaran sangat besar dan terus bertambah. Baik toko buku online maupun platform digital memerlukan sistem yang mampu membantu pembaca menemukan buku yang relevan dengan minat dan preferensi mereka. Tanpa bantuan sistem rekomendasi yang cerdas, pembaca akan kesulitan menemukan buku yang sesuai, dan perusahaan berpotensi kehilangan peluang penjualan. Permasalahan ini menjadi penting untuk dipecahkan karena sistem rekomendasi yang baik tidak hanya meningkatkan pengalaman pengguna tetapi juga berdampak langsung terhadap performa bisnis. Dengan merekomendasikan buku-buku yang relevan berdasarkan kesamaan konten, perusahaan penerbitan atau penjualan buku dapat meningkatkan kepuasan pelanggan sekaligus mendorong penjualan secara lebih efisien. Proyek ini bertujuan untuk membangun sistem rekomendasi buku berbasis content-based filtering dengan memanfaatkan data deskriptif buku seperti nama buku, genre, author, penerbit, dan bahasa buku. Sistem ini akan mengidentifikasi buku-buku yang mirip satu sama lain menggunakan teknik pemrosesan bahasa alami (TF-IDF) dan pengukuran kesamaan (cosine similarity). Dari penelitian terdahulu yang berjudul "Sistem Rekomendasi Buku Menggunakan Metode Content Best Filtering mendapatkan hasil bahwa Sistem rekomendasi buku dengan menggunakan teknik pembobotan TF-IDF dan algoritma cosine similarity dapat memberikan rekomendasi kepada pengguna sesuai dengan kemiripan data buku yang tersedia pada database, pada penelitiannya akurasi sistem rekomendasi buku menggunakan content best filtering memiliki tingkat akurasi precision sebesar 85% (Zayyad, 2021). Sehingga pada penelitian ini akan mencoba membuktikan apakah metode content best filtering bisa atau tidak memberikan akurasi yang akurat mengenai sistem rekomendasi buku.

## Business Understanding
Suatu perusahaan yang bergerak di bidang penerbitan atau penjualan buku tentunya perlu memahami minat dan preferensi pembaca. Memahami tren minat baca sangat penting agar perusahaan dapat memasarkan dan menerbitkan buku yang relevan, sehingga dapat meningkatkan penjualan dan kepuasan pelanggan. Oleh karena itu, diperlukan sistem rekomendasi yang mampu menyarankan buku sesuai dengan minat pembaca berdasarkan konten atau informasi terkait buku-buku yang telah tersedia.

### Problem Statements
- Diperlukan metode untuk mengidentifikasi buku-buku yang memiliki kemiripan topik atau konten dengan buku yang sedang dibaca atau disukai oleh pembaca
- Perusahaan membutuhkan model yang dapat digunakan untuk membangun sistem rekomendasi buku berbasis konten guna meningkatkan relevansi dan kepuasan pelanggan

### Goals
- Mengembangkan metode berbasis pemrosesan teks dan pembelajaran mesin untuk mengidentifikasi buku-buku dengan kemiripan konten atau topik secara otomatis
- Membangun sistem rekomendasi buku berbasis content-based filtering yang mampu memberikan saran buku yang relevan dengan preferensi pembaca, sehingga dapat mendukung strategi bisnis perusahaan dalam meningkatkan penjualan dan kepuasan pelanggan

    ### Solution statements
    - Membuat sistem rekomendasi buku menggunakan content best filtering

## Data Understanding
Data pada proyek ini berasal dari kaggle yang berjudul Books Sales and Ratings dengan link https://www.kaggle.com/datasets/thedevastator/books-sales-and-ratings 

Variabel-variabel pada Books Sales and Ratings adalah sebagai berikut:
- index : merupakan kode dari buku
- Publishing Year : Tahun dimana buku tersebut diterbitkan
- Book Name : Judul buku
- Author : Nama penulis buku
- language_code : Kode yang mewakili bahasa penulisan buku tersebut
- Author_Rating : Penilaian penulis berdasarkan karya-karyanya sebelumnya
- Book_average_rating : Nilai rata-rata yang diberikan pembaca terhadap buku tersebut
- Book_ratings_count : Jumlah rating yang diberikan pembaca terhadap buku tersebut
- genre : Genre atau kategori buku
- gross sales : Total pendapatan penjualan yang dihasilkan oleh buku tertentu
- publisher revenue : Pendapatan yang diperoleh penerbit dari penjualan buku tertentu
- sale price : Harga jual buku
- sales rank : Peringkat buku tertentu berdasarkan kinerja penjualannya
- Publisher : Penerbit
- units sold : Jumlah unit yang terjual

Untuk memahami seperti apa data yang digunakan maka dilakukan data understanding dengan melakukan beberapa tahapan yaitu:
1. Memeriksa info data
   Terdapat 1070 data dengan 15 variabel yaitu index (int), Publishing Year (float), Book Name (object), Author (object), language_code (object), Author_Rating (object), Book_average_rating (float), Book_ratings_count (int), genre (object), gross sales (float), publisher revenue (float), sale price (float), sales rank (int), Publisher (object), dan units sold (int)
2. Memeriksa nilai kosong di dalam data
   Pada variabel Publishing Year terdapat 1 data yang kosong, pada variabel, Book Name terdapat 23 data yang kosong, dan pada variabel language_code terdapat 53 data yang kosong
3. Memeriksa data duplikat
   Tidak ada data yang duplikat
4. Visualisasi variabel numerik
   
   <img src="https://raw.githubusercontent.com/AmandaRiyas/Sistem-Rekomendasi/refs/heads/main/Gambar/visualisasi%20data%20numerik.png" width="500"/>

   Dari gambar di atas terlihat bahwa 
   - Pada `index` distribusinya seragam karena index tidak mengandung     informasi analitis
    - Pada `Publishing Year` distribusi terpusat di sekitar tahun 1900 ke atas dan ada nilai ekstrem yaitu tahun di bawah 0, tahun di bawah 0 ini merupakan bagian dari missing value karena tidak mungkin tahun bernilai negatif
    - Pada `Book_average_rating` distribusi datanya hampir normal
    - Pada `Book_ratings_count` distribusi data miring ke kanan (right-skewed)
    - Pada `gross sales` distribusi data sangat miring ke kanan
    - Pada `publisher revenue` distribusi data miring ke kanan
    - Pada `sale price` data miring ke kanan (right-skewed)
    - Pada `sales rank` distribusi data hampir uniform atau penyebaran data cukup rata
    - Pada `units sold` distribusi data sangat miring ke kanan

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data beserta insight atau exploratory data analysis.

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
