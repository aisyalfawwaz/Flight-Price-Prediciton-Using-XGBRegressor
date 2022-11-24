# Laporan Proyek Machine Learning - Aisy Al Fawwaz

## Domain Proyek.

Domain yang saya pilih pada proyek ini adalah **Bisnis Aviasi/Penerbangan**

Pelanggan airline pasti tidak asing dengan sistem pemesanan tiket pesawat seperti ini. Penerbangan yang sama bisa datang dengan harga yang berbeda, tergantung engine pembanding harga yang digunakan pelanggan. Waktu keberangkatan, destinasi, jarak penerbangan, dan jumlah kursi yang tersedia juga dapat memengaruhi harga tiket. Dan harga tiket yang sama pun bisa berubah dalam hitungan menit.Inilah yang disebut dynamic pricing, yaitu teknik menyesuaikan harga berdasarkan situasi terkini untuk mencapai tingkat yang paling menguntungkan (bagi airline tentunya).

Untuk itu sebuah dataset **Flight Price Prediction** yang didapatkan di platform kaggle dianalisis, adapun dataset pemesanan penerbangan yang diperoleh dari situs web “Ease My Trip” dan melakukan berbagai uji hipotesis statistik untuk mendapatkan informasi yang bermakna darinya. Algoritma statistik 'Regresi Linier' akan digunakan untuk melatih kumpulan data dan memprediksi variabel target berkelanjutan. 'Easemytrip' adalah platform internet untuk memesan tiket pesawat, dan karenanya merupakan platform yang digunakan calon penumpang untuk membeli tiket. Studi menyeluruh terhadap data akan membantu menemukan wawasan berharga yang akan sangat bermanfaat bagi calon penumpang dalam memilih maskapai penerbangan yang sesuai

## Business Understanding.

### Problem Statements

Bagaimana pengaruh variabel-variabel dalam dataset terhadap harga jual tiket pesawat ?

### Goals

Membuat prediksi harga jual tiket pesawat dari variabel variabel dalam dataset meliputi *airline, flight, source city, departure time, stops, arrival time, destination city, class, days left*, sehingga calon penumpang bisa mengetahui penyebab perbedaan harga tiket pesawat. 

### Solution statements
Solution Statements yang akan dilakukan adalah dengan menerapkan 4 algoritma *Machine Learning* yaitu :

- **K-Nearest Neighbor**.<br>
  KNN adalah algoritma yang relatif sederhana dibandingkan dengan algoritma lain. Algoritma KNN menggunakan ‘kesamaan fitur’ untuk memprediksi nilai dari setiap data yang baru. Dengan kata lain, setiap data baru diberi nilai berdasarkan seberapa mirip titik tersebut dalam set pelatihan.

- **LinearRegression**.<br>
   Linear Regression adalah variasi algoritma  Decision Trees yang membantu menghitung hubungan linier antara variabel dependen dan independen, lalu menggunakan hubungan tersebut untuk prediksi. 

- **XGBRegressor**.<br>
 XGBoostRegressor merupakan salah satu algoritma yang paling populer dan paling banyak digunakan karena algoritma ini termasuk algoritma yang powerful. Pada dasarnya, algoritma ini sama dengan algoritma gradient boost hanya saja menggunakan beberapa proses tambahan sehingga lebih powerful. Proses tersebut adalah pemangkasan, newton boosting, dan parameter pengacakan ekstra.

- **CatBoostRegressor**.<br>
  CatBoostRegressor adalah library yang populer dan berkinerja tinggi dari algoritma Gradient Boosting Decision Tree (GBDT). GBDT adalah algoritma *supervised learning* yang mencoba memprediksi variabel target secara akurat dengan menggabungkan ansambel perkiraan dari serangkaian model yang lebih sederhana dan lebih lemah.

## Data Understanding

