# online-retail-customer-segmentation

## Executive Summary
Proyek ini memetakan segmen pelanggan e-commerce menggunakan analisis **RFM (Recency, Frequency, Monetary)** dan algoritma **K-Means Clustering**[cite: 1]. Hasil segmentasi digunakan untuk merancang strategi pemasaran terarah (*targeted marketing*) guna mengoptimalkan *Customer Lifetime Value* (CLV) serta efisiensi biaya promosi.

---

## Key Insights (EDA)
* **Sales Driver:** Korelasi linier `Quantity` terhadap `TotalPrice` sangat kuat (**0.89**), membuktikan volume pembelian adalah pendorong utama pendapatan.
* **Distribusi & Outliers:** Pengeluaran pelanggan terdistribusi *right-skewed*[cite: 1]. Mayoritas pelanggan belanja di bawah 500, tetapi segmen *high-value* membentuk *long-tail* hingga >4.000.
* **Pola Bisnis:** Penjualan didominasi penuh oleh pasar UK (>8 juta)[cite: 5], mengalami lonjakan musiman drastis pada Q4 (puncak November mendekati 1.5 juta)[cite: 6], dan jam transaksi paling aktif terjadi pada pukul 10.00–12.00 siang[cite: 7].

---

## Preprocessing & Modeling
1. **Feature Engineering:** Agregasi transaksi ke level pelanggan (*CustomerID*) untuk membentuk variabel RFM.
2. **Data Transformation:** Mengaplikasikan *Symmetric Log Transformation* / *QuantileTransformer* dan *StandardScaler* untuk meratakan data *skewed* tanpa *data loss*[cite: 1, 4].
3. **Clustering:** Menentukan $k=4$ klaster paling optimal berdasarkan evaluasi *Elbow Method* dan *Silhouette Score* (0.42)[cite: 1].

---

## Cluster Profiles & Actionable Strategies

| Segmen | Karakteristik RFM | Strategi Bisnis |
| :--- | :--- | :--- |
| **VIP / High-Value** | Recency sangat rendah, Frequency & Monetary sangat tinggi. | Program *VIP Loyalty*, akses produk prioritas, dan layanan khusus untuk retensi. |
| **Loyal Customers** | Transaksi rutin berkala, Monetary kelas menengah. | Penawaran paket *bundling*, *upselling*, dan *cross-selling* rekomendasi produk. |
| **At-Risk / Hibernating** | Transaksi lama tinggi, namun Recency sudah sangat tinggi. | Kampanye *win-back* terautomasi lewat surel dan voucher reaktivasi terbatas. |
| **Low-Value / Occasional** | Frekuensi transaksi rendah dan nilai belanja kecil. | Promosi massal berbiaya rendah (*flash sale*, batas minimum *free ongkir*). |

---

## Tech Stack
* **Language:** Python
* **Libraries:** Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn
