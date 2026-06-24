---
category: general
date: 2026-06-24
description: Pulihkan DOCX yang rusak menggunakan Aspose.Words di Python – kemudian
  konversi DOCX ke PDF, terapkan bayangan pada bentuk, dan simpan DOCX sebagai Markdown
  dengan persamaan LaTeX.
draft: false
keywords:
- recover corrupted docx
- convert docx to pdf
- apply shadow to shape
- save docx as markdown
- export equations to latex
language: id
og_description: Pelajari cara memulihkan DOCX yang rusak, mengonversinya ke PDF, menerapkan
  bayangan pada bentuk, dan mengekspor persamaan ke LaTeX menggunakan Aspose.Words
  untuk Python.
og_title: Pulihkan DOCX Rusak dan Konversi ke PDF – Panduan Python
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Recover corrupted DOCX using Aspose.Words in Python – then convert
    DOCX to PDF, apply shadow to shape, and save DOCX as Markdown with LaTeX equations.
  headline: Recover Corrupted DOCX and Convert to PDF with Aspose.Words (Python)
  type: TechArticle
- description: Recover corrupted DOCX using Aspose.Words in Python – then convert
    DOCX to PDF, apply shadow to shape, and save DOCX as Markdown with LaTeX equations.
  name: Recover Corrupted DOCX and Convert to PDF with Aspose.Words (Python)
  steps:
  - name: Common Pitfalls
    text: '- **Missing fonts:** If the corrupted file references a font that isn’t
      installed, Aspose substitutes a default. To keep the original look, embed fonts
      before saving (see the PDF step). - **Partial loss:** Some complex objects (e.g.,
      SmartArt) may be dropped entirely. Always verify the output visual'
  - name: Why bother with shadows?
    text: '- **Readability:** Shadows separate the shape from the page background,
      especially in dense reports. - **Aesthetic consistency:** If your brand guidelines
      call for subtle depth, this is the programmatic way to enforce it.'
  - name: Edge Cases to Watch
    text: '- **Unsupported elements:** Certain Word features (e.g., SmartArt) are
      rendered as images in Markdown. Review the output if you rely on pure text.
      - **Large equations:** Very complex formulas may exceed the LaTeX parser’s limits;
      consider simplifying them before saving.'
  type: HowTo
