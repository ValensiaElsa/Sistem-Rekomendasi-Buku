## Project Overview

Dalam era digital saat ini, pilihan buku yang tersedia semakin beragam, tidak hanya terbatas pada buku fisik, tetapi juga melibatkan **ebook** yang semakin populer di berbagai platform digital. Meskipun banyaknya pilihan buku memberikan kemudahan, hal ini juga memunculkan tantangan bagi pengguna dalam menemukan buku yang sesuai dengan minat atau preferensi mereka. Oleh karena itu, dibutuhkan sistem rekomendasi yang dapat membantu pengguna memilih buku yang relevan, baik dalam bentuk fisik maupun digital. Sistem rekomendasi yang baik harus mampu memberikan saran yang akurat dan personal untuk setiap individu berdasarkan preferensi mereka.

Salah satu pendekatan utama yang digunakan dalam sistem rekomendasi adalah **content-based filtering** dan **collaborative filtering**. **Content-based filtering** menggunakan informasi yang terkandung dalam buku, seperti genre, penulis, dan deskripsi, untuk memberikan rekomendasi berdasarkan kesamaan atribut antara buku yang telah dibaca oleh pengguna dan buku lainnya. Penelitian oleh Az Zayyad (2021) menunjukkan bahwa penerapan metode ini, menggunakan **cosine similarity** dan **TF-IDF**, dapat memberikan rekomendasi buku yang relevan berdasarkan kemiripan isi buku yang disukai oleh pengguna \[1]. Di sisi lain, **collaborative filtering** mengandalkan data interaksi pengguna dengan buku, seperti rating atau pembelian, untuk memberikan rekomendasi berdasarkan kesamaan preferensi antara pengguna yang satu dengan lainnya. Pendekatan ini lebih mengutamakan pola interaksi antar pengguna yang memiliki preferensi serupa \[2].

Penelitian telah menunjukkan bahwa kedua pendekatan ini memiliki keunggulan masing-masing dalam memberikan rekomendasi yang relevan. **Content-based filtering** efektif ketika informasi terkait buku tersedia secara lengkap, seperti deskripsi dan atribut lainnya. Sementara itu, **collaborative filtering** lebih efektif dalam memberikan rekomendasi yang relevan dengan memanfaatkan interaksi antar pengguna yang memiliki preferensi serupa, meskipun informasi konten buku tidak lengkap. Oleh karena itu, sistem rekomendasi yang menggabungkan kedua pendekatan ini diharapkan dapat memberikan rekomendasi yang lebih akurat dan meningkatkan pengalaman pengguna dalam menemukan buku yang sesuai dengan minat mereka.

## Business Understanding
### Problem Statements
Berdasarkan uraian yang telah dipaparkan pada latar belakang diatas, maka dapat diambil sebuah rumusan masalah yang dirumuskan sebagai berikut:
- Berdasarkan data mengenai pengguna, bagaimana membuat sistem rekomendasi buku yang dipersonalisasi menggunakan teknik content-based filtering?
- Bagaimana cara memberikan rekomendasi buku yang relevan kepada pengguna baru (cold start problem) berdasarkan data rating dan interaksi pengguna lain yang serupa?

### Goals
Berdasarkan rumusan masalah yang telah dipaparkan di atas, maka proyek penelitian ini memiliki tujuan, yaitu:
- Menghasilkan rekomendasi buku yang dipersonalisasi untuk pengguna menggunakan teknik content-based filtering, dengan mempertimbangkan atribut seperti penulis dan penerbit buku yang telah dibaca.
- Menghasilkan rekomendasi buku yang sesuai dengan preferensi pengguna baru, yang belum pernah dibaca sebelumnya, dengan menggunakan collaborative filtering, berdasarkan data rating dan interaksi pengguna lain yang memiliki pola serupa.

### Solution Statements
- Menerapkan Content-Based Filtering: Menggunakan data tentang buku yang telah dibaca oleh pengguna, seperti genre, penulis, dan deskripsi, untuk memberikan rekomendasi berdasarkan kesamaan atribut antara buku yang telah disukai atau dibaca oleh pengguna dan buku lainnya, menggunakan teknik seperti cosine similarity atau TF-IDF.
- Menerapkan Collaborative Filtering: Menggunakan data rating dan interaksi pengguna lain untuk merekomendasikan buku yang mungkin disukai pengguna berdasarkan preferensi serupa dari pengguna lain, serta mengatasi cold start problem dengan memanfaatkan data pengguna yang serupa meskipun pengguna baru belum memiliki banyak interaksi dengan sistem.

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

