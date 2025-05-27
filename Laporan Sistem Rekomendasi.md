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
4. Visualisasi variabel kategorik
   
   <img src="https://raw.githubusercontent.com/AmandaRiyas/Sistem-Rekomendasi/refs/heads/main/Gambar/visualisasi%20data%20kategorik.png" width="500"/>

   - Pada `Book Name` distribusi rata rata sangat rendah karena tidak ada buku yang mendominasi
    - Pada `Author` memiliki distribusi long tail distribution dengan auuthor yang paling dominan yaitu Stephen King
    - Pada `language_code` didominasi oleh kode eng, yang artinya bahasa utama buku tersebut adalah bahasa inggris
    - Pada `Author_Rating` mayoritas memiliki kategori Intermediate dan yang paling rendah Novice
    - Pada `genre` didominasi oleh genre fiction dan yang paling rendah genre children
    - Pada `Publisher` penerbit terbanyaknya yaitu Amazon Digital Services, Inc

## Data Preparation
Data preparation sangat penting dilakukan sebelum membuat pemodelan karena untuk mengetahui lebih mendalam mengenai seperti apa data yang digunakan untuk menganalisis suatu permasalahan dan memastikan tidak ada kesalahan sebelum pemodelan agar model yang dihasilkan nanti lebih akurat. Pada bagian Data Preparation ada beberapa tahapan yang dilakukan yaitu:
1. Menangani data yang kosong
   Karena pada variabel Book Name terdapat 23 data yang kosong, oleh karena itu diperlukan penanganan dengan menghapus data karena nantinya akan sulit menganalisis buku jika nama buku tidak ada. Kemudian pada variabel language_code terdapat 53 data kosong oleh karena itu dilakukan pengisian data yang kosong dengan modus agar data tetap bisa diproses dengan konsisten.
2. Menghapus variabel yang tidak dibutuhkan
   Terdapat beberapa variabel yang tidak di butuhkan untuk mmebuat model sistem rekomendasi dengan content best filtering. Variabel-variabel tersebut yaitu `Author_Rating`, `Book_average_rating`, `Book_ratings_count`, `gross sales`, `publisher revenue`, `sale price`, `sales rank`, `units sold`, `index`, dan `Publishing Year`. Dan setelah dilakukan penghapusan diperoleh sisa data yaitu 1047 dan variabelnya 5 yaitu variabel `Book Name`, `Author`, `language_code`, `genre`, `Publisher` dengan tipe data object semua.

## Modeling
Pada tahap ini, dilakukan pemodelan untuk membuat sistem rekomendasi buku dengan content best filtering dengan tahapan:
1. TF-IDF Vectorizer
   TF-IDF Vectorizer digunakan untuk mengubah teks menjadi matriks vektor, sehingga bisa digunakan dalam model machine learning sistem rekomendasi. Namun setelah membuat TF-IDF Vectorizer ternyata ada karakter yang aneh sehingga perlu dilakukan penghapusan karakter aneh tersebut. Dan setelah dilakukan penghapusan karakter aneh, lakukan fit dan transformasi ke dalam bentuk matriks dan diperoleh hasil akhir ukuran matriksnya yaitu 1047 baris dan 1437 kolom. Untuk menghasilkan vektor tf-idf dalam bentuk matriks, kita menggunakan fungsi todense() kemudian lihat matriks tf-idf untuk beberapa nama buku dan content atau variabel yang digunakan untuk membuat sistem rekomendasi dan diperoleh output:
   
   <img src="https://raw.githubusercontent.com/AmandaRiyas/Sistem-Rekomendasi/refs/heads/main/Gambar/Matriks%20TF-IDF.png" width="500"/>

   Hasil 0.0 wajar, nilai ini muncul karena kata-kata yang dipilih tidak ada dalam konten buku yang ditampilkan
2. Cosine Similarity
   Pada tahap perhitungan cosine similarity, langkah pertama yang dilakukan adalah membentuk matriks similarity, yaitu matriks dua dimensi yang berisi nilai kemiripan antar buku berdasarkan representasi fitur teks dari masing-masing buku yang telah diubah menjadi vektor TF-IDF, nilai similarity berkisar dari 0 hingga 1, dimana:
- 1 berarti dokumen itu identik dengan dirinya sendiri
- Nilai mendekati 1 menunjukkan kemiripan konten yang tinggi antar buku
- Nilai rendah menunjukkan perbedaan konten yang signifikan
  Selanjutnya lihat matriks kesamaan setiap resto dengan menampilkan nama restoran dalam 10 sampel kolom (axis = 0) dan 5 sampel baris (axis=1) dan diperoleh output:

  <img src="https://raw.githubusercontent.com/AmandaRiyas/Sistem-Rekomendasi/refs/heads/main/Gambar/Similarity%20buku%20acak.png" width="500"/>

  Dengan cosine similarity, maka dapat diidentifikasi kesamaan antara buku satu dengan buku lainnya. Shape (1047, 1047) merupakan ukuran matriks similarity dari data yang dimiliki. Berdasarkan data yang ada, matriks berukuran 1047 buku x 1047 buku (masing-masing dalam sumbu X dan Y). Artinya, kita mengidentifikasi tingkat kesamaan pada 1047 nama buku. Tapi tidak ditampilkan semuanya. Oleh karena itu, hanya dipilih 10 restoran pada baris vertikal dan 5 restoran pada sumbu horizontal seperti pada contoh di atas. Semakin besar nilai dari output maka tingkat kemiripan buku semakin tinggi.
3. Mendapatkan Rekomendasi
  Untuk mengecek apakah bisa menampilkan rekomendasi buku atau tidak maka dicek terlebih dahulu dengan memasukkan nama buku yang ada di dataset, kemudian setelah buku tersebut tersedia maka dilakukan pencarian top 5 buku yang mirip dengan buku tersebut. Dari pencarian buku yang berjudul "A Little Princess" diperoleh buku lain yang memiliki kemiripan yaitu:

<img src="https://raw.githubusercontent.com/AmandaRiyas/Sistem-Rekomendasi/refs/heads/main/Gambar/Top%205.png" width="500"/>

Dari hasil Top 5 rekomendasi di atas maka buku A Little Princess memiliki kemiripan dengan "Loving Frank", "Skeleton Crew", "Lover Enshrined, part one", "The Complete Anne of Green Gables Boxed Set", dan "Anne of the Island"
  
Tahapan ini membahas mengenai model sisten rekomendasi yang Anda buat untuk menyelesaikan permasalahan. Sajikan top-N recommendation sebagai output.

## Evaluation
Pada bagian ini Anda perlu menyebutkan metrik evaluasi yang digunakan. Kemudian, jelaskan hasil proyek berdasarkan metrik evaluasi tersebut.

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
