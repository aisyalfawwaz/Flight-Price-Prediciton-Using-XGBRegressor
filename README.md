# Laporan Proyek Machine Learning - Aisy Al Fawwaz

## Domain Proyek.

Domain yang saya pilih pada proyek ini adalah **Bisnis Aviasi/Penerbangan**.
Untuk itu sebuah dataset **Flight Price Prediction** yang didapatkan di platform kaggle dianalisis, adapun dataset pemesanan penerbangan yang diperoleh dari situs web “Ease My Trip” dan melakukan berbagai uji hipotesis statistik untuk mendapatkan informasi yang bermakna darinya. Algoritme statistik 'Regresi Linier' akan digunakan untuk melatih kumpulan data dan memprediksi variabel target berkelanjutan. 'Easemytrip' adalah platform internet untuk memesan tiket pesawat, dan karenanya merupakan platform yang digunakan calon penumpang untuk membeli tiket. Studi menyeluruh terhadap data akan membantu menemukan wawasan berharga yang akan sangat bermanfaat bagi calon penumpang dalam memilih maskapai penerbangan yang sesuai
## Business Understanding.

### Problem Statements

1. Menemukan Variabel  yang paling mempengaruhi harga tiket?

### Goals
Membuat prediksi harga tiket pesawat dari beberapa variabel agar para pembeli dapat dengan mudah memperhitungkan harga tiket pesawat di lain waktu

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

Proses modeling yang saya lakukan pada data ini adalah dengan menggabungkan empat algoritma machine learning kemudian dicari performa yang paling baik dari keempat algoritma machine learning tersebut. adapun metriks yang dipakai dari keempat model adalah mencari nilai r2, dimana semakin tinggi nilai r2 maka semakin bagus algoritma tersebut

![Hasil tes skor dari beberapa model](https://github.com/aisyalfawwaz/Machinelearningterapan/blob/main/regressor.png?raw=truer)

dapat dilihat dari bar gambar di atas dari ke model algoritma yang dipakai, bahwa  hasil terbaik diberikan oleh XGBRegressor. Ini mungkin dijelaskan oleh fakta bahwa beberapa hubungan tidak linier seperti durasi atau hari_tersisa. Jadi algoritma yang lebih fleksibel seperti XGBRegressor cenderung memberikan hasil yang lebih baik.


Sekarang mari kita lakukan model development menggunakan XGBRegressor

berikut adalah hasil dari modelnya  
![hasil model predisi](https://raw.githubusercontent.com/aisyalfawwaz/Machinelearningterapan/main/price.png)


## Evaluation

Evaluasi metrik yang digunakan untuk mengukur kinerja model adalah metrik MAE (Mean absolute  Error), karena kasus yang saya pilih merupakan kasus regresi.

MAE pada dasarnya  adalah rata-rata selisih mutlak nilai sebenarnya (aktual) dengan nilai prediksi (peramalan).makin tinggi nilai ini, makin buruk modelnya. Nilai MAE tidak pernah negatif, karena kita menguadratkan kesalahan prediksi individu sebelum menjumlahkannya, tetapi akan menjadi nol untuk model yang sempurna.

Selain itu, didapatkan kesimpulan bahwa :

1. Model yang memberikan hasil terbaik adalah XGBRegressor dengan pada dataset uji skor R^2 sama dengan 0,9836 dan skor MAE sama dengan 1579. 

2. Ada gap yang besar antara tiket pesawat di bisnis dan ekonomi. Rata-rata tiket bisnis 6,5 kali lebih mahal daripada tiket ekonomi.

3. Vistara dan AirIndia tampaknya menjadi perusahaan termahal dan AirAsia termurah. Namun untuk tiket bisnis, hanya Vistara dan AirIndia yang tersedia, dan Vistara sedikit lebih mahal.

4. Secara umum, harga naik cukup lambat hingga 20 hari sebelum penerbangan dimana harga naik drastis. Namun satu hari sebelum penerbangan, biasanya masih ada kursi kosong yang belum terjual. Dengan demikian dimungkinkan untuk menemukan tiket tiga kali lebih murah dari hari sebelumnya.

5. Semakin lama penerbangan semakin mahal tiketnya hingga mencapai sekitar 20 jam, maka harganya cenderung turun.

6. Keberangkatan sore dan larut malam lebih murah, dan malam hari lebih mahal. dan keberangkatan pagi, siang dan larut malam lebih murah, dan malam hari lebih mahal.

7. Penerbangan dari Delhi adalah yang termurah dari kota-kota lain rata-rata tampaknya sama tetapi sedikit lebih mahal untuk Chenai.
Penerbangan ke Delhi adalah yang termurah dan ke Bengalore yang paling mahal.

8. Secara umum, semakin banyak pemberhentian, semakin mahal harga tiket pesawatnya.

**---Ini adalah bagian akhir laporan---**
