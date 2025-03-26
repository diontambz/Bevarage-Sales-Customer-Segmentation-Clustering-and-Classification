# Analisis Segmentasi Pelanggan: Perilaku Pembelian Minuman

## 📌 Gambaran Umum
Proyek ini menganalisis data penjualan minuman untuk mengidentifikasi segmen pelanggan menggunakan clustering, kemudian membangun model klasifikasi untuk memprediksi segmentasi pelanggan ini. Proyek ini menganalisis pola pembelian minuman menggunakan pendekatan **unsupervised learning** (clustering) dan **supervised learning** (klasifikasi). Hasil akhirnya, model mampu memprediksi tipe customer berdasarkan segmentasi Cluster Low Spend, Mid Spend, atau Hight Spend.

## Alur Teknis
1. **Preprocessing**:
   - Standarisasi fitur numerik
   - Encoding fitur kategorikal
   - Feature engineering (Discount Ratio = Discount/Total_Price)

2. **Clustering**:
   - Metode: K-Means (n_clusters=4)
   - Fitur utama: Unit_Price, Total_Price, Quantity, Discount

3. **Klasifikasi**:
   - Pembagian data: 80% training, 20% testing
   - Model: Random Forest vs Logistic Regression

## 🔍 Interpretasi Hasil Clustering

### 1. Cluster 0: Pembeli Biasa - Pengeluaran Rendah  
**Karakteristik**:  
- Rata-rata belanja: \$21.67 per transaksi  
- Pembelian khas: 9 item dengan diskon minimal (0.7%)  
- Variasi produk: Seimbang di semua kategori  

**Insight Bisnis**:  
Konsumen individu yang sensitif harga dengan pembelian kecil rutin.

---

### 2. Cluster 1: Pembeli Premium - Pengeluaran Tinggi  
**Karakteristik**:  
- Fokus eksklusif: 100% minuman beralkohol  
- Margin tinggi: harga satuan \$55.27  
- Sensitivitas diskon rendah (1.1%)  

**Insight Bisnis**:  
Konsumen kaya yang mengutamakan kualitas daripada harga.

### 3. Cluster 2: Pembeli Grosir - Sensitif Diskon  
**Karakteristik**:  
- Volume tinggi: 63 item/transaksi  
- Diskon signifikan (9.6%)  
- Pola pembelian: Akhir bulan

**Insight Bisnis**:  
Pemilik usaha kecil yang berbelanja stok. **Taktik**:
- Program diskon volume (contoh: 15% untuk >100 item)
- Notifikasi stok masuk

---

### 4. Cluster 3: Distributor - Pengeluaran Besar  
**Karakteristik**:  
- Rata-rata transaksi: \$3,979.02  
- Diskon khusus 10.1%  
- Frekuensi pembelian: Mingguan

**Insight Bisnis**:  
Mitra bisnis dengan kebutuhan logistik kompleks. **Aksi**:
- Dedicated account manager
- Flexible payment terms (Net 30/60)


## 🔍 Hasil Klasifikasi
| Model              | Akurasi | F1-Score |
|--------------------|---------|----------|
| Random Forest      | 96%     | 0.96     |
| Logistic Regression| 94%     | 0.94     |

## 🔎 Temuan Utama

- **Random Forest** lebih baik dalam mengidentifikasi cluster minoritas:  
  `Recall: 91%` (RF) vs `73%` (Logistic Regression) untuk Cluster 1
- **Kedua model** menunjukkan performa kuat di cluster pengeluaran tinggi:  
  `F1-Score > 0.98` untuk Cluster 1 dan 3

## 💡 Aplikasi Bisnis

### 🎯 Optimasi Pemasaran
- Desain kampanye spesifik untuk setiap segmentasi cluster
- Contoh: 
  - Cluster 0: Program loyalitas untuk pembeli casual
  - Cluster 3: Penawaran eksklusif untuk distributor

### 💰 Strategi Harga
- Implementasi harga dinamis berdasarkan sensitivitas:
  - Cluster 2 (Discount-Oriented): Diskon volume
  - Cluster 1 (Premium): Harga premium dengan value-added

### 📦 Perencanaan Inventaris
- Sistem prediksi permintaan khusus untuk:
  - Antisipasi lonjakan order dari **Cluster 3** (Distributor)
  - Manajemen stok harian untuk **Cluster 0** (Pembeli rutin)
