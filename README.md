# Blog Personal — Cek Dulu

Blog personal ini berfokus pada profil dan portofolio penulis serta **Ruang Klarifikasi**: pemeriksaan klaim dengan sumber yang dapat ditelusuri, konteks yang cukup, dan kebijakan koreksi yang terbuka.

## Status dan arah proyek

- **Tahap saat ini:** fondasi situs publik dan prototipe desain.
- **Teknologi:** belum final. Struktur konten disiapkan agar mudah dipindahkan ke Astro, tetapi belum ada framework atau backend yang dipaksakan.
- **Ruang teman:** ditunda. Jika kelak dibuat, area privat harus dipisahkan dari situs publik dan memakai autentikasi yang layak.
- **Konten artikel:** disimpan sebagai berkas Markdown; database atau server belum diperlukan untuk tahap awal.

## Laporan progres proyek

**Pembaruan: 6 November 2026**

### Yang sudah dikerjakan

- Membuat prototipe HTML untuk beranda dan halaman profil/portofolio.
- Menyusun konsep blog, arah desain, peta konten, metodologi klarifikasi, dan tahapan pengembangan.
- Memindahkan isi `deskripsi.txt` ke README agar konsep proyek terdokumentasi di satu tempat.
- Menyiapkan folder awal untuk aset, konten, halaman klarifikasi, komponen, layout, dan style. Folder-folder tersebut masih kosong selain berkas `.gitkeep`.
- Menambahkan struktur target, penjelasan fungsi folder, dan contoh skema konten di README.

### Yang belum dikerjakan

- Situs belum menjadi aplikasi yang bisa dijalankan: Astro/HTML statis belum diputuskan dan belum ada konfigurasi build.
- Halaman Astro, komponen, layout, dan token CSS yang tercantum pada struktur target belum dibuat.
- Nama blog dan penulis masih placeholder; foto, bio final, karya portofolio, email, dan tautan profil publik belum dilengkapi.
- Template dan daftar artikel klarifikasi, halaman metodologi/kontak/kebijakan, serta tiga artikel contoh belum selesai.
- Hosting, domain, form kontak, dan analitik belum dipilih atau dipasang.

**Kesimpulan:** proyek sudah memiliki konsep, dokumentasi, prototipe desain, dan persiapan struktur folder. Ini belum keseluruhan proyek dan belum siap diluncurkan; tahap berikutnya adalah melengkapi bahan profil dan memilih teknologi, lalu membangun halaman situs serta kontennya.

## Struktur target proyek

Folder-folder untuk struktur berikut sudah disiapkan. Berkas aplikasi Astro dan aset yang belum tersedia akan dibuat saat teknologi dan implementasi ditetapkan.

```text
blogpribadi/
├── public/
│   ├── images/                      # Foto dan sampul yang sudah dioptimalkan
│   └── favicon.svg                  # Ikon situs (ditambahkan saat aset siap)
├── src/
│   ├── content/
│   │   ├── klarifikasi/             # Satu berkas Markdown per artikel verifikasi
│   │   ├── analisis/                # Analisis dan opini yang diberi label
│   │   ├── catatan-metode/           # Artikel edukasi metode pemeriksaan
│   │   └── portofolio/              # Satu berkas Markdown per karya
│   ├── pages/
│   │   ├── index.astro              # Beranda
│   │   ├── tentang.astro            # Profil dan portofolio
│   │   ├── metodologi.astro         # Metodologi dan kebijakan koreksi
│   │   ├── kontak.astro             # Kontak dan kanal koreksi
│   │   ├── privacy-policy.astro     # Kebijakan privasi
│   │   ├── disclaimer.astro         # Disclaimer
│   │   └── klarifikasi/
│   │       ├── index.astro          # Daftar artikel klarifikasi
│   │       └── [slug].astro         # Template halaman artikel
│   ├── components/                  # Komponen UI yang digunakan ulang
│   ├── layouts/                     # Kerangka halaman dan artikel
│   └── styles/
│       └── tokens.css               # Token warna, tipografi, dan bayangan
├── Cek Dulu — Beranda Blog Personal.html
├── Cek Dulu — Profil & Portofolio.html
├── panduan-lanjutan.md              # Panduan struktur dan langkah pengembangan
├── Blog Personal Brief Lanjutan dan Dasar Backend.md
└── README.md                        # Ringkasan, struktur, dan spesifikasi proyek
```