1. **Users**: Menyediakan informasi demografis pengguna, termasuk ID pengguna, lokasi, dan usia (beberapa data kosong).
2. **Books**: Menyediakan informasi tentang buku, termasuk ISBN, judul buku, penulis, penerbit, serta URL gambar sampul buku.
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
- **Image-URL-S, Image-URL-M, Image-URL-L**: URL gambar sampul buku dalam tiga ukuran berbeda (kecil, medium, besar).

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
*gambar hasil books.info*
Berdasarkan hasil pemanggilan fungsi books.info(), dataset Books.csv terdiri dari 271,360 entri dengan 8 kolom. Semua kolom memiliki nilai yang non-null, kecuali pada kolom Book-Author dan Publisher, yang memiliki beberapa nilai kosong. Kolom-kolom ini menyimpan informasi penting mengenai buku, seperti ISBN, Book-Title, Book-Author, Year-Of-Publication, dan Publisher, yang akan digunakan dalam proses rekomendasi.

Kolom Year-Of-Publication saat ini bertipe data object, padahal seharusnya kolom ini bertipe data int64 untuk merepresentasikan tahun terbit buku. Oleh karena itu, tipe data pada kolom ini perlu diubah menjadi int agar dapat digunakan dengan benar dalam analisis dan model prediksi.

Selain itu, beberapa kolom seperti Image-URL-S, Image-URL-M, dan Image-URL-L berisi URL gambar sampul buku dalam tiga ukuran berbeda (kecil, medium, dan besar). Kolom-kolom ini tidak relevan dalam konteks sistem rekomendasi berbasis content-based filtering dan collaborative filtering, sehingga sebaiknya dihapus agar tidak menambah kompleksitas data.

**Pengecekan Missing Value**
Langkah selanjutnya adalah memeriksa apakah ada data yang hilang (missing values) pada setiap fitur. Untuk pengecekan missing values, kode berikut digunakan:
*kode missing value*
*gambar hasil missing value*

Berdasarkan hasil pemeriksaan terhadap nilai yang hilang dalam dataset **Books.csv**, terdapat beberapa kolom yang memiliki nilai yang hilang (missing values). Kolom **Book-Author** memiliki 2 entri yang kosong, yang menunjukkan bahwa beberapa buku tidak memiliki informasi mengenai penulisnya. Hal yang sama berlaku pada kolom **Publisher**, yang juga memiliki 2 entri kosong, menandakan bahwa ada beberapa buku yang tidak tercatat penerbitnya. Meskipun jumlahnya relatif kecil, data yang hilang ini perlu ditangani, baik dengan imputasi atau penghapusan data, terutama karena kedua kolom tersebut berperan penting dalam proses rekomendasi berbasis konten. Selain itu, penting untuk memeriksa kolom mana saja yang kosong untuk mempermudah proses imputasi, agar kita dapat memilih metode imputasi yang tepat. Berdasarkan hasil pengecekan, missing value Book Author berada pada kolom 118033 dan 187689 dan missing value Publisher berada pada kolom 128890 dan 129037.
*gambar*

Kolom **Image-URL-S**, **Image-URL-M**, dan **Image-URL-L** memiliki sedikit atau tanpa nilai yang hilang. Kolom **Image-URL-S** dan **Image-URL-M** tidak memiliki entri yang kosong, sementara kolom **Image-URL-L** hanya memiliki 3 entri yang kosong. Namun, karena kolom gambar ini tidak relevan untuk sistem rekomendasi berbasis **content-based filtering** dan **collaborative filtering**, kolom-kolom ini akan dihapus dari dataset sehingga tidak perlu dilakukan penanganan.

