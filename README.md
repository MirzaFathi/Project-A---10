# Analisis Sentimen pada Pengaruh Tiktok Shop pada UMKM Menggunakan NLP
Written by: Mirza Fathi Taufiqurrahman (5026231105), M Faiza Fachra Azizi (5026231126), Ida Bagus A (5026231120), Ibrahim Amar Alfanani (5026231195), Hizkia Crisantino (5026231040)

# 📕Introduction 
Topik yang dipilih pada penelitian ini adalah pengaruh dari Tiktok Shop terhadap UMKM mulai dari regulasinya, dampak dari segi bisnis, dan strateginya. Sehingga kami mencoba mengumpulkan data yaitu artikel terkait Tiktok Shop yang berkaitan dengan UMKM.

# Abstract

Ekosistem perdagangan digital di Indonesia tengah mengalami pergeseran paradigma dengan hadirnya fenomena social commerce, khususnya melalui platform TikTok Shop. Relevansi topik ini terletak pada kemampuannya mengubah perilaku belanja konsumen dari pencarian produk secara aktif menjadi konsumsi konten yang interaktif melalui video pendek dan live streaming. Mengingat Indonesia merupakan salah satu pasar TikTok terbesar di dunia, integrasi fitur belanja langsung ini menciptakan dualitas dampak: di satu sisi menawarkan peluang digitalisasi yang cepat bagi pelaku usaha, namun di sisi lain menimbulkan disrupsi masif terhadap pelaku UMKM tradisional. Dinamika ini mencapai puncaknya pada intervensi regulasi pemerintah melalui Permendag No. 31 Tahun 2023, yang menjadikan analisis terhadap pengaruh TikTok Shop sebuah isu krusial untuk menentukan masa depan ketahanan ekonomi kerakyatan di era transformasi digital.

Berdasarkan fenomena tersebut, kelompok kami merumuskan pertanyaan riset utama: "Bagaimana pola sentimen publik dan pelaku UMKM di media sosial terhadap kehadiran TikTok Shop di Indonesia, dan sejauh mana narasi digital tersebut mencerminkan keberhasilan atau tantangan transformasi digital bagi pengusaha kecil?" Alasan utama kelompok kami memutuskan untuk meneliti hal ini adalah karena melimpahnya data tekstual tidak terstruktur di media sosial yang mencerminkan opini jujur masyarakat. Hal ini memberikan peluang ideal untuk mengimplementasikan teknik Natural Language Processing (NLP) melalui Google Colab, seperti Sentiment Analysis dan Topic Modeling. Kami ingin melihat apakah data tersebut menunjukkan dukungan terhadap efisiensi digital atau justru kekhawatiran terhadap persaingan harga yang tidak sehat, sehingga riset ini dapat memberikan wawasan berbasis data bagi para pengambil kebijakan.

Urgensi masalah ini didukung oleh sejumlah studi terindeks Scopus yang memperkuat relevansi topik dan pendekatan metodologis penelitian ini. Pertama, (Wirdiyanti R. & Yusgiantoro I., 2023) dalam jurnal Electronic Commerce Research (Springer) dengan http://doi.org/10.1007/s10660-022-09547-7 membuktikan bahwa adopsi e-commerce oleh UMKM di Indonesia secara signifikan meningkatkan kinerja bisnis dan inklusi keuangan, namun masih terkendala oleh rendahnya literasi digital dan keterbatasan infrastruktur teknologi. Temuan ini menjustifikasi mengapa transisi UMKM ke platform berbasis social commerce seperti TikTok Shop merupakan isu strategis yang mendesak untuk dikaji, khususnya dalam konteks kesiapan pelaku usaha kecil menghadapi ekosistem platform baru. Kedua, (Wongkitrungrueng A. & Assarut N., 2020) dalam Journal of Business Research (Elsevier, Scopus Q1) dengan https://doi.org/10.1016/j.jbusres.2018.01.016 menunjukkan bahwa live streaming merupakan mekanisme utama dalam membangun kepercayaan konsumen dan mendorong keterlibatan dalam transaksi social commerce. Relevansi studi ini sangat langsung terhadap penelitian kami, mengingat fitur live streaming TikTok Shop merupakan salah satu term paling dominan yang muncul dalam analisis TF-IDF (term live mendominasi periode 2025-Q3), mengindikasikan bahwa dinamika live commerce menjadi inti narasi pemberitaan pada fase adoptif. Ketiga, Tatik dan Setiawan (2024) dalam Asia Pacific Journal of Marketing and Logistics (Tatik D. & Setiawan D., 2024) dengan https://doi.org/10.1108/APJML-01-2024-0090 secara spesifik menganalisis pengaruh social media marketing terhadap kinerja UMKM di Indonesia, dan menemukan bahwa faktor kepercayaan dan persepsi kemudahan penggunaan platform merupakan prediktor utama adopsi. Hasil ini memperkuat basis teoritis mengapa analisis sentimen terhadap narasi media—yang mencerminkan persepsi publik—memiliki implikasi langsung bagi pengambilan keputusan pelaku UMKM.

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
- uppercase to lowercase
- stopwords
- membuat kolom before stopwords dan after stopwords
- lemmatization: root words (kata dasar)
- (n) before stopwords & after stopwords
- (n) frequency top 100 words

# Analysis TF-IDF

# Result

# Conclusion
