# Catatan Riset Topik Skripsi — Adaro

Disusun: 15 September 2026
Mahasiswa: Muhammad Arya Wiandra Utomo, Teknik Komputer FT UI
Posisi: Business Analyst Intern, PT Adaro Mining Technologies (AMT)

Dokumen ini merangkum hasil riset pencarian topik. Ditulis agar bisa dibaca ulang tanpa konteks percakapan sebelumnya.

---

## 1. Situasi

Mencari topik skripsi bertema optimisasi berbasis machine learning menggunakan data Adaro. Benchmark: skripsi Aldrian Raffi Wicaksono (Teknik Komputer FT UI, 2025), "Rancang Bangun Sistem Optimisasi Pemakaian Batubara Pada Proses Produksi Feronikel", pembimbing Dr. Eng. Mia Rizkinia.

Status izin data: atasan di AMT menjawab **"Ya, namun boleh coba dilihat dulu ya nanti datanya apa saja yg diinginkan."** Lampu hijau bersyarat — perlu mengajukan daftar data lebih dulu. Jalur ke direksi (Bu Santi) sudah pernah dibuka oleh intern sebelumnya (Javen) dengan respons positif.

Arahan pembimbing: meniru pendekatan Aldrian dengan data Adaro sudah dianggap cukup.

---

## 2. Struktur Grup Adaro (penting, sering tertukar)

Grup pecah dua sejak Desember 2024.

**PT Alamtri Resources Indonesia Tbk (IDX: ADRO)** — nama baru dari Adaro Energy Indonesia. Sudah melepas batu bara termal.
- Alamtri Minerals Indonesia (ADMR) — batu bara metalurgi, tambang Lampunut (hard coking coal) dan Haju (semi-soft), merek Enviromet
- Kalimantan Aluminium Industry (KAI) — smelter aluminium 500.000 ton, komisioning sebagian Q4 2025
- Saptaindra Sejati (SIS) — kontraktor tambang, 2.500+ alat berat
- Alamtri Power Indonesia — ketenagalistrikan

**PT Adaro Andalan Indonesia Tbk (AAI)** — spin-off Desember 2024, batu bara termal murni, 2.968 karyawan tetap. **AMT ada di bawah entitas ini.**
- Adaro Indonesia (AI) — pit Tutupan dan Wara, Kalsel, 23.942 ha, merek Envirocoal
- Balangan Coal: SCM, LSA, PCS — tiga IUP @2.500 ha
- Mustika Indah Permai (MIP) — Lahat, Sumsel
- Adaro Logistics — Kelanis, IBT, IMPT, MBP, HBI
- Kaltara Power Indonesia (KPI) — pembangkit disewakan ke smelter KAI, aset US$1,19 miliar
- Adaro Tirta Mandiri — pengolahan air, lima anak usaha
- Adaro Mining Technologies (AMT) — jasa, berdiri 2023, aset US$15,7 juta

**Peringatan:** angka operasional di Annual Report ADRO 2025 (produksi 7,41 juta ton, pengupasan 26,33 juta bcm, nisbah kupas 3,55x) adalah milik Alamtri Minerals, **bukan AAI**. Jangan dikutip sebagai angka AAI.

---

## 3. Apa yang Ditambang dan Sampai Mana Hilirnya

Hanya batu bara. Tidak ada nikel, emas, bauksit, tembaga.

Batu bara metalurgi dijual mentah — Adaro tidak membuat kokas maupun baja. Batu bara termal dijual, sebagian dibakar sendiri untuk listrik.

Ada smelter aluminium, tapi bukan dari bijih sendiri. Adaro tidak menambang bauksit; alumina dibeli. Integrasinya lewat energi, bukan material: batu bara termal menjadi listrik di pembangkit KPI, listrik disewakan ke KAI, KAI melebur aluminium.

**Implikasi penting:** Adaro tidak punya proses pirometalurgi atas bijihnya sendiri. Tidak ada padanan RKEF. Karena itu setting skripsi Aldrian tidak bisa disalin langsung.

