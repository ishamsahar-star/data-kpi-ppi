# IEEP POLIMAS Dashboard — Plan

## Top-Level Overview

Bina sebuah **dashboard HTML interaktif satu halaman** untuk meringkaskan dan memaparkan data program IEEP (Industrial Expert Enrichment Program) Jabatan Kejuruteraan Elektrik (JKE) POLIMAS bagi tempoh 2024–2026.

Data sumber diambil daripada tiga fail Excel yang telah dianalisis:
- `SENARAI AKTIVITI PPI 2024 beserta PLO.xlsx` — 12 aktiviti
- `SENARAI AKTIVITI PPI 2025 beserta PLO.xlsx` — 10 aktiviti
- `LIST IEEP 2026.xlsx` — 5 aktiviti

Dashboard dibina sebagai **fail HTML tunggal** (tidak memerlukan pelayan web), gaya profesional biru gelap/putih, sesuai untuk pembentangan kepada pengurusan POLIMAS.

Carta menggunakan library **Chart.js** (CDN) — tiada kebergantungan lain.

---

## Sub-Tasks

---

### Sub-Task 1 — Struktur HTML & Gaya (Layout & Styling)

**Intent:** Bina kerangka HTML asas dengan CSS gaya profesional biru gelap/putih, header institusi, dan layout grid untuk semua bahagian dashboard.

