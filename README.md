# Analisis Data Penjualan Coffee Shop


## 🗃️ Dataset

Data diambil dari database `CoffeeShop_Dataset.db` yang berisi tabel-tabel berikut:

* `sales outlet`: Informasi tentang toko/outlet (ID, tipe, lokasi, dll.)
* `pastry inventory`: Data inventaris harian untuk produk pastry (terjual, terbuang, % terbuang).
* `product`: Detail produk (ID, kategori, tipe, harga grosir, harga eceran).
* `generations`: Pemetaan tahun lahir ke nama generasi.
* `sales reciepts` (sic): Data transaksional utama (ID transaksi, tanggal, waktu, ID outlet, ID staf, ID pelanggan, ID produk, kuantitas, total harga item).
* `customer`: Informasi pelanggan (ID, nama, email, tanggal bergabung, tanggal lahir, gender).

## 🎯 Tujuan Analisis

Notebook ini bertujuan untuk menjawab beberapa pertanyaan kunci:

1.  Produk apa yang menghasilkan pendapatan (non-promo) paling tinggi?
2.  Outlet di kota mana yang memiliki total pembelian (jumlah item) paling banyak?
3.  Outlet mana yang paling ramai (transaksi terbanyak) dan paling sepi (transaksi paling sedikit)?
4.  Produk apa yang paling banyak dibeli oleh pelanggan pria (M) dan wanita (F)? (Analisis ini diubah dari "generasi" menjadi "gender" selama pengerjaan).

## 💡 Wawasan Utama (Key Insights)

Dari analisis yang dilakukan, ditemukan beberapa wawasan utama:

1.  **Produk Pendapatan Tertinggi:** Pendapatan tertinggi (berdasarkan harga eceran non-promo) didominasi oleh **minuman (Beverages) ukuran besar (Lg)**.
    * **#1:** Sustainably Grown Organic Lg
    * **#2:** Dark chocolate Lg
    * **#3:** Latte Rg

2.  **Penjualan Berdasarkan Kota:**
    * Secara total, **New York** memiliki jumlah penjualan item yang jauh lebih tinggi (48.138 item) dibandingkan **Long Island City** (23.620 item).

3.  **Kinerja Outlet (Ramai vs. Sepi):**
    * **Outlet Paling Ramai** (berdasarkan jumlah transaksi) adalah **Outlet #3 di Astoria, Long Island City** (4.203 transaksi).
    * **Outlet Paling Sepi** (berdasarkan jumlah transaksi) adalah **Outlet #5 di Lower Manhattan, New York** (2.524 transaksi).
    * *Temuan menarik*: Meskipun New York City memimpin total penjualan item secara keseluruhan, outlet tunggal tersibuk justru berada di Long Island City.

4.  **Preferensi Berdasarkan Gender:**
    * Untuk pelanggan yang gendernya terdaftar (M atau F), **Brewed Chai tea** adalah jenis produk yang paling banyak dibeli oleh **wanita** (1.971 unit) dan **pria** (1.507 unit).

## 🚀 Rekomendasi dan Saran Perbaikan

Berdasarkan wawasan dan analisis kode Anda, berikut adalah beberapa rekomendasi untuk bisnis dan untuk perbaikan analisis di masa depan:

### Rekomendasi Bisnis

1.  **Fokus pada Upselling Minuman:** Karena minuman ukuran besar (Lg) adalah penghasil pendapatan terbesar, staf harus didorong untuk secara aktif menawarkan *upsell* dari ukuran reguler ke besar, terutama untuk produk terlaris.
2.  **Strategi Outlet Berbeda:**
    * **Untuk Outlet #5 (Lower Manhattan):** Karena ini adalah outlet yang paling sepi, pertimbangkan untuk meluncurkan promosi lokal atau program loyalitas khusus untuk meningkatkan jumlah transaksi.
    * **Untuk Outlet #3 (Astoria):** Pelajari apa yang membuat outlet ini begitu sukses. Apakah karena lokasi, staf, atau preferensi produk lokal? Terapkan pembelajaran ini ke outlet yang lebih sepi.
3.  **Manfaatkan Data Inventaris (Waste):** Anda memuat tabel `pastry inventory` yang berisi data `% waste` (produk terbuang) tetapi tidak menggunakannya. Ini adalah data yang sangat berharga.
    * **Aksi:** Analisis produk pastry mana yang memiliki `% waste` tertinggi. Jika produk tersebut juga tidak laku, pertimbangkan untuk menghentikannya. Jika laku tetapi sering terbuang, sesuaikan jumlah stok awal (`start_of_day`) untuk mengurangi kerugian.
4.  **Tingkatkan Registrasi Pelanggan:** Analisis gender dan generasi Anda terbatas karena banyak transaksi (`customer_id = 0`) adalah "Tamu".
    * **Aksi:** Tawarkan insentif (misal: diskon 10% untuk pembelian pertama) bagi pelanggan untuk mendaftar menjadi anggota. Ini akan memberikan data demografis yang lebih kaya untuk pemasaran yang lebih tertarget.
