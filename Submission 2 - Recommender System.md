# Laporan Proyek Machine Learning - Dinar Wahyu Rahman

Sistem Rekomendasi Destinasi Wisata di Indonesia dengan Content-Based Filtering 

## Link Notebook
[Notebook](https://github.com/dinarrahman30/Machine-Learning-Terapan/blob/main/Recommender_System.ipynb)

## Project Overview
![Foto](https://cove-blog-id.sgp1.cdn.digitaloceanspaces.com/cove-blog-id/2021/12/jakarta-barat.webp)

Indonesia memiliki ribuan destinasi wisata dengan keindahan alam, budaya, dan kuliner yang menarik. Namun, dengan begitu banyak pilihan, wisatawan sering kali bingung menentukan destinasi yang sesuai dengan preferensi pribadi. Oleh karena itu, dibutuhkan sistem rekomendasi berbasis fitur destinasi yang dapat membantu pengguna menemukan tempat wisata yang relevan berdasarkan karakteristik tempat dan preferensi mereka.

## Business Understanding
Industri pariwisata menghadapi tantangan untuk memahami kebutuhan pelanggan secara mendalam dan menyediakan pengalaman wisata yang dipersonalisasi. Wisatawan memiliki preferensi unik yang sulit dipetakan secara manual. Selain itu, keberagaman destinasi wisata yang ditawarkan sering kali membuat wisatawan bingung untuk memilih destinasi yang sesuai dengan minat mereka.

Tujuan utama dari Sistem Rekomendasi Destinasi Wisata ini adalah untuk memberikan rekomendasi destinasi wisata yang relevan bagi pengguna berdasarkan preferensi mereka. Dengan menggunakan Content-Based Filtering, sistem dapat menyarankan tempat wisata yang memiliki kesamaan dengan tempat yang sudah dinikmati pengguna, serta mengidentifikasi destinasi berdasarkan kategori yang paling diminati. Rekomendasi ini diharapkan dapat meningkatkan pengalaman pengguna dalam merencanakan perjalanan wisata.

### Problem Statements

Menjelaskan pernyataan masalah:
- Bagaimana memahami preferensi wisatawan secara otomatis?
- Bagaimana menyediakan rekomendasi destinasi yang relevan untuk setiap wisatawan?
  
### Goals

Membangun sebuah Sistem Rekomendasi Destinasi Wisata yang dapat:
- Memberikan rekomendasi destinasi wisata yang relevan dan sesuai dengan preferensi pengguna.
- Menggunakan pendekatan Content-Based Filtering untuk mengidentifikasi kesamaan preferensi antar wisatawan.

    ### Solution statements
    - Tahap persiapan data atau data preparation dilakukan dengan menggunakan beberapa teknik persiapan data, yaitu:
        - Melakukan proses _Case Folding_ dan _Data Cleaning_ pada dataset.
        - Melakukan proses pengecekan data duplikat pada data.
          
    - **Content-Based Filtering**: Pendekatan ini mencari kesamaan antar dokumen dengan menggunakan istilah yang terdapat pada item tersebut. Sistem rekomendasi dengan metode ini, merekomendasikan item yang mirip dengan item sebelumnya yang disukai atau dipilih oleh pengguna. Kemiripan item dihitung lewat fitur-fitur yang ada pada item yang dibandingkan [[1]](https://publikasi.dinus.ac.id/index.php/technoc/article/view/8556).

        Kelebihan:

        - Tidak Bergantung pada Data Pengguna Lain.
        - Rekomendasi Personal dan Relevan.

        Kekurangan:

        - Terbatas pada Preferensi Pengguna.
        - Memerlukan Deskripsi Fitur yang Baik
          
      
## Data Understanding
Kumpulan data yang digunakan dikumpulkan dari situs web [Kaggle](https://www.kaggle.com/aprabowo/indonesia-tourism-destination). Setelah mendapatkan data, data tersebut tinggal dibersihkan dan disiapkan untuk analisis. 
Berikut informasi mengenai dataset: 

Dalam dataset terdapat 4 buah file bertipe csv (Comma-Seperated Values), yaitu
- _tourism_with_id.csv_: mengandung informasi tempak wisata di 5 kota besar di Indonesia (Yogyakarta, Bandung, Jakarta, Semarang, dan Surabaya).
- _user.csv_: mengandung informasi pengguna untuk membuat rekomendasi fitur berdasar pengguna.
- _tourism_rating.csv_: mengandung informasi pengguna, tempat wisata, dan rating untuk membuat sistem rekomendasi berdasar rating.
- _package_tourism.csv_: berisi rekomendasi tempat terdekat berdasarkan waktu, biaya, dan peringkat.

Untuk pemodelan machine learning pada kasus ini, data yang akan digunakan hanya file `tourism_with_id.csv`.

Dari output `.info()` pada file data _tourism_with_id.csv_ dapat disimpulkan bahwa:
- `Place_Id`: ID dari setiap tempat wisata yang digunakan untuk membedakan tempat satu dengan lainnya.
- `Place_Name`: Nama tempat wisata
- `Description`: Deskripsi singkat tentang tempat wisata, mencakup informasi utama yang menarik perhatian wisatawan, seperti daya tarik utama atau sejarah singkat.
- `Category`: Kategori tempat wisata, seperti "Budaya", "Sejarah", "Alam", atau "Kuliner".
- `City`: Kota tempat wisata tersebut berada, misalnya "Yogyakarta".
- `Price`: Harga masuk atau biaya yang diperlukan untuk menikmati tempat wisata tersebut (dapat berupa nominal dalam mata uang tertentu).
- `Rating`: Penilaian rata-rata dari pengunjung, biasanya dalam skala tertentu (misalnya 1-5).
- `Time_Minutes`: Estimasi waktu yang diperlukan untuk menikmati atau mengunjungi tempat wisata tersebut (dalam satuan menit).
- `Coordinate`: Informasi lokasi dalam bentuk koordinat geografis yang mungkin mencakup kombinasi latitude (Lat) dan longitude (Long).
- `Lat`: Latitude, yaitu garis lintang yang menunjukkan lokasi tempat wisata di peta.
- `Long`: Longitude, yaitu garis bujur yang menunjukkan lokasi tempat wisata di peta.
- `Unnamed: 11`: Kolom yang berisi nilai NaN.
- `Unnamed; 12`: Kolom yang berisi angka.

Kesimpulan dari sesi `Data Understanding`, didapat,
- Dataset memiliki 437 sample dengan jumlah kolom sebanyak 13.
- Terdapat fitur `Time_Minutes` dengan missing value sebanyak 232 dan kolom `Unnamed: 11` sebanyak 437.
- Tidak terdapat data yang duplikat.
- Dataset memiliki 3 fitur `int64`, 5 `object`, dan 5 `float64`.

### Exploratory Data Analytics (EDA) - Visualisasi Data
Exploratory data analysis merupakan proses investigasi awal pada data untuk menganalisis karakteristik, menemukan pola, anomali, dan memeriksa asumsi pada data. Teknik ini biasanya menggunakan bantuan statistik dan representasi grafis atau visualisasi.

![Gambar 1](https://github.com/user-attachments/assets/6bfafe31-cce6-40af-8853-a09f7544f6af)

Gambar 1. Category

Dari Gambar 1 di atas dapat disimpulkan bahwa,
- Grafik ini akan menunjukkan frekuensi atau jumlah destinasi wisata yang terdaftar di setiap kategori. Jika satu kategori memiliki banyak destinasi wisata, itu menunjukkan bahwa kategori tersebut lebih populer atau lebih banyak tempat yang terdaftar dalam kategori tersebut.
- Dari jumlah bar pada grafik, dapat melihat kategori mana yang memiliki jumlah destinasi wisata terbanyak, dan mana yang memiliki jumlah sedikit. Misalnya, jika kategori "Alam" memiliki jumlah yang sangat tinggi dibandingkan dengan kategori "Kuliner", maka dapat disimpulkan bahwa lebih banyak destinasi wisata yang berkaitan dengan alam daripada kuliner dalam dataset tersebut.

![Gambar 2](https://github.com/user-attachments/assets/33326508-b0ab-4a6a-9937-d7a5797aa25e)

Gambar 2. Rating

Dari Gambar 2 di atas dapat disimpulkan bahwa,
- Jika histogram menunjukkan distribusi yang terpusat di satu nilai tertentu (misalnya, banyak rating berkumpul di sekitar angka 4 atau 5), itu menunjukkan bahwa sebagian besar tempat wisata mendapatkan rating yang tinggi. Ini bisa menunjukkan kepuasan umum yang tinggi dari para pengunjung.
- Jika distribusi terlihat berdiri tegak dengan beberapa puncak 4.4-4.5, itu bisa menunjukkan adanya variasi dalam kepuasan pengguna. Artinya, ada banyak tempat wisata dengan rating yang berbeda-beda, yang bisa menunjukkan adanya perbedaan kualitas pengalaman wisata antara destinasi yang ada.

## Data Preparation
Data Preparation merupakan tahap untuk mempersiapkan data sebelum masuk ke tahap pembuatan model Machine Learning:
- **Menghapus Kolom yang Tidak Diperlukan**: Untuk persiapan ke modeling, beberapa kolom yang tidak akan digunakan dalam membangun model rekomendasi _content-based filtering_ akan didrop yaitu `Rating`, `Time_Minutes`, `Unnamed: 11`, dan `Unnamed: 12`.
- **Case folding**: Konversi karakter dari huruf besar ke huruf kecil pada kolom `Description`.
- **Data Cleaning**: Menghilangkan huruf Jawa Kuno pada kolom `Description` .
- **TF-IDF Vectorizer**: Untuk mengubah kumpulan teks pada kolom _Tags_ yang berisi kumpulan data pada kolom _Category_, _City_, dan _Price_ menjadi representasi vektor menggunakan metode TF-IDF. TF-IDF Vectorizer adalah metode yang digunakan untuk menghitung bobot setiap kata yang telah diekstrasi. TF-IDF digunakan untuk menghitung kata-kata umum dalam pencarian. [[2](https://www.researchgate.net/publication/368065924_Opinion_Analysis_of_Traveler_Based_on_Tourism_Site_Review_Using_Sentiment_Analysis)].
  
$$W_{dt} = tf_{dt} \times IDF_{t}$$
  
  Di mana:
  - $d =$ dokumen ke-d
  - $t =$ kata ke-t dari kata kunci
  - $W_{dt} =$ bobot dokumen ke-d terhadap kata ke-t
  - $tf_{dt} =$ banyaknya kata yang dicari pada sebuah dokumen
  - $IDF =$ Inversed Document Frequency

Langkah-Langkah dalam tahapan TF-IDF Vectorizer,
1. Menggabungkan Kolom Category, City, dan Price:
   - Kolom Category, City, dan Price digabungkan menjadi satu kolom baru bernama Tags.
   - Nilai Price diubah menjadi tipe string karena akan digabung dengan teks.
2. Membuat Objek TF-IDF Vectorizer:
   - Objek TfidfVectorizer dari sklearn.feature_extraction.text digunakan untuk memproses teks.
   - Secara default, vektorizer ini akan:
     - Tokenisasi teks (memecah teks menjadi kata-kata).
     - Menghitung nilai TF-IDF untuk setiap kata.
3. Fit dan Transform Kolom Tags:
   - fit_transform digunakan untuk mempelajari fitur (kata-kata unik) dari kolom Tags dan mengubahnya menjadi representasi vektor TF-IDF.
   - Hasilnya adalah matriks sparse (dengan banyak nilai nol) yang merepresentasikan nilai TF-IDF untuk setiap kata dalam setiap baris data.
4. Menampilkan Matriks TF-IDF:
   - tfidf_matrix adalah objek matriks sparse, yang menunjukkan nilai TF-IDF untuk setiap kata.
5. Menampilkan Fitur yang Dipelajari:
   - tfidf.get_feature_names_out() memberikan daftar fitur (kata-kata unik) yang digunakan oleh model.
   - Ini menunjukkan semua kata yang terdapat dalam teks setelah proses tokenisasi. 

## Modeling
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Pada tahapan ini perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan. Beberapa tahapan dalam membuat sistem rekomendasi dengan metode _Content-Based Filtering_.
    
**Cosine Similarity**: Melakukan perhitungan derajat kesamaan atau similatiry degree antar nama tempat wisata dengan teknik cosine similarity menggunakan library scikit-learn. Secara umum, fungsi _similarity_ adalah fungsi yang menerima dua buah objek berupa bilangan riil (0 dan 1) dan mengembalikan nilai kemiripan antara kedua objek tersebut berupa bilangan riil. Jika kefua objek memiliki nilai similaritas 1, maka kedua ibjek yang diavaluasi dianggap semakin mirip, begitupun sebaliknya. [[3](https://jurnal.uns.ac.id/itsmart/article/view/35008/27748)]

$$\text{Similarity} = \cos(\theta) = \frac{\mathbf{A} \cdot \mathbf{B}}{\|\mathbf{A}\| \|\mathbf{B}\|} = 
\frac{\displaystyle\sum_{i=1}^{n} \left( wA_i \cdot wB_i \right)}{\sqrt{\displaystyle\sum_{i=1}^{n} \left( wA_i \right)^2} \cdot \sqrt{\displaystyle\sum_{i=1}^{n} \left( wB_i \right)^2}}$$
  
  Di mana:
  - $A \cdot B =$ dot product antara vektor A dan vektor B
  - $\|A\| =$ panjang vektor A
  - $\|B\| =$ panjang vektor B
  - $\|A\| \|B\| =$ cross product antara $\|A\|$ dan $\|B\|$
  - $wA_i =$ bobot term pada query ke-i
  - $wB_i =$ bobot term pada dokumen ke-i
  - $i =$ jumlah term dalam kalimat
  - $n =$ jumlah vektor

Hasil dari rekomendasi diatas setelah dikonversi oleh _TF-IDF Vectorizer_, dan tingkat kesamaan lewat nama tempat yang ditentukan oleh _Cosine Similiraty_. Berikat output pengujian dengan menggunakan pendekatan _Content-Based Filtering_:

**Input**:

get_recommendation: **Jembatan Kota Intan**

Berikut output hasil rekomendasi tempat wisata berdasarkan rekomendasi yang sama (kota dan kategori).

**Output**:

| No | **Top 6 Rekomendasi Tempat Wisata**|
| --- | --------- |
| 1 | Jembatan Kota Intan |
| 2 | Setu Babakan |
| 3 | Istana Negara Republik Indonesia |
| 4 | Galeri Nasional Indonesia |
| 5 | Monumen Selamat Datang |
| 6 | Galeri Indonesia Kaya |

## Evaluation
Dalam tahap evaluasi, metrik yang digunakan adalah `Presicion` dan `Recall`, didapatkan dengan menghitung persentase dari jumlah prediksi yang benar dibagi dengan jumlah seluruh prediksi. 
Langkah-langkah Utama dalam Evaluasi:
- Pembagian Data:
  Data dibagi menjadi train dan test menggunakan train_test_split dengan 20% data untuk pengujian.
- Kategori Relevan:
  Kali ini model hanya mengevaluasi tempat dengan kategori 'Budaya' dan 'Alam'.
- Looping pada Data Uji:
  Sistem mengevaluasi rekomendasi berdasarkan apakah rekomendasi mencakup kategori relevan.
- Menghitung Precision:
  Precision diukur sebagai proporsi rekomendasi yang relevan dibandingkan dengan total rekomendasi.
- Menghitung Recall:
  Recall diukur sebagai proporsi rekomendasi relevan yang ditemukan dibandingkan dengan total tempat yang relevan dalam dataset.
- Rata-rata Precision dan Recall:
  Precision dan Recall rata-rata dihitung dari semua iterasi data uji.

Rumus:

$$precision = \frac{TP}{TP + FP}$$

   Di mana:
   
   - $TP =$ _True Positive_; rekomendasi yang sesuai.
   
   - $FP =$ _False Positive_; rekomendasi yang tidak sesuai.


$$Recall = \frac{TP}{TP + FN}$$

   Di mana:
   
   - $TP =$ _True Positive_; rekomendasi yang sesuai.
   
   - $FN =$ _False Negative_; Jumlah item relevan yang tidak ditemukan dalam rekomendasi.

Hasil Akhir dari evaluasi metriks dengan menggunakan rumus diatas, didapatkan:
| Evaluate Metrics | Result |
| -------| ----- |
| Precision | 0.26 |
| Recall | 0.01 |

Kesimpulan dari evaluasi metriks diatas, ialah
- Precision (0.26) menunjukkan bahwa beberapa rekomendasi benar, tetapi kualitas rekomendasi masih belum konsisten (banyak tempat tidak relevan yang direkomendasikan).
- Recall (0.01) yang sangat rendah menunjukkan bahwa sistem hampir tidak mampu menemukan item relevan di dataset untuk direkomendasikan.

_Referensi:_
- https://www.kaggle.com/aprabowo/indonesia-tourism-destination
- Mondi, R. H., Wijayanto, A., & Winarno, W. (2019). Recommendation System With Content-Based Filtering Method for Culinary Tourism in Mangan Application. ITSMART: Jurnal Teknologi dan Informasi, 8(2), 65-72.
- Savero, R. R., Antaryama, G. N., & Soemardiono, B. (2020). OPINION ANALYSIS OF TRAVELER BASED ON TOURISM SITE REVIEW USING SENTIMENT ANALYSIS. IPTEK The Journal for Technology and Science, 31(2), 236-248.
