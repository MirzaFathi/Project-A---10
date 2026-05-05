# Analisis Sentimen pada Pengaruh Tiktok Shop pada UMKM Menggunakan NLP
Written by: Mirza Fathi Taufiqurrahman (5026231105), M Faiza Fachra Azizi (5026231126), Ida Bagus A (5026231120), Ibrahim Amar Alfanani (5026231195), Hizkia Crisantino (5026231040)

# 📕Introduction 
Topik yang dipilih pada penelitian ini adalah pengaruh dari Tiktok Shop terhadap UMKM mulai dari regulasinya, dampak dari segi bisnis, dan strateginya. Sehingga kami mencoba mengumpulkan data yaitu artikel terkait Tiktok Shop yang berkaitan dengan UMKM.

Ekosistem perdagangan digital di Indonesia tengah mengalami pergeseran paradigma dengan hadirnya fenomena social commerce, khususnya melalui platform TikTok Shop. Relevansi topik ini terletak pada kemampuannya mengubah perilaku belanja konsumen dari pencarian produk secara aktif menjadi konsumsi konten yang interaktif melalui video pendek dan live streaming. Mengingat Indonesia merupakan salah satu pasar TikTok terbesar di dunia, integrasi fitur belanja langsung ini menciptakan dualitas dampak: di satu sisi menawarkan peluang digitalisasi yang cepat bagi pelaku usaha, namun di sisi lain menimbulkan disrupsi masif terhadap pelaku UMKM tradisional. Dinamika ini mencapai puncaknya pada intervensi regulasi pemerintah melalui Permendag No. 31 Tahun 2023, yang menjadikan analisis terhadap pengaruh TikTok Shop sebuah isu krusial untuk menentukan masa depan ketahanan ekonomi kerakyatan di era transformasi digital.

Berdasarkan fenomena tersebut, kelompok kami merumuskan pertanyaan riset utama: "Bagaimana pola sentimen publik dan pelaku UMKM di media sosial terhadap kehadiran TikTok Shop di Indonesia, dan sejauh mana narasi digital tersebut mencerminkan keberhasilan atau tantangan transformasi digital bagi pengusaha kecil?" Alasan utama kelompok kami memutuskan untuk meneliti hal ini adalah karena melimpahnya data tekstual tidak terstruktur di media sosial yang mencerminkan opini jujur masyarakat. Hal ini memberikan peluang ideal untuk mengimplementasikan teknik Natural Language Processing (NLP) melalui Google Colab, seperti Sentiment Analysis dan Topic Modeling. Kami ingin melihat apakah data tersebut menunjukkan dukungan terhadap efisiensi digital atau justru kekhawatiran terhadap persaingan harga yang tidak sehat, sehingga riset ini dapat memberikan wawasan berbasis data bagi para pengambil kebijakan.

Urgensi masalah ini didukung oleh sejumlah studi terindeks Scopus yang memperkuat relevansi topik dan pendekatan metodologis penelitian ini. Pertama, (Wirdiyanti R. & Yusgiantoro I., 2023) dalam jurnal Electronic Commerce Research (Springer) membuktikan bahwa adopsi e-commerce oleh UMKM di Indonesia secara signifikan meningkatkan kinerja bisnis dan inklusi keuangan, namun masih terkendala oleh rendahnya literasi digital dan keterbatasan infrastruktur teknologi. Temuan ini menjustifikasi mengapa transisi UMKM ke platform berbasis social commerce seperti TikTok Shop merupakan isu strategis yang mendesak untuk dikaji, khususnya dalam konteks kesiapan pelaku usaha kecil menghadapi ekosistem platform baru. Kedua, (Wongkitrungrueng A. & Assarut N., 2020) dalam Journal of Business Research (Elsevier, Scopus Q1) menunjukkan bahwa live streaming merupakan mekanisme utama dalam membangun kepercayaan konsumen dan mendorong keterlibatan dalam transaksi social commerce. Relevansi studi ini sangat langsung terhadap penelitian kami, mengingat fitur live streaming TikTok Shop merupakan salah satu term paling dominan yang muncul dalam analisis TF-IDF (term live mendominasi periode 2025-Q3), mengindikasikan bahwa dinamika live commerce menjadi inti narasi pemberitaan pada fase adoptif. Ketiga, Tatik dan Setiawan (2024) dalam Asia Pacific Journal of Marketing and Logistics (Tatik D. & Setiawan D., 2024) secara spesifik menganalisis pengaruh social media marketing terhadap kinerja UMKM di Indonesia, dan menemukan bahwa faktor kepercayaan dan persepsi kemudahan penggunaan platform merupakan prediktor utama adopsi. Hasil ini memperkuat basis teoritis mengapa analisis sentimen terhadap narasi media—yang mencerminkan persepsi publik—memiliki implikasi langsung bagi pengambilan keputusan pelaku UMKM.

