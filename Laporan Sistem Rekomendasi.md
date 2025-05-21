# Laporan Proyek Machine Learning - Amanda Riyas Utami

## Project Overview

Terkadang banyak orang ingin membaca suatu buku yang sesuai dengan kesukaan mereka atau membaca buku yang mirip dengan buku yang pernah mereka cari atau pernah mereka baca. Namun banyak orang sering kesulitan mencari buku apa yang mirip dengan buku yang pernah mereka baca atau yang mereka cari. Hal ini tentu saja menjadi suatu perhatian khusus yang harus diselesaikan. Seharusnya ada suatu teknologi yang dapat membuat suatu rekomendasi mengenai buku apa yang sebaiknya mereka baca. Oleh karena itu dilakukan pemodelan rekomendasi sistem menggunakan content best filtering agar mereka bisa menemukan apa yang mereka cari. Dari penelitian terdahulu yang berjudul "Sistem Rekomendasi Buku Menggunakan Metode Content Best Filtering mendapatkan hasil bahwa Sistem rekomendasi buku dengan menggunakan teknik pembobotan TF-IDF dan algoritma cosine similarity dapat memberikan rekomendasi kepada pengguna sesuai dengan kemiripan data buku yang tersedia pada database, pada penelitiannya akurasi sistem rekomendasi buku menggunakan content best filtering memiliki tingkat akurasi precision sebesar 85% (Zayyad, 2021). Sehingga pada penelitian ini akan mencoba membuktikan apakah metode content best filtering bisa atau tidak memberikan akurasi yang akurat mengenai sistem rekomendasi buku.

## Business Understanding
Suatu perusahaan yang bergerak pada bidang penerbitan buku atau penjualan buku tentunya selalu mencari tahu minat pembaca dalam membaca buku itu apa saja. Perusahaan akan selalu melakukan analisis tren minat baca buku agar nantinya memperoleh keuntungan yang maksimal dalam penjualan bukunya. Oleh karen itu diperlukan suatu sistem untuk mencari buku apa saja yang menjadi minat pembaca saat ini dan buku apa saja yang hampir sama topiknya dengan apa yanng mereka baca. Hal ini tentunya dapat meningkatkan penjualan dengan lebih baik lagi karena apa yang dibutuhkan masyarakat dapat dicari di sistem rekomendasi dan perusahaan dapat menggunakan data ini untuk menerbitkan atau menjual buku sesuai yang diminati pembaca.

### Problem Statements
Membuat sistem rekomendasi yang dapat mencari tahu buku yang dapat direkomendasikan kepada pembaca sesuai apa yang mereka inginkan.

### Goals
Berhasil membuat sistem rekomendasi buku yang dapat memberikan rekomendasi buku semirip mungkin dengan apa yang mereka cari.

    ### Solution statements
    - Menggunakan content best filtering

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
