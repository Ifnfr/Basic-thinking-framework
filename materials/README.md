# 📚 materials/

Folder ini adalah **tempat penampungan bahan belajar** yang akan dibahas bersama AI (Kiro) dalam sesi active recall dan diskusi.

---

## Kenapa folder ini ada?

Kiro tidak bisa membaca file yang kamu upload langsung di chat (PDF, DOCX, dll). Solusinya:

1. **Simpan bahan di folder ini** (lewat GitHub web)
2. **Sebut nama file di chat Kiro**
3. **Kiro membaca file dari repo** dan langsung membahasnya

---

## Struktur folder

```
materials/
├── README.md               ← file ini
├── tka/                    ← Tes Kemampuan Akademik (penalaran, logika, dll.)
├── matematika-dasar/       ← Aljabar, geometri, statistika, kalkulus dasar
├── bahasa-inggris/         ← Grammar, reading, vocabulary
├── bahasa-indonesia/       ← Linguistik, sastra, EYD, kelas kata
├── _archive/               ← Bahan yang sudah selesai dipelajari
└── _template.md            ← Template untuk file bahan baru
```

---

## Format file yang didukung

| Format | Bisa dibaca? | Catatan |
|--------|:---:|---------|
| `.md` | ✅ | **Paling direkomendasikan** |
| `.txt` | ✅ | Plain text, tanpa formatting |
| `.json`, `.csv` | ✅ | Cocok untuk data / flashcard |
| `.png`, `.jpg`, `.jpeg`, `.webp` | ✅ | Foto slide, papan tulis, catatan tangan |
| `.pdf` | ❌ | Harus copy-paste isinya ke `.md` dulu |
| `.docx`, `.pptx` | ❌ | Harus dikonversi |

---

## Konvensi penamaan file

```
YYYY-MM-DD_topik-spesifik.md
```

Contoh:
- `2026-05-16_kelas-kata-utama.md`
- `2026-05-17_silogisme-dan-penalaran.md`
- `2026-05-18_tenses-overview.md`
- `2026-05-19_limit-fungsi.md`

---

## Cara memanggil di chat Kiro

```
"Bahas materials/bahasa-indonesia/2026-05-16_kelas-kata-utama.md"
"Buatkan soal active recall dari materials/tka/2026-05-17_silogisme.md"
"Jelaskan konsep di materials/matematika-dasar/2026-05-19_limit-fungsi.md"
```

---

## Workflow belajar

1. **Upload** bahan ke subfolder yang sesuai
2. **Chat Kiro** — minta penjelasan, soal recall, atau diskusi
3. **Catat** hasil sesi di bagian bawah file (apa yang paham, apa yang lemah)
4. **Review** di interval 1 hari → 3 hari → 7 hari (spaced repetition)
5. **Arsipkan** — pindahkan ke `_archive/` setelah materi dikuasai
