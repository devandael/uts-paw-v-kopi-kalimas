# Kopi Kalimas — UTS Pemrograman Antarmuka Web (ITATS, 2026/2027)

Situs multihalaman untuk kedai kopi fiktif **Kopi Kalimas** (sub-tema 1: Kedai kopi / warung makan). Framework: **Bootstrap 5.3.3 (CDN)**. Tanpa JavaScript buatan sendiri.

Situs: `https://<akun>.github.io/uts-paw-<kelas>-kopi-kalimas/`

## Anggota & pembagian halaman
| NPM | Nama | Akun GitHub | Halaman |
|---|---|---|---|
| ADITYA MAULANA ZIDQY
06.2025.1.07923 | aditya maulana zidqy | [akun1] | `index.html`, `katalog.html` |
| DEVANDA EKA LISTYONO 06.2025.1.07876 | devanda eka listyono | devandael | `reservasi.html`, `tentang.html`, `terima-kasih.html` |

`css/style.css` dikerjakan bergantian, lihat riwayat commit.

## Target pengguna
Mahasiswa dan pekerja lepas di sekitar Surabaya yang ingin melihat menu dan memesan meja lewat ponsel.

## Sitemap & denah
`index` → `katalog` · `reservasi` → `terima-kasih` · `tentang`. Navigasi sama di semua halaman.

Sketsa denah: [mobile](img/sketsa-mobile.png) dan [desktop](img/sketsa-desktop.png).
- Mobile: semua 1 kolom, galeri menu 1 kolom, Tentang bertumpuk.
- Tablet (≥ 48em): hero 2 kolom, Tentang 2 kolom.
- Desktop (≥ 64em): hero 5:4, Tentang 3 kolom (`profil tim lokasi` / `faq`).

## Token (`:root`)
| Token | Terang | Gelap | Pemakaian |
|---|---|---|---|
| `--c-bg` / `--c-surface` | #f3f6f4 / #fff | #0e1a17 / #162623 | latar halaman / kartu |
| `--c-text` / `--c-muted` | #14231f / #46605a | #e8f1ee / #b7cbc5 | teks utama / teks bantu |
| `--c-primary` / `--c-primary-d` | #0f5a4d / #0a4036 | #6fd1bb / #9be3d1 | tombol, tautan, hover |
| `--c-on-primary` | #fff | #0e1a17 | teks di atas tombol |
| `--c-accent` / `--c-on-accent` | #f2b134 / #14231f | sama | badge, garis aktif |
| `--c-border` | #cfdcd7 | #2c423d | garis tepi |
| `--c-danger` | #a4161a | #ff9a9a | input tidak valid |
| `--c-focus` | #0b5cad | #8ec5ff | outline fokus keyboard |
| `--c-invert` | 0 | 1 | membalik ikon hamburger di mode gelap |
| `--font-head`, `--font-body` | Palatino/Georgia, system-ui | | tipografi (2 keluarga) |
| `--space-1`, `--space-2`, `--space-3` | .5 / 1 / 2 rem | | jarak |
| `--radius` | .5rem | | sudut |

## Breakpoint
| Nama | Lebar | Perubahan |
|---|---|---|
| Dasar | < 48em | 1 kolom |
| md | ≥ 48em | hero 2 kolom; Tentang 2 kolom |
| lg | ≥ 64em | hero 5:4; Tentang 3 kolom |

## Framework vs CSS sendiri
- **Bootstrap:** navbar responsif (collapse), grid `row-cols-*`, card, button, badge, alert, table, form-control/select/check.
- **CSS sendiri:** token dan dark mode, `grid-template-areas` (hero, Tentang), galeri `auto-fit`, header sticky, badge `position:absolute`, gaya `:user-invalid`, penimpaan variabel `--bs-*`, dan perbaikan tanda centang Bootstrap di mode gelap.
- **Perbandingan kartu.** Bootstrap: `<div class="card"><div class="card-body">…` (2 class, gaya siap pakai, tetapi tampilan bawaan perlu ditimpa). CSS murni: `.menu-card{border:1px solid var(--c-border);border-radius:var(--radius);display:flex;flex-direction:column}` (±6 baris, kendali penuh, tetapi semuanya ditulis sendiri). Kami memakai Bootstrap untuk kerangka lalu menimpa warna lewat token supaya tidak terlihat seperti template bawaan.

## Bukti pengujian
Tangkapan layar (full page): [360px](img/ss-360.png) (Beranda), [768px](img/ss-768.png) (Menu), [1280px](img/ss-1280.png) (Tentang), [mode gelap](img/ss-gelap.png) (Reservasi, ada contoh validasi).

| Halaman | Lighthouse Accessibility | W3C Validator |
|---|---|---|
| index | 100 | 0 error |
| katalog | 100 | 0 error |
| reservasi | 100 | 0 error |
| tentang | 100 | 0 error |
| terima-kasih | 100 | 0 error |

- Lighthouse (mode mobile, Chromium) dijalankan pada salinan lokal dengan file Bootstrap 5.3.3 yang sama. Axe-core: 0 pelanggaran di mode terang dan gelap, lebar 360 dan 1280px.
- W3C: Nu HTML Checker (vnu), semua halaman 0 error dan 0 warning.
- Lebar 320px sampai 1280px: tidak ada scroll mendatar. Target sentuh menu, tombol, dan pilihan form minimal 44px.
- Kontras (dihitung dari token): semua pasangan teks/latar ≥ 6,1 : 1 di mode terang dan gelap.
- Uji keyboard (Tab): skip link jadi fokus pertama, lalu menu, isi halaman, dan form dari atas ke bawah sampai tombol Kirim (25 kali Tab di halaman reservasi). Semua fokus punya outline. Submit form kosong menampilkan pesan validasi browser. FAQ `<details>` bisa dibuka dengan Enter/Spasi.

## Sumber & AI
- Ilustrasi (img/*.webp) dibuat sendiri dalam bentuk SVG (file sumber di `img/sumber/`), lalu diekspor ke WebP ukuran 480 dan 960. Tidak ada foto atau logo merek nyata.
- Peta: OpenStreetMap (© kontributor OpenStreetMap). Framework: Bootstrap 5.3.3 lewat CDN jsDelivr.
- Snippet tanda centang mode gelap mengikuti dokumentasi Bootstrap 5.3 (Forms › Checks and radios).
- AI: Claude (Anthropic) membantu kerangka awal HTML/CSS, ilustrasi SVG, perbaikan aksesibilitas, pengujian otomatis, dan draf README. Seluruh anggota sudah membaca dan memahami kode.
