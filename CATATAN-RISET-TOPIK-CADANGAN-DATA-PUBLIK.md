# Catatan Riset Topik Skripsi Cadangan — Data Publik

Disusun: 22 September 2026
Mahasiswa: Muhammad Arya Wiandra Utomo, Teknik Komputer FT UI
Posisi: Business Analyst Intern, PT Adaro Mining Technologies (AMT)

Dokumen ini adalah kelanjutan dari `CATATAN-RISET-TOPIK.md`. Ditulis agar bisa dibaca ulang tanpa konteks percakapan sebelumnya.

---

## 1. Situasi Terbaru

Update 22 September 2026: data Adaro untuk topik blending batu bara **sebenarnya ada dan bisa diberikan**, tetapi proses persetujuannya berlapis. AMT adalah anak usaha PT Adaro Mining Technologies di bawah PT Adaro Andalan Indonesia (AAI), sedangkan data kualitas batu bara dan stockpile dimiliki perusahaan lain yang juga di bawah AADI tapi beda Business Unit. Karena beda BU, permintaan data harus melalui persetujuan lintas-BU, bukan cukup lewat atasan langsung di AMT. Status: sedang dibicarakan atasan dengan pihak terkait, belum ada kepastian waktu.

Karena topik blending batu bara masih menunggu kejelasan approval, dicari topik cadangan yang:
1. Tetap bertema machine learning
2. Memakai data yang publik atau tidak sulit didapat (Kaggle, open data pemerintah/lembaga, dataset yang sudah dirilis perusahaan untuk riset) — bukan data yang butuh persetujuan korporat berlapis
3. Relevan dengan tren riset dan industri ML terkini (per riset 22 September 2026)
4. Selaras dengan preferensi industri kerja ke depan: **consulting** (prioritas utama), **oil & gas / energy** boleh tapi opsi terakhir

Topik blending batu bara TIDAK dibatalkan — statusnya tetap jalur utama jika approval cair. Dokumen ini adalah rencana cadangan/paralel, bukan pengganti.

---

## 2. Tiga Kandidat Topik

### Peringkat 1 — Peramalan permintaan dan optimisasi inventori (predict-then-optimize), data ritel M5/Walmart

**Judul usulan sementara:** *Rancang Bangun Sistem Peramalan Permintaan dan Optimisasi Kebijakan Inventori Multi-Produk Berbasis Machine Learning*

- **Data:** Dataset kompetisi **M5 Forecasting - Accuracy** (Kaggle, dirilis University of Nicosia berbasis data ritel Walmart AS asli) — 3.049 produk, 10 toko, 3 negara bagian, granularitas harian, lengkap dengan data kalender/event dan harga. Gratis diunduh langsung dari Kaggle, tanpa perlu izin apa pun.
- **Peran ML:** Model prediktif meramalkan permintaan per produk per toko (baseline gradient boosting/LightGBM, model utama LSTM atau Temporal Fusion Transformer)
- **Optimizer:** Kebijakan inventori (safety stock, reorder point, order quantity) dioptimasi berdasarkan hasil peramalan — linear programming sebagai baseline, multi-objective optimization (biaya penyimpanan vs risiko stockout) atau reinforcement learning sebagai metode utama
- **Kenapa relevan untuk consulting:** peramalan permintaan dan optimisasi rantai pasok adalah salah satu lini jasa inti consulting operasi/strategi. Riset McKinsey (dikutip dalam pencarian 22 September 2026) menyebut AI pada distribusi dan inventori memangkas inventori 20–30% dan biaya logistik 5–20%.
- **Tren riset terkini yang mendukung:** kerangka "predict-then-optimize" sudah baku di literatur management science. Riset 2025–2026 mendorong ke arah reinforcement learning dan multi-agent deep RL untuk optimisasi safety stock dan integrasi peramalan-inventori sekaligus (contoh: paper PROPEL — large-scale supply chain planning dengan supervised + RL, arXiv 2504.07383; multi-agent DRL untuk peramalan dan inventori terintegrasi, PMC12031219). Ini sejalan dengan standar metode 2026 yang lebih maju dari sekadar regresi tunggal.
- **Struktur mengikuti pola skripsi Aldrian (model prediktif + optimizer berkendala)** sehingga tetap sejalan arahan pembimbing untuk meniru pendekatan tersebut, hanya datanya berbeda.
- **Kepastian data:** tinggi — dataset publik permanen, tidak bergantung persetujuan siapa pun.
- **Risiko novelty:** prediksi churn dan peramalan permintaan generik sudah banyak dikerjakan (termasuk di UI, ditemukan skripsi churn telekomunikasi di perpustakaan UI). Mitigasi: fokus bukan pada model prediksi semata, tapi pada penggabungan prediksi + optimisasi kebijakan inventori berkendala sebagai satu sistem — pola yang sama dengan preseden Aldrian, dan masih jarang di skripsi Teknik Komputer UI berdasarkan pencarian awal.