# 📕Data
# Data Acquisition
Data diambil dengan script python dengan modul scriptparser dan newspaper3k serta beautifulsoup melalui google colab. Lalu menggunakan filter queries untuk mencari artikel terkait, diantaranya ""TikTok Shop Indonesia", "TikTok Shop UMKM", "TikTok Shop regulasi", "Dampak TikTok Shop", "UMKM Bangkrut", "TikTok Shop UMKM gulung tikar", "TikTok Shop bunuh UMKM", "Tiktok UMKM".

Metode Pengumpulan:
1. Penarikan (Web Scraping): Menggunakan script untuk menelusuri berita yang mengandung kata kunci spesifik
2. Ekstraksi Teks (Parsing): Dari halaman web yang ditemukan, elemen HTML ditarik untuk mengambil metadata dan konten berita, yang kemudian dimasukkan ke dalam kolom title, source, undirect link, published, dan content.
3. Pembersihan Awal (Basic Preprocessing): Menyusun data mentah yang berhasil ditarik ke dalam format tabular baris dan kolom yang rapi agar siap untuk dilabeli.
4. Pemberian Label (Manual Labeling): Melakukan analisis pada kolom title dan content untuk menentukan nilai pada kolom category (topik pembahasan) dan sentimen (nada pemberitaan).

# Datasets Definition
Dataset yang digunakan untuk analisis ini berupa kumpulan artikel terkait TikTok Shop, dinamika e-commerce, UMKM, dan regulasi di Indonesia, yang telah dilabeli berdasarkan kategori topik dan sentimennya.

Struktur dari dataset ini adalah:
- title: Judul artikel
- source: Source artikel
- link: Link artikel
- published: Tanggal dan waktu publish
- content: Isi/text dari artikel
- sentimen: Terbagi berdasarkan nada artikel
- tag: kategori artikel
  terbagi jadi 6 tag:

| Kategori | Deskripsi |
| :--- | :--- |
| **Regulasi** | Berita seputar aturan pemerintah, pajak, audit, izin operasional, denda KPPU, dan kepatuhan terhadap hukum Indonesia. |
| **Bisnis** | Berita tentang angka penjualan, profit, investasi, akuisisi/merger (GoTo & TikTok), pangsa pasar, dan persaingan antar platform (Shopee vs TikTok). |
| **Edukasi** | Berita tentang pelatihan, workshop, webinar, tips jualan, dan pengembangan talenta (seperti pelatihan Live Host). |
| **Event** | Berita seputar agenda resmi, pameran, summit, dan kampanye promosi musiman (Harbolnas, Ramadan, Tanggal Kembar). |
| **Isu** | Berita tentang masalah, kabar negatif, atau kontroversi (PHK massal, barang impor ilegal, penipuan, keluhan pedagang soal biaya admin). |
| **Strategi** | Berita tentang langkah taktis perusahaan atau tips sukses penjual untuk masa depan (biasanya mengandung kata "Sinergi", "Pacu", "Dongkrak", atau "Langkah"). |

# Dataset Preparation and Dataset Preprocessing
Data teks mentah (raw text) yang terdapat pada kolom content belum dapat dianalisis secara komputasional karena memiliki variasi format, imbuhan, dan tanda baca yang kompleks. Oleh karena itu, diterapkan tahapan Data Preprocessing yang berurutan untuk menstandarkan teks, mengurangi noise, dan mengecilkan dimensi fitur kata tanpa menghilangkan makna semantiknya. Tahapan ini dilakukan menggunakan bahasa pemrograman Python dengan bantuan pustaka NLP khusus bahasa Indonesia (seperti Sastrawi) dan NLTK.

Langkah-langkah dalam pra-pemrosesan data meliputi:

1. Penyeragaman Huruf (Case Folding)
Langkah pertama adalah menstandarkan seluruh karakter teks di dalam dokumen menjadi huruf kecil (lowercase). Pada tahap ini juga, elemen-elemen pengganggu (seperti angka, tanda baca, simbol khusus, dan tautan URL yang tersisa) umumnya dibersihkan menggunakan Regular Expression (Regex), sehingga hanya menyisakan karakter alfabet murni.