---

## 4. Rantai Nilai Batu Bara AAI

1. Eksplorasi dan model geologi (JORC 2012)
2. Pengupasan lapisan penutup (overburden), diukur dalam bank cubic meter
3. Penggalian batu bara
4. Hauling ke stockpile ROM
5. Crushing dan sizing
6. Hauling jalan khusus, sekitar 80 km ke Sungai Barito, ratusan trailer 130 ton
7. Terminal Kelanis — crushing lanjutan, stockpile, pemuatan tongkang. **Titik terjadinya blending**
8. Tongkang menyusuri Barito
9. Transshipment di Taboneo ke kapal induk, atau terminal IBT Pulau Laut

Proses paralel yang berjalan terus: penirisan tambang dan pengolahan air asam tambang di settling pond, dinetralkan dengan kapur. pH, TSS, Fe, Mn wajib memenuhi baku mutu dan dilaporkan ke pemerintah.

---

## 5. Struktur Biaya AAI (Semester I 2026, ribuan USD)

Pendapatan US$2.546.596. Beban pokok pendapatan US$1.763.894.

| Komponen | Nilai | % BPP |
|---|---|---|
| Pertambangan (kontraktor) | 845.724 | 47,9% |
| Royalti ke Pemerintah | 326.335 | 18,5% |
| Pembelian batu bara | 208.654 | 11,8% |
| Pengangkutan dan bongkar muat | 186.410 | 10,6% |
| Pemrosesan batu bara | 138.891 | 7,9% |
| Penyusutan | 27.954 | 1,6% |

Sumber: laporan keuangan konsolidasian interim AAI per 30 Juni 2026, Catatan 27.

Kontraktor penambangan: PT Bukit Makmur Mandiri Utama (sampai 2030) dan Saptaindra Sejati (sampai 2042). Pemasok bahan bakar: Pertamina Patra Niaga (sampai 2029). Pelanggan di atas 10% pendapatan: TNB Fuel Services Sdn. Bhd.

---

## 6. Apa yang Dikerjakan AMT

Berdasarkan folder handover di `~/Documents/6th Term/AMT/javen-handovers`, AMT adalah tim yang mendigitalkan proses kantor, bukan proses tambang.

Dua project:
- **ITMS** (Integrated Travel Management System) — pengajuan perjalanan dinas lintas entitas AlamTri dan Adaro, terintegrasi SAP RISE dan Microsoft Dynamics 365
- **ALS** — project Legal, digitalisasi proses hukum

Contoh BRD lain yang dipakai referensi: GHG dan Legal.

Isi pekerjaan: wawancara user, pemetaan proses As-Is dan To-Be (BPMN), penyusunan BRD dan PRD, perancangan ERD, benchmark UI. Metodologi DMAIC/Six Sigma.

Tim kecil: 3 intern dan 2 karyawan tetap, pekerjaan sama. Proyek yang sedang dipegang: asset rental untuk laptop dan periferal karyawan — **bukan alat berat**.

**Konsekuensi:** posisi di AMT tidak memberi akses langsung ke data operasi tambang. Data harus diminta ke divisi lain lewat jalur resmi.

---

## 7. Prior Art di Teknik Komputer UI — TEMUAN PALING PENTING

Dari daftar 440 judul di D'Office, Mia Rizkinia membimbing **lima skripsi RKEF feronikel** di semester 2025/2026-2, di luar Aldrian:

| Mahasiswa | Judul |
|---|---|
| Darmawan Hanif | Model Time Series Machine Learning untuk Memprediksi Hasil Produksi Feronikel pada Sistem RKEF |
| Fabsesya Muhammad Putra Ibradi | Model Deep Learning Berbasis Time Series untuk Prediksi Kualitas Produk dan Target Operasional pada RKEF |
| Darren Nathanael Boentara | Sistem Optimasi Multiobjektif untuk Efisiensi Penggunaan Batubara pada Industri Pengolahan Feronikel Berbasis R-NSGA-II |
| Mario Matthews Gunawan | Pengembangan Digital Twin Data-Driven untuk Produksi Feronikel Berbasis Machine Learning |
| Azriel Dimas Ash-Shidiqi | Sistem Prediksi Parameter Produksi Feronikel Berbasis ML dan Optimasi R-NSGA-II pada RKEF |