Folder `public/` berisi aset statis yang akan disajikan apa adanya. `src/content/` memisahkan artikel menurut jenisnya agar konten mudah ditulis, ditinjau, dan dilacak riwayatnya. `src/pages/` memetakan halaman dan URL situs; `[slug].astro` adalah template dinamis untuk setiap artikel klarifikasi. `src/components/` menampung elemen antarmuka yang dipakai ulang, `src/layouts/` kerangka halaman, dan `src/styles/tokens.css` nilai desain bersama. Berkas `.gitkeep` di folder kosong hanya menjaga struktur folder tetap tersedia; berkas aplikasi Astro dan aset akan ditambahkan saat implementasi dimulai.

### Berkas yang sudah tersedia

- [Cek Dulu — Beranda Blog Personal.html](./Cek%20Dulu%20%E2%80%94%20Beranda%20Blog%20Personal.html) adalah prototipe visual beranda.
- [Cek Dulu — Profil & Portofolio.html](./Cek%20Dulu%20%E2%80%94%20Profil%20%26%20Portofolio.html) adalah prototipe visual halaman profil dan portofolio.
- [panduan-lanjutan.md](./panduan-lanjutan.md) berisi kebutuhan yang perlu disiapkan, struktur yang disarankan, skema frontmatter, dan urutan pengerjaan.
- [Blog Personal Brief Lanjutan dan Dasar Backend.md](./Blog%20Personal%20Brief%20Lanjutan%20dan%20Dasar%20Backend.md) merangkum keputusan desain, peta situs, model data, serta kebutuhan backend per fase.

## Skema konten yang disarankan

### Artikel klarifikasi

```yaml
---
title: ""
slug: ""
summary: ""
claim_text: ""
claim_where: ""
claim_first_seen: 2026-01-01
verdict: perlu-konteks   # benar | salah | menyesatkan | perlu-konteks | belum-pasti
sources:
  - title: ""
    url: ""
    publisher: ""
    kind: primer          # primer | sekunder
    accessed: 2026-01-01
method_limits: ""
status: draft             # draft | review | published
published_at: 2026-01-01
revisions:
  - date: 2026-01-01
    note: ""
cover_image: ""
image_license: ""
---
```

Artikel klarifikasi tidak boleh berstatus `published` sebelum memiliki setidaknya satu sumber, verdict, dan penjelasan batasan metode.

### Karya portofolio

```yaml
---
title: ""
kind: aplikasi          # aplikasi | tulisan | verifikasi | lainnya
role: ""
result: ""              # satu kalimat hasil
link: ""
year: 2026
featured: true
---
```

---

# Konsep Blog Personal dan Ruang Klarifikasi

Bagian berikut memindahkan seluruh isi `deskripsi.txt` ke README agar konsep dan spesifikasi proyek tersimpan di satu tempat. Berkas sumber `deskripsi.txt` sudah tidak digunakan lagi.

## 1. Gambaran Umum

Blog ini adalah situs personal dengan dua tujuan jangka panjang:
- Membangun branding profesional melalui profil, portofolio, analisis, dan tulisan.
- Menyediakan ruang terbatas untuk teman berbagi cerita dan berdiskusi.

Kedua tujuan tersebut memiliki kebutuhan privasi dan pengalaman yang berbeda. Karena itu, pengembangan dilakukan bertahap. Fase awal berfokus pada situs publik dan konten verifikasi. Ruang teman menjadi rencana fase berikutnya, sebagai area terpisah dengan akses yang benar-benar terlindungi.

## 2. Tujuan dan Positioning

Tujuan utama situs publik adalah membantu pembaca memeriksa informasi sebelum mempercayai atau ikut menyebarkannya. Situs ini membahas isu yang ramai atau viral dengan proses verifikasi yang transparan, sumber yang dapat ditelusuri, dan bahasa yang bertanggung jawab.

Positioning:

> Untuk orang yang mau mengecek dulu sebelum percaya atau ikut berkomentar.