### Peringkat 2 — Peramalan produksi migas dan optimisasi parameter operasi, dataset Volve (Equinor, North Sea)

**Judul usulan sementara:** *Rancang Bangun Sistem Peramalan Produksi dan Optimisasi Parameter Operasi Lapangan Minyak Berbasis Machine Learning*

- **Data:** **Volve Field Open Dataset** — dirilis penuh oleh Equinor sejak 2018 untuk riset, ~40.000 file mencakup well log, survei seismik, riwayat produksi dan injeksi, model simulasi reservoir, dan dokumen pendukung. Salah satu dataset migas terbuka paling lengkap di dunia, diunduh langsung dari halaman resmi Equinor tanpa perjanjian kerahasiaan.
- **Peran ML:** Model prediktif meramalkan laju produksi (LSTM, BiLSTM, GRU, atau XGBoost — dipakai di riset 2025 seperti arXiv 2508.14078) atau memprediksi properti sumur dari well log
- **Optimizer:** Optimisasi parameter operasi (choke setting, strategi injeksi) untuk memaksimalkan produksi dengan kendala operasional dan keselamatan
- **Dataset pendamping:** kompetisi **FORCE 2020** (well log dari 98+ sumur lepas pantai Norwegia) untuk klasifikasi litologi berbasis well log, bisa jadi topik alternatif atau tambahan dalam domain yang sama
- **Kenapa relevan:** tetap di industri sumber daya alam/energi (bukan mining tapi migas — masih sejalan dengan opsi terakhir preferensi industri), dan meneruskan literasi domain pertambangan/energi yang sudah dibangun Arya selama riset topik Adaro sebelumnya
- **Tren riset terkini:** aktif diriset — paper terbaru soal deteksi dini stuck pipe pakai Crossformer (arXiv 2503.07440, Maret 2025), survei foundation model untuk peramalan energi bersih (arXiv 2507.23147, 2025), model hybrid AutoML pada Volve sendiri (arXiv 2103.02598)
- **Kepastian data:** tinggi — dataset permanen milik Equinor, dirilis khusus untuk riset dan pendidikan
- **Risiko novelty:** dataset ini sudah sangat populer secara internasional (banyak tutorial, artikel Medium, repo GitHub yang mereplikasi peramalan produksi dasar). Perlu sudut pandang yang lebih spesifik — misalnya menggabungkan peramalan dengan optimisasi operasi (bukan sekadar prediksi), atau fokus ke sub-masalah yang belum banyak dikerjakan (deteksi anomali operasi, optimisasi injeksi). Berdasarkan pencarian awal, belum ditemukan skripsi Teknik Komputer UI yang memakai dataset ini — perlu konfirmasi lewat `lib.ui.ac.id`/`lontar.ui.ac.id`.
- **Risiko konteks:** lapangan Norwegia, bukan Indonesia — bisa memicu pertanyaan "kenapa bukan data lokal" saat sidang, meski wajar dijawab karena ini benchmark terbuka standar dunia untuk ML migas.

### Peringkat 3 — Peramalan dan deteksi anomali konsumsi energi gedung, dataset ASHRAE/LEAD

**Judul usulan sementara:** *Rancang Bangun Sistem Peramalan dan Deteksi Anomali Konsumsi Energi Gedung Berbasis Machine Learning*

- **Data:** **ASHRAE Great Energy Predictor III** (kompetisi Kaggle 2019, >20 juta titik data dari 2.380 meter energi di 1.448 gedung, 16 sumber) untuk peramalan; **dataset LEAD** (arXiv 2203.17256) untuk deteksi anomali konsumsi energi di gedung komersial berskala besar dan sudah berlabel
- **Peran ML:** Model peramalan konsumsi energi (gradient boosting, sesuai pendekatan tim pemenang kompetisi ASHRAE) dipadukan dengan deteksi anomali untuk mengidentifikasi pemborosan atau kerusakan peralatan
- **Kenapa relevan:** sejalan opsi terakhir preferensi industri (energy)
- **Kepastian data:** sangat tinggi — dataset besar, publik permanen, sudah jadi rujukan akademik selama bertahun-tahun
- **Risiko novelty — PALING BESAR dari tiga kandidat:** ASHRAE GEPIII adalah kompetisi Kaggle yang sudah sangat "selesai" — lebih dari 400 notebook publik dan puluhan solusi lengkap sudah dibagikan pemenangnya. Skripsi yang hanya mereplikasi peramalan akan terlihat seperti mengikuti tutorial Kaggle, bukan kontribusi baru. Perlu lapisan tambahan yang jelas (mis. deteksi anomali + rekomendasi tindakan, atau optimisasi penjadwalan HVAC berbasis hasil peramalan) supaya tidak sekadar replikasi.

---

## 3. Rekomendasi

**Peringkat 1 (peramalan permintaan + optimisasi inventori, data M5/Walmart)** adalah pilihan terkuat karena:
- Paling selaras preferensi industri utama (consulting)
- Data paling pasti tersedia dan paling ringan diproses (tabular + time series, tidak perlu domain expertise geologi/reservoir)
- Tren metodologi 2025–2026 (predict-then-optimize, RL untuk inventori) jelas dan terdokumentasi, sehingga metode bisa langsung dirancang setara level metodologi angkatan sekarang, tidak perlu takut dianggap ketinggalan
- Tetap mempertahankan struktur "model prediktif + optimizer berkendala" yang disukai pembimbing

**Peringkat 2 (Volve, migas)** adalah cadangan yang baik kalau Arya ingin mempertahankan narasi "pengalaman di industri sumber daya alam" saat wawancara kerja atau sidang, karena literasi domain tambang/energi yang sudah dibangun selama magang di AMT tetap terpakai.

**Peringkat 3 (ASHRAE, energi gedung)** disarankan jadi opsi terakhir kalau dua di atas tidak memungkinkan, karena risiko dianggap replikasi kompetisi Kaggle paling tinggi.

---

## 3a. Benchmark Tingkat Kompleksitas — Judul Skripsi Teknik Komputer 2021-2026