**Pengecekan Invalid Data**
*gambar*
Dari hasil pemeriksaan pada kolom Year-Of-Publication, ditemukan dua entri yang tidak sesuai dengan format yang diharapkan, di mana kolom ini berisi nama penerbit seperti "DK Publishing Inc" dan "Gallimard", padahal kolom tersebut seharusnya hanya berisi tahun penerbitan buku. Kesalahan input ini menyebabkan data pada kolom lainnya, seperti Book-Title dan Book-Author, menjadi tergeser. Terdapat tiga entri pada kolom Book-Author di mana nama penulis tercampur dengan judul buku dalam satu kolom, yang jelas merupakan kesalahan format data. Untuk memperbaiki hal ini, perlu dilakukan pemisahan antara nama penulis dan judul buku yang tercampur, serta memperbaiki nilai pada kolom Year-Of-Publication agar sesuai dengan format yang benar, sehingga dataset menjadi lebih konsisten dan siap untuk digunakan dalam analisis dan pengembangan sistem rekomendasi.

Selanjutnya, kita memeriksa apakah terdapat karakter non-alfanumerik pada kolom ISBN dalam data rating. Dari hasil pengecekan, menggunakan flag, ditemukan bahwa ada karakter non-alfanumerik yang tidak sesuai dengan format yang diharapkan, sehingga perlu dilakukan perbaikan pada data tersebut. Flag diatur menjadi 1 saat karakter non-alfanumerik ditemukan, yang menandakan bahwa ada masalah dalam data ISBN yang perlu diperbaiki.

**Pengecekan Data Duplikat**
Selanjutnya, kita memeriksa apakah ada data duplikat di dalam dataset. Data duplikat dapat terjadi akibat kesalahan saat pengumpulan atau proses input data. Untuk pengecekan data duplikat, kode berikut digunakan:

```python
# Memeriksa duplikasi data 
jumlah_duplikat = books.duplicated().sum()
print(f"Jumlah baris duplikat: {jumlah_duplikat}") 
```

Namun, pada dataset ini, **tidak ditemukan duplikat**, yang berarti setiap entri dalam dataset adalah unik dan tidak ada baris yang terduplikasi.

### Data Understanding untuk Users.csv
*gambar head()*
Berdasarkan pemeriksaan awal menggunakan fungsi head() pada dataset Users, ditemukan bahwa kolom Location menggabungkan informasi tentang kota, negara bagian, dan negara dalam satu kolom, seperti yang terlihat pada contoh "nyc, new york, usa". Meskipun kolom Location tidak digunakan dalam model rekomendasi berbasis Collaborative Filtering dan Content-Based Filtering, penting untuk melakukan pembersihan data terlebih dahulu. Pemisahan kolom Location menjadi City, State, dan Country dapat menjaga konsistensi data dan mempermudah pengelolaan data di masa depan, terutama jika terdapat perkembangan model yang memerlukan informasi lokasi.

*gambar info()*
Berdasarkan hasil pemeriksaan dengan menggunakan fungsi info() pada dataset Users, terdapat tiga kolom utama: User-ID, Location, dan Age. Kolom User-ID memiliki tipe data int64, yang sudah sesuai untuk mewakili ID pengguna. Kolom Age memiliki tipe data float64, yang juga sudah tepat karena usia bisa berupa angka desimal pada beberapa kasus.

**Pengecekan Missing Value**
*gambar*
Berdasarkan hasil pemeriksaan terhadap nilai yang hilang (missing values) menggunakan fungsi isnull().sum() pada dataset Users, ditemukan bahwa kolom Age memiliki 110,762 entri yang kosong. Meskipun kolom Age tidak digunakan dalam model rekomendasi berbasis Content-Based Filtering dan Collaborative Filtering, penting untuk menangani nilai yang hilang pada kolom ini untuk menjaga konsistensi data. Salah satu cara untuk mengatasi masalah ini adalah dengan mengisi nilai yang hilang menggunakan nilai rata-rata (mean) dari kolom Age, yang dapat dilakukan dengan imputasi.

**Pengecekan Invalid Data**
*gambar*
Berdasarkan hasil pengecekan data pada kolom Age, dapat dilihat bahwa bahwa terdapat nilai NaN (missing values) dalam data usia. Setelah disortir, terdapat berbagai rentang usia yang tercatat dalam dataset. Rentang usia ini bervariasi dari 0 hingga 244. Ada beberapa nilai usia yang lebih tinggi (lebih dari 80), yang bisa jadi merupakan entri yang tidak valid atau mungkin hasil kesalahan input.

