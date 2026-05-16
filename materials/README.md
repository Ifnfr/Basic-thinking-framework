# materials/

Folder ini berfungsi sebagai **tempat penampungan bahan belajar** yang akan dibahas bersama AI (Kiro / Claude / model lain) dalam sesi *active recall* dan diskusi.

Karena Kiro tidak bisa membaca file lokal yang diupload langsung di chat (terutama PDF/DOCX), workflow-nya menjadi:

1. Upload file bahan ke folder ini (lewat GitHub web atau git push)
2. Sebut nama file-nya di chat Kiro
3. Kiro akan membaca file dari repository dan membahasnya

---

## Struktur folder

```
materials/
├── README.md           ← file ini
├── linguistik/         ← contoh subfolder per topik
├── _archive/           ← bahan yang sudah selesai dibahas
└── <topik-lain>/       ← buat sesuai kebutuhan
```

Konvensi:
- **Satu subfolder per mata pelajaran / topik besar.** Contoh: `linguistik/`, `sejarah/`, `biologi/`.
- **Pindahkan file ke `_archive/`** setelah selesai dipelajari, supaya folder utama tetap fokus pada bahan aktif.
- **Penamaan file:** gunakan format `YYYY-MM-DD_topik-spesifik.md`, contoh: `2026-05-16_kelas-kata-utama.md`. Ini memudahkan pelacakan kronologis dan mendukung *spaced repetition*.

---

## Format file yang didukung

| Format | Bisa dibaca AI? | Catatan |
|---|---|---|
| `.md`, `.txt` | ✓ | **Format utama yang direkomendasikan** |
| `.json`, `.yaml`, `.csv` | ✓ | Cocok untuk data terstruktur / flashcard |
| `.py`, `.js`, kode lain | ✓ | Untuk bahan pemrograman |
| `.png`, `.jpg`, `.jpeg`, `.webp` | ✓ | Foto papan tulis, slide, catatan tangan |
| `.pdf` | ✗ | **Harus dikonversi ke `.md` atau `.txt` lebih dulu** |
| `.docx`, `.pptx` | ✗ | Harus dikonversi |

> Tips: kalau bahan asalnya PDF/PPT, copy-paste isinya ke file `.md` baru. Atau minta AI bantu merangkumnya saat upload pertama.

---

## Template file bahan

Untuk konsistensi, gunakan template di `materials/_template.md` saat menambah bahan baru.

Struktur minimum yang disarankan:

```markdown
# <Judul Bahan>

**Sumber:** <buku / slide kuliah / video / dst.>
**Tanggal upload:** YYYY-MM-DD
**Status:** belajar / review / arsip

## Ringkasan
<Satu paragraf inti dari bahan ini>

## Konsep kunci
- <konsep 1>
- <konsep 2>

## Isi bahan
<konten lengkap di sini>

## Pertanyaan terbuka
- <hal yang belum dipahami>
```

---

## Cara memanggil bahan di chat Kiro

Pilih salah satu format ini saat memulai sesi:

- *"Bahas bahan di `materials/linguistik/2026-05-16_kelas-kata-utama.md`."*
- *"Buatkan soal active recall dari `materials/biologi/sel.md`."*
- *"Bandingkan isi `materials/linguistik/<file-A>.md` dengan `<file-B>.md`."*

Kiro akan langsung membaca file tersebut dari repository.

---

## Workflow yang disarankan

1. **Sebelum sesi belajar:** upload bahan ke folder yang sesuai
2. **Selama sesi:** minta penjelasan, soal recall, atau diskusi
3. **Setelah sesi:** tambahkan catatan reflektif di bagian bawah file (apa yang sudah paham, apa yang masih lemah)
4. **Review berkala:** kembali ke file yang sama dalam interval 1 hari, 3 hari, 7 hari (spaced repetition)
5. **Arsipkan:** pindahkan ke `_archive/` saat materi sudah dikuasai