Sumber: daftar judul skripsi/tesis/disertasi D'Office FTUI yang diberikan Arya (`D'Office - Daftar Judul Skripsi, Tesis, Disertasi.html`), difilter untuk Program = Teknik Komputer (Reguler/Paralel) dan Jenis = Skripsi (S1). Total 353 judul S1 Teknik Komputer periode 2021/2022 sampai 2025/2026-2, dari situ 118 berkaitan dengan machine learning/prediksi/optimasi/deteksi.

**Standar metode terus naik tiap semester.** Judul-judul semester terbaru (2025/2026-2) sudah memakai teknik yang jauh lebih berat dari sekadar model prediktif tunggal:

| Judul (2025/2026-2) | Metode |
|---|---|
| Algorithmic trading | Risk-Sensitive RL, arsitektur CMDP-PPO-LSTM, pembatasan risiko CVaR |
| Prediksi land subsidence (Semarang-Demak) | Explainable AI + Spatio-Temporal Graph Neural Network |
| Optimasi batubara pada RKEF (kelompok Aldrian) | R-NSGA-II |
| Deteksi anomali video CCTV | Perbandingan arsitektur Frame-Based vs Spatio-Temporal |
| (2024/2025-2) Remaining Useful Life mesin turbofan | Multitask Learning, Multi-Gate Mixture-of-Experts (MMoE) |
| (2024/2025-2) Deteksi anomali time series multivariat | Attention-LSTM Wasserstein GAN + Deep Convolutional |
| (2025/2026-2) Deteksi IDS | Federated Learning + LLM (QLoRA) + Knowledge Distillation |

Kesimpulan: kalau metode Peringkat 1 nanti hanya "LSTM lalu linear programming", itu akan terasa satu-dua tingkat di bawah standar 2026. Perlu diangkat setara — lihat rekomendasi penyesuaian metode di bawah.

**Preseden langsung pola "prediksi lalu optimasi"** (struktur yang sama dengan tiga kandidat di dokumen ini) sudah ada dan diterima di luar kelompok RKEF:

> *"Coverage and Capacity Optimization (CCO) pada Jaringan Wi-Fi dengan Metode Cell Breathing Menggunakan XGBoost dan Genetic Algorithm Berdasarkan Lokasi User"* (2024/2025-2) — prediksi (XGBoost) dipasangkan dengan optimasi (Genetic Algorithm), persis pola yang diusulkan untuk Peringkat 1, hanya beda domain (jaringan WiFi, bukan inventori).

**Cek novelty per kandidat terhadap 118 judul ini:**

- **Peringkat 1 (peramalan permintaan + optimisasi inventori):** Nol judul tentang peramalan permintaan ritel, rantai pasok, inventori berbasis ML, atau churn pelanggan ditemukan di Teknik Komputer 2021-2026. Satu-satunya yang menyinggung "inventori" adalah *"Rancang Bangun Sistem Manajemen Inventori Kantor Pada Lembaga XYZ"* (2025/2026-2) — itu sistem CRUD/database biasa, bukan berbasis ML. **Domain ini benar-benar kosong di jurusan.** Bonus: pembimbing Arya sendiri, **Dr. Eng. Mia Rizkinia**, pernah membimbing skripsi berkonteks ritel — *"Prototipe Sistem Computer Vision untuk Pengenalan Aktivitas Pelanggan pada Cashier-Less Store Skala Kecil"* (2024/2025-2, computer vision, bukan forecasting) — jadi domain ritel bukan hal asing baginya.
- **Peringkat 2 (migas, Volve):** Ada satu preseden domain migas — *"Pengembangan Sistem Deteksi Anomali Menggunakan Algoritma Autoencoder dan Generative Adversarial Network pada Mesin Gas Turbin Industri Hulu Minyak Dan Gas"* (2024/2025-2) — tapi soal deteksi anomali mesin gas turbin, bukan peramalan produksi sumur dari data Volve. Sub-masalahnya beda, jadi kandidat ini masih orisinal, hanya perlu ditulis eksplisit di skripsi bahwa preseden migas sebelumnya beda topik.
- **Peringkat 3 (ASHRAE, energi gedung):** **Ditemukan preseden ganda di jurusan sendiri**, bukan cuma kompetisi Kaggle internasional — *"Evaluasi Metode SCA ETS dan ANN Pada Hybrid Forecasting Model Untuk Memprediksi Penggunaan Listrik Gedung S FTUI"* (2021/2022-2) dan *"RANCANG BANGUN SISTEM MONITORING DAN PREDIKSI PENGHEMATAN ENERGI PADA ACCESS POINT DI LINGKUNGAN KAMPUS MENGGUNAKAN XGBOOST"* (2024/2025-2). Ini memperkuat kesimpulan sebelumnya: Peringkat 3 adalah opsi paling lemah dari sisi kebaruan, baik secara internasional maupun domestik.

**Rekomendasi penyesuaian metode Peringkat 1 supaya setara standar 2026:** naikkan dari "LSTM + linear programming" ke kombinasi yang lebih sejalan preseden terbaru — misalnya **Temporal Fusion Transformer atau N-BEATS** untuk peramalan permintaan (dibandingkan baseline gradient boosting), dipasangkan dengan **optimisasi multi-objektif atau reinforcement learning berkendala** untuk kebijakan inventori (mengikuti pola RL+CVaR pada skripsi trading, atau R-NSGA-II pada kelompok RKEF), dengan linear programming sebagai baseline pembanding saja — bukan metode utama.

---

## 4. Langkah Berikutnya

1. Diskusikan tiga kandidat ini dengan Arya untuk memilih arah yang ingin didalami
2. Setelah arah dipilih, lakukan riset literatur mendalam (state of the art internasional + cek prior art UI via `lib.ui.ac.id`/`lontar.ui.ac.id`, perlu login)
3. Unduh dan periksa struktur data yang dipilih untuk memastikan skrip data benar-benar memadai sebelum diajukan ke pembimbing
4. Konfirmasi judul sementara ke pembimbing (Dr. Eng. Mia Rizkinia) — sampaikan sebagai opsi cadangan sambil menunggu kejelasan approval data Adaro, bukan pengganti otomatis
5. Topik blending batu bara (`CATATAN-RISET-TOPIK.md`) tetap dipantau paralel — begitu approval AADI lintas-BU cair, opsi itu bisa diambil kembali sebagai jalur utama

## 5. Risiko Utama

| Risiko | Dampak | Mitigasi |
|---|---|---|
| Topik dianggap terlalu generik/replikasi Kaggle (khusus Peringkat 3, dan sebagian Peringkat 1–2) | Nilai rendah karena dianggap tanpa kontribusi baru | Selalu gabungkan prediksi dengan optimisasi/keputusan berkendala, jangan berhenti di model prediktif saja |
| Approval Adaro cair di tengah jalan setelah topik cadangan sudah didalami | Waktu riset topik cadangan terasa terbuang | Tetap pilih topik cadangan yang membangun kemampuan metodologis (predict-then-optimize) yang transferable ke topik Adaro bila approval cair |
| Belum dicek prior art UI (`lib.ui.ac.id`, `lontar.ui.ac.id`) untuk tiga kandidat ini | Klaim kebaruan belum terverifikasi | Cek repositori UI setelah arah topik dipilih, sebelum bimbingan |
| Dataset migas/energi (Volve, ASHRAE) berkonteks luar negeri | Berpotensi ditanya relevansi lokal saat sidang | Siapkan jawaban: dataset ini adalah benchmark terbuka standar dunia di bidangnya, dipakai luas di literatur akademik internasional |

---

## 6. Update 29 September 2026 — Daftar topik cadangan diperluas

**Situasi.** Direktur Adaro memberi respons positif, tetapi proposal permohonan data ditujukan ke pejabat yang sedang di Bali, jadi prosesnya tertahan di sana. Direktur juga menyebut beberapa perusahaan Adaro sudah punya model ML untuk blending. Kualitas model itu belum diketahui dan publikasinya belum ditemukan, kemungkinan karena rahasia. Daftar di bawah untuk skenario terburuk: harus ganti topik.

**Tolok ukur kompleksitas.** Sama dengan §3a, yaitu judul Teknik Komputer 2025/2026-2 (CMDP-PPO-LSTM + CVaR, STGNN + XAI, R-NSGA-II, MMoE, QLoRA/RAG). Pencarian kata kunci pada ekspor D'Office tidak menemukan satu pun judul Teknik Komputer tentang satelit/penginderaan jauh, tambang, flotasi, process mining, kontrak, atau churn. Sudah ada preseden skripsi yang memakai dataset benchmark publik, misalnya segmentasi tumor dengan dataset HECKTOR 2025, jadi data publik sendiri tidak menjadi masalah.

**Alat peraga baru:** `model-gar-batubara.html`. Halaman interaktif untuk menjelaskan ke pembimbing kenapa GAR tidak linier: konversi basis, uji model linier, dan simulasi pencampuran Monte Carlo dengan chance constraint.

### Kandidat (urut berdasarkan kerja yang tidak terbuang)

**1. Topik blending yang sama, dengan data publik — USGS COALQUAL v3.0**
- Data: 7.657 sampel batubara dengan proksimat, ultimat, dan GCV pada basis as-received, publik dari USGS (Data Series 975).
- Metode:
  - Model GCV physics-informed: lapis fisika konversi basis, ditambah gradient boosting atau Gaussian process untuk residual, dengan conformal prediction.
  - Optimisasi blending chance-constrained atau NSGA-II pada skenario stockpile yang disusun dari distribusi sampel nyata.
- Kelebihan: pipeline dan bab metodologi bisa dibangun sekarang. Kalau data Adaro keluar, cukup lapis datanya yang ditukar, sehingga tidak ada kerja yang terbuang.
- Kelemahan:
  - Data berasal dari AS.
  - Tidak ada pasangan rencana vs realisasi, jadi lapis 2 (penyimpangan realisasi) hanya bisa disimulasikan.
  - Prediksi GCV dari proksimat sudah banyak dipublikasikan, jadi kontribusinya harus ada di lapis optimisasi dan ketidakpastian.

**2. Segmentasi dan deteksi perubahan area tambang di Kalimantan — Sentinel-2 + poligon Maus et al. 2022**
- Data:
  - Citra Sentinel-2, gratis dari Copernicus.
  - Poligon tambang global Maus et al. (2022): 44.929 poligon, 101.583 km², PANGAEA doi 10.1594/PANGAEA.942325, digitasi dari mosaik Sentinel-2 tahun 2019.
- Metode: U-Net atau SegFormer dibandingkan dengan fine-tune foundation model geospasial, ditambah change detection multi-temporal untuk memantau bukaan lahan dan reklamasi.
- Kebaruan: tidak ada judul satelit di Teknik Komputer. Preseden geospasial terdekat adalah STGNN untuk land subsidence, yang masalahnya berbeda.
- Kecocokan: konteks batubara Kalimantan tetap terjaga, ada sudut ESG yang relevan untuk consulting, dan pembimbing sudah membimbing skripsi computer vision (deteksi APD).
- Risiko: label hanya untuk 2019, jadi tahun lain perlu dilabeli ulang. Awan tropis juga mengganggu citra.

**3. Peramalan permintaan + optimisasi inventori, M5** (peringkat 1 di §2). Tetap paling cocok untuk karier consulting.

**4. Predictive + prescriptive process monitoring — BPI Challenge 2017**
- Data: 31.509 kasus dan 1.202.267 event proses pengajuan pinjaman, CC BY 4.0 dari 4TU.ResearchData.
- Metode: transformer untuk prediksi next-activity dan remaining time, ditambah rekomendasi intervensi (causal uplift atau RL).
- Kebaruan: tidak ada judul process mining di Teknik Komputer.
- Kecocokan: langsung memakai pengalaman BA (BPMN As-Is/To-Be, DMAIC), dan relevan untuk consulting operations.
- Risiko: dataset ini populer di komunitas process mining. Pembedanya ada di lapis preskriptif.

**5. Soft sensor flotasi + optimisasi setpoint — Kaggle "Quality Prediction in a Mining Process"**
- Data: 737.453 baris dan 23 variabel dari pabrik flotasi bijih besi, Maret–September 2017.
- Metode: model deret waktu (misalnya TFT) untuk memprediksi % silika, ditambah R-NSGA-II atau offline RL untuk setpoint reagen dan aliran udara. Strukturnya sama dengan skripsi Aldrian/Darren.
- Risiko: dataset ini sudah ramai di Kaggle (banyak notebook prediksi) dan hanya mencakup 6 bulan. Pembedanya harus ada di lapis optimisasi.

**Volve dan ASHRAE** (§2) tetap tercatat, tetapi turun prioritas.

### Cara memilih
- Ingin tetap di batubara dan tidak membuang kerja → pilih nomor 1.
- Harus lepas sepenuhnya dari data Adaro tapi tetap di domain tambang → pilih nomor 2.
- Prioritas karier consulting → pilih nomor 3 atau 4.

### Positioning terhadap model ML internal Adaro
- Jangan mengklaim "ML pertama untuk blending". Posisikan skripsi sebagai model yang terdokumentasi terbuka, sadar ketidakpastian, dan memakai objektif dua sisi (reject vs give-away).
- Lewat atasan, minta metrik error model internal itu (MAE atau bias rencana vs realisasi) untuk dipakai sebagai baseline pembanding. Kalau metriknya tidak bisa dibagikan, cukup catat bahwa model internal ada dan tidak terpublikasi.
