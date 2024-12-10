# Laporan Proyek Machine Learning - Dinar Wahyu Rahman

![British Airways](https://media.cntraveler.com/photos/577fcc03e0b5a6244f4c789c/16:9/w_2560%2Cc_limit/BritishAirways-Boeing777-AlamyF1KW8J.jpg)

## Domain Proyek

British Airways (BA) adalah maskapai penerbangan nasional Britania Raya (UK) [[1](https://www.britishairways.com/content/information/about-ba)]. Setiap hari, ribuan penerbangan BA tiba dan berangkat dari Inggris, membawa pelanggan dari seluruh dunia. Baik untuk liburan, pekerjaan, atau alasan lainnya, proses menyeluruh dari penjadwalan, perencanaan, naik pesawat, pengisian bahan bakar, transportasi, pendaratan, dan terus menjalankan penerbangan tepat waktu, efisien, dan dengan layanan pelanggan kelas atas merupakan tugas besar dengan banyak tanggung jawab yang sangat penting.

## Business Understanding

Pelanggan kini lebih berdaya dari sebelumnya karena mereka memiliki akses ke banyak informasi di ujung jari mereka. Inilah salah satu alasan mengapa siklus pembelian sangat berbeda dengan sebelumnya. 
Saat ini, jika Anda berharap pelanggan membeli tiket pesawat atau liburan Anda saat mereka datang ke bandara, maskapai penerbangan harus proaktif untuk mendapatkan pelanggan sebelum mereka memulai liburan. Dengan model prediktif, penting untuk menginterpretasikan hasilnya guna memahami seberapa "prediktif" data tersebut sebenarnya dan apakah kita dapat menggunakannya secara layak untuk memprediksi hasil target (pelanggan yang membeli selama liburan).

Bagian laporan ini mencakup:

### Problem Statements

Menjelaskan pernyataan masalah latar belakang:
- Bagaimana membuat model machine learning yang dapat memprediksi pelanggan berdasarkan customer booking behavior?
- Model yang seperti apa yang memiliki akurasi paling baik?
- Bagaimana model ini dapat membantu perusahaan?

### Goals

Menjelaskan tujuan dari pernyataan masalah:
- Bangun model prediktif berkualitas tinggi untuk memprediksi hasil target (pelanggan yang membeli selama liburan).
- Memilih algoritma model yang cocok untuk menemukan akurasi terbaik dalam memprediksi customer booking.

    ### Solution statements
    - Lakukan Analisis Data Eksploratif dari data yang disediakan oleh British Airways.
    - Bangun model prediktif berkualitas tinggi untuk memprediksi hasil target (pelanggan yang membeli selama liburan).
    - Evaluasi model pembelajaran mesin yang telah dibuat.
    - Ringkas temuan utama analisis, beserta penjelasan yang jelas dan ringkas.
      
## Data Understanding
Kumpulan data yang digunakan dikumpulkan dari situs web [Skytrax.com](https://www.skytrax.com), menggunakan metode web scraping. Setelah mendapatkan data, data tersebut tinggal dibersihkan dan disiapkan untuk analisis. Berikut informasi mengenai dataset:  

### Variabel-variabel pada dataset adalah sebagai berikut:
- `num_passengers` = number of passengers travelling
- `sales_channel` = sales channel booking was made on
- `trip_type` = trip Type (Round Trip, One Way, Circle Trip)
- `purchase_lead` = number of days between travel date and booking date
- `length_of_stay` = number of days spent at destination
- `flight_hour` = hour of flight departure
- `flight_day` = day of week of flight departure
- `route` = origin -> destination flight route
- `booking_origin` = country from where booking was made
- `wants_extra_baggage` = if the customer wanted extra baggage in the booking
- `wants_preferred_seat` = if the customer wanted a preferred seat in the booking
- `wants_in_flight_meals` = if the customer wanted in-flight meals in the booking
- `flight_duration` = total duration of flight (in hours)
- `booking_complete` = flag indicating if the customer completed the booking

![2](https://github.com/user-attachments/assets/dda76384-998d-4063-92d9-201e0b365755)
Gambar 1. Dataset

- Dataset berupa CSV (Comma-Seperated Values).
- Dataset memiliki 4999 sample.
- Dataset memiliki 1 fitur bertipe float64, 8 fitur bertipe int64, dan 5 fitur bertipe object.
- Tidak terdapat missing value dalam dataset.

## Data Preparation
Pada proses Data Preparation dilakukan kegiatan seperti Data Gathering, Data Assessing, dan Data Cleaning. Pada proses Data Gathering, data diimpor sedemikian rupa agar bisa dibaca dengan baik menggunakan dataframe Pandas. Untuk proses Data Assessing, berikut adalah beberapa pengecekan yang dilakukan:
- Duplicate data (data yang serupa dengan data lainnya).
- Missing value (data atau informasi yang "hilang" atau tidak tersedia)
- Outlier (data yang menyimpang dari rata-rata sekumpulan data yang ada).
- Menghitung Mutual Information (MI) scores antara fitur independen (X) dan target (y) dalam dataset. MI mengukur tingkat ketergantungan antara variabel, memberikan wawasan tentang pentingnya setiap fitur terhadap target dalam tugas klasifikasi.

![image](https://github.com/user-attachments/assets/0ca8f7d3-b5fb-401c-b0d3-a3bc855f2280)
Gambar 2. MI Scores

Pada proses Data Cleaning yang dilakukan adalah seperti:
- Converting Column Type (Mengubah tipe suatu kolom) dengan Label Encoder, Label Encoder adalah teknik dalam pembelajaran mesin yang digunakan untuk mengubah nilai kategori (categorical values) menjadi angka (numerical values).
- Train Test Split (membagi data menjadi data latih dan data uji).

## Modeling
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Anda perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan.
* RandomForestClassification: Untuk model yang lebih kompleks dan mampu menangani interaksi fitur.
    * Keuntungan:
        * Deteksi pentingnya fitur
        * Fleksibel
    * Kekurangan:
        * Potensi overfitting
        * Kurang optimal untuk data skala kecil
* Gradient Boosting Classifier (XGBoost):
    * Keuntungan:
          * Performa tinggi
          * dapat menangani data non-linier
          * Fitur tambahan, seperti handling missing value
    * Kekurangan:
          * Resiko overfitting
          * Memerlukan banyak data
          * Kompleksitas     
* Logistic Regression:
     * Keuntungan:
          * Sederhana dan cepat
          * Efisien untuk data linier
    * Kekurangan:
          * Sensitif terhadap korelasi antar fitur
          * Tidak cocok untuk data non-linier
          * Kinerja terbatas terhadap data kompleks
      
* KFold: Kelas ini digunakan untuk membagi kumpulan data Anda menjadi K lipatan berurutan untuk validasi silang.

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
| RandomForest  | 0.8543 |
| XGBoost | 0.851 |
| Logistic Regression | 0.852 |

Tabel 1. Hasil Akurasi

![image](https://github.com/user-attachments/assets/0cc44c61-72cf-4f79-b982-c2408a934eb6)

Gambar 3. Hasil dari akurasi berbagai model


Top 5 Customer Behavior dengan model Random Forest
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
