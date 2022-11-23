# Laporan Proyek Machine Learning - Aisy Al Fawwaz

## Domain Proyek.

Domain yang saya pilih pada proyek ini adalah **Bisnis Aviasi/Penerbangan**.
Untuk itu sebuah dataset **Flight Price Prediction** yang didapatkan di platform kaggle dianalisis, adapun dataset pemesanan penerbangan yang diperoleh dari situs web “Ease My Trip” dan melakukan berbagai uji hipotesis statistik untuk mendapatkan informasi yang bermakna darinya. Algoritme statistik 'Regresi Linier' akan digunakan untuk melatih kumpulan data dan memprediksi variabel target berkelanjutan. 'Easemytrip' adalah platform internet untuk memesan tiket pesawat, dan karenanya merupakan platform yang digunakan calon penumpang untuk membeli tiket. Studi menyeluruh terhadap data akan membantu menemukan wawasan berharga yang akan sangat bermanfaat bagi calon penumpang dalam memilih maskapai penerbangan yang sesuai

## Business Understanding.

### Problem Statements

Bagaiamana  Variabel  mempengaruhi harga tiket masing-masing maskapai ?

### Goals
Membuat prediksi harga tiket pesawat dari beberapa variabel dalam dataset, hasil prediksi nantinya digunakan para pembeli untuk mengetahui harga tiket pesawat tiap maskpai syang cocok bagi mereka.

### Solution statements
Solution Statements yang akan dilakukan adalah dengan menerapkan 4 algoritma Machine Learning yaitu :

- **K-Nearest Neighbor**.<br>
  KNN adalah algoritma yang relatif sederhana dibandingkan dengan algoritma lain. Algoritma KNN menggunakan ‘kesamaan fitur’ untuk memprediksi nilai dari setiap data yang baru. Dengan kata lain, setiap data baru diberi nilai berdasarkan seberapa mirip titik tersebut dalam set pelatihan.

- **LinearRegression**.<br>
   Linear Regression adalah variasi algoritma  Decision Trees yang membantu menghitung hubungan linier antara variabel dependen dan independen, lalu menggunakan hubungan tersebut untuk prediksi. 

- **XGBRegressor**.<br>
 XGBoostRegressor merupakan salah satu algoritma yang paling populer dan paling banyak digunakan karena algoritma ini termasuk algoritma yang powerful. Pada dasarnya, algoritma ini sama dengan algoritma gradient boost hanya saja menggunakan beberapa proses tambahan sehingga lebih powerful. Proses tersebut adalah pemangkasan, newton boosting, dan parameter pengacakan ekstra.

- **CatBoostRegressor**.<br>
  CatBoostRegressor adalah library yang populer dan berkinerja tinggi dari algoritma Gradient Boosting Decision Tree (GBDT). GBDT adalah algoritma pembelajaran yang diawasi yang mencoba memprediksi variabel target secara akurat dengan menggabungkan ansambel perkiraan dari serangkaian model yang lebih sederhana dan lebih lemah.

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

## Data Preparation

Data preparation yang digunakan oleh saya yaitu :
- melakukan encoding pada variabel stops dan kelas
- Membuat variabel dummy pada variabel cities, waktu tempuh, dan maskapai
- Membagi data menjadi data training dan test : untuk membagi data untuk dilatih dan tes (2:8)


## Modeling

Proses modeling yang saya lakukan pada data ini adalah dengan menggabungkan empat algoritma machine learning kemudian dicari performa yang paling baik dari keempat algoritma machine learning tersebut. berikut adalah parameter yang saya gunakan dari tiap-tiap model yang diuji :

models KNeighborsRegressor memiliki n-neighboor dengan nilai 50
models LinearRegression memiliki parameter bawaan
modelsXGBRegressormodel memiliki nilai n_jobs=5, learning_rate=0.1 ,max_depth=10, dan random_state=1
models CatBoostRegressor memiliki nilai logging_level ='Silent', iterations=500, dan random_state=1

Setelah itu dilakukan uji tiap model dengan fungsi get_scores lalu kemudian didapatkan hasil sebagai berikut :

![Hasil tes skor dari beberapa model](https://github.com/aisyalfawwaz/Machinelearningterapan/blob/main/regressor.png?raw=truer)

dapat dilihat dari bar gambar di atas dari ke model algoritma yang dipakai, bahwa  hasil terbaik diberikan oleh XGBRegressor. Ini mungkin dijelaskan oleh fakta bahwa beberapa hubungan tidak linier seperti durasi atau hari_tersisa. Jadi algoritma yang lebih fleksibel seperti XGBRegressor cenderung memberikan hasil yang lebih baik.

Untuk itu model XGBRegressor dipilih untuk menyelesaikan permasalahan kali ini, model yang dipilih kemudian dilatih dan dilakukan validasi, hasil dari nilai prediksi dan validasi divisualisasikan menjadi gambar dibawah ini :

![hasil model predisi](https://raw.githubusercontent.com/aisyalfawwaz/Machinelearningterapan/main/price.png)


## Evaluation

Karena kasus yang dipilih merupakan kasus regresi maka evaluasi metrik yang digunakan untuk mengukur kinerja model adalah metrik MAE (Mean absolute  Error), MAE pada dasarnya  adalah rata-rata selisih mutlak nilai sebenarnya (aktual) dengan nilai prediksi (peramalan).

Adapun cara untuk menhitung nilai MAE adalah :

(Δx) = xi – x,

dimana:
xi adalah nilai hasil pengukuran
x adalah nilai sebenarnya

oleh karena itu, semakin tinggi nilai ini maka semakin buruk modelnya dan apabila semakin mendekati nilai O maka dapat dikatakan semakin baik modelnya, adapun pada data ini mendapatkan nilai MAE sebesar 1588.

