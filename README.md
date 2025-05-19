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

### Variabel-variabel pada Book Recommendation dataset:
## Data Understanding

| Jenis      | Keterangan                                                                                    |
| ---------- | --------------------------------------------------------------------------------------------- |
| Title      | [Book-Crossing Dataset](https://www.kaggle.com/datasets/cedricdastugue/book-crossing-dataset) |
| Source     | [Kaggle](https://www.kaggle.com)                                                              |
| Maintainer | Cai-Nicolas Ziegler                                                                           |
| License    | Unknown                                                                                       |
| Visibility | Publik                                                                                        |
| Tags       | Books, User Data, Recommender System                                                          |
| Usability  | 8.0                                                                                           |

Dataset yang digunakan dalam proyek ini adalah **Book-Crossing Dataset** yang diperoleh dari Kaggle. Dataset ini berisi data dari **Book-Crossing community** yang mengumpulkan informasi tentang buku-buku yang telah dibaca oleh pengguna dan rating yang diberikan oleh pengguna terhadap buku tersebut. Dataset ini terdiri dari tiga file utama: **Users**, **Books**, dan **Ratings**, yang digunakan untuk membangun sistem rekomendasi buku berbasis **content-based filtering** dan **collaborative filtering**. Dataset ini mencakup 278,858 pengguna (yang teranonimkan tetapi dengan data demografi) dan 1,149,780 rating (baik eksplisit maupun implisit) mengenai 271,379 buku.

### Deskripsi Data

Dataset ini terdiri dari tiga file utama yang berfungsi untuk membangun sistem rekomendasi buku:

1. **Users**: Menyediakan informasi demografis pengguna, termasuk ID pengguna, lokasi, dan usia (beberapa data kosong).
2. **Books**: Menyediakan informasi tentang buku, termasuk ISBN, judul buku, penulis, penerbit, serta URL gambar sampul buku.
3. **Ratings**: Berisi informasi tentang rating yang diberikan oleh pengguna terhadap buku-buku tertentu, baik yang eksplisit (1-10) maupun implisit (0).

### Variabel-variabel pada Book-Crossing Dataset:

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


## Referensi

\[1] M. R. Az Zayyad, "Sistem Rekomendasi Buku Menggunakan Metode Content-Based Filtering," Universitas Islam Indonesia, Yogyakarta, 2021. \[Online]. Available: [https://dspace.uii.ac.id/bitstream/handle/123456789/35942/17523144%20Muhammad%20Rizqi%20Az%20Zayyad.pdf?sequence=1](https://dspace.uii.ac.id/bitstream/handle/123456789/35942/17523144%20Muhammad%20Rizqi%20Az%20Zayyad.pdf?sequence=1).

\[2] L. Dzumiroh, "Penerapan Metode Collaborative Filtering Menggunakan Rating Implisit pada Sistem Perekomendasi Pemilihan Film di Rental VCD," *Jurnal ITSMART*, vol. 1, no. 2, pp. 54-56, 2012. \[Online]. Available: [https://jurnal.uns.ac.id/itsmart/article/viewFile/590/542](https://jurnal.uns.ac.id/itsmart/article/viewFile/590/542).
