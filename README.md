# Sistem Web Arsip As-Built Drawing & Opname Lapangan (PDAM / BUMD)

Prototipe antarmuka sistem pengelolaan berkas gambar teknik *As-Built Drawing* dan lembar hasil *opname* survei lapangan instalasi pipa air minum berbasis **Pure HTML5 + CSS3** (Zero JavaScript, Bebas Framework, Zero Dependencies).

Dibangun dengan arsitektur **Atomic Design**, mematuhi standar kontras warna **WCAG 2.1 AA**, target sentuh minimum $\ge 44 \times 44\text{px}$, dan mendukung dua lingkungan operasional: **Web Responsive Desktop/Tablet** dan **Mobile App View Material 3 (PWA Mock)**.

---

## 🌟 Fitur Utama

### A. Web Responsive (Desktop 1280px+ & Tablet 768px-1024px)
1. **Login & Simulasi Role Switcher (`index.html`)**: Pintu masuk cepat untuk pengujian berbagai peran (Approver L2, Pengawas L1/L3, Admin GIS, dan Petugas Lapangan).
2. **Dashboard Eksekutif (`dashboard.html`)**: Ringkasan metrik dokumen, grafik donat komposisi berkas (CSS-only conic gradient), progress bar deviasi material pipa, dan antrean verifikasi mendesak.
3. **Katalog Dokumen As-Built (`dokumen-list.html`)**: Filter terpadu (pencarian, zona DMA, tipe pipa, status chip), tabel inventaris responsif, dan modal unggah dokumen (`#modal-upload` via CSS `:target`).
4. **Viewer Gambar As-Built & Split Metadata (`dokumen-detail.html`)**:
   - Kanvas gambar teknik SVG interaktif (simulasi CAD 65% lebar layar) lengkap dengan jalur pipa HDPE, gate valve, meter induk DMA, penanda deviasi, dan stempel stempel verifikasi L1.
   - Panel metadata 35% lebar layar memuat spesifikasi pipa, riwayat versi revisi berkas, serta modal aksi putusan reviewer (Setujui, Minta Revisi, Tolak).
5. **Monitoring Opname Lapangan (`opname-monitoring.html`)**: Matriks perbandingan DED (Desain) vs Terpasang Fisik, toleransi SNI/PDAM, dan galeri dokumentasi foto geotagged GPS.
6. **Pusat Persetujuan Berjenjang 3-Level (`approval-inbox.html`)**:
   - Level 1: Pengawas Lapangan (Verifikasi fisik & foto).
   - Level 2: Kasi Perencanaan & Pengawasan (Verifikasi kalkulasi teknis & deviasi DED).
   - Level 3: Manajer Teknik / Direksi (Pengesahan formal SK).
   - Dilengkapi tab switching murni CSS dan dialog putusan cepat.
7. **Master DMA & Audit Trail (`admin-master.html`)**: Pengelolaan batas hidrolis zona District Meter Area dan log aktivitas sistem yang tercatat secara kronologis.

### B. Mobile App View Material 3 (`/app/index.html`)
- **Tampilan Smartphone Terpusat:** Di desktop ditampilkan dalam mock frame smartphone realistis (390px $\times$ 844px); pada perangkat ponsel otomatis menjadi layar penuh `100dvh` dengan penyesuaian `safe-area-inset-*`.
- **Indikator Mode Offline:** Banner visual penanda blank spot galian pipa ("Mode Offline: 3 data tersimpan di perangkat lokal").
- **5 Tab Lapangan Material 3 (CSS Tab Switcher):**
  1. **Beranda:** Profil surveyor, ringkasan tugas harian, kartu SPK aktif, dan Floating Action Button (FAB).
  2. **Tugas & Form Opname:** Filter chip tugas, status GPS Lock (-6.20882, 106.84561), accordion parameter fisik pipa tertanam, dokumentasi foto kamera mock, dan bottom-sheet konfirmasi kirim data (`#sheet-kirim`).
  3. **Viewer Gambar Lapangan:** Sketsa skematik pipa SVG mobile-friendly dengan toggle legenda simbol.
  4. **Status Approval Tim:** Stepper vertikal riwayat verifikasi berjenjang L1 &rarr; L2 &rarr; L3 beserta catatan koreksi inspektur.
  5. **Profil & Sinkronisasi:** Info NIP/wilayah tugas, monitor kapasitas memori cache offline (42 MB / 500 MB), dan simulasi sinkronisasi data manual (`#sheet-sync`).

---

## 📁 Struktur Direktori

```text
demo-prototipe/
├── index.html               # Halaman Login & Role Switcher
├── dashboard.html           # Dashboard Monitoring Eksekutif & Chart CSS
├── dokumen-list.html        # Katalog Dokumen As-Built & Modal Upload
├── dokumen-detail.html      # Viewer Lembar Gambar CAD (SVG) & Split Metadata
├── opname-monitoring.html   # Matriks Deviasi DED vs Terpasang & Foto Geotag
├── approval-inbox.html      # Pusat Persetujuan Dokumen 3-Level (L1-L3)
├── admin-master.html        # Master Data DMA & Log Audit Sistem
├── app/
│   └── index.html           # Shell Aplikasi Mobile Surveyor (5 Tab M3)
├── css/
│   ├── 00-tokens.css        # Variabel Warna, Spasi 4/8px, Radius, Elevasi, Tema
│   ├── 01-reset.css         # CSS Reset, Anti-Sudut Lancip, Target Sentuh >= 44px
│   ├── 02-components.css    # Reusable Atoms, Molecules, Modal & Bottom Sheet :target
│   ├── 03-web-layout.css    # Layout Responsive Web Shell, Sidebar Drawer
│   └── 04-app-view.css      # Frame Smartphone Desktop & Safe-Area 100dvh Mobile
└── .github/
    └── workflows/
        └── deploy-pages.yml # Otomasi Deployment GitHub Pages
```

---

## 🎨 Spesifikasi Desain & Aksesibilitas
- **Bebas Sudut Lancip:** Seluruh tombol, form input, kartu, modal, dan badge wajib memiliki `border-radius` membulat (tanpa sudut lancip).
- **Target Sentuh Minimum:** Bounding box kontrol interaktif $\ge 44\text{px}$ (khusus bottom navigation mobile $52\text{px}$).
- **Kontras WCAG AA:** Rasio kontras teks terhadap latar belakang minimal 4.5:1.
- **Responsif 360px:** Zero horizontal overflow pada layar terkecil smartphone (360px).
- **Teknologi Interaktivitas:**
  - Dialog Modal & Bottom Sheet: `:target` selector.
  - Tab Navigasi: CSS Hidden Radio Selector (`:checked ~ .content`).
  - Accordion: Tag semantik `<details><summary>`.

---

## 🚀 Menjalankan Secara Lokal
Cukup buka berkas `index.html` langsung di browser modern mana pun (Google Chrome, Mozilla Firefox, Safari, Microsoft Edge). Tidak memerlukan Node.js, npm, live-server, atau dependensi eksternal.
