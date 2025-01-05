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
** *teks yang dimiringkan*Variabel - Deskripsi** </br>
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
