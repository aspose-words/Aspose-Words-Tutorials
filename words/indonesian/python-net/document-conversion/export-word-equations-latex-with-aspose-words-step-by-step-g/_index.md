---
category: general
date: 2026-08-07
description: Ekspor persamaan LaTeX Word ke file LaTeX menggunakan Aspose.Words. Pelajari
  cara mengonversi LaTeX matematika Word dan mengekstrak persamaan dari Word dengan
  cepat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- export word equations latex
- convert word math latex
- extract latex from word
- extract equations from word
language: id
lastmod: 2026-08-07
og_description: Ekspor persamaan Word ke LaTeX dengan Aspose.Words. Panduan ini menunjukkan
  cara mengonversi LaTeX matematika Word dan mengekstrak persamaan dari Word dalam
  satu skrip.
og_image_alt: Screenshot of a Python script exporting Word equations to LaTeX
og_title: Ekspor persamaan Word ke LaTeX – tutorial lengkap Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Export word equations latex to LaTeX files using Aspose.Words. Learn
    how to convert word math latex and extract equations from word quickly.
  headline: Export word equations latex with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Export word equations latex to LaTeX files using Aspose.Words. Learn
    how to convert word math latex and extract equations from word quickly.
  name: Export word equations latex with Aspose.Words – step‑by‑step guide
  steps:
  - name: Expected output
    text: 'If `equations.docx` contains two equations, the resulting `out.txt` might
      look like:'
  - name: Verify the file
    text: Open `out.txt` in any text editor and confirm that every equation is represented
      by LaTeX. If an equation is missing, it is likely not an Office Math object
      (e.g., an image of a formula). In that case, you must replace the image manually
      or use OCR tools.
  - name: 'Edge case: Documents without Office Math'
    text: 'If the source document contains no Office Math objects, the output file
      will be plain text without LaTeX blocks. You can check the presence of equations
      beforehand:'
  - name: 'Edge case: Large documents'
    text: 'For very large `.docx` files, consider streaming the output to avoid high
      memory consumption:'
  - name: Next steps
    text: '* Explore `aw.saving.TxtSaveOptions` properties such as `encoding` to control
      character sets. * Combine the exported LaTeX with a template engine (e.g., Jinja2)
      to generate full LaTeX reports. * If you need inline math rather than display
      math, set `txt_save_options.math_output_mode = aw.saving.Math'
  type: HowTo
tags:
- Aspose.Words
- Python
- LaTeX
- Word equations
title: Ekspor persamaan Word ke LaTeX dengan Aspose.Words – panduan langkah demi langkah
url: /id/python/document-conversion/export-word-equations-latex-with-aspose-words-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Export word equations latex dengan Aspose.Words – panduan langkah‑demi‑langkah

Jika Anda perlu **export word equations latex**, tutorial ini menunjukkan secara tepat cara melakukannya. Anda juga akan belajar cara **convert word math latex** dan mengekstrak representasi LaTeX yang mendasari setiap persamaan dalam file Word.

Panduan ini mencakup semua yang Anda perlukan untuk menjalankan skrip Python yang membaca dokumen *.docx*, mengonfigurasi opsi penyimpanan yang tepat, dan menulis file *.txt* teks biasa yang berisi kode LaTeX. Tidak ada alat eksternal yang diperlukan selain Aspose.Words untuk Python.

## Prasyarat

* Python 3.8 atau yang lebih baru terpasang.
* Lisensi aktif Aspose.Words for Python via .NET (atau kunci evaluasi gratis).
* Dokumen Word (`.docx`) yang berisi persamaan Office Math yang ingin Anda ekstrak.
* Familiaritas dasar dengan sistem impor Python.

Jika ada item yang belum ada, instal sekarang; langkah-langkah di bawah mengasumsikan semuanya sudah tersedia.

## Langkah 1: Instal Aspose.Words untuk Python

Buka terminal dan jalankan:

```bash
pip install aspose-words
```

Paket `aspose-words` menyediakan namespace `aw` yang digunakan dalam contoh kode. Menginstal paket ini menyelesaikan `ImportError` yang muncul ketika skrip mencoba mengimpor `aw`.

## Langkah 2: Muat dokumen Word yang berisi persamaan

```python
import aspose.words as aw

# Load the source document. Replace the path with the location of your .docx file.
document = aw.Document("YOUR_DIRECTORY/equations.docx")
```

Kelas `aw.Document` mengurai seluruh file Word, termasuk teks, gambar, dan objek Office Math. Memuat dokumen adalah langkah pertama menuju **extract latex from word** karena perpustakaan membuat representasi dalam memori untuk setiap persamaan.

## Langkah 3: Konfigurasikan opsi penyimpanan TXT untuk mengekspor Office Math sebagai LaTeX

`TxtSaveOptions` memberi tahu Aspose.Words cara menulis file output. Menetapkan `office_math_export_mode` ke `LATEX` menginstruksikan perpustakaan untuk mengganti setiap objek Office Math dengan padanan LaTeX-nya. Ini adalah mekanisme inti yang memungkinkan Anda **export word equations latex** dalam satu panggilan.

```python
txt_save_options = aw.saving.TxtSaveOptions()
txt_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
```

## Langkah 4: Simpan dokumen sebagai file teks biasa

Ketika `document.save` dijalankan dengan `txt_save_options` yang telah dikonfigurasi, Aspose.Words menulis file `.txt` di mana setiap persamaan muncul sebagai kode LaTeX yang dikelilingi oleh teks paragraf normal. Hasilnya adalah sumber LaTeX yang bersih dan dapat dicari yang dapat Anda masukkan ke dalam kompiler LaTeX apa pun.

```python
output_path = "YOUR_DIRECTORY/out.txt"
document.save(output_path, txt_save_options)
print(f"LaTeX export completed. File saved to {output_path}")
```

### Output yang diharapkan

Jika `equations.docx` berisi dua persamaan, `out.txt` yang dihasilkan mungkin terlihat seperti:

```
This is a paragraph before the first equation.

