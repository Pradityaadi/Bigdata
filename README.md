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