Pendekatan ini tidak menganggap kebenaran hanya dapat diakses oleh orang yang sudah ahli. Konten ditujukan kepada siapa pun yang bersedia mencari informasi dan mempertimbangkan bukti secara terbuka.

## 3. Target Pembaca

- Pembaca umum yang menemukan klaim atau isu viral di media sosial.
- Orang yang ingin memahami konteks dan sumber informasi dengan lebih baik.
- Calon klien, rekan kerja, atau komunitas yang ingin mengenal profil dan cara berpikir pemilik blog.
- Teman dekat sebagai calon pengguna ruang privat pada fase pengembangan selanjutnya.

## 4. Cakupan Konten

Konten publik dibagi dengan label yang jelas agar fakta, analisis, dan opini tidak tercampur:

### 4.1 Ruang Klarifikasi

Artikel verifikasi isu atau klaim yang beredar. Setiap artikel berupaya menjelaskan bukti, konteks, metode, dan keterbatasan pemeriksaan.

### 4.2 Analisis dan Opini

Tulisan yang menyampaikan analisis atau sudut pandang pribadi. Konten ini harus diberi label sebagai analisis/opini dan membedakan fakta yang terverifikasi dari penilaian penulis.

### 4.3 Catatan Metode

Konten edukasi mengenai cara memeriksa informasi, misalnya cara menelusuri sumber primer, memeriksa foto atau video, dan memahami keterbatasan bukti digital.

### 4.4 Profil dan Portofolio

Informasi singkat tentang pemilik blog, pengalaman, karya, dan cara menghubungi.

## 5. Format Artikel Ruang Klarifikasi

Setiap artikel Ruang Klarifikasi dapat menggunakan susunan berikut:

- **Klaim:** kutipan atau ringkasan klaim, lokasi klaim beredar, dan tanggal pertama kali ditemukan atau diperiksa.
- **Asal-usul:** informasi yang dapat dipastikan mengenai peredaran klaim, tanpa menuduh atau menyudutkan individu.
- **Fakta dan verifikasi:** poin-poin pemeriksaan dengan tautan ke sumber yang relevan.
- **Konteks yang hilang:** informasi penting yang tidak disampaikan atau tidak terlihat dalam klaim.
- **Verdict:** Benar, Salah, Menyesatkan, Perlu Konteks, atau Belum Bisa Dipastikan.
- **Metode dan batasan:** apa yang diperiksa, sumber atau metode yang digunakan, serta hal yang belum dapat dipastikan.
- **Riwayat pembaruan:** tanggal dan ringkasan perubahan jika artikel dikoreksi atau dilengkapi.

Verdict harus mengikuti bukti yang tersedia. Jika bukti belum cukup, gunakan "Belum Bisa Dipastikan" daripada memaksakan kesimpulan.

## 6. Metodologi dan Kebijakan Koreksi

Halaman Metodologi menjelaskan:
- Cara memilih klaim atau isu yang akan diperiksa.
- Cara membedakan klaim faktual, interpretasi, dan opini.
- Prioritas sumber: sumber primer, kemudian sumber sekunder tepercaya, dengan opini digunakan secara hati-hati dan tidak diperlakukan sebagai bukti utama.
- Cara menilai bukti dan menentukan verdict.
- Batas pemeriksaan dan keadaan ketika kesimpulan belum dapat dipastikan.

Jika ditemukan kesalahan atau informasi baru yang memengaruhi isi, artikel akan diperbarui dengan tanggal dan catatan perubahan yang terlihat. Koreksi merupakan bagian dari komitmen terhadap akurasi dan transparansi.

Target penerbitan awal adalah satu artikel mendalam setiap satu hingga dua minggu. Kualitas pemeriksaan dan keterlacakan sumber lebih diutamakan daripada jumlah artikel.

## 7. Ruang Teman dan Privasi

Ruang teman bukan bagian dari peluncuran awal. Cerita pribadi dan diskusi internal tidak akan ditempatkan di area publik atau dilindungi hanya dengan kode yang mudah ditebak, seperti tanggal lahir atau nama.

Jika ruang ini tetap dibutuhkan, aksesnya harus dibuat terpisah dari situs publik dan menggunakan autentikasi yang layak, seperti akun dengan email dan kata sandi atau tautan undangan unik. Data yang dikumpulkan harus dibatasi dan dijelaskan kepada pengguna. Pilihan sederhana untuk tahap awal adalah menggunakan layanan privat yang sudah tersedia, seperti grup WhatsApp/Discord atau Notion privat.

