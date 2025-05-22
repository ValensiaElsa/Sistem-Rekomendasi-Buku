# Laporan Proyek Machine Learning - Valensia Elsa Kurnia
## Project Overview

![Cover Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/cover.jpg)

Seiring dengan berkembangnya platform digital, pengguna kini memiliki akses yang mudah ke berbagai buku, baik dalam bentuk fisik maupun digital. Namun, banyaknya pilihan buku yang tersedia seringkali membuat pengguna kesulitan dalam menemukan buku yang sesuai dengan minat atau preferensi mereka. Tanpa sistem yang tepat, pengguna dapat merasa kewalahan dalam memilih buku yang relevan. Oleh karena itu, dibutuhkan solusi berupa **sistem rekomendasi** yang mampu memberikan saran yang lebih personal dan relevan berdasarkan preferensi individu pengguna. Sistem rekomendasi ini sangat penting untuk meningkatkan pengalaman pengguna dalam mencari buku yang mereka sukai, serta mempercepat proses pemilihan buku.

Masalah utama yang perlu diselesaikan adalah bagaimana cara mengelola dan menyaring informasi yang sangat banyak dan beragam untuk memberikan rekomendasi yang tepat. Untuk itu, dua pendekatan utama dalam sistem rekomendasi yang relevan adalah **content-based filtering** dan **collaborative filtering**. **Content-based filtering** menggunakan informasi yang terkandung dalam buku, seperti isi konten buku, penulis, dan penerbit, untuk merekomendasikan buku yang memiliki kesamaan dengan buku yang telah dibaca oleh pengguna sebelumnya. Pendekatan ini akan diterapkan dalam proyek ini dengan menganalisis metadata buku yang telah dibaca oleh pengguna dan mencocokkannya dengan buku-buku lain yang memiliki kesamaan dalam hal genre, tema, atau penulis. Penelitian oleh Az Zayyad (2021) menunjukkan bahwa penerapan metode ini dapat memberikan rekomendasi yang relevan berdasarkan kemiripan konten yang disukai oleh pengguna [[1]](https://dspace.uii.ac.id/bitstream/handle/123456789/35942/17523144%20Muhammad%20Rizqi%20Az%20Zayyad.pdf?sequence=1).

Di sisi lain, **collaborative filtering** mengandalkan data interaksi pengguna, seperti rating, pembelian, atau preferensi pengguna lain yang memiliki pola yang serupa. Pendekatan ini akan diterapkan dalam proyek ini dengan mengumpulkan data interaksi pengguna seperti rating buku dan preferensi yang telah dipilih oleh pengguna sebelumnya. Dengan demikian, rekomendasi akan diberikan berdasarkan kesamaan pola preferensi antar pengguna yang memiliki kecenderungan yang mirip, tanpa memerlukan informasi mendalam tentang isi buku. Dzumiroh (2012) dalam penelitiannya menunjukkan bahwa **collaborative filtering** dapat memberikan rekomendasi yang efektif berdasarkan kesamaan preferensi antar pengguna yang mungkin tidak diketahui sebelumnya [[2]](https://jurnal.uns.ac.id/itsmart/article/viewFile/590/542).

Kedua pendekatan ini memiliki keunggulannya masing-masing. **Content-based filtering** lebih efektif ketika informasi konten buku lengkap dan mendalam, sedangkan **collaborative filtering** lebih cocok digunakan ketika data interaksi pengguna tersedia, meskipun informasi konten buku terbatas. Dengan memahami dan menerapkan kedua pendekatan ini secara terpisah, sistem rekomendasi buku dapat lebih akurat dalam membantu pengguna menemukan buku yang sesuai dengan minat mereka, serta meningkatkan pengalaman pengguna dalam memilih buku.

## Business Understanding
### Problem Statements
Berdasarkan uraian yang telah dipaparkan pada latar belakang diatas, maka dapat diambil sebuah rumusan masalah yang dirumuskan sebagai berikut:
- Berdasarkan data mengenai pengguna, bagaimana membuat sistem rekomendasi buku yang dipersonalisasi menggunakan teknik content-based filtering?
- Bagaimana memberikan rekomendasi buku yang relevan kepada pengguna berdasarkan pola preferensi pengguna lain yang serupa?

### Goals
Berdasarkan rumusan masalah yang telah dipaparkan di atas, maka proyek penelitian ini memiliki tujuan, yaitu:
- Menghasilkan rekomendasi buku yang dipersonalisasi untuk pengguna menggunakan teknik content-based filtering, dengan mempertimbangkan atribut seperti penulis dan penerbit buku yang telah dibaca.
- Membangun sistem rekomendasi buku yang dipersonalisasi untuk setiap pengguna dengan menggunakan Collaborative Filtering yang berbasis pada data rating dan interaksi pengguna lain dengan buku

### Solution Statements
- Menerapkan Content-Based Filtering: Menggunakan data tentang buku yang telah dibaca oleh pengguna, seperti penulis dan penerbit buku, untuk memberikan rekomendasi berdasarkan kesamaan atribut antara buku yang telah disukai atau dibaca oleh pengguna dan buku lainnya, menggunakan teknik seperti cosine similarity atau TF-IDF.
- Menerapkan Collaborative Filtering: Membangun sistem rekomendasi dengan memanfaatkan interaksi pengguna dengan buku (seperti rating atau preferensi eksplisit) untuk menganalisis pola kesamaan antar pengguna dan memberikan rekomendasi buku yang relevan berdasarkan kesamaan preferensi tersebut.

## Data Understanding

| Jenis | Keterangan |
| ------ | ------ |
| Title | [Book Recommendation Dataset](https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset) |
| Source | [Kaggle](https://www.kaggle.com) |
| Maintainer | [Möbius](https://www.kaggle.com/arashnic) |
| License | CC0: Public Domain |
| Visibility | Publik |
| Tags | Online Communities, Literature, Art, Recommender Systems, Culture and Humanities |
| Usability | 10.00 |

Dataset yang digunakan dalam proyek ini adalah [Book Recommendation Dataset](https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset) yang diperoleh dari Kaggle. Dataset ini berisi data dari Book-Crossing community yang mengumpulkan informasi tentang buku-buku yang telah dibaca oleh pengguna dan rating yang diberikan oleh pengguna terhadap buku tersebut. Dataset ini terdiri dari tiga file utama: Users, Books, dan Ratings, yang digunakan untuk membangun sistem rekomendasi buku berbasis content-based filtering dan collaborative filtering. Dataset ini mencakup 278,858 pengguna (yang teranonimkan tetapi dengan data demografi) dan 1,149,780 rating (baik eksplisit maupun implisit) mengenai 271,379 buku

### Deskripsi Data

Dataset ini terdiri dari tiga file utama yang berfungsi untuk membangun sistem rekomendasi buku:

1. **Books**: Menyediakan informasi tentang buku, termasuk ISBN, judul buku, penulis, penerbit, serta URL gambar sampul buku.
2. **Users**: Menyediakan informasi demografis pengguna, termasuk ID pengguna, lokasi, dan usia.
3. **Ratings**: Berisi informasi tentang rating yang diberikan oleh pengguna terhadap buku-buku tertentu, baik yang eksplisit (1-10) maupun implisit (0).

### Variabel-variabel pada Book Recommendation dataset:
#### Books Dataset:

| # | Column              | Dtype  |
| - | ------------------- | ------ |
| 0 | ISBN                | object |
| 1 | Book-Title          | object |
| 2 | Book-Author         | object |
| 3 | Year-Of-Publication | object |
| 4 | Publisher           | object |
| 5 | Image-URL-S         | object |
| 6 | Image-URL-M         | object |
| 7 | Image-URL-L         | object |

- **ISBN**: Nomor ISBN yang digunakan untuk mengidentifikasi buku.
- **Book-Title**: Judul buku.
- **Book-Author**: Penulis buku (hanya penulis pertama jika ada lebih dari satu).
- **Year-Of-Publication**: Tahun terbit buku.
- **Publisher**: Penerbit buku.
- **Image-URL-S**: URL gambar sampul buku dalam ukuran kecil.
- **Image-URL-M**: URL gambar sampul buku dalam ukuran medium.
- **Image-URL-L**: URL gambar sampul buku dalam ukuran besar.

#### Users Dataset:

| # | Column   | Dtype  |
| - | -------- | ------ |
| 0 | User-ID  | int64  |
| 1 | Location | object |
| 2 | Age      | float64  |

- **User-ID**: ID pengguna yang telah dianonimkan.
- **Location**: Lokasi pengguna (NULL jika tidak tersedia).
- **Age**: Umur pengguna (NULL jika tidak tersedia).

#### Ratings Dataset:

| # | Column      | Dtype  |
| - | ----------- | ------ |
| 0 | User-ID     | int64  |
| 1 | ISBN        | object |
| 2 | Book-Rating | int64  |

- **User-ID**: ID pengguna yang memberikan rating pada buku.
- **ISBN**: ISBN buku yang diberi rating.
- **Book-Rating**: Rating yang diberikan oleh pengguna, dengan rentang nilai 1-10 (nilai 0 menandakan rating implisit).

### Data Understanding untuk Book.csv
- **Pengecekan Informasi Awal**
  
  ![Book Info Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/books_info.png)

  Berdasarkan hasil pemanggilan fungsi `books.info()`, dataset Books.csv terdiri dari 271,360 entri dengan 8 kolom. Kolom-kolom ini menyimpan informasi penting mengenai buku, seperti ISBN, Book-Title, Book-Author, Year-Of-Publication, dan Publisher, yang akan digunakan dalam proses rekomendasi. Kolom Year-Of-Publication saat ini bertipe data object, padahal seharusnya kolom ini bertipe data int64 untuk merepresentasikan tahun terbit buku. Oleh karena itu, tipe data pada kolom ini perlu diubah menjadi int agar dapat digunakan dengan benar dalam analisis dan model prediksi.

  Selain itu, beberapa kolom seperti Image-URL-S, Image-URL-M, dan Image-URL-L berisi URL gambar sampul buku dalam tiga ukuran berbeda (kecil, medium, dan besar). Kolom-kolom ini tidak relevan dalam konteks sistem rekomendasi berbasis content-based filtering dan collaborative filtering, sehingga sebaiknya dihapus agar tidak menambah kompleksitas data.

- **Pengecekan Missing Value**

  Langkah selanjutnya adalah memeriksa apakah ada data yang hilang (missing values) pada setiap fitur. Untuk pengecekan missing values, kode berikut digunakan:
  ```python
  # Memeriksa missing value
  books.isnull().sum()
  ```

  ![Missing Book Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/missing_books.png)

  Berdasarkan hasil pemeriksaan terhadap nilai yang hilang dalam dataset **Books.csv**, terdapat beberapa kolom yang memiliki nilai yang hilang (missing values). Kolom `Book-Author` memiliki 2 entri yang kosong, yang menunjukkan bahwa beberapa buku tidak memiliki informasi mengenai penulisnya. Hal yang sama berlaku pada kolom `Publisher`, yang juga memiliki 2 entri kosong, menandakan bahwa ada beberapa buku yang tidak tercatat penerbitnya. Meskipun jumlahnya relatif kecil, data yang hilang ini perlu ditangani, baik dengan imputasi atau penghapusan data, terutama karena kedua kolom tersebut berperan penting dalam proses rekomendasi berbasis konten. Selain itu, penting untuk memeriksa kolom mana saja yang kosong untuk mempermudah proses imputasi, agar kita dapat memilih metode imputasi yang tepat. Berdasarkan hasil pengecekan, missing value `Book Author` berada pada kolom 118033 dan 187689 dan missing value `Publisher` berada pada kolom 128890 dan 129037.

  ![Missing Author Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/missing_author.png)

  ![Missing Publisher Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/missing_publisher.png)

  Kolom **Image-URL-S**, **Image-URL-M**, dan **Image-URL-L** memiliki sedikit atau tanpa nilai yang hilang. Kolom **Image-URL-S** dan **Image-URL-M** tidak memiliki entri yang kosong, sementara kolom **Image-URL-L** hanya memiliki 3 entri yang kosong. Namun, karena kolom gambar ini tidak relevan untuk sistem rekomendasi berbasis **content-based filtering** dan **collaborative filtering**, kolom-kolom ini akan dihapus dari dataset sehingga tidak perlu dilakukan penanganan.

- **Pengecekan Invalid Data**

  ![Invalid Year Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/invalid_year.png)

  Dari hasil pemeriksaan pada kolom Year-Of-Publication, ditemukan dua entri yang tidak sesuai dengan format yang diharapkan, di mana kolom ini berisi nama penerbit seperti "DK Publishing Inc" dan "Gallimard", padahal kolom tersebut seharusnya hanya berisi tahun penerbitan buku. Setelah pengecekan, terdapat kesalahan input yang menyebabkan data pada beberapa kolom tergeser. Terdapat tiga entri pada kolom Book-Author di mana nama penulis tercampur dengan judul buku dalam satu kolom, yang jelas merupakan kesalahan format data. 

  ![Invalid Year Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/invalid_year_proof.png)

  Untuk memperbaiki hal ini, perlu dilakukan pemisahan antara nama penulis dan judul buku yang tercampur, serta memperbaiki nilai pada kolom Year-Of-Publication agar sesuai dengan format yang benar, sehingga dataset menjadi lebih konsisten dan siap untuk digunakan dalam analisis dan pengembangan sistem rekomendasi.

  Selanjutnya, kita memeriksa apakah terdapat **karakter non-alfanumerik** pada kolom ISBN dalam data rating. Dari hasil pengecekan, menggunakan flag, ditemukan bahwa **ada karakter non-alfanumerik** yang tidak sesuai dengan format yang diharapkan, sehingga perlu dilakukan perbaikan pada data tersebut. Flag diatur menjadi 1 saat karakter non-alfanumerik ditemukan, yang menandakan bahwa ada masalah dalam data ISBN yang perlu diperbaiki.

- **Pengecekan Data Duplikat**

  Selanjutnya, kita memeriksa apakah ada data duplikat di dalam dataset. Data duplikat dapat terjadi akibat kesalahan saat pengumpulan atau proses input data. Untuk pengecekan data duplikat, kode berikut digunakan:

  ```python
  # Memeriksa duplikasi data 
  jumlah_duplikat = books.duplicated().sum()
  print(f"Jumlah baris duplikat: {jumlah_duplikat}") 
  ```

  Namun, pada dataset ini, **tidak ditemukan duplikat**, yang berarti setiap entri dalam dataset adalah unik dan tidak ada baris yang terduplikasi.

### Data Understanding untuk Users.csv
- **Pengecekan Informasi Awal**
  
  ![Users Head Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/users_head.png)

  Berdasarkan pemeriksaan awal menggunakan fungsi `head()` pada dataset Users, ditemukan bahwa kolom Location menggabungkan informasi tentang kota, negara bagian, dan negara dalam satu kolom, seperti yang terlihat pada contoh "nyc, new york, usa". Meskipun kolom Location tidak digunakan dalam model rekomendasi berbasis Collaborative Filtering dan Content-Based Filtering, penting untuk melakukan pembersihan data terlebih dahulu. Pemisahan kolom Location menjadi City, State, dan Country dapat menjaga konsistensi data dan mempermudah pengelolaan data di masa depan, terutama jika terdapat perkembangan model yang memerlukan informasi lokasi.

  ![Users Info Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/users_info.png)

  Berdasarkan hasil pemeriksaan dengan menggunakan fungsi `info()` pada dataset Users, terdapat tiga kolom utama: User-ID, Location, dan Age. Kolom User-ID memiliki tipe data int64, yang sudah sesuai untuk mewakili ID pengguna. Kolom Age memiliki tipe data float64, yang juga sudah tepat karena usia bisa berupa angka desimal pada beberapa kasus.

- **Pengecekan Missing Value**

  ![Users Missing Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/missing_users.png)

  Berdasarkan hasil pemeriksaan terhadap nilai yang hilang (missing values) menggunakan fungsi isnull().sum() pada dataset Users, ditemukan bahwa kolom Age memiliki 110,762 entri yang kosong. Meskipun kolom Age tidak digunakan dalam model rekomendasi berbasis Content-Based Filtering dan Collaborative Filtering, penting untuk menangani nilai yang hilang pada kolom ini untuk menjaga konsistensi data. Salah satu cara untuk mengatasi masalah ini adalah dengan mengisi nilai yang hilang menggunakan nilai rata-rata (mean) dari kolom Age, yang dapat dilakukan dengan imputasi.

- **Pengecekan Invalid Data**

  ![Invalid Age Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/invalid_age.png)

  Berdasarkan hasil pengecekan data pada kolom Age, dapat dilihat bahwa bahwa terdapat nilai NaN (missing values) dalam data usia. Setelah disortir, terdapat berbagai rentang usia yang tercatat dalam dataset. Rentang usia ini bervariasi dari 0 hingga 244. Ada beberapa nilai usia yang lebih tinggi (lebih dari 80), yang bisa jadi merupakan entri yang tidak valid atau mungkin hasil kesalahan input.

  Untuk memastikan bahwa data ini valid dan konsisten, data usia akan dianalisis lebih lanjut melalui visualisasi pada tahap Exploratory Data Analysis (EDA). Dengan menggunakan grafik distribusi atau histogram, kita dapat mengeksplorasi lebih dalam pola distribusi usia, mengidentifikasi nilai yang tidak wajar, dan mengevaluasi apakah ada kebutuhan untuk melakukan penyesuaian atau imputasi pada nilai usia yang tidak valid.

- **Pengecekan Data Duplikat**

  Selanjutnya, kita memeriksa apakah ada data duplikat di dalam dataset. Berdasarkan hasil pemeriksaan terhadap duplikasi data menggunakan fungsi `.duplicated()` pada dataset users, ditemukan bahwa **tidak ada baris duplikat** dalam dataset tersebut.

### Data Understanding untuk Ratings.csv
- **Pengecekan Informasi Awal**
  
  ![Ratings Info Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/ratings_info.png)

  Berdasarkan hasil pemeriksaan dataset ratings menggunakan fungsi `info()`, dataset ini terdiri dari 1.149.780 entri dengan 3 kolom, yaitu User-ID, ISBN, dan Book-Rating. Semua kolom memiliki jumlah data yang tidak hilang (non-null), artinya tidak ada missing value dalam dataset ratings, yang sangat baik untuk kelancaran proses analisis dan model prediksi.

  Tipe data pada kolom User-ID dan Book-Rating sudah sesuai dengan tipe data yang diharapkan, yaitu int64 untuk data numerik, sedangkan kolom ISBN bertipe object. Untuk kolom ISBN, meskipun bertipe object, ini adalah tipe data yang sesuai karena ISBN bersifat alfanumerik dan terdiri dari karakter yang dapat berbeda.

- **Pengecekan Missing Value**
  
  ![Missing Ratings Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/missing_ratings.png)
  
  Berdasarkan hasil pemeriksaan menggunakan fungsi `isnull().sum()` pada dataset ratings, terlihat bahwa tidak ada nilai yang hilang (missing values) pada ketiga kolom, yaitu User-ID, ISBN, dan Book-Rating. Semua kolom memiliki 0 nilai kosong, yang berarti dataset ini sudah lengkap dan tidak memerlukan penanganan missing values. 

- **Pengecekan Invalid Data**
  
  Dengan metode yang sama untuk pengecekan ISBN pada dataset books, atribut ISBN pada dataset ratings juga diperiksa. Berdasarkan hasil pemeriksaan, ditemukan bahwa **ada karakter non-alfanumerik dalam kolom ISBN** pada data ratings. Untuk memastikan integritas data dalam sistem rekomendasi, hal ini perlu segera diperbaiki. ISBN seharusnya hanya berisi angka dan huruf yang valid, tanpa karakter khusus seperti simbol atau spasi. Oleh karena itu, perlu dilakukan pembersihan data dengan memperbaiki entri ISBN yang mengandung karakter non-alfanumerik.

  ![Ratings Describe Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/ratings_describes.png)

  Berdasarkan hasil deskripsi statistik dari dataset ratings, terdapat beberapa informasi penting yang perlu diperhatikan terkait dengan kolom Book-Rating. Kolom ini berisi nilai rating dari pengguna terhadap buku, dengan nilai minimum 0 dan maksimum 10. Nilai 0 menunjukkan bahwa rating tersebut bersifat implisit atau tidak ada rating yang diberikan untuk buku tertentu, yang biasanya digunakan untuk menandakan ketidaktertarikan atau tidak ada interaksi dengan buku tersebut.
Oleh karena itu, untuk menjaga kualitas rekomendasi dan menghindari data yang tidak memberikan kontribusi, nilai 0 dalam kolom Book-Rating harus dihapus dari dataset. Hal ini akan memastikan bahwa hanya interaksi yang relevan, yakni yang memiliki rating lebih tinggi dari 0, yang digunakan dalam proses pembuatan model rekomendasi berbasis collaborative filtering.

- **Pengecekan Data Duplikat**

  Berdasarkan hasil pemeriksaan terhadap data ratings, **tidak ditemukan adanya baris duplikat** pada dataset. Hal ini menandakan bahwa setiap entri pada data ratings adalah unik, yang penting untuk memastikan bahwa setiap interaksi pengguna dengan buku dihitung secara terpisah dan tidak terjadi redundansi dalam informasi yang diberikan kepada model rekomendasi.

## Exploratory Data Analysis (EDA)
### Univariate Analysis
- **Analisis Distribusi Data Kategorikal**
  
  ![Distribusi Penulis Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/distribusi_penulis.png)
  
  Berdasarkan analisis distribusi penulis, ditunjukkan bahwa Agatha Christie adalah penulis dengan jumlah buku terbanyak, melebihi 600 judul, diikuti oleh William Shakespeare dan Stephen King dengan jumlah buku mendekati 500-600 judul. Penulis lain seperti Ann M. Martin, Carolyn Keene, dan Isaac Asimov juga memiliki jumlah buku yang signifikan, sekitar 300-400 judul. Selain itu, terdapat juga beberapa penulis lain dengan lebih dari satu judul buku. Penulis dengan jumlah buku yang lebih banyak cenderung memiliki representasi konten yang lebih besar. Dalam content-based filtering, ini berarti pengguna yang menyukai karya penulis yang sangat produktif seperti Agatha Christie mungkin akan lebih sering direkomendasikan buku lain dari penulis yang sama atau yang memiliki kemiripan konten. Sementara itu, dalam collaborative filtering, popularitas penulis dengan banyak buku dapat tercermin dalam data interaksi pengguna, yang berpotensi menghasilkan rekomendasi yang lebih sering untuk karya-karya mereka.

  ![Distribusi Penerbit Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/distribusi_penerbit.png)
  
  Dari visualisasi tersebut, dapat disimpulkan bahwa Harlequin adalah penerbit dengan jumlah buku terbanyak secara signifikan dibandingkan penerbit lain. Penerbit-penerbit berikutnya seperti Silhouette, Pocket, dan Ballantine Books memiliki jumlah buku yang relatif lebih seimbang namun jauh lebih sedikit dibanding Harlequin. Kondisi ini menunjukkan dominasi Harlequin dalam koleksi buku yang dapat mempengaruhi fokus analisis dan sistem rekomendasi, khususnya pada content-based filtering dan pola interaksi pengguna dalam collaborative filtering.
 
- **Analisis Distribusi Data Numerik**
  
  ![Distribusi Umur Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/distribusi_umur.png)
  
  Distribusi umur pengguna menunjukkan adanya potensi data yang tidak valid, terutama pada rentang umur mendekati 0 dan di atas 100 tahun. Keberadaan data umur yang invalid dapat mempengaruhi akurasi sistem rekomendasi jika umur digunakan sebagai fitur (meskipun dalam konteks Content-Based Filtering dan Collaborative Filtering tidak digunakan). Oleh karena itu, langkah-langkah penanganan data invalid perlu dilakukan. Mengingat jumlah data invalid yang signifikan, diputuskan untuk menerapkan metode imputasi dalam penanganan data ini dengan menggunakan nilai rata-rata (mean).
  
  ![Distribusi Rating Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/distribusi_rating.png)
  
  Visualisasi distribusi rating buku memperjelas dominasi rating 0 dalam dataset, yang mengindikasikan sejumlah besar interaksi implisit atau tidak adanya rating eksplisit. Nilai 0 harus dihapus untuk memfokuskan analisis pada preferensi pengguna yang terungkap melalui rating positif (1 hingga 10). Penghapusan ini akan menghasilkan dataset yang lebih kecil namun berpotensi lebih relevan untuk mengidentifikasi preferensi pengguna yang sebenarnya dalam pengembangan sistem rekomendasi berbasis collaborative filtering.

### Bivariate Analysis

![Most Rated Book Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/most_rated_book.png)

Visualisasi Buku yang Paling Banyak Diberikan Rating mengidentifikasi 'Wild Animus' sebagai buku yang menerima rating terbanyak secara signifikan, diikuti oleh 'The Lovely Bones: A Novel'. Buku-buku dengan jumlah rating tinggi ini mengindikasikan popularitas yang besar di kalangan pengguna dan dapat menjadi rekomendasi yang kuat dalam sistem. Data ini penting karena buku-buku populer sering kali memiliki banyak rating positif, menjadikannya kandidat yang baik untuk direkomendasikan kepada pengguna lain.

![Distribusi Pengguna Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/distribusi_pengguna.png)

Visualisasi pengguna yang memberikan rating terbanyak menunjukkan bahwa pengguna dengan ID 11676 secara signifikan memberikan rating untuk jumlah buku yang jauh lebih banyak dibandingkan pengguna lain dalam dataset. Pengguna-pengguna aktif seperti ini sangat berharga untuk pengembangan model collaborative filtering karena menyediakan data preferensi yang kaya dan beragam. Rating dari pengguna dengan banyak interaksi dapat membantu algoritma dalam mengidentifikasi pola kesamaan antar pengguna dan meningkatkan kualitas rekomendasi. 

## Data Preparation
Tahapan data preparation penting dilakukan dalam membangun sistem rekomendasi. Preparation yang dilakukan adalah sebagai berikut:

- **Penghapusan Kolom yang Tidak Diperlukan (_dropping coloumns_)**
  
  Tiga kolom yang berisi URL gambar buku, yaitu 'Image-URL-S', 'Image-URL-M', dan 'Image-URL-L', dihapus dari DataFrame books. Kode yang digunakan untuk drop kolom adalah sebagai berikut:
  ```python
  # Drop URL columns
  books.drop(['Image-URL-S', 'Image-URL-M', 'Image-URL-L'], axis=1, inplace=True)
  ```
  Proses ini dilakukan dengan menentukan nama-nama kolom yang akan dihapus dan menggunakan parameter axis=1 untuk mengindikasikan penghapusan berdasarkan kolom, serta inplace=True untuk menerapkan perubahan langsung pada DataFrame. Penghapusan kolom URL gambar ini diperlukan karena informasi tersebut tidak relevan untuk pemodelan rekomendasi berbasis konten maupun kolaboratif, dapat mengurangi dimensi data yang tidak perlu, memfokuskan analisis pada fitur-fitur yang lebih bermakna dalam menentukan kemiripan buku atau preferensi pengguna, serta menyederhanakan proses pemodelan dengan menghilangkan potensi kompleksitas pemrosesan data gambar.

- **Penanganan Missing Value**
  
  Penanganan missing value merupakan langkah krusial dalam persiapan data untuk sistem rekomendasi. Dalam dataset **books**, teknik imputasi dengan nilai 'Other' diterapkan pada kolom 'Book-Author' dan 'Publisher' untuk mengatasi nilai yang hilang pada baris-baris tertentu.
  ```python
  # Menetapkan nilai 'Other' pada kolom 'Book-Author' di baris 187689
  books.loc[187689, 'Book-Author'] = 'Other'
  ```
  Sementara itu, pada dataset **users**, teknik imputasi dengan nilai rata-rata (mean imputation) digunakan untuk mengisi nilai yang hilang (NaN) pada kolom 'Age' dengan nilai rata-rata usia dari seluruh pengguna.
  ```python
  # Mengganti nilai NaN atau data yang tidak valid (misalnya nilai negatif) dengan rata-rata usia
  users['Age'] = users['Age'].apply(lambda x: mean_age if pd.isna(x) else x)
  ```
  Tindakan ini diperlukan untuk memastikan bahwa dataset bebas dari nilai yang hilang yang dapat mengganggu proses pemodelan algoritma rekomendasi. Imputasi memungkinkan untuk mempertahankan sebagian besar informasi dalam dataset dibandingkan dengan penghapusan baris, sekaligus menciptakan data yang lebih konsisten dan dapat diandalkan. Pengisian dengan nilai yang representatif menjaga informasi yang ada dan membuat model lebih stabil.

- **Standarisasi Format**
  
  Dalam tahapan persiapan data, standarisasi format diterapkan pada kolom ISBN yang terdapat baik dalam dataset books maupun ratings. Proses ini melibatkan pengubahan seluruh karakter dalam kolom 'ISBN' menjadi huruf kapital menggunakan fungsi `.str.upper()` pada kedua dataset. Standarisasi format penting untuk menjaga konsistensi dalam penggabungan data, terutama saat menggunakan ISBN sebagai kunci penghubung antar dataset. Dengan mengubah ISBN menjadi format seragam, kita menghindari masalah kesalahan pencocokan data antara dataset books dan ratings yang disebabkan oleh perbedaan format penulisan. Konsistensi ini sangat penting untuk operasi penggabungan data (merging atau joining) berdasarkan ISBN.

- **Penanganan Invalid Data**
  
  Penanganan data tidak valid merupakan serangkaian proses krusial dalam mempersiapkan dataset sebelum digunakan untuk membangun sistem rekomendasi yang efektif. Tujuannya adalah untuk mengidentifikasi dan memperbaiki atau mengatasi data yang tidak akurat, tidak konsisten, atau tidak relevan, sehingga kualitas informasi yang digunakan dalam pelatihan model menjadi lebih baik dan menghasilkan rekomendasi yang lebih handal. Beberapa teknik spesifik diterapkan pada dataset books, users, dan ratings untuk mencapai tujuan ini.
  
  **Mengatasi Kesalahan Data yang Tergeser**
  
  Pada dataset books, langkah pertama adalah **pembaharuan data yang teridentifikasi atau explicit value replacement**.
  
  ```python
  # Memperbarui informasi di baris 209538
  books.loc[209538, 'Publisher'] = 'DK Publishing Inc'
  books.loc[209538, 'Year-Of-Publication'] = 2000
  books.loc[209538, 'Book-Title'] = 'DK Readers: Creating the X-Men, How It All Began (Level 4: Proficient Readers)'
  books.loc[209538, 'Book-Author'] = 'Michael Teitelbaum'
  ```
  
  Teknik ini melibatkan penggantian nilai-nilai spesifik yang diketahui salah atau tidak akurat dengan nilai yang benar. Pada baris-baris tertentu, informasi seperti nama penerbit, tahun publikasi, judul buku, atau nama penulis yang keliru diperbaiki secara manual berdasarkan data understanding yang sudah dilakukan sebelumnya. Tindakan ini penting untuk memastikan bahwa informasi dasar buku dalam dataset akurat dan dapat diandalkan. Berikut adalah hasil data setelah dilakukan perbaikan.

  ![Penanganan Data Geser Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/data_geser.png)
  
  **Mengubah Invalid Years pada "Years-of-Publication"**
  
  Selanjutnya, **konversi tipe data atau data type conversion** diterapkan pada kolom **'Year-Of-Publication'**. Mengubah tipe data menjadi integer memastikan bahwa tahun publikasi dapat diolah dengan benar dalam analisis numerik, seperti perhitungan usia buku atau pengelompokan berdasarkan periode publikasi, serta menghindari potensi kesalahan interpretasi jika kolom tersebut masih berupa string atau tipe data lainnya. Untuk mengatasi data tahun publikasi yang jelas-jelas tidak valid, seperti nilai 0 atau tahun yang jauh di masa depan (melebihi 2025), digunakan teknik imputasi dengan nilai mode atau **mode imputation**. Kode yang digunakan adalah sebagai berikut:
   ```python
   mode_year = books['Year-Of-Publication'].mode()[0]
   # Terapkan perubahan pada kolom 'Year-Of-Publication'
   books['Year-Of-Publication'] = books['Year-Of-Publication'].apply( lambda x:   mode_year if x == 0 or x > 2025 else x)
  ```
   
  **Menghapus Karakter Tidak Valid pada Kolom ISBN**
  
  Untuk memastikan integritas kode International Standard Book Number (ISBN), diterapkan teknik **penghapusan karakter tidak valid atau invalid character removal**. Teknik ini melibatkan identifikasi dan penghilangan karakter-karakter selain huruf (A-Z, a-z) dan angka (0-9) dari setiap nilai dalam kolom 'ISBN' pada dataset books dan ratings. Kode pembersihan adalah sebagai berikut
  ```python
  def clean_isbn(isbn):
    return re.sub(r'[^A-Za-z0-9]', '', isbn)
  ```
  Proses ini bertujuan untuk membersihkan kode ISBN dari karakter-karakter yang tidak sesuai dengan format standar. Penghapusan karakter tidak valid ini krusial karena beberapa alasan. Pertama, memastikan format ISBN yang benar adalah langkah penting untuk identifikasi buku yang akurat. ISBN adalah pengidentifikasi unik, dan karakter-karakter selain alfanumerik dapat mengganggu proses identifikasi dan pencocokan buku. Kedua, meningkatkan kualitas data dengan menghilangkan noise yang mungkin timbul akibat kesalahan input atau perbedaan format. Data yang bersih akan meminimalkan potensi kesalahan saat menghubungkan informasi buku antar dataset (books dan ratings). Ketiga, memfasilitasi matching data yang akurat berdasarkan kode ISBN. Sistem rekomendasi seringkali memerlukan penggabungan informasi dari berbagai sumber menggunakan ISBN sebagai kunci penghubung. Jika ISBN mengandung karakter yang tidak valid, proses matching bisa menjadi tidak efektif.

  **Mengubah Nilai Invalid Age**
  
  Pada dataset **users**, penanganan data tidak valid dilakukan pada kolom 'Age' dan 'Location'. Untuk kolom 'Age', digunakan teknik imputasi dengan nilai rata-rata atau **mean imputation** untuk mengganti nilai-nilai usia yang di luar batas wajar (kurang dari 10 atau lebih dari 80 tahun). Asumsi di balik ini adalah bahwa nilai-nilai ekstrem kemungkinan merupakan kesalahan input, dan menggantinya dengan nilai rata-rata usia pengguna secara keseluruhan akan mempertahankan distribusi usia yang lebih realistis dalam dataset.

  **Memisahkan Lokasi (City, State, Country)**
  
  Pada kolom 'Location', diterapkan teknik **ekstraksi informasi atau information extraction** dan **pemisahan data atau data splitting**. Informasi lokasi yang awalnya mungkin berupa string gabungan (misalnya, "city, state, country") dipecah menjadi tiga kolom terpisah ('City', 'State', 'Country'). Teknik ekstraksi informasi dan pemisahan data pada kolom 'Location' di dataset users diterapkan dengan tujuan untuk mendapatkan informasi geografis yang lebih terstruktur dan spesifik mengenai pengguna. Alasan utama dilakukannya tahapan ini adalah untuk memungkinkan analisis preferensi pengguna berdasarkan lokasi geografis mereka. Informasi lokasi dalam format string gabungan (seperti "city, state, country") sulit untuk dianalisis secara langsung atau digunakan sebagai fitur dalam model rekomendasi. Dengan memecahnya menjadi kolom-kolom terpisah, kita mendapatkan data yang lebih granular dan mudah diolah.  Berikut adalah hasil setelah data Location dipisah menjadi City, State, dan Country.
  
  ![Penanganan Lokasi Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/penanganan_lokasi.png)

  **Menghapus Rating dengan Nilai 0**
  
  Terakhir, penanganan invalid data 'Book-Rating' pada dataset **ratings** dilakukan dengan teknik **pemfilteran data atau data filtering** dengan menghapus baris-baris di mana nilai pada kolom 'Book-Rating' adalah 0. Proses ini dilakukan dengan memilih baris-baris di mana nilai 'Book-Rating' tidak sama dengan 0.
  ```python
  ratings = ratings[ratings['Book-Rating'] != 0]
  ratings = ratings.reset_index(drop = True)
  ```
  Penghapusan rating 0 diperlukan karena nilai ini sering diartikan sebagai ketidaktertarikan atau tidak adanya rating eksplisit, sehingga dapat mengintroduksi noise dan mengaburkan sinyal preferensi pengguna yang sebenarnya dalam analisis collaborative filtering. Dengan memfokuskan data hanya pada rating positif, diharapkan model rekomendasi dapat mempelajari preferensi pengguna dengan lebih akurat dan menghasilkan rekomendasi yang lebih relevan.

  Secara keseluruhan, serangkaian teknik penanganan data tidak valid ini sangat penting untuk memastikan bahwa data yang digunakan dalam membangun sistem rekomendasi adalah data yang bersih, akurat, konsisten, dan relevan. Data yang berkualitas tinggi akan menghasilkan model rekomendasi yang lebih baik dalam memahami preferensi pengguna dan memberikan rekomendasi yang lebih tepat sasaran.

- **Penghapusan Baris Duplikat**
  
  Sebagai langkah terakhir dalam pembersihan data, dilakukan pengecekan dan penghapusan baris-baris duplikat. Proses ini melibatkan identifikasi baris-baris yang memiliki nilai identik di seluruh kolom dalam dataset menggunakan fungsi `duplicated().sum()`. Meskipun pada tahap data understanding tidak ditemukan adanya baris duplikat, berbagai operasi pemrosesan data yang telah dilakukan (seperti imputasi, standardisasi, atau pemisahan data) berpotensi menimbulkan duplikasi. Berdasarkan pengecekan terdapat beberapa baris duplikat pada dataset.
  
  ![Duplikasi Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/duplikasi.png)
  
  Setelah baris duplikat teridentifikasi, baris-baris tersebut dihapus dengan fungsi `drop_duplicates()`. Tahapan ini diperlukan karena keberadaan baris duplikat dapat mengganggu integritas data dengan merepresentasikan entitas yang sama berulang kali, yang dapat menciptakan bias dalam pemodelan sistem rekomendasi dengan memberikan bobot berlebih pada pola yang sebenarnya tidak unik. Selain itu, penghapusan duplikat meningkatkan efisiensi pemrosesan dengan mengurangi ukuran dataset yang tidak perlu dan memastikan keakuratan metrik evaluasi model dengan mencegah perhitungan ganda entitas yang sama. Dengan dataset yang bebas dari baris duplikat, model rekomendasi yang dibangun akan lebih handal dan mampu memberikan rekomendasi yang lebih akurat dan representatif, terutama setelah melalui berbagai transformasi data.

- **Merging Dataset dan Sampling**
  
  Tahapan persiapan data selanjutnya melibatkan penggabungan dataset (merging) dan pengambilan sampel (sampling). Proses penggabungan dilakukan dengan menggunakan fungsi pd.merge() sebanyak dua kali.
  ```python
  dataset = pd.merge(books, ratings, on='ISBN', how='inner')
  dataset = pd.merge(dataset, users, on='User-ID', how='inner')
  ```
  Pertama, DataFrame books dan ratings digabungkan berdasarkan kolom 'ISBN' dengan metode 'inner', menghasilkan DataFrame dataset yang berisi hanya baris dengan nilai 'ISBN' yang sama di kedua DataFrame. Kemudian, DataFrame dataset ini digabungkan kembali dengan DataFrame users berdasarkan kolom 'User-ID' juga menggunakan metode 'inner'. Penggabungan ini bertujuan untuk mengintegrasikan informasi buku, rating pengguna, dan informasi pengguna ke dalam satu DataFrame yang komprehensif, yang esensial untuk membangun sistem rekomendasi yang efektif. Metode 'inner' memastikan hanya data yang lengkap dari ketiga sumber yang disertakan. Penggabungan dataset memungkinkan kita untuk mengintegrasikan informasi yang relevan dari berbagai sumber, yang esensial untuk pemodelan rekomendasi yang efektif.
  
  Setelah penggabungan, dilakukan pengambilan sampel (sampling) dengan menggunakan fungsi `dataset.sample(n=10000, random_state=42)` untuk memilih secara acak 10000 baris dari DataFrame dataset. Pengambilan sampel ini dilakukan untuk mengurangi beban komputasi selama tahap pengembangan dan eksperimen model, terutama ketika dataset terlalu besar. Penggunaan random_state memastikan hasil pengambilan sampel yang konsisten dan dapat direproduksi. Dengan demikian, penggabungan dataset menyediakan data terintegrasi yang diperlukan, sementara pengambilan sampel memungkinkan pengelolaan sumber daya komputasi yang lebih efisien dalam proses pengembangan sistem rekomendasi.
  Berikut adalah struktur dataset setelah dilakukan penggabungan dan sampling:
  
  ![Data Clean Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/data_clean.png)

### Persiapan Content-Based Filtering
- **Konversi dalam Bentuk List**
  
  Dalam mempersiapkan data untuk pembangunan sistem rekomendasi berbasis content-based filtering, salah satu teknik konversi tipe data krusial dilakukan dengan mengubah kolom-kolom kunci dari DataFrame menjadi format list Python. Proses ini mencakup konversi kolom 'Book-Title', 'Book-Author', 'Publisher', dan 'ISBN' dari pandas Series menjadi list terpisah menggunakan fungsi `tolist()`, yang masing-masing disimpan dalam variabel book_title, book_author, publisher, dan isbn. Tahapan ini sangat diperlukan karena banyak teknik pemrosesan teks dan pembuatan matriks fitur yang menjadi inti dari content-based filtering (seperti TF-IDF) mengharapkan input dalam format list Python. Konversi ini memastikan kompatibilitas data dengan berbagai library dan algoritma yang akan digunakan untuk mengekstrak fitur konten buku, sehingga memfasilitasi analisis kemiripan antar buku secara efisien.
- **Membuat DataFrame Baru**
  
  Dalam mempersiapkan data untuk content-based filtering, langkah penting selanjutnya adalah **strukturisasi data** melalui pembuatan *pandas DataFrame* baru. Proses ini melibatkan pembentukan dictionary Python bernama `book_data` yang memetakan kunci-kunci seperti 'book_title', 'book_author', dan 'publisher' ke *list* data yang sesuai. Dictionary ini kemudian diubah menjadi *pandas DataFrame* dengan nama yang sama (`book_data`) menggunakan fungsi `pd.DataFrame()`. Pembuatan DataFrame ini bertujuan untuk mengorganisir fitur-fitur konten buku ke dalam struktur tabular yang efisien dan mudah diakses. Struktur ini memfasilitasi tahapan selanjutnya dalam content-based filtering, di mana fitur-fitur seperti judul dan penulis akan dianalisis lebih lanjut untuk mengekstrak representasi numerik yang dapat digunakan dalam algoritma perbandingan kemiripan antar buku dan menghasilkan rekomendasi yang relevan berdasarkan preferensi pengguna terhadap konten buku.
  
  ![List Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/list.png)
  
- **Menghapus Duplikasi DataFrame Baru**
  
  Dalam mempersiapkan data untuk content-based filtering, langkah penting selanjutnya adalah penghapusan duplikasi dari DataFrame book_data.  Hal ini dapat terjadi karena satu buku dapat memiliki beberapa entri akibat adanya rating berbeda pada dataset yang telah di-cleaning. Proses ini diawali dengan mengidentifikasi jumlah baris duplikat, yang dalam kasus ini ditemukan sebanyak **12553 baris**. Kemudian, fungsi `.drop_duplicates()` digunakan dengan fokus pada kolom 'book_title' sebagai subset pertimbangan duplikasi. Penghapusan duplikasi berdasarkan judul buku ini krusial untuk memastikan bahwa setiap buku direpresentasikan secara unik dalam data fitur konten, meskipun mungkin memiliki penulis atau penerbit yang berbeda untuk edisi yang berbeda. Tindakan ini mencegah representasi berlebihan buku yang sama, mengurangi potensi bias dalam perhitungan kemiripan konten, meningkatkan efisiensi pemrosesan data, dan pada akhirnya menghasilkan rekomendasi yang lebih beragam dan relevan bagi pengguna.
- **TF-IDF Vectorizer**
  
  Selanjutnya, tahapan persiapan data untuk content-based filtering adalah ekstraksi fitur menggunakan TF-IDF (Term Frequency-Inverse Document Frequency). Proses ini dimulai dengan menginisialisasi TfidfVectorizer yang bertugas mengubah teks menjadi representasi numerik. Kemudian, vectorizer ini dilatih pada kolom 'book_title' dari DataFrame book_data untuk mempelajari kosakata unik dan menghitung bobot IDF setiap kata, yang mencerminkan pentingnya kata tersebut dalam keseluruhan koleksi judul. Setelah itu, `book_data['book_title']` ditransformasi menjadi tfidf_matrix, sebuah matriks numerik berukuran 25969 baris dan 21623 kolom. Berikut adalah gambar vektor tf-idf dalam bentuk matriks
  
  ![Matriks TF IDF Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/matriks_tf_idf.png)
  
  Tahapan TF-IDF ini harus dilakukan untuk mengubah data teks menjadi format numerik yang dapat diproses oleh algoritma, menangkap pentingnya kata kunci dengan memberikan bobot lebih tinggi pada kata-kata spesifik yang deskriptif, serta menjadi dasar untuk perhitungan kemiripan konten antar buku menggunakan metrik seperti cosine similarity. Dengan demikian, TF-IDF memungkinkan sistem untuk secara objektif mengukur kesamaan konten buku dan merekomendasikan buku berdasarkan relevansi tematik.
- **Mengubah Tipe Data Matriks TF-IDF**
  
  Selanjutnya, matriks TF-IDF yang merepresentasikan bobot fitur teks diubah tipe datanya menjadi float32. Konversi ini penting dilakukan karena bertujuan untuk mengoptimalkan efisiensi memori dan kecepatan komputasi saat memproses data, terutama karena matriks TF-IDF biasanya berukuran besar dan sparse. Dengan menggunakan tipe data float32, penggunaan ruang penyimpanan berkurang dibandingkan float64, sehingga mempercepat operasi matematika dan pemrosesan algoritma tanpa mengorbankan akurasi yang signifikan. Langkah ini penting dalam pipeline content-based filtering untuk menjaga performa sistem tetap responsif dan scalable saat menangani dataset besar.
  

### Persiapan Colaborative Filtering
- **Penghapusan Kolom untuk Menyederhanakan Dataset**
  
  Dalam tahapan persiapan data, dilakukan pemilihan fitur melalui penghapusan kolom untuk menyederhanakan dataset. Proses ini menghapus kolom-kolom **'Year-Of-Publication', 'Publisher', 'Age', 'City', 'State', dan 'Country'** dari DataFrame utama. Tindakan ini diperlukan untuk mengurangi kompleksitas data dan memfokuskan dataset pada fitur-fitur yang dianggap paling relevan untuk tujuan sistem rekomendasi yang akan dibangun. Dengan mengurangi dimensi data, proses komputasi untuk pelatihan model dapat menjadi lebih efisien dan berpotensi meningkatkan kinerja model dengan menghindari noise atau informasi yang tidak perlu sehingga menghasilkan rekomendasi yang lebih tepat sasaran.
  
- **Encoding Data**
  
  Tahapan selanjutnya dalam persiapan data untuk model rekomendasi adalah encoding, khususnya melalui pemetaan ID ke integer. Proses ini dimulai dengan mengekstrak semua nilai unik dari kolom 'User-ID' dan 'ISBN' ke dalam list terpisah. Selanjutnya, dibuat kamus (dictionary) dua arah, satu untuk memetakan setiap 'User-ID' unik ke sebuah integer berurutan (user_to_user_encoded), dan satu lagi untuk memetakan integer tersebut kembali ke 'User-ID' aslinya (user_encoded_to_user). Proses yang sama juga diterapkan pada 'ISBN'. Encoding ID pengguna dan ISBN ini sangat penting karena algoritma machine learning memerlukan representasi numerik yang tidak dapat memproses ID yang bersifat kategorikal secara langsung. Selain itu, encoding ke integer yang berurutan dapat mengurangi kompleksitas data, membantu dalam pengindeksan, dan mempercepat operasi tertentu, terutama ketika ID ini digunakan sebagai indeks untuk lapisan embedding. Berikut contoh kode encode pada User-ID
  ```python
  # Mengubah userID menjadi list tanpa nilai yang sama
  user_ids = df['User-ID'].unique().tolist()
 
  # Melakukan encoding userID
  user_to_user_encoded = {x: i for i, x in enumerate(user_ids)}

  # Melakukan proses encoding angka ke ke userID
  user_encoded_to_user = {i: x for i, x in enumerate(user_ids)}
  ```
- **Memetakan ‘User-ID’ dan ‘ISBN’ ke dataframe yang berkaitan**
  
  Proses ini dilakukan dengan membuat kolom baru, `user` dan `book`, di DataFrame df. Kolom `user` dibuat dengan memetakan setiap `User-ID` asli ke representasi integer yang telah di-encode menggunakan kamus user_to_user_encoded, sementara kolom `book` dihasilkan dengan memetakan `ISBN` asli ke integer yang di-encode menggunakan kamus book_to_book_encoded. Pemetaan ID ini sangat penting karena algoritma machine learning pada dasarnya memerlukan input numerik yang berurutan, dan ID asli seringkali tidak memenuhi kriteria tersebut.
- **Mengecek jumlah user dan jumlah buku dan mengubah nilai rating menjadi float**
  
   Selanjutnya, jumlah pengguna `(num_users)` dihitung dari ID pengguna yang sudah di-encode, dan jumlah buku `(num_books)` dihitung dari ID buku yang sudah di-encode. Langkah ini penting untuk memahami skala data dan menyediakan dimensi yang diperlukan untuk inisialisasi model, seperti ukuran lapisan embedding. Kemudian, dilakukan pemeriksaan dan penentuan nilai minimum `(min_rating)` serta nilai maksimum `(max_rating)` dari kolom `Book-Rating`. Proses ini diawali dengan **mengubah tipe data kolom** `Book-Rating` menjadi **float**, kemudian nilai minimum dan maksimum dari seluruh rating yang ada diambil.
  ```python
  # Nilai minimum rating
  min_rating = min(df['Book-Rating'])

  # Nilai maksimal rating
  max_rating = max(df['Book-Rating'])
  ```
  Penentuan rentang rating ini krusial untuk memahami distribusi data rating dan memastikan bahwa model memiliki informasi yang akurat mengenai batas-batas nilai yang mungkin diprediksi atau dianalisis.
- **Membagi Data untuk Training dan Validasi**
  
  Selanjutnya, kita perlu membagi data menjadi training dan validasi. Namun sebelum itu, kita perlu **mengacak seluruh data** secara menyeluruh. Hal ini penting untuk dilakukan untuk memastikan bahwa saat data nanti dibagi, bagian-bagian data pelatihan dan pengujian memiliki campuran informasi yang merata. Jika tidak diacak, model bisa belajar pola yang salah karena data yang berdekatan mungkin memiliki karakteristik yang mirip. Berikut hasil acak data

  ![Data Acak Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/data_acak.png)
  
  Selanjutnya, informasi yang akan menjadi masukan model dan informasi yang akan diprediksi model dikumpulkan. **ID pengguna dan ID buku** yang sudah diubah menjadi angka diambil untuk **input**. Untuk bagian yang akan **diprediksi**, gunakan nilai **rating buku**. Pada tahap ini, nilai rating ini juga diubah skalanya menjadi antara 0 dan 1 (disebut normalisasi) agar model lebih mudah mempelajarinya dan bekerja dengan stabil.
  
  Terakhir, data dibagi menjadi dua bagian, 80% untuk data pelatihan dan 20% sisanya untuk data validasi. Data training akan digunakan untuk melatih model, sedangkan data testing akan digunakan untuk mengevaluasi kinerja model yang sudah dibangun. Pemisahan data ini penting untuk menghindari overfitting dan memastikan model dapat diuji pada data yang tidak digunakan selama proses pelatihan. Kita harus membagi data agar proses transformasi hanya dilakukan pada data latih saja. Data uji harus berperan sebagai data baru yang tidak terpengaruh oleh proses pelatihan, untuk menilai bagaimana model bekerja pada data yang belum pernah dilihat sebelumnya. Berikut adalah hasil split data

  ![Data Split Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/data_split.png)

## Modeling
Pada tahap modeling, kita akan menggunakan 2 pendekatan, yaitu **Content-Based Filtering** dan **Collaborative Filtering** untuk membangun sistem rekomendasi buku. 

### 1. Content-Based Filtering
Pendekatan ini akan memberikan rekomendasi buku berdasarkan kesamaan konten antara buku yang telah dibaca oleh pengguna dan buku lainnya dalam dataset. Rekomendasi dihitung menggunakan **Cosine Similarity**, yang mengukur seberapa mirip dua buku berdasarkan fitur kontennya, seperti judul, penulis, dan penerbit.

#### Proses Content-Based Filtering

- **Perhitungan Cosine Similarity**

   * Dengan menggunakan **Cosine Similarity**, kita menghitung tingkat kemiripan antara buku yang satu dengan buku lainnya. Cosine similarity mengukur sejauh mana dua buku memiliki kemiripan berdasarkan fitur teks seperti judul dan penulis. Semakin tinggi nilai cosine similarity, semakin mirip dua buku tersebut.
   * Fungsi `cosine_similarity(normalized_df, normalized_df)` digunakan untuk menghitung matriks kemiripan antara buku dalam dataset. Hasilnya adalah matriks berbentuk **DataFrame** yang menunjukkan kemiripan antar semua buku yang ada.
  
- **Menyusun Matrix Cosine Similarity**

   * Matriks cosine similarity yang dihasilkan kemudian disusun menjadi **DataFrame** agar mudah dianalisis dan digunakan untuk mencari buku-buku yang paling mirip dengan buku tertentu. Kolom dan indeks pada DataFrame ini adalah judul buku, dan nilai-nilai di dalamnya menunjukkan tingkat kemiripan antar buku.
     
     ![Cosine Similarity Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/cosine_similarity.png)
     
   * Dengan menggunakan cosine similarity, sistem berhasil mengukur tingkat kemiripan antara satu judul buku dengan judul lainnya. Matriks kesamaan yang dihasilkan berukuran (10000, 10000), yang menunjukkan bahwa terdapat perhitungan kemiripan di antara 10.000 judul buku, baik pada sumbu X maupun Y. Ukuran ini berarti setiap judul dibandingkan dengan semua judul lainnya untuk mengetahui sejauh mana kemiripannya. Namun, karena ukuran data yang besar, tidak semua hasil dapat ditampilkan secara langsung. Oleh karena itu, hanya ditampilkan sebagian data, yaitu 10 judul buku secara vertikal dan 5 judul buku secara horizontal. Hasil kemiripan antar judul ini nantinya digunakan untuk merekomendasikan buku-buku lain yang serupa dengan buku yang pernah dibaca atau dibeli oleh pengguna.

- **Fungsi Rekomendasi Buku**

   * Fungsi book_recommendation dibuat untuk menghasilkan rekomendasi buku berbasis konten, dengan menampilkan daftar judul buku beserta nama penulis yang memiliki kemiripan dengan buku yang sebelumnya pernah dibaca atau dibeli oleh pengguna. Sesuai dengan konsep sistem rekomendasi, output dari fungsi ini berupa **Top-N rekomendasi**, yang jumlahnya dapat diatur melalui parameter k.
   * Dalam model ini, kita memilih **5 buku teratas** dengan nilai similarity terbesar, yang dianggap paling mirip dengan buku yang dicari.
   * Dalam implementasinya, fungsi ini memanfaatkan `argpartition()` untuk mengekstrak sejumlah nilai kemiripan tertinggi dari matriks similarity. Nilai-nilai tersebut kemudian diurutkan berdasarkan bobot kemiripan dari yang paling tinggi ke rendah dan disimpan dalam variabel `closest`. Untuk menghindari duplikasi dalam hasil, judul buku yang dijadikan acuan (input) akan dihapus dari daftar rekomendasi agar tidak muncul kembali dalam hasil rekomendasi yang diberikan.

#### Output Rekomendasi

Ketika pengguna memilih **buku tertentu**, sistem akan mencari buku-buku dengan **kemiripan tertinggi** terhadap buku tersebut berdasarkan judul, penulis, dan penerbit. Rekomendasi yang dihasilkan akan mencakup 5 buku yang paling mirip dengan buku yang dipilih.

Misalnya, jika pengguna memilih buku **"Harry Potter und der Stein der Weisen"**, maka sistem akan memberikan rekomendasi seperti berikut:

![Rekomendasi Content Based Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/rekomendasi_content_based.png)

Rekomendasi ini didasarkan pada kesamaan penulis atau elemen lain yang relevan dalam buku-buku tersebut. Berdasarkan output diatas, sistem berhasil merekomendasikan 5 judul buku teratas dengan kategori nama penulis (book_author) yaitu 'J.K. Rowling' dan memiliki judul yang mirip (masih dalam satu rangkaian series Harry Potter)

#### Kelebihan dan Kekurangan Content-Based Filtering

**Kelebihan:**

1. **Personalisasi yang kuat**: Rekomendasi didasarkan pada preferensi pengguna sebelumnya. Jika pengguna menyukai buku dengan genre tertentu atau penulis tertentu, sistem akan terus merekomendasikan buku dalam kategori yang sama.
2. **Tidak membutuhkan data pengguna lain**: Berbeda dengan **Collaborative Filtering**, Content-Based Filtering tidak bergantung pada data interaksi pengguna lain. Ini membuat sistem ini lebih cocok untuk sistem yang baru diluncurkan atau untuk item-item baru yang belum banyak diinteraksikan oleh pengguna.
3. **Rekomendasi dapat dipahami dan lebih transparan**: Pengguna dapat memahami alasan mengapa sebuah buku direkomendasikan, karena rekomendasi didasarkan pada kesamaan fitur yang jelas seperti judul dan penulis.

**Kekurangan:**

1. **Sangat terbatas pada konten yang ada**: Content-Based Filtering hanya dapat merekomendasikan buku-buku yang memiliki kemiripan dengan buku yang sudah ada. Ini berarti, jika pengguna hanya tertarik pada satu genre atau penulis tertentu, rekomendasi bisa menjadi monoton dan kurang bervariasi.
2. **Kesulitan dalam menangani data teks yang kompleks**: Jika deskripsi atau konten buku sangat kompleks dan beragam, TF-IDF dan metode lain mungkin tidak menangkap makna atau semantik yang lebih dalam, yang bisa mengurangi kualitas rekomendasi.
3. **Tidak memanfaatkan data interaksi pengguna lain**: Sistem ini tidak bisa mengungkapkan pola atau rekomendasi yang lebih luas berdasarkan preferensi kolektif dari pengguna lain, yang bisa mengarah pada hasil yang lebih generalis dan lebih sedikit inovatif dalam hal penemuan buku baru.

### 2. Collaborative Filtering
Pada tahap **Collaborative Filtering**, kita membangun sistem rekomendasi dengan memanfaatkan **interaksi pengguna** dengan item (dalam hal ini buku). **Collaborative Filtering** bekerja dengan memprediksi preferensi pengguna terhadap buku yang belum mereka baca, berdasarkan pola interaksi pengguna lain yang memiliki kesamaan preferensi.

#### Proses Collaborative Filtering

- **Model Embedding untuk Pengguna dan Buku**

  * Model menggunakan teknik **embedding** untuk merepresentasikan **pengguna** dan **buku** dalam bentuk vektor berdimensi rendah. Embedding ini berfungsi sebagai representasi numerik yang dapat menangkap pola preferensi pengguna dan karakteristik buku yang kompleks secara efisien. Setiap pengguna dan buku memiliki vektor embedding yang dipelajari selama proses pelatihan. 
  * Selain embedding, model juga menyertakan **bias** untuk masing-masing pengguna dan buku guna mengakomodasi preferensi individual.
  * Untuk mengurangi risiko overfitting, dropout dengan rate 0.2 diterapkan pada embedding.

- **Perhitungan Prediksi Rating**
  
  * Prediksi rating dihitung dengan melakukan **dot product** antara embedding pengguna dan buku.
  * Hasil dot product ini ditambahkan dengan bias pengguna dan bias buku.
  * Nilai akhir prediksi kemudian diolah melalui fungsi aktivasi **sigmoid** untuk menghasilkan skor dalam rentang 0 hingga 1.

- **Pelatihan Model**
  
  * Model dilatih menggunakan data interaksi yang berisi pasangan **User-ID** dan **ISBN buku**, serta rating yang diberikan pengguna.
  * Penggunaan regularisasi L2 dan **dropout** bertujuan untuk mencegah overfitting dan meningkatkan kemampuan generalisasi model.
  * Model dioptimasi dengan fungsi loss **binary crossentropy** dan optimizer **Adam** dengan learning rate 1e-4.
  * Pelatihan dilakukan selama 50 epoch dengan batch size 64 dan menggunakan data validasi untuk memonitor performa.
    ```python
    model.compile(
    loss = tf.keras.losses.BinaryCrossentropy(),
    optimizer=keras.optimizers.Adam(learning_rate=1e-4),
    metrics=[tf.keras.metrics.RootMeanSquaredError()]
    )
    ```

- **Fungsi Rekomendasi**
  
  * Setelah model dilatih, proses rekomendasi dimulai dengan memilih satu pengguna secara acak dari dataset. Dari pengguna ini, diidentifikasi buku-buku yang sudah diberi rating dan buku yang belum pernah dinilai.
  * Buku-buku yang belum dinilai di-encode sesuai dengan format embedding, kemudian dibuat array input gabungan antara user yang sudah di-encode dan buku-buku yang belum dinilai.
  * Model kemudian memprediksi rating untuk setiap buku yang belum pernah dinilai tersebut. Dari hasil prediksi ini, diambil 10 buku dengan prediksi rating tertinggi sebagai rekomendasi. Selain itu, untuk memberikan konteks preferensi pengguna, juga ditampilkan 5 buku dengan rating tertinggi yang sudah pernah dinilai oleh pengguna. Semua rekomendasi buku dan buku yang sudah dinilai ini ditampilkan lengkap dengan judul dan pengarangnya, sehingga memberikan gambaran rekomendasi yang relevan dan personal untuk pengguna tersebut.

#### Output Rekomendasi

Setelah pelatihan, model dapat memberikan **Top-N rekomendasi buku** berdasarkan prediksi rating. Misalnya, jika pengguna menyukai buku **"Harry Potter"**, sistem akan merekomendasikan buku serupa berdasarkan pola preferensi pengguna lain yang juga menyukai **"Harry Potter"** dan buku-buku sejenis.

Sebagai contoh hasil rekomendasi buku untuk pengguna dengan ID 146230, tampak bahwa model berhasil memahami preferensi pengguna yang cenderung menyukai buku-buku dengan tema keluarga, pendidikan, dan nilai-nilai kehidupan sehari-hari, seperti terlihat dari buku-buku yang diberi rating tinggi seperti Winnie the Pooh and His Friends, Emphasis Art, dan Beautiful Junk. Berdasarkan pola tersebut, sistem merekomendasikan buku-buku seperti The Power of Myth, The Re-Enchantment of Everyday Life, hingga Basic for Home Computers, yang menunjukkan kecenderungan pada materi reflektif, edukatif, dan bermakna. Model mampu menyarankan pilihan yang tidak semata-mata populer, melainkan selaras dengan jenis bacaan yang menstimulasi pemikiran dan memberikan nilai praktis atau filosofis. Dengan memanfaatkan pendekatan collaborative filtering, rekomendasi ini mencerminkan keberhasilan sistem dalam menangkap pola kesamaan antar pengguna dan memberikan saran bacaan yang lebih personal, bervariasi, serta tetap relevan dengan preferensi pengguna.

![Rekomendasi Colaborative Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/rekomendasi_colaborative.png)

#### Kelebihan dan Kekurangan Collaborative Filtering

**Kelebihan**:

1. **Personalisasi Tinggi**: Collaborative Filtering menghasilkan rekomendasi yang sangat personal, karena mempelajari pola interaksi pengguna dengan buku lain, dan memberikan rekomendasi berdasarkan preferensi pengguna serupa.
2. **Tidak Memerlukan Fitur Konten**: Berbeda dengan **Content-Based Filtering**, sistem ini tidak memerlukan informasi eksplisit tentang konten buku (seperti genre atau penulis), hanya membutuhkan data rating atau interaksi pengguna.

**Kekurangan**:

1. **Cold Start Problem**: Jika pengguna atau buku baru tidak memiliki banyak interaksi, model ini kesulitan memberikan rekomendasi yang akurat.
2. **Sparsity**: Jika matriks interaksi sangat jarang (misalnya, hanya sebagian kecil pengguna yang memberi rating pada buku tertentu), ini dapat mempengaruhi akurasi rekomendasi.

## Evaluasi
### 1. **Evaluasi Model Content-Based Filtering**

Dalam model Content-Based Filtering, digunakan tiga metrik evaluasi utama untuk mengukur performa sistem rekomendasi buku berbasis kemiripan konten, yaitu **Precision**, **Recall**, dan **F1-score**. Metrik-metrik ini dipilih karena sesuai untuk mengukur kualitas model dalam tugas klasifikasi biner, yakni memprediksi apakah sebuah pasangan buku memiliki kemiripan tinggi (positif) atau tidak (negatif).

#### **Formula Precision, Recall, dan F1-Score**
**Precision** mengukur proporsi prediksi positif yang benar-benar relevan.

  $$
  \text{Precision} = \frac{\text{True Positives}}{\text{True Positives} + \text{False Positives}}
  $$

   Dalam konteks ini, precision adalah rasio antara jumlah item relevan yang berhasil direkomendasikan dengan jumlah total item yang direkomendasikan. Semakin tinggi precision, semakin sedikit item tidak relevan yang direkomendasikan oleh model.

**Recall** mengukur proporsi data positif yang berhasil ditemukan oleh model

  $$
  \text{Recall} = \frac{\text{True Positives}}{\text{True Positives} + \text{False Negatives}}
  $$

  Recall adalah rasio antara jumlah item relevan yang berhasil direkomendasikan dengan total item relevan yang seharusnya direkomendasikan. Semakin tinggi recall, semakin banyak item relevan yang berhasil ditemukan oleh sistem.

**F1-score** merupakan harmonisasi rata-rata dari precision dan recall, memberikan ukuran keseimbangan antara keduanya:

  $$
  \text{F1-Score} = 2 \times \frac{\text{Precision} \times \text{Recall}}{\text{Precision} + \text{Recall}}
  $$

  F1-Score adalah rata-rata harmonik dari precision dan recall. F1 memberikan satu nilai tunggal yang mewakili keseimbangan antara keduanya, terutama berguna jika terjadi ketidakseimbangan antara jumlah positif dan negatif. F1-score penting untuk memastikan model tidak hanya akurat tapi juga tidak melewatkan rekomendasi penting..

Sebelum menghitung ketiga metrik ini, perlu disiapkan data `ground_truth` yang menjadi acuan evaluasi. Dalam proyek ini, data `ground_truth` dibentuk berdasarkan nilai kemiripan antar buku yang dihitung menggunakan teknik cosine similarity. Setiap baris dan kolom mewakili judul buku, dan nilai dalam sel menunjukkan apakah dua buku tersebut dianggap mirip atau tidak. Nilai 1 menunjukkan bahwa dua buku dianggap mirip (similar), sementara nilai 0 berarti tidak mirip (not similar).

Agar bisa memutuskan apakah dua buku dianggap mirip, digunakan ambang batas (threshold) dengan nilai 0.5. Nilai threshold ini ditentukan berdasarkan kebutuhan dan karakteristik data setelah mengamati hasil rekomendasi sebelumnya. Proses pembuatan ground truth dilakukan dengan fungsi `np.where()` dari library NumPy, yang menghasilkan matriks berisi nilai 1 jika similarity ≥ threshold, dan 0 jika sebaliknya. Matriks ini kemudian diubah ke dalam bentuk DataFrame, dengan judul buku digunakan sebagai indeks pada baris dan kolom.

Setelah ground truth terbentuk, langkah selanjutnya adalah mengevaluasi performa model menggunakan metrik precision, recall, dan f1-score. Fungsi precision_recall_fscore_support dari pustaka Scikit-learn digunakan untuk menghitung ketiga metrik tersebut. Evaluasi dilakukan pada keseluruhan data yang berjumlah 10.000 entri, yang telah dikonversi ke bentuk array 1 dimensi agar dapat dibandingkan secara langsung.

Baik matriks similarity maupun ground truth kemudian diubah menjadi array 1 dimensi (flattened) agar mudah dibandingkan. Nilai prediksi dikonversi menjadi biner (0 atau 1) berdasarkan nilai threshold, lalu disimpan dalam array bernama predictions.

Terakhir, fungsi `precision_recall_fscore_support` digunakan untuk menghitung tiga metrik evaluasi tersebut. Parameter `average='binary'` digunakan karena klasifikasi yang dilakukan bersifat biner, dan `zero_division=1` digunakan untuk menghindari error pembagian dengan nol jika salah satu kelas tidak muncul dalam prediksi.

Adapun hasil evaluasi yang diperoleh menunjukkan performa model sebagai berikut: 

![Evaluasi Content Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/evaluasi_content.png)

#### **Hasil Evaluasi**
Pada hasil evaluasi, ketiga metrik menunjukkan nilai sempurna yaitu **1.00**. Ini berarti model berhasil memberikan semua rekomendasi buku yang benar-benar relevan (precision = 1.00), sekaligus tidak melewatkan buku yang relevan sama sekali (recall = 1.00). Nilai F1-score yang sempurna menunjukkan keseimbangan ideal antara precision dan recall.

Nilai evaluasi ini mengindikasikan bahwa **sistem rekomendasi bekerja sangat baik** pada subset data yang diuji, menghasilkan rekomendasi yang sangat akurat dan komprehensif.

### 2. **Evaluasi Model Collaborative Filtering **

Metrik yang digunakan dalam proyek ini untuk mengevaluasi performa model rekomendasi menggunakan Collaborative Filtering adalah **Root Mean Squared Error (RMSE)**. RMSE adalah metrik yang umum digunakan untuk mengukur kesalahan dalam prediksi yang dihasilkan oleh model, dan dalam konteks sistem rekomendasi, ini mengukur seberapa jauh prediksi rating yang diberikan oleh model dengan rating aktual yang diberikan oleh pengguna.

#### **Formula RMSE**

RMSE dihitung dengan rumus sebagai berikut:

$$
RMSE = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2}
$$

Di mana:

* $n$ adalah jumlah total prediksi yang dihitung,
* $y_i$ adalah nilai aktual atau nilai rating yang diberikan pengguna,
* $\hat{y}_i$ adalah nilai prediksi yang dihasilkan oleh model.

Untuk menghitung nilai RMSE, pertama-tama, selisih antara nilai rating sebenarnya dan nilai rating yang diprediksi dihitung untuk setiap rating. Selanjutnya, selisih tersebut kemudian dikuadratkan. Pengkuadratan ini berfungsi untuk menghilangkan nilai negatif dan memberikan bobot lebih pada kesalahan yang lebih besar. Setelah itu, hasil kuadrat dari semua selisih dijumlahkan dan dirata-ratakan, yang menghasilkan Mean Squared Error (MSE). Terakhir, akar kuadrat dari MSE diambil, bertujuan untuk mengembalikan unit error ke skala asli dari nilai rating agar lebih mudah dipahami. RMSE memberikan ukuran kesalahan yang lebih besar ketika perbedaan antara nilai yang diprediksi dan nilai aktual lebih besar, sehingga **semakin rendah nilai RMSE, semakin baik kinerja model**.

#### **Hasil Evaluasi RMSE**

![Evaluasi RMSE Image](https://raw.githubusercontent.com/ValensiaElsa/Sistem-Rekomendasi-Buku/main/images/evaluasi_rmse.png)

Gambar grafik RMSE selama epoch menunjukkan performa model rekomendasi buku dalam proses pelatihan dan pengujian. Terlihat bahwa nilai RMSE pada data training menurun secara konsisten dari sekitar 0.31 ke sekitar 0.19, yang menandakan **model semakin mampu mempelajari pola interaksi pengguna dan buku dengan baik**. Namun, pada data testing, RMSE relatif stabil di kisaran 0.31 tanpa penurunan signifikan, yang mengindikasikan model mengalami **sedikit overfitting**—mampu menyesuaikan dengan data pelatihan namun kurang optimal dalam generalisasi ke data baru. Meski demikian, **perbedaan nilai RMSE yang tidak terlalu besar** tetap **menunjukkan bahwa model memiliki kemampuan prediksi yang cukup baik**. Untuk meningkatkan generalisasi, langkah seperti regularisasi lebih kuat, penyesuaian dropout, atau peningkatan jumlah data pelatihan bisa dipertimbangkan. Secara keseluruhan, model sudah menunjukkan performa yang memuaskan dengan potensi perbaikan di masa depan.

## Referensi

\[1] M. R. Az Zayyad, "Sistem Rekomendasi Buku Menggunakan Metode Content-Based Filtering," Universitas Islam Indonesia, Yogyakarta, 2021. \[Online]. Available: [https://dspace.uii.ac.id/bitstream/handle/123456789/35942/17523144%20Muhammad%20Rizqi%20Az%20Zayyad.pdf?sequence=1](https://dspace.uii.ac.id/bitstream/handle/123456789/35942/17523144%20Muhammad%20Rizqi%20Az%20Zayyad.pdf?sequence=1).

\[2] L. Dzumiroh, "Penerapan Metode Collaborative Filtering Menggunakan Rating Implisit pada Sistem Perekomendasi Pemilihan Film di Rental VCD," *Jurnal ITSMART*, vol. 1, no. 2, pp. 54-56, 2012. \[Online]. Available: [https://jurnal.uns.ac.id/itsmart/article/viewFile/590/542](https://jurnal.uns.ac.id/itsmart/article/viewFile/590/542).
