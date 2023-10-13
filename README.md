# Analisis_Video_Game_Sales

Proyek ini merupakan bagian dari pengembangan pribadi saya dalam memahami workflow analisis data. Pada proyek ini saya menggunakan bahasa pemrograman Python dengan beberapa library seperti Pandas, NumPy, Seaborn, dan Matplotlib.

---

Dataset [video_game_sales](video_game_sales) saya ambil dari website Kaggle. Pada data tersebut terdapat 11 Kolom dan 16599 baris.

Berikut adalah penjelasan untuk setiap kolom pada dataset ini:

| Kolom                 | Deskripsi                 |
|-----------------------|---------------------------|
| No                    | Nomor Urut                |
| Name                  | Nama Game                 |
| Platform              | Media / Wadah Game        |
| Year                  | Tahun Rilis Game          |
| Genre         	    | Jenis Game                |
| Publisher     	    | Pembuat Game              |
| NA_Sales	            | Penjualan Region Amerika Utara|
| EU_Sales	            | Penjualan Region Uni Eropa|
| JP_Sales	            | Penjualan Region Jepang   |
| Other_Sales	        | Penjualan Region Lainnya  |
| Global_Sales	        | Penjualan Seluruh Region  |

---

## Pertanyaan
1. 10 Game dengan penjualan terbanyak?
2. Genre game yang paling banyak dibuat?
3. Platform yang paling sedikit memiliki game?
4. Publisher dengan penjualan terbanyak?
    - Top 3 Game paling diminati dari publisher tersebut?
5. Tahun berapa perilisan game tertinggi?
	- 3 Game apa yang memiliki penjualan tertinggi pada tahun tersebut?
	- Genre apa yang memiliki penjualan tertinggi pada tahun tersebut?
6. Penjualan game pada region mana yang paling tinggi?
	- Berapa total penjualannya?
7. Tahun berapa penjualan game terbanyak di seluruh dunia?

---

## Proses Analisis
Langkah awal yang saya lakukan pada proses ini adalah melakukan pengecekan data, dimana saya melakukan pengecekan ringkasan dataframe dengan menggunakan `.info()` dan `.isnull().sum()` untuk melihat jumlah null dari setiap kolom.

  ![summary](pic/1.%20Cek%20Kolom.png) ![null](pic/2.%20Cek%20Null.png) 

Dari gambar diatas, saya mendapatkan informasi untuk kolom Rank, Name, Platform, Genre, NA_Sales, EU_Sales, JP_Sales, Other_Sales, Global_Sales memiliki 16598 data yang tidak null atau tidak ada data null, lalu untuk kolom Year memiliki 271 data null dan kolom Publisher memiliki 59 data yang  null.

---

###Mengecek Data Unik 

Pada tahap ini saya melakukan pengecekan untuk data pada kolom Platform, Genre dan Publisher. Pada tahap ini saya menggunakan kode `.unique` dan `.nunique` untuk melihat semua informasi setiap kolom tanpa ada data yang duplikat dan menghitung berapa jumlah data yang unik. Berikut hasil pengecekannya:

#### Platform
Terdapat 31 jenis platform yang berbeda pada kolom Platform, berikut list platformnya
![Platform](pic/3.%20Cek%20Platform.png)

#### Genre
Terdapat 12 jenis genre yang berbeda pada kolom Genre, berikut list genrenya
![Genre](pic/4.%20Cek%20Genre.png)

#### Publisher
Terdapat 578 publisher pembuat game berbeda pada kolom Publisher, berikut list publishernya
![Publisher](pic/5.%20Cek%20Publisher.png) 

---