🥗 Analisis Food Insecurity Experience Scale (FIES) – Aceh 2022
📘 Deskripsi Proyek

Proyek ini bertujuan untuk menganalisis kerawanan pangan rumah tangga di Aceh tahun 2022 menggunakan instrumen Food Insecurity Experience Scale (FIES) yang terdiri dari 8 pertanyaan utama (Q1–Q8).
Analisis dilakukan menggunakan Python dengan pendekatan statistik deskriptif, evaluasi reliabilitas, dan pemodelan klasifikasi untuk menentukan faktor utama penyebab kerentanan pangan.

🎯 Tujuan Pembelajaran

Melatih penggunaan Python dalam analisis data survei.

Menerapkan statistik deskriptif dan uji reliabilitas instrumen.

Membangun model klasifikasi untuk memprediksi status kerawanan pangan.

Menginterpretasikan hasil dan memberikan rekomendasi kebijakan berbasis data.

📊 Task 1 – Statistik Deskriptif
Langkah-langkah:

Hitung jumlah dan persentase Status_Rawan dari data FIES Aceh.

Buat visualisasi distribusi status kerawanan pangan menggunakan bar chart.

Interpretasikan hasil secara deskriptif.

Cuplikan Kode:
status_counts = df['Status_Rawan'].value_counts()
status_percent = df['Status_Rawan'].value_counts(normalize=True) \* 100

plt.figure(figsize=(6, 5))
sns.barplot(x=status_counts.index, y=status_counts.values, palette="Set2")
plt.title("Distribusi Status Kerawanan Pangan (FIES Aceh 2022)")
plt.xlabel("Status Rawan Pangan")
plt.ylabel("Jumlah Rumah Tangga")
plt.show()

Interpretasi:

Dari hasil perhitungan, diketahui persentase rumah tangga yang mengalami kerawanan pangan sebesar sekitar XX%, sedangkan yang tidak rawan sekitar YY%.
Hal ini menunjukkan masih terdapat rumah tangga dengan akses pangan terbatas yang perlu menjadi perhatian utama pemerintah daerah.

🤖 Task 2 – Pemodelan Klasifikasi
Langkah-langkah:

Split data menjadi train dan test (80:20).

Gunakan beberapa algoritma klasifikasi:

Naive Bayes (GaussianNB)

Decision Tree

K-Nearest Neighbour

Support Vector Machine

Evaluasi model menggunakan metrik:

Accuracy

Precision

Recall

F1-Score

ROC-AUC

Visualisasikan ROC Curve untuk membandingkan performa antar model.

Tentukan model terbaik berdasarkan F1-score dan AUC tertinggi.

Cuplikan Kode Evaluasi:
for name, model in models.items():
model.fit(X_train_used, y_train)
y_pred = model.predict(X_test_used)
y_prob = model.predict_proba(X_test_used)[:, 1] if hasattr(model, "predict_proba") else model.decision_function(X_test_used)

    result[name] = {
        'model': model,
        'accuracy': accuracy_score(y_test, y_pred),
        'precision': precision_score(y_test, y_pred),
        'recall': recall_score(y_test, y_pred),
        'f1': f1_score(y_test, y_pred),
        'auc': roc_auc_score(y_test, y_prob),
        'y_pred': y_pred,
        'y_prob': y_prob
    }

ROC Curve:
plt.figure(figsize=(10, 7))
for name, data in result.items():
fpr, tpr, \_ = roc_curve(y_test, data['y_prob'])
roc_auc = roc_auc_score(y_test, data['y_prob'])
plt.plot(fpr, tpr, label=f'{name} (AUC = {roc_auc:.2f})')

plt.plot([0, 1], [0, 1], 'k--')
plt.xlabel('False Positive Rate')
plt.ylabel('True Positive Rate')
plt.title('ROC Curve per Model')
plt.legend()
plt.show()

Hasil Ringkasan:
Model Accuracy Precision Recall F1-Score AUC
Naive Bayes 0.XX 0.XX 0.XX 0.XX 0.XX
Decision Tree 0.XX 0.XX 0.XX 0.XX 0.XX
KNN 0.XX 0.XX 0.XX 0.XX 0.XX
SVM 0.XX 0.XX 0.XX 0.XX 0.XX

Model terbaik: Decision Tree (F1 dan AUC tertinggi).

🧠 Task 3 – Rekomendasi Kebijakan
Identifikasi Indikator Utama:

Setelah model terbaik ditentukan, dilakukan analisis feature importance menggunakan Permutation Importance:

best_model = result[best_model_name]['model']
perm = permutation_importance(best_model, X_test, y_test, n_repeats=20, random_state=42)

feat_imp = pd.DataFrame({
'feature': X_test.columns,
'importance': perm.importances_mean
}).sort_values('importance', ascending=False)

print(feat_imp.head(10))

📈 Top 3 indikator paling berpengaruh:

Q5 – Frekuensi makan berkurang karena kekurangan makanan

Q3 – Kekurangan makanan bergizi

Q1 – Kekhawatiran kehabisan makanan

💡 Rekomendasi Kebijakan:

Program peningkatan akses pangan
Fokus pada rumah tangga dengan keterbatasan jumlah konsumsi (indikator Q5).
Intervensi dapat berupa subsidi pangan lokal dan dukungan distribusi bahan pokok.

Edukasi gizi dan pola makan sehat
Untuk menurunkan risiko Q3, pemerintah dapat memperkuat program penyuluhan pangan bergizi di desa-desa.

Sistem peringatan dini kerawanan pangan
Gunakan Q1 (kekhawatiran kehabisan makanan) sebagai indikator awal untuk memetakan potensi krisis pangan sebelum terjadi.

⚙️ Tools dan Library

Python 3.x

pandas, numpy, matplotlib, seaborn

scikit-learn (sklearn)

Jupyter Notebook

🧾 Kesimpulan

Model terbaik: Decision Tree

Akurasi tertinggi: XX%

F1-score & AUC terbaik: Decision Tree menunjukkan performa paling stabil.

Tiga indikator utama: Q5, Q3, dan Q1 menjadi fokus intervensi kebijakan pangan Aceh.

📁 Struktur Project
FIES_Aceh2022/
│
├── FIES_Aceh2022_999.csv # Dataset utama
├── FIES.ipynb # Notebook analisis utama
├── README.md # Dokumentasi proyek (file ini)

💡 Rekomendasi Kebijakan
🥦 1. Program Peningkatan Akses Pangan

Fokus pada rumah tangga dengan umur kepala rumah tangga lebih tua dan keterbatasan konsumsi.
Intervensi dapat berupa subsidi pangan lokal serta peningkatan distribusi bahan pokok di wilayah terpencil.

💧 2. Perbaikan Akses Air Minum Layak

Sumber air minum yang tidak layak menjadi faktor penting dalam kerentanan pangan.
Pemerintah perlu memperkuat program air bersih melalui pembangunan infrastruktur dan edukasi sanitasi.

🔥 3. Substitusi Energi Masak Aman dan Terjangkau

Penggunaan bahan bakar masak yang tidak efisien meningkatkan kerentanan pangan.
Program konversi energi bersih (seperti LPG atau biogas) dapat mengurangi beban rumah tangga miskin.
