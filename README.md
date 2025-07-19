# Analisis Sentimen Ulasan Aplikasi Gojek

## 📌 Ringkasan Proyek
Proyek ini bertujuan untuk membangun model *machine learning* yang dapat mengklasifikasikan sentimen (positif, negatif, netral) dari ulasan pengguna aplikasi Gojek di Google Play Store. Dengan menggunakan algoritma **Multinomial Naive Bayes** dan teknik pra-pemrosesan teks yang komprehensif, model ini dikembangkan untuk memahami persepsi publik terhadap layanan Gojek.

Meskipun model mencapai akurasi keseluruhan sebesar **79.7%**, analisis yang lebih dalam menunjukkan bahwa performa model sangat tidak seimbang. Temuan paling krusial dari proyek ini adalah bahwa model sangat andal dalam mendeteksi ulasan negatif, namun hampir sepenuhnya gagal mengidentifikasi ulasan netral dan positif.

🔗 **[Lihat Kode Lengkap di Repositori GitHub](https://github.com/YusepFathul/Analisis-Sentimen-Gojek)**

---

## 🎯 Tujuan Proyek
- **Pra-pemrosesan Data Teks:** Membersihkan, menormalisasi, dan mengubah data ulasan mentah menjadi format yang siap dianalisis.
- **Pembangunan Model:** Membangun model klasifikasi sentimen menggunakan Multinomial Naive Bayes dengan penanganan data tidak seimbang (imbalance).
- **Evaluasi Kritis:** Menganalisis kinerja model secara mendalam menggunakan metrik seperti *Precision, Recall, F1-score,* dan *Confusion Matrix*, tidak hanya bergantung pada akurasi.
- **Identifikasi Tantangan:** Mengidentifikasi kelemahan model dan tantangan yang muncul dari karakteristik dataset yang digunakan.

---

## 🧰 Teknologi & Library yang Digunakan
- **Lingkungan Kerja:** Google Colaboratory
- **Library Utama:**
  - **`Python`**
  - **`Pandas`** & **`NumPy`**: Untuk manipulasi dan pembersihan data.
  - **`Scikit-learn`**: Untuk TF-IDF Vectorizer, model Naive Bayes, dan metrik evaluasi.
  - **`Imbalanced-learn`**: Untuk teknik over-sampling SMOTE.
  - **`Stanza`**: Untuk proses tokenisasi teks bahasa Indonesia.
  - **`Matplotlib`** & **`Seaborn`**: Untuk visualisasi data.

---

## 🛠️ Metodologi Proyek

1.  **Pengumpulan & Pembersihan Data:**
    - **Sumber:** Dataset ulasan aplikasi Gojek dari Kaggle.
    - **Pembersihan:** Menghapus kolom yang tidak relevan dan semua baris data yang kosong (NaN), yang mengurangi dataset dari 445,500 menjadi 90,559 baris.
    - **Sampling:** Mengambil sampel acak sebanyak 10,000 data untuk efisiensi komputasi.

2.  **Pra-pemrosesan Teks (Text Preprocessing):**
    - **Normalisasi:** Mengubah teks menjadi huruf kecil dan menghapus karakter non-alfabet.
    - **Tokenisasi:** Memecah kalimat menjadi kata-kata (tokens) menggunakan library **Stanza** yang dirancang untuk linguistik bahasa Indonesia.

3.  **Pelabelan Sentimen:**
    Sentimen ditentukan secara otomatis berdasarkan rating bintang (`score`):
    - **Negatif**: Skor < 3 (⭐ & ⭐⭐)
    - **Netral**: Skor = 3 (⭐⭐⭐)
    - **Positif**: Skor > 3 (⭐⭐⭐⭐ & ⭐⭐⭐⭐⭐)

4.  **Pemodelan Machine Learning:**
    - **Ekstraksi Fitur:** Mengubah teks menjadi vektor numerik menggunakan **TF-IDF Vectorizer**, dengan mempertimbangkan kata tunggal dan frasa dua kata (*bigram*).
    - **Penanganan Imbalance:** Menerapkan **SMOTE** (*Synthetic Minority Over-sampling Technique*) pada data latih untuk menyeimbangkan jumlah data di setiap kelas sentimen.
    - **Algoritma:** Menggunakan model **Multinomial Naive Bayes** untuk klasifikasi.

---

## 📈 Hasil dan Analisis

### Distribusi Sentimen
Visualisasi data menunjukkan dataset sampel sangat tidak seimbang dan didominasi oleh sentimen negatif.
- **Negatif**: 83.5%
- **Netral**: 13.4%
- **Positif**: 3.1%

*Insight: Mayoritas pengguna dalam sampel ini memberikan ulasan dengan nada negatif, yang menandakan adanya isu signifikan yang perlu diperhatikan.*

### Performa Model
Meskipun akurasi keseluruhan **79.7%**, angka ini menyesatkan. Analisis lebih dalam melalui *Classification Report* dan *Confusion Matrix* menunjukkan:

- **Sangat Andal untuk Sentimen Negatif:** Model mampu mendeteksi ulasan negatif dengan sangat baik (**F1-score 0.90**).
- **Sangat Buruk untuk Sentimen Netral & Positif:** Model hampir tidak memiliki kemampuan untuk mengidentifikasi ulasan netral (**F1-score 0.11**) dan positif (**F1-score 0.17**).
- **Kesimpulan Matriks Kebingungan:** Model cenderung "bermain aman" dengan memprediksi mayoritas ulasan sebagai negatif. Sebagian besar ulasan netral dan positif salah diklasifikasikan sebagai negatif.

---

## 💡 Kesimpulan dan Insight Utama

1.  **Dominasi Sentimen Negatif:** Ulasan aplikasi Gojek dalam dataset ini secara signifikan didominasi oleh keluhan dan kritik.
2.  **Model yang Bias:** Model Naive Bayes yang dibangun sangat bias terhadap kelas mayoritas (negatif). Akurasi tinggi yang ditampilkan hanyalah ilusi yang menutupi ketidakmampuannya mengenali kelas lain.
3.  **Tidak Efektif untuk Umpan Balik Positif:** Model ini tidak dapat diandalkan untuk menyaring ulasan positif atau netral, sehingga membatasi kegunaannya untuk memahami kelebihan produk atau area perbaikan spesifik.
4.  **Tantangan Data Tidak Seimbang:** Teknik SMOTE terbukti tidak cukup untuk mengatasi masalah ketidakseimbangan data yang ekstrem pada kasus ini.

---

## Tantangan dan Potensi Peningkatan
- **Tantangan Utama:** Ketidakseimbangan kelas yang ekstrem dan potensi bias yang timbul dari proses pembersihan data (menghapus ribuan baris NaN).
- **Potensi Peningkatan:**
  - Menggunakan teknik sampling yang lebih canggih (misalnya, kombinasi SMOTE dan Edited Nearest Neighbours).
  - Mencoba algoritma lain yang lebih tangguh terhadap data tidak seimbang, seperti **SVM** atau **XGBoost**.
  - Melakukan pengumpulan data tambahan, terutama untuk ulasan positif dan netral, untuk menciptakan dataset yang lebih representatif.

---

## 👤 Contact
- **Name:** Yusep Fathul Anwar
- **LinkedIn:** [https://linkedin.com/in/your-username](https://linkedin.com/in/your-username)](https://www.linkedin.com/in/yusepfathulanwar/
- **Github:** https://github.com/YusepFathul
