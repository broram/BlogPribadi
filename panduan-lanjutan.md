# Panduan Lanjutan Blog Personal

Status: **Fase 1, situs publik.** Sudah ada prototipe Beranda dan Profil & Portofolio. Dokumen ini menjawab dua hal: apa yang kamu perlu siapkan, dan struktur proyek yang tepat untuk sekarang.

## 1. Yang kamu butuhkan selanjutnya

### Konten dari kamu (wajib sebelum desain dilanjutkan)
- [ ] Nama blog final dan nama penulis (sekarang "Cek Dulu" dan "[Nama Kamu]" hanya placeholder)
- [ ] Foto profil (rasio 4:5, rapi, latar sederhana)
- [ ] Bio 3-4 kalimat dan satu kalimat peran (contoh: "Mahasiswa Informatika, penulis, pembuat aplikasi")
- [ ] 3 karya portofolio: judul, jenis, peranmu, satu kalimat hasil, tautan (GitHub, PDF, demo)
- [ ] Email kontak yang boleh tampil publik
- [ ] Tautan profil publik yang mau ditampilkan (GitHub, LinkedIn), jika ada

### Keputusan yang perlu kamu ambil
- [ ] Teknologi: Astro (disarankan) atau HTML statis dulu
- [ ] Hosting dan domain (Cloudflare Pages atau Vercel gratis; domain bisa menyusul)
- [ ] Layanan form kontak (tanpa server sendiri)
- [ ] Analitik: Plausible atau cukup Search Console dulu

### Desain yang belum dibuat (urutan prioritas)
1. Template artikel Ruang Klarifikasi (paling penting, menentukan data backend)
2. Halaman daftar `/klarifikasi`
3. Halaman Metodologi
4. Kontak, Privacy Policy, Disclaimer (teks, tampilan sederhana)
5. 404 dan versi cetak/baca artikel

### Konten tulisan
- [ ] 3 artikel contoh Ruang Klarifikasi sebelum peluncuran
- [ ] Teks Metodologi, Privacy Policy, Disclaimer (aku bisa bantu draf; untuk aspek hukum konsultasikan ke orang yang paham)

## 2. Struktur proyek yang tepat untuk sekarang

Pilih struktur **statis dan berbasis file**. Belum perlu database atau server. Struktur ini langsung siap dipindah ke Astro.

```
blog-personal/
├── public/
│   ├── images/            # foto, sampul (WebP, sudah dikompres)
│   └── favicon.svg
├── src/
│   ├── content/
│   │   ├── klarifikasi/   # satu file .md per artikel verifikasi
│   │   ├── analisis/      # opini, berlabel
│   │   ├── catatan-metode/
│   │   └── portofolio/    # satu file .md per karya
│   ├── pages/
│   │   ├── index.astro            # Beranda
│   │   ├── tentang.astro          # Profil & portofolio
│   │   ├── metodologi.astro
│   │   ├── kontak.astro
│   │   ├── privacy-policy.astro
│   │   ├── disclaimer.astro
│   │   └── klarifikasi/
│   │       ├── index.astro        # daftar
│   │       └── [slug].astro       # template artikel
│   ├── components/        # Hero, NavPanel, Card, VerdictChip, SourceList
│   ├── layouts/           # BaseLayout (gelap), ArticleLayout (krem)
│   └── styles/tokens.css  # warna, font, bayangan dari prototipe
└── README.md
```

Alasan struktur ini:
- Artikel adalah file Markdown, jadi mudah ditulis, di-backup lewat Git, dan dicek riwayat perubahannya (cocok dengan kebijakan koreksi).
- Komponen dan token desain dipakai ulang, jadi seluruh halaman tetap konsisten.
- Tidak ada data pengguna di fase ini, jadi tidak ada risiko privasi dari backend.

## 3. Skema frontmatter

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

Aturan: tidak boleh `published` tanpa minimal satu sumber, verdict, dan `method_limits`.

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

## 4. Urutan kerja yang disarankan

1. Isi daftar konten di bagian 1 dan tentukan nama.
2. Desain template artikel Ruang Klarifikasi.
3. Siapkan proyek Astro dengan struktur di atas, pindahkan token dan komponen dari prototipe.
4. Tulis halaman wajib dan 3 artikel contoh.
5. Pasang analitik dan Privacy Policy yang sesuai, lalu rilis.

## 5. Ditunda

- Statistik Verdict (Fase 3, bisa dihitung saat build dari frontmatter)
- Ruang teman dengan login (Fase 4, perlu backend dan autentikasi sungguhan, bukan kode tanggal lahir)
- Komentar publik (mulai tanpa komentar atau dengan moderasi)