Data atau dataset yang digunakan pada proyek machine learning ini adalah data **flight Price Prediction** yang didapat dari situs kaggle. Link dataset dapat dilihat dari tautan berikut [Clean_Dataset.csv](https://www.kaggle.com/datasets/shubhambathwal/flight-price-prediction)

Variabel-variabel pada Flight Price Prediction dataset adalah sebagai berikut :

Berbagai fitur dari kumpulan data yang dibersihkan dijelaskan di bawah ini:
1. Airline : Nama perusahaan penerbangan disimpan di kolom maskapai penerbangan. Ini adalah fitur kategoris yang memiliki 6 maskapai berbeda.
2. Flight : Penerbangan menyimpan informasi mengenai kode penerbangan pesawat. Ini adalah fitur kategorikal.
3. Source City : Kota tempat penerbangan lepas landas. Ini adalah fitur kategoris yang memiliki 6 kota unik.
4. Departure time: Ini adalah fitur kategoris turunan yang diperoleh dengan mengelompokkan periode waktu ke dalam bin. Ini menyimpan informasi tentang waktu keberangkatan dan memiliki 6 label waktu unik.
5. Stops: Fitur kategorikal dengan 3 nilai berbeda yang menyimpan jumlah perhentian antara kota sumber dan tujuan.
6. Arrival time : Ini adalah fitur kategorikal turunan yang dibuat dengan mengelompokkan interval waktu ke dalam nampan. Ini memiliki enam label waktu yang berbeda dan menyimpan informasi tentang waktu kedatangan.
7. Destination City : Kota dimana penerbangan akan mendarat. Ini adalah fitur kategoris yang memiliki 6 kota unik.
8. Class: Fitur kategorikal yang berisi informasi tentang kelas kursi; ia memiliki dua nilai berbeda: Bisnis dan Ekonomi.
9. Duration: Fitur berkelanjutan yang menampilkan jumlah keseluruhan waktu yang diperlukan untuk melakukan perjalanan antar kota dalam hitungan jam.
10. Days Left : Ini adalah karakteristik turunan yang dihitung dengan mengurangkan tanggal perjalanan dengan tanggal pemesanan.
11. Price: Variabel target menyimpan informasi harga tiket.

Setelah itu dilakukan analisis pada masing-masing variabel dengan dilakukan visualisasi data  meliputi : 

1. **Fitur perbedaan harga tiket antara kelas Ekonomi dan Bisnis?**
(https://github.com/aisyalfawwaz/Machinelearningterapan/blob/main/regressor.png?raw=truer)
2. **Fitur perbedaan harga tiket tiap maskapai**
(https://github.com/aisyalfawwaz/Machinelearningterapan/blob/main/regressor.png?raw=truer](https://github.com/aisyalfawwaz/Flight-Price-Prediciton-Using-XGBRegressor/blob/main/maskapai.png?raw=true)
3. **Fitur pengaruh harga jika tiket dibeli hanya dalam 1 atau 2 hari sebelum keberangkatan?** 
(https://github.com/aisyalfawwaz/Machinelearningterapan/blob/main/regressor.png?raw=truer)](https://github.com/aisyalfawwaz/Flight-Price-Prediciton-Using-XGBRegressor/blob/main/1%202%20keberangkatan.png?raw=true)
4. **Fitur harga berubah seiring durasi penerbangan**
(https://github.com/aisyalfawwaz/Flight-Price-Prediciton-Using-XGBRegressor/blob/main/durasi.png?raw=true)
5. **Fitur harga tiket berubah berdasarkan waktu keberangkatan dan waktu kedatangan?**
(https://github.com/aisyalfawwaz/Flight-Price-Prediciton-Using-XGBRegressor/blob/main/waktu%20keberangkatan.png?raw=true)
6. **Fitur  harga tiket pada asal dan Tujuan?**
(https://github.com/aisyalfawwaz/Machinelearningterapan/blob/main/regressor.png?raw=truer)](https://github.com/aisyalfawwaz/Flight-Price-Prediciton-Using-XGBRegressor/blob/main/asal.png?raw=true)
7. **Fitur jumlah pemberhentian mempengaruhi harga?**
(https://github.com/aisyalfawwaz/Machinelearningterapan/blob/main/regressor.png?raw=truer)](https://github.com/aisyalfawwaz/Flight-Price-Prediciton-Using-XGBRegressor/blob/main/jumlah%20pemberhentian.png?raw=true)

lalu kemudian dilakukan visualisasi untuk menganalisis terhadap fitur tersebut untuk mengetahui fitu yang paling memengaruhi harga tiket
(https://github.com/aisyalfawwaz/Flight-Price-Prediciton-Using-XGBRegressor/blob/main/paling%20memengaruhi.png?raw=true)

Dari visualisasi data diatas dapat diketahui bahwa variabel yang paling memengaruhi harga tiket adalah Kelas tiket pesawat dan durasi.

## Data Preparation

Data preparation yang digunakan oleh saya yaitu :
- melakukan encoding pada variabel stops dan kelas
- Membuat variabel dummy pada variabel cities, waktu tempuh, dan maskapai
- Membagi data menjadi data training dan test : untuk membagi data untuk dilatih dan tes (2:8)


## Modeling

Proses modeling yang saya lakukan pada data ini adalah dengan menggabungkan empat algoritma machine learning kemudian dicari performa yang paling baik dari keempat algoritma machine learning tersebut. berikut adalah parameter yang saya gunakan dari tiap-tiap model yang diuji :

models KNeighborsRegressor bekerja berdasarkan prinsip bahwa setiap titik data yang berdekatan satu sama lain akan berada di kelas yang sama. Dengan kata lain, KNN mengklasifikasikan titik data baru berdasarkan kemiripan. parameter n-neighboor yang digunakan bernilai 50

models LinearRegression bekerja dengan cara Linear Regression memprediksi nilai dari y dengan mengetahui nilai x dan menemukan nilai m dan b yang errornya paling minimal.

modelsXGBRegressormodel dipilih karena secara efektif bisa mempercepat sistem perhitungan dan mencegah overfitting karena didalmnya mengandung fitur tambahan, adapun parameter XGBRegressormodel yang digunakan memiliki nilai n_jobs=5, learning_rate=0.1 ,max_depth=10, dan random_state=1


models CatBoostRegressor memiliki nilai logging_level ='Silent', iterations=500, dan random_state=1

Setelah itu dilakukan uji tiap model dengan fungsi get_scores lalu kemudian didapatkan hasil sebagai berikut :

![Hasil tes skor dari beberapa model](https://github.com/aisyalfawwaz/Machinelearningterapan/blob/main/regressor.png?raw=truer)

dapat dilihat dari bar gambar di atas dari ke model algoritma yang dipakai, bahwa  hasil terbaik diberikan oleh XGBRegressor. Ini mungkin dijelaskan oleh fakta bahwa beberapa hubungan tidak linier seperti durasi atau hari_tersisa. Jadi algoritma yang lebih fleksibel seperti XGBRegressor cenderung memberikan hasil yang lebih baik.

Untuk itu model XGBRegressor dipilih untuk menyelesaikan permasalahan kali ini, model yang dipilih kemudian dilatih dan dilakukan validasi, hasinlnya adalah didapatkan nilai r2 sebesar 0.9838 dan nilai MAE 1588



## Evaluation

Karena kasus yang dipilih merupakan kasus regresi maka evaluasi metrik yang digunakan untuk mengukur kinerja model adalah metrik MAE (Mean absolute  Error), MAE pada dasarnya  adalah rata-rata selisih mutlak nilai sebenarnya (aktual) dengan nilai prediksi (peramalan).

Adapun cara untuk menhitung nilai MAE adalah :

(Δx) = xi – x,

dimana:
xi adalah nilai hasil pengukuran
x adalah nilai sebenarnya

oleh karena itu, semakin tinggi nilai ini maka semakin buruk modelnya dan apabila semakin mendekati nilai O maka dapat dikatakan semakin baik modelnya, adapun pada data ini didapatkan nilai MAE sebesar 1588.

