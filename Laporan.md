# Laporan Proyek Machine Learning - Marsella Vindriani

## Domain Proyek

Proyek ini menggunakan model pembelajaran mesin untuk sistem rekomendasi film yang berisi penilaian bintang 5 dari pengguna.

Dataset ini berisi 100836 penilaian dan 3683 penanda/tag di seluruh 9742 film, dibuat oleh 610 pengguna antara 29 Maret 1996 dan 24 September 2018. Dataset ini buat pada 26 September 2018.


## Latar Belakang
Sistem rekomendasi adalah sistem yang memprediksi rating atau preferensi pengguna terhadap item tertentu. Rekomendasi ini dibuat berdasarkan perilaku pengguna di masa lalu atau perilaku pengguna lainnya. Jadi, sistem ini akan merekomendasikan sesuatu terhadap pengguna berdasarkan data perilaku atau preferensi dari waktu ke waktu.

Dalam penelitian ini, dataset MovieLens digunakan sebagai studi kasus untuk mengevaluasi dan membandingkan kedua pendekatan tersebut. Dataset ini, yang berisi data rating dan tag film dalam jumlah besar, memungkinkan analisis akurasi sistem rekomendasi serta kemampuan dalam menangani tantangan seperti cold start dan sparsity. Penelitian ini bertujuan untuk meningkatkan pengalaman pengguna dengan memastikan rekomendasi yang relevan dan sesuai dengan preferensi mereka.
  
  
## Business Understanding

### Problem Statements
berdasarkan latar belakang diatas, berikut ini rumusan masalah yang dapat diselesaikan pada proyek ini:

1. Apa saja faktor-faktor yang mempengaruhi efektivitas sistem rekomendasi film pada dataset ini?
2. Bagaimana cara untuk membuat model content-based filtering dalam merekomendasikan film yang relevan kepada pengguna?
3. Bagaimana cara untuk membuat model collaborative filtering dalam merekomendasikan film yang relevan kepada pengguna?
4. Jika dibandingkan kedua model, manakah yang lebih efektif dalam merekomendasikan film?

### Goals
Goals Tujuan dari proyek ini dirancang untuk menjawab problem statements di atas dengan cara sebagai berikut:

1. Mengidentifikasi dan menganalisis faktor-faktor yang mempengaruhi efektivitas kedua metode rekomendasi pada dataset MovieLens.
2. Mengetahui cara membuat model content-based filtering dalam merekomendasikan film yang relevan kepada pengguna
3. Mengetahui cara membuat model collaborative filtering dalam merekomendasikan film yang relevan kepada pengguna
4. Mengetahui model mana yang lebih efektif dalam merekomendasikan film

### Solution Statements
Solusi yang dapat dilakukan untuk memenuhi tujuan dari proyek ini diantaranya :

1. Melakukan analisis eksploratif data untuk memahami distribusi rating dan karakteristik film yang ada dalam dataset MovieLens.
2. Menerapkan content-based filtering dengan memanfaatkan fitur konten film, seperti genre dan tag.
3. Menerapkan collaborative filtering dengan memanfaatkan informasi rating dari pengguna.



