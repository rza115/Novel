# Suara dari Ambang — Reader

Reader statis (HTML + vanilla JS, tanpa build step) yang mengambil bab langsung
dari `github.com/rza115/Novel/Chapters` dan menampilkannya sebagai halaman baca
yang sudah dipolish — bukan markdown mentah.

## Cara kerja

- Daftar bab diambil dari `api.github.com/repos/rza115/Novel/contents/Chapters`
  (public, tanpa token, sekitar 60 request/jam per IP — cukup untuk pemakaian pribadi).
- Isi tiap bab diambil dari `raw.githubusercontent.com` (via field `download_url`
  yang dikembalikan API di atas).
- Parser khusus (bukan markdown generik) mengenali format bab kamu:
  - `# Bab NNN — Judul` → judul & nomor bab
  - baris `**Status:** ... **Lokasi:** ... **Tema utama:** ... **Tokoh yang muncul:** ...`
    → jadi chip metadata di atas bab
  - pemisah `---` antar adegan → dirender jadi motif "ambang" (garis + jejak kucing
    melintas), bukan garis horizontal polos — mengikuti simbol batas yang berulang
    di novelmu sendiri
  - blok `## Catatan Penulis (opsional, dihapus di draft final)` sampai akhir file
    otomatis **dibuang** dari tampilan baca (itu memang catatan kerja, bukan bagian
    cerita)
- Progres baca (bab terakhir dibuka + bab yang sudah dibaca) disimpan di
  `localStorage` browser, jadi persist antar sesi tanpa perlu backend.

Tidak butuh Supabase sama sekali untuk versi ini — semuanya baca publik dari
GitHub, jadi murni statis. Kalau nanti kamu mau tambah akun/sync progres lintas
device, itu baru butuh Supabase (tinggal bilang, tinggal tambah).

## Deploy ke Vercel

Paling cepat lewat Vercel CLI:

```bash
npm i -g vercel   # kalau belum ada
cd novel-reader
vercel deploy --prod
```

Atau tanpa CLI:
1. Push folder ini (cukup `index.html`) ke repo GitHub baru (atau folder di repo yang ada).
2. Di dashboard Vercel → "Add New Project" → import repo itu.
3. Framework preset: pilih **Other** (tidak perlu build command / output directory,
   karena ini static HTML murni).
4. Deploy.

Atau paling simpel: buka `index.html` langsung di browser — sudah jalan tanpa
server sama sekali, karena semua fetch-nya ke API publik.

## Kalau mau ganti sumber

Semua konfigurasi ada di bagian atas `<script>` di `index.html`:

```js
const OWNER = "rza115";
const REPO = "Novel";
const BRANCH = "main";
const CHAPTERS_DIR = "Chapters";
```

## Kalau format bab kamu berubah

Parser ada di fungsi `parseChapter()`. Kalau kamu ubah struktur front-matter
bab (misalnya urutan field metadata, atau nama section catatan penulis), update
regex di fungsi itu — bagian lain (render, navigasi, progres) tidak perlu diubah.