Untuk memastikan bahwa data ini valid dan konsisten, data usia akan dianalisis lebih lanjut melalui visualisasi pada tahap Exploratory Data Analysis (EDA). Dengan menggunakan grafik distribusi atau histogram, kita dapat mengeksplorasi lebih dalam pola distribusi usia, mengidentifikasi nilai yang tidak wajar, dan mengevaluasi apakah ada kebutuhan untuk melakukan penyesuaian atau imputasi pada nilai usia yang tidak valid.

**Pengecekan Data Duplikat**
Selanjutnya, kita memeriksa apakah ada data duplikat di dalam dataset. Berdasarkan hasil pemeriksaan terhadap duplikasi data menggunakan fungsi .duplicated() pada dataset users, ditemukan bahwa tidak ada baris duplikat dalam dataset tersebut.

### Data Understanding untuk Ratings.csv
*gambar info()*
Berdasarkan hasil pemeriksaan dataset ratings menggunakan fungsi info(), dataset ini terdiri dari 1.149.780 entri dengan 3 kolom, yaitu User-ID, ISBN, dan Book-Rating. Semua kolom memiliki jumlah data yang tidak hilang (non-null), artinya tidak ada missing value dalam dataset ratings, yang sangat baik untuk kelancaran proses analisis dan model prediksi.

Tipe data pada kolom User-ID dan Book-Rating sudah sesuai dengan tipe data yang diharapkan, yaitu int64 untuk data numerik, sedangkan kolom ISBN bertipe object. Untuk kolom ISBN, meskipun bertipe object, ini adalah tipe data yang sesuai karena ISBN bersifat alfanumerik dan terdiri dari karakter yang dapat berbeda.

**Pengecekan Missing Value**
*gambar*
Berdasarkan hasil pemeriksaan menggunakan fungsi isnull(),sum() pada dataset ratings, terlihat bahwa tidak ada nilai yang hilang (missing values) pada ketiga kolom, yaitu User-ID, ISBN, dan Book-Rating. Semua kolom memiliki 0 nilai kosong, yang berarti dataset ini sudah lengkap dan tidak memerlukan penanganan missing values. 

**Pengecekan Invalid Data**
Dengan metode yang sama untuk pengecekan ISBN pada dataset books, atribut ISBN pada dataset ratings juga diperiksa. Berdasarkan hasil pemeriksaan, ditemukan bahwa ada karakter non-alfanumerik dalam kolom ISBN pada data ratings. Untuk memastikan integritas data dalam sistem rekomendasi, hal ini perlu segera diperbaiki. ISBN seharusnya hanya berisi angka dan huruf yang valid, tanpa karakter khusus seperti simbol atau spasi. Oleh karena itu, perlu dilakukan pembersihan data dengan memperbaiki entri ISBN yang mengandung karakter non-alfanumerik.

*gambar describe*
Berdasarkan hasil deskripsi statistik dari dataset ratings, terdapat beberapa informasi penting yang perlu diperhatikan terkait dengan kolom Book-Rating. Kolom ini berisi nilai rating dari pengguna terhadap buku, dengan nilai minimum 0 dan maksimum 10. Nilai 0 menunjukkan bahwa rating tersebut bersifat implisit atau tidak ada rating yang diberikan untuk buku tertentu, yang biasanya digunakan untuk menandakan ketidaktertarikan atau tidak ada interaksi dengan buku tersebut.
Oleh karena itu, untuk menjaga kualitas rekomendasi dan menghindari data yang tidak memberikan kontribusi, nilai 0 dalam kolom Book-Rating harus dihapus dari dataset. Hal ini akan memastikan bahwa hanya interaksi yang relevan, yakni yang memiliki rating lebih tinggi dari 0, yang digunakan dalam proses pembuatan model rekomendasi berbasis collaborative filtering.

**Pengecekan Data Duplikat**
Berdasarkan hasil pemeriksaan terhadap data ratings, tidak ditemukan adanya baris duplikat pada dataset. Hal ini menandakan bahwa setiap entri pada data ratings adalah unik, yang penting untuk memastikan bahwa setiap interaksi pengguna dengan buku dihitung secara terpisah dan tidak terjadi redundansi dalam informasi yang diberikan kepada model rekomendasi.

