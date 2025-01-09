# Program Deteksi Embrio Menggunakan Watershed Algorithm

## Deskripsi
Program ini bertujuan untuk mendeteksi dan memvisualisasikan area embrio dalam sebuah gambar menggunakan teknik **image processing** dengan pendekatan algoritma Watershed. Proses terdiri dari langkah-langkah pre-processing, segmentasi, dan visualisasi hasil dengan histogram.

---

## Langkah-Langkah Proses

### 1. Membaca Gambar
- **Deskripsi:**
  Gambar dibaca menggunakan OpenCV (`cv2.imread()`), lalu diubah ke skala abu-abu dengan `cv2.cvtColor`.
- **Tujuan:**
  Konversi ke grayscale mempermudah operasi pada tahap berikutnya.

---

### 2. Peningkatan Gambar
- **Deskripsi:**
  Melakukan **Histogram Equalization** pada gambar grayscale menggunakan `cv2.equalizeHist()` untuk meningkatkan kontras.
- **Tujuan:**
  Menonjolkan area yang memiliki intensitas piksel rendah atau tinggi.

---

### 3. Thresholding
- **Deskripsi:**
  Menggunakan metode **Otsu's Thresholding** untuk mengubah gambar ke bentuk biner.
- **Langkah:**
  Mengaplikasikan `cv2.threshold()` dengan mode `THRESH_BINARY + THRESH_OTSU`.
- **Tujuan:**
  Memisahkan objek (embrio) dari latar belakang.

---

### 4. Penghapusan Noise
- **Deskripsi:**
  Menggunakan operasi morfologi **Opening** dengan kernel 3x3.
- **Langkah:**
  Aplikasi `cv2.morphologyEx()` dengan parameter `MORPH_OPEN`.
- **Tujuan:**
  Menghilangkan noise kecil pada hasil thresholding.

---

### 5. Penentuan Area
- **Deskripsi:**
  Menentukan area foreground (embrio) dan background (latar belakang).
- **Langkah:**
  - **Sure Background:** Menggunakan dilasi pada hasil morfologi opening.
  - **Sure Foreground:** Menggunakan **distance transform** dan threshold.
  - **Unknown Region:** Dihitung dengan mengurangkan sure background dari sure foreground.
- **Tujuan:**
  Memisahkan dengan jelas area embrio dari latar belakang.

---

### 6. Marker Labelling
- **Deskripsi:**
  Menandai setiap area tersegmentasi menggunakan `cv2.connectedComponents()`. Menambahkan satu ke semua label untuk memastikan latar belakang memiliki nilai `1`.
- **Tujuan:**
  Persiapan untuk proses algoritma Watershed.

---

### 7. Segmentasi dengan Watershed
- **Deskripsi:**
  Menerapkan algoritma Watershed untuk memperbaiki segmentasi dan menandai batas area embrio.
- **Langkah:**
  - Menandai batas area sebagai `-1`.
  - Menampilkan batas tersebut dengan warna merah pada gambar asli.
- **Tujuan:**
  Mengidentifikasi batas yang lebih akurat antara embrio dan latar belakang.

---

### 8. Visualisasi Hasil
- **Deskripsi:**
  Menampilkan hasil setiap langkah dalam bentuk gambar dan histogram:
  - **Gambar asli** dan histogramnya.
  - **Grayscale image** dan histogramnya.
  - **Enhanced image** dan histogramnya.
  - **Binary image** dan histogramnya.
  - **Noise removed image** dan histogramnya.
  - **Distance transform**.
  - **Sure foreground**.
  - **Hasil Watershed segmentation**.
- **Tujuan:**
  Memahami perubahan yang terjadi pada setiap tahap pemrosesan.

---

## Penjelasan Output

### 1. Original Image
- **Deskripsi:**
  Gambar asli yang diinputkan ke sistem.

### 2. Grayscale Image
- **Deskripsi:**
  Gambar asli yang telah diubah menjadi grayscale.

### 3. Enhanced Image
- **Deskripsi:**
  Gambar grayscale yang telah ditingkatkan kontrasnya melalui histogram equalization.

### 4. Binary Image
- **Deskripsi:**
  Hasil thresholding untuk memisahkan embrio dari latar belakang.


### 5. Noise Removed (Hasil Setelah Penghapusan Noise)
- Tahap ini menggunakan operasi morfologi seperti **opening** untuk menghilangkan noise kecil pada gambar hasil thresholding.
- **Interpretasi**:
  - Area putih pada gambar menunjukkan objek utama (kemungkinan embrio).
  - Area hitam merupakan latar belakang.
- Noise kecil berhasil dihilangkan, sehingga objek utama menjadi lebih jelas.

---

### 6. Histogram: Noise Removed
- Histogram ini menunjukkan distribusi nilai piksel setelah penghapusan noise.
- **Interpretasi**:
  - Sebagian besar piksel memiliki nilai di ujung atas (warna putih) dan bawah (warna hitam).
  - Hal ini konsisten dengan hasil biner dari proses thresholding.

---

### 7. Distance Transform
- **Distance transform** digunakan untuk menghitung jarak tiap piksel latar depan (foreground) ke piksel latar belakang (background) terdekat.
- **Interpretasi**:
  - Area yang lebih terang menandakan jarak terbesar dari piksel foreground ke tepi.
  - Tahap ini membantu dalam menentukan **sure foreground** (area foreground yang pasti).

---

### 8. Sure Foreground
- Gambar ini menunjukkan area **foreground yang pasti** yang dihasilkan dari thresholding pada hasil distance transform.
- **Interpretasi**:
  - Area putih adalah bagian yang dianggap sebagai bagian objek utama yang paling jelas (yaitu embrio).
  - Area ini akan digunakan sebagai input untuk segmentasi.

---

### 9. Watershed Segmentation
- Hasil akhir dari segmentasi menggunakan algoritma watershed.
- **Interpretasi**:
  - Batas antara objek (dan antara objek dengan latar belakang) ditandai dengan garis merah.
  - Objek utama (embrio) berhasil dipisahkan dari latar belakang dengan lebih jelas.

---

## Kesimpulan
- Proses deteksi melalui langkah-langkah seperti penghapusan noise, transformasi jarak, dan algoritma watershed telah berhasil memisahkan embrio dari latar belakang.
- **Saran untuk Analisis**:
  - Pastikan hasil segmentasi sesuai dengan bentuk dan lokasi embrio yang sebenarnya.
  - Jika terdapat noise atau batas tidak sempurna, tambahkan langkah-langkah perbaikan seperti fine-tuning parameter threshold atau kernel morfologi.
  - Gunakan gambar dengan kualitas tinggi untuk meningkatkan akurasi hasil deteksi.

## Persyaratan
- **Pustaka Python:**
  - `cv2` (OpenCV)
  - `NumPy`
  - `Matplotlib`
  - `google.colab` (untuk mengunggah file di Google Colab)

---

## Cara Menggunakan
1. Unggah file gambar yang ingin diproses.
2. Jalankan fungsi `detect_embryo(image_path)` dengan jalur file gambar sebagai parameter.
3. Amati hasil visualisasi pada layar.

---

## Catatan
- Pastikan gambar memiliki resolusi yang cukup untuk mendeteksi detail embrio.
- Ubah nilai kernel atau parameter lainnya jika diperlukan untuk hasil segmentasi yang lebih optimal.
