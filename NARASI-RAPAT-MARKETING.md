# Narasi Rapat dengan Tim Marketing — Permintaan Data Skripsi

Konteks: dibawa ke rapat hari ini (21 September 2026) dengan orang marketing Adaro yang pegang data, untuk minta data skripsi. Diagram pendukung: `rantai-nilai-blending-gar.html`.

---

## 1. Buka dengan proses coal-nya (pakai diagram)

"Jadi gini, singkatnya rantai batu bara kita itu ada lima tahap besar. Mulai dari tambang — ada dua sumber, Adaro Indonesia yang pit Tutupan sama Wara, terus Balangan Coal yang tiga IUP-nya, SCM, LSA, PCS. Dari situ diangkut ke stockpile ROM, di situ tiap sumber disampling mutunya — kalori (GAR), total moisture, ash content, sulphur, sama tonasenya.

Habis itu di-hauling darat sekitar 80 km ke Sungai Barito, baru sampai di Terminal Kelanis. Nah, di Kelanis ini titik yang penting — di situ ada banyak stockpile dari sumber-sumber berbeda, dan di situ juga terjadi **blending**: nyampur proporsi dari tiap sumber itu supaya hasil campurannya memenuhi spesifikasi yang diminta kontrak. Habis diblending, baru dimuat ke tongkang, jalan di Sungai Barito, terus transshipment di Taboneo atau IBT ke kapal besar buat dikirim ke pelanggan."

## 2. Masuk ke blending dan GAR

"Nah yang nentuin GAR itu justru proses blending di Kelanis ini. Karena tiap pit atau tiap stockpile itu kualitasnya beda-beda dan enggak konstan — kadang lebih tinggi kalorinya, kadang lebih rendah, tergantung seam-nya. Jadi tim di lapangan itu harus nentuin proporsi campuran dari beberapa sumber supaya begitu diblending, hasil GAR-nya pas di spesifikasi kontrak — enggak boleh di bawah minimum (nanti dianggap under-quality, kena klaim atau penalti), tapi juga sebisa mungkin enggak jauh di atas minimum (soalnya kalau kualitasnya kelewat tinggi dari yang dikontrakkan, itu namanya *quality give-away* — istilahnya rugi, karena kita kasih kualitas lebih tapi dibayar sesuai harga kontrak yang lebih rendah)."

## 3. Masuk ke isu Balangan (dari denger cerita Chila)

"Terus kemarin aku denger dari Chila, katanya ada yang di Balangan sempet dicabut izin jual thermal coal-nya karena GAR-nya enggak memenuhi standar kontrak. Aku belum tahu detailnya persis kayak gimana — makanya mau tanya juga ke sini, biar aku ngerti konteksnya bener."

## 4. Ajukan permintaan data untuk skripsi ML

"Nah dari situ aku kepikiran, ini kan sebenarnya soal: gimana caranya kita bisa mastiin proporsi blending itu udah pas — enggak under, enggak over — sebelum kargo itu berangkat. Ini yang mau aku angkat jadi topik skripsi aku: bikin model *machine learning* yang bisa memprediksi mutu hasil campuran dari proporsi sumbernya (karena ini enggak linier — moisture, HGI, titik leleh abu itu enggak sekadar rata-rata tertimbang), terus dioptimasi proporsinya supaya hasil GAR-nya presisi sesuai kontrak.

Kalau boleh, aku mau minta empat kelompok data ini — bisa disamarkan kodenya, enggak perlu nama pelanggan atau harga:

- **A. Kualitas per sumber** di ROM — CV/GAR, total moisture, ash, total sulphur, tonase — harian, kalau bisa 12 bulan terakhir
- **B. Inventori stockpile** di Kelanis — tonase & mutu rata-rata per stockpile, harian
- **C. Catatan pencampuran & pemuatan** — kode kargo, sumber & proporsinya, mutu hasil campuran
- **D. Batas spesifikasi produk** — minimum-maksimum tiap parameter per jenis produk/kontrak

Yang enggak aku minta: harga jual, nilai kontrak, data keuangan, identitas pelanggan, koordinat tambang. Kalau datanya sensitif, aku juga bisa mulai dari sampel satu bulan dulu buat cek strukturnya, baru lanjut ke rentang penuh."