Total enam skripsi pada dataset Antam yang sama. Darren adalah penerus langsung Aldrian dengan objektif identik, metode naik dari SLSQP/GA ke R-NSGA-II.

**Konteks penting:** RKEF Antam adalah proyek pribadi dosen dengan Antam yang sudah selesai. Datasetnya lalu tersedia dan dipakai mahasiswa. Jadi ini bukan program riset yang diarahkan, melainkan data yang kebetulan ada. Topik bebas selama ada domain teknik komputernya.

**Yang tetap relevan dari temuan ini:** patokan metode yang dipakai angkatan sekarang sudah bukan Ridge Regression plus SLSQP, melainkan R-NSGA-II, deep learning time series, dan digital twin. Memakai metode 2025 di angkatan 2026 berisiko terlihat tertinggal saat sidang, terlepas dari apakah ada program riset atau tidak.

**Domain tambang batu bara kosong.** Tidak ada satu pun skripsi Teknik Komputer UI tentang operasi tambang batu bara. Yang menyentuh batu bara hanya dua, keduanya Teknik Elektro dan bukan operasi tambang:
- Isolator polymer silicone rubber–coal fly ash berbasis ML (Christiono R, riset S3)
- Optimasi rantai pasok biomassa untuk co-firing PLTU dengan GIS, MCDA, linear programming (Ali Ahmudi, disertasi)

Belum dicek: repositori `lib.ui.ac.id` dan `lontar.ui.ac.id` (butuh login). Kata kunci untuk dicek sendiri: blending batubara, optimasi batubara, coal blending.

---

## 8. Anatomi Skripsi Benchmark (Aldrian, 2025)

| Aspek | Detail |
|---|---|
| Domain | RKEF feronikel — rotary dryer, rotary kiln, electric furnace |
| Data | 43 variabel: 29 input, 11 output |
| Rentang | Januari 2021, resolusi per jam, sekitar 744 baris |
| Model prediktif | Ridge Regression |
| Optimizer | SLSQP dibandingkan Genetic Algorithm |
| Variabel keputusan | 15 dari 29; sisanya fixed (komposisi bijih, kualitas batu bara) |
| Fungsi objektif | Meminimalkan selisih prediksi terhadap nilai aktual |
| Kendala | Rentang operasi aman tiap input; mutu produk: Ni > 17%, C 1–2%, S < 0,4%, suhu logam > 1300 °C |
| Evaluasi | Lima sumbu: efisiensi energi, pelanggaran kendala, kewajaran solusi, deviasi output, waktu komputasi |
| Hasil | SLSQP skenario e direkomendasikan: 0 pelanggaran kendala, 23,8 detik. GA skenario d lebih efisien energi (1,85 ton/jam) tapi 365,78 detik |

Sumber data Aldrian: tiga file dari perusahaan (data smelting EF, data RK dan RD, laporan penggunaan bahan bakar). Perusahaan tidak disebut namanya — ditulis "suatu industri pengolahan feronikel".

---

## 9. Kandidat Topik

### Peringkat 1 — Optimisasi blending batu bara terhadap spesifikasi kontrak

Judul usulan: *Rancang Bangun Sistem Optimisasi Pencampuran Batu Bara untuk Pemenuhan Spesifikasi Produk Berbasis Machine Learning*

