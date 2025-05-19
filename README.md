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

## Referensi

\[1] M. R. Az Zayyad, "Sistem Rekomendasi Buku Menggunakan Metode Content-Based Filtering," Universitas Islam Indonesia, Yogyakarta, 2021. \[Online]. Available: [https://dspace.uii.ac.id/bitstream/handle/123456789/35942/17523144%20Muhammad%20Rizqi%20Az%20Zayyad.pdf?sequence=1](https://dspace.uii.ac.id/bitstream/handle/123456789/35942/17523144%20Muhammad%20Rizqi%20Az%20Zayyad.pdf?sequence=1).

\[2] L. Dzumiroh, "Penerapan Metode Collaborative Filtering Menggunakan Rating Implisit pada Sistem Perekomendasi Pemilihan Film di Rental VCD," *Jurnal ITSMART*, vol. 1, no. 2, pp. 54-56, 2012. \[Online]. Available: [https://jurnal.uns.ac.id/itsmart/article/viewFile/590/542](https://jurnal.uns.ac.id/itsmart/article/viewFile/590/542).