## Exploratory Data Analysis (EDA)
### Univariate Analysis
- **Analisis Distribusi Data Kategorikal**
  *gambar distribusi penulis*
  Berdasarkan analisis distribusi penulis, ditunjukkan bahwa Agatha Christie adalah penulis dengan jumlah buku terbanyak, melebihi 600 judul. Selain itu, terdapat juga beberapa penulis lain dengan lebih dari satu judul buku. Penulis dengan jumlah buku yang lebih banyak cenderung memiliki representasi konten yang lebih besar. Dalam content-based filtering, ini berarti pengguna yang menyukai karya penulis yang sangat produktif seperti Agatha Christie mungkin akan lebih sering direkomendasikan buku lain dari penulis yang sama atau yang memiliki kemiripan konten. Sementara itu, dalam collaborative filtering, popularitas penulis dengan banyak buku dapat tercermin dalam data interaksi pengguna, yang berpotensi menghasilkan rekomendasi yang lebih sering untuk karya-karya mereka.

  *gambar distribusi penerbit*
  Visualisasi jumlah buku berdasarkan penerbit memperlihatkan Harlequin sebagai penerbit dengan jumlah buku terbanyak secara signifikan, diikuti oleh penurunan jumlah buku pada penerbit-penerbit berikutnya. Sama seperti penulis, dalam konteks sistem rekomendasi, dominasi Harlequin dapat berarti bahwa buku-buku dari penerbit ini memiliki representasi konten yang lebih besar untuk analisis content-based filtering. Selain itu, popularitas buku-buku dari penerbit-penerbit teratas ini dapat tercermin dalam data interaksi pengguna untuk collaborative filtering.

- **Analisis Distribusi Data Numerik**
  *gambar distribusi umur*
  Distribusi umur pengguna menunjukkan adanya potensi data yang tidak valid, terutama pada rentang umur mendekati 0 dan di atas 100 tahun. Keberadaan data umur yang invalid dapat mempengaruhi akurasi sistem rekomendasi jika umur digunakan sebagai fitur (meskipun dalam konteks Content-Based Filtering dan Collaborative Filtering tidak digunakan). Oleh karena itu, langkah-langkah penanganan data invalid perlu dilakukan. Mengingat jumlah data invalid yang signifikan, diputuskan untuk menerapkan metode imputasi dalam penanganan data ini dengan menggunakan nilai rata-rata (mean).
  
  *gambar distribusi rating*
  Visualisasi distribusi rating buku memperjelas dominasi rating 0 dalam dataset, yang mengindikasikan sejumlah besar interaksi implisit atau tidak adanya rating eksplisit. Nilai 0 harus dihapus untuk memfokuskan analisis pada preferensi pengguna yang terungkap melalui rating positif (1 hingga 10). Penghapusan ini akan menghasilkan dataset yang lebih kecil namun berpotensi lebih relevan untuk mengidentifikasi preferensi pengguna yang sebenarnya dalam pengembangan sistem rekomendasi berbasis collaborative filtering.

### Bivariate Analysis
*gambar most rated book*
Visualisasi Buku yang Paling Banyak Diberikan Rating mengidentifikasi 'Wild Animus' sebagai buku yang menerima rating terbanyak secara signifikan, diikuti oleh 'The Lovely Bones: A Novel'. Buku-buku dengan jumlah rating tinggi ini mengindikasikan popularitas yang besar di kalangan pengguna dan dapat menjadi rekomendasi yang kuat dalam sistem. Data ini penting karena buku-buku populer sering kali memiliki banyak rating positif, menjadikannya kandidat yang baik untuk direkomendasikan kepada pengguna lain.

*gambar*
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
  Penanganan missing value merupakan langkah krusial dalam persiapan data untuk sistem rekomendasi. Dalam dataset **books**, teknik imputasi dengan nilai'Other' diterapkan pada kolom 'Book-Author' dan 'Publisher' untuk mengatasi nilai yang hilang pada baris-baris tertentu. Sementara itu, pada dataset **users**, teknik imputasi dengan nilai rata-rata (mean imputation) digunakan untuk mengisi nilai yang hilang (NaN) pada kolom 'Age' dengan nilai rata-rata usia dari seluruh pengguna.
  Tindakan ini diperlukan untuk memastikan bahwa dataset bebas dari nilai yang hilang yang dapat mengganggu proses pemodelan algoritma rekomendasi. Imputasi memungkinkan untuk mempertahankan sebagian besar informasi dalam dataset dibandingkan dengan penghapusan baris, sekaligus menciptakan data yang lebih konsisten dan dapat diandalkan untuk analisis dan pengembangan sistem rekomendasi, baik yang berbasis konten maupun kolaboratif. Dengan mengisi kekosongan dengan nilai yang representatif, diharapkan model rekomendasi yang dihasilkan akan lebih akurat dan robust.

