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
3. Tahun berapa perilisan game tertinggi?
	- 3 Game apa yang memiliki penjualan tertinggi pada tahun tersebut?
	- Genre apa yang memiliki penjualan tertinggi pada tahun tersebut?
4. Penjualan game pada region mana yang paling tinggi?
	- Berapa total penjualannya?
5. Tahun berapa penjualan game terbanyak di seluruh dunia?

---

## Proses Analisis
Langkah awal yang saya lakukan pada proses ini adalah melakukan pengecekan data, dimana saya melakukan pengecekan ringkasan dataframe dengan menggunakan '.info()'.

![summary](pic/1.%20Cek%20Kolom.png)

