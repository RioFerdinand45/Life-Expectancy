# Klasifikasi Binary

- Cars Purchase Decision Dataset : https://www.kaggle.com/datasets/gabrielsantello/cars-purchase-decision-dataset

  Dataset ini berisi informasi mengenai karakteristik konsumen dan keputusan mereka dalam membeli mobil. Setiap baris merepresentasikan seorang konsumen. Informasi tersebut dapat digunakan untuk mempelajari hubungan antara usia, jenis kelamin, dan pendapatan tahunan dengan keputusan pembelian mobil. Targetnya adalah kolom purchased dimana 0 = tidak membeli mobil 1 = membeli mobil

- Play Badminton Dataset : https://www.kaggle.com/datasets/aditya0kumar0tiwari/play-badminton

  Dataset ini berisi informasi mengenai kondisi cuaca yang digunakan untuk menentukan apakah seseorang akan bermain badminton atau tidak. Targetnya adalah kolom play dimana yes = menandakan bermain badminton, sedangkan no = tidak bermain badminton

- Immigration Madrid 2021 Dataset : https://www.kaggle.com/datasets/rober2598/immigration-madrid-2021

  Dataset ini berkaitan dengan data imigrasi di Madrid, Spanyol, pada tahun 2021. yang berisi data gender, umur, studies, nationality, administrative_situation, dan working. Targetnya adalah kolom working dimana ketika yes = menandakan dia bekerja, sedangkan no = dia tidak bekerja

# Klasifikasi Multi Label

- Multi-Labelled SMILES Odors Dataset : https://www.kaggle.com/datasets/aryanamitbarsainyan/multi-labelled-smiles-odors-dataset

  Dataset ini berisi informasi struktur molekul kimia menggunakan format SMILES (Simplified Molecular Input Line Entry System) yang dikaitkan dengan karakteristik bau atau aroma suatu senyawa. Targetnya bukan hanya satu kolom kelas, melainkan sekumpulan label aroma yang dapat aktif secara bersamaan. 138 odor descriptors Jadi ketika ada molukel A pada kolom fruity bisa di kira kalau 0 = berarti bukan baunya kalau 1 = berarti baunya menyerupai

- Multi-Label Classification Dataset : https://www.kaggle.com/datasets/shivanandmn/multilabel-classification-dataset

  Dataset ini berisi kumpulan abstrak atau ringkasan penelitian ilmiah yang dikategorikan berdasarkan bidang ilmu pengetahuan. Setiap dokumen penelitian dapat memiliki lebih dari satu kategori bidang ilmu. Contohnya, penelitian yang membahas penerapan machine learning dalam bidang kesehatan dapat berkaitan dengan Computer Science sekaligus Quantitative Biology. Targetnya adalah enam kategori bidang ilmu sebagai label seperti Computer Science, Fisika, Matematika, Statistika, Biologi Kuantitatif, Keuangan Kuantitatif. Jadi ketika ada judul penelitian seperti " Statistical Modeling for Data Analyst machine akan melabeli peneletian tersebut yaitu penelitian statistika

- App/ Software Category (Multi-Label) Dataset : https://www.kaggle.com/datasets/aklimarimi/multi-label-classifier-dataset

  Dataset ini berisi informasi aplikasi atau perangkat lunak yang dikategorikan berdasarkan deskripsi dan jenis aplikasinya. Tujuannya adalah memprediksi kategori yang sesuai berdasarkan deskripsi suatu aplikasi. Misalnya, sebuah aplikasi dapat memiliki karakteristik yang berhubungan dengan beberapa kategori sekaligus. Targetnya adalah kategori aplikasi atau software (Software Category). Contoh ada aplikasi pengelolaan tugas ada 3 label yaitu productivity, education, business, dimana 0 = tidak masuk kriteria, dan 1 = masuk kriteria, berarti aplikasi tersebut berlabel productivity = 1, education = 0, business = 0

# Klasifikasi Multi Class

- Diabetes Dataset : https://www.kaggle.com/datasets/yasserhessein/multiclass-diabetes-dataset

  Dataset ini berisi informasi kesehatan pasien yang dapat digunakan untuk mengklasifikasikan status diabetes berdasarkan karakteristik demografis dan hasil pemeriksaan laboratorium. Informasi yang digunakan mencakup usia, jenis kelamin, BMI, kolesterol, trigliserida, HbA1c, dan beberapa parameter kesehatan lainnya. Targetnya kolom class ada tiga kategori target N = Non-Diabetic, P = Predict-Diabetic, Y = Diabetic

- Weather Condition Dataset : https://www.kaggle.com/datasets/nasiruddin123/weather-conditions-dataset

  Dataset ini berkaitan dengan kondisi cuaca dan dapat digunakan untuk membangun model yang mengklasifikasikan keadaan cuaca berdasarkan informasi atau karakteristik yang tersedia. Dalam permasalahan klasifikasi cuaca, atribut yang mungkin digunakan antara lain suhu, kelembapan, kecepatan angin, tekanan udara, dan curah hujan. Targetnya adalah prediksi weather condition dimana ada Sunny, Cloudy, Rainy, Cold, Hot, dll

- Car Body Type Images Dataset : https://www.kaggle.com/datasets/ademboukhris/cars-body-type-cropped

  Dataset berisi gambar mobil yang dikelompokkan berdasarkan tipe atau bentuk bodi kendaraan. Struktur folder dataset dapat digunakan sebagai label kelas untuk proses supervised image classification. Berdasarkan informasi referensi mengenai dataset ini, kategori yang ditemukan mencakup SUV, VAN, SEDAN, HATCHBACK, dan PICK UP. Targetnya class gambar, ada SUV, VAN, SEDAN, HATCHBACK, PICK UP