- questions:
  - answer: Aspose.Words attempts to salvage anything it can, but a file that’s zero‑bytes
      or missing the core XML parts will still fail. In such cases, fallback to a
      file‑upload alert for the user.
    question: Does recovery work on DOCX files that are completely unreadable?
  - answer: Absolutely. Wrap the load‑recover‑save logic in a `for` loop and adjust
      the output filenames accordingly.
    question: Can I batch‑process a folder of corrupted files?
  - answer: Omit `export_floating_shapes_as_inline_tag=True`. The default keeps shapes
      floating, but be aware that some PDF viewers may not render them exactly as
      Word does.
    question: What if I need the PDF to retain the original floating‑shape positions?
  - answer: 'The LaTeX conversion is part of the standard Aspose.Words feature set;
      no extra license is required beyond the base library. --- ## Next Steps & Related
      Topics - **Batch conversion:** Combine `os.listdir()` with the script to **convert
      docx to pdf** en masse. - **Advanced styling:** Explore `ShapeSt'
    question: Are there licensing concerns for the LaTeX export?
  type: FAQPage
tags:
- Aspose.Words
- Python
- Document Automation
title: Pulihkan DOCX Rusak dan Konversi ke PDF dengan Aspose.Words (Python)
url: /id/python/document-conversion/recover-corrupted-docx-and-convert-to-pdf-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Pulihkan DOCX Rusak dan Konversi ke PDF dengan Aspose.Words (Python)

Pernahkah Anda perlu **memulihkan DOCX yang rusak** yang tidak dapat dibuka di Word? Anda tidak sendirian—dokumen yang rusak muncul lebih sering daripada yang kita inginkan, terutama ketika berurusan dengan pipeline otomatis atau unggahan pengguna. Pada tutorial ini kami akan menunjukkan cara menyelamatkan DOCX yang rusak, lalu **mengonversi DOCX ke PDF**, **menambahkan bayangan pada shape**, **menyimpan DOCX sebagai Markdown**, dan akhirnya **mengekspor persamaan ke LaTeX**—semua dengan satu skrip Python yang rapi.

Kami akan menelusuri setiap baris kode, menjelaskan mengapa setiap opsi penting, dan menyoroti beberapa jebakan yang mungkin Anda temui. Pada akhir tutorial Anda akan memiliki potongan kode yang dapat digunakan kembali dan dapat dimasukkan ke proyek apa pun yang membutuhkan penanganan dokumen yang kuat.

> **Intip cepat:** Anda memerlukan Python 3.8+, lisensi Aspose.Words for Python (atau trial gratis), dan sebuah folder dengan `maybe_broken.docx` yang rusak serta `source.docx` yang sehat. Tidak ada dependensi lain.

## Apa yang Akan Anda Pelajari

- Cara membuka DOCX yang mungkin rusak dalam **mode pemulihan**.
- Langkah tepat untuk **mengonversi DOCX ke PDF** sambil mempertahankan shape mengambang.
- Cara **menambahkan bayangan pada shape** menggunakan API gambar Aspose.Words.
- Cara **menyimpan DOCX sebagai Markdown** dan memastikan persamaan diekspor sebagai **LaTeX**.
- Tips menangani kasus tepi seperti font yang hilang atau elemen yang tidak didukung.

---

## Prasyarat

| Persyaratan | Mengapa penting |
|-------------|----------------|
| Python 3.8+ | Aspose.Words for Python hanya mendukung 3.8 ke atas. |
| paket `aspose-words` | Perpustakaan inti yang melakukan semua pekerjaan berat. |
| Lisensi Aspose.Words yang valid (atau trial) | Tanpa lisensi perpustakaan berjalan dalam mode evaluasi, menambahkan watermark. |
| Dua file DOCX (`source.docx` dan `maybe_broken.docx`) | Satu file bersih untuk mendemonstrasikan penyimpanan normal, satu file rusak untuk menampilkan pemulihan. |

Pasang paket dengan:

```bash
pip install aspose-words
```

---

## Langkah 1: Pulihkan DOCX Rusak dengan Aspose.Words

Hal pertama yang kami lakukan adalah memuat dokumen yang dicurigai dalam **mode pemulihan**. Aspose.Words akan mencoba membangun kembali struktur internal, melewati bagian yang tidak dapat dibaca sambil mempertahankan sebanyak mungkin konten.

```python
import aspose.words as aw

# Load a healthy reference document (optional, just for demo)
doc = aw.Document("YOUR_DIRECTORY/source.docx")

# Load the potentially broken document using recovery mode
recovered_doc = aw.Document(
    "YOUR_DIRECTORY/maybe_broken.docx",
    aw.LoadOptions(recovery_mode=aw.LoadOptions.RecoveryMode.RECOVER)
)

print("Recovery completed. Pages loaded:", recovered_doc.page_count)
```

> **Mengapa menggunakan mode pemulihan?**  
> Perbaikan bawaan Word sering membuang konten secara diam‑diam. Flag `RECOVER` milik Aspose berusaha membangun kembali tabel, gambar, dan bahkan teks tersembunyi, memberi Anda objek `Document` yang dapat diproses lebih lanjut.

### Jebakan Umum

- **Font yang hilang:** Jika file rusak merujuk pada font yang tidak terpasang, Aspose akan menggantinya dengan default. Untuk mempertahankan tampilan asli, sematkan font sebelum menyimpan (lihat langkah PDF).  
- **Kehilangan parsial:** Beberapa objek kompleks (misalnya SmartArt) mungkin dihapus sepenuhnya. Selalu verifikasi output secara visual.

---

## Langkah 2: Konversi DOCX ke PDF Sambil Mempertahankan Shape Mengambang

Setelah kita memiliki objek `Document` yang bersih, mari **konversi DOCX ke PDF**. Kami juga akan mengaktifkan opsi untuk mengekspor shape mengambang sebagai tag inline, yang penting ketika Anda membutuhkan PDF yang dapat dicari atau ketika alat hilir mengharapkan grafik inline.

```python
# Configure PDF save options
pdf_options = aw.saving.PdfSaveOptions(export_floating_shapes_as_inline_tag=True)

