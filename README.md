<<<<<<< HEAD
# 🐾 Katalon Studio Web Automation - JPetStore

Repository ini berisi skrip automated testing untuk aplikasi web **JPetStore** menggunakan **Katalon Studio**. Proyek ini disusun sebagai pemenuhan **Final Project Software Quality Assurance / Test Automation**.

---

## 📌 Ringkasan Proyek

| Informasi | Keterangan |
| :--- | :--- |
| **Aplikasi Target** | [JPetStore Demo](https://petstore.octoperf.com/actions/Catalog.action) |
| **Automation Tool** | Katalon Studio (Katalon Studio (v10.4.3)) |
| **Bahasa Scripting** | Groovy / Java |
| **Metode Pengujian** | Data-Driven Testing (DDT), Functional Testing, E2E |
| **Data File Source** | Excel / CSV (Internal/External Test Data) |
| **Target Browser** | Google Chrome, Mozilla Firefox, Edge | 
| **Konfigurasi Variabel** | Execution Profile (`profile`) & Global Variables |


## 🌐 Execution Profiles & Global Variables
Proyek ini menggunakan Profile bernama **`Profile`** untuk mengelola seluruh variabel global secara terpusat (*Global Variables*). Nilai-nilai ini digunakan secara dinamis di berbagai Test Case:
| Nama Variable | Tipe | Nilai Awal (*Initial Value*) | Deskripsi / Penggunaan |
| :--- | :---: | :--- | :--- |
| **`baseUrl`** | `String` | `https://petstore.octoperf.com/actions/Catalog.action` | URL utama aplikasi web JPetStore |
| **`username`** | `String` | `j2ee` | Akun default untuk login dan transaksi |
| **`password`** | `String` | `j2ee` | Password akun default |
| **`searchPositive`** | `String` | `Manx` | Kata kunci pencarian valid (`TC_serachPositive`) |
| **`SearchNegative`** | `String` | `Dogs` | Kata kunci pencarian invalid / filter khusus (`TC_serachNegative`) |
| **`productId`** | `String` | `FL-DSH-01` | ID Produk untuk pengetesan katalog dan order |
| **`itemID`** | `String` | `EST-15` | ID Item spesifik untuk transaksi keranjang belanja |
> ⚠️ **Penting:** Pastikan Execution Profile yang dipilih di pojok kanan atas Katalon Studio adalah **`Profile`** sebelum menjalankan pengujian.

---
## 🎯 Daftar Test Case & Skenario Pengujian
### 1. Modul Autentikasi (`Authentication`) - Data-Driven Testing (DDT)
Pengujian login menggunakan 1 Test Case berbasis data (**`loginDDT`**) yang mengeksekusi 3 dataset pengujian secara otomatis melalui Test Suite **`logiinsuite`**:
| Test Case | Dataset / Kondisi | Tipe | Expected Result |
| :--- | :--- | :--- | :--- |
| **`loginDDT`** | **Data 1:** Username & Password valid | **Positive** | Berhasil login, sesi aktif, dan username muncul di header |
| **`loginDDT`** | **Data 2:** Password salah / invalid | **Negative** | Gagal login & muncul pesan error *Invalid username or password* |
| **`loginDDT`** | **Data 3:** Username tidak terdaftar / kosong | **Negative** | Gagal login & sistem menolak autentikasi |
---
### 2. Modul Pencarian & Transaksi (`Search & Cart`)
| Test Case | Keterangan Skenario | Tipe | Expected Result |
| :--- | :--- | :--- | :--- |
| **`TC_serachPositive`** | Pencarian produk dengan kata kunci valid (misal: "Fish", "Dog") | **Positive** | Menampilkan daftar produk yang sesuai dengan kata kunci |
| **`TC_serachNegative`** | Pencarian produk dengan kata kunci acak / tidak terdaftar | **Negative** | Sistem menampilkan hasil kosong / pesan produk tidak ditemukan |
| **`TC_checkOut`** | Melakukan proses checkout barang yang ada di keranjang | **Positive** | Pengguna berhasil diarahkan ke form pemesanan dan pembayaran |
---
### 3. Modul End-to-End (`E2E Flow`)
| Test Case | Cakupan Alur Pengujian | Tipe | Expected Result |
| :--- | :--- | :--- | :--- |
| **`TC_e2e`** | **Alur Penuh Transaksi:**<br>1. Login dengan akun valid<br>2. Cari dan pilih produk hewan<br>3. Masukkan produk ke keranjang (*Add to Cart*)<br>4. Lakukan Checkout & isi detail pembayaran<br>5. Konfirmasi order pemesanan | **Positive** | Seluruh tahapan berhasil tanpa error, Order ID diterbitkan, dan halaman tanda terima (*receipt*) muncul |
---
## 🛠️ Prasyarat Lingkungan (Prerequisites)
Sebelum menjalankan pengujian, pastikan perangkat Anda telah memenuhi prasyarat berikut:
1. **[Katalon Studio](https://katalon.com/)** (versi 8.x atau 9.x+)
2. **Java Development Kit (JDK)** versi 8, 11, atau 17
3. **Browser**: Google Chrome versi stabil terbaru
4. **WebDriver**: Sinkronisasi driver browser melalui:  
   > `Tools` > `Update WebDrivers` > `Chrome`
---

## 📁 Struktur Direktori Proyek
```text
katalon-petstore-web/
├── Profiles/                   # Konfigurasi Execution Profiles
│   └── Profile.glbl            # Global Variables (baseUrl, credentials, search, product)
├── Checkpoints/
├── Data Files/                 # File sumber data pengujian DDT (Excel/CSV)
│   └── LoginData               # Dataset untuk 3 skenario login
├── Object Repository/          # Lokasi penyimpanan Web Element Locators
│   ├── Page_Home/
│   ├── Page_Login/
│   ├── Page_Cart/
│   └── Page_Order/
├── Test Cases/                 # Kumpulan Skrip Pengujian
│   ├── loginDDT                # Test Case Login Data-Driven (3 data via DDT)
│   ├── TC_serachPositive       # Test Case Pencarian valid ('Manx')
│   ├── TC_serachNegative       # Test Case Pencarian invalid/filter ('Dogs')
│   ├── TC_checkOut             # Test Case Proses Checkout produk
│   └── TC_e2e                  # Test Case End-to-End (Login s/d Berhasil Pesan)
├── Test Suites/
│   └── logiinsuite             # Test Suite untuk eksekusi loginDDT
├── Reports/                    # Hasil laporan eksekusi tes (HTML/PDF)
├── .gitignore                  # Filter file Git
└── README.md                   # Dokumentasi proyek

  
=======
# katalon-petstore-web
>>>>>>> ac63074bf1fae88629cf9383f871c8c0dcb71467
