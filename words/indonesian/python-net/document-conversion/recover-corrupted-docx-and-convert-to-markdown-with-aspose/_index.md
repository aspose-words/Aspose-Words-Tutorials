---
category: general
date: 2026-08-04
description: Pulihkan file docx yang rusak menggunakan mode pemulihan Aspose.Words
  dan konversi docx ke markdown, mengekspor persamaan sebagai LaTeX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- recover corrupted docx
- convert docx to markdown
- how to use recovery mode
- export equations latex
language: id
lastmod: 2026-08-04
og_description: Pulihkan file docx yang rusak dengan mode pemulihan Aspose.Words,
  lalu konversi docx ke markdown sambil mengekspor persamaan sebagai LaTeX. Ikuti
  panduan langkah demi langkah ini untuk juga membuat output PDF dan TXT.
og_image_alt: Screenshot of Aspose.Words Python code converting a corrupted docx to
  markdown with LaTeX equations
og_title: Pulihkan docx yang rusak dan konversi ke markdown – Panduan Aspose
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Recover corrupted docx files using Aspose.Words recovery mode and convert
    docx to markdown, exporting equations as LaTeX.
  headline: Recover corrupted docx and convert to markdown with Aspose
  type: TechArticle
- description: Recover corrupted docx files using Aspose.Words recovery mode and convert
    docx to markdown, exporting equations as LaTeX.
  name: Recover corrupted docx and convert to markdown with Aspose
  steps:
  - name: Export floating shapes as inline tags
    text: Floating images or text boxes can cause layout issues when converting to
      PDF. Setting `export_floating_shapes_as_inline_tag` forces Aspose.Words to treat
      those shapes as regular inline elements, preserving the visual flow.
  - name: Adjust the shadow of the first shape
    text: You might want to enhance the appearance of a specific shape before saving
      the final PDF. The code below accesses the first `Shape` node, enables its shadow,
      and tweaks visual parameters.
  - name: Expected output
    text: '| File | Description | |------|-------------| | `output.md` | Markdown
      version of the original DOCX. All equations appear as LaTeX (`$...$` or `$$...$$`).
      | | `output.txt` | Plain‑text dump'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document conversion
title: Pulihkan docx yang rusak dan konversi ke markdown dengan Aspose
url: /id/python/document-conversion/recover-corrupted-docx-and-convert-to-markdown-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Pulihkan docx yang rusak dan konversi ke markdown dengan Aspose

Jika Anda perlu **memulihkan docx yang rusak**, Aspose.Words menyediakan mode pemulihan bawaan yang dapat secara otomatis memperbaiki dokumen Word yang rusak. Setelah file dipulihkan, Anda dapat **mengonversi docx ke markdown**, dan bahkan **mengekspor persamaan latex** untuk penggunaan yang mulus dalam dokumen ilmiah. Tutorial ini menunjukkan secara tepat cara melakukannya di Python, serta beberapa opsi tambahan untuk output PDF dan teks biasa.

Anda akan belajar bagaimana:

* Memuat DOCX yang mungkin rusak menggunakan mode pemulihan.  
* Menyimpan dokumen yang dipulihkan sebagai Markdown dengan persamaan berformat LaTeX.  
* Menghasilkan versi teks biasa (TXT) yang juga berisi persamaan LaTeX.  
* Mengekspor ke PDF sambil menandai bentuk mengambang sebagai elemen inline.  
* Menyesuaikan bayangan sebuah bentuk dan menghasilkan PDF akhir.

Tidak diperlukan alat eksternal—hanya pustaka Aspose.Words untuk Python yang gratis.

## Prasyarat

| Persyaratan | Mengapa penting |
|-------------|----------------|
| Python 3.8+ | Diperlukan oleh Aspose.Words for Python |
| `aspose-words` package (`pip install aspose-words`) | Menyediakan namespace `aw` yang digunakan dalam kode |
| File DOCX yang mungkin rusak (misalnya `corrupted.docx`) | Menunjukkan alur kerja pemulihan |
| Izin menulis ke direktori output | Script menulis beberapa file (`.md`, `.txt`, `.pdf`) |

Pastikan lisensi Aspose.Words (versi percobaan gratis atau berbayar) telah dikonfigurasi dengan benar jika Anda melampaui batas evaluasi.

## Pulihkan docx yang rusak menggunakan Aspose.Words

Langkah pertama adalah memberi tahu Aspose.Words untuk memperlakukan file input sebagai kemungkinan rusak. Ini dilakukan dengan `LoadOptions.recovery_mode`.

```python
import aspose.words as aw

# Step 1: Load a possibly corrupted document using recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER   # Enables automatic recovery of damaged files
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)
```

**Mengapa ini berhasil:**  
`RecoveryMode.RECOVER` memaksa pemuat untuk mengabaikan kesalahan struktural dan berusaha membangun kembali pohon dokumen. Jika file hanya rusak sebagian, sebagian besar konten—termasuk teks, gambar, dan persamaan—akan dipulihkan.

**Tip:** Jika Anda hanya ingin memvalidasi dokumen tanpa memperbaikinya, gunakan `RecoveryMode.NO_RECOVERY`. Untuk pemulihan penuh, pertahankan pengaturan seperti yang ditunjukkan.

## Konversi docx ke markdown dengan persamaan LaTeX

Setelah dokumen berada di memori, Anda dapat menyimpannya sebagai Markdown. Menetapkan `office_math_export_mode` ke `LATEX` memberi tahu Aspose.Words untuk merender setiap persamaan Word sebagai string LaTeX.

```python
# Step 2: Save the document as Markdown while exporting equations in LaTeX format
markdown_save_options = aw.saving.MarkdownSaveOptions()
markdown_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", markdown_save_options)
```

File `output.md` yang dihasilkan akan terlihat seperti file Markdown biasa, tetapi setiap persamaan muncul sebagai kode LaTeX `$...$` (inline) atau `$$...$$` (display). Ini penting untuk alat downstream seperti Pandoc atau notebook Jupyter yang memahami sintaks LaTeX.

## Cara menggunakan mode pemulihan untuk file yang rusak

Mode pemulihan dapat digunakan kembali untuk operasi pemuatan apa pun. Di bawah ini adalah pola ringkas yang dapat Anda salin ke skrip lain:

```python
def load_with_recovery(path: str) -> aw.Document:
    opts = aw.loading.LoadOptions()
    opts.recovery_mode = aw.loading.RecoveryMode.RECOVER
    return aw.Document(path, opts)
```

Memanggil `load_with_recovery("myfile.docx")` mengembalikan objek `Document` yang telah Aspose.Words coba perbaiki. Fungsi ini menggambarkan **cara menggunakan mode pemulihan** secara aman di seluruh proyek.

## Ekspor persamaan latex saat menyimpan ke markdown dan txt

Jika Anda juga memerlukan versi teks biasa, flag `office_math_export_mode` yang sama berfungsi dengan `TxtSaveOptions`.

```python
# Step 3: Save the same document as plain‑text (TXT) with LaTeX equations
txt_save_options = aw.saving.TxtSaveOptions()
txt_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_save_options)
```

File `.txt` berisi teks mentah dari dokumen Word, dan setiap persamaan direpresentasikan sebagai kode LaTeX. Format ini berguna untuk pengindeksan atau memasukkan konten ke mesin pencari yang memahami LaTeX.

## Opsi tambahan: PDF dengan bentuk inline dan bayangan bentuk

### Ekspor bentuk mengambang sebagai tag inline

Gambar atau kotak teks yang mengambang dapat menyebabkan masalah tata letak saat mengonversi ke PDF. Menetapkan `export_floating_shapes_as_inline_tag` memaksa Aspose.Words memperlakukan bentuk-bentuk tersebut sebagai elemen inline biasa, menjaga alur visual.

```python
# Step 4: Export the document to PDF and tag floating shapes as inline elements
pdf_save_options = aw.saving.PdfSaveOptions()
pdf_save_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_save_options)
```

### Sesuaikan bayangan bentuk pertama

Anda mungkin ingin meningkatkan tampilan bentuk tertentu sebelum menyimpan PDF akhir. Kode di bawah mengakses node `Shape` pertama, mengaktifkan bayangannya, dan menyesuaikan parameter visual.

```python
# Step 5: Adjust the shadow of the first shape and save the result
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
shape_shadow = first_shape.shadow_format
shape_shadow.visible = True
shape_shadow.blur = 5.0          # Controls shadow softness
shape_shadow.distance = 3.0      # Distance from the shape
shape_shadow.angle = 45          # Direction of the light source
shape_shadow.color = aw.Color.black

doc.save("YOUR_DIRECTORY/shadowed.pdf")
```

**Hasil:** `shadowed.pdf` terlihat identik dengan `output.pdf` tetapi bentuk pertama kini memancarkan bayangan hitam halus, yang dapat meningkatkan keterbacaan dalam presentasi.

## Skrip lengkap yang dapat dijalankan

Berikut adalah skrip lengkap yang menggabungkan semua langkah. Salin ke file bernama `recover_and_convert.py`, ganti `YOUR_DIRECTORY` dengan jalur yang sebenarnya, dan jalankan `python recover_and_convert.py`.

```python
import aspose.words as aw

# -------------------------------------------------
# 1. Load the possibly corrupted DOCX using recovery mode
# -------------------------------------------------
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)

# -------------------------------------------------
# 2. Save as Markdown with LaTeX equations
# -------------------------------------------------
markdown_save_options = aw.saving.MarkdownSaveOptions()
markdown_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", markdown_save_options)

# -------------------------------------------------
# 3. Save as plain‑text (TXT) with LaTeX equations
# -------------------------------------------------
txt_save_options = aw.saving.TxtSaveOptions()
txt_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_save_options)

# -------------------------------------------------
# 4. Export to PDF, converting floating shapes to inline
# -------------------------------------------------
pdf_save_options = aw.saving.PdfSaveOptions()
pdf_save_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_save_options)

# -------------------------------------------------
# 5. Add a shadow to the first shape and save a new PDF
# -------------------------------------------------
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
shape_shadow = first_shape.shadow_format
shape_shadow.visible = True
shape_shadow.blur = 5.0
shape_shadow.distance = 3.0
shape_shadow.angle = 45
shape_shadow.color = aw.Color.black

doc.save("YOUR_DIRECTORY/shadowed.pdf")
```

### Output yang diharapkan

| File | Deskripsi |
|------|-----------|
| `output.md` | Versi Markdown dari DOCX asli. Semua persamaan muncul sebagai LaTeX (`$...$` atau `$$...$$`). |
| `output.txt` | Dump teks biasa |

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Cara Menggunakan Markdown: Konversi DOCX ke Markdown dengan Persamaan LaTeX](/words/english/net/programming-with-markdownsaveoptions/how-to-use-markdown-convert-docx-to-markdown-with-latex-equa/)
- [cara memulihkan docx dengan Aspose.Words – langkah demi langkah](/words/english/net/programming-with-loadoptions/how-to-recover-docx-with-aspose-words-step-by-step/)
- [Pulihkan DOCX Rusak & Konversi Word ke Markdown](/words/english/python-net/document-conversion/recover-corrupted-docx-convert-word-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}