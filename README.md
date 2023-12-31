# Analisis_Video_Game_Sales

Proyek ini merupakan bagian dari pengembangan pribadi saya dalam memahami workflow analisis data. Pada proyek ini saya menggunakan bahasa pemrograman Python dengan beberapa library seperti Pandas, NumPy, Seaborn, dan Matplotlib.

---

Dataset [video_game_sales.csv](video_game_sales.csv) saya ambil dari website Kaggle. Pada data tersebut terdapat 11 Kolom dan 16599 baris.

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
1. Game dengan penjualan terbanyak?
2. Genre game yang paling banyak dibuat?
3. Platform yang paling banyak memiliki game?
4. Publisher dengan penjualan terbanyak?
    - Top 3 Game paling diminati dari publisher tersebut?
5. Tahun berapa perilisan game tertinggi?
	- 3 Game apa yang memiliki penjualan tertinggi pada tahun tersebut?
	- Genre apa yang paling banyak dibuat pada tahun tersebut?
6. Penjualan game pada region mana yang paling tinggi?
7. Tahun berapa penjualan game terbanyak di seluruh dunia?

---

## Proses Analisis
Langkah awal yang saya lakukan pada proses ini adalah melakukan pengecekan data, dimana saya melakukan pengecekan ringkasan dataframe dengan menggunakan `.info()` dan `.isnull().sum()` untuk melihat jumlah null dari setiap kolom.

  ![summary](pic/1.%20Cek%20Kolom.png) ![null](pic/2.%20Cek%20Null.png) 

Dari gambar diatas, saya mendapatkan informasi untuk kolom Rank, Name, Platform, Genre, NA_Sales, EU_Sales, JP_Sales, Other_Sales, Global_Sales memiliki 16598 data yang tidak null atau tidak ada data null, lalu untuk kolom Year memiliki 271 data null dan kolom Publisher memiliki 59 data yang  null.

---

#### Mengecek Data Unik 

Pada tahap ini saya melakukan pengecekan untuk data pada kolom Platform, Genre dan Publisher. Pada tahap ini saya menggunakan metode `.unique` dan `.nunique` untuk melihat semua informasi setiap kolom tanpa ada data yang duplikat dan menghitung berapa jumlah data yang unik. Berikut hasil pengecekannya:

##### Platform
Terdapat 31 jenis platform yang berbeda pada kolom Platform, berikut list platformnya
![Platform](pic/3.%20Cek%20Platform.png)

##### Genre
Terdapat 12 jenis genre yang berbeda pada kolom Genre, berikut list genrenya
![Genre](pic/4.%20Cek%20Genre.png)

##### Publisher
Terdapat 578 publisher pembuat game berbeda pada kolom Publisher, berikut list publishernya
![Publisher](pic/5.%20Cek%20Publisher.png) 

---

### Mencari 10 game dengan penjualan terbanyak
Untuk mencari 10 game dengan penjualan terbanyak, hal pertama yang saya lakukan adalah mengelompokan data berdasarkan nama dan menjumlahkan kolom Global_Sales yang sudah dikelompokan berdasarkan nama, berikut kodenya `df.groupby('Name')['Global_Sales'].sum().reset_index()`.

Langkah selanjutnya adalah mengurutkan data sebelumnya berdasarkan Kolom Global_Sales dari terbesar hingga terkecil dengan kode `grouped.sort_values(by='Global_Sales', ascending=False)`. 

Langkah terakhir adalah mengambil 10 nama teratas setelah dilakukan sorting dengan kode `sorted_data.iloc[0:10,:]` dimana saya mengambil 10 baris dari index 0-9.

Berikut hasil pencarian untuk 10 game dengan penjualan terbanyak
![toptengame](pic/6.%20Hasil%20Top%2010%20Sales%20Game.png)
![toptengamechart](pic/6.1%20Grafik%20Hasil%20Top%2010%20Sales%20Game.png)

Dari hasil diatas didapat 10 besar game dengan total penjualan terbanyak dimana game dengan penjualan tertinggi adalah Wii Sports dengan total penjualan 82.74 juta dan game dengan total penjualan terbanyak nomor 10 adalah New Super Mario Bros dengan total penjualan 30.01 juta.

