# Laporan Proyek Machine Learning - Prediksi Konsumsi Energi

## Domain Proyek

Prediksi konsumsi energi yang memperhitungkan berbagai faktor seperti suhu, kelembaban udara, luas bangunan, tingkat hunian, penggunaan HVAC dan pencahayaan, energi terbarukan, hari dalam seminggu, serta hari libur, sangat penting untuk mengoptimalkan penggunaan energi secara efisien [[1](https://ideas.repec.org/a/eee/energy/v32y2007i9p1761-1768.html)] [[2](https://www.sciencedirect.com/science/article/abs/pii/S0957582021004663)]. Kemampuan memprediksi konsumsi tentunya membantu sekali dalam rangka penghematan energi untuk tetap menjaga bumi.  

Variasi dalam faktor-faktor ini dapat signifikan memengaruhi konsumsi energi, seperti suhu dan kelembaban yang mempengaruhi penggunaan HVAC dan pencahayaan, serta luas bangunan yang mempengaruhi kebutuhan energi secara keseluruhan [[3](https://jurnal.untan.ac.id/index.php/Elkha/article/download/3002/2961)] [[4](https://id.wikihow.com/Mencari-Luas))]. Selain itu, faktor-faktor seperti tingkat hunian, penggunaan energi terbarukan, hari dalam seminggu, dan hari libur juga berkontribusi pada fluktuasi dalam konsumsi energi [[5](https://publication.petra.ac.id/index.php/acesa/article/download/13450/11654)] [[6](https://scholarhub.ui.ac.id/cgi/viewcontent.cgi?article=1301&context=jepi)]. Oleh karena itu, dengan mempertimbangkan semua faktor ini yang juga tersedia pada *dataset*, dapat membantu untuk merencanakan penggunaan energi yang lebih efisien dan berkelanjutan dari melihat seberapa besar korelasi pengaruh faktor-faktor tersebut. 

Dalam membuat model regresi ada banyak cara algoritma yang bisa dipilih. Salah satu algoritma yang paling umum digunakan adalah regresi. Dengan menggunakan regresi dan memasukkan faktor-faktor dari rumah yang dituju diharapkan dapat memprediksi harga rumah yang dimaksud [[6](https://j-ptiik.ub.ac.id/index.php/j-ptiik/article/download/2403/897/17458)] [[7](https://journal.eng.unila.ac.id/index.php/jitet/article/download/237/228)] [[8](https://ejournal.itn.ac.id/index.php/jati/article/download/8083/4796/)] [[9](https://ejurnal.its.ac.id/index.php/teknik/article/view/92329)] [[10](https://elektroda.uho.ac.id/index.php/journal/article/download/95/37)] [[11](https://jom.untidar.ac.id/index.php/dinamic/article/download/1428/669)].

## Business Understanding

Prediksi konsumsi energi menjadi proses penting dalam berbagai industri dan sektor, termasuk manufaktur, transportasi, dan bangunan. 
Dalam hal ini pola konsumsi energi membantu untuk merencanakan penggunaan energi yang efisien, mengoptimalkan biaya operasional, dan mengurangi dampak lingkungan.

### Problem Statements
- Berdasarkan eksplorasi *dataset*, fitur apa saja yang mempengaruhi dalam menentukan prediksi konsumsi energi?
- Bagaimana mengolah *dataset* agar dapat dibuat model prediksi konsumsi energi?
- Bagaimanna cara meningkatkan nilai perfoma model prediksi konsumsi energi
  
### Goals
- Mengeksplorasi semua fitur yang tersedia pada *dataset* kemudian membuat melihat korelasi konsumsi dari semua fitur yang sedia untuk melihat faktor apa saja yang paling berpengaruh sampai paling kurang berpengaruh terhadap konsumsi energi
- Melakukan proses *data wragling* dan *data preparation* terhadap *dataset* agar dapat dibuat model predksi konsumsi energi
- Melakukan beberapa variasi model untuk mendapatkan model yang paling baik dari beberapa model yang telah dibuat untuk prediksi konsumsi energi

### Solution statements
- Untuk eksplorasi fitur dilakukan Analisis Univariat dan Analisis Multivariat. Analisis Univariat dilakukan untuk mengeksploasi data numerik dan data kategorik. Analisis Multivariat dilakukan untuk melihat hubungan antar fitur. Teknik yang digunakan adalah menggunakan catplot, pairplot, dan heatmap untuk melihat *Correlation Matrix* dari fitur-fitur yang dimiliki.
- Agar didapatkan model prediksi yang baik maka dilakukan proses *Data Wragling* yang meliputi *Data Gathering*, *Data Assessing*, dan *Data Cleaning*.
- Untuk mengetahui perfoma model dilakukan pengecekan performa dengan metrik evaluasi.

## Data Understanding
Data yang digunakan dalam pembuatan model merupakan data sekunder. Data diambil dari Kaggle dengan nama *dataset* yaitu *Energy-consumption-prediction*. 

URL: https://www.kaggle.com/datasets/mrsimple07/energy-consumption-prediction/data 

Berikut merupakan detail dari *dataset* yang digunakan untuk pembuatan model:
- Dataset berupa CSV
- Dataset terdiri dari 1001 *records* dengan 11 buah fitur yang diukur.
- Dataset terdiri dari 4 data kategori dan 7 data numerik.
- Dataset memiliki *missing value* sejumlah 0 records

### Variabel-variabel pada *dataset* adalah sebagai berikut:
- Temperature : Suhu udara di lingkungan digunakan untuk memengaruhi kebutuhan pemanasan atau pendinginan, yang pada gilirannya mempengaruhi konsumsi energi HVAC (diukur dalam satuan angka)
- Humidity : Kadar kelembaban udara, merupakan persentase dari kandungan uap air di udara. Berpengaruh pada kenyamanan termal dan kualitas udara dalam ruangan. (dalam satuan kelembaban)
- Square Foot age : Luas area bangunan atau ruangan, digunakan untuk menentukan ukuran ruangan yang mempengaruhi kebutuhan energi untuk pemanasan, pendinginan, dan pencahayaan (dalam satuan luas)
- Occupancy : Jumlah orang yang hadir atau menggunakan bangunan pada waktu tertentu digunakan untuk menggambarkan beban internal yang mempengaruhi suhu dan kebutuhan ventilasi (dalam satuan orang)
- HVAC Usage : Penggunaan sistem HVAC (Heating, Ventilation, and Air Conditioning), mengindikasikan seberapa sering sistem tersebut digunakan digunakan untuk menunjukkan tingkat penggunaan energi untuk pendinginan atau pemanasan ruangan (berupa kategori 'On', 'Off')
- Lighting Usage : Penggunaan pencahayaan di dalam bangunan, dapat diukur dalam waktu penggunaan atau intensitas cahaya yang digunakan untuk memengaruhi konsumsi energi untuk pencahayaan ruangan (berupa kategori 'On', 'Off')
- Renewable Energy : Energi yang dihasilkan dari sumber-sumber yang dapat diperbaharui, seperti tenaga surya atau angin digunakan untuk memberikan alternatif energi yang ramah lingkungan dan dapat mengurangi konsumsi energi dari sumber-sumber konvensional (dalam satuan energi)
- Day Of Week : Hari dalam seminggu, dimulai dari Minggu hingga Sabtu (Pola konsumsi energi dapat bervariasi berdasarkan hari dalam seminggu berupa kategori 'Senin', 'Selasa', 'Rabu', 'Kamis', 'Jumat', 'Sabtu', 'Minggu')
- Holiday : Hari libur atau hari khusus di mana aktivitas mungkin berbeda dari hari biasa digunakan untuk memengaruhi pola konsumsi energi karena perubahan dalam aktivitas dan kehadiran (berupa kategori 'Yes', 'No')
- EnergyConsumption : Jumlah energi yang dikonsumsi oleh bangunan atau sistem pada waktu tertentu, yang digunakan untuk interaksi antara faktor-faktor di atas yang dapat diprediksi untuk perencanaan energi yang lebih efisien (dalam satuan energi)

Untuk memahami data lebih lanjut, dilakukan Analisis Univariat dan Analisis Multivariat, serta Visualisasi Data.

Analisis Univariat merupakan bentuk analisis data yang hanya merepresentasikan informasi yang terdapat pada satu variabel.  Jenis visualisasi ini umumnya digunakan untuk memberikan gambaran terkait distribusi sebuah variabel dalam suatu *dataset*. Sedangkan, Analisis Multivariat tmerupakan jenis analisis data yang terdapat dalam lebih dari dua variabel. Jenis visualisasi ini digunakan untuk merepresentasikan hubungan dan pola yang terdapat dalam multidimensional data. 

Selain melalui analisis, dilakukan juga Visualisasi Data. Memvisualisasikan data memberikan wawasan mendalam tentang perilaku berbagai fitur-fitur yang tersedia dalam *dataset*. 

Teknik visualisasi yang digunakan pada pembuatan model proyek ini adalah dengan menggunakan catplot yang digunakan untuk memplot distribusi data pada data kategori, pairplot yang digunakan untuk melakukan hubungan antar fitur dalam *dataset*, dan heatmap yang menampilkan korelasi antar fitur yang ada dalam *dataset* dalam bentuk matriks.

Berikut adalah hasil Exploratory Data Analysis (EDA), dimana Gambar 1 merupakan EDA Analisis Univariat dan Gambar 2 merupakan EDA Analisis Multivariat.

(![image](https://github.com/Fadila13/Machine-Learning/assets/162153177/856c40e4-5060-401d-ae66-ba29d9cdf3d5)) ![image](https://github.com/Fadila13/Machine-Learning/assets/162153177/951fb27a-0c5c-462e-92e4-e563f3890f20) ![image](https://github.com/Fadila13/Machine-Learning/assets/162153177/7fde54b5-54d5-4eb5-8b57-46de1a256d19) ![image](https://github.com/Fadila13/Machine-Learning/assets/162153177/246b0a18-b0ca-4b4f-838d-807fd190608e)

Gambar 1a. Analisis Univariat (Data Kategori)

![image](https://github.com/Fadila13/Machine-Learning/assets/162153177/beed0b8b-526e-4bc0-b43d-3aa65e268e3c)

Gambar 1b. Analisis Univariat (Data Numerik)

Berdasarkan Gambar 1a , dapat dilihat bahwa distribusi data kategori untuk 'ocean_proximity' memiliki perbandingan jumlah yang tidak sama, untuk nilai data '<1H OCEAN' berjumlah 7607 dengan persentase 43.2% sedangkan nilai data 'ISLAND' hanya berjumlah 5. Lebih jauh, pada Gambar 1b, untuk data numerik memiliki karakteristik, yaitu:
- koordinat longitude rumah mayoritas berada pada -118 derajat dan -122 derajat dan koordinat latitude rumah mayoritas berada pada 34 derajat dan 38 derajat
- median dari umur rumah banyak terdistribusi pada rentang umur 10 - 40, namun nilai terbanyak terdapat pada nilai 50.
- rata-rata terbanyak untuk data total room dan total bedroom yaitu di antara angka 1000-2000 room dan 200-400 bedroom.
- rata-rata terbanyak untuk data population dan households berada di antara angka 500-1000 dan 200-400.
- median income dan median house value terbanyak masing-masing berada di antara angka 3 dan 200000.
- distribusi median house value miring ke kanan (right-skewed). Hal ini akan berimplikasi pada model.

![image](https://github.com/Fadila13/Machine-Learning/assets/162153177/e2c70522-5e6f-46a5-a63b-3ca3b90b967a)

Gambar 2a. Analisis Multivariat (Data Kategori)

![image](https://github.com/Fadila13/Machine-Learning/assets/162153177/044c7fc9-e3a4-4811-a57f-a9099b4d5710)

Gambar 2b. Analisis Multivariat (Data Numerik)

![image](https://github.com/Fadila13/Machine-Learning/assets/162153177/81620a32-7f69-4409-8d9f-b60691ad6f10)

Gambar 2c. Analisis Multivariat (Correlation Matrix)

Pada Gambar 2a tampak persebaran data 'ocean proximity' terhadap 'median house value'. Dengan mengamati rata-rata 'median_house_value' relatif terhadap fitur kategori di atas, diperoleh insight sebagai berikut:
- Pada fitur 'ocean_proximity', rata-rata 'median_house_value' cenderung bervariasi. Rentangnya berada antara 120000 hingga 400000.
- Nilai 'median_house_value' tertinggi berada pada nilai 'ocean_proximity' yaitu 'ISLAND' dan nilai 'median_house_value' terendah berada pada nilai 'ocean_proximity' yaitu 'INLAND'. Sehingga, fitur 'ocean_proximity' memiliki pengaruh yang signifikan terhadap rata-rata 'median_house_value'.
- Kesimpulan akhir, fitur kategori memiliki pengaruh terhadap fitur numerik 'median_house_value'.

Pada Gambar 2b, dengan menggunakan fungsi pairplot dari library seaborn, tampak terlihat relasi pasangan dalam dataset. Dari gambar, terlihat plot relasi masing-masing fitur numerik pada dataset. Pada pola sebaran data grafik pairplot, terlihat bahwa 'median_income' memiliki korelasi dengan fitur 'median_house_value'. Sedangkan kedua fitur lainnya terlihat memiliki korelasi yang lemah karena sebarannya tidak membentuk pola

Terakhir, Gambar 2c merupakan Correlation Matrix menunjukkan hubungan antar fitur dalam nilai korelasi. Jika diamati, fitur 'median_income' memiliki skor korelasi yang cukup besar (0.63) dengan fitur target 'median_house_value'. Artinya, fitur 'median_house_value' berkorelasi cukup tinggi dengan keempat fitur tersebut. Sementara itu, fitur lainnya memiliki korelasi negatif sehingga fitur tersebut dapat dieliminasi.
  
## Data Preparation
Pada proses *Data Preparation* dilakukan kegiatan seperti *Data Gathering*, *Data Assessing*, dan *Data Cleaning*.
Pada proses *Data Gathering*, data diimpor sedemikian rupa agar bisa dibaca dengan baik menggunakan *datafram*e Pandas.
Untuk proses *Data Assessing*, berikut adalah beberapa pengecekan yang dilakukan:
- Duplicate data (data yang serupa dengan data lainnya)
- Missing value (data atau informasi yang "hilang" atau tidak tersedia)
- Outlier (data yang menyimpang dari rata-rata sekumpulan data yang ada)
 
Pada proses *Data Cleaning*, secara garis besar, terdapat tiga metode yang dapat digunakan antara lain seperti berikut:
- Dropping (metode yang dilakukan dengan cara menghapus sejumlah baris data)
- Imputation (metode yang dilakukan dengan cara mengganti nilai yang "hilang" atau tidak tersedia dengan nilai tertentu yang bisa berupa median atau mean dari data)
- Interpolation (metode menghasilkan titik-titik data baru dalam suatu jangkauan dari suatu data)

Pada kasus proyek ini tidak ditemukan data duplikat. Pada proyek ini ditemukan *Missing Value*. Adapaun metode yang digunakan untuk mengatasi hal ini adalah dengan menerapkan *imputation* dimana data yang *missing* diganti dengan nilai *mean*. Untuk *outlier* sendiri dilakukan metode *dropping* menggunakan metode IQR. IQR sendiri didapatkan dengan cara mengurangi Q3 dengan Q1 sebagaimana rumusan berikut. 

$$ IQR = Q<sub>3</sub> - Q<sub>1</sub> $$

dimana

Q<sub>1</sub> adalah kuartil pertama dan Q<sub>3</sub> adalah kuartil ketiga.

Dengan menggunakan metode IQR, dapat ditentukan *outlier* melalui suatu nilai batas yang ditentukan. Setelah menggunakan metode IQR dimana *dataset* yang sebelumnya berjumlah 20640 menjadi 17609.
 
Semua proses ini diperlukan dalam rangka membuat model yang baik. 
Untuk mereduksi jumlah fitur dilakukan proses PCA. Teknik reduksi ini adalah prosedur yang mengurangi jumlah fitur dengan tetap mempertahankan informasi pada data. PCA ini adalah teknik untuk mereduksi dimensi, mengekstraksi fitur, dan mentransformasi data dari “n-dimensional space” ke dalam sistem berkoordinat baru dengan dimensi m, di mana m lebih kecil dari n. Pada proyek ini, fitu 'housing_median_age',	'total_rooms',	'total_bedrooms',	'households' divisualisasikan untuk melihat hubungan di antara fitur-fitur tersebut. sperti yang terlihat pada Gambar 3 berikut.

![image](https://github.com/Fadila13/Machine-Learning/assets/162153177/d30e85da-cb2b-478e-8d4a-86ab6bb06221)

Gambar 3 Visualisasi Hubungan antar Fitur sebelum Reduksi PCA

Berdasarkan Gambar 3 dapat diketahui yang memiliki hubungan antar fitur hanya tiga yaitu 'total_rooms',	'total_bedrooms',	'households'. Selanjutnya, 3 fitur ini dapat direduksi dengan PCA. Sebelum itu, cek proporsi informasi dari ketiga komponen PCs tadi.

```
pca.explained_variance_ratio_.round(3)
```

Potongan kode tersebut memberikan keluaran berupa array([0.985, 0.014, 0.001]). Berdasarkan hasil ini, yang dipertahankan adalah PC (komponen) pertama saja karena dari output yang dideroleh diketahui bahwa 98.5% informasi pada ketiga fitur 'total_rooms',	'total_bedrooms',	'households' terdapat pada PC pertama. Sedangkan sisanya, sebesar 1.4% dan 0.1% terdapat pada PC kedua dan ketiga. PC pertama ini akan menjadi fitur 'house properties' menggantikan ketiga fitur lainnya ('total_rooms',	'total_bedrooms',	'households').

Setelah data dibersihkan, *dataset* dibagi menjadi data train dan data test untuk proses *Modeling*, dimana rasio pembagian data yang dipilih adalah 90:10 mengingat data test untuk rasio tersebut sudah terbilang cukup. 
Adapun detail dari *dataset* tersebut adalah:
- Total sampel di dalam *dataset* train: 15848
- Total sampel di dalam *dataset* test: 1761

## Modeling
Seperti yang dijelaskan di awal, model yang dipilih adalah model regresi karena merupakan salah satu algoritma yang paling umum digunakan dalam pembuatan model prediksi. Dalam bentuk yang sederhana, regresi terdiri dari intersep dan slope yang dituliskan dalam rumusan berikut

$$ y = a + bX $$

dimana: 
- y adalah variabel kriterium (variabel terikat yang digunakan untuk memprediksi)
- a adalah intersep (variabel konstan yang memiliki arti sebagai titik perpotongan suatu garis dengan sumbu Y),
- b adalah slope (nilai koefisien yang menyatakan ukuran kemiringan suatu garis), dan
- X adalah variabel prediktor (variabel yang digunakan untuk memprediksi atau menjelaskan variabel lain dalam suatu model)

Secara umum, regresi ini itu sendiri digunakan untuk meramalkan pengaruh variabel prediktor terhadap variabel kriterium atau membuktikan ada atau tidaknya hubungan fungsional antara variabel bebas (X) dengan variabel terikat (y).

Namun begitu terdapat kelebihan dan kekurangan dari model regresi, yaitu:
Kelebihan regresi:
- Kemudahan untuk digunakan
- Kekuatan Prediktor dalam mengidentifikasi sekuat apa pengaruh yang diberikan oleh variabel prediktor (variabel independen) terhadap variabel lainnya (variabel dependen).
- Dapat memprediksi nilai/tren di masa yang mendatang

Kelemahan dari model regresi adalah karena hasil ramalan dari analisis regresi merupakan nilai estimasi sehingga kemungkinan untuk tidak sesuai dengan data aktual tetaplah ada.

Pada proyek yang dikerjakan, algoritma regresi yang coba dibandingkan adalah regresi linear, regresi ridge, *random forest regressor*, dan *random forest regressor* dengan hyperparamter tuning. Regresi linear adalah teknik analisis data yang memprediksi nilai data yang tidak diketahui dengan menggunakan nilai data lain yang terkait dan diketahui dimana secara matematis dimodelkan sebagai persamaan linier, regresi ridge merupakan metode estimasi koefisien regresi yang diperoleh melalui penambahan konstanta bias c, dan random forest adalah suatu algoritma yang digunakan pada klasifikasi data dalam jumlah yang besar dimana teknik klasifikasi *random forest* dilakukan melalui penggabungan pohon dengan melakukan training pada sampel data yang dimiliki.

Untuk meningkatkan model, dilakukan *hyperparamter tuning*. Adapun paramater yang di-tuning antara lain n_estimators', 'max_depth', 'min_samples_split', dan 'min_samples_leaf. Untuk memudahkan proses *tuning* digunakan GridSearchCV. GridSearchCV itu sendiri merupakan bagian dari modul scikit-learn yang dapat digunakan untuk mendapatkan nilai *hyperparameter* secara otomatis. Grid Search adalah metode yang digunakan untuk mencari parameter yang paling tepat untuk meningkatkan performa model dengan mencoba seluruh kombinasi *hyperparameter* yang diberikan.

Berikut adalah nilai parameter *tuning*

```
params = {'n_estimators' : [50,80,100],
          'max_depth' : [3,5,10],
           'min_samples_split':[2,3,4],
            'min_samples_leaf': [2,3,4]}
```

Berdasarkan hasil pengujian, terpilih grid.best_params_ yaitu 

```
{'max_depth': 3,
 'min_samples_leaf': 4,
 'min_samples_split': 2,
 'n_estimators': 80}
```

Parameter dengan nilai inilah yang kemudian dibuat sebagai model.

## Evaluation
Adapun metrik yang sebagai alat ukur perfoma model yang dibuat antara lain **MSE · MAE · R<sup>2</sup>**. 
Berikut merupakan rumus dari masing-masing metrik yang digunakan:
$$ MAE = (1/n) Σ |y<sub>i</sub> - ŷ<sub>i</sub>| $$
$$ MSE = (1/n) Σ (y<sub>i</sub> - ŷ<sub>i</sub>)<sup>2</sup> $$
$$ R<sup>2</sup> = 1 - (MSE / Var(y)) $$
y<sub>i</sub> mewakili nilai yang diamati,
ŷ<sub>i</sub> mewakili nilai prediksi,
n adalah jumlah titik data,
Var(y) mewakili varians dari nilai yang diamati.

Berikut merupakan penjelasan kegunaan dari masing-masing metrik yang digunakan:
- MAE menghitung rata-rata dari selisih absolut antara nilai prediksi dan nilai aktual. Semakin kecil nilai MAE, semakin baik kualitas model tersebut.
- MSE menghitung rata-rata dari selisih kuadrat antara nilai prediksi dan nilai aktual. Semakin kecil nilai MSE, semakin baik kualitas model tersebut.
- R<sup>2</sup> digunakan untuk menilai seberapa besar pengaruh variabel independen tertentu terhadap variabel dependen
Tabel 1 berikut merupakan perbandingan 4 buah model yang coba dibandingkan
	train	test
	train	test
|     |Model 1|Model 2|Model 3|Model 4|
|---|---|---|---|---|
|R<sup>2</sup>|-5.866891890416883e+30|-5.854037463450065e+30|-10.86085432086093|-1.9107220495762078|
|MSE|6.240873331968297e+30|6.234032670639091e+30|8873589032742468.0|4395838143451591.0|
|MAE|5.60355812900379e+30|5.597412179979567e+30|7729832889370363.0|3368259107818206.0|

Tabel 1. Perbandingan Performa MAE, MSE, dan R<sup>2</sup> Model

Berdasarkan Tabel 1, secara umum Model 3 (RF1) dan Model 4 (RF2) menampilkan hasil performa yang lebih baik dimana masing-masing memiliki nilai R^2 yaitu sebesar -1.880080745581838 dan -2.432728538383974.

Secara lebih jauh perbandingan Model 1, 2, 3, dan 4 bisa dilihat pada Gambar 4 berikut.

![image](https://github.com/Fadila13/Machine-Learning/assets/162153177/709426d1-13db-4cd9-bcff-b38391698855)

Gambar 4. Perbandingan Model berdasarkan Nilai Error (dalam 1e6)

Berdasarkan Gambar 4 dapat terlihat bahwa nilai error train dan test dari Model 3 (RF1) dan Model 4 (RF2) jauh lebih baik dibandingkan model lainnya.

Selain itu dilakukan perbandingan nilai y_true terhadap nilai prediksi harga rumah dari 4 buah model yang dibuat. Tabel 2 berikut merupakan hasil dari evaluasi model yang telah dibuat.

|     |y_true|prediksi_LR|prediksi_RR|prediksi_RF1|prediksi_RF2|
|---|---|---|---|---|---|
|131|7.142759e+14|7.633840e+15|7.633540e+15|4.995583e+15|5.906515e+15|

Tabel 2. Perbandingan Model

Berdasarkan hasil evaluasi, terlihat bahwa prediksi harga rumah dengan *Random Forest* (RF), baik RF1 (tanpa tuning) ataupun RF2 (dengan tuning) memberikan hasil yang paling mendekati y_true, dimana nilai y_true yaitu 341700 dan nilai RF1 dan RF2 masing-masing yaitu 347466.0 dan 315645.2. Dengan demikian bisa disimpulkan bahwa model yang telah dikembangkan dapat memprediksi harga rumah dengan baik dengan menggunakan *Random Forest Regressor*.

## Referensi:
[1] Hassan, Mohammad Mujaheed & Ahmad, Nobaya & Hariza, Ahmad & Hashim, Ahmad. (2021). Factors Influencing Housing Purchase Decision. 11. 429-443. 10.6007/IJARBSS/v11-i7/10295.
[2] Ariyawansa, Ranthilaka. (2009). Housing Market: A Review of Purchase Decision of Potential Buyers.
[3] Jiang, Jiaxin & Zhang, Jin. (2021). Analysis of County Consumers’ Housing Purchase Intention and Influencing Factors. 
[4] Heymann, Sommervoll. (2019). House prices and relative location
[5] Jayasekare, Ajith & Herath, Shanaka & Wickramasuriya, Rohan & Perez, Pascal. (2019). The price of a view: Estimating the impact of view on house prices. Pacific Rim Property Research Journal. 25. 1-18. 10.1080/14445921.2019.1626543. 
[6] Agarwal, Umang & Gupta, Smriti & Goyal, Madhav. (2022). House Price Prediction using Linear Regression. 10.13140/RG.2.2.11175.62887. 
[7] Li, Xinshu. (2022). Prediction and Analysis of Housing Price Based on the Generalized Linear Regression Model. Computational Intelligence and Neuroscience. 2022. 1-9. 10.1155/2022/3590224. 
[8] Zietz, Joachim & Zietz, Emily & Sirmans, G.. (2008). Determinants of House Prices: A Quantile Regression Approach. The Journal of Real Estate Finance and Economics. 37. 317-333. 10.1007/s11146-007-9053-7. 
