# Blog Personal: Brief Lanjutan dan Dasar Backend

Dokumen ini merangkum keputusan sejauh ini supaya pekerjaan bisa dilanjutkan (desain halaman lain, lalu backend) tanpa mengulang diskusi. Nama blog "Cek Dulu" masih sementara.

## 1. Ringkasan proyek

Blog personal dengan fokus utama **situs publik**: branding profesional dan **Ruang Klarifikasi** (verifikasi isu viral dengan sumber tertaut). Positioning: *untuk orang yang mau mengecek dulu sebelum percaya atau ikut berkomentar.* Ruang teman (curhat, diskusi internal) **ditunda** ke fase terakhir sebagai area terpisah dengan login.

## 2. Keputusan yang sudah diambil

- Fase 1 hanya situs publik. Ruang teman bukan bagian peluncuran awal.
- UI/UX dikerjakan bertahap, dimulai dari **beranda** (sudah ada prototipe HTML).
- Halaman artikel memakai latar krem terang untuk keterbacaan. Hero dan panel navigasi boleh gelap.
- Efek 3D hanya lewat CSS (gradien, bayangan, lapisan), tanpa WebGL.
- Emas hanya aksen dekoratif, bukan warna teks.
- Komentar ditiadakan atau dimoderasi di fase awal. Koreksi lewat halaman kontak.
- Teknologi disarankan, belum final: Astro + Markdown/MDX untuk situs statis.

## 3. Peta situs (sitemap)

| Rute | Isi | Fase |
| --- | --- | --- |
| `/` | Beranda | 1 |
| `/klarifikasi` dan `/klarifikasi/[slug]` | Daftar dan artikel verifikasi | 1-2 |
| `/analisis` | Analisis dan opini (berlabel) | 1-2 |
| `/catatan-metode` | Edukasi cara memeriksa informasi | 2 |
| `/metodologi` | Cara memilih isu, prioritas sumber, penentuan verdict, kebijakan koreksi | 1 |
| `/tentang`, `/portofolio`, `/kontak` | Profil dan kontak | 1 |
| `/privacy-policy`, `/disclaimer` | Halaman wajib | 1 |
| `/statistik-verdict` | Evaluasi, daftar isu yang sudah dicek | 3 |
| `/ruang-teman` | Area privat dengan login | 4 |

## 4. Design tokens (dari prototipe beranda)

- **Warna:** forest `#12302a`, teal `#2b5953`, sage `#a8b79e`, brown `#6a4733`, beige `#e3d4ba`, cream `#f6f0e2`, gold `#c4a25a`.
- **Verdict:** Benar `#2f6b46`, Salah `#99392d`, Menyesatkan `#9c5e17`, Perlu Konteks `#35646d`, Belum Bisa Dipastikan `#646658`. Selalu tampil dengan teks, tidak hanya warna.
- **Tipografi:** Bricolage Grotesque (judul), Instrument Sans (isi). Garis teks maksimal sekitar 70 karakter untuk artikel.
- **Bentuk:** sudut membulat besar (sekitar 2rem), bayangan lembut berlapis, grain halus di latar.
- **Mobile:** susunan asimetris berubah menjadi satu kolom. Blur dimatikan di layar kecil.
- **Mode gelap:** token `--paper`, `--ink`, `--card` sudah punya varian gelap.

## 5. Komponen beranda

1. Hero: judul besar, pengantar, CTA, daun botani berlapis, kartu contoh klarifikasi.
2. Panel navigasi: empat bagian dengan ikon garis.
3. Grid kartu editorial: kartu unggulan, metodologi plus legenda verdict, kartu foto, ikon, teks, koreksi.
4. Footer: tautan halaman wajib.

Aset botani dibatasi (daun SVG yang dipakai ulang). Foto harus berlisensi atau karya sendiri.

## 6. Model data artikel (dasar backend)

Untuk Astro, ini menjadi skema *content collection* di frontmatter Markdown. Untuk database, ini menjadi tabel `articles`.

| Field | Tipe | Catatan |
| --- | --- | --- |
| `slug` | string unik | URL artikel |
| `type` | enum | `klarifikasi`, `analisis`, `catatan-metode` |
| `title`, `summary` | string |  |
| `claim_text` | string | Kutipan atau ringkasan klaim |
| `claim_where`, `claim_first_seen` | string, date | Tempat dan tanggal klaim ditemukan |
| `origin_note` | text | Asal-usul tanpa menuduh individu |
| `verdict` | enum | `benar`, `salah`, `menyesatkan`, `perlu-konteks`, `belum-pasti` (hanya untuk tipe klarifikasi) |
| `missing_context` | text |  |
| `method_limits` | text | Metode dan batasan pemeriksaan |
| `sources[]` | daftar | `title`, `url`, `publisher`, `kind` (primer/sekunder), `accessed_at` |
| `status` | enum | `draft`, `review`, `published` |
| `published_at`, `updated_at` | datetime |  |
| `revisions[]` | daftar | `date`, `note` (riwayat pembaruan) |
| `cover_image`, `image_license` | string | Lisensi gambar wajib diisi |

Aturan validasi yang disarankan: artikel `klarifikasi` tidak boleh `published` tanpa minimal satu sumber, verdict, dan `method_limits`.

## 7. Kebutuhan backend per fase

- **Fase 1-2:** cukup Markdown/MDX dan build statis. Form kontak lewat layanan form (tanpa server sendiri). Analitik Plausible atau Search Console, disebut di Privacy Policy.
- **Fase 3:** `/statistik-verdict` bisa dihitung saat build dari frontmatter (jumlah per verdict, per bulan).
- **Fase 4 (ruang teman):** perlu backend sungguhan. Autentikasi akun (email + password) atau magic link undangan, bukan kode tanggal lahir atau nama. Tabel `users`, `invites`, `posts`, `comments`, dengan data dibatasi dan dijelaskan ke pengguna. Aturan moderasi dan penghapusan data ditetapkan sebelum konten pribadi dikumpulkan. Area ini terpisah dari konten publik (rute dan data sendiri).

## 8. Langkah berikutnya

1. Tinjau prototipe beranda, lalu tentukan nama blog dan nama penulis.
2. Rancang halaman artikel Ruang Klarifikasi (template terpenting).
3. Rancang halaman Metodologi dan About.
4. Pilih teknologi dan hosting, lalu mulai implementasi Fase 1.
5. Siapkan tiga artikel contoh sebelum peluncuran.

Catatan: untuk risiko hukum seperti pencemaran nama baik dan UU ITE, konsultasikan dengan orang yang memahami hukum.
