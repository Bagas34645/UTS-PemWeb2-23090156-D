# UTS Pemrograman Web 2 - 23090156-D

## Instalasi dan Konfigurasi

Ikuti langkah-langkah berikut untuk menginstal dan mengonfigurasi proyek ini:

### 1. Clone Repository
Clone repository ini ke komputer Anda:
```bash
git clone https://github.com/Bagas34645/UTS-PemWeb2-23090156-D.git
cd UTS-PemWeb2-23090156-D
```

### 2. Install Dependencies
Jalankan perintah berikut untuk menginstal semua dependensi yang diperlukan:
```bash
composer install
npm install
```

### 3. Konfigurasi Environment
Salin file `.env.example` menjadi `.env` dan sesuaikan konfigurasi database:
```bash
cp .env.example .env
```
Edit file `.env` sesuai dengan pengaturan database Anda.

### 4. Generate Application Key
Jalankan perintah berikut untuk menghasilkan application key:
```bash
php artisan key:generate
```

### 5. Migrasi Database
Jalankan migrasi untuk membuat tabel di database:
```bash
php artisan migrate
```

### 6. Jalankan Server
Jalankan server pengembangan lokal:
```bash
composer run dev
```

Akses aplikasi melalui browser di alamat: [http://localhost:8000](http://localhost:8000)

---

## Implementasi Fitur CRUD Products Menggunakan FluxUI

Fitur CRUD (Create, Read, Update, Delete) untuk produk telah diimplementasikan menggunakan FluxUI. Berikut adalah penjelasan singkat mengenai setiap fitur:

### 1. **Create Product**
- Formulir untuk menambahkan produk baru dapat diakses melalui route: `/dashboard/products/create`.
- Menggunakan komponen `flux:input` untuk input data seperti nama, harga, stok, dan URL gambar.
- Data yang dimasukkan akan divalidasi dan disimpan ke database.

### 2. **Read Products**
- Daftar produk ditampilkan di halaman `/dashboard/products`.
- Menggunakan tabel dengan komponen FluxUI untuk menampilkan data produk, termasuk nama, kategori, harga, stok, dan gambar.
- Fitur pencarian tersedia untuk memfilter produk berdasarkan nama atau deskripsi.

### 3. **Update Product**
- Halaman edit produk dapat diakses melalui tombol "Edit" di daftar produk.
- Route: `/dashboard/products/{id}/edit`.
- Formulir edit menggunakan komponen `flux:input` dan `flux:textarea` untuk memperbarui data produk.

### 4. **Delete Product**
- Produk dapat dihapus melalui tombol "Delete" di daftar produk.
- Konfirmasi penghapusan menggunakan dialog sebelum data dihapus dari database.

### Komponen FluxUI yang Digunakan:
- `flux:input` untuk input teks.
- `flux:textarea` untuk deskripsi produk.
- `flux:button` untuk tombol aksi.
- `flux:badge` untuk menampilkan pesan sukses atau error.
- `flux:dropdown` untuk menu aksi pada setiap produk.

---

## Informasi Route Admin

Berikut adalah daftar route admin yang digunakan untuk fitur CRUD Products:

| HTTP Method | URL                          | Controller Method          | Deskripsi                     |
|-------------|------------------------------|----------------------------|-------------------------------|
| GET         | `/dashboard/products`        | `ProductController@index`  | Menampilkan daftar produk.    |
| GET         | `/dashboard/products/create` | `ProductController@create` | Menampilkan form tambah produk. |
| POST        | `/dashboard/products`        | `ProductController@store`  | Menyimpan produk baru.        |
| GET         | `/dashboard/products/{id}/edit` | `ProductController@edit` | Menampilkan form edit produk. |
| PATCH/PUT   | `/dashboard/products/{id}`   | `ProductController@update` | Memperbarui data produk.      |
| DELETE      | `/dashboard/products/{id}`   | `ProductController@destroy`| Menghapus produk.             |

Pastikan Anda telah login sebagai admin untuk mengakses route ini, karena route ini dilindungi oleh middleware `auth` dan `verified`.

```bash
Route::group(['prefix' => 'dashboard', 'middleware' => ['auth', 'verified']], function() {
    Route::resource('products', ProductController::class);
});
```

Akses halaman admin melalui: [http://localhost:8000/dashboard/products](http://localhost:8000/dashboard/products)
