# 🏦 KoperasiKu

> Aplikasi Manajemen Koperasi Harian berbasis Web  
> Tidak perlu instalasi — buka langsung di browser.

[![GitHub Pages](https://img.shields.io/badge/Deploy-GitHub%20Pages-222?logo=github)](https://pages.github.com)
[![Firebase](https://img.shields.io/badge/Database-Firebase%20Firestore-orange?logo=firebase)](https://firebase.google.com)
[![HTML5](https://img.shields.io/badge/Built%20With-HTML5%20%2B%20Vanilla%20JS-blue?logo=html5)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![License: MIT](https://img.shields.io/badge/License-MIT-green)](LICENSE)

---

## 🌐 Demo Live

Setelah deploy ke GitHub Pages, aplikasi bisa diakses di:

```
https://<username>.github.io/<nama-repo>/
```

---

## 📱 Screenshot & Fitur

### 🏠 Beranda
Dashboard utama yang menampilkan ringkasan real-time:
- **Statistik Anggota** — Total, Berjalan, Macet, Lunas
- **Ringkasan Pinjaman** — Modal pokok vs Modal + Bunga
- **Ringkasan Angsuran** — Terkumpul hari ini & bulan ini
- **Daftar Pinjaman Terbaru**
- **Notifikasi Tutup Buku** — Otomatis muncul di tanggal 1–3 setiap bulan

---

### 👥 Anggota
Manajemen data anggota koperasi:
- Tambah, edit, dan hapus anggota
- **Status bebas input** — pilih dari chip (Aktif, Tidak Aktif, Calon, Keluar, Macet) atau ketik status sendiri
- Deteksi **nama duplikat real-time** dengan debounce:
  - ❌ Nama sama persis → tombol Simpan di-*disable* otomatis
  - ⚠️ Nama mirip → peringatan kuning, bisa tetap lanjut
  - ✅ Nama bersih → konfirmasi hijau
- Info anggota: No. HP, KTP, alamat, tabungan, status pinjaman aktif

---

### 💳 Pinjaman
Pencatatan dan simulasi pinjaman:

**Rumus Angsuran:**
```
Angsuran = (Pokok + (Pokok × Bunga%)) ÷ Tenor
```

Contoh:
```
Rp 500.000 × 20% = Rp 100.000 (bunga)
Rp 500.000 + Rp 100.000 = Rp 600.000 (total)
Rp 600.000 ÷ 24 hari = Rp 25.000/hari (angsuran)
```

**Potongan Pencairan:**
```
Dana Cair = Pokok − 5% (Admin) − 5% (Tabungan)
```

Fitur:
- Kalkulator angsuran **real-time** sebelum simpan
- Pilihan Tempo: **Harian / Mingguan / Bulanan**
- Tenor bebas input (jumlah angsuran)
- Persentase bunga bebas input
- Progress bar visual per pinjaman
- **Draft Tagihan** langsung dari data pinjaman

---

### 💵 Angsuran
Pembayaran dan pencatatan cicilan:
- Pilih anggota → tampil semua tagihan aktif
- Bayar angsuran dengan jumlah bebas (bisa lebih dari normal)
- Riwayat pembayaran per pinjaman
- Status otomatis berubah menjadi **Lunas** saat sisa = 0
- **Draft Tagihan** langsung dari halaman angsuran

---

### 📄 Draft Tagihan
Surat tagihan yang bisa dicetak atau disalin:
- **Header kop** — Nama koperasi, tanggal cetak, nomor referensi
- **Data peminjam** — Nama, tgl pinjaman, status
- **Rincian pinjaman** — Pokok, bunga, total, angsuran/tempo, tenor
- **Potongan pencairan** — Admin 5%, tabungan 5%, dana diterima
- **Posisi saat ini** — Angsuran ke-, sisa utang, sudah terbayar
- **Progress bar** visual
- **Riwayat 5 pembayaran terakhir**
- **Catatan & tanda tangan** di bagian bawah
- Tombol **🖨️ Print / Simpan PDF** dan **📋 Salin Teks**

---

### 📈 Laporan
Laporan keuangan dengan filter periode:

**Filter Cepat:**
| Tombol | Periode |
|--------|---------|
| 📅 Hari Ini | Tanggal hari ini |
| 🗓️ Bulan Ini | Awal bulan hingga hari ini |
| ⬅️ Bulan Lalu | Seluruh bulan sebelumnya |
| 📊 Tahun Ini | 1 Januari hingga hari ini |
| 📉 Tahun Lalu | Seluruh tahun sebelumnya |
| 🔍 Semua | Semua data tanpa filter |

Filter tanggal manual (dari–sampai) juga tersedia.

Isi laporan:
- Ringkasan total pinjaman, bunga, tagihan, angsuran terkumpul
- Pendapatan admin & tabungan masuk
- Tabel detail pinjaman
- Riwayat semua pembayaran

---

### 🔍 Audit Keuangan
Analisis mendalam keuangan koperasi:

**6 Section Audit:**
1. **⚠️ Temuan Audit** — Deteksi anomali otomatis:
   - Angsuran *orphan* (tidak punya data pinjaman)
   - Status tidak konsisten (tenor selesai tapi masih "berjalan")
   - Sisa utang negatif (lebih bayar)
   - Nama anggota duplikat
   - Rasio macet ≥ 30% (peringatan risiko tinggi)

2. **💰 Arus Kas** — Kas masuk vs kas keluar vs saldo bersih

3. **📋 Posisi Piutang** — Total sisa utang semua pinjaman aktif + rasio macet

4. **📊 Statistik Pinjaman** — Ringkasan per periode dengan efektivitas penagihan %

5. **🏦 Posisi Tabungan** — Total & rata-rata tabungan per anggota

6. **👥 Rincian per Anggota** — Tabel: pinjaman, terbayar, sisa, status, progress

7. **🎯 Analisis Risiko** — Badge risiko (🟢 Rendah / 🟠 Sedang / 🔴 Tinggi) + peringatan pembayaran tertinggal

8. **📜 Audit Trail** — Log semua transaksi kronologis (pinjaman keluar + angsuran masuk)

---

### 📋 Profil
Tabel ringkasan semua anggota dalam satu layar:

| Kolom | Keterangan |
|-------|-----------|
| Nama | Nama lengkap anggota |
| Tgl Pinjaman | Tanggal pinjaman aktif |
| Status | Status pinjaman (badge warna) |
| Pinjaman | Nominal pokok pinjaman |
| Sisa Utang | Sisa yang belum dibayar |
| Tabungan | Saldo tabungan (dari potongan 5%) |
| Sisa Tenor | Angsuran tersisa / total |

**Tutup Buku Bulanan:**
- Buat snapshot data per periode
- Arsip riwayat tutup buku
- Preview data sebelum konfirmasi
- Notifikasi otomatis tiap awal bulan

---

## 🗂️ Struktur File

```
koperasiku/
├── index.html     ← Seluruh aplikasi (HTML + CSS + JS dalam 1 file, ±103KB)
├── README.md      ← Dokumentasi ini
└── .gitignore     ← Abaikan file sistem & editor
```

---

## 💾 Penyimpanan Data

| Layer | Keterangan |
|-------|-----------|
| **LocalStorage** | Penyimpanan lokal di browser — aktif otomatis, bekerja offline |
| **Firebase Firestore** | Sinkronisasi cloud — aktif setelah konfigurasi Firebase diisi |

Data yang disimpan:
- `kop_anggota` — Data anggota
- `kop_pinjaman` — Data pinjaman
- `kop_angsuran` — Riwayat pembayaran
- `kop_tutupbuku` — Arsip tutup buku

---

## 🔥 Setup Firebase

### Langkah 1 — Buat Project Firebase
1. Buka [console.firebase.google.com](https://console.firebase.google.com)
2. Klik **"Add project"** → isi nama → klik **Continue**
3. Klik **"Create project"**

### Langkah 2 — Daftarkan Aplikasi Web
1. Di halaman project, klik ikon **`</>`** (Web)
2. Isi nama app → klik **"Register app"**
3. Salin `firebaseConfig` yang muncul

### Langkah 3 — Aktifkan Firestore
1. Di menu kiri: **Build → Firestore Database**
2. Klik **"Create database"**
3. Pilih **"Start in test mode"** → pilih region → **Enable**

### Langkah 4 — Set Rules Firestore
Di tab **Rules**, ganti isinya dengan:
```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if true;
    }
  }
}
```
> ⚠️ Rules di atas untuk testing. Tambahkan autentikasi sebelum digunakan publik.

### Langkah 5 — Isi Konfigurasi di index.html
Cari bagian ini di `index.html` dan ganti dengan config Anda:

```javascript
const firebaseConfig = {
  apiKey: "GANTI_API_KEY",
  authDomain: "GANTI_PROJECT.firebaseapp.com",
  projectId: "GANTI_PROJECT_ID",
  storageBucket: "GANTI_PROJECT.appspot.com",
  messagingSenderId: "GANTI_SENDER_ID",
  appId: "GANTI_APP_ID",
  measurementId: "GANTI_MEASUREMENT_ID"
};
```

---

## 🚀 Deploy ke GitHub Pages

### Cara Mudah (Tanpa Terminal)

**1. Buat Repository**
- Login ke [github.com](https://github.com) → klik **"New"**
- Isi nama repo (contoh: `koperasiku`) → pilih **Public** → **"Create repository"**

**2. Upload File**
- Di halaman repo kosong, klik **"uploading an existing file"**
- Drag & drop file: `index.html`, `README.md`, `.gitignore`
- Klik **"Commit changes"**

**3. Aktifkan GitHub Pages**
- Klik tab **Settings** → klik **Pages** (menu kiri)
- Di **Source**: Branch = `main`, Folder = `/ (root)`
- Klik **Save**
- Tunggu 1–2 menit → link aplikasi muncul otomatis ✅

---

### Cara Via Git (Terminal)

```bash
# Clone atau init repo
git init
git add .
git commit -m "feat: initial commit KoperasiKu"
git branch -M main
git remote add origin https://github.com/<username>/<repo>.git
git push -u origin main
```

Lalu aktifkan GitHub Pages dari Settings seperti di atas.

---

### Update Aplikasi (Setelah Edit)

```bash
git add index.html
git commit -m "fix: update fitur tagihan"
git push
```

GitHub Pages otomatis deploy ulang dalam ~1 menit.

---

## ⌨️ Cara Penggunaan

### Alur Kerja Normal

```
1. Daftar Anggota
   Tab Anggota → "+ Tambah" → isi data → Simpan

2. Buat Pinjaman
   Tab Pinjaman → "+ Pinjaman" → pilih anggota → isi nominal,
   bunga, tempo, tenor → lihat simulasi → Simpan

3. Bayar Angsuran
   Tab Angsuran → pilih anggota → "💵 Bayar Angsuran" → 
   isi tanggal & jumlah → Bayar

4. Cetak Tagihan
   Tab Pinjaman atau Angsuran → "📄 Draft Tagihan" → 
   Print atau Salin Teks

5. Laporan Bulanan
   Tab Laporan → klik "Bulan Ini" → lihat ringkasan

6. Tutup Buku (awal bulan)
   Tab Profil → "📒 Tutup Buku" → pilih periode → Konfirmasi

7. Audit Keuangan
   Tab Laporan → klik "🔍 Audit" → pilih periode → Generate
```

---

## 🛠️ Teknologi

| Teknologi | Keterangan |
|-----------|-----------|
| HTML5 | Struktur & markup |
| CSS3 | Styling, animasi, layout (Flexbox/Grid) |
| Vanilla JavaScript | Logika aplikasi (ES6+) |
| Firebase Firestore | Database cloud (opsional) |
| Firebase Analytics | Analitik penggunaan (opsional) |
| Google Fonts | Plus Jakarta Sans, JetBrains Mono |
| localStorage | Penyimpanan offline di browser |

**Tidak ada:**
- ❌ Framework (React, Vue, Angular)
- ❌ Build tool (webpack, vite)
- ❌ Node.js / npm
- ❌ Backend server

---

## 🙋 FAQ

**Q: Apakah data hilang kalau browser di-clear?**  
A: Data di localStorage akan hilang jika cache browser dihapus. Gunakan Firebase untuk penyimpanan permanen di cloud.

**Q: Bisa dipakai offline?**  
A: Ya, seluruh fitur bekerja offline. Data tersimpan di localStorage. Sinkronisasi Firebase hanya butuh koneksi internet.

**Q: Apakah bisa diakses dari HP?**  
A: Ya, desain responsif dan dioptimalkan untuk mobile (max-width 480px).

**Q: Bagaimana cara backup data?**  
A: Gunakan Firebase Firestore — data otomatis tersimpan di cloud dan bisa diakses dari perangkat manapun.

**Q: Bisa multi-user (dipakai banyak orang)?**  
A: Bisa, asalkan Firebase sudah dikonfigurasi. Semua user akan melihat data yang sama dari Firestore. Untuk keamanan, tambahkan Firebase Authentication.

---

## 📝 Lisensi

MIT License — bebas digunakan, dimodifikasi, dan didistribusikan.

---

## 👨‍💻 Kontribusi

Pull request dan issue sangat diterima. Untuk perubahan besar, buka issue terlebih dahulu untuk diskusi.

---

<div align="center">
  Dibuat dengan ❤️ untuk kemudahan pengelolaan koperasi harian
</div>
