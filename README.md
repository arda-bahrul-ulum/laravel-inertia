# Laravel Inertia - Simple CRUD

## Deskripsi Sistem

Aplikasi ini adalah contoh implementasi CRUD (Create, Read, Update, Delete) sederhana untuk entitas Post menggunakan Laravel sebagai backend dan Inertia.js + Vue 3 sebagai frontend. Dengan pendekatan Inertia, aplikasi ini memberikan pengalaman SPA (Single Page Application) tanpa harus meninggalkan ekosistem Laravel.

Fitur utama:

-   Manajemen data Post (judul & konten)
-   Validasi data pada backend
-   Flash message setelah aksi sukses
-   SPA experience dengan Vue 3

## Stack & Library yang Digunakan

### Backend

-   **Laravel Framework** (^8.75)
-   **PHP** (^7.3|^8.0)
-   **Inertia.js Laravel Adapter** (^1.3)
-   **Laravel Sanctum** (^2.11) - untuk autentikasi API/token (jika diperlukan)
-   **Fruitcake Laravel CORS** (^2.0)
-   **Guzzle HTTP Client** (^7.0.1)
-   **Laravel Tinker** (^2.5) - untuk REPL

### Frontend

-   **Vue 3** (^3.5.13)
-   **@inertiajs/inertia** (^0.11.1)
-   **@inertiajs/inertia-vue3** (^0.6.0)
-   **Axios** (^0.21) - HTTP client
-   **Lodash** (^4.17.19)
-   **Laravel Mix** (^6.0.6) - build tool
-   **PostCSS** (^8.1.14)
-   **vue-loader** (^16.8.3)

## Cara Instalasi

### 1. Clone Repository

```bash
git clone <url-repo-anda>
cd laravel-inertia
```

### 2. Instalasi Backend (Laravel)

```bash
composer install
```

### 3. Instalasi Frontend (Node Modules)

```bash
npm install
```

### 4. Konfigurasi Environment

Copy file `.env.example` menjadi `.env` lalu sesuaikan konfigurasi database dan lainnya:

```bash
cp .env.example .env
```

Generate application key:

```bash
php artisan key:generate
```

### 5. Migrasi Database

Pastikan database sudah dibuat, lalu jalankan:

```bash
php artisan migrate
```

### 6. Build Frontend Assets

```bash
npm run dev
```

Untuk production:

```bash
npm run prod
```

### 7. Menjalankan Server

```bash
php artisan serve
```

Akses aplikasi di `http://localhost:8000`

## Struktur Direktori Penting

-   `app/Http/Controllers/PostController.php` — Logic CRUD Post
-   `resources/js/` — Source code Vue & Inertia
-   `resources/views/app.blade.php` — Root template Inertia
-   `routes/web.php` — Routing aplikasi

## Lisensi

Aplikasi ini menggunakan lisensi MIT.
