# 🌱 Proyek Deteksi Risiko Stunting dengan Self-Organizing Map (SOM)

## 📘 Latar Belakang
Stunting dan wasting merupakan dua indikator serius dalam menilai status gizi anak. Dengan semakin meluasnya data kesehatan anak, muncul kebutuhan untuk memahami dan memetakan kondisi ini secara efisien.

Dalam proyek ini, kita mencoba **mengelompokkan anak-anak berdasarkan umur, tinggi badan, dan berat badan**, guna mendeteksi potensi risiko stunting—dan semua itu dilakukan menggunakan algoritma **Self-Organizing Map (SOM)** buatan sendiri. Sebuah pendekatan tak terawasi (unsupervised learning) yang memiliki kekuatan dalam memvisualisasikan struktur data multidimensi ke dalam peta 2D.

---

## 📂 Dataset

Kami menggunakan dua dataset utama:

### 🔹 Data Latih (`Stunting_Dataset.csv`)
- Jumlah data: **100.000 entri**
- Kolom penting:
  - `Umur (bulan)`
  - `Tinggi Badan (cm)`
  - `Berat Badan (kg)`
  - `Stunting`
  - `Wasting`

### 🔹 Data Uji (`stunting_wasting_dataset.csv`)
- Digunakan untuk menguji generalisasi model SOM terhadap data baru.
- Disesuaikan nama kolomnya agar seragam dengan data latih.

---

## 🛠️ Proses Analisis

### 1. **Pra-pemrosesan & Normalisasi**
Kami menggunakan **Min-Max Scaling** untuk meratakan skala data:

> "Justifikasi: Fitur umur, tinggi badan, dan berat badan memiliki rentang berbeda. Min-Max scaling menormalkan nilai fitur dalam rentang 0-1 agar SOM tidak berat sebelah."

### 2. **Pembangunan Model SOM**
Kami membangun kelas `SimpleSOM` manual:
- Grid SOM: fleksibel ukuran `x × y`
- Parameter penting:
  - `sigma` (radius pengaruh)
  - `learning_rate`
- Proses pelatihan mencatat jarak antara input dan BMU (Best Matching Unit)

---

## 📊 Hasil dan Statistik

### Statistik Data Latih:
```
        Umur (bulan)  Tinggi Badan (cm)  Berat Badan (kg)
count  100000.000000      100000.000000     100000.000000
mean       11.992580          73.132657          9.259256
std         7.199671          11.360846          3.300780
min         0.000000          42.600000          1.000000
25%         6.000000          65.500000          6.900000
50%        12.000000          74.200000          9.200000
75%        18.000000          81.400000         11.700000
max        24.000000          97.600000         17.200000
```

### Nilai Kosong:
Tidak ditemukan nilai kosong pada data latih:
```
Jenis Kelamin        0
Umur (bulan)         0
Tinggi Badan (cm)    0
Berat Badan (kg)     0
Stunting             0
Wasting              0
```

---

## 🔍 Kesimpulan

```
- Model SOM berhasil mengelompokkan data anak berdasarkan fitur umur, tinggi badan, dan berat badan.
- Normalisasi Min-Max efektif menyeimbangkan skala fitur sehingga model dapat belajar dengan baik.
- Parameter learning rate dan sigma signifikan mempengaruhi performa dan stabilitas konvergensi SOM.
- Eksperimen menunjukkan learning rate=0.5 dan sigma=1.0 memberikan rata-rata jarak BMU terbaik.
- Visualisasi cluster membantu dalam memahami distribusi data dan karakteristik tiap cluster.
- Klaster-klaster dapat digunakan untuk analisis lebih lanjut seperti identifikasi risiko stunting.
```

---

## 💡 Catatan Tambahan
- File `Tubes ML SOM FIXX.ipynb` mencakup keseluruhan kode Python, mulai dari pra-pemrosesan, visualisasi, hingga evaluasi SOM.
- Dataset telah dibersihkan dan divalidasi sebelum digunakan.
- Model tidak menggunakan label `Stunting` atau `Wasting` secara langsung dalam pelatihan, namun hasil klaster dapat dibandingkan terhadap label tersebut untuk validasi lebih lanjut.

---

## 🧠 Teknologi dan Library
- Python
- Pandas
- NumPy
- Matplotlib

---

> Dibuat sebagai bagian dari tugas akhir pembelajaran Machine Learning dengan pendekatan sederhana namun mendalam.