- **Standarisasi Format**
  Dalam tahapan persiapan data, standarisasi format diterapkan pada kolom ISBN yang terdapat baik dalam dataset books maupun ratings. Proses ini melibatkan pengubahan seluruh karakter dalam kolom 'ISBN' menjadi huruf kapital menggunakan fungsi `.str.upper()` pada kedua dataset. Tujuan utama dari standarisasi ini adalah untuk menciptakan format kode ISBN yang konsisten di seluruh data. Dengan format yang seragam, potensi kesalahan atau kesulitan dalam menghubungkan informasi buku antara dataset books dan ratings dapat diminimalkan. Konsistensi ini sangat penting untuk operasi penggabungan data (merging atau joining) berdasarkan kode buku, yang menjadi landasan untuk analisis preferensi pengguna terhadap berbagai buku dan pengembangan model rekomendasi yang akurat.

- **Penanganan Invalid Data**
  Penanganan data tidak valid merupakan serangkaian proses krusial dalam mempersiapkan dataset sebelum digunakan untuk membangun sistem rekomendasi yang efektif. Tujuannya adalah untuk mengidentifikasi dan memperbaiki atau mengatasi data yang tidak akurat, tidak konsisten, atau tidak relevan, sehingga kualitas informasi yang digunakan dalam pelatihan model menjadi lebih baik dan menghasilkan rekomendasi yang lebih handal. Beberapa teknik spesifik diterapkan pada dataset books, users, dan ratings untuk mencapai tujuan ini.
  Pada dataset books, langkah pertama adalah **pembaharuan data yang teridentifikasi atau explicit value replacement**.
  
  *gambar contoh kode*
  
  Teknik ini melibatkan penggantian nilai-nilai spesifik yang diketahui salah atau tidak akurat dengan nilai yang benar. Pada baris-baris tertentu, informasi seperti nama penerbit, tahun publikasi, judul buku, atau nama penulis yang keliru diperbaiki secara manual berdasarkan data understanding yang sudah dilakukan sebelumnya. Tindakan ini penting untuk memastikan bahwa informasi dasar buku dalam dataset akurat dan dapat diandalkan.
  Selanjutnya, **konversi tipe data atau data type conversion** diterapkan pada kolom **'Year-Of-Publication'**. Mengubah tipe data menjadi integer memastikan bahwa tahun publikasi dapat diolah dengan benar dalam analisis numerik, seperti perhitungan usia buku atau pengelompokan berdasarkan periode publikasi, serta menghindari potensi kesalahan interpretasi jika kolom tersebut masih berupa string atau tipe data lainnya. Untuk mengatasi data tahun publikasi yang jelas-jelas tidak valid, seperti nilai 0 atau tahun yang jauh di masa depan (melebihi 2025), digunakan teknik imputasi dengan nilai mode atau **mode imputation**. Kode yang digunakan adalah sebagai berikut:
   ```python
   mode_year = books['Year-Of-Publication'].mode()[0]
   # Terapkan perubahan pada kolom 'Year-Of-Publication'
   books['Year-Of-Publication'] = books['Year-Of-Publication'].apply( lambda x:   mode_year if x == 0 or x > 2025 else x)
  ```
  Untuk memastikan integritas kode International Standard Book Number (ISBN), diterapkan teknik **penghapusan karakter tidak valid atau invalid character removal**. Teknik ini melibatkan identifikasi dan penghilangan karakter-karakter selain huruf (A-Z, a-z) dan angka (0-9) dari setiap nilai dalam kolom 'ISBN' pada dataset books. Proses ini bertujuan untuk membersihkan kode ISBN dari karakter-karakter yang tidak sesuai dengan format standar. Penghapusan karakter tidak valid ini krusial karena beberapa alasan. Pertama, memastikan format ISBN yang benar adalah langkah penting untuk identifikasi buku yang akurat. ISBN adalah pengidentifikasi unik, dan karakter-karakter selain alfanumerik dapat mengganggu proses identifikasi dan pencocokan buku. Kedua, meningkatkan kualitas data dengan menghilangkan noise yang mungkin timbul akibat kesalahan input atau perbedaan format. Data yang bersih akan meminimalkan potensi kesalahan saat menghubungkan informasi buku antar dataset (books dan ratings). Ketiga, memfasilitasi matching data yang akurat berdasarkan kode ISBN. Sistem rekomendasi seringkali memerlukan penggabungan informasi dari berbagai sumber menggunakan ISBN sebagai kunci penghubung. Jika ISBN mengandung karakter yang tidak valid, proses matching bisa menjadi tidak efektif.

  Pada dataset **users**, penanganan data tidak valid berfokus pada kolom 'Age' dan 'Location'. Untuk kolom 'Age', digunakan teknik imputasi dengan nilai rata-rata atau **mean imputation** untuk mengganti nilai-nilai usia yang di luar batas wajar (kurang dari 10 atau lebih dari 80 tahun). Asumsi di balik ini adalah bahwa nilai-nilai ekstrem kemungkinan merupakan kesalahan input, dan menggantinya dengan nilai rata-rata usia pengguna secara keseluruhan akan mempertahankan distribusi usia yang lebih realistis dalam dataset. 
  Sementara itu, pada kolom 'Location', diterapkan teknik **ekstraksi informasi atau information extraction** dan **pemisahan data atau data splitting**. Informasi lokasi yang awalnya mungkin berupa string gabungan (misalnya, "city, state, country") dipecah menjadi tiga kolom terpisah ('City', 'State', 'Country'). Teknik ekstraksi informasi dan pemisahan data pada kolom 'Location' di dataset users diterapkan dengan tujuan untuk mendapatkan informasi geografis yang lebih terstruktur dan spesifik mengenai pengguna. Alasan utama dilakukannya tahapan ini adalah untuk memungkinkan analisis preferensi pengguna berdasarkan lokasi geografis mereka. Informasi lokasi dalam format string gabungan (seperti "city, state, country") sulit untuk dianalisis secara langsung atau digunakan sebagai fitur dalam model rekomendasi. Dengan memecahnya menjadi kolom-kolom terpisah, kita mendapatkan data yang lebih granular dan mudah diolah.  Berikut adalah hasil setelah data Location dipisah menjadi City, State, dan Country.
  *gambar setelah proses*

  Terakhir, pada dataset **ratings**, penanganan data tidak valid difokuskan pada kolom 'ISBN' dan 'Book-Rating'. Sama seperti pada dataset books, **penghapusan karakter tidak valid** diterapkan pada kolom 'ISBN' untuk memastikan konsistensi dan integritas kode buku yang digunakan untuk menghubungkan rating dengan informasi buku. Selain itu, diterapkan teknik **pemfilteran data atau data filtering** dengan menghapus baris-baris di mana nilai pada kolom 'Book-Rating' adalah 0. Proses ini dilakukan dengan memilih baris-baris di mana nilai 'Book-Rating' tidak sama dengan 0. Penghapusan rating 0 diperlukan karena nilai ini sering diartikan sebagai ketidaktertarikan atau tidak adanya rating eksplisit, sehingga dapat mengintroduksi noise dan mengaburkan sinyal preferensi pengguna yang sebenarnya dalam analisis collaborative filtering. Dengan memfokuskan data hanya pada rating positif, diharapkan model rekomendasi dapat mempelajari preferensi pengguna dengan lebih akurat dan menghasilkan rekomendasi yang lebih relevan.

  Secara keseluruhan, serangkaian teknik penanganan data tidak valid ini sangat penting untuk memastikan bahwa data yang digunakan dalam membangun sistem rekomendasi adalah data yang bersih, akurat, konsisten, dan relevan. Data yang berkualitas tinggi akan menghasilkan model rekomendasi yang lebih baik dalam memahami preferensi pengguna dan memberikan rekomendasi yang lebih tepat sasaran.

