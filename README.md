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

## Referensi

\[1] M. R. Az Zayyad, "Sistem Rekomendasi Buku Menggunakan Metode Content-Based Filtering," Universitas Islam Indonesia, Yogyakarta, 2021. \[Online]. Available: [https://dspace.uii.ac.id/bitstream/handle/123456789/35942/17523144%20Muhammad%20Rizqi%20Az%20Zayyad.pdf?sequence=1](https://dspace.uii.ac.id/bitstream/handle/123456789/35942/17523144%20Muhammad%20Rizqi%20Az%20Zayyad.pdf?sequence=1).

\[2] L. Dzumiroh, "Penerapan Metode Collaborative Filtering Menggunakan Rating Implisit pada Sistem Perekomendasi Pemilihan Film di Rental VCD," *Jurnal ITSMART*, vol. 1, no. 2, pp. 54-56, 2012. \[Online]. Available: [https://jurnal.uns.ac.id/itsmart/article/viewFile/590/542](https://jurnal.uns.ac.id/itsmart/article/viewFile/590/542).