2. Pemotongan Teks (Tokenization)
Setelah teks bersih dan seragam, dilakukan tokenization, yaitu proses memecah rentetan kalimat panjang menjadi unit-unit kata yang berdiri sendiri (disebut token). Pemisahan ini umumnya menggunakan spasi (whitespace) sebagai pemisah (delimiter).

3. Penghapusan Kata Hubung (Stopword Removal)
Dalam tata bahasa Indonesia, terdapat banyak kata fungsional yang sangat sering muncul namun tidak membawa informasi kontekstual yang signifikan untuk analisis sentimen atau topik. Kata-kata ini disebut stopwords, seperti "dan", "di", "ke", "yang", "untuk", "dari", atau "ini". Jika tidak dihapus, kata-kata ini akan mendominasi hasil analisis dan menutupi kata-kata kunci  yang sebenarnya penting.

4. Pengembalian Kata Dasar (Stemming)
Teks berita sering kali menggunakan bahasa formal yang kaya akan imbuhan, baik awalan, sisipan, maupun akhiran. Tahap stemming bertujuan untuk memotong seluruh imbuhan tersebut dan mengembalikan setiap kata ke bentuk dasarnya. Dengan mengembalikan kata menjadi bentuk dasar, sistem dapat mengelompokkan variasi kata yang memiliki makna identik, sehingga meningkatkan akurasi pembobotan kata dalam analisis selanjutnya.

# 📕Analysis TF-IDF
Analisis Term Frequency-Inverse Document Frequency (TF-IDF) dilakukan untuk mengekstrak dan mengevaluasi kata-kata yang paling signifikan dalam korpus berita. Analisis ini dieksplorasi melalui beberapa dimensi untuk menangkap konteks secara utuh:  

Analisis Keseluruhan (Overall): Didominasi oleh kluster aktivitas ekonomi (jual, produk, usaha, pasar), regulasi (dagang, atur, perintah).  

Analisis Temporal (Per Kuartal): Memetakan 5 fase pergeseran isu, mulai dari fase eksplorasi platform, krisis regulasi (didominasi term 'dagang' dan 'atur'), transisi merger, adopsi digital (didominasi term 'live'), hingga kampanye musiman (term 'ramadan').  

Analisis Kategori & Sumber Berita: Mengungkap diversitas framing editorial, di mana portal tertentu fokus pada monetisasi iklan digital, sementara yang lain fokus pada perdagangan fisik, perlindungan UMKM, atau perspektif makroekonomi.  

Analisis Lanjutan (POS, NER, & N-Grams): Penggunaan Bigram dan Trigram berhasil menangkap frasa krusial penanda diskursus seperti "media sosial", "social commerce", "live streaming", dan "pasar tanah abang".

# 📕Result
Pola Wacana Media (TF-IDF & NER): Pemberitaan terbukti bersifat regulasi-sentris, reaktif-temporal terhadap perubahan kebijakan, dan terpolarisasi secara framing antar media. Kategori Named Entity Recognition (NER) mengonfirmasi dominasi entitas institusional/organisasi dibandingkan figur perorangan.  

Performa Klasifikasi Sentimen: Evaluasi model Machine Learning untuk klasifikasi sentimen 3 kelas (Positif, Negatif, Netral) menunjukkan bahwa Multinomial Naive Bayes (54,04%) mengungguli Logistic Regression (49,07%).  

Tantangan Model: Kelas "Netral" secara konsisten menjadi kelas yang paling sulit diprediksi (F1-score terendah) oleh kedua model, mengindikasikan adanya tumpang tindih pola kata antara artikel netral dengan artikel bernada positif maupun negatif.  

# 📕Conclusion
Kehadiran TikTok Shop telah mendisrupsi ekosistem perdagangan digital dan UMKM di Indonesia, yang memicu respons reaktif dari media massa dan pemerintah (Permendag No. 31 Tahun 2023). Berdasarkan pendekatan Natural Language Processing (NLP), dapat disimpulkan bahwa narasi media massa di Indonesia tidak hanya menyoroti kerentanan pasar tradisional (seperti Tanah Abang), tetapi juga secara signifikan mengafirmasi peluang adaptasi digital bagi pelaku UMKM. Penelitian ini memberikan data-driven insights yang membuktikan pentingnya penguatan literasi digital pelaku usaha, serta dapat menjadi landasan evaluasi bagi perumusan kebijakan e-commerce di masa depan.