- **Penghapusan Baris Duplikat**
  Sebagai langkah terakhir dalam pembersihan data, dilakukan pengecekan dan penghapusan baris-baris duplikat. Proses ini melibatkan identifikasi baris-baris yang memiliki nilai identik di seluruh kolom dalam dataset menggunakan fungsi `duplicated().sum()`. Meskipun pada tahap data understanding tidak ditemukan adanya baris duplikat, berbagai operasi pemrosesan data yang telah dilakukan (seperti imputasi, standardisasi, atau pemisahan data) berpotensi menimbulkan duplikasi. Berdasarkan pengecekan terdapat beberapa baris duplikat pada dataset.
  
  *gambar*
  
  Setelah baris duplikat teridentifikasi, baris-baris tersebut dihapus dengan fungsi `drop_duplicates()`. Tahapan ini diperlukan karena keberadaan baris duplikat dapat mengganggu integritas data dengan merepresentasikan entitas yang sama berulang kali, yang dapat menciptakan bias dalam pemodelan sistem rekomendasi dengan memberikan bobot berlebih pada pola yang sebenarnya tidak unik. Selain itu, penghapusan duplikat meningkatkan efisiensi pemrosesan dengan mengurangi ukuran dataset yang tidak perlu dan memastikan keakuratan metrik evaluasi model dengan mencegah perhitungan ganda entitas yang sama. Dengan dataset yang bebas dari baris duplikat, model rekomendasi yang dibangun akan lebih handal dan mampu memberikan rekomendasi yang lebih akurat dan representatif, terutama setelah melalui berbagai transformasi data.

