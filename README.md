# Laporan Proyek Machine Learning - Prediksi Konsumsi Energi

## Domain Proyek

Konsumsi energi adalah jumlah energi yang digunakan oleh individu, rumah tangga, industri, atau negara untuk memenuhi suatu kebutuhan dalam melakukan berbagai aktivitas. Pertumbuhan konsumsi energi sering kali dikaitkan dengan pertumbuhan ekonomi, urbanisasi, dan perkembangan teknologi, tetapi juga berdampak pada lingkungan melalui emisi gas rumah kaca dan penggunaan sumber daya alam yang tidak terbarukan. Konsumsi energi sangat penting untuk merencanakan agar penggunaan sumber daya dapat dipakai secara efisien dan berkelanjutan. Selain itu, memperkirakan konsumsi energi juga membantu mengurangi dampak negatif terhadap lingkungan dengan mengurangi emisi gas rumah kaca dan meminimalkan eksploitasi sumber daya alam yang tidak terbarukan.  [[1](https://ideas.repec.org/a/eee/energy/v32y2007i9p1761-1768.html)] [[2](https://www.sciencedirect.com/science/article/abs/pii/S0957582021004663)]. Kemampuan memprediksi konsumsi tentunya membantu sekali dalam rangka penghematan energi untuk tetap menjaga bumi.  

Prediksi konsumsi energi yang memperhitungkan berbagai faktor seperti suhu, kelembaban udara, luas bangunan, penggunaan HVAC dan pencahayaan, sangat penting untuk mengoptimalkan penggunaan energi secara efisien [[3](https://jurnal.untan.ac.id/index.php/Elkha/article/download/3002/2961)] [[4](https://www.sciencedirect.com/science/article/pii/S1674927814500135))]. Selain itu, faktor-faktor seperti tingkat hunian, penggunaan energi terbarukan, hari dalam seminggu, dan hari libur juga berkontribusi pada fluktuasi dalam konsumsi energi [[5](https://publication.petra.ac.id/index.php/acesa/article/download/13450/11654)] [[6](https://scholarhub.ui.ac.id/cgi/viewcontent.cgi?article=1301&context=jepi)]. Oleh karena itu, dengan mempertimbangkan semua faktor ini yang juga tersedia pada *dataset*, dapat membantu untuk merencanakan penggunaan energi yang lebih efisien dan berkelanjutan dari melihat seberapa besar korelasi pengaruh faktor-faktor tersebut. 

Dalam membuat model regresi ada banyak cara algoritma yang bisa dipilih. Salah satu algoritma yang paling umum digunakan adalah regresi. Dengan menggunakan regresi dan memasukkan faktor-faktor dari rumah yang dituju diharapkan dapat memprediksi harga rumah yang dimaksud [[7](https://j-ptiik.ub.ac.id/index.php/j-ptiik/article/download/2403/897/17458)] [[8](https://journal.eng.unila.ac.id/index.php/jitet/article/download/237/228)] [[9](https://ejournal.itn.ac.id/index.php/jati/article/download/8083/4796/)] [[10](https://ejurnal.its.ac.id/index.php/teknik/article/view/92329)] [[11](https://elektroda.uho.ac.id/index.php/journal/article/download/95/37)] [[12](https://jom.untidar.ac.id/index.php/dinamic/article/download/1428/669)].

## Business Understanding

Prediksi konsumsi energi menjadi proses penting dalam berbagai industri dan sektor, termasuk manufaktur, transportasi, dan bangunan. 
Dalam hal ini pola konsumsi energi membantu untuk merencanakan penggunaan energi yang efisien, mengoptimalkan biaya operasional, dan mengurangi dampak lingkungan.

### Problem Statements
- Berdasarkan eksplorasi *dataset*, fitur apa saja yang mempengaruhi dalam menentukan prediksi konsumsi energi?
- Bagaimana mengolah *dataset* agar dapat dibuat model prediksi konsumsi energi?
- Bagaimanna cara meningkatkan nilai perfoma model prediksi konsumsi energi
  
### Goals
- Mengeksplorasi semua fitur yang tersedia pada *dataset* kemudian membuat melihat korelasi energi dari semua fitur yang sedia untuk melihat faktor apa saja yang paling berpengaruh sampai paling kurang berpengaruh terhadap konsumsi energi
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
- Dataset terdiri dari 1000 *records* dengan 10 buah fitur yang diukur.
- Dataset terdiri dari 4 data kategori dan 6 data numerik.
- Dataset memiliki *missing value* sejumlah 0 records

### Variabel-variabel pada *dataset* adalah sebagai berikut:
- Temperature : Suhu udara di lingkungan digunakan untuk memengaruhi kebutuhan pemanasan atau pendinginan, yang pada gilirannya mempengaruhi konsumsi energi (diukur dalam satuan serajat celcius)
- Humidity : Kadar kelembaban udara, merupakan persentase dari kandungan uap air di udara. Berpengaruh pada kenyamanan termal dan kualitas udara dalam ruangan. (diukur dalam persentase)
- Square Foot age : Luas area bangunan atau ruangan, digunakan untuk menentukan ukuran ruangan yang mempengaruhi kebutuhan energi untuk pemanasan, pendinginan, dan pencahayaan (dalam satuan luas persegi)
- Occupancy : Jumlah orang yang hadir atau menggunakan bangunan pada waktu tertentu digunakan untuk menggambarkan beban internal yang mempengaruhi suhu dan kebutuhan ventilasi (dalam satuan orang)
- HVAC Usage : Penggunaan sistem HVAC (Heating, Ventilation, and Air Conditioning), mengindikasikan seberapa sering sistem tersebut digunakan digunakan untuk menunjukkan tingkat penggunaan energi untuk pendinginan atau pemanasan ruangan (berupa kategori 'On', 'Off')
- Lighting Usage : Penggunaan pencahayaan di dalam bangunan, dapat diukur dalam waktu penggunaan atau intensitas cahaya yang digunakan untuk memengaruhi konsumsi energi untuk pencahayaan ruangan (berupa kategori 'On', 'Off')
- Renewable Energy : Energi yang dihasilkan dari sumber-sumber yang dapat diperbaharui, seperti tenaga surya atau angin digunakan untuk memberikan alternatif energi yang ramah lingkungan dan dapat mengurangi konsumsi energi dari sumber-sumber konvensional (dalam persentase)
- Day Of Week : Hari dalam seminggu, dimulai dari Minggu hingga Sabtu (Pola konsumsi energi dapat bervariasi berdasarkan hari dalam seminggu berupa kategori 'Senin', 'Selasa', 'Rabu', 'Kamis', 'Jumat', 'Sabtu', 'Minggu')
- Holiday : Hari libur atau hari khusus di mana aktivitas mungkin berbeda dari hari biasa digunakan untuk memengaruhi pola konsumsi energi karena perubahan dalam aktivitas dan kehadiran (berupa kategori 'Yes', 'No')
- EnergyConsumption : Jumlah energi yang dikonsumsi oleh bangunan atau sistem pada waktu tertentu, yang digunakan untuk interaksi antara faktor-faktor di atas yang dapat diprediksi untuk perencanaan energi yang lebih efisien (dalam satuan energi)

Untuk memahami data lebih lanjut, dilakukan Analisis Univariat dan Analisis Multivariat, serta Visualisasi Data.

Analisis Univariat merupakan bentuk analisis data yang hanya merepresentasikan informasi yang terdapat pada satu variabel.  Jenis visualisasi ini umumnya digunakan untuk memberikan gambaran terkait distribusi sebuah variabel dalam suatu *dataset*. Sedangkan, Analisis Multivariat merupakan jenis analisis data yang terdapat dalam lebih dari dua variabel. Jenis visualisasi ini digunakan untuk merepresentasikan hubungan dan pola yang terdapat dalam multidimensional data. 

Selain melalui analisis, dilakukan juga Visualisasi Data. Memvisualisasikan data memberikan wawasan mendalam tentang perilaku berbagai fitur-fitur yang tersedia dalam *dataset*. 

Teknik visualisasi yang digunakan pada pembuatan model proyek ini adalah dengan menggunakan catplot yang digunakan untuk memplot distribusi data pada data kategori, pairplot yang digunakan untuk melakukan hubungan antar fitur dalam *dataset*, dan heatmap yang menampilkan korelasi antar fitur yang ada dalam *dataset* dalam bentuk matriks.

Berikut adalah hasil Exploratory Data Analysis (EDA), dimana Gambar 1 merupakan EDA Analisis Univariat dan Gambar 2 merupakan EDA Analisis Multivariat.

(![image](https://github.com/Fadila13/Machine-Learning/assets/162153177/856c40e4-5060-401d-ae66-ba29d9cdf3d5)) ![image](https://github.com/Fadila13/Machine-Learning/assets/162153177/951fb27a-0c5c-462e-92e4-e563f3890f20) ![image](https://github.com/Fadila13/Machine-Learning/assets/162153177/7fde54b5-54d5-4eb5-8b57-46de1a256d19) ![image](https://github.com/Fadila13/Machine-Learning/assets/162153177/246b0a18-b0ca-4b4f-838d-807fd190608e)

Gambar 1a. Analisis Univariat (Data Kategori)

![image](https://github.com/Fadila13/Machine-Learning/assets/162153177/beed0b8b-526e-4bc0-b43d-3aa65e268e3c)

Gambar 1b. Analisis Univariat (Data Numerik)

Berdasarkan Gambar 1a , dapat dilihat bahwa terdapat beberapa distribusi data kategori yaitu:
1. 'HVACusage'
   untuk 'HVACusage' memiliki perbandingan jumlah yang tidak sama, untuk nilai data 'Off' berjumlah 508 dengan persentase 50.8% sedangkan nilai data 'On' hanya berjumlah 492 dengan presentase 49.2%. Namun perbandingan ini juga tidak memiliki selisi yang signifikan. 
2. 'LightingUsage'
  untuk 'LightingUsage' memiliki perbandingan jumlah yang tidak sama, untuk nilai data 'Off' berjumlah 509 dengan persentase 50.9% sedangkan nilai data 'On' hanya berjumlah 491 dengan presentase 49.1%. Namun perbandingan ini juga tidak memiliki selisi yang signifikan.
3. 'DayOfWeek'
  untuk 'DayOfWeek' memiliki perbandingan jumlah yang tidak sama, untuk nilai data 'Friday' berjumlah 164 dengan persentase 16.4% sedangkan nilai data 'Monday' hanya berjumlah 123 dengan presentase 12.3%. Pada bagian ini selisih perbandingan cukup signifikan.
4. 'Holiday'
   untuk 'Holiday' memiliki perbandingan jumlah yang tidak sama, untuk nilai data 'yes' berjumlah 533 dengan persentase 53.3% sedangkan nilai data 'On' hanya berjumlah 467 dengan presentase 46.7%. Pada perbandingan ini juga memiliki selisi yang cukup signifikan.

  Lebih jauh, pada Gambar 1b, untuk data numerik memiliki karakteristik, yaitu:
- Temperatur untuk konsumsi energi mayoritas berada pada 2.5 derajat celcius dan 25 derajat celcius.
- Humidity untuk konsumsi energi mayoritas berada pada 0.4% dan 0.3%
- median dari Renewable Energy banyak terdistribusi pada rentang presentase 0%-3%, namun nilai terbanyak terdapat pada nilai 0.2%.
- rata-rata terbanyak untuk data total SquareFootage yaitu di antara angka 1%-2%.
- rata-rata terbanyak untuk data Occupansi berada di antara angka 6-8 orang
- distribusi EnergyConsumption miring ke kanan (right-skewed). Hal ini akan berimplikasi pada model.

![image](https://github.com/Fadila13/Machine-Learning/assets/162153177/9b5422df-95b1-4762-a975-86f3ce0da66e) ![image](https://github.com/Fadila13/Machine-Learning/assets/162153177/fb01c423-3371-402e-a6d2-bd6e7471fe82) ![image](https://github.com/Fadila13/Machine-Learning/assets/162153177/e2c70522-5e6f-46a5-a63b-3ca3b90b967a) ![image](https://github.com/Fadila13/Machine-Learning/assets/162153177/6d667589-69fa-4276-bc07-e19aaf69d009)

Gambar 2a. Analisis Multivariat (Data Kategori)

 ![image](https://github.com/Fadila13/Machine-Learning/assets/162153177/044c7fc9-e3a4-4811-a57f-a9099b4d5710) 

Gambar 2b. Analisis Multivariat (Data Numerik)

![image](https://github.com/Fadila13/Machine-Learning/assets/162153177/81620a32-7f69-4409-8d9f-b60691ad6f10)

Gambar 2c. Analisis Multivariat (Correlation Matrix)

Pada Gambar 2a tampak persebaran data 'HVACUsage', 'LightingUsage', 'DayOfWeek', dan 'Holiday'  terhadap 'EnergrConsumption'. Dengan mengamati rata-rata 'EnergyConsumption' relatif terhadap fitur kategori di atas, diperoleh insight sebagai berikut:
1. Pada fitur 'HVACUsage'
- Rata-rata 'EnergyConsumption' hanya terdapat 2 bervariasi. Rentangnya berada antara lebih dari 7 hingga kurang dari 8.
- Nilai 'EnergyConsumption' pada nilai 'HVACUsage' cukup setara karena hanya ada dua pilihan yaitu On dan Off dan nilai nya tidak terlihat perbedaannya secara signifikan. Namun, fitur 'HVACUsage' memiliki pengaruh yang signifikan terhadap rata-rata 'EnergyConsumption'.

2. Pada Fitur 'LightingUsage'
- Rata-rata 'EnergyConsumption' hanya terdapat 2 bervariasi. Rentangnya berada antara lebih dari 7 hingga kurang dari 8.
- Nilai 'EnergyConsumption' pada nilai 'LightingUsage' cukup setara karena hanya ada dua pilihan yaitu On dan Off dan nilai nya tidak terlihat perbedaannya secara signifikan. Namun, fitur 'LightingUsage' memiliki pengaruh yang signifikan terhadap rata-rata 'EnergyConsumption'.

3. Pada Fitur 'DayOfWeek'
- Rata-rata 'EnergyConsumption' cukup bervariasi senanyak Jumlah Hari. Rentangnya juga berada antara lebih dari 7 hingga kurang dari 8.
- Nilai 'EnergyConsumption' tertinggi berada pada nilai 'DayOfWeek' yaitu 'Friday' dan nilai 'EnergyConsumption' terendah berada pada nilai 'DayOfWeek' yaitu 'Tuesday'. Sehingga, fitur 'DayOfWeek' juga memiliki pengaruh yang signifikan terhadap rata-rata 'EnergyConsumption'.

4. Pada Fitur 'Holiday'
- Rata-rata 'EnergyConsumption' hanya terdapat 2 bervariasi. Rentangnya berada antara lebih dari 7 hingga kurang dari 8.
- Nilai 'EnergyConsumption' pada nilai 'LightingUsage' cukup setara karena hanya ada dua pilihan yaitu Yes dan No dan nilai nya tidak terlihat perbedaannya secara signifikan. Namun, fitur 'LightingUsage' juga memiliki pengaruh yang signifikan terhadap rata-rata 'EnergyConsumption'.

*Kesimpulan akhir, fitur kategori memiliki pengaruh terhadap 'EnergyConsumption'.*

Pada Gambar 2b, dengan menggunakan fungsi pairplot dari library seaborn, tampak terlihat relasi pasangan dalam dataset. Dari gambar, terlihat plot relasi masing-masing fitur numerik pada dataset. Pada pola sebaran data grafik pairplot sebelumnya, terlihat bahwa 'Temperature', 'Humidity', dan 'SquareFootage' memiliki korelasi dengan fitur 'EnergyConsumption'. Sedangkan kedua fitur lainnya terlihat memiliki korelasi yang lemah karena sebarannya tidak membentuk pola

Terakhir, Gambar 2c merupakan Correlation Matrix menunjukkan hubungan antar fitur dalam nilai korelasi. Jika diamati, fitur 'Occupancy' memiliki skor korelasi yang cukup besar (0.04) dengan fitur target 'EnergyConsumption'. Artinya, fitur 'EnergyConsumption' berkorelasi cukup tinggi dengan kedua fitur tersebut. Sementara itu, fitur lainnya memiliki korelasi negatif sehingga, fitur tersebut dapat di-drop.
  
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
Untuk mereduksi jumlah fitur dilakukan proses PCA. Teknik reduksi ini adalah prosedur yang mengurangi jumlah fitur dengan tetap mempertahankan informasi pada data. PCA ini adalah teknik untuk mereduksi dimensi, mengekstraksi fitur, dan mentransformasi data dari “n-dimensional space” ke dalam sistem berkoordinat baru dengan dimensi m, di mana m lebih kecil dari n. Pada proyek ini, fitur 'Temperature', 'Humidity', 'Occupancy', 'RenewableEnergy' divisualisasikan untuk melihat hubungan di antara fitur-fitur tersebut. sperti yang terlihat pada Gambar 3 berikut.

![image](https://github.com/Fadila13/Machine-Learning/assets/162153177/d30e85da-cb2b-478e-8d4a-86ab6bb06221)

Gambar 3 Visualisasi Hubungan antar Fitur sebelum Reduksi PCA

Berdasarkan Gambar 3 dapat diketahui yang memiliki hubungan antar fitur hanya tiga yaitu  'Temperature', 'Humidity', 'RenewableEnergy'. Selanjutnya, 3 fitur ini dapat direduksi dengan PCA. Sebelum itu, cek proporsi informasi dari ketiga komponen PCs tadi.

```
pca.explained_variance_ratio_.round(3)
```

Potongan kode tersebut memberikan keluaran berupa array([0.602, 0.206, 0.192]). Berdasarkan hasil ini, yang dipertahankan adalah PC (komponen) pertama saja karena dari output yang dideroleh diketahui bahwa 60.2% informasi pada ketiga fitur 'Temperature', 'Humidity', 'RenewableEnergy' terdapat pada PC pertama. Sedangkan sisanya, sebesar 20.6% dan 19.2% terdapat pada PC kedua dan ketiga. PC pertama ini akan menjadi fitur 'energy properties' menggantikan ketiga fitur lainnya ('tTemperature', 'Humidity', 'RenewableEnergy').

Setelah data dibersihkan, *dataset* dibagi menjadi data train dan data test untuk proses *Modeling*, dimana rasio pembagian data yang dipilih adalah 90:10 mengingat data test untuk rasio tersebut sudah terbilang cukup. 
Adapun detail dari *dataset* tersebut adalah:
- Total sampel di dalam *dataset* train: 900
- Total sampel di dalam *dataset* test: 100

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

Berdasarkan Tabel 1, secara umum Model 3 (RF1) dan Model 4 (RF2) menampilkan hasil performa yang lebih baik dimana masing-masing memiliki nilai R^2 yaitu sebesar -1.9107220495762078 dan -10.86085432086093.

Secara lebih jauh perbandingan Model 1, 2, 3, dan 4 bisa dilihat pada Gambar 4 berikut.

![image](https://github.com/Fadila13/Machine-Learning/assets/162153177/709426d1-13db-4cd9-bcff-b38391698855)

Gambar 4. Perbandingan Model berdasarkan Nilai Error (dalam 1e6)

Berdasarkan Gambar 4 dapat terlihat bahwa nilai error train dan test dari Model 3 (RF1) dan Model 4 (RF2) jauh lebih baik dibandingkan model lainnya.

Selain itu dilakukan perbandingan nilai y_true terhadap nilai prediksi harga rumah dari 4 buah model yang dibuat. Tabel 2 berikut merupakan hasil dari evaluasi model yang telah dibuat.

|     |y_true|prediksi_LR|prediksi_RR|prediksi_RF1|prediksi_RF2|
|---|---|---|---|---|---|
|131|7.142759e+14|7.633840e+15|7.633540e+15|4.995583e+15|5.906515e+15|

Tabel 2. Perbandingan Model

Berdasarkan hasil evaluasi, terlihat bahwa prediksi konsumsi energi dengan *Random Forest* (RF), baik RF1 (tanpa tuning) ataupun RF2 (dengan tuning) memberikan hasil yang paling mendekati y_true, dimana nilai y_true yaitu 341700 dan nilai RF1 dan RF2 masing-masing yaitu 347466.0 dan 315645.2. Dengan demikian bisa disimpulkan bahwa model yang telah dikembangkan dapat memprediksi harga rumah dengan baik dengan menggunakan *Random Forest Regressor*.

## Referensi:
[1]	G. K. F. Tso and K. K. W. Yau, “Predicting electricity energy consumption: A comparison of regression analysis, decision tree and neural networks,” Energy, vol. 32, no. 9, pp. 1761–1768, 2007, doi: 10.1016/j.energy.2006.11.010.

[2]	F. Bagherzadeh, A. S. Nouri, M. J. Mehrani, and S. Thennadil, “Prediction of energy consumption and evaluation of affecting factors in a full-scale WWTP using a machine learning approach,” Process Saf. Environ. Prot., vol. 154, pp. 458–466, 2021, doi: 10.1016/j.psep.2021.08.040.

[3]	I. Syahrizal, S. Panjaitan, and Yandri, “Analisis Konsumsi Energi Listrik Pada Sistem Pengkondisian Udara Berdasarkan Variasi Kondisi Ruangan (Studi Kasus Di Politeknik Terpikat Sambas),” J. ELKHA, vol. 5, no. 1, pp. 1–7, 2013.

[4]	Y. L. Hou, H. Z. Mu, G. T. Dong, and J. Shi, “Influences of urban temperature on the electricity consumption of Shanghai,” Adv. Clim. Chang. Res., vol. 5, no. 2, pp. 74–80, 2014, doi: 10.3724/SP.J.1248.2014.074.

[5]	R. D. Setyowati and J. Raharjo, “Pengaruh Karakteristik Konsumsi Energi Terhadap Pencapaian Efisiensi Energi— Studi Kasus Di Perumahan Bulan Terang Utama Malang,” Adv. Civ. Eng. Sustain. Archit., vol. 5, no. 1, pp. 38–55, 2023, doi: 10.9744/acesa.v5i1.13450.

[6]	M. Nazer and H. Handra, “Analisis Konsumsi Energi Rumah Tangga Perkotaan di Indonesia: Periode Tahun 2008 dan 2011,” J. Ekon. dan Pembang. Indones., vol. 16, no. 2, pp. 141–153, 2016, doi: 10.21002/jepi.v16i2.04.

[7]	F. Febrianto, C. Dewi, and B. Rahayudi, “Pemodelan Regresi Linear Untuk Prediksi Konsumsi Energi Primer Indonesia Menggunakan Hybrid Particle Swarm Optimization Dan Continuous Ant Colony Optimization,” J. Pengemb. Teknol. Inf. dan Ilmu Komput. Univ. Brawijaya, vol. 2, no. 9, pp. 2760–2769, 2018.

[8]	M. Syafruddin, L. Hakim, and D. Despa, “Metode Regresi Linier Untuk Prediksi Kebutuhan Energi Listrik Jangka Panjang (Studi Kasus Provinsi Lampung),” J. Inform. dan Tek. Elektro Terap., vol. 2, no. 2, 2014, doi: 10.23960/jitet.v2i2.237.

[9]	T. Maulana, R. Astuti, and F. Muhammad Basysyar, “Implementasi Algoritma Regresi Linear Untuk Memprediksi Pendapatan Pt Pln Berdasarkan Penggunaan Per Kelompok Pelanggan,” JATI (Jurnal Mhs. Tek. Inform., vol. 7, no. 6, pp. 3196–3202, 2024, doi: 10.36040/jati.v7i6.8083.

[10]	T. N. Faza and A. M. Navastara, “Faktor yang Memengaruhi Konsumsi Energi Listrik Rumah Tangga pada Masa Pandemi COVID-19 (Studi Kasus: Rusunawa di Jakarta Timur),” J. Tek. ITS, vol. 11, no. 2, 2022, doi: 10.12962/j23373539.v11i2.92329.

[11]	N. Rahmadani, M. Musaruddin, M. Nadzirin, A. Nur, and H. T. Mokui, “Analisis Prakiraan Kebutuhan Energi Listrik di Kabupaten Kolaka Utara menggunakan Metode Dkl 3 . 2 , Regresi Linear dan Software Leap,” vol. 08, no. 02, pp. 101–109, 2023.

[12]	Y. Afriyanti, H. Sasana, and G. Jalunggono, “Analisis Faktor-Faktor Yang Mempengaruhi Konsumsi Energi Terbarukan Di Indonesia,” Din. Dir. J. Econ., vol. 2, no. 3, pp. 865–884, 2018.
