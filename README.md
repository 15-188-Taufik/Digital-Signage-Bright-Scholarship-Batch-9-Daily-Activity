# Digital Signage - Daily Activity Awardee Bright Scholarship

![Digital Signage Preview](https://placehold.co/800x200/0c2461/ffffff?text=Digital+Signage+YBM+BRILiaN&font=segoe-ui)

Proyek ini adalah sebuah dasbor visual (*digital signage*) yang dirancang untuk menampilkan status penyelesaian aktivitas harian para penerima beasiswa (awardee) **Bright Scholarship YBM BRILiaN** secara *real-time*. Tampilan ini ditujukan untuk dipasang di layar monitor di area umum seperti asrama atau sekretariat.

Tujuannya adalah untuk menciptakan lingkungan yang transparan, memotivasi para awardee melalui gamifikasi (skor), dan memberikan gambaran umum kemajuan pembinaan kepada pengelola.

---

## 🚀 Live Demo

Anda dapat mengakses tampilan *digital signage* secara langsung melalui link berikut:

**[Digital Signage - Live View](https://15-188-taufik.github.io/Digital-Signage-Bright-Scholarship-Batch-9-Daily-Activity/)**

---

## ✨ Fitur Utama

-   **🖥️ Tampilan Real-Time:** Data diambil secara periodik dari Google Sheets, memastikan informasi yang ditampilkan selalu yang terbaru.
-   **📈 Visualisasi Data Dinamis:** Menampilkan daftar awardee beserta status penyelesaian setiap aktivitas dalam format kartu yang mudah dibaca.
-   **🏆 Sistem Skor:** Setiap aktivitas memiliki bobot nilai yang berbeda, dan total skor setiap awardee dihitung dan ditampilkan secara otomatis untuk memberikan elemen gamifikasi.
-   **🔄 Rotasi Otomatis (Carousel):** Kartu awardee akan berotasi secara otomatis, memastikan semua data awardee dapat ditampilkan bahkan pada layar dengan ruang terbatas.
-   **🎨 Desain Menarik:** Antarmuka dirancang dengan estetika modern, lengkap dengan animasi halus dan partikel latar belakang untuk tampilan yang lebih hidup dan menarik.
-   **💡 Indikator Pembaruan:** Sebuah notifikasi visual muncul setiap kali data berhasil diperbarui, memberikan kepastian bahwa informasi yang ditampilkan adalah yang terkini.
-   **🕒 Tampilan Tanggal & Waktu:** Menampilkan tanggal dan waktu saat ini untuk informasi kontekstual.

---

## 🛠️ Teknologi yang Digunakan

-   **Frontend:**
    -   HTML5
    -   CSS3 (dengan animasi dan layouting modern)
    -   JavaScript (Vanilla)
-   **Sumber Data:**
    -   [Google Sheets API v4](https://developers.google.com/sheets/api) (Mode Read-Only dengan API Key)

---

## ⚙️ Cara Kerja

Aplikasi ini adalah sebuah halaman web statis tunggal (`index.html`) yang bekerja sepenuhnya di sisi klien (browser).

1.  **Pengambilan Data:**
    -   Saat halaman dimuat, sebuah skrip JavaScript akan melakukan panggilan (`fetch`) ke Google Sheets API menggunakan **API Key** yang telah disediakan.
    -   Data mentah dari sheet `Sheet1` akan diambil.
    -   Proses ini diulang secara otomatis setiap 35 detik untuk memastikan data tetap sinkron.

2.  **Pemrosesan Data:**
    -   Skrip akan mem-parsing data dari spreadsheet, mengidentifikasi nama awardee dari baris header dan nama aktivitas dari kolom pertama.
    -   Status "selesai" (`1`) atau "belum selesai" (`0`) untuk setiap aktivitas akan dipetakan ke masing-masing awardee.
    -   Skor dihitung berdasarkan bobot poin yang telah didefinisikan dalam variabel `ACTIVITY_POINTS`.

3.  **Visualisasi:**
    -   Data yang telah diproses kemudian di-render ke dalam DOM, menciptakan kartu-kartu untuk setiap awardee.
    -   Setiap kartu menampilkan nama, total skor, dan daftar aktivitas beserta statusnya (lengkap dengan ikon visual).
    -   Jika jumlah awardee melebihi kapasitas tampilan, sistem carousel akan aktif dan menampilkan kartu secara bergantian.

---

## 🚀 Panduan Setup

Untuk menjalankan proyek ini, Anda hanya perlu melakukan beberapa konfigurasi sederhana.

### 1. Prasyarat
-   Sebuah Google Spreadsheet yang sudah terisi data aktivitas (dengan struktur yang sama seperti proyek check-in).
-   Sebuah **API Key** dari [Google Cloud Console](https://console.cloud.google.com/). Pastikan API Key ini memiliki akses ke Google Sheets API.

**Penting:** Untuk keamanan, batasi penggunaan API Key Anda agar hanya bisa digunakan dari domain atau alamat IP tempat Anda akan meng-hosting *digital signage* ini.

### 2. Konfigurasi Kode
1.  Buka file `index.html`.
2.  Temukan dan ganti nilai variabel berikut di dalam tag `<script>`:
    ```javascript
    const SHEET_ID = 'GANTI_DENGAN_ID_SPREADSHEET_ANDA';
    const API_KEY = 'GANTI_DENGAN_API_KEY_ANDA';
    ```
3.  (Opsional) Sesuaikan bobot poin untuk setiap aktivitas di dalam objek `ACTIVITY_POINTS`:
    ```javascript
    const ACTIVITY_POINTS = {
        "Dhuha": 3,
        "Tahajjud": 3,
        // ...aktivitas lainnya
    };
    ```

### 3. Menjalankan Proyek
-   Karena proyek ini hanya mengambil data dan tidak memerlukan otentikasi OAuth, Anda bisa membukanya langsung di browser.
-   Untuk hasil terbaik, jalankan file `index.html` pada mode layar penuh (F11) di browser yang terpasang pada perangkat *digital signage* Anda.
-   Pastikan perangkat tersebut memiliki koneksi internet yang stabil.