\[
\frac{a}{b} = c
\]

Another paragraph.

\[
E = mc^2
\]

End of document.
```

Perhatikan bahwa blok LaTeX dibungkus dengan `\[` dan `\]`, yang merupakan pembatas tampilan‑math default yang digunakan oleh Aspose.Words.

## Langkah 5: Verifikasi ekspor dan tangani kasus tepi

### Verifikasi file

Buka `out.txt` di editor teks apa pun dan pastikan setiap persamaan direpresentasikan dalam LaTeX. Jika ada persamaan yang hilang, kemungkinan itu bukan objek Office Math (mis., gambar formula). Dalam kasus tersebut, Anda harus mengganti gambar secara manual atau menggunakan alat OCR.

### Kasus tepi: Dokumen tanpa Office Math

Jika dokumen sumber tidak berisi objek Office Math, file output akan menjadi teks biasa tanpa blok LaTeX. Anda dapat memeriksa keberadaan persamaan sebelumnya:

```python
has_math = any(isinstance(node, aw.Math.OfficeMath) for node in document.get_child_nodes(aw.NodeType.OFFICE_MATH, True))
if not has_math:
    print("No Office Math equations found; nothing to export.")
```

### Kasus tepi: Dokumen besar

Untuk file `.docx` yang sangat besar, pertimbangkan untuk streaming output guna menghindari konsumsi memori yang tinggi:

```python
with open(output_path, "w", encoding="utf-8") as out_file:
    document.save(out_file, txt_save_options)
```

Streaming menulis setiap halaman secara berurutan, menjaga jejak memori tetap rendah sambil tetap **export word equations latex** dengan benar.

## Langkah 6: Otomatiskan proses untuk banyak file (opsional)

Jika Anda perlu **extract equations from word** secara massal, bungkus logika dalam sebuah fungsi dan iterasi melalui folder:

```python
import os

def export_latex_from_docx(src_path, dst_path):
    doc = aw.Document(src_path)
    options = aw.saving.TxtSaveOptions()
    options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
    doc.save(dst_path, options)

source_dir = "YOUR_DIRECTORY/source_docs"
target_dir = "YOUR_DIRECTORY/latex_exports"

os.makedirs(target_dir, exist_ok=True)

for filename in os.listdir(source_dir):
    if filename.lower().endswith(".docx"):
        src = os.path.join(source_dir, filename)
        dst = os.path.join(target_dir, os.path.splitext(filename)[0] + ".txt")
        export_latex_from_docx(src, dst)
        print(f"Exported {filename} → {dst}")
```

Skrip pembantu ini **convert word math latex** untuk setiap dokumen dalam folder, membuat alur kerja dapat diskalakan untuk proyek besar.

## Kesimpulan

Anda kini memiliki solusi lengkap yang dapat dijalankan untuk **export word equations latex** menggunakan Aspose.Words untuk Python. Skrip ini memuat file Word, mengonfigurasi `TxtSaveOptions` untuk menghasilkan LaTeX, dan menulis hasilnya ke file teks biasa. Dengan potongan kode pemrosesan massal opsional, Anda juga dapat **extract latex from word** dan **extract equations from word** pada banyak dokumen dengan usaha minimal.

### Langkah selanjutnya

* Jelajahi properti `aw.saving.TxtSaveOptions` seperti `encoding` untuk mengontrol set karakter.
* Gabungkan LaTeX yang diekspor dengan mesin templat (mis., Jinja2) untuk menghasilkan laporan LaTeX lengkap.
* Jika Anda memerlukan matematika inline daripada display math, setel `txt_save_options.math_output_mode = aw.saving.MathOutputMode.INLINE`.

Silakan bereksperimen dengan pengaturan dan mengintegrasikan skrip ke dalam pipeline pembuatan dokumen Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Cara Mengekspor LaTeX dari Word – Panduan Langkah‑per‑Langkah](/words/english/net/basic-conversions/how-to-export-latex-from-word-step-by-step-guide/)
- [Cara Mengekspor LaTeX dari Word: Mengonversi DOCX ke Markdown dengan Aspose](/words/english/net/programming-with-markdownsaveoptions/how-to-export-latex-from-word-convert-docx-to-markdown-with/)
- [Simpan docx sebagai txt – Ekspor Word Math ke LaTeX dengan C#](/words/english/net/programming-with-officemath/save-docx-as-txt-export-word-math-to-latex-with-c/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}