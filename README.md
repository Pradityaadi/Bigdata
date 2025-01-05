# Hotel Bookings Data

# "Pendahuluan"
## 1.Pernyataan Masalah
Industri perhotelan merupakan sektor yang sangat dinamis yang bergantung pada tingkat hunian untuk mempertahankan pendapatan yang stabil. ***Namun***, salah satu tantangan terbesar yang dihadapi hotel adalah tingkat pembatalan yang tinggi. Pembatalan ini dapat mengakibatkan kerugian yang signifikan, karena kamar yang telah dibayar di muka dan kemudian dibatalkan **tidak dapat segera diisi ulang**. Oleh karena itu, pemahaman yang lebih baik tentang faktor-faktor yang memengaruhi pembatalan sangatlah penting.

Mengapa harus tertarik dengan hal ini? Karena setiap pembatalan yang terjadi dapat memengaruhi **profitabilitas** hotel. Dengan memahami faktor-faktor yang memengaruhi pembatalan, hotel dapat menerapkan kebijakan ***yang lebih terarah*** untuk mengurangi jumlah pembatalan dan meningkatkan tingkat hunian. Hal ini tidak hanya menguntungkan secara finansial, tetapi juga meningkatkan pengalaman pelanggan.
## 2.Rencana Mengatasi Masalah:
Untuk mengatasi masalah ini, kami berencana menganalisis data pemesanan hotel yang mencakup informasi tentang **status pembatalan, jenis hotel, jumlah tamu, jenis kamar yang dipesan, lama menginap, dan faktor lain seperti negara asal tamu dan jenis pemesanan**. Kami akan menggunakan metode analisis data eksploratif menggunakana** machine learning** untuk memahami pola yang ada, serta khususnya teknik **klasifikasi** untuk memprediksi kemungkinan pembatalan berdasarkan data yang ada.
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
Periode pengumpulan data berlangsung dari **1 Juli 2015** hingga 3**1 Agustus 2017** dengan fokus pengambilan data di negara **Portugal**. Hotel Resor (H1) berlokasi di wilayah **Algarve**, sedangkan Hotel Kota (H2) berlokasi di kota **Lisbon**. Dengan kumpulan data yang mencakup** 32 variabel** dan total **119.390 raw data**. Dari jumlah tersebut, **40.060 raw data** berasal dari Hotel Resor (H1), sedangkan **79.330 raw data** lainnya berasal dari Hotel Kota (H2). Data ini dikumpulkan secara real time tanpa menyertakan informasi yang dapat mengidentifikasi hotel atau pelanggan tertentu.
