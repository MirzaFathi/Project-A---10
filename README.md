# Analisis Sentimen pada Pengaruh Tiktok Shop pada UMKM Menggunakan NLP
Written by: Mirza Fathi Taufiqurrahman (5026231105), M Faiza Fachra Azizi (5026231126), Ida Bagus A (5026231120), Ibrahim Amar Alfanani (5026231195), Hizkia Crisantino (5026231040)

# 📕Introduction 
Topik yang dipilih pada penelitian ini adalah pengaruh dari Tiktok Shop terhadap UMKM mulai dari regulasinya, dampak dari segi bisnis, dan strateginya. Sehingga kami mencoba mengumpulkan data yaitu artikel terkait Tiktok Shop yang berkaitan dengan UMKM.

# Abstract

Ekosistem perdagangan digital di Indonesia tengah mengalami pergeseran paradigma dengan hadirnya fenomena social commerce, khususnya melalui platform TikTok Shop. Relevansi topik ini terletak pada kemampuannya mengubah perilaku belanja konsumen dari pencarian produk secara aktif menjadi konsumsi konten yang interaktif melalui video pendek dan live streaming. Mengingat Indonesia merupakan salah satu pasar TikTok terbesar di dunia, integrasi fitur belanja langsung ini menciptakan dualitas dampak: di satu sisi menawarkan peluang digitalisasi yang cepat bagi pelaku usaha, namun di sisi lain menimbulkan disrupsi masif terhadap pelaku UMKM tradisional. Dinamika ini mencapai puncaknya pada intervensi regulasi pemerintah melalui Permendag No. 31 Tahun 2023, yang menjadikan analisis terhadap pengaruh TikTok Shop sebuah isu krusial untuk menentukan masa depan ketahanan ekonomi kerakyatan di era transformasi digital.

Berdasarkan fenomena tersebut, kelompok kami merumuskan pertanyaan riset utama: "Bagaimana pola sentimen publik dan pelaku UMKM di media sosial terhadap kehadiran TikTok Shop di Indonesia, dan sejauh mana narasi digital tersebut mencerminkan keberhasilan atau tantangan transformasi digital bagi pengusaha kecil?" Alasan utama kelompok kami memutuskan untuk meneliti hal ini adalah karena melimpahnya data tekstual tidak terstruktur di media sosial yang mencerminkan opini jujur masyarakat. Hal ini memberikan peluang ideal untuk mengimplementasikan teknik Natural Language Processing (NLP) melalui Google Colab, seperti Sentiment Analysis dan Topic Modeling. Kami ingin melihat apakah data tersebut menunjukkan dukungan terhadap efisiensi digital atau justru kekhawatiran terhadap persaingan harga yang tidak sehat, sehingga riset ini dapat memberikan wawasan berbasis data bagi para pengambil kebijakan.

Urgensi masalah ini didukung oleh berbagai studi terindeks Scopus yang menyoroti pergeseran pasar dan efektivitas metodologi NLP. Studi oleh Han et al. (2023) dalam Journal of Theoretical and Applied Electronic Commerce Research https://doi.org/10.3390/jtaer18010015 menjelaskan bagaimana fitur sosial meningkatkan adopsi belanja secara impulsif, yang menjustifikasi mengapa platform ini menjadi ancaman serius bagi ritel konvensional. Indrawati et al. (2022) dalam jurnal Sustainability https://doi.org/10.3390/su141912444 secara spesifik membahas tantangan adopsi teknologi pada UMKM di Indonesia, memperkuat dasar mengapa fokus pada pelaku usaha kecil sangat penting. Lebih lanjut, Wongkitrungrueng & Assarut (2020) dalam Journal of Retailing and Consumer Services https://doi.org/10.1016/j.jretconser.2018.08.005 menunjukkan bahwa keterlibatan melalui live streaming adalah kunci kepercayaan konsumen modern. Terakhir, penggunaan NLP sebagai metode divalidasi oleh Li et al. (2024) dalam IJIM Data Insights https://doi.org/10.1016/j.jjimei.2024.100267 sebagai alat paling efektif untuk mengevaluasi sentimen pasar dalam skala besar, yang membuktikan bahwa pendekatan teknis kelompok kami memiliki landasan ilmiah yang kuat.

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
