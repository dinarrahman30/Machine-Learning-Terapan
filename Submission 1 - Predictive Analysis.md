# Laporan Proyek Machine Learning - Dinar Wahyu Rahman

![British Airways](https://media.cntraveler.com/photos/577fcc03e0b5a6244f4c789c/16:9/w_2560%2Cc_limit/BritishAirways-Boeing777-AlamyF1KW8J.jpg)

## Link Notebook
[Notebook](https://github.com/dinarrahman30/Machine-Learning-Terapan/blob/main/Predictive_Analysis.ipynb)

## Domain Proyek

British Airways (BA) adalah maskapai penerbangan nasional Britania Raya (UK) [[1](https://www.britishairways.com/content/information/about-ba)]. Setiap hari, ribuan penerbangan BA tiba dan berangkat dari Inggris, membawa pelanggan dari seluruh dunia. Baik untuk liburan, pekerjaan, atau alasan lainnya, proses menyeluruh dari penjadwalan, perencanaan, naik pesawat, pengisian bahan bakar, transportasi, pendaratan, dan terus menjalankan penerbangan tepat waktu, efisien, dan dengan layanan pelanggan kelas atas merupakan tugas besar dengan banyak tanggung jawab yang sangat penting.

## Business Understanding

Pelanggan kini lebih berdaya dari sebelumnya karena mereka memiliki akses ke banyak informasi di ujung jari mereka. Inilah salah satu alasan mengapa siklus pembelian sangat berbeda dengan sebelumnya. 
Saat ini, jika Anda berharap pelanggan membeli tiket pesawat atau liburan Anda saat mereka datang ke bandara, maskapai penerbangan harus proaktif untuk mendapatkan pelanggan sebelum mereka memulai liburan. Dengan model prediktif, penting untuk menginterpretasikan hasilnya guna memahami seberapa "prediktif" data tersebut sebenarnya dan apakah kita dapat menggunakannya secara layak untuk memprediksi hasil target (pelanggan yang membeli selama liburan).

### Problem Statements

Menjelaskan pernyataan masalah latar belakang:
- Bagaimana membuat model machine learning yang dapat memprediksi pelanggan berdasarkan customer booking behavior?
- Model yang seperti apa yang memiliki akurasi paling baik?

### Goals

Menjelaskan tujuan dari pernyataan masalah:
- Bangun model prediktif berkualitas tinggi untuk memprediksi hasil target (pelanggan yang membeli selama liburan).
- Memilih algoritma model yang cocok untuk menemukan akurasi terbaik dalam memprediksi customer booking.

    ### Solution statements
    - Lakukan Analisis Data Eksploratif dari data yang disediakan oleh British Airways.
    - Bangun model prediktif berkualitas tinggi untuk memprediksi hasil target (pelanggan yang membeli selama liburan). Diantaranya membuat perbandingan dengan menggunakan model,
      - Random Forest: Algoritma machine learning dengan menggunakan prinsip umum ensemble acak dari suatu pohon keputusan [[2](https://ejournal.bsi.ac.id/ejurnal/index.php/jtk/article/view/10468/pdf)].
      - Gradient Boosting Classifier (XGBoost): Algoritme ini membangun model aditif secara bertahap; memungkinkan pengoptimalan fungsi kerugian yang dapat dibedakan secara acak. Pada setiap tahap, n_classes_ pohon regresi dipasang pada gradien negatif fungsi kerugian, misalnya kerugian log biner atau multikelas. Klasifikasi biner adalah kasus khusus di mana hanya satu pohon regresi yang diinduksi [[3](https://scikit-learn.org/1.5/modules/generated/sklearn.ensemble.GradientBoostingClassifier.html)].
      - Logistic Regression: Algoritma machine learning yang dapat bekerja pada data kategorikal yang digunakan untuk klasifikasi. Meskipun namanya mengandung kata "regression", logistic regression digunakan untuk memodelkan probabilitas dari suatu kelas atau kategori, bukan untuk regresi kontinu seperti pada linear regression [[4](https://jtiik.ub.ac.id/index.php/jtiik/article/view/8198/1332)].
      
## Data Understanding
Kumpulan data yang digunakan dikumpulkan dari situs web [Skytrax.com](https://www.airlinequality.com/), menggunakan metode web scraping. Setelah mendapatkan data, data tersebut tinggal dibersihkan dan disiapkan untuk analisis. Berikut informasi mengenai dataset: 

![image](https://github.com/user-attachments/assets/db1ac901-6c11-496c-83a4-4535e238558d)
Gambar 1. Dataset

Metode `.head()` memungkinkan kita untuk melihat 5 baris pertama dalam dataset, ini berguna untuk inspeksi visual kolom kita.

### Exploratory Data Analytics (EDA)
Exploratory data analysis merupakan proses investigasi awal pada data untuk menganalisis karakteristik, menemukan pola, anomali, dan memeriksa asumsi pada data. Teknik ini biasanya menggunakan bantuan statistik dan representasi grafis atau visualisasi.

Metode .info() memberi kita deskripsi data, yang memberi tahu kita nama kolom, tipe datanya, dan berapa banyak nilai null yang kita miliki. 
#### Variabel-variabel pada dataset adalah sebagai berikut:
- `num_passengers` = jumlah penumpang yang bepergian
- `sales_channel` = saluran penjualan tempat pemesanan dilakukan
- `trip_type` = Jenis perjalanan (Pulang Pergi, Sekali Jalan, Perjalanan Lingkaran)
- `purchase_lead` = jumlah hari antara tanggal perjalanan dan tanggal pemesanan
- `length_of_stay` = jumlah hari yang dihabiskan di tempat tujuan
- `flight_hour` = jam keberangkatan pesawat
- `flight_day` = hari keberangkatan pesawat
- `route` = rute penerbangan asal -> tujuan
- `booking_origin` = negara tempat pemesanan dilakukan
- `wants_extra_baggage` = jika pelanggan menginginkan bagasi tambahan dalam pemesanan
- `wants_preferred_seat` = jika pelanggan menginginkan kursi pilihan dalam pemesanan
- `wants_in_flight_meals` = jika pelanggan menginginkan makanan dalam pesawat dalam pemesanan
- `flight_duration` = total durasi penerbangan (dalam jam)
- `booking_complete` = tanda yang menunjukkan apakah pelanggan telah menyelesaikan pemesanan

Ringkasan informasi yang kita dapat dari `Data Understanding` ialah,

- Dataset berupa CSV (Comma-Seperated Values).  
- Dataset memiliki 50000 sample dengan jumlah kolom sebanyak 14.
- Dataset sebelum konversi kolom flight_day berjumlah data int64 berjumlah 8, data object berjumlah 5, dan data float64 berjumlah 1.
- Dataset setelah konversi kolom flight_day berumlah data int64 berjumlah 9, data object berjumlah 4, dan data float64 berjumlah 1. Konversi ini memudahkan untuk mencari MI scores.
- Tidak terdapat missing value dalam dataset.

#### MI Scores
Menghitung Mutual Information (MI) scores antara fitur independen (X) dan target (y) dalam dataset. MI mengukur tingkat ketergantungan antara variabel, memberikan wawasan tentang pentingnya setiap fitur terhadap target dalam tugas klasifikasi. Guna untuk membantu mendapatkan MI Score, kita melakukan konversi `flight_day` dari mengubah nilai-nilai dalam kolom `flight_day` di DataFrame df dari nama hari menjadi angka sesuai dengan urutan hari dalam satu minggu. Guna memudahkan dalam machine learning. Penjelasan detailnya:

mapping:

- Sebuah dictionary yang memetakan nama hari ke angka.
Contoh: "Mon" dipetakan menjadi 1, "Tue" menjadi 2, dan seterusnya.
`df["flight_day"].map(mapping)`:

- Fungsi .map() digunakan untuk mengganti setiap nilai dalam kolom `flight_day` dengan nilai yang sesuai dalam dictionary mapping.
Jika nilai dalam kolom tidak ada di mapping, nilai tersebut akan diganti menjadi NaN.

![image](https://github.com/user-attachments/assets/0ca8f7d3-b5fb-401c-b0d3-a3bc855f2280)
Gambar 2. MI Scores

## Data Preparation
Data Preparation merupakan tahap untuk mempersiapkan data sebelum masuk ke tahap pembuatan model Machine Learning:
- Converting Column Type (Mengubah tipe suatu kolom) dengan Label Encoder, Label Encoder adalah teknik dalam machine learning yang digunakan untuk mengubah nilai kategori (categorical values) menjadi angka (numerical values) yang dapat mempermudah dalam menjalankan model machine learning.
  - Dapat kita lihat data yang sesuah di encoding berjumlah data 1 fitur bertipe float64 dan 12 fitur bertipe int64.
- Train Test Split (dengan pembagian data menjadi data latih 80% dan data uji 20%).

## Modeling
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Anda perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan.
* **RandomForestClassification**: Random Forest adalah algoritma ensemble yang menggunakan banyak decision trees. Setiap tree dilatih pada subset data yang diambil secara acak, dan hasil prediksi didasarkan pada voting mayoritas dari semua tree.
  
  Parameter yang digunakan adalah:
  - `n_estimators`.
      - Jumlah decision tree yang digunakan dalam ensemble.
      - Value: Integer (contoh: 10, 100, 200).
      - Default: 100. 
  
  Keuntungan:
  * Deteksi pentingnya fitur
  * Fleksibel

  Kekurangan:
  * Potensi overfitting
  * Kurang optimal untuk data skala kecil
  
* **Gradient Boosting Classifier (XGBoost)**: XGBoost adalah algoritma boosting berbasis gradient descent yang secara iteratif membangun tree baru untuk mengurangi error dari prediksi sebelumnya. Tujuannya adalah untuk meminimalkan fungsi loss secara iteratif.
  
  Parameter yang digunakan adalah:
  - `random_state` 
      - Integer (misal: 42, 0, 123).
      - Pengambilan sampel secara acak.
      - Default: 42.
  
  Keuntungan:
  * Performa tinggi
  * dapat menangani data non-linier
  * Fitur tambahan, seperti handling missing value

  Kekurangan:
  * Resiko overfitting
  * Memerlukan banyak data
  * Kompleksitas
     
* **Logistic Regression**: Logistic Regression adalah algoritma klasifikasi yang menggunakan fungsi logistik untuk memodelkan hubungan antara variabel independen dan probabilitas hasil kategori. Hasilnya adalah nilai probabilitas yang kemudian diubah menjadi kategori dengan threshold tertentu (biasanya 0.5).

  Parameter yang digunakan adalah:
  - `max_iter`
      - Menentukan jumlah maksimum iterasi saat algoritma konvergen.
      - Value: Integer (contoh: 100, 1000).
      - Default: 100.
  
  Keuntungan:
  * Sederhana dan cepat
  *  Efisien untuk data linier

  Kekurangan:
  * Sensitif terhadap korelasi antar fitur
  * Tidak cocok untuk data non-linier
  * Kinerja terbatas terhadap data kompleks

## Evaluation
Dalam tahap evaluasi, metrik yang digunakan adalah `accuracy`
Accuracy didapatkan dengan menghitung persentase dari jumlah prediksi yang benar dibagi dengan jumlah seluruh prediksi. Rumus:

$$\text{Accuracy} = \frac{\text{TP + TN}}{\text{TN + TP + FN + FP}} \times 100\%$$

*Penjelasan*
- TP (True Positive): Jumlah data positif yang diprediksi dengan benar sebagai positif.
- TN (True Negative): Jumlah data negatif yang diprediksi dengan benar sebagai negatif.
- FP (False Positive): Jumlah data negatif yang diprediksi secara tidak benar sebagai positif (Kesalahan Tipe I).
- FN (False Negative): Jumlah data positif yang diprediksi secara tidak benar sebagai negatif (Kesalahan Tipe II).

Rumus ini memecah akurasi menjadi rasio antara data yang diklasifikasikan dengan benar (TP dan TN) dengan jumlah total data. Mengalikan dengan 100% mengubah rasio menjadi persentase.

Berikut hasil accuracy dari ketiga model yang latih:
| Model | Accuracy |
| ------ | ------ |
| RandomForest  | 0.8553 |
| XGBoost | 0.851 |
| Logistic Regression | 0.852 |

Tabel 1. Hasil Akurasi

![image](https://github.com/user-attachments/assets/0cc44c61-72cf-4f79-b982-c2408a934eb6)

Gambar 3. Hasil dari akurasi berbagai model

## Section Tambahan - Feature Important
Top 5 Customer Behavior dengan model Random Forest,
1. purchase_lead
2. route
3. light_hour
4. length_of_stay
5. booking_origin

![image](https://github.com/user-attachments/assets/be00fe07-7c7a-44b1-845f-6c67db361b98)

Gambar 4. Top 5 Customer Behavior

Dilihat dari Tabel 1. Hasil Accuracy dapat diketahui bahwa model dengan algoritma Random Forest memiliki Accuracy yang lebih tinggi dengan accuracy 85.4% . Untuk itu model tersebut yang akan dipilih untuk digunakan. Alasan mengapa metode Random Forest yang dipilih karena Random Forest adalah algoritma yang sederhana dan fleksibel dibandingkan. Hal ini membuatnya lebih mudah untuk dipahami, diimplementasikan, dan diinterpretasikan. KNN juga tidak memiliki banyak parameter yang perlu dioptimalkan, sehingga lebih mudah untuk digunakan. Pada gambar 4, dengan menggunakan model Random Forest didapatkan top 5  fitur customer behavior ketika sedang melakukan pemesanan tiket. Customer akan mempertimbangkan kelima fitur di atas dalam memesan tiket. Kita dalam menggunakan top 5 fitur ini untuk membuat pengambilan keputusan bisnis perusahaan.



_Referensi_
- https://www.britishairways.com/content/information/about-ba
