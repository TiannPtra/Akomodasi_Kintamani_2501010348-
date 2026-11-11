# Akuisisi Data Akomodasi di Kecamatan Kintamani

**Mata Kuliah:** BIFP-243 Akuisisi dan Manajemen Data  
**Pengambil Data:** Mahasiswa INSTIKI (NIM: 2501010348)  
**Tanggal Akses:** 11 November 2026  

---

## 1. Tujuan Proyek
Proyek ini bertujuan untuk melakukan akuisisi data sekunder berupa data akomodasi (hotel, guest house, hostel, motel, apartment, chalet) di wilayah Kecamatan Kintamani, Kabupaten Bangli, Bali secara etis menggunakan Overpass API (OpenStreetMap). Data hasil akuisisi kemudian dibersihkan, didokumentasikan, dan dibandingkan dengan data resmi Badan Pusat Statistik (BPS).

## 2. Sumber Data & Lisensi
* **Sumber Data Utama:** OpenStreetMap melalui Overpass API (`https://overpass-api.de/api/interpreter`)
* **Data Pembanding:** Publikasi BPS Kabupaten Bangli (*Kecamatan Kintamani Dalam Angka*)
* **Atribusi Wajib:** **© OpenStreetMap contributors**
* **Lisensi Data:** Open Database License (ODbL)

## 3. Metode Akuisisi & Pengolahan Data
1. **Pengambilan Data:** Mengirimkan query Overpass API dengan filter batas administratif Kecamatan Kintamani (`admin_level=6`) dan kategori tag `tourism`.
2. **Penyimpanan Raw:** Respons mentah JSON disimpan ke dalam folder `data/raw/` dilengkapi dengan checksum MD5 dan dokumentasi provenance.
3. **Transformasi Tabular:** Data mentah diekstrak menjadi format tabular CSV di `data/interim/akomodasi_kintamani.csv`.
4. **Data Cleaning & Quality Check:** Memeriksa dan menghapus duplikat berdasarkan `osm_type` dan `osm_id`, trimming spasi pada nama, dan konversi tipe data.

## 4. Batasan Etika & Minimisasi Data
* **Data Pribadi:** Sesuai dengan prinsip etika data, data kontak pribadi seperti nomor telepon pribadi, email pribadi, atau akun media sosial pemilik **tidak diambil/disimpan**.
* **Batas Akses API:** Menggunakan kriteria timeout dan retry exponential backoff serta menyantumkan identitas `User-Agent` yang jelas untuk menghormati server Overpass.

## 5. Cara Menjalankan Ulang Kode
1. Pastikan Python 3.x dan library `pandas` serta `requests` sudah terinstall:
   ```bash
   pip install requests pandas
   ```
