# Laporan UAS Praktikum

### Teori Deteksi Tepi dan Kontur
1. Pendahuluan
   
Deteksi tepi dan kontur adalah teknik dasar dalam pengolahan citra yang digunakan untuk menemukan batas objek dalam gambar. Teknik ini sangat penting dalam berbagai aplikasi seperti pengenalan objek, segmentasi citra, dan visi komputer.

3. Deteksi Tepi (Edge Detection)
   
Deteksi tepi adalah proses menemukan batas-batas objek dalam gambar dengan mengidentifikasi titik-titik di mana intensitas piksel berubah secara signifikan. Salah satu algoritma deteksi tepi yang paling umum digunakan adalah algoritma Canny.

Algoritma Canny

Algoritma Canny adalah salah satu metode deteksi tepi yang paling populer karena memberikan hasil yang akurat. Algoritma ini terdiri dari beberapa langkah:

- Penghalusan (Smoothing): Menggunakan filter Gaussian untuk menghaluskan gambar dan mengurangi noise.
- Deteksi Gradien: Menghitung gradien intensitas gambar menggunakan operator Sobel untuk menemukan arah dan kekuatan perubahan intensitas.
- Non-Maximum Suppression: Menekan semua piksel yang tidak berada di puncak lokal untuk menipiskan tepi.
- Double Thresholding: Menggunakan dua ambang batas untuk mengidentifikasi tepi kuat dan lemah.
- Edge Tracking by Hysteresis: Menghubungkan tepi lemah yang terhubung ke tepi kuat untuk membentuk tepi akhir.

3. Deteksi Kontur (Contour Detection)
   
Kontur adalah kurva yang menghubungkan semua titik kontinu (sepanjang batas), dengan warna atau intensitas yang sama. Dalam OpenCV, fungsi findContours digunakan untuk mendeteksi kontur dalam gambar biner yang dihasilkan dari deteksi tepi. Kontur dapat digunakan untuk analisis bentuk dan objek dalam gambar, memungkinkan pengukuran area, panjang, dan fitur lainnya dari objek yang terdeteksi.

4. Aplikasi dan Manfaat
- Pengenalan Objek: Deteksi tepi dan kontur membantu dalam mengidentifikasi dan melacak objek dalam gambar atau video.
- Segmentasi Citra: Teknik ini memudahkan pemisahan objek dari latar belakang untuk analisis lebih lanjut.
- Vektor Fitur: Kontur dapat digunakan untuk mengekstraksi fitur bentuk dari objek, yang berguna dalam aplikasi pengenalan pola dan klasifikasi.

5. Kesimpulan
    
Deteksi tepi dan kontur adalah teknik penting dalam pengolahan citra dan visi komputer. Dengan menggunakan algoritma seperti Canny untuk deteksi tepi dan fungsi kontur dalam OpenCV, kita dapat secara efektif mengidentifikasi dan menganalisis batas-batas objek dalam gambar. Ini membuka banyak kemungkinan untuk aplikasi dalam berbagai bidang, termasuk pengenalan objek, analisis citra medis, dan pemantauan visual.


### Tahapan Cara Menyelesaikan Proyek Deteksi Tepi dan Kontur
1. Pendahuluan
   
Proyek ini bertujuan untuk mendeteksi tepi dan kontur objek dalam gambar menggunakan algoritma Canny dan fungsi deteksi kontur dari OpenCV. Deteksi tepi dan kontur sangat penting dalam analisis citra digital, terutama dalam bidang seperti pengenalan objek, visi komputer, dan pengolahan citra medis. Dengan mendeteksi tepi, kita dapat mengekstrak fitur penting dari gambar yang berguna untuk berbagai aplikasi seperti segmentasi gambar, pengenalan pola, dan analisis bentuk.

2. Membaca Gambar
   
Gunakan OpenCV untuk membaca gambar dari file yang akan digunakan. Membaca gambar adalah langkah awal yang penting karena gambar adalah data yang akan diolah. OpenCV menyediakan fungsi cv2.imread() yang dapat digunakan untuk membaca gambar dari file. Pastikan gambar yang dipilih relevan dengan tujuan proyek.

3. Konversi Warna
   
Gambar yang dibaca oleh OpenCV biasanya dalam format BGR (Blue, Green, Red), sedangkan banyak alat visualisasi seperti Matplotlib bekerja dengan format RGB (Red, Green, Blue). Oleh karena itu, konversi dari BGR ke RGB diperlukan agar gambar kompatibel dengan alat-alat visualisasi ini. Konversi warna dapat dilakukan dengan fungsi cv2.cvtColor() dari OpenCV.

4. Deteksi Tepi Menggunakan Algoritma Canny
   
Pengaturan Parameter:

Algoritma Canny membutuhkan dua nilai ambang batas untuk mendeteksi tepi dalam gambar. Nilai ambang batas ini menentukan sensitivitas deteksi tepi. Nilai yang lebih rendah akan mendeteksi lebih banyak tepi, termasuk yang kurang signifikan, sementara nilai yang lebih tinggi hanya akan mendeteksi tepi yang lebih kuat. Penentuan nilai ambang batas yang tepat adalah kunci untuk mendapatkan hasil deteksi tepi yang optimal.

