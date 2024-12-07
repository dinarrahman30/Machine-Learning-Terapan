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

- Dataset berupa CSV (Comma-Seperated Values).
- Dataset memiliki 4999 sample.
- Dataset memiliki 1 fitur bertipe float64, 8 fitur bertipe int64, dan 5 fitur bertipe object.
- Tidak terdapat missing value dalam dataset.

## Data Preparation
Pada proses Data Preparation dilakukan kegiatan seperti Data Gathering, Data Assessing, dan Data Cleaning. Pada proses Data Gathering, data diimpor sedemikian rupa agar bisa dibaca dengan baik menggunakan dataframe Pandas. Untuk proses Data Assessing, berikut adalah beberapa pengecekan yang dilakukan:
- Duplicate data (data yang serupa dengan data lainnya).
- Missing value (data atau informasi yang "hilang" atau tidak tersedia)
- Outlier (data yang menyimpang dari rata-rata sekumpulan data yang ada).

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

* KFold: Kelas ini digunakan untuk membagi kumpulan data Anda menjadi K lipatan berurutan untuk validasi silang.
* 

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

Berikut hasil accuracy RandomForestClassification model yang latih:

![Haisl dari evaluasi](https://github.com/user-attachments/assets/eb55e20e-9de8-498c-a3e2-e41b125def0d)


_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
