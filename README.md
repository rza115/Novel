# [Judul Belum Ditentukan]

Sebuah novel observasional yang dinarasikan oleh seekor kucing liar tanpa nama, hidup di antara gang sempit, rumah, sekolah, taman, dan pasar — mengamati manusia dari luar sistem sosial mereka.

Terinspirasi secara struktural oleh *I Am a Cat* (Natsume Sōseki): cerita digerakkan bukan oleh konflik plot, melainkan oleh siklus observasi → refleksi → pertanyaan → ironi → simpulan kecil.

## Cara Pakai Repo Ini

Folder ini adalah **story bible + writing system**, bukan cuma tempat naskah. Tiap folder punya fungsi:

| Folder | Fungsi |
|---|---|
| `StoryBible/` | Aturan main cerita — konsep, tema, filosofi, dunia, narator, gaya, aturan cerita, simbol, nada. Baca ini sebelum nulis bab apa pun. |
| `Characters/` | Profil narator dan tokoh pendukung, plus peta relasi antar mereka. |
| `Observations/` | Bank tema — catatan mentah/ide observasi per topik (keluarga, pertemanan, pendidikan, dll) yang bisa "ditarik" jadi bahan bab. |
| `Chapters/` | Naskah bab, satu file per bab. |
| `Reviews/` | Catatan review terhadap naskah — konsistensi, pacing, kedalaman filosofis, gaya. |
| `Prompts/` | Role/persona prompt buat dipakai di sesi Claude Code CLI — editor, philosopher, critic, dll. |
| `Lessons/` | "Pelajaran" atau pertanyaan reflektif per bab/tema, semacam indeks makna. |

## Alur Kerja yang Disarankan

1. Isi `StoryBible/` dulu sampai solid — ini fondasi, jangan mulai nulis bab sebelum ini jelas.
2. Isi `Characters/narrator.md` dan `Observations/*` sebagai bank bahan.
3. Tiap mau nulis bab baru, ambil 1 topik dari `Observations/`, cek `StoryBible/07_story_rules.md` buat pola loop-nya, lalu tulis di `Chapters/`.
4. Setelah bab jadi, jalankan lewat `Reviews/` checklist dan/atau `Prompts/critic.md`.
5. `Lessons/` diisi belakangan sebagai indeks — bab mana ngomongin apa.

## Status Proyek

Lihat `PROJECT.md` untuk progres dan `AGENTS.md` untuk cara kerja sama Claude/Claude Code di proyek ini.
