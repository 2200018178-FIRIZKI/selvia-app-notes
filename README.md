# Project name: Submission Selvia App Notes

## Project Summary
Aplikasi ini merupakan aplikasi catatan sederhana berbasis web yang dibangun menggunakan JavaScript, Webpack, dan modularisasi komponen. Fitur utama meliputi menambah, mencari, dan menghapus catatan.

---

## Error Notes


Pada project yang diperiksa terjadi beberapa error saat proses build dan menjalankan aplikasi di browser, di antaranya:
- **Error 404 pada resource CSS/JS:** Browser menolak memuat file CSS dan JS dari `/src` karena file tidak ditemukan atau MIME type tidak sesuai.
- **Error font:** Font gagal di-load karena file font rusak atau konfigurasi loader belum tepat.
- **Error favicon.ico:** Browser gagal menemukan favicon, menyebabkan error 404.

**Cara mengatasinya:**
- Pastikan semua resource (CSS, JS, font, gambar) di-load melalui Webpack, bukan dari path relatif `/src/...` pada hasil build.
- Hapus tag `<link rel="stylesheet" href="./src/styles/styles.css">` dan `<script src="./src/data/data.js"></script>` dari HTML hasil build.
- Pastikan hanya ada `<script type="module" src="./bundle.js"></script>` di HTML hasil build.
- Pastikan font di-import dari CSS/JS, bukan langsung dari HTML, dan file font tidak rusak.
- Tambahkan file `favicon.ico` ke folder `src` dan pastikan sudah di-link di `<head>`.

---

## Code Review

### 1. Kode Tidak Pernah Digunakan
Kode yang tidak pernah digunakan baik itu class, method, ataupun variable sebaiknya dihapus. Hal ini akan membuat kode lebih bersih dan mudah dipelihara. Gunakan fitur Analyze - Code Cleanup untuk mempercepat proses ini.

### 2. Resource Tidak Terpakai
Selalu perhatikan resources yang tidak pernah digunakan di dalam project karena akan mempengaruhi size build. Gunakan fitur Remove Unused Resource untuk menghapus resources yang tidak pernah digunakan.

---

## code
**Contoh:**  
```js
import './styles/styles.css';
```
**Feedback:**  
Import CSS sudah dilakukan dari JS, sehingga tidak perlu lagi menambahkan tag `<link rel="stylesheet" ...>` di HTML.

---

## code
**Contoh:**  
```js
{
  test: /\.(woff(2)?|ttf|eot|otf)$/i,
  type: 'asset/resource',
},
```
**Feedback:**  
Konfigurasi loader font sudah benar, pastikan tidak ada duplikasi loader font di file webpack.

---

## code
**Contoh:**  
```html
<link rel="icon" type="image/x-icon" href="favicon.ico">
```
**Feedback:**  
Menambahkan favicon.ico di folder `src` dan menghubungkannya di HTML akan menghilangkan error 404 favicon.

---

## code
**Contoh:**  
```js
// Tidak ada kode yang tidak digunakan
```
**Feedback:**  
Pastikan seluruh kode yang tidak digunakan sudah dihapus agar project tetap bersih dan maintainable.

---

## code
**Contoh:**  
```js
// Struktur modular komponen
```
**Feedback:**  
Struktur file sudah cukup baik dan modular, memudahkan pengembangan dan pemeliharaan.

---

## Saran

### 1. Keterbacaan Kode
- Kode sudah cukup rapi dan terstruktur, namun akan lebih baik jika setiap fungsi utama diberi komentar singkat mengenai tujuannya.
- Gunakan penamaan variabel dan fungsi yang deskriptif agar mudah dipahami oleh pembaca lain.
- Jika ada bagian kode yang kompleks, tambahkan komentar penjelas.

### 2. Arsitektur Proyek
- Arsitektur proyek sudah sesuai untuk aplikasi skala kecil-menengah.
- Pemisahan komponen sudah baik, namun bisa dipertimbangkan untuk menambah folder khusus untuk utilitas/helper jika aplikasi berkembang.
- Jika aplikasi bertambah besar, pertimbangkan penggunaan state management sederhana.

### 3. Tampilan dan Responsivitas
- Tampilan sudah cukup baik dan responsif di berbagai ukuran layar.
- Disarankan untuk menambah feedback visual (misal: notifikasi sukses/gagal saat menambah/menghapus catatan).
- Pastikan semua elemen UI tetap proporsional di perangkat mobile.

### 4. Efektivitas Penggunaan Library dan Framework
- Penggunaan Webpack sudah tepat dan efektif untuk kebutuhan modularisasi dan asset management.
- Library yang digunakan sudah sesuai kebutuhan, tidak ada library berlebih.
- Jika aplikasi berkembang, pertimbangkan penggunaan framework UI (seperti React/Vue) untuk manajemen komponen yang lebih kompleks.

---

**Good job! Setelah perbaikan di atas, aplikasi berjalan lancar dan fitur utama dapat