---

### Mancari genre game yang paling banyak dibuat
Pada proses ini, untuk mencari jumlah genre yang paling banyak dibuat, pertama saya melakukan penghapusan untuk nama game yang sama(duplikat) dengan cara `df.drop_duplicates(subset='Name')`. Selanjutnya saya menhitung setiap genre pada kolom Genre dengan metode `.value_counts()`.

![topgenre](pic/7%20Hasil%20Sort%20Genre%20High%20to%20Low.png)
![topgenrechart](pic/8.%20Grafik%20Genre.png)

Dari gambar diatas didapatkan informasi bahwa untuk genre game yang paling banyak dibuat adalah genre Action dengan jumlah 3316 game dan genre paling sedikit adalah puzzle dengan jumlah game sebanyak 582.

---

### Mencari jumlah game dari setiap platform
Untuk mencari jumlah game dari setiap platsform prosesnya sama dengan sebelumnya, pertama saya melakukan penghapusan untuk nama game yang sama(duplikat) dan menghitung setiap platform pada kolom Platform.

![topplatform](pic/7.2%20platform.png)

Dari gambar diatas untuk platform dengan game terbanyak adalah PS2 yaitu dengan 1861 game dan diikuti oleh DS dengan 1807 game.

---

### Mencari publisher yang merilis game terbanyak
Pada proses ini saya mencari publisher yang merilis game terbanyak dengan cara melakukan pengelompokan data dari publisher dengan kondisi jika ada nama game yang sama pada kolom Name akan dihitung satu game. Berikut kode yang saya gunakan `df.groupby('Publisher')['Name'].nunique()`.

![publisher](pic/8.1%20Publisher.png)

Hasilnya dapat dilihat bahwa Namco Bandai Games adalah publisher yang paling banyak merilis game, yaitu sebanyak 776 game.

Setelah saya mengetahui bahwa Namco Bandai Games adalah publisher yang paling banyak merilis game, selanjutnya saya mencari game dari Namco yang memiliki penjualan terbanyak. 
Proses pertama yang saya lakukan adalah mengambil subset dari dataframe yang mana nilai kolom Publisher hanya Namco Bandai Games menggunakan kode `df_NBG = df[df['Publisher']=='Namco Bandai Games']` selanjutnya saya pengelompokan kolom Name dari dataset `df_NBG` dan menjumlahkan total penjualan berdasarkan kolom Global_Sales dengan kode `grouped = df_NBG.groupby('Name')['Global_Sales'].sum().reset_index()`.

![publisher2](pic/8.1.2%20Publisher.png)

Dari gambar diatas 3 game dari Namco Bandai Games yang memiliki penjualan tertinggi adalah Namco Museum, The Witcher 3: Wild Hunt dan Namco Museum: 50th Anniversary.

---

### Mencari tahun dengan perilisan game tertinggi
Selanjutnya saya akan mencari tahun dengan perilisan game tertinggi, lalu game apa saja yang penjualannya tertinggi di tahun tersebut dan genre apa yang paling banyak dibuat pada tahun tersebut.

Dikarenakan pada kolom Year terdapat data yang kosong (N/A) maka saya merubah bari yang bertuliskan N/A menjadi NaN dengan `df['Year'] = df['Year'].replace('N/A', np.nan)`, lalu baris yang berisi NaN di hapus dengan `.dropna` dan menetapkan nilainya kembali menjadi 0 dengan tipe data integer dengan kode `.fillna(0).astype(int)`.

![listyear](pic/11.1.%20List%20Year.png)
![graphyear](pic/11.%20Grafik%20Year.png)

Dari gambar diatas saya mendapatkan informasi bahwa 2009 adalah tahun dimana perilisan game paling banyak. 

Dari informasi itu selanjutnya saya mencari game dan genre yang paling banyak terjual pada tahun 2009.

Untuk pencarian game terlaris di 2009 pertama saya melakukan filter pada kolom Year dengan kode `df_2009 = df[df['Year']==2009]`, dan melakukan pencarian dengan `df_2009.groupby('Name')['Global_Sales'].sum().reset_index()` dimana saya kelompokan Kolom nama dari dataframe yang sudah di filter ke tahun 2009 kemudian menjumlahkan total penjualan setiap game.