# Optional: embed all fonts to avoid substitution in the PDF
pdf_options.embed_full_fonts = True

# Save the recovered document as PDF
recovered_doc.save("YOUR_DIRECTORY/recovered_output.pdf", pdf_options)

print("PDF saved with floating shapes as inline tags.")
```

> **Tip:** Menetapkan `embed_full_fonts` sedikit menambah beban kinerja tetapi menjamin PDF terlihat identik di mesin mana pun.

---

## Langkah 3: Tambahkan Bayangan pada Shape – Sentuhan Visual

Menambahkan isyarat visual seperti bayangan dapat membuat diagram lebih menonjol. Aspose.Words memungkinkan Anda menyisipkan shape dan menyesuaikan properti bayangannya secara programatis.

```python
# Use DocumentBuilder on the original (or recovered) document
builder = aw.DocumentBuilder(doc)

# Insert an ellipse shape of size 150x150 points
ellipse = builder.insert_shape(aw.drawing.ShapeType.ELLIPSE, 150, 150)

# Turn on the shadow and fine‑tune its appearance
ellipse.shadow_format.visible = True
ellipse.shadow_format.blur_radius = 6      # Softness of the shadow
ellipse.shadow_format.distance = 4        # How far the shadow sits from the shape
ellipse.shadow_format.angle = 30          # Direction in degrees

print("Ellipse with shadow added.")
```

### Mengapa repot dengan bayangan?

- **Keterbacaan:** Bayangan memisahkan shape dari latar belakang halaman, terutama dalam laporan yang padat.  
- **Konsistensi estetika:** Jika pedoman merek Anda mengharuskan kedalaman halus, ini adalah cara programatis untuk menegakkannya.

---

## Langkah 4: Simpan DOCX sebagai Markdown dan Ekspor Persamaan ke LaTeX

Jika Anda membutuhkan format ringan yang dapat dikontrol versi, **simpan DOCX sebagai Markdown**. Aspose.Words juga dapat mengekspor persamaan Office Math apa pun dalam dokumen sebagai **LaTeX**, yang sempurna untuk publikasi ilmiah.

```python
# Prepare Markdown save options with LaTeX export for equations
markdown_options = aw.saving.MarkdownSaveOptions(
    office_math_export_mode=aw.saving.MarkdownOfficeMathExportMode.LATEX
)

# Save the document (including the newly added ellipse) as .md
doc.save("YOUR_DIRECTORY/out.md", markdown_options)

print("Document saved as Markdown with LaTeX equations.")
```

File `out.md` yang dihasilkan akan berisi sintaks Markdown biasa untuk paragraf dan gambar, sementara objek `Equation` akan menjadi potongan LaTeX `$...$`.

### Kasus Tepi yang Perlu Diwaspadai

- **Elemen yang tidak didukung:** Fitur Word tertentu (misalnya SmartArt) dirender sebagai gambar dalam Markdown. Tinjau output jika Anda mengandalkan teks murni.  
- **Persamaan besar:** Formula yang sangat kompleks mungkin melampaui batas parser LaTeX; pertimbangkan menyederhanakannya sebelum menyimpan.

---

## Contoh Skrip Lengkap

Berikut adalah skrip lengkap yang menggabungkan semua langkah. Salin‑tempel ke file bernama `process_docx.py`, sesuaikan placeholder `YOUR_DIRECTORY`, dan jalankan.

```python
import aspose.words as aw

# ------------------------------------------------------------------
# Step 1 – Load documents (healthy + potentially corrupted)
# ------------------------------------------------------------------
doc = aw.Document("YOUR_DIRECTORY/source.docx")
recovered_doc = aw.Document(
    "YOUR_DIRECTORY/maybe_broken.docx",
    aw.LoadOptions(recovery_mode=aw.LoadOptions.RecoveryMode.RECOVER)
)

# ------------------------------------------------------------------
# Step 2 – Convert the recovered DOCX to PDF (preserve floating shapes)
# ------------------------------------------------------------------
pdf_options = aw.saving.PdfSaveOptions(export_floating_shapes_as_inline_tag=True)
pdf_options.embed_full_fonts = True
recovered_doc.save("YOUR_DIRECTORY/recovered_output.pdf", pdf_options)