- Fungsi objektif: meminimalkan quality give-away, yaitu selisih antara mutu yang dikirim dan mutu yang dikontrakkan
- Variabel keputusan: proporsi tiap sumber (pit, seam, stockpile) dalam satu kargo
- Kendala: batas atas dan bawah tiap parameter mutu per kontrak, ketersediaan stok, kapasitas tongkang
- Peran ML: memprediksi mutu campuran. Total moisture, HGI, dan titik leleh abu tidak bercampur linier
- Optimizer: linear programming sebagai baseline, NSGA-II atau R-NSGA-II sebagai metode utama
- Kepastian data: tinggi — mutu adalah dasar penagihan dan perhitungan royalti

### Peringkat 2 — Optimisasi konsumsi bahan bakar armada hauling

- Nilai ekonomi terbesar (pertambangan 47,9% BPP), preseden literatur kuat
- Risiko: penambangan dikerjakan kontraktor; data fleet management kemungkinan milik BUMA atau SIS, dan SIS kini di sisi Alamtri bukan AAI
- Catatan: SIS melaporkan ketersediaan fisik alat 93% tetapi utilisasi hanya 59%

### Peringkat 3 — Optimisasi dosis penetral air asam tambang

- Objektif: meminimalkan konsumsi kapur dengan kendala pH, TSS, Fe, Mn memenuhi baku mutu
- Kepastian data paling tinggi: pemantauan harian wajib dilaporkan ke pemerintah
- Sudah ada penelitian akademik pada settling pond Wara milik Adaro
- Nilai ekonomi lebih kecil; argumen bersandar pada kepatuhan lingkungan

### Peringkat 4 — Optimisasi energi dan throughput crushing plant

Paling mirip struktur RKEF, tapi butuh historian SCADA yang belum tentu rapi dan bisa diekspor.

### Peringkat 5 — Optimisasi penjadwalan tongkang dan transshipment

Nilai tinggi, tapi masalah kombinatorial — bentuknya paling jauh dari benchmark.

---

## 10. Posisi terhadap Prior Art

Topik bebas selama ada domain teknik komputernya. Tidak perlu memposisikan diri terhadap skripsi RKEF, karena mereka memakai dataset yang kebetulan tersedia, bukan mengikuti arahan riset.

Yang tetap perlu dijawab: apa kontribusi teknik komputernya. Untuk topik blending, jawabannya ada pada pemodelan prediktif sebagai pengganti asumsi rata-rata tertimbang, formulasi optimisasi berkendala, dan rancangan sistemnya. Preseden bahwa bentuk ini diterima: skripsi Aldrian.

Perbedaan struktural terhadap jalur RKEF, berguna kalau ditanya bedanya apa:

| Aspek | Jalur RKEF (6 skripsi) | Usulan |
|---|---|---|
| Variabel keputusan | Setelan mesin, kontinu | Proporsi campuran, berjumlah tetap |
| Kendala | Rentang operasi aman | Spesifikasi kontrak dan ketersediaan stok |
| Sifat masalah | Satu titik operasi | Berulang per kargo, stok berubah antar periode |
| Ketidakpastian | Minim | Mutu stockpile hanya diketahui dari sampel |

Dua hal terakhir tidak ada di jalur RKEF dan menjadi bahan kontribusi.

---

## 11. Literatur

### Internasional — state of the art blending

| Karya | Metode | Identitas |
|---|---|---|
| Coal allocation optimization, hybrid residual prediction + improved GA (2024) | RF seleksi fitur; XGBoost, AdaBoost, LightGBM; GA termodifikasi | doi 10.1016/j.engappai.2024.109072 |
| Reinforcement learning-enhanced multi-objective optimization for sustainable coal blending in thermal power plants (2025) | QNSGA-III (Q-learning + NSGA-III). Validasi industri Huaneng Yingkou: biaya bahan bakar turun 14,7%, slagging turun 41% | doi 10.1371/journal.pone.0331208 |
| Machine Learning Surrogated Coal Blend Optimisation for Inventory-Aware Coking (2026) | Surrogate ML dengan kesadaran inventori | EPJ Conferences, GCMM 2025 |
| Optimizing Coal Blending for Metallurgical Coke Production | RL-enhanced evolutionary algorithm | SSRN 5276103 |

