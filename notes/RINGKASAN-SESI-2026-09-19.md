# Ringkasan Sesi — 15–19 September 2026

Dua permintaan terpisah dikerjakan dalam sesi ini: (1) tracker assignment mingguan sebagai artifact HTML, dan (2) kompilasi riset topik skripsi ke Google Docs milik Arya. Dokumen ini merangkum keduanya supaya bisa dibaca ulang tanpa konteks percakapan sebelumnya.

---

## 1. Tracker Assignment (Artifact HTML)

**Permintaan awal:** tiru template Google Sheets "Assignment Tracker" (kolom Subject/Assignment/Status/Time/Start date/Due on) sebagai artifact, dengan tanggal Senin–Sabtu saja dan isi "sudah ngapain aja".

**Hasil akhir:** artifact HTML — `https://claude.ai/artifact/RY94N4kWUSXA95KgF6hmjQ`

### Iterasi
1. **v1** — isi awal ditiru langsung dari screenshot (topik chatbot emosi Plutchick), lalu disadari itu bukan skripsi Arya sendiri.
2. **v2** — dibongkar total, diganti isi dari riset topik skripsi Arya sendiri (blending batu bara Adaro), memakai konten dari `CATATAN-RISET-TOPIK.md` dan memory. Struktur: 8 assignment selesai (riset topik s.d. dokumen permintaan data), 1 in-progress (cek repositori UI), sisanya rencana s.d. sidang. Jalur kritis (konfirmasi judul → kirim data tahap 1 → verifikasi & tahap 2) ditandai visual merah.
3. **v3** — kolom dikunci ke vocabulary tracker asli: **Subject** dari 7 pilihan (paper review, code review/analysis, coding, writing book, writing paper, dataset labeling, dataset collecting), **Status** dari 4 pilihan (Not started/In progress/Skipped/Done), tanggal format `M/DD/YYYY`.
4. **v4 (final)** — teks assignment dipadatkan jadi satu baris gaya kalimat kerja ringkas (mengikuti contoh gaya teman Arya), tanpa sub-keterangan.

### Catatan
- `Writing book` dan `Skipped` sengaja tidak terpakai — tidak ada aktivitas yang cocok, tidak dipaksakan.
- Asumsi tanggal sidang (13 Feb 2027) murni perkiraan mundur dari akhir semester, belum ada kalender resmi.

---

## 2. Kompilasi Riset ke Google Docs

**Permintaan:** compile "semuanya" — struktur skripsi benchmark Aldrian, proses bisnis end-to-end Adaro, opsi topik optimasi + data + PT terkait, state of the art, dan prior art — ke Google Docs `Arya_Skripsi Progress`, dengan referensi format dari doc lain (fleksibel, tidak wajib ditiru persis), plus sertakan screenshot paper dari folder `materials/`.

**Dokumen tujuan:** `Arya_Skripsi Progress` → tab **Week 3**
`https://docs.google.com/document/d/1YYMAgi-jGrNmiGom_3zQ3jVWEfMwlc3rLIRO9aq97PY/edit`

**Doc referensi format** ("Javana Paper Review"): dipakai hanya sebagai inspirasi longgar — pola kotak topik + tabel "Paper | Findings | Comparison" — tidak ditiru literal.

### Sumber paper (folder `materials/`)
5 paper diidentifikasi dan di-screenshot halaman sampul/abstraknya (dikirim ke user via file terpisah, bukan disisipkan inline di doc):

| File sumber | Identitas |
|---|---|
| `Rancang Bangun Sistem Optimisasi...Feronikel.pdf` | Skripsi benchmark Aldrian Raffi Wicaksono (2025) |
| `1-s2.0-S0952197624012302-main.pdf` | Liu et al., *Coal allocation optimization...*, EAAI 137 (2024) 109072 |
| `1-s2.0-S0016236125025025-main.pdf` | Li et al., *Optimizing coal blending...*, Fuel 406 (2026) 136777 |
| `journal.pone.0331208.pdf` | Li et al., *RL-enhanced multi-objective optimization...*, PLOS ONE 20(9) (2025) |
| `epjconf_gcmm2025_02001.pdf` | Nimbalkar, Kashyap & Nagaraju, *ML Surrogated Coal Blend Optimisation...*, EPJ Web of Conf. 354 (2026) |

