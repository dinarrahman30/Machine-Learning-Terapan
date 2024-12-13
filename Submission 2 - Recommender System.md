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
    - 

## Data Understanding


Dalam dataset terdapat 4 buah file bertipe csv, yaitu
- tourism_with_id.csv: mengandung informasi tempak wisata di 5 kota besar di Indonesia (Yogyakarta, Bandung, Jakarta, Semarang, dan Surabaya).
- user.csv: mengandung informasi pengguna untuk membuat rekomendasi fitur berdasar pengguna.
- tourism_rating.csv: mengandung informasi pengguna, tempat wisata, dan rating untuk membuat sistem rekomendasi berdasar rating.
- package_tourism.csv: berisi rekomendasi tempat terdekat berdasarkan waktu, biaya, dan peringkat.


## Data Preparation


**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling


**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menyajikan dua solusi rekomendasi dengan algoritma yang berbeda.
- Menjelaskan kelebihan dan kekurangan dari solusi/pendekatan yang dipilih.

## Evaluation


_Referensi:_