## Data Understanding
Tahap ini memberikan informasi seperti jumlah data, kondisi data, dan informasi mengenai data yang digunakan, tautan sumber data (link download), dan menguraikan seluruh variabel atau fitur pada data.
## Dataset
| Jenis | Keterangan |
| ------ | ------ |
| Sumber | [MovieLens Dataset](https://files.grouplens.org/datasets/movielens/ml-latest-small.zip)|
| Lisensi |Public Domain|
| Kategori | Film|


### Isi Dataset
Dataset MovieLens ini terbagi menjadi beberapa dataset, antara lain:
- ratings.csv: Semua penilaian terkandung di file ini, dengan skala penilaian 5 bintang dengan peningkatan setengah bintang.
- tags.csv: Semua tag terkandung dalam file ini, mewakili tag yang diterapkan pada film oleh pengguna.
- movies.csv: Informasi film terkandung dalam file ini, termasuk judul film dan genre.
- links.csv: Pengenal yang dapat digunakan untuk menghubungkan ke sumber data film lainnya terkandung dalam file ini.

**1. Dataset ratings**

![image](https://github.com/user-attachments/assets/f0a6a80a-8f6c-4a99-827a-0f4892531f35)


![image](https://github.com/user-attachments/assets/3cacd269-3967-43e5-b983-2eaf25129e80)

![image](https://github.com/user-attachments/assets/bcdaa538-a48b-4f36-8385-a1ef338c9224)

Dari grafik, terlihat bahwa rating dengan nilai 4.0 adalah yang paling sering diberikan, sesuai dengan nilai modus yang kita hitung sebelumnya. Rating dengan nilai 3.0 dan 4.0 menjadi nilai tertinggi yang menunjukkan bahwa kebanyakan film menerima penilaian positif dari pengguna. Distribusi rating menunjukkan kecenderungan pengguna untuk memberikan rating yang lebih tinggi, dengan jumlah rating yang lebih rendah (seperti 0.5 dan 1.0) jauh lebih sedikit dibandingkan dengan rating tinggi.

![image](https://github.com/user-attachments/assets/cc15e739-f5d9-4856-8c11-34517aa72eaf)

Visualisasi dan analisis rating rata-rata per genre film menunjukkan:
+Film-Noir, War, dan Documentary adalah genre dengan rating rata-rata tertinggi, menunjukkan bahwa film-film dalam genre ini cenderung sangat dihargai oleh pengguna.
Di sisi lain, Comedy dan Horror memiliki rating rata-rata yang lebih rendah dibandingkan dengan genre lain, meskipun perbedaan rating antar genre tidak terlalu signifikan.
Drama dan Crime, yang merupakan dua genre paling populer berdasarkan frekuensi, juga memiliki rating rata-rata yang cukup tinggi, menegaskan popularitas dan apresiasi mereka di kalangan pengguna.
Genre (no genres listed), meskipun memiliki jumlah film yang relatif rendah, menunjukkan rating rata-rata yang sebanding dengan genre populer lainnya.

**Rata-rata rating per Film**


![image](https://github.com/user-attachments/assets/dc623403-6a0b-4561-9e38-151612d2d32e)


**2. Dataset tags**

![image](https://github.com/user-attachments/assets/1f8a73f6-7420-4321-8cc6-12f137bd9d4e)

![image](https://github.com/user-attachments/assets/0a9fffcc-0ff0-42e7-a4a9-c82ab31501b9)



![image](https://github.com/user-attachments/assets/df589ca8-711e-4da5-ad85-e67dde77bd1b)
Visualisasi dan daftar 20 tag paling populer menunjukkan:

In Netflix queue adalah tag paling populer, dengan jauh melebihi frekuensi tag lainnya. Ini menunjukkan ketertarikan pengguna untuk menandai film yang mereka ingin tonton di Netflix.
Tag seperti atmospheric, thought-provoking, dan superhero juga populer, mencerminkan apresiasi pengguna terhadap suasana film, konten yang memicu pemikiran, dan genre superhero.
Disney, surreal, dan funny termasuk dalam tag populer lainnya, menunjukkan ketertarikan pengguna pada film-film dengan elemen fantasi, humor, atau yang diproduksi oleh Disney.
Tag seperti religion, sci-fi, crime, dan politics menunjukkan ketertarikan pengguna pada tema-tema spesifik dalam film.

**3. Dataset movies**

![image](https://github.com/user-attachments/assets/b14d13c4-0ee3-44ec-8d7c-ec4bba0b6a50)

![image](https://github.com/user-attachments/assets/d8fcd5de-de4c-4145-a61c-d1ea3bcc7b27)



**4. Dataset links**

![image](https://github.com/user-attachments/assets/a9341046-6bc8-467b-a09d-8833b9fca896)

![image](https://github.com/user-attachments/assets/10f8b256-8756-4940-a35e-f21db7ffbbe4)





Seluruh dataset tidak memiliki missing value, duplikat, dan outlier



## Data Preparation
Tahapan data preparation sistem rekomendasi yang menggunakan dataset MovieLens pada proyek ini meliputi langkah-langkah berikut, dirancang untuk mempersiapkan dan memproses data agar sesuai dengan kebutuhan analisis dan pemodelan:

1. Menggabungkan Data Movies dengan Tags
   Data dari tabel movies dan tags digabungkan berdasarkan movieId. Untuk film yang tidak memiliki tag, nilai NaN pada kolom tag digantikan dengan string kosong. Tujuan menggabungkan ini memperkaya informasi setiap film dengan detail tambahan dari tag, memungkinkan sistem rekomendasi berbasis konten untuk lebih akurat dalam menilai kesamaan antar film berdasarkan konten dan preferensi pengguna.
2. Membuat Kolom Combined Features
   Kolom combined_features dibuat dengan menggabungkan informasi dari kolom genres dan tag, menggunakan | sebagai pemisah. Ini bertujuan untuk memfasilitasi pembuatan vektor fitur dari teks untuk analisis kesamaan, yang krusial dalam sistem rekomendasi berbasis konten. Ini membantu model dalam memahami dan membandingkan kompleksitas konten film secara lebih efektif.
3. Encoding untuk Collaborative Filtering
   userId dan movieId diubah menjadi urutan angka berurutan dengan menggunakan .astype('category').cat.codes. Proses ini juga melibatkan pembuatan pemetaan ulang antara kode kategori dengan ID asli. Encoding ini menyederhanakan data dan mengurangi kompleksitas komputasional, memungkinkan algoritma collaborative filtering untuk lebih efisien dalam memproses data. Ini penting untuk teknik embedding yang digunakan dalam model collaborative filtering, yang membutuhkan input numerik.
4. Pembagian Data untuk Training dan Validasi
   Data dibagi menjadi set pelatihan dan validasi menggunakan train_test_split, dengan proporsi tertentu dari data dialokasikan untuk validasi. Pembagian ini memastikan bahwa model dapat diuji pada data yang belum pernah dilihat sebelumnya, mengukur kemampuan model dalam memprediksi rating dengan akurat pada situasi nyata. Hal ini membantu dalam mengidentifikasi dan mengatasi overfitting.
5. Persiapan model:
- Mengonversi combined_features menjadi matriks vektor dengan menggunakan TF-IDF Vectorizer.
- Menghitung skor kesamaan antar film dengan menggunakan cosine similarity.
- Mengembangkan fungsi yang menerima judul film sebagai input dan mengembalikan rekomendasi film serupa.

Setiap tahapan data preparation ini untuk memastikan bahwa data yang digunakan dalam pemodelan sistem rekomendasi bersih, konsisten, dan siap untuk analisis lebih lanjut. Langkah-langkah ini dirancang untuk memaksimalkan efektivitas model rekomendasi baik dalam pendekatan berbasis konten maupun collaborative filtering.

![image](https://github.com/user-attachments/assets/9015f147-a98d-4548-8adf-88fb5fcef156)

## Modeling and Result
Melakukan modeling terhadap data dengan 2 metode sistem rekomendasi untuk mengetahui sistem rekomendasi mana terbaik terhadap dataset ini.
Adapun sistem rekomendasi yang digunakan antara lain : Content-Based Filtering dan Collaborative Filtering

### Content Based Filtering
- Pembuatan Model: Menggunakan TF-IDF Vectorizer untuk mengonversi combined_features menjadi matriks fitur dan menghitung cosine similarity antara film-film berdasarkan matriks tersebut. Sistem kemudian merekomendasikan film yang memiliki kesamaan konten tertinggi dengan film yang disukai pengguna.
- Output: Top-N rekomendasi disajikan berdasarkan skor kesamaan tertinggi.
- Kelebihan:
  1. Rekomendasi sangat personal dan relevan dengan preferensi spesifik pengguna berdasarkan konten.
  2. Sistem tetap efektif bahkan dengan jumlah pengguna yang terbatas.
Kekurangan:
  1. Terbatas pada konten yang mirip dengan apa yang sudah diketahui; dapat menghasilkan rekomendasi yang monoton.
  2. Tidak mempertimbangkan pendapat atau preferensi pengguna lain, yang bisa membatasi keragaman rekomendasi.



### Mendapatkan Rekomendasi

![image](https://github.com/user-attachments/assets/aa7d7185-b7d7-4299-bdee-a1ed69ec3a17)



### Collaborative Filtering
- Pembuatan Model: Menggunakan teknik Deep Learning dengan TensorFlow dan Keras untuk membangun model yang memprediksi rating film berdasarkan histori interaksi antara pengguna dan film. Model memanfaatkan struktur embedding untuk pengguna dan film, serta menggunakan input dari userId dan movieId.
- Output: Sistem merekomendasikan Top-N film yang belum ditonton oleh pengguna berdasarkan prediksi rating tertinggi.
- Kelebihan:
  1. Mampu mengidentifikasi pola dan preferensi tersembunyi yang mungkin tidak terlihat dalam konten film itu sendiri, menawarkan rekomendasi yang lebih beragam.
  2. Dapat meningkatkan dengan penambahan data; semakin banyak interaksi yang dianalisis, semakin akurat rekomendasinya.
- Kekurangan:
  1. Memerlukan data yang cukup besar untuk pelatihan model agar efektif, dikenal sebagai masalah cold start.
  2. Kompleksitas komputasi lebih tinggi dibandingkan content-based filtering, membutuhkan sumber daya komputasi yang lebih besar.
  3. Kedua pendekatan memiliki tempatnya masing-masing dalam ekosistem rekomendasi, dengan pilihan antara keduanya bergantung pada konteks aplikasi dan ketersediaan data.
  4. Membuat model sistem rekomendasi film dengan menggunakan TensorFlow dan Keras. Fungsi RecommenderNet dari Keras mendefinisikan model untuk memprediksi rating film berdasarkan interaksi antara pengguna dan film.

Proses hyperparameter training dilakukan dengan epochs 10


### Mendapatkan Rekomendasi

![image](https://github.com/user-attachments/assets/b22b0a84-ab50-4826-9990-50c40ee112c1)




Sehingga : 

- Content-Based Filtering lebih cocok untuk aplikasi yang kontennya sangat spesifik dan personalisasi yang mendalam sangat penting, atau ketika informasi tentang preferensi pengguna lebih mudah diakses daripada data interaksi pengguna lain.
- Collaborative Filtering cocok untuk platform dengan banyak pengguna dan interaksi, di mana dapat memanfaatkan pola besar tersebut untuk menghasilkan rekomendasi yang relevan dan beragam.


## Evaluation
Untuk evaluasi model Content Based Filtering digunakan metrik precision yang mengukur proporsi rekomendasi yang relevan terhadap jumlah total rekomendasi yang diberikan. Rumusnya adalah:

![image](https://github.com/user-attachments/assets/fc6206a6-b96c-48f1-8456-4d824915e475)


Sedangkan dalam evaluasi model Collaborative Filtering yang dikembangkan menggunakan TensorFlow dan Keras, Mean Square Error (MSE) digunakan sebagai metrik utama untuk mengukur akurasi prediksi model terhadap rating yang sebenarnya. MSE memberikan gambaran kuantitatif mengenai tingkat kesalahan prediksi model dalam mengestimasi rating film, dengan fokus pada bagaimana model mampu meminimalkan kesalahan tersebut sepanjang proses pelatihan dan validasi.

MSE dihitung menggunakan rumus berikut:

![image](https://github.com/user-attachments/assets/632f562b-14ce-407b-b791-0cf5c611a3e4)


Selama pelatihan, model dijalankan melalui beberapa epoch, dimana setiap epoch merupakan satu siklus di mana seluruh dataset training dilewati oleh model. Dalam proses ini, RMSE dihitung untuk setiap batch data sebagai indikator kinerja model. Model bertujuan untuk meminimalkan nilai RMSE dengan mengadjust bobotnya berdasarkan backpropagation dan optimasi gradient descent. Hasil pelatihan divisualisasikan dalam bentuk grafik yang menampilkan Training Loss dan Validation Loss mengilustrasikan perubahan nilai RMSE selama proses pelatihan untuk dataset training dan validation. Grafik ini penting karena memberikan gambaran tentang:

1. Peningkatan Akurasi Prediksi
   Penurunan RMSE menunjukkan peningkatan kemampuan model dalam memprediksi rating yang akurat.
2. Deteksi Overfitting
   Jika Validation Loss mulai meningkat sementara Training Loss terus menurun, ini menandakan model mulai overfit terhadap training data dan performanya pada data baru (validation data) mulai menurun.
Kesimpulan Hasil evaluasi model Content Based Filtering mempunyai nilai precision yang sempurna (1) menandakan bahwa semua rekomendasi yang diberikan relevan. Meskipun pada pandangan pertama ini bisa dianggap sebagai indikasi sukses total, tetap harus mempertimbangkan potensi bias dalam evaluasi atau kurangnya variasi dalam skenario pengujian.

Sedangkan hasil Collaborative Filtering menggunakan Mean Squared Error (MSE) sebagai metrik seperti gambar berikut, teramati penurunan yang konsisten dalam loss pelatihan dan validasi selama iterasi, yang menandakan peningkatan kemampuan prediktif model. Penurunan ini mencapai stabilitas tanpa adanya divergensi antara keduanya, mengindikasikan bahwa model telah menghindari overfitting, yang sering menjadi tantangan dalam sistem rekomendasi.

### Visualisasi Metrik
![image](https://github.com/user-attachments/assets/4a0c183f-9c4b-462d-8726-ce72abe5b91c)


Secara lebih khusus, loss validasi konvergen ke nilai yang dekat dengan loss pelatihan, mendekati nilai 0.9. Ini menunjukkan bahwa model mampu melakukan generalisasi dari data yang dilihat selama pelatihan ke data yang tidak dikenal, yang tercermin dalam dataset validasi.
Melihat kembali pernyataan masalah dan tujuan dari proyek ini, yang bertujuan untuk memberikan rekomendasi yang relevan dan personal kepada pengguna, hasil yang diperoleh menunjukkan kesuksesan terhadap pencapaian tujuan tersebut. Namun, untuk menyelesaikan masalah yang diangkat dengan lebih komprehensif, direkomendasikan untuk melakukan pengujian lebih lanjut, khususnya dalam setting yang lebih beragam dan dengan kasus penggunaan yang lebih luas. Proyek ini telah berhasil menjawab pertanyaan-pertanyaan yang diajukan dalam pernyataan masalah dengan memanfaatkan dataset MovieLens untuk membangun dan mengevaluasi model rekomendasi berbasis content-based filtering dan collaborative filtering. Faktor-faktor yang mempengaruhi efektivitas model rekomendasi teridentifikasi melalui analisis eksploratif yang mendalam, yang mencakup distribusi rating dan analisis genre serta tag dari film.
Hasil analisis ini telah membantu dalam pembuatan fitur dan pemahaman konten yang relevan dengan preferensi pengguna. Kedua model rekomendasi yang dikembangkan menunjukkan kemampuan untuk merekomendasikan film yang relevan kepada pengguna. Model content-based filtering terutama efektif dalam merekomendasikan film dengan konten yang serupa dengan preferensi pengguna sebelumnya, sementara model collaborative filtering memanfaatkan pola rating dari banyak pengguna untuk mengidentifikasi film yang mungkin disukai oleh pengguna tertentu, meskipun pengguna tersebut belum pernah menilai film yang serupa.

**---Terima kasih---**

