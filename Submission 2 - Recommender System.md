# Laporan Proyek Machine Learning - Dinar Wahyu Rahman

Sistem Rekomendasi Destinasi Wisata di Indonesia dengan Content-Based Filtering 

## Project Overview
![Foto](https://opinijogja.com/wp-content/uploads/2023/02/Wisata.jpg)

Indonesia memiliki ribuan destinasi wisata dengan keindahan alam, budaya, dan kuliner yang menarik. Namun, dengan begitu banyak pilihan, wisatawan sering kali bingung menentukan destinasi yang sesuai dengan preferensi pribadi. Oleh karena itu, dibutuhkan sistem rekomendasi berbasis fitur destinasi yang dapat membantu pengguna menemukan tempat wisata yang relevan berdasarkan karakteristik tempat dan preferensi mereka.

## Business Understanding
Industri pariwisata menghadapi tantangan untuk memahami kebutuhan pelanggan secara mendalam dan menyediakan pengalaman wisata yang dipersonalisasi. Wisatawan memiliki preferensi unik yang sulit dipetakan secara manual. Selain itu, keberagaman destinasi wisata yang ditawarkan sering kali membuat wisatawan bingung untuk memilih destinasi yang sesuai dengan minat mereka.

Sistem rekomendasi berbasis Collaborative Filtering memberikan peluang besar untuk meningkatkan pengalaman pelanggan dengan menyediakan saran destinasi yang relevan. Pendekatan ini tidak hanya membantu wisatawan menemukan destinasi favorit, tetapi juga membantu penyedia layanan pariwisata dalam mendorong engagement pelanggan dan meningkatkan loyalitas.

### Problem Statements

Menjelaskan pernyataan masalah:
- Bagaimana memahami preferensi wisatawan secara otomatis?
- Bagaimana menyediakan rekomendasi destinasi yang relevan untuk setiap wisatawan?
- Bagaimana evaluasi kinerja sistem rekomendasi yang dibangun?
  
### Goals

Membangun sebuah Sistem Rekomendasi Destinasi Wisata yang dapat:
- Memberikan rekomendasi destinasi wisata yang relevan dan sesuai dengan preferensi pengguna.
- Menggunakan pendekatan Content-Based Filtering untuk mengidentifikasi kesamaan preferensi antar wisatawan.
- Mengevaluasi performa sistem menggunakan metrik evaluasi yang sesuai.

    ### Solution statements
    - **Content-Based Filtering**: Pendekatan ini mencari kesamaan antar dokumen dengan menggunakan istilah yang terdapat pada item tersebut. Sistem rekomendasi dengan metode ini, merekomendasikan item yang mirip dengan item sebelumnya yang disukai atau dipilih oleh pengguna. Kemiripan item dihitung lewat fitur-fitur yang ada pada item yang dibandingkan [[1]](https://publikasi.dinus.ac.id/index.php/technoc/article/view/8556).

        Kelebihan:

        - Tidak Bergantung pada Data Pengguna Lain.
        - Rekomendasi Personal dan Relevan.

        Kekurangan:

        - Terbatas pada Preferensi Pengguna.
        - Memerlukan Deskripsi Fitur yang Baik
          
    - **Meningkatkan Akurasi Rekomendasi**
      
## Data Understanding
Kumpulan data yang digunakan dikumpulkan dari situs web [Kaggle]([https://www.airlinequality.com/](https://www.kaggle.com/aprabowo/indonesia-tourism-destination)). Setelah mendapatkan data, data tersebut tinggal dibersihkan dan disiapkan untuk analisis. 
Berikut informasi mengenai dataset: 

Dalam dataset terdapat 4 buah file bertipe csv (Comma-Seperated Values), yaitu
- tourism_with_id.csv: mengandung informasi tempak wisata di 5 kota besar di Indonesia (Yogyakarta, Bandung, Jakarta, Semarang, dan Surabaya).
- user.csv: mengandung informasi pengguna untuk membuat rekomendasi fitur berdasar pengguna.
- tourism_rating.csv: mengandung informasi pengguna, tempat wisata, dan rating untuk membuat sistem rekomendasi berdasar rating.
- package_tourism.csv: berisi rekomendasi tempat terdekat berdasarkan waktu, biaya, dan peringkat.

### Exploratory Data Analytics (EDA)
Exploratory data analysis merupakan proses investigasi awal pada data untuk menganalisis karakteristik, menemukan pola, anomali, dan memeriksa asumsi pada data. Teknik ini biasanya menggunakan bantuan statistik dan representasi grafis atau visualisasi.

![Gambar 1](https://github.com/user-attachments/assets/6bfafe31-cce6-40af-8853-a09f7544f6af)

Gambar 1. Category

Dari Gambar 1 di atas dapat disimpulkan bahwa,
- Grafik ini akan menunjukkan frekuensi atau jumlah destinasi wisata yang terdaftar di setiap kategori. Jika satu kategori memiliki banyak destinasi wisata, itu menunjukkan bahwa kategori tersebut lebih populer atau lebih banyak tempat yang terdaftar dalam kategori tersebut.
- Dari jumlah bar pada grafik, kita dapat melihat kategori mana yang memiliki jumlah destinasi wisata terbanyak, dan mana yang memiliki jumlah sedikit. Misalnya, jika kategori "Alam" memiliki jumlah yang sangat tinggi dibandingkan dengan kategori "Kuliner", maka dapat disimpulkan bahwa lebih banyak destinasi wisata yang berkaitan dengan alam daripada kuliner dalam dataset tersebut.

![Gambar 2](https://github.com/user-attachments/assets/33326508-b0ab-4a6a-9937-d7a5797aa25e)

Gambar 2. Rating

Dari Gambar 2 di atas dapat disimpulkan bahwa,
- Jika histogram menunjukkan distribusi yang terpusat di satu nilai tertentu (misalnya, banyak rating berkumpul di sekitar angka 4 atau 5), itu menunjukkan bahwa sebagian besar tempat wisata mendapatkan rating yang tinggi. Ini bisa menunjukkan kepuasan umum yang tinggi dari para pengunjung.
- Jika distribusi terlihat berdiri tegak dengan beberapa puncak 4.4-4.5, itu bisa menunjukkan adanya variasi dalam kepuasan pengguna. Artinya, ada banyak tempat wisata dengan rating yang berbeda-beda, yang bisa menunjukkan adanya perbedaan kualitas pengalaman wisata antara destinasi yang ada.

## Data Preparation
Data Preparation merupakan tahap untuk mempersiapkan data sebelum masuk ke tahap pembuatan model Machine Learning:
- **Case folding**:
- **Stopword removal**:

## Modeling
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Kita perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan. Beberapa tahapan dalam membuat sistem rekomendasi dengan metode __Content-Based Filtering__.
- **TF-IDF Vectorizer**:
- **Normalized Rating**:
- **Cosine Similarity**:

**Top 5 Rekomendasi Tempat Wisata**


## Evaluation


_Referensi:_