**Expected Outcomes:**
- Fail `ieep-dashboard.html` wujud di workspace root
- Header menunjukkan nama institusi dan tajuk dashboard
- Layout grid responsif untuk kad statistik dan bahagian carta
- Warna skema: biru gelap (#1a3a5c), putih (#ffffff), aksen emas/kuning (#f0a500)

**Todo List:**
1. Cipta fail `ieep-dashboard.html` dengan struktur HTML5 asas
2. Tambah CSS inline — warna, font, grid layout, kad statistik, header
3. Tambah placeholder sections untuk setiap bahagian dashboard
4. Import Chart.js via CDN dalam `<head>`

**Relevant Context:**
- Tiada fail HTML sedia ada — fail baru perlu dicipta
- Semua CSS dan JS dalam satu fail sahaja (standalone)

**Status:** [ ] pending

---

### Sub-Task 2 — Kad Ringkasan Statistik (KPI Cards)

**Intent:** Paparkan 4 kad KPI utama di bahagian atas dashboard — jumlah aktiviti, jumlah jam, bilangan industri terlibat, dan bilangan pelajar yang terlibat.

**Expected Outcomes:**
- 4 kad KPI ditunjukkan dalam satu baris
- Setiap kad mempunyai ikon, nilai besar, dan label
- Data dikira daripada semua 3 tahun (2024, 2025, 2026)

**Data KPI:**
- Jumlah Aktiviti: 27 (12 + 10 + 5)
- Jumlah Jam (DET/DEP/DEE): DET=107.5j, DEP=81j, DEE=95j
- Industri/Agensi Terlibat: 5 (TNB, Quantum Solar, RTM, KTM/MYRA, BEM/ETAC)
- Anggaran Pelajar Terlibat: 1000+

**Todo List:**
1. Tambah seksyen KPI cards dalam HTML
2. Masukkan nilai data dari semua 3 tahun
3. Styling kad dengan ikon Unicode dan warna aksen

**Relevant Context:**
- Jumlah jam diambil dari baris JUMLAH JAM dalam setiap fail Excel
- Jumlah aktiviti dikira dari baris data (bukan baris kosong)

**Status:** [ ] pending

---

### Sub-Task 3 — Carta Bilangan Aktiviti & Jam Mengikut Tahun

**Intent:** Paparkan dua carta bersebelahan — carta bar bilangan aktiviti per tahun, dan carta bar jam mengikut program (DET/DEP/DEE) per tahun.

**Expected Outcomes:**
- Carta 1: Bar chart — Bilangan Aktiviti 2024 vs 2025 vs 2026
- Carta 2: Grouped bar chart — Jam DET/DEP/DEE mengikut tahun
- Kedua carta menggunakan Chart.js dengan warna yang konsisten

**Data Carta:**
- Aktiviti: 2024=12, 2025=10, 2026=5
- Jam DET: 2024=37, 2025=52.5, 2026=18
- Jam DEP: 2024=33, 2025=28, 2026=20
- Jam DEE: 2024=37, 2025=40, 2026=18

**Todo List:**
1. Tambah dua elemen `<canvas>` untuk Chart.js
2. Tulis JavaScript untuk render kedua carta
3. Tetapkan warna konsisten — DET=biru, DEP=oren, DEE=hijau

**Relevant Context:**
- Gunakan Chart.js `type: 'bar'` dengan `grouped` mode untuk carta jam

**Status:** [ ] pending

---

### Sub-Task 4 — Carta Pai Jenis Aktiviti & Carta Industri

**Intent:** Paparkan carta pai jenis aktiviti dan senarai syarikat/agensi industri yang terlibat sepanjang 2024–2026.

**Expected Outcomes:**
- Carta pai — kategori: Lawatan Sambil Belajar, Kursus/Bengkel, Keselamatan, Ceramah Industri, Kerjasama Industri
- Senarai industri dalam bentuk badge/tag yang menarik

**Data Carta Pai:**
- Lawatan Sambil Belajar: 11
- Kursus/Bengkel Teknikal: 9
- Keselamatan & Kesedaran: 2
- Ceramah Industri: 2
- Kerjasama Industri: 3

**Industri:**
- TNB (Tenaga Nasional Bhd), Quantum Solar Park Sdn Bhd, RTM Perlis, KTM/Akademi MYRA, BEM/ETAC

**Todo List:**
1. Tambah canvas untuk doughnut chart jenis aktiviti
2. Tambah seksyen industri dengan kad/badge untuk setiap agensi
3. Warna konsisten dengan skema dashboard

**Status:** [ ] pending

---

### Sub-Task 5 — Jadual Senarai Aktiviti Lengkap dengan Penapis

**Intent:** Paparkan jadual lengkap semua 27 aktiviti dengan fungsi penapis (filter) mengikut tahun, dan opsyen carian teks.

**Expected Outcomes:**
- Jadual dengan lajur: Bil, Aktiviti, Program Terlibat, Tarikh, Jam, PIC
- Dropdown penapis Tahun (Semua / 2024 / 2025 / 2026)
- Kotak carian teks untuk menapis nama aktiviti
- Baris jadual berwarna berselang-seli untuk keterbacaan

**Todo List:**
1. Bina data array JavaScript untuk semua 27 aktiviti
2. Render jadual dinamik menggunakan JavaScript
3. Tambah dropdown penapis tahun dan input carian
4. Tambah logik JS untuk menapis dan memaparkan semula jadual

**Relevant Context:**
- Data diambil dari analisis tiga fail Excel (Sub-Task 1 dalam konteks asal)
- PIC merujuk kepada nama pensyarah yang bertanggungjawab

**Status:** [ ] pending

---

### Sub-Task 6 — Footer & Pengesahan Akhir

**Intent:** Tambah footer dengan maklumat institusi, tarikh jana laporan, dan pastikan dashboard berfungsi sepenuhnya sebagai fail HTML standalone.

**Expected Outcomes:**
- Footer menunjukkan nama jabatan, politeknik, dan tahun
- Semua carta dirender dengan betul apabila fail dibuka dalam pelayar
- Fail boleh dibuka terus tanpa pelayan web

**Todo List:**
1. Tambah footer HTML
2. Semak semua script Chart.js berfungsi tanpa ralat
3. Pastikan CDN Chart.js dimuatkan dari internet (bukan fail tempatan)

**Status:** [ ] pending
