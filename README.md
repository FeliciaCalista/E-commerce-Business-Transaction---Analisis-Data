# E-commerce-Business-Transaction---Analisis-Data

## Deskripsi

Proyek ini bertujuan untuk menganalisis data transaksi e-commerce guna mendapatkan insight bisnis terkait performa penjualan, perilaku pelanggan, performa produk, dan tren wilayah.

Analisis dilakukan menggunakan SQL (SQLite) dan Python (Pandas, Matplotlib) untuk menunjukkan alur kerja end-to-end, mulai dari data cleaning hingga segmentasi pelanggan.

---

## Informasi Dataset

- **Sumber**: https://www.kaggle.com/datasets/gabrielramos87/an-online-shop-business
- **Jumlah Data Bersih**: 531.095 baris
- **Database**: ecommerce.db
- **Tabel Utama**: sales
- **Kolom Data:**
  
| Kolom         | Deskripsi         |
| ------------- | ----------------- |
| TransactionNo | ID transaksi      |
| Date          | Tanggal transaksi |
| ProductNo     | ID produk         |
| ProductName   | Nama produk       |
| Price         | Harga satuan      |
| Quantity      | Jumlah pembelian  |
| CustomerNo    | ID pelanggan      |
| Country       | Negara pelanggan  |

---

## Persiapan & Pembersihan Data
**1. Persiapan Data**

- Data CSV dimasukkan ke dalam database SQLite
- Membuat kolom turunan: `Revenue = Price × Quantity`

**2. Pembersihan Data**

- Menangani missing values
- Menghapus data duplikat
- Konversi kolom Date ke format datetime

**3. Identifikasi Outlier**

- Outlier diidentifikasi menggunakan boxplot pada:
  - Price
  - Quantity
  - Revenue
- Outlier tidak langsung dihapus, tetapi:
  - Tetap dianalisis
  - Dikecualikan hanya untuk KPI tertentu agar hasil lebih representatif

---

## Analisis Data

### Key Performance Indicators (KPI)

| KPI | Nilai |
|---|---|
| Total Revenue | £62,781,300 |
| Total Transaksi | 19,789 |
| Total Pelanggan | 4,718 |
| Rata-rata Revenue per Transaksi | £3,172.53 |
| Rata-rata Revenue per Transaksi (tanpa outlier) | £1,699.13 |
| Revenue per Customer | £5.97 – £2,112,282.03 |

**_Insight_:**
- Outlier memiliki dampak besar terhadap metrik berbasis rata-rata
- Definisi KPI perlu disesuaikan dengan tujuan bisnis (operasional vs strategis)

---

### Time-Based Analysis

#### 1. Tren Penjualan Bulanan
- Revenue meningkat dari **Agustus hingga Oktober**
- **Puncak penjualan terjadi di bulan November**
- Mengindikasikan adanya efek musiman atau kampanye promosi

#### 2. Tren Penjualan Mingguan
Lonjakan signifikan terjadi pada:
- Akhir 2018 – awal 2019
- Minggu ke-17 tahun 2019
- Periode Agustus – November

#### 3. Pola Musiman
- **Agustus** memiliki rata-rata revenue bulanan tertinggi
- Disusul oleh **September** dan **Januari**

#### 4. _Weekend_ vs _Weekday_
- Transaksi akhir pekan menyumbang **38.31% dari total revenue**
- Menunjukkan intensitas belanja yang lebih tinggi saat weekend

---

### Product Analysis

#### 1. Produk Terlaris (berdasarkan Quantity)
1. Paper Craft Little Birdie – 80,995 unit
2. Medium Ceramic Top Storage Jar – 78,033 unit

#### 2. Produk dengan Revenue Tertinggi
1. Paper Craft Little Birdie – 1.59% total revenue
2. Medium Ceramic Top Storage Jar – 1.30% total revenue

#### 3.  _Pricing Insight_
Beberapa produk menghasilkan revenue tinggi meskipun volume penjualannya relatif rendah, seperti:
- Cream Hanging Heart T-Light Holder
- Assorted Colour Bird Ornament
- Regency Cakestand 3 Tier

#### 4. Produk dengan Jumlah Pembatalan Terbanyak
- Paper Craft Little Birdie
- Medium Ceramic Top Storage Jar

#### 5. _Cancellation Rate Insight_
- **Blue Padded Soft Mobile** memiliki tingkat pembatalan tertinggi
- Produk dengan volume tinggi tidak selalu memiliki risiko pembatalan tertinggi

---

### Customer Analysis

#### 1. Pelanggan dengan Kontribusi Terbesar
- 10 pelanggan teratas menyumbang **15.19% dari total revenue**
- Menunjukkan adanya **VIP / high-value customers**

#### 2. _Repeat Purchase Behavior_
- 3,141 dari 4,718 pelanggan melakukan pembelian lebih dari satu kali
- **Repeat purchase rate: 66.57%**

#### 3. _Average Purchase Value_ (APV)
- APV rendah + total belanja tinggi → sering belanja dengan nilai kecil
- APV tinggi + total belanja rendah → jarang belanja tapi bernilai besar

#### 4. _Customer Retention_
- **63.92% pelanggan** melakukan transaksi di lebih dari satu bulan
- Membuka peluang untuk:
  - Program loyalitas
  - Membership
  - Strategi retensi pelanggan

 ---
 
### Regional Analysis

#### 1. Transaksi per Negara
- **Inggris** mendominasi jumlah transaksi

#### 2. Revenue per Negara
- Beberapa negara memiliki revenue tinggi meskipun jumlah transaksi rendah
- Mengindikasikan **Average Order Value (AOV)** yang tinggi

#### 3. Revenue per Pelanggan
- **Belanda** dan **Irlandia** memiliki revenue per customer sangat tinggi
- Menunjukkan perilaku belanja premium

---

### Price & Quantity Analysis

#### 1. Price vs Quantity
- Tidak ditemukan korelasi kuat antara harga dan jumlah pembelian

#### 2. Quantity vs Revenue
- Produk dengan quantity tinggi cenderung menghasilkan revenue tinggi
- Namun harga tetap menjadi faktor penting dalam kontribusi revenue

---

### Customer Segmentation (RFM Analysis)

Segmentasi pelanggan menggunakan **RFM (Recency, Frequency, Monetary)**.

| Segment | Deskripsi |
|---|---|
| At Risk | Jarang berbelanja dan nilai transaksi rendah |
| Champions | Pelanggan baru, sering belanja, dan bernilai tinggi |
| Loyal Customers | Aktif dan konsisten |
| Frequent Buyers | Sering belanja dengan nilai transaksi kecil |

_Insight_:
- Mayoritas pelanggan berada di segmen **At Risk**
- Segmen **Champions** relatif kecil tetapi berkontribusi besar terhadap revenue

---

## Alat & Teknologi
- Python (Pandas, NumPy, Matplotlib)
- SQL (SQLite)
- Google Colab

---

## Kesimpulan
- Outlier memiliki dampak signifikan terhadap interpretasi KPI
- Revenue terdistribusi tidak merata antar pelanggan dan wilayah
- Segmentasi RFM membantu strategi targeting dan retensi
- Data menunjukkan peluang untuk optimasi harga, promosi musiman, dan loyalitas pelanggan

---

## Pekerjaan di Masa Depan
- Antarmuka interaktif (Tableau / Power BI)
- Analisis kohort & retensi
- Nilai Seumur Hidup Pelanggan (CLV)
- Analisis prediktif untuk peramalan permintaan
