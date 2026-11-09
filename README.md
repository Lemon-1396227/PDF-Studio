# PDF Studio Pro

Aplikasi manajemen dan manipulasi berkas PDF modern dengan pemrosesan 100% lokal di browser pengguna (Client-Side) menggunakan `pdf-lib`, `pdf.js`, `jszip`, dan `tesseract.js`. Seluruh pemrosesan dokumen berjalan langsung di browser tanpa mengirim data atau berkas ke server luar.

---

## Panduan Upload & Deploy ke GitHub

### Langkah 1: Buat Repositori Baru di GitHub
1. Buka [github.com/new](https://github.com/new).
2. Beri nama repositori (contoh: `pdf-studio` atau `pdf-studio-pro`).
3. Pilih visibilitas **Public** (wajib Public jika menggunakan GitHub Pages gratis).
4. Jangan centang "Add a README file" jika ingin mengunggah seluruh berkas dari folder ini.
5. Klik **Create repository**.

---

### Langkah 2: Upload Berkas ke Repositori

#### Opsi A: Upload via Terminal / Git CLI (Direkomendasikan)
Buka terminal / PowerShell di dalam folder ini, lalu jalankan:

```bash
git init
git add .
git commit -m "Initial commit - PDF Studio Pro"
git branch -M main
git remote add origin https://github.com/<USERNAME-ANDA>/<NAMA-REPO>.git
git push -u origin main
```
*(Ganti `<USERNAME-ANDA>` dan `<NAMA-REPO>` sesuai akun dan repositori GitHub Anda)*

#### Opsi B: Upload Manual via Browser (Web GitHub)
1. Pada halaman repositori GitHub baru Anda, klik tombol **"uploading an existing file"**.
2. Seret (*drag and drop*) seluruh isi berkas dan folder dari direktori ini ke area upload browser.
3. Tunggu proses transfer selesai, lalu klik **Commit changes**.

---

### Langkah 3: Deploy ke GitHub Pages (Live Website)
Setelah berkas berhasil diunggah:
1. Buka tab **Settings** di halaman repositori GitHub Anda.
2. Pada menu sidebar sebelah kiri, klik **Pages**.
3. Pada bagian **Build and deployment**:
   - **Source**: Pilih **Deploy from a branch**.
   - **Branch**: Pilih **main** (atau **master**), dan folder **/ (root)**.
4. Klik **Save**.
5. Tunggu sekitar 1 - 2 menit. Refresh halaman Settings Pages, dan Anda akan melihat tautan aktif:
   ```
   https://<username>.github.io/<nama-repo>/
   ```
Aplikasi Anda kini sudah aktif dan dapat diakses dari browser komputer maupun perangkat seluler.

---

### Langkah 4: Auto-Build APK Android via GitHub Actions
Repositori ini telah dilengkapi dengan workflow GitHub Actions di `.github/workflows/build-apk.yml`.
1. Setiap kali Anda melakukan push ke branch `main`, GitHub akan secara otomatis mengompilasi aplikasi Android native.
2. Untuk mengunduh APK hasil kompilasi:
   - Buka tab **Actions** di repositori GitHub Anda.
   - Klik workflow run terbaru ("Build Android APK").
   - Scroll ke bagian bawah pada tabel **Artifacts**.
   - Klik **PDF-Studio-Pro-Debug-APK** untuk mengunduh berkas `.apk`.

Untuk panduan seluler dan instalasi PWA lebih lanjut, silakan baca `PANDUAN_HP_DAN_APK.md`.

---

## Struktur Berkas Repositori

```text
├── index.html                   Entry point utama aplikasi web (GitHub Pages)
├── Index.html                   Salinan berkas HTML utama
├── manifest.webmanifest         Konfigurasi PWA (Progressive Web App)
├── sw.js                        Service Worker untuk dukungan offline & caching
├── icon.svg                     Ikon aplikasi vektor resolusi tinggi
├── .gitignore                   Daftar berkas yang diabaikan oleh Git
├── README.md                    Dokumentasi dan panduan deployment
├── PANDUAN_HP_DAN_APK.md        Panduan instalasi HP, PWA, dan build APK
├── .github/
│   └── workflows/
│       └── build-apk.yml        Workflow otomatisasi build APK Android via GitHub Actions
└── android-app/                 Proyek aplikasi Android native (Android Studio)
```

---

## Daftar Fitur PDF Studio Pro

### 1. KELOLA & ATUR HALAMAN
* **Organizer Visual (Grid & Drag)** `[PRO]` - Atur urutan, putar lembar 90 derajat, dan buang halaman via thumbnail interaktif drag-and-drop.
* **Gabung PDF** - Satukan beberapa dokumen PDF menjadi satu berkas dengan preview daftar file.
* **Pisah Halaman (Split)** - Ambil rentang halaman tertentu (misal: 1-3, 5, 7-10).
* **Hapus Halaman** - Buang halaman tertentu dari dokumen secara aman.
* **Pisah Semua Lembar (.ZIP)** - Pecah setiap halaman otomatis dan unduh sekaligus dalam arsip ZIP.

### 2. KONVERSI & OPTIMASI
* **Kompres Ukuran PDF** - Optimasi struktur objek internal untuk memperkecil kapasitas file.
* **Ubah Ukuran Kertas PDF** `[BARU]` - Sesuaikan dimensi lembaran ke standar A4, F4 / Folio (215 x 330 mm), Letter, Legal, A3, atau A5 (Portrait/Landscape) dengan penskalaan proporsional dan auto-center.
* **Gambar ke PDF** - Susun koleksi foto JPG/PNG menjadi satu dokumen PDF rapi.
* **PDF ke Gambar (PNG/ZIP)** - Ekstrak setiap lembar menjadi gambar PNG resolusi tinggi dalam format ZIP.
* **PDF ke Dokumen Word** - Salin isi teks dokumen ke format file DOC siap edit.
* **PDF ke Halaman Web (HTML)** - Ubah lembaran PDF menjadi tampilan halaman web interaktif.
* **Cetak Hitam Putih (Grayscale)** - Konversi dokumen ke nuansa monokrom hemat tinta printer.

### 3. KEAMANAN & PENGESAHAN
* **Kunci Password (Encrypt)** - Proteksi dokumen rahasia dengan kata sandi kuat.
* **Buka Kunci Password** - Hapus proteksi kata sandi dari file yang terkunci.
* **Sensor Data Rahasia (Redact)** `[BARU]` - Seret mouse di atas lembaran PDF untuk menandai area sensitif (NIK, nomor rekening, nominal gaji). Ditutup dengan kotak hitam pekat permanen langsung ke struktur PDF.
* **Tanda Tangan Digital** - Coret tanda tangan asli di kanvas interaktif dan tempelkan ke dokumen PDF.
* **Stempel Dokumen (Stamp)** - Pasang cap status resmi (APPROVED, REJECTED, CONFIDENTIAL, COMPLETED).
* **Watermark Dokumen** - Sematkan teks latar transparan dengan kontrol warna, posisi, dan opasitas.

### 4. TEKS & UTILITAS DOKUMEN
* **Pindai OCR & Searchable PDF** - Pindai teks dari foto/scan dan tempelkan lapisan teks transparan sehingga PDF menjadi Searchable (dapat dicari via Ctrl+F) serta salin teks TXT.
* **Isi Formulir & Teks Bebas** `[BARU]` - Ketik teks lalu klik pada posisi mana pun di lembar PDF untuk mengisi formulir, biodata, atau catatan dengan pilihan ukuran dan warna font.
* **Nomor Halaman Otomatis** - Sematkan penomoran lembar otomatis di bagian bawah dokumen.
* **Edit Metadata Dokumen** - Sunting judul (Title) dan nama pembuat (Author) berkas PDF.