### Indonesia — prior art blending, seluruhnya non-ML

Semuanya dari Teknik Pertambangan, metode linear programming, simpleks, atau Excel Solver. Deterministik, satu objektif, tanpa model prediksi; mutu campuran diasumsikan rata-rata tertimbang.

- Universitas Sriwijaya: beberapa skripsi (analisis blending untuk spesifikasi; optimasi pencampuran di PT Bukit Asam; analisis ratio komposisi blending untuk market brand)
- Universitas Hasanuddin: optimasi hasil pencampuran batubara
- UIN Jakarta: optimasi coal blending memenuhi permintaan
- Jurnal Himasapta ULM: optimasi pencampuran melalui simulasi berdasarkan kriteria parameter
- Jurnal Proximal: metode simpleks dengan Excel Solver
- PT Multi Tambangjaya Utama (ResearchGate): optimasi blending untuk target market

### Topik cadangan — air asam tambang

| Karya | Metode | Identitas |
|---|---|---|
| Minimally Active Neutralization of AMD through Monte Carlo (2023) | Monte Carlo untuk dosis kapur, fly ash, Al(OH)3 optimum | doi 10.3390/w15193496 |
| ML-Based Spatiotemporal AMD Prediction (2025) | RF, XGBoost, SVM. R² 0,81 untuk Fe; 0,77 untuk Cu | doi 10.3390/w17182661 |
| Comparison of individual and ensemble ML models for sulphate prediction in AMD | Model tunggal vs ensemble | PMC10907470 |
| Application of ML for Predicting AMD Generation in Abandoned Coal Washery Rejects Pile (2025) | Studi kasus | doi 10.1080/15320383.2025.2490989 |

Celah: prediksi sudah banyak; optimisasi dosis tertutup (prediksi digabung optimizer berkendala) masih tipis.

### Topik cadangan — bahan bakar armada

Sudah sangat ramai. XGBoost mencapai R² 0,94 dan MAE 0,37; ada pula OOA-LightGBM dan Deep Siamese Transformer Network (Scientific Reports 2025, s41598-025-30178-z). Literatur melaporkan optimisasi kemiringan jalan dan tahanan gelinding dapat memangkas waktu siklus hingga 15% dan bahan bakar hingga 13%.

---

## 12. Dokumen Permintaan Data (siap kirim)

### Pemohon
Nama, NPM, Program Studi Teknik Komputer FT UI, posisi Business Analyst Intern di PT Adaro Mining Technologies, nama dosen pembimbing.

### Judul sementara
Rancang Bangun Sistem Optimisasi Pencampuran Batu Bara untuk Pemenuhan Spesifikasi Produk Berbasis Machine Learning

### Data yang dimohonkan

**A. Hasil analisis kualitas batu bara per sumber** — harian, 12 bulan terakhir

| Kolom | Keterangan | Satuan |
|---|---|---|
| Tanggal | Tanggal pengambilan sampel | — |
| Kode sumber | Pit, seam, atau stockpile. Boleh disamarkan menjadi Sumber A, B, C | — |
| Calorific value | Nilai kalori | kcal/kg |
| Total moisture | Kandungan air total | % |
| Ash content | Kandungan abu | % |
| Total sulphur | Kandungan sulfur | % |
| Tonase | Tonase sampel atau batch terkait | ton |

**B. Inventori stockpile** — harian, 12 bulan terakhir: tanggal, kode stockpile (boleh disamarkan), tonase tersedia, mutu rata-rata (CV, TM, ash, TS).

**C. Catatan pencampuran dan pemuatan** — 12 bulan terakhir: tanggal muat, kode kargo (boleh disamarkan), sumber dan proporsi, mutu hasil campuran.

**D. Batas spesifikasi produk** — batas minimum dan maksimum tiap parameter untuk tiap jenis produk, disajikan sebagai Produk A, B, dan seterusnya. Nama pelanggan dan harga tidak diperlukan.