# ------------------------------------------------------------------
# Step 3 – Insert an ellipse and apply a shadow
# ------------------------------------------------------------------
builder = aw.DocumentBuilder(doc)
ellipse = builder.insert_shape(aw.drawing.ShapeType.ELLIPSE, 150, 150)
ellipse.shadow_format.visible = True
ellipse.shadow_format.blur_radius = 6
ellipse.shadow_format.distance = 4
ellipse.shadow_format.angle = 30

# ------------------------------------------------------------------
# Step 4 – Save the original document as Markdown with LaTeX equations
# ------------------------------------------------------------------
markdown_options = aw.saving.MarkdownSaveOptions(
    office_math_export_mode=aw.saving.MarkdownOfficeMathExportMode.LATEX
)
doc.save("YOUR_DIRECTORY/out.md", markdown_options)

print("All operations completed successfully.")
```

**Output yang diharapkan**

- `recovered_output.pdf` – PDF bersih di mana shape mengambang menjadi tag inline.  
- `out.md` – file Markdown dengan teks biasa plus blok LaTeX `$...$` untuk setiap persamaan.  
- Log konsol yang mengonfirmasi setiap langkah.

---

## Pemeriksaan Visual – Bayangan Shape (Gambar)

<img src="shadow_example.png" alt="recover corrupted docx example – ellipse with shadow" width="400"/>

*Gambar menunjukkan elips yang kami tambahkan; perhatikan bayangan halus yang membuatnya menonjol.*

---

## Pertanyaan yang Sering Diajukan

**T: Apakah pemulihan bekerja pada file DOCX yang benar‑benar tidak dapat dibaca?**  
J: Aspose.Words berusaha menyelamatkan apa saja yang bisa, tetapi file yang berukuran nol byte atau kehilangan bagian XML inti tetap akan gagal. Dalam kasus seperti itu, alihkan ke peringatan unggahan file bagi pengguna.

**T: Bisakah saya memproses batch folder berisi file rusak?**  
J: Tentu. Bungkus logika load‑recover‑save dalam loop `for` dan sesuaikan nama file output sesuai kebutuhan.

**T: Bagaimana jika saya ingin PDF mempertahankan posisi shape mengambang asli?**  
J: Hilangkan `export_floating_shapes_as_inline_tag=True`. Defaultnya mempertahankan shape mengambang, tetapi sadar bahwa beberapa penampil PDF mungkin tidak merendernya persis seperti di Word.

**T: Apakah ada masalah lisensi untuk ekspor LaTeX?**  
J: Konversi LaTeX termasuk dalam set fitur standar Aspose.Words; tidak memerlukan lisensi tambahan di luar perpustakaan dasar.

---

## Langkah Selanjutnya & Topik Terkait

- **Konversi batch:** Gabungkan `os.listdir()` dengan skrip untuk **mengonversi docx ke pdf** secara massal.  
- **Styling lanjutan:** Jelajahi `ShapeStyle` untuk menambahkan gradien atau efek 3‑D sebelum mengekspor.  
- **Integrasi cloud:** Deploy logika ini sebagai Azure Function atau AWS Lambda untuk perbaikan dokumen on‑demand.  
- **Output alternatif:** Aspose.Words juga mendukung HTML, EPUB, dan bahkan format gambar—bagus untuk pipeline pratinjau web.

---

## Kesimpulan

Kami telah menelusuri alur kerja lengkap end‑to‑end yang **memulihkan DOCX rusak**, **mengonversi DOCX ke PDF**, **menambahkan bayangan pada shape**, **menyimpan DOCX sebagai Markdown**, dan **mengekspor persamaan ke LaTeX**—semua dalam satu skrip Python yang terorganisir.

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Recover Corrupted DOCX & Convert Word to Markdown](/words/english/python-net/document-conversion/recover-corrupted-docx-convert-word-to-markdown/)
- [Recover Corrupted DOCX – Open & Load Word Document](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)
- [How to Export LaTeX from Word: Convert DOCX to Markdown & Save as PDF](/words/english/java/document-conversion-and-export/how-to-export-latex-from-word-convert-docx-to-markdown-save/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}