## 8. Prinsip Etika dan Legalitas

- Fokus pada pemeriksaan klaim dan bukti, bukan menyerang pribadi.
- Gunakan bahasa yang hati-hati; hindari menyatakan seseorang berbohong tanpa dasar yang memadai.
- Cantumkan sumber dan berikan konteks yang cukup agar pembaca dapat memeriksanya sendiri.
- Hormati hak cipta. Gunakan foto atau ilustrasi berlisensi atau karya sendiri.
- Jangan menampilkan tangkapan layar yang membuka identitas atau data pribadi tanpa alasan yang sah; samarkan informasi pribadi jika diperlukan.
- Sediakan halaman About, Contact, Privacy Policy, Disclaimer, dan Metodologi.
- Privacy Policy harus menjelaskan data yang dikumpulkan, tujuan penggunaannya, serta layanan analitik yang digunakan.
- Pada fase awal, komentar dapat ditiadakan atau dimoderasi. Sediakan kanal kontak untuk tanggapan dan koreksi.
- Untuk keputusan editorial yang berisiko hukum, konsultasikan dengan pihak yang memahami hukum terkait.

## 9. Arah Desain

### Brief desain awal

Design a modern premium personal blog website with an **organic 3D editorial aesthetic**, inspired by botanical compositions, natural materials, and contemporary luxury web design.

The overall visual style should feel **calm, sophisticated, tactile, warm, natural, and artistic**. Use a combination of **deep forest green, muted teal, sage green, earthy brown, warm beige, cream, and subtle gold accents**.

Create a **layered composition with simulated 3D depth**, using soft shadows, subtle highlights, floating elements, overlapping cards, rounded corners, dimensional surfaces, and realistic depth. The website should look three-dimensional without relying on heavy real-time 3D or WebGL. Prioritize lightweight visual techniques such as CSS gradients, soft shadows, blur, layered elements, subtle textures, and optimized images.

#### Hero Section

Create a large immersive hero section with an asymmetrical editorial layout. The left side contains large elegant typography, a short introduction, and a rounded CTA button. The right side contains layered botanical elements such as leaves and organic shapes that partially overlap the section boundaries, creating a floating 3D effect.

Use a **dark green / teal background combined with earthy brown surfaces**. Botanical objects should have realistic textures and subtle shadows. Some elements can extend outside their containers to create depth.

#### Navigation / Feature Section

Below the hero, create a wide rounded rectangular navigation panel with a dark translucent green surface. Arrange several navigation items horizontally using minimalist line-art icons. Each item should have an icon, short title, and small supporting text.

Use subtle glassmorphism, soft inner highlights, thin borders, and low-intensity shadows. Keep the section elegant and spacious rather than overly dense.

#### Content Grid

Create a flexible editorial card grid underneath. Use large rounded cards with varying sizes and compositions rather than a rigid symmetrical grid.

Mix:
- solid color cards,
- botanical illustration cards,
- photography cards,
- text-based cards,
- minimal icon cards.

Use muted green, sage, brown, beige, and cream surfaces. Each card should have **large rounded corners, soft 3D shadows, subtle gradients, and dimensional lighting**.

Some cards should appear slightly elevated from the background, while others should blend naturally into the surface.

#### Background

Use a textured organic background inspired by **paper, fabric, leaves, and natural surfaces**. Add extremely subtle grain/noise and abstract botanical shadows. The texture should be elegant and almost imperceptible, never distracting from the content.

#### Typography

Use a modern editorial sans-serif typography system with:
- large bold display headings,
- clean medium-weight navigation text,
- small minimalist supporting text,
- generous line spacing,
- strong visual hierarchy.

Typography should feel modern, clean, premium, and slightly editorial.

#### Visual Details

Use:
- large rounded corners,
- soft ambient shadows,
- subtle 3D elevation,
- layered objects,
- organic shapes,
- botanical motifs,
- muted natural colors,
- translucent surfaces,
- subtle gradients,
- tactile textures,
- asymmetrical editorial composition,
- generous whitespace.