![topgame2009](pic/12.%203%20Game%20dengan%20penjualan%20terbanyak%20tahun%202009.png)

Dari proses diatas saya mendapatkan bahwa pada tahun 2009 game yang memiliki penjualan tertinggi adalah Wii Sports Resort, diikuti dengan game New Super Mario Bros. Wii dan Call of Duty: Modern Warfare 2.

Lalu untuk mencari genre yang paling banyak dibuat pada tahun 2009 saya masih menggunakan dataframe yang sudah di filter yaitu `df_2009`, lalu mengelompokan kolom genre dan memakai kode `.size()`.

![topgenre2009](pic/13%20Hasil%20Sort%20Genre%20High%20to%20Low%202009.png)

Dari proses tersebut pada gambar diatas saya mendapat informasi bahwa genre yang paling banyak dibuat pada tahun 2009 adalah genre action yang mencapai 272 game.

---

### Mencari jumlah penjualan game di setiap region

Untuk mencari jumlah penjualan di setiap region, di sini saya membuat sebuah daftar yang disebut regions yang berisi nama kolom yang merepresentasikan penjualan game di wilayah yang berbeda dengan cara `regions = ['NA_Sales', 'EU_Sales', 'JP_Sales', 'Other_Sales']`. 

Setelah membuat daftar regions, selanjutnya saya menjumlahkan setiap region dengan cara `regions_sales = df[regions].sum()`. Hasil dari perhitungan ini akan menghasilkan sebuah Series (serangkaian data) yang berisi total penjualan untuk masing-masing wilayah yang ada dalam daftar regions.

![region](pic/10.%20Total%20Sale%20per%20Region.png)
![graphregion](pic/9.%20Grafik%20Sale%20per%20Region.png)

Dari hasil diatas dapat disimpulkan untuk region dengan total penjualan game terbanyak adalah Amerika Utara, diikuti oleh Uni Eropa dan Jepang. Lalu diluar ketiga region tersebut memiliki penjualan paling sedikit.

---

### Mencari tahun dengan penjualan game terbanyak diseluruh dunia

Untuk mencari tahun dengan penjualan tertinggi, langkah pertama yang sama lakukan adalah mengelompokan kolom Year terlebih dahulu lalu menjumlahkan kolom Global_Sales. Berikut kodenya `df.groupby('Year')['Global_Sales'].sum()`.

![topyearsell](pic/14.1%20topsellallyear.png)
![graphtopyearsell](pic/14.%20Diagram%20Garis.png)

Dari gambar diatas untuk tahun dengan penjualan terbanyak adalah tahun 2008.

---

### Kesimpulan

Dari proses yang saya lakukan dapat disimpulkan untuk game dengan total penjualan terbanyak adalah Wii Sports dengan total 82.74 juta, lalu untuk genre yang paling banyak dibuat dari tahun 1980-2020 adalah Action yaitu sebanyak 1923 game. Dan untuk platform yang memiliki game terbanyak adalah PS2 dengan jumlah game mencapai 1861.

Publisher yang merilis game paling banyak dari hasil analisis ini adalah Namco Bandai Game, dimana publisher ini merilis 776 game berbeda dan untuk game yang paling banyak dijual adalah Namco Museum, The Witcher 3: Wild Hunt dan Namco Museum: 50th Anniversary.

Tahun 2009 adalah tahun dimana perilisan video game paling banyak yaitu sebanyak 1431 game. Lalu untuk game dengan penjualan tertinggi di tahun 2009 adalah Wii Sports Resort sebanyak 33 juta penjualan. Namun untuk hal itu tidak membuat tahun 2009 menjadi tahun dengan penjualan game terbanyak. Untuk tahun dengan penjualan game terbanyak berada di tahun 2008.

Region yang memiliki penjualan game terbanyak adalah Amerika Utara dengan total penjualan 4,3 miliar lebih penjualan diikuti dengan Uni Eropa dengan total 2,4 miliar penjualan.

