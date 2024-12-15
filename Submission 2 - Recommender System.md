# Laporan Proyek Machine Learning - Dinar Wahyu Rahman

Sistem Rekomendasi Destinasi Wisata di Kota Yogyakarta dengan Collaborative Filtering 

## Project Overview
![Foto](https://opinijogja.com/wp-content/uploads/2023/02/Wisata.jpg)

Pariwisata menjadi salah satu bidang andalan perekonomian negara Indonesia. Kota Yogyakarta adalah salah satu destinasi wisata terpopuler di Indonesia, menawarkan berbagai jenis tempat wisata mulai dari wisata budaya, sejarah, alam, hingga kuliner. Dengan banyaknya pilihan, wisatawan sering menghadapi kesulitan dalam menentukan destinasi yang sesuai dengan minat mereka. Selain itu, platform pariwisata sering kali memberikan rekomendasi generik yang kurang relevan dengan preferensi individu.

Untuk mengatasi masalah ini, sistem rekomendasi destinasi wisata berbasis Collaborative Filtering dirancang untuk memberikan rekomendasi yang personal dan sesuai dengan preferensi pengguna, khususnya bagi wisatawan yang berkunjung ke Kota Yogyakarta.

## Business Understanding
Industri pariwisata menghadapi tantangan untuk memahami kebutuhan pelanggan secara mendalam dan menyediakan pengalaman wisata yang dipersonalisasi. Wisatawan memiliki preferensi unik yang sulit dipetakan secara manual. Selain itu, keberagaman destinasi wisata yang ditawarkan sering kali membuat wisatawan bingung untuk memilih destinasi yang sesuai dengan minat mereka.

Sistem rekomendasi berbasis Collaborative Filtering memberikan peluang besar untuk meningkatkan pengalaman pelanggan dengan menyediakan saran destinasi yang relevan. Pendekatan ini tidak hanya membantu wisatawan menemukan destinasi favorit, tetapi juga membantu penyedia layanan pariwisata dalam mendorong engagement pelanggan dan meningkatkan loyalitas.

### Problem Statements

Menjelaskan pernyataan masalah:
- Bagaimana memahami preferensi wisatawan secara otomatis?
- Bagaimana menyediakan rekomendasi destinasi yang relevan untuk setiap wisatawan?
- Bagaimana meningkatkan keterlibatan wisatawan dalam platform?

### Goals

Membangun sebuah Sistem Rekomendasi Destinasi Wisata yang dapat:
- Memberikan rekomendasi destinasi wisata yang relevan dan sesuai dengan preferensi pengguna.
- Menggunakan pendekatan Collaborative Filtering untuk mengidentifikasi kesamaan preferensi antar wisatawan.
- Meningkatkan pengalaman wisatawan dengan memberikan saran yang personal dan mendekati selera mereka.

    ### Solution statements
    - **Item-Based Collaborative Filtering**: Pendekatan ini mencari hubungan antar destinasi wisata berdasarkan pola penilaian pengguna. Sistem ini merekomendasikan destinasi yang serupa dengan destinasi yang sudah pernah dikunjungi oleh pengguna.

        Kelebihan:

        - Lebih stabil dibandingkan User-Based Collaborative Filtering.

        - Tidak terlalu terpengaruh oleh jumlah pengguna baru.

        Kekurangan:

        - Memerlukan data interaksi yang cukup untuk menganalisis hubungan antar destinasi.
    - **Meningkatkan Akurasi Rekomendasi**: Menggunakan algoritma Neural Network untuk membangun Sistem Rekomendasi Destinasi Wisata dengan Collaborative Filtering dapat dilakukan dengan pendekatan berbasis Deep Learning, seperti Neural Collaborative Filtering (NCF). Algoritma ini memanfaatkan jaringan saraf tiruan (Artificial Neural Network) untuk menemukan pola hubungan kompleks antara pengguna dan destinasi wisata.

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

![Gambar 2](https://github.com/user-attachments/assets/33326508-b0ab-4a6a-9937-d7a5797aa25e)

Gambar 2. Rating



## Data Preparation
Data Preparation merupakan tahap untuk mempersiapkan data sebelum masuk ke tahap pembuatan model Machine Learning:
- Label Encoding
    -    
- Train Test Split (dengan pembagian data menjadi data latih 80% dan data uji 20%)

## Modeling
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Kita perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan.

## Evaluation


_Referensi:_