### Data yang tidak dimohonkan
Harga jual, nilai kontrak, data keuangan, identitas pelanggan, koordinat, data cadangan, model geologi, data personil.

### Komitmen kerahasiaan
- Nama perusahaan tidak dicantumkan pada judul maupun isi; dirujuk sebagai "suatu perusahaan pertambangan batu bara di Indonesia", mengikuti praktik penelitian sejenis sebelumnya
- Kode sumber, stockpile, dan produk dapat disamarkan sepenuhnya oleh perusahaan sebelum penyerahan
- Nilai absolut dapat dinormalisasi atau diskalakan; yang dibutuhkan hanya pola hubungan antar variabel
- Bersedia menandatangani perjanjian kerahasiaan
- Draft skripsi bersedia ditinjau perusahaan sebelum sidang dan sebelum diunggah ke repositori universitas

### Permintaan bertahap
Tahap 1: sampel satu bulan untuk tabel A dan C, untuk memastikan struktur data memadai.
Tahap 2: rentang penuh 12 bulan setelah Tahap 1 terverifikasi.
Format: CSV atau Excel.

### Alternatif bila data mutu terlalu sensitif
Dialihkan ke optimisasi dosis penetral air asam tambang. Kebutuhan data: log pemantauan settling pond harian (debit, pH inlet dan outlet, TSS, Fe, Mn), catatan pemakaian kapur, curah hujan harian. Data ini umumnya tersedia karena merupakan kewajiban pelaporan lingkungan.

---

## 13. Langkah Berikutnya

1. Konfirmasi judul sementara ke pembimbing sebelum data diminta, agar tidak terjadi perubahan topik setelah data keluar
2. Kirim dokumen permintaan data ke atasan di AMT, bukan langsung ke direksi — biarkan atasan yang meneruskan
3. Cek repositori UI (`lib.ui.ac.id`, `lontar.ui.ac.id`) untuk memastikan tidak ada skripsi UI tentang blending batu bara
4. Cari tahu status Darren Nathanael Boentara — sudah sidang atau belum, dan apakah lima skripsi RKEF itu memakai dataset Antam yang sama
5. Naikkan rencana metode: gradient boosting sebagai model prediksi (bukan Ridge), NSGA-II atau R-NSGA-II sebagai optimizer utama, linear programming sebagai baseline yang mewakili prior art Indonesia

## 14. Risiko Utama

| Risiko | Dampak | Mitigasi |
|---|---|---|
| Persetujuan data lambat atau ditolak | Tidak ada penelitian sama sekali | Kirim permintaan secepatnya; sertakan topik alternatif air asam tambang di dokumen yang sama |
| Lima rekan seangkatan sudah punya dataset, pemohon belum | Tertinggal jadwal | Permintaan data adalah jalur kritis, bukan langkah kedua |
| Metode Ridge plus SLSQP dinilai tertinggal dari rekan seangkatan | Nilai rendah meski lulus | Pakai gradient boosting dan NSGA-II sejak awal |
| Data mutu dianggap sensitif komersial | Topik utama gugur | Tidak meminta harga dan nama pelanggan; tawarkan penyamaran kode dan normalisasi nilai |
| Ada skripsi UI serupa yang belum terdeteksi | Klaim kebaruan runtuh | Cek repositori UI sebelum bimbingan |

---

## 15. Catatan Administratif

Password akun UI sempat terkirim dalam percakapan dan **harus diganti**.

File sumber di folder ini:
- `ADRO Annual Report 2025.pdf` — Laporan Tahunan PT Alamtri Resources Indonesia Tbk, 472 halaman
- `FS Adaro Andalan Indonesia - 30 June 2026.pdf` — laporan keuangan konsolidasian interim AAI, 142 halaman
- `Rancang Bangun Sistem Optimisasi Pemakaian Batubara Pada Proses Produksi Feronikel.pdf` — skripsi benchmark Aldrian, 109 halaman