### Struktur isi Google Doc (tab Week 3)
1. **Judul + intro** — konteks & tanggal disusun.
2. **Struktur Skripsi Benchmark — Aldrian (2025)** — 10 bullet aspek (domain, data, model prediktif, optimizer, variabel keputusan, fungsi objektif, kendala, evaluasi, hasil).
3. **Proses Bisnis End-to-End Adaro (PT AAI)** — 5 subbagian (H2): struktur grup & posisi AMT, apa yang ditambang, rantai nilai batu bara (9 tahap), struktur biaya (Semester I 2026), posisi AMT dalam proses.
4. **Opsi Topik Optimasi, Data, dan Entitas Terkait** — 5 kandidat topik diperingkat, tiap satu mencantumkan data yang dibutuhkan + PT/entitas Adaro yang memegangnya + tingkat kepastian data.
5. **State of the Art (Literatur Internasional)** — 4 paper dengan metode & hasil kunci, ditandai `[Lampiran: nama-file.png]` untuk menunjuk ke screenshot terkait.
6. **Prior Art — Indonesia (Optimisasi Blending, Non-ML)** — 6 institusi/jurnal.
7. **Prior Art di Teknik Komputer UI — Grup Riset Dr. Mia Rizkinia** — 6 skripsi RKEF (termasuk Aldrian sebagai benchmark), plus catatan pergeseran metode standar dan domain batu bara yang masih kosong.
8. **Penutup** — sumber (`CATATAN-RISET-TOPIK.md` + 5 paper), catatan lampiran.

Tabel asli di doc referensi diganti jadi bullet list berlabel ("Label — value") karena insert-table Google Docs lewat otomasi browser terbukti sangat tidak stabil di sesi ini (lihat catatan teknis di bawah).

### Catatan teknis / kendala selama pengerjaan
- **Editing dilakukan via Chrome asli (claude-in-chrome)**, bukan browser sandbox, karena perlu login akun Google Arya (`aryautomo21@gmail.com`).
- **Klik koordinat mentah tidak reliable** — viewport/scroll bergeser antar-panggilan sehingga koordinat dari screenshot sebelumnya sering meleset (kadang offset ~50px). Pola yang akhirnya reliable:
  - Style heading (Heading 1/2) diterapkan lewat toolbar dropdown, dicari via `find()` lalu diklik via `ref` — **bukan** koordinat mentah, dan **selalu diverifikasi via screenshot sebelum mengetik teks**.
  - Navigasi ke akhir dokumen pakai tombol **Down berulang** (aman, tidak overshoot) alih-alih klik langsung ke paragraf kosong.
  - Bullet list terdeteksi otomatis cukup dengan mengetik `"- teks"` di awal baris (fitur "Automatically detect lists" Google Docs).
  - Markdown-style shortcut (`# heading`, `**bold**`) **tidak berfungsi** via automation meski "Enable Markdown" diaktifkan di Preferences.
- **Insert Table via menu grid gagal berulang kali** — panel grid-picker selalu tertutup sebelum klik kedua sempat mendarat di sel yang benar, walau dalam satu batch. Diputuskan beralih ke bullet list, bukan tabel native.
- **Ada satu artefak tersisa**: kotak kosong bergaris di bawah heading "2.4 Struktur Biaya AAI" (kemungkinan sisa interaksi tak sengaja dengan menu Insert → Smart chips saat eksplorasi cara insert tabel). Sudah dicoba dihapus lewat berbagai cara (select+delete, clear formatting, cek Table/Borders options) tapi tetap muncul balik setelah reload — ternyata bukan gambar maupun tabel asli (opsi Table/Borders selalu abu-abu/disabled saat kursor di dalamnya). **Belum terhapus** — perlu diklik manual sekali lalu ditekan Delete oleh Arya sendiri (~2 detik).
- Sempat ada insersi gambar tak sengaja (preview tabel "27. BEBAN POKOK PENDAPATAN" dari data FS AAI) yang berhasil dihapus permanen.
- Semua kerusakan teks tak sengaja selama proses (mis. karakter terpotong di paragraf "Proses paralel...") sudah diperiksa dan diperbaiki.

### Yang perlu ditindaklanjuti Arya
1. Hapus kotak kosong bergaris di bawah heading "2.4 Struktur Biaya AAI" (klik sekali → Delete).
2. Opsional: tempel 5 screenshot paper (dikirim terpisah via chat) ke posisi `[Lampiran: ...]` yang relevan di doc.
3. Tanggal sidang di tracker HTML (13 Feb 2027) masih asumsi — sesuaikan begitu kalender sidang resmi keluar.

---

## Berkas & tautan terkait
- Tracker HTML: `https://claude.ai/artifact/RY94N4kWUSXA95KgF6hmjQ`
- Google Docs kompilasi riset: `https://docs.google.com/document/d/1YYMAgi-jGrNmiGom_3zQ3jVWEfMwlc3rLIRO9aq97PY/edit` (tab **Week 3**)
- Catatan riset sumber: `CATATAN-RISET-TOPIK.md` (folder SKRIPSI)
- Paper acuan: folder `materials/` (5 file PDF)
- Screenshot sampul/abstrak 5 paper: dikirim via chat (file terpisah, nama sesuai yang dirujuk `[Lampiran]` di Google Doc)
