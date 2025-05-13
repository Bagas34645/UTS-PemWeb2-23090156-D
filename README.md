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