- **Merging Dataset dan Sampling**
  Tahapan persiapan data selanjutnya melibatkan penggabungan dataset (merging) dan pengambilan sampel (sampling). Proses penggabungan dilakukan dengan menggunakan fungsi pd.merge() sebanyak dua kali.
  ```python
  dataset = pd.merge(books, ratings, on='ISBN', how='inner')
  dataset = pd.merge(dataset, users, on='User-ID', how='inner')
  ```
  Pertama, DataFrame books dan ratings digabungkan berdasarkan kolom 'ISBN' dengan metode 'inner', menghasilkan DataFrame dataset yang berisi hanya baris dengan nilai 'ISBN' yang sama di kedua DataFrame. Kemudian, DataFrame dataset ini digabungkan kembali dengan DataFrame users berdasarkan kolom 'User-ID' juga menggunakan metode 'inner'. Penggabungan ini bertujuan untuk mengintegrasikan informasi buku, rating pengguna, dan informasi pengguna ke dalam satu DataFrame yang komprehensif, yang esensial untuk membangun sistem rekomendasi yang efektif. Metode 'inner' memastikan hanya data yang lengkap dari ketiga sumber yang disertakan.
  Setelah penggabungan, dilakukan pengambilan sampel (sampling) dengan menggunakan fungsi `dataset.sample(n=40000, random_state=42)` untuk memilih secara acak 40000 baris dari DataFrame dataset. Pengambilan sampel ini kemungkinan dilakukan untuk mengurangi beban komputasi selama tahap pengembangan dan eksperimen model, terutama dengan dataset yang berpotensi besar. Penggunaan random_state memastikan hasil pengambilan sampel yang konsisten dan dapat direproduksi. Dengan demikian, penggabungan dataset menyediakan data terintegrasi yang diperlukan, sementara pengambilan sampel memungkinkan pengelolaan sumber daya komputasi yang lebih efisien dalam proses pengembangan sistem rekomendasi.
  Berikut adalah dataset setelah dilakukan penggabungan dan sampling:
  *gambar*
 
## Referensi

\[1] M. R. Az Zayyad, "Sistem Rekomendasi Buku Menggunakan Metode Content-Based Filtering," Universitas Islam Indonesia, Yogyakarta, 2021. \[Online]. Available: [https://dspace.uii.ac.id/bitstream/handle/123456789/35942/17523144%20Muhammad%20Rizqi%20Az%20Zayyad.pdf?sequence=1](https://dspace.uii.ac.id/bitstream/handle/123456789/35942/17523144%20Muhammad%20Rizqi%20Az%20Zayyad.pdf?sequence=1).

\[2] L. Dzumiroh, "Penerapan Metode Collaborative Filtering Menggunakan Rating Implisit pada Sistem Perekomendasi Pemilihan Film di Rental VCD," *Jurnal ITSMART*, vol. 1, no. 2, pp. 54-56, 2012. \[Online]. Available: [https://jurnal.uns.ac.id/itsmart/article/viewFile/590/542](https://jurnal.uns.ac.id/itsmart/article/viewFile/590/542).