## 5. Pertanyaan ke Bang Fadil

"Oh iya, mau nanya juga — menurut Bang Fadil, kenapa ya belum ada yang bikin sistem kayak gini sebelumnya? Kan kejadian di Balangan itu lumayan serius sampai izinnya dicabut."

---

## 6. Kalau ditanya balik "kenapa menurut kamu belum ada yang bikin ini" — jawaban Claude

Catatan jujur dulu: kejadian pencabutan izin di Balangan itu informasi yang kamu dengar sendiri dari Chila sekitar dua minggu lalu, jadi saya (Claude) tidak bisa mengonfirmasi detail kejadian itu sebagai fakta — itu di luar apa yang saya tahu. Yang bisa saya jawab adalah **kenapa secara struktural** kelas masalah ini (blending vs spesifikasi kontrak) jarang dipegang dengan pendekatan ML, berdasarkan riset yang sudah kita kumpulkan:

1. **Datanya ada, tapi enggak nyambung ke tim yang punya kemampuan ML.** Data mutu itu tersebar di tim operasi tambang dan quality control, sementara kemampuan data science/ML biasanya ada di tim lain (atau enggak ada sama sekali di sisi operasi). Buktinya di UI sendiri: semua penelitian akademik soal coal blending di Indonesia (Universitas Sriwijaya, Hasanuddin, UIN Jakarta, dll) itu dari Teknik Pertambangan, dan semuanya masih pakai linear programming atau Excel Solver — deterministik, satu objektif, mutu campuran diasumsikan rata-rata tertimbang. Enggak ada satupun yang pakai model prediktif buat mutu campurannya.

2. **Blending itu keputusan real-time di lapangan, bukan pipeline data.** Orang yang nentuin proporsi campuran di Kelanis biasanya kerja dengan pengalaman dan aturan praktis (heuristik), bukan lewat sistem yang menjalankan model tiap kali mau nentuin proporsi. Membangun sistem ML yang bisa dipercaya dan dipakai real-time butuh investasi infrastruktur (integrasi ke operasi harian) yang jauh lebih besar daripada sekadar bikin model di atas kertas.

3. **"Rata-rata tertimbang" itu kelihatannya udah cukup — sampai enggak cukup.** Selama toleransi kontrak masih longgar dan stockpile-nya konsisten, asumsi linier itu kelihatan jalan, jadi enggak ada dorongan buat ganti pendekatan. Baru kelihatan gagalnya kalau ada kombinasi buruk: campuran dari sumber-sumber yang variasinya lagi tinggi, atau spesifikasi kontraknya lagi ketat — dan itu biasanya baru ketahuan pas hasilnya sudah meleset, bukan sebelumnya. Ini pola umum: biaya dari sistem yang "cukup baik" itu enggak kelihatan sampai ada kejadian yang mahal.

4. **Data mutu itu sensitif secara komersial**, karena langsung berhubungan dengan penagihan dan royalti. Ini bikin data itu enggak gampang dibagi ke luar tim operasi/finance, apalagi ke pihak yang mau eksperimen dengan pendekatan baru — termasuk ke mahasiswa magang sepertimu. Makanya permintaan data ini perlu jalur resmi dan komitmen kerahasiaan yang jelas (dan ini alasan kenapa kamu perlu izin bertahap, bukan cuma soal administrasi).

5. **Ketidakpastian mutu stockpile itu nyata dan sering diabaikan.** Mutu tiap stockpile cuma diketahui dari sampel, bukan diketahui pasti — jadi model campuran yang paling akurat pun tetap punya batas ketidakpastian. Sistem yang dibangun tanpa memperhitungkan ini bisa kelihatan "berhasil" di uji coba tapi gagal di lapangan begitu sampelnya enggak mewakili stockpile yang sebenarnya.

Kalau digabung: bukan karena masalahnya enggak penting atau enggak terlihat — nilainya besar karena langsung memengaruhi penagihan dan kepatuhan kontrak — tapi karena orang yang melihat masalahnya (operasi) dan orang yang punya alat buat menyelesaikannya (data science/ML) itu jarang ketemu, dan pendekatan lama sudah dianggap "cukup" sampai ada kejadian yang membuktikan sebaliknya.
