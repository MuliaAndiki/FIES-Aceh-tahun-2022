Tentu, mari kita buat README.md Anda menjadi lebih menarik, profesional, dan mudah dipahami.

Saya akan menggunakan format Markdown yang lebih kaya, termasuk badges (lencana), emoji, tabel, dan penekanan pada poin-poin penting untuk memandu pembaca. Ini akan mengubah dokumen Anda dari sekadar teks menjadi ringkasan proyek yang visual dan efektif.

Salin dan tempel seluruh konten di bawah ini untuk menggantikan README.md Anda.

🥗 Analisis Kerawanan Pangan (FIES) di Aceh 2022 📊

![alt text](https://img.shields.io/badge/Python-3.10-blue.svg)
![alt text](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)
![alt text](https://img.shields.io/badge/Pandas-✓-green.svg)
![alt text](https://img.shields.io/badge/Scikit--learn-✓-blueviolet.svg)

Proyek ini menggali data Food Insecurity Experience Scale (FIES) tahun 2022 untuk Provinsi Aceh. Tujuannya adalah untuk membangun model klasifikasi yang dapat memprediksi status kerawanan pangan sebuah rumah tangga dan mengidentifikasi faktor-faktor sosio-ekonomi yang paling berpengaruh.

🎯 Tujuan Utama Proyek

Analisis Deskriptif: Memahami distribusi dan karakteristik kerawanan pangan di Aceh.

Pemodelan Prediktif: Membangun dan membandingkan beberapa model machine learning untuk mengklasifikasikan status kerawanan pangan.

Rekomendasi Kebijakan: Memberikan rekomendasi intervensi yang tepat sasaran berdasarkan faktor-faktor paling signifikan yang ditemukan dari model.

🔑 Hasil Utama (Key Findings)

Model Terbaik: k-Nearest Neighbour (KNN) terpilih sebagai model paling seimbang dengan F1-Score 0.854 dan ROC-AUC 0.631. Model ini mampu membedakan antara rumah tangga rawan dan tidak rawan secara efektif, tidak seperti model lain yang cenderung bias.

Faktor Paling Berpengaruh: Tiga faktor utama yang paling signifikan dalam menentukan status kerawanan pangan adalah:

Umur Kepala Rumah Tangga (KRT)

Luas Lantai Hunian

Status Penerima Bantuan Pemda

📈 Task 1: Statistik Deskriptif

Analisis awal menunjukkan adanya ketidakseimbangan data yang signifikan, di mana ini menjadi dasar pertimbangan penting dalam evaluasi model pada Task 2.

✅ Tidak Rawan: 789 rumah tangga (79.0%) - Kelas Mayoritas

⚠️ Rawan: 210 rumah tangga (21.0%) - Kelas Minoritas

Ini mengindikasikan bahwa metrik Accuracy saja tidak cukup untuk menilai performa model, karena model yang hanya menebak "Tidak Rawan" akan otomatis mendapatkan akurasi ~79%.

🤖 Task 2: Pemodelan Klasifikasi

Empat model klasifikasi dilatih dan dievaluasi. Pemilihan model terbaik didasarkan pada metrik yang seimbang, terutama ROC-AUC (kemampuan membedakan kelas) dan F1-Score (keseimbangan Precision-Recall).

Hasil Evaluasi Model
Model Accuracy F1-Score ROC-AUC Specificity Keterangan
🥇 k-Nearest Neighbour 0.750 0.854 0.631 0.079 Model Terbaik. Paling seimbang.
Naive Bayes 0.300 0.255 0.615 0.857 Performa rendah, tidak cocok.
Decision Tree 0.763 0.864 0.526 0.048 ROC-AUC rendah, hampir setara tebakan acak.
Support Vector Machine 0.790 0.883 0.646 0.000 Ditolak. Sangat bias, gagal total mengidentifikasi kelas 'Tidak Rawan'.
<br>

Visualisasi ROC Curve menunjukkan KNN memiliki kemampuan diskriminatif yang baik di antara model yang tidak bias.

💡 Task 3: Rekomendasi Kebijakan

Berdasarkan analisis Permutation Importance, tiga indikator berikut direkomendasikan sebagai prioritas utama untuk intervensi.

👴 1. Umur Kepala Rumah Tangga (KRT)

Bukti Statistik: Faktor paling berpengaruh dengan importance score 0.0103.

Rekomendasi: Prioritaskan rumah tangga dengan KRT lansia dalam program bantuan sosial (BLT/BPNT) dan kembangkan program pemberdayaan ekonomi ringan yang sesuai untuk mereka.

🏠 2. Luas Lantai Hunian

Bukti Statistik: Faktor terpenting kedua dengan importance score 0.0088.

Rekomendasi: Jadikan Luas_Lantai sebagai kriteria kunci dalam skoring kemiskinan. Program bantuan perbaikan rumah tidak layak huni sangat relevan karena kondisi hunian yang sempit berkorelasi kuat dengan kerawanan pangan.

🏛️ 3. Status Penerima Bantuan Pemda

Bukti Statistik: Faktor terpenting ketiga dengan importance score 0.0065.

Rekomendasi: Evaluasi efektivitas Bantuan Pemda. Signifikansi fitur ini menunjukkan program sudah menyasar kelompok rentan, namun mungkin belum cukup untuk mengeluarkan mereka dari status rawan. Kaji ulang jumlah atau bentuk bantuan agar lebih berdampak.

🛠️ Cara Menjalankan Proyek

Clone repository ini:

code
Bash
download
content_copy
expand_less
git clone https://github.com/username/FIES_Aceh2022.git
cd FIES_Aceh2022

Install library yang dibutuhkan:

code
Bash
download
content_copy
expand_less
pip install pandas numpy matplotlib seaborn scikit-learn

Jalankan Jupyter Notebook:

code
Bash
download
content_copy
expand_less
jupyter notebook FIES.ipynb
💻 Tools yang Digunakan

Python 3.x

pandas & numpy

matplotlib & seaborn

scikit-learn

Jupyter Notebook