Penerapan Algoritma Canny

Algoritma Canny bekerja dengan beberapa langkah:

- Noise Reduction: Menggunakan filter Gaussian untuk menghaluskan gambar dan mengurangi noise.
- Gradient Calculation: Menghitung gradien intensitas pada setiap piksel untuk menemukan area dengan perubahan intensitas yang tajam.
- Non-maximum Suppression: Menekan semua nilai gradien yang bukan merupakan puncak lokal untuk memastikan bahwa hanya tepi yang paling tajam yang dipertahankan.
- Double Threshold: Menggunakan dua nilai ambang batas untuk mengklasifikasikan piksel menjadi tepi kuat, tepi lemah, atau bukan tepi.
- Edge Tracking by Hysteresis: Menghubungkan tepi lemah ke tepi kuat jika tepi lemah bersebelahan dengan tepi kuat.

5. Deteksi Kontur
   
Menemukan Kontur:

Setelah tepi terdeteksi, langkah selanjutnya adalah menemukan kontur. Kontur adalah kurva yang menghubungkan semua titik kontinu yang memiliki intensitas warna yang sama. Dalam konteks pengolahan citra, kontur membantu dalam mengenali bentuk dan batas objek dalam gambar. OpenCV menyediakan fungsi cv2.findContours() untuk mendeteksi kontur dalam gambar biner hasil dari algoritma Canny.

Menggambar Kontur:

Untuk memvisualisasikan hasil deteksi kontur, kita dapat menggambar kontur yang ditemukan pada gambar asli. Fungsi cv2.drawContours() dari OpenCV digunakan untuk menggambar kontur pada gambar. Ini membantu dalam memahami hasil deteksi dengan lebih baik, karena kita dapat melihat batas-batas objek yang terdeteksi pada gambar asli.

6. Menampilkan Hasil Menggunakan Matplotlib
Membuat Tampilan:

Setelah semua langkah pemrosesan selesai, penting untuk menampilkan hasil secara visual. Matplotlib digunakan untuk membuat tampilan dari gambar asli, hasil deteksi tepi, dan hasil deteksi kontur. Tampilan visual ini membantu dalam menganalisis hasil dan memvalidasi kebenaran deteksi tepi dan kontur.

Pengaturan Plot:

Untuk memudahkan analisis dan perbandingan, atur plot agar menampilkan semua hasil dalam satu jendela. Matplotlib menyediakan berbagai fungsi untuk mengatur plot, seperti plt.subplot() untuk membuat beberapa plot dalam satu jendela, plt.imshow() untuk menampilkan gambar, dan plt.title() untuk memberikan judul pada setiap plot.

### Referensi dan Jurnal Terkait
Untuk mendukung proyek ini secara teoretis dan menambahkan kedalaman pada laporan, berikut adalah beberapa jurnal dan referensi terkait yang dapat digunakan:

Jurnal tentang Deteksi Tepi:

1. Canny, J. (1986). "A Computational Approach to Edge Detection". Makalah ini memperkenalkan algoritma Canny yang terkenal untuk deteksi tepi. Algoritma ini diakui sebagai salah satu metode terbaik untuk deteksi tepi karena kemampuannya untuk menemukan tepi dengan baik dan menghasilkan sedikit noise.

2. Marr, D., & Hildreth, E. (1980). "Theory of Edge Detection". Makalah ini membahas teori dasar tentang deteksi tepi dan pentingnya perubahan intensitas dalam gambar untuk mendeteksi batas-batas objek.
Jurnal tentang Deteksi Kontur:

1. Suzuki, S., & be, K. (1985). "Topological Structural Analysis of Digitized Binary Images by Border Following". Makalah ini membahas metode untuk menemukan kontur dalam gambar biner. Metode ini sering digunakan dalam aplikasi pengolahan citra untuk mengenali bentuk dan batas objek.

2. Freeman, H., & Shapira, R. (1975). "Determining the Minimum-Area Encasing Rectangle for an Arbitrary Closed Curve". Makalah ini membahas algoritma untuk menemukan persegi panjang dengan area minimum yang menutupi kurva tertutup dalam gambar. Ini berguna dalam analisis bentuk dan segmentasi objek.

Buku Referensi:

Gonzalez, R. C., & Woods, R. E. (2008). "Digital Image Processing". Buku ini adalah referensi komprehensif tentang teori dan aplikasi pengolahan citra digital. Ini mencakup berbagai topik termasuk deteksi tepi dan kontur.
Szeliski, R. (2010). "Computer Vision: Algorithms and Applications". Buku ini menyediakan pemahaman mendalam tentang algoritma dan aplikasi visi komputer. Ini termasuk pembahasan tentang deteksi tepi dan kontur serta aplikasi praktisnya.
