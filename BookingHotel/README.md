# Hotel Bookings Data
![Deskripsi gambar](https://raw.githubusercontent.com/Pradityaadi/Bigdata/main/hotel.webp)


# "Pendahuluan"
## 1.Pernyataan Masalah
Industri perhotelan merupakan sektor yang sangat dinamis yang bergantung pada tingkat hunian untuk mempertahankan pendapatan yang stabil. ***Namun***, salah satu tantangan terbesar yang dihadapi hotel adalah tingkat pembatalan yang tinggi. Pembatalan ini dapat mengakibatkan kerugian yang signifikan, karena kamar yang telah dibayar di muka dan kemudian dibatalkan **tidak dapat segera diisi ulang**. Oleh karena itu, pemahaman yang lebih baik tentang faktor-faktor yang memengaruhi pembatalan sangatlah penting.

Mengapa harus tertarik dengan hal ini? Karena setiap pembatalan yang terjadi dapat memengaruhi **profitabilitas** hotel. Dengan memahami faktor-faktor yang memengaruhi pembatalan, hotel dapat menerapkan kebijakan ***yang lebih terarah*** untuk mengurangi jumlah pembatalan dan meningkatkan tingkat hunian. Hal ini tidak hanya menguntungkan secara finansial, tetapi juga meningkatkan pengalaman pelanggan.
## 2.Rencana Mengatasi Masalah:
Untuk mengatasi masalah ini, kami berencana menganalisis data pemesanan hotel yang mencakup informasi tentang **status pembatalan, jenis hotel, jumlah tamu, jenis kamar yang dipesan, lama menginap, dan faktor lain seperti negara asal tamu dan jenis pemesanan**. Kami akan menggunakan metode analisis data eksploratif menggunakan **machine learning** untuk memahami pola yang ada, serta khususnya teknik **klasifikasi** untuk memprediksi kemungkinan pembatalan berdasarkan data yang ada.
## 3.Pendekatan/ Teknik Analisis yang Diusulkan:
**Pendekatan yang akan digunakan meliputi beberapa langkah analisis:**

1. **Data Preprocessing:** bertujuan guna membersihkan data yang hilang dan mengubah data kategori menjadi format yang bisa di analisis, seperti encoding untuk variabel kategorikal.

2. **Analisis Deskriptif**: Mengidentifikasi distribusi dan korelasi antar variabel untuk mendapatkan wawasan lebih lanjut tentang data. Misalnya, apakah tamu dari negara tertentu lebih cenderung membatalkan pemesanan atau ada pola pola lainnya.

3. **Model Klasifikasi:** Menggunakan algoritma klasifikasi, seperti XGBoost, Decission tree, dan Random Forest untuk memprediksi apakah pemesanan akan dibatalkan atau tidak berdasarkan atribut-atribut yang ada pada pemesanan. Model ini akan dilatih untuk membedakan pola antara pemesanan yang dibatalkan dan yang tidak dibatalkan.

4. Evaluasi Model: Menggunakan metrik evaluasi seperti akurasi, precision, recall, dan F1-score untuk menilai seberapa baik model dapat memprediksi pembatalan.
## 4.Manfaat Analisis bagi Konsumen:
**Analisis ini akan membantu hotel dalam beberapa cara:**

1. **Pengelolaan Pemesanan:** Dengan prediksi yang lebih akurat tentang kemungkinan pembatalan, pihak hotel dapat merencanakan kapasitas kamar dengan lebih efisien. Serta bisa mengalokasikan lebih banyak kamar untuk pemesanan yang memiliki kemungkinan kecil untuk dibatalkan, serta mengelola kamar cadangan dengan lebih baik.

2. **Strategi Pemasaran dan Kebijakan:** Hotel dapat menyusun kebijakan pemesanan yang lebih fleksibel atau menawarkan insentif bagi pelanggan yang tidak membatalkan pemesanan mereka, seperti diskon atau penawaran khusus.

3. **Kepuasan Pelanggan:** Dengan memahami alasan di balik pembatalan pemesanan, hotel bisa meningkatkan pelayanan dan pengalaman pelanggan. Misalnya, jika pembatalan sering terjadi karena masalah dengan jenis kamar atau fasilitas tertentu, hotel bisa berfokus pada perbaikan tersebut.

# "Data Preparation"
## 1.Sumber data
Data ini berasal dari **Antonio, Almeida, dan Nunes (2019)** yang mana ini merupakan kumpulan data yang mencakup informasi lengkap tentang pemesanan di dua jenis hotel, yaitu **Resort Hotel** dan **City Hotel**. Data ini mencakup berbagai atribut seperti **status pemesanan (dibatalkan, dilanjutkan, atau no-show)**, **lead time (jumlah hari antara pemesanan dilakukan dan tanggal kedatangan)**, **jumlah tamu (dewasa, anak-anak, dan bayi)**, **tingkat harga harian**, **jenis makanan**, **asal negara**, **segmen pasar**, dan **jumlah permintaan khusus**. Data ini tersedia secara publik dan dapat diunduh melalui tautan hotels.csv. Selain itu, pengguna dapat memuat data menggunakan paket R seperti **tidytuesdayR**.

Data ini sangat berguna untuk berbagai analisis seperti prediksi pembatalan pemesanan, segmentasi pelanggan berdasarkan pola pemesanan, dan perencanaan operasional hotel. Misalnya, dengan analisis pola kedatangan tamu, hotel dapat mengoptimalkan alokasi sumber daya seperti staf atau tempat parkir. Dengan tambahan alat analisis seperti tsibble, fable, dan feasts, data ini juga mendukung analisis deret waktu, seperti prediksi musiman pemesanan dan deteksi pola fluktuasi permintaan.
## 2.Informasi data
Periode pengumpulan data berlangsung dari **1 Juli 2015** hingga **31 Agustus 2017** dengan fokus pengambilan data di negara **Portugal**. Hotel Resor (H1) berlokasi di wilayah **Algarve**, sedangkan Hotel Kota (H2) berlokasi di kota **Lisbon**. Dengan kumpulan data yang mencakup **32 variabel** dan total **119.390 raw data**. Dari jumlah tersebut, **40.060 raw data** berasal dari Hotel Resor (H1), sedangkan **79.330 raw data** lainnya berasal dari Hotel Kota (H2). Data ini dikumpulkan secara real time tanpa menyertakan informasi yang dapat mengidentifikasi hotel atau pelanggan tertentu.</br>
* **teks yang dimiringkan*Variabel - Deskripsi**
  
* **hotel** - Jenis hotel: Resort Hotel (H1) atau City Hotel (H2).  
* **is_canceled** - Status pembatalan reservasi, dengan 1 menunjukkan reservasi dibatalkan dan 0 tidak dibatalkan.  
* **lead_time** - Selang waktu dalam hari antara pemesanan diterima hingga tanggal kedatangan.  
* **arrival_date_year** - Tahun kedatangan pelanggan.  
* **arrival_date_month** - Bulan kedatangan pelanggan.  
* **arrival_date_week_number** - Nomor minggu dalam tahun berdasarkan tanggal kedatangan.  
* **arrival_date_day_of_month** - Hari kedatangan dalam satu bulan.  
* **stays_in_weekend_nights** - Total malam yang dipesan atau diinapi pada akhir pekan (Sabtu dan Minggu).  
* **stays_in_week_nights** - Total malam yang dipesan atau diinapi pada hari kerja (Senin hingga Jumat).  
* **adults** - Jumlah tamu dewasa dalam pemesanan.  
* **children** - Jumlah anak-anak dalam pemesanan.  
* **babies** - Jumlah bayi dalam pemesanan.  
* **meal** - Paket makan yang dipesan, seperti Undefined/SC (tanpa paket makan), BB (Bed & Breakfast), HB (Half Board), atau FB (Full Board).  
* **country** - Negara asal pelanggan dalam format ISO 3155–3:2013.  
* **market_segment** - Segmen pasar untuk pemesanan: "TA" (Travel Agents) atau "TO" (Tour Operators).  
* **distribution_channel** - Saluran distribusi untuk pemesanan, seperti "TA" (Travel Agents) atau "TO" (Tour Operators).  
* **is_repeated_guest** - Indikator apakah tamu merupakan pelanggan yang pernah menginap sebelumnya (1) atau tamu baru (0).  
* **previous_cancellations** - Jumlah reservasi sebelumnya yang dibatalkan oleh tamu.  
* **previous_bookings_not_canceled** - Jumlah reservasi sebelumnya yang tidak dibatalkan oleh tamu.  
* **reserved_room_type** - Kode kamar yang dipesan (dianonimkan).  
* **assigned_room_type** - Kode kamar yang diberikan kepada tamu, yang mungkin berbeda dari yang dipesan (dianonimkan).  
* **booking_changes** - Jumlah perubahan yang dilakukan pada pemesanan sebelum check-in atau pembatalan.  
* **deposit_type** - Jenis deposit: No Deposit (tanpa deposit), Non Refund (deposit penuh), atau Refundable (deposit sebagian).  
* **agent** - ID agen perjalanan yang menangani pemesanan (dianonimkan).  
* **company** - ID perusahaan atau lembaga yang mengurus pemesanan atau pembayarannya (dianonimkan).  
* **days_in_waiting_list** - Jumlah hari pemesanan berada dalam daftar tunggu hingga dikonfirmasi.  
* **customer_type** - Jenis pelanggan: Contract (terikat kontrak), Group (terkait grup), Transient (tidak terikat grup atau kontrak), atau Transient-party (terkait dengan pemesanan transient lainnya).  
* **adr** - Tarif rata-rata harian, dihitung dengan membagi total biaya penginapan dengan jumlah malam menginap.  
* **required_car_parking_spaces** - Jumlah tempat parkir mobil yang diminta oleh pelanggan.  
* **total_of_special_requests** - Jumlah permintaan khusus dari pelanggan, seperti tempat tidur twin atau kamar di lantai atas.  
* **reservation_status** - Status reservasi, seperti Canceled (dibatalkan), Check-Out (tamu telah check-out), atau No-Show (tamu tidak hadir).  
* **reservation_status_date** - Tanggal saat status reservasi terakhir kali diperbarui.

## Alur
![Deskripsi gambar](https://raw.githubusercontent.com/Pradityaadi/Bigdata/main/Screenshot%202025-01-05%20125914.png)
## 3.Pre Processing
### 3.1 Cek Missing Value
Bagi kami, mempertahankan kolom dengan nilai null dengan menanganinya memberi  lebih banyak fleksibilitas dan informasi yang berguna untuk analisis. Kami bisa menangani nilai null dengan cara yang lebih cerdas, seperti mengimputasi atau mengganti nilai tersebut dengan label tertentu, dan ini memungkinkan kami untuk terus menggunakan kolom tersebut tanpa kehilangan informasi yang penting. Menghapusnya tanpa pertimbangan bisa mengurangi kualitas dan kedalaman analisis.
### 3.2 Encoding fitur
Fitur kategorikal perlu di-encoding agar model machine learning dapat memprosesnya dengan baik. Tanpa encoding, algoritma tidak dapat memahami data kategorikal dalam bentuk string, yang menghalangi kemampuan model untuk melakukan perhitungan dan analisis yang diperlukan. Encoding mengubah data kategorikal menjadi format numerik yang dapat digunakan oleh model, memungkinkan penghitungan jarak antar data dan mencegah model salah menginterpretasikan urutan atau perbandingan antar kategori. Selain itu, encoding juga dapat meningkatkan akurasi model dan mengurangi bias dalam analisis, sehingga model dapat memanfaatkan informasi dari fitur kategorikal secara maksimal.
## 4.Rangkuman Data
Dalam proses pengolahan data, langkah-langkah penanganan missing value dan encoding fitur kategorikal merupakan dua komponen penting yang harus dilakukan untuk memastikan kualitas dan kesiapan data sebelum diterapkan pada model machine learning.

**Penanganan Missing Value:**
Missing value atau nilai yang hilang dalam suatu dataset dapat menyebabkan distorsi atau ketidakakuratan dalam model yang akan dibangun, terutama jika model tidak dapat menangani nilai yang hilang dengan baik. Oleh karena itu, penanganan missing value sangat penting untuk menjaga kualitas data yang digunakan. Pada dataset ini, beberapa kolom memiliki nilai yang hilang, seperti `children`, `country`, `agent`, dan `company`. Penanganan missing value dilakukan dengan pendekatan yang sesuai dengan karakteristik masing-masing kolom:
- Kolom `children`: Nilai yang hilang pada kolom ini diinterpretasikan sebagai tidak adanya anak dalam reservasi, yang berarti jika tidak ada informasi yang diberikan, maka dapat diasumsikan bahwa jumlah anak adalah nol.
- Kolom `country`: Missing value pada kolom ini diasumsikan terjadi karena negara asal pelanggan tidak dicatat dalam sistem, kemungkinan besar pada reservasi yang dilakukan tanpa proses formal yang mencatat lokasi secara lengkap.
- Kolom `agent` dan `company`: Missing value pada kolom ini diartikan bahwa pemesanan tidak melibatkan agen perjalanan atau perusahaan yang tercatat, sehingga pemesanan bersifat independen.

Dengan pendekatan kali ini, nilai yang hilang tidak dihapus, melainkan diinterpretasikan dan ditangani secara strategis untuk mempertahankan informasi yang berguna dan mengurangi potensi bias dalam analisis atau prediksi yang dilakukan menggunakan model machine learning.

**Encoding Fitur Kategorikal:**
Fitur kategorikal dalam dataset, seperti `hotel`, `meal`, `country`, dan beberapa kolom lainnya, berisi informasi dalam bentuk teks yang tidak dapat langsung digunakan oleh sebagian besar algoritma machine learning. Oleh karena itu, diperlukan teknik encoding untuk mengubah data kategorikal menjadi bentuk numerik yang dapat diproses oleh model. Dalam kasus ini, `LabelEncoder` digunakan untuk mengubah nilai-nilai kategorikal menjadi nilai numerik, dengan memberikan representasi angka pada masing-masing kategori dalam kolom tersebut. Misalnya, kolom `hotel` yang memiliki dua kategori yaitu "Resort Hotel" dan "City Hotel", diubah menjadi angka yang mewakili masing-masing kategori.

Penerapan encoding ini memungkinkan model untuk mengenali hubungan antar kategori dan memanfaatkan informasi tersebut dalam proses pembelajaran, mengurangi potensi kesalahan interpretasi yang terjadi jika data dibiarkan dalam bentuk string. Dengan demikian, encoding fitur kategorikal merupakan langkah yang esensial untuk mempersiapkan data dalam format yang sesuai dengan input model machine learning, memastikan bahwa data dapat dianalisis dengan tepat dan efisien.

**Kesimpulan:**
Secara keseluruhan, penanganan missing value dan encoding fitur kategorikal merupakan langkah-langkah pra-pemrosesan data yang bertujuan untuk meningkatkan kualitas data dan memastikan bahwa dataset siap untuk digunakan dalam model machine learning. Dengan menangani missing value secara tepat dan menerapkan encoding pada fitur kategorikal, dapat meminimalkan risiko bias, meningkatkan efisiensi analisis, dan memastikan bahwa model machine learning dapat berfungsi dengan baik menggunakan data yang telah dipersiapkan secara optimal.

# "Eksplorasi dan analisa data"
**Pembatalan**
![Deskripsi gambar](https://raw.githubusercontent.com/Pradityaadi/Bigdata/main/pembatalan.png)
Jika di lihat sekilas tidak ada kenaikan dan penurunan yang begitu signifikan, akan tetapi ada tren tersembunyi dimana pada akhir tahun jumlah pengunjung malah berkurang dibandingkan bulan bulan lainnya.

**Negara Pengunjung**
![Deskripsi gambar](https://raw.githubusercontent.com/Pradityaadi/Bigdata/main/negara.png)
Negara pengunjung terbanyak negara tempat berasal dari negara pengambilan data ini yaitu portugal dengan total 48590 pengunjung dilanjut gibraltar,france,spanyol, belgia, italia, irlandia, belgia, brazil dan belanda

**Status Reservasi**
![Deskripsi gambar](https://raw.githubusercontent.com/Pradityaadi/Bigdata/main/statusreservasi.png)
Jika dilihat sekilas semakin menyimpulkan bahwasannya menuju akhir tahun terdapat penurunan pengunjung.

# "Machine Learning"
## Random Forest
Random Forest adalah ensemble learning method yang menggabungkan beberapa decision tree untuk meningkatkan kinerja model. Setiap tree dalam hutan dibangun menggunakan subset acak dari data pelatihan dan memilih fitur secara acak saat membangun pohon. Prediksi dari model ini didapat dengan melakukan voting (untuk klasifikasi) atau averaging (untuk regresi) dari prediksi setiap pohon.
## Decision Tree
Decision Tree adalah model pembelajaran mesin yang digunakan untuk tugas klasifikasi dan regresi. Model ini bekerja dengan membuat serangkaian keputusan yang berdasarkan pada pembagian data ke dalam subset berdasarkan nilai fitur. Setiap keputusan atau cabang dalam pohon mewakili keputusan berdasarkan atribut tertentu, dan setiap daun mewakili hasil keputusan (output).
## XGBoost
XGBoost adalah algoritma boosting yang dirancang untuk efisiensi dan kinerja. XGBoost membangun model secara bertahap, dengan setiap pohon baru yang mencoba untuk mengoreksi kesalahan yang dibuat oleh pohon sebelumnya. Algoritma ini menggunakan gradient boosting, yang mengoptimalkan fungsi loss menggunakan gradien, dan memiliki beberapa fitur tambahan untuk mengurangi overfitting, seperti regularisasi.

# "Hasil"
![Deskripsi gambar](https://raw.githubusercontent.com/Pradityaadi/Bigdata/main/Screenshot%202025-01-05%20134806.png)

Untuk hasil klasifikasi report dari ke-3 algoritma tersebut memiliki accuracy sama baiknya yaitu mencapai 100 persen

![Deskripsi gambar](https://raw.githubusercontent.com/Pradityaadi/Bigdata/main/Feature.png)
![Deskripsi gambar](https://raw.githubusercontent.com/Pradityaadi/Bigdata/main/xgb.png)

Dari ketiga algoritma yang digunakan, *reservation_status* muncul sebagai fitur paling penting dalam semua model. Dalam Random Forest, fitur ini memiliki kontribusi terbesar sebesar 69,68%, diikuti oleh *deposit_type* (7,59%) dan *country* (4,05%) serta Lead Time. Pada Decision Tree, *reservation_status* memiliki kontribusi penuh (nilai 1.0), sedangkan pada XGBoost, *reservation_status* tetap menjadi yang paling dominan dengan nilai 66,0, diikuti oleh *country* (20,0) dan *market_segment* (13,0) serta Lead Time. Meskipun ketiga algoritma menunjukkan pentingnya *reservation_status*, model XGBoost mengakui kontribusi fitur tambahan seperti *country* dan *market_segment*, sementara Decision Tree sangat bergantung pada fitur ini saja. Random Forest memberikan kontribusi yang lebih merata antara beberapa fitur, namun *reservation_status* tetap menjadi faktor utama dalam ketiga model tersebut.

Penelitian ini menganalisis kontribusi fitur dalam prediksi data hotel menggunakan tiga algoritma machine learning: Random Forest, Decision Tree, dan XGBoost. Secara keseluruhan dari ketiga algoritma yang diuji, reservation_status muncul sebagai fitur paling dominan, memberikan kontribusi besar terhadap prediksi perilaku reservasi tamu dalam seluruh model. Meskipun ketiga model menilai reservation_status sebagai fitur utama, hasil analisis juga menunjukkan bahwa algoritma seperti XGBoost dan Random Forest mampu mengidentifikasi lebih banyak fitur relevan yang memengaruhi prediksi. Hal ini menunjukkan kompleksitas data yang lebih baik ditangani oleh model yang lebih fleksibel seperti Random Forest dan XGBoost dibandingkan dengan Decision Tree yang cenderung bergantung pada satu fitur dominan.

# "Knowledge Interpretation"
Berdasar kan hasil dari Ketiga algoritma yang dipakai yaitu XGBoost, Decission tree, dan random forest. Kesemuanya memiliki akurasi maksimal, yang membedakan yaitu fitur fitur yang mempengaruhi hasil tersebut. Untuk kesemuanya ***reservation_status*** menjadi yang utama dikarenakan memang atribut tersebut berbanding lurus dengan keputan pengunjung karena atribut ini merupakan Status reservasi, seperti Canceled (dibatalkan), Check-Out (tamu telah check-out), atau No-Show (tamu tidak hadir), ada juga fitur fitur yang cukup berpengaruh lainnya yaitu :

1. country
2. deposit_type
3. market_segment
4. lead time

## Country
![Deskripsi gambar](https://raw.githubusercontent.com/Pradityaadi/Bigdata/main/CA.png)

Dapat disimpulkan bahwa negara Portugal (PRT) memiliki tingkat pembatalan yang sangat tinggi dibandingkan dengan negara-negara lainnya. Di sisi lain, negara-negara seperti Prancis (FRA), Inggris (GBR), Spanyol (ESP), Jerman (DEU), Irlandia (IRL), Italia (ITA), Belanda (NLD), Brasil (BRA), dan Belgia (BEL) menunjukkan angka pembatalan yang lebih rendah jika dibandingkan dengan yang tidak dibatalkan.

Strategi Pemasaran untuk Portugal (PRT):

* Mungkin perlu ada pendekatan pemasaran yang lebih intensif untuk mengurangi tingkat pembatalan di Portugal, seperti memberikan insentif bagi pelanggan untuk tidak membatalkan, seperti penawaran diskon atau promosi eksklusif.
* Menyusun ulang kebijakan pembayaran atau deposit untuk mendorong komitmen lebih awal dari pelanggan di Portugal.

Strategi Pemasaran untuk Negara-negara dengan Pembatalan Lebih Rendah:

* Negara-negara seperti Prancis, Inggris, Spanyol, dan lainnya yang memiliki pembatalan lebih rendah bisa diperlakukan dengan pendekatan yang berbeda. Misalnya, Anda bisa meningkatkan upaya pemasaran untuk meningkatkan loyalitas pelanggan di negara-negara ini, atau menyesuaikan layanan untuk menyesuaikan dengan preferensi lokal mereka.

Melakukan analisis lebih mendalam untuk menemukan pola di antara pelanggan dari Portugal, apakah ada faktor tertentu (seperti periode tertentu dalam setahun) yang lebih rentan terhadap pembatalan.
![Deskripsi gambar](https://raw.githubusercontent.com/Pradityaadi/Bigdata/main/PRT.png)
### Analisis Tren Pembatalan dan Tidak Pembatalan untuk Negara Portugal (PRT)

Dari data yang diberikan, berikut adalah analisis tren pembatalan dan tidak pembatalan per bulan di Portugal dari Juli 2015 hingga Agustus 2017:

#### 1. **Kenaikan Pembatalan Secara Umum**:
   - Secara keseluruhan, jumlah pembatalan cenderung meningkat dalam beberapa bulan pertama dari Juli 2015 hingga Maret 2016. Ini dapat dilihat dari bulan-bulan awal yang memiliki jumlah pembatalan yang lebih tinggi daripada jumlah yang tidak dibatalkan.
   - Misalnya, pada bulan **2015-07**, pembatalan (1210) lebih tinggi daripada yang tidak dibatalkan (867), dan tren ini berlanjut hingga **2016-03**.
   
#### 2. **Penurunan Pembatalan pada 2016-11 dan 2016-12**:
   - Pada **2016-11** dan **2016-12**, ada penurunan signifikan dalam pembatalan jika dibandingkan dengan bulan-bulan sebelumnya.
   - **2016-11** menunjukkan pembatalan (480) yang sangat rendah, bahkan lebih rendah daripada jumlah yang tidak dibatalkan (816), menunjukkan bahwa banyak pelanggan yang tidak membatalkan reservasi mereka.
   - **2016-12** juga memiliki jumlah pembatalan (919) yang lebih rendah dari bulan-bulan sebelumnya, meskipun masih lebih tinggi dibandingkan yang tidak dibatalkan (812). Hal ini mungkin menunjukkan adanya faktor musiman atau promosi yang mengurangi pembatalan.

#### 3. **Peningkatan Pembatalan pada 2017**:
   - Pada tahun **2017**, khususnya bulan-bulan pertama, pembatalan meningkat kembali. Misalnya, **2017-01** dan **2017-02** menunjukkan pembatalan yang lebih tinggi daripada bulan-bulan sebelumnya (634 dan 681).
   - Pembatalan mencapai angka tertinggi pada **2017-05** (1467), yang menunjukkan bahwa terdapat faktor tertentu yang menyebabkan lonjakan pembatalan pada bulan ini.

#### 4. **Fluktuasi yang Signifikan**:
   - Secara keseluruhan, meskipun ada tren peningkatan dan penurunan, angka pembatalan cenderung berfluktuasi di sekitar angka tertentu.
   - Ada bulan-bulan tertentu dengan jumlah pembatalan yang sangat tinggi, seperti pada **2016-06** (1557) dan **2017-05** (1467), diikuti oleh bulan dengan pembatalan yang lebih rendah.
   
#### 5. **Perbedaan Tren Musiman**:
   - Data ini juga menunjukkan adanya pengaruh musiman terhadap pembatalan. Misalnya, pada **2016-12** dan **2017-08**, pembatalan cenderung lebih rendah, yang mungkin terkait dengan liburan atau periode musim tinggi ketika permintaan lebih stabil.

#### **Kesimpulan**:
- **Tantangan Pembatalan**: Diperlukan strategi untuk mengurangi pembatalan, terutama pada bulan-bulan dengan tingkat pembatalan tinggi. Ini bisa mencakup penawaran diskon atau insentif untuk tidak membatalkan reservasi, serta memperbaiki komunikasi dan layanan pelanggan.
  
- **Pemahaman Musiman**: Analisis musiman penting untuk memahami kapan permintaan dan pembatalan mencapai puncaknya, sehingga dapat mempersiapkan kapasitas dan penawaran dengan lebih baik.

- **Strategi Pemulihan**: Untuk bulan-bulan dengan tingkat pembatalan yang tinggi, perusahaan hotel bisa mempertimbangkan cara untuk memulihkan atau menarik kembali pelanggan yang mungkin batal, seperti menawarkan pengembalian dana parsial atau perubahan tanggal.

## Deposit Type
![Deskripsi gambar](https://raw.githubusercontent.com/Pradityaadi/Bigdata/main/DEPOSIT.png)

Berdasarkan data diatas mengenai tipe deposit dan tingkat pembatalan, berikut adalah beberapa keputusan yang dapat diambil sebagai pimpinan hotel:

- **Tingkat Pembatalan**:
  - Tipe deposit **No Deposit** memiliki lebih banyak pengunjung yang tidak membatalkan dibandingkan yang membatalkan.
  - Tipe deposit **Non-Refundable** dan **Refundable** cenderung memiliki lebih banyak pengunjung yang tidak membatalkan dibandingkan yang membatalkan.

### Keputusan yang Dapat Diambil:

1. **Fokus pada Promosi dan Insentif untuk Tipe No Deposit**:
   - **No Deposit** memiliki banyak pengunjung yang tidak membatalkan, jadi ini bisa menjadi opsi yang menarik untuk lebih sering digunakan dalam promosi. Anda bisa mempertimbangkan untuk membuat lebih banyak paket yang menawarkan opsi ini.
   - Memberikan insentif lebih lanjut seperti diskon atau layanan tambahan untuk pengunjung yang memilih tipe **No Deposit**, yang terbukti tidak mudah membatalkan.

2. **Tingkatkan Penawaran Non-Refundable**:
   - Meskipun **Non-Refundable** lebih sedikit digunakan, tipe ini memberikan lebih banyak stabilitas keuangan karena pembayaran tidak dapat dikembalikan. Anda bisa meningkatkan penawaran untuk tipe ini, seperti menawarkan tarif lebih murah untuk tamu yang memilih **Non-Refundable**.
   - Untuk meningkatkan konversi dari **Non-Refundable**, Anda bisa memberikan penawaran spesial seperti tambahan fasilitas atau layanan ekstra.

3. **Perbaiki Kebijakan Refundable**:
   - Mengingat tipe **Refundable** memiliki jumlah pengunjung yang lebih sedikit, ini bisa menunjukkan bahwa orang cenderung lebih memilih opsi **Non-Refundable** atau **No Deposit** karena faktor kenyamanan harga atau kemudahan.
   - Juga mempertimbangkan untuk mempromosikan lebih agresif opsi **Refundable** untuk pengunjung yang membutuhkan lebih banyak fleksibilitas. Mungkin dapat memberikan lebih banyak jaminan atau peningkatan layanan yang dapat menarik lebih banyak pelanggan untuk memilih tipe ini.

4. **Strategi untuk Menurunkan Tingkat Pembatalan pada Tipe Non-Refundable dan Refundable**:
   - Meskipun pembatalan lebih sering terjadi pada tipe **Refundable**, juga bisa menambahkan kebijakan yang memperkecil kemungkinan pembatalan, seperti pengenaan biaya pembatalan atau persyaratan lebih ketat untuk pengembalian uang.
   - Mengingat pembatalan pada **Non-Refundable** dan **Refundable** relatif lebih rendah, memanfaatkan tipe ini untuk membuat kebijakan lebih keras terhadap pembatalan. Memberikan pemahaman yang lebih jelas tentang ketentuan ini di situs web bisa membantu menurunkan pembatalan.


### Kesimpulan:
- **No Deposit** memiliki potensi lebih besar untuk pengunjung yang tidak membatalkan, jadi bisa lebih dipromosikan.
- **Non-Refundable** bisa diperkaya dengan promosi tambahan untuk menarik lebih banyak pengunjung.
- **Refundable** perlu lebih diperkenalkan dengan layanan tambahan untuk membuatnya lebih menarik bagi pelanggan yang membutuhkan fleksibilitas.

## Market Segment
![Deskripsi gambar](https://raw.githubusercontent.com/Pradityaadi/Bigdata/main/MARKET.png)

### Market Segment:
  1. **Online TA** (Online Travel Agent) adalah segmen dengan pengunjung terbanyak, diikuti oleh **Offline TA/TO** (Travel Agents / Tour Operators), **Groups**, **Direct**, **Corporate**, **Complementary**, **Aviation**, dan **Undefined**.
  2. **Tingkat Pembatalan**:
     Secara umum, tingkat pembatalan lebih banyak **Tidak Batal** dibandingkan dengan **Batal** pada hampir semua segmen pasar, kecuali pada segmen **Groups** yang menunjukkan lebih banyak pembatalan.

### Keputusan yang Dapat Kami Ambil:

1. **Fokus pada Promosi untuk Segmen Online TA**:
   - **Online TA** memiliki jumlah pengunjung terbanyak dan tingkat pembatalannya relatif rendah. Kami bisa mempertimbangkan untuk menjalin lebih banyak kemitraan dengan agen perjalanan online (OTA) untuk meningkatkan visibilitas hotel dan menarik lebih banyak pengunjung.
   - Menawarkan penawaran khusus atau diskon bagi pengunjung yang memesan melalui OTA dapat memperkuat hubungan kami dengan agen ini dan meningkatkan kedatangan tamu.

2. **Tingkatkan Penawaran untuk Segmen Offline TA/TO**:
   - **Offline TA/TO** memiliki jumlah pengunjung yang signifikan dan tingkat pembatalan yang rendah, jadi ini adalah segmen yang patut diperhatikan lebih lanjut. Kami dapat bekerja lebih erat dengan agen perjalanan offline untuk menciptakan penawaran eksklusif atau paket bundling yang menarik bagi mereka.
   - Memperkenalkan paket perjalanan yang lebih murah atau eksklusif untuk pasar ini juga bisa menjadi strategi yang baik untuk meningkatkan pemesanan.

3. **Penanganan Segmen Groups**:
   - Pada segmen **Groups**, yang memiliki tingkat pembatalan lebih tinggi, kami perlu mempertimbangkan untuk memperkenalkan kebijakan pembatalan yang lebih ketat atau biaya pembatalan yang lebih tinggi untuk memitigasi risiko pembatalan mendadak.
   - Kami juga bisa menyediakan fleksibilitas dalam hal peraturan pembatalan untuk grup besar, dengan menawarkan potongan harga atau insentif bagi grup yang memesan dalam jumlah besar, untuk mendorong komitmen dari pihak yang memesan.

4. **Tingkatkan Penawaran untuk Segmen Direct dan Corporate**:
   - **Direct** (langsung) dan **Corporate** (korporat) adalah segmen yang biasanya memiliki stabilitas lebih tinggi dalam hal pemesanan. Kami dapat menawarkan lebih banyak paket atau keanggotaan loyalitas bagi tamu yang datang langsung ke hotel atau perusahaan yang melakukan pemesanan massal.
   - Menyediakan harga khusus untuk perusahaan yang melakukan pemesanan korporat atau menawarkan program loyalitas untuk tamu yang sering datang langsung bisa menjadi strategi yang efektif.

5. **Analisis Segmen Complementary dan Aviation**:
   - **Complementary** (komplementer) dan **Aviation** (maskapai penerbangan) memiliki lebih sedikit pengunjung, namun bisa menjadi segmen yang penting jika kami ingin mengembangkan kemitraan dengan maskapai atau penyedia layanan komplementer.
   - Bekerja sama dengan maskapai penerbangan untuk menawarkan paket khusus atau berkolaborasi dengan sektor-sektor terkait bisa memberikan peluang pemasaran tambahan.

6. **Optimalkan Segmen Undefined**:
   - **Undefined** (tidak terdefinisi) biasanya menunjukkan pengunjung yang tidak tercatat dalam kategori pasar tertentu. Mungkin ini adalah area di mana kami perlu melakukan pengumpulan data yang lebih baik dan segmentasi pasar lebih lanjut untuk mengidentifikasi potensi pasar dan memanfaatkannya.

### Kesimpulan:
- **Online TA** dan **Offline TA/TO** adalah segmen pasar yang memiliki tingkat pembatalan rendah dan merupakan peluang besar untuk mengembangkan kerjasama lebih lanjut.
- Untuk **Groups**, perlu memperkenalkan kebijakan lebih ketat terkait pembatalan, tetapi dengan menawarkan insentif yang lebih besar, ini dapat menjadi segmen yang menguntungkan.
- **Direct** dan **Corporate** merupakan segmen yang stabil dan penting, yang dapat diberikan keuntungan lebih seperti diskon dan program loyalitas.
- Perlu lebih banyak analisis untuk segmen **Complementary** dan **Aviation** serta segmentasi pasar **Undefined** untuk memaksimalkan peluang.

## Lead Time
![Deskripsi gambar](https://raw.githubusercontent.com/Pradityaadi/Bigdata/main/LEAD.png)

Berikut adalah strategi yang bisa diambil berdasarkan pembagian **Lead Time** dan tingkat pembatalan:

### 1. **Pembagian Lead Time per 50 (0-750)**
Lead time dibagi dalam interval 50, mulai dari 0 hingga 750. Kami akan menganalisis tingkat pembatalan pada rentang lead time ini, dengan fokus pada perubahan tren pembatalan.

### 2. **Tingkat Pembatalan pada Lead Time**
- **0 hingga 250**: Pada rentang ini, kami akan melihat bahwa tingkat pembatalan lebih banyak **Tidak Batal** daripada **Batal**.
- **250 ke atas**: Di atas 250, kebalikannya terjadi, yaitu tingkat pembatalan lebih banyak **Batal** daripada **Tidak Batal**.

Berdasarkan hal ini, berikut adalah langkah yang dapat diambil:

### Keputusan Berdasarkan Analisis:
1. **Untuk Lead Time 0 hingga 250**:
   - Dapat memanfaatkan **tidak banyak pembatalan** untuk meningkatkan kepercayaan tamu dan melakukan promosi untuk pemesanan dalam jangka waktu pendek (terutama untuk lead time rendah).
   - Bisa juga menawarkan penawaran khusus untuk tamu yang melakukan pemesanan lebih awal dengan lead time yang lebih pendek, misalnya diskon atau paket spesial untuk jangka waktu mendekati kedatangan (misalnya, 0 hingga 100 hari sebelumnya).
   - Ini bisa mendorong lebih banyak tamu untuk memesan di hotel tanpa khawatir melakukan pembatalan.

2. **Untuk Lead Time 250 hingga 750**:
   - Pada rentang ini, harus lebih berhati-hati karena pembatalan lebih banyak terjadi, terutama setelah **250 hari ke atas**. Oleh karena itu, bisa menerapkan kebijakan pembatalan yang lebih ketat atau biaya pembatalan tambahan bagi tamu dengan lead time yang lebih panjang.
   - Jika memungkinkan,bisa menawarkan insentif untuk tamu yang memesan jauh-jauh hari, tetapi dengan syarat bahwa mereka melakukan pemesanan dengan kebijakan pembatalan yang lebih ketat atau non-refundable.
   - Mempertimbangkan promosi untuk **non-refundable deposit** atau memaksa pembatalan hanya dalam waktu terbatas setelah pemesanan bisa mengurangi risiko pembatalan di lead time panjang.

### 3. **Strategi Berdasarkan Tren Pembatalan**:
- **Untuk rentang lead time 0 hingga 250** (lebih banyak tidak batal): Fokus pada **penawaran insentif untuk mendorong pemesanan** dalam jangka waktu dekat dan meningkatkan pemesanan langsung.
- **Untuk rentang lead time 250 hingga 750** (lebih banyak batal): Terapkan **biaya pembatalan lebih tinggi** atau kebijakan lebih ketat dan tawarkan **penawaran non-refundable** untuk meminimalisir kerugian akibat pembatalan.


## Lisensi
Proyek ini dilisensikan di bawah [colab License](https://colab.research.google.com/drive/1Y6RJcYETbYcMIkfgzizHUyLIZ4l5fQxm#scrollTo=spChRZ_jIQ4C).

## Nama Kelompok
- 👨‍💻Muhamad Minan Nur Mu'alim(202110370311197)
- 👨‍💻Praditya Adi Saputra(202110370311181)