Avoid overly futuristic interfaces, neon colors, excessive glassmorphism, sharp geometric layouts, excessive animations, or complicated 3D models.

The final result should feel like a **luxury botanical editorial magazine transformed into a modern personal blog interface** — artistic and dimensional, but still lightweight, readable, responsive, and practical for a real website.

### Ringkasan arahan desain

Desain situs mengusung estetika editorial organik dengan kesan tenang, profesional, hangat, alami, dan artistik. Palet utama terdiri dari hijau hutan, teal redup, sage, cokelat tanah, beige hangat, dan krem. Emas digunakan sebagai aksen dekoratif, bukan warna teks utama.

Hero dan navigasi dapat menggunakan latar hijau tua/teal dengan komposisi editorial asimetris. Halaman artikel menggunakan latar terang bernuansa krem agar nyaman dibaca dalam waktu lama. Tipografi memiliki hierarki yang jelas, jarak baris yang lega, serta keterbacaan yang diutamakan.

Kedalaman visual dibuat dengan teknik ringan seperti gradasi, bayangan lembut, lapisan elemen, tekstur halus, dan sudut membulat. Hindari efek 3D berat, animasi berlebihan, blur yang berlebihan di perangkat seluler, serta antarmuka yang terlalu ramai.

Aset botani dibatasi dan dipilih dengan cermat. Gunakan ilustrasi berlisensi atau karya sendiri, optimalkan ukuran gambar, dan siapkan beberapa aset utama sebelum memperluas variasi visual.

Desain dibuat mobile-first. Komposisi desktop yang asimetris harus berubah menjadi susunan vertikal yang rapi di layar kecil. Kontras teks dan latar harus tetap nyaman dibaca.

## 10. Platform dan Teknologi

Platform yang direncanakan adalah situs blog personal. Karena konten utamanya berupa artikel, static site generator seperti Astro dengan Markdown/MDX dapat dipertimbangkan agar situs ringan dan artikel mudah dikelola. Pilihan teknologi dan hosting ditetapkan saat tahap implementasi sesuai kebutuhan serta kemampuan pemilik situs.

## 11. Analitik dan Evaluasi

Analitik digunakan untuk memahami jangkauan dan kebutuhan pembaca, bukan untuk mengumpulkan data yang tidak diperlukan. Plausible dapat dipertimbangkan sebagai pilihan analitik yang lebih ringan dan berorientasi privasi. Google Search Console dapat digunakan untuk memantau performa pencarian.

Evaluasi konten dapat dikembangkan bertahap, misalnya melalui halaman Statistik Verdict atau daftar isu yang sudah diperiksa. Bentuk, indikator, dan periode evaluasi ditentukan setelah situs memiliki konten dan data yang cukup.

## 12. Tahapan Pengerjaan

### Fase 1 — Fondasi situs publik

- Beranda.
- Profil/About dan Portofolio.
- Contact.
- Privacy Policy dan Disclaimer.
- Metodologi.
- Kategori dan template artikel.

### Fase 2 — Konten awal dan peluncuran

- Siapkan tiga artikel Ruang Klarifikasi sebagai contoh.
- Pastikan setiap artikel memiliki sumber tertaut, verdict, batasan, serta riwayat pembaruan bila ada.
- Terapkan desain responsif, SEO dasar, dan analitik yang sesuai dengan kebijakan privasi.

### Fase 3 — Evaluasi

- Tinjau keterbacaan, jangkauan, masukan pembaca, dan konsistensi proses verifikasi.
- Pertimbangkan halaman Statistik Verdict atau daftar isu yang telah diperiksa.

### Fase 4 — Ruang teman, jika masih dibutuhkan

- Rancang sebagai area terpisah dari konten publik.
- Gunakan autentikasi yang sesuai untuk privasi, bukan kode berbasis informasi pribadi yang mudah ditebak.
- Tetapkan aturan akses, moderasi, dan pengelolaan data sebelum mengumpulkan konten pribadi.

Catatan: contoh format dan praktik dari TurnBackHoax (Mafindo) serta Cek Fakta Tempo dapat dipelajari sebagai referensi. Situs ini tetap harus menjelaskan metodologi dan keputusan editorialnya sendiri secara transparan.
