---
category: general
date: 2026-10-16
description: Cara mengekspor LaTeX dari dokumen Word menggunakan Aspose.Words. Pelajari
  cara mengonversi DOCX ke LaTeX, menyimpan Word sebagai TXT, dan mengekstrak persamaan
  dalam satu skrip.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to export latex
- convert docx to latex
- export word equations latex
- save word as txt
- extract equations latex
language: id
lastmod: 2026-10-16
og_description: Cara mengekspor LaTeX dari dokumen Word dengan Aspose.Words. Panduan
  ini menunjukkan cara mengonversi DOCX ke LaTeX, menyimpan Word sebagai TXT, dan
  mengekstrak persamaan dengan cepat.
og_image_alt: How to export LaTeX from Word using Aspose.Words
og_title: Cara mengekspor LaTeX dari dokumen Word – panduan langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: How to export LaTeX from a Word document using Aspose.Words. Learn
    to convert DOCX to LaTeX, save Word as TXT, and extract equations in a single
    script.
  headline: How to export LaTeX from Word documents using Aspose.Words
  type: TechArticle
- description: How to export LaTeX from a Word document using Aspose.Words. Learn
    to convert DOCX to LaTeX, save Word as TXT, and extract equations in a single
    script.
  name: How to export LaTeX from Word documents using Aspose.Words
  steps:
  - name: Load the Word document containing equations
    text: '```python import aspose.words as aw'
  - name: Create TXT save options
    text: '```python txt_opts = aw.saving.TxtSaveOptions() ```'
  - name: Set the export mode for Office Math objects to LaTeX
    text: '```python # Export all Office Math objects as LaTeX markup txt_opts.office_math_export_mode
      = aw.saving.OfficeMathExportMode.LATEX ```'
  - name: Save the document as a plain‑text file using the configured options
    text: '```python # The resulting file will contain regular text plus LaTeX for
      each equation doc.save("YOUR_DIRECTORY/out.txt", txt_opts) ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- LaTeX
- DOCX conversion
- Equation extraction
title: Cara mengekspor LaTeX dari dokumen Word menggunakan Aspose.Words
url: /id/python/document-conversion/how-to-export-latex-from-word-documents-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengekspor LaTeX dari dokumen Word menggunakan Aspose.Words

Mengekspor LaTeX dari dokumen Word adalah kebutuhan umum ketika Anda ingin menggunakan kembali konten matematika dalam makalah ilmiah. Jika Anda perlu mengonversi DOCX ke LaTeX sambil mempertahankan objek Office Math, tutorial ini akan memandu Anda melalui langkah‑langkah tepat menggunakan Aspose.Words untuk Python.

Anda akan melihat skrip lengkap yang dapat dijalankan yang memuat file *.docx*, mengonfigurasi opsi penyimpanan, dan menulis file teks biasa yang berisi markup LaTeX untuk setiap persamaan. Panduan ini juga menjelaskan mengapa setiap pengaturan penting, cara menangani kasus tepi, dan apa yang diharapkan dalam output.

![Cara mengekspor LaTeX dari Word menggunakan Aspose.Words](images/export-latex.png)

## Prasyarat

* Python 3.8 atau lebih baru terpasang.
* Lisensi aktif untuk **Aspose.Words for Python via .NET** (versi percobaan gratis dapat digunakan untuk pengujian).
* Paket `aspose-words` terpasang:

```bash
pip install aspose-words
```

Tidak diperlukan pustaka pihak ketiga tambahan; Aspose.Words menangani konversi secara internal.

## Cara mengekspor LaTeX dengan Aspose.Words

Inti solusi terdiri dari empat pernyataan singkat. Setiap pernyataan sesuai dengan langkah logis dalam alur konversi.

### Langkah 1: Muat dokumen Word yang berisi persamaan

```python
import aspose.words as aw

# Replace the path with the location of your source DOCX file
doc = aw.Document("YOUR_DIRECTORY/equations.docx")
```

`aw.Document` mem-parsing seluruh paket Word, termasuk objek Office Math. Memuat dokumen terlebih dahulu memastikan setiap persamaan tersedia untuk diekspor kemudian.

### Langkah 2: Buat opsi penyimpanan TXT

```python
txt_opts = aw.saving.TxtSaveOptions()
```

`TxtSaveOptions` memberi tahu Aspose.Words untuk menulis output teks biasa. Secara default mesin akan menghapus format, tetapi nanti kita akan mengaktifkan ekspor LaTeX untuk persamaan.

### Langkah 3: Atur mode ekspor untuk objek Office Math menjadi LaTeX

```python
# Export all Office Math objects as LaTeX markup
txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
```

Properti `office_math_export_mode` mengontrol cara persamaan dirender. Mengaturnya ke `LATEX` mengonversi setiap elemen MathML menjadi padanan LaTeX‑nya, yang merupakan apa yang Anda butuhkan untuk **export word equations latex**.

### Langkah 4: Simpan dokumen sebagai file teks biasa menggunakan opsi yang telah dikonfigurasi

```python
# The resulting file will contain regular text plus LaTeX for each equation
doc.save("YOUR_DIRECTORY/out.txt", txt_opts)
```

Pemanggilan `save` menulis file `.txt` yang mencampur paragraf normal dengan fragmen LaTeX. Ini memenuhi persyaratan **save word as txt** sambil tetap menghasilkan markup persamaan berkualitas tinggi.

## Mengonversi DOCX ke LaTeX dengan kode minimal

Menggabungkan empat langkah menghasilkan skrip ringkas yang **convert docx to latex** dalam hanya beberapa baris:

```python
import aspose.words as aw

def export_docx_to_latex(source_path: str, target_path: str) -> None:
    """
    Loads a DOCX file, exports all Office Math objects as LaTeX,
    and writes the result to a plain‑text file.
    """
    doc = aw.Document(source_path)                     # Load the source
    txt_opts = aw.saving.TxtSaveOptions()              # Prepare TXT options
    txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
    doc.save(target_path, txt_opts)                    # Write the output

# Example usage
export_docx_to_latex(
    "YOUR_DIRECTORY/equations.docx",
    "YOUR_DIRECTORY/out.txt"
)
```

Menjalankan skrip menghasilkan `out.txt`. Contoh potongan tipikal terlihat seperti ini:

```
This is a paragraph introducing the equation.

\[
E = mc^{2}
\]

Another paragraph follows the displayed formula.
```

Fragmen LaTeX `\[` … `\]` dihasilkan secara otomatis untuk setiap objek Office Math, sehingga file siap disertakan dalam dokumen LaTeX tanpa pemrosesan lebih lanjut.

## Mengekspor persamaan Word LaTeX – menangani jebakan umum

Meskipun alur dasar berfungsi untuk kebanyakan dokumen, Anda mungkin menemukan situasi berikut:

| Situasi | Mengapa penting | Perbaikan yang disarankan |
|-----------|----------------|-----------------|
| **Persamaan di dalam tabel** | Sel tabel diperlakukan sebagai paragraf terpisah; pengekspor tetap berfungsi, tetapi spasi dapat berbeda. | Setelah ekspor, verifikasi lingkungan `\begin{tabular}` di sekitarnya secara manual atau gunakan skrip pasca‑pemrosesan untuk membungkus fragmen LaTeX. |
| **Arah bahasa campuran (RTL/LTR)** | Aspose.Words menghormati arah asli, yang dapat memengaruhi cara LaTeX merender. | Tambahkan `\usepackage{bidi}` dalam preamble LaTeX Anda jika memerlukan dukungan kanan‑ke‑kiri. |
| **Dokumen besar** | Menyimpan sebagai teks biasa memuat seluruh file ke memori. | Gunakan `txt_opts.save_format = aw.SaveFormat.TXT` dan proses file dalam potongan jika memori terbatas. |
| **Lisensi hilang** | Versi percobaan menyisipkan watermark ke dalam output. | Terapkan lisensi yang valid sebelum memanggil `aw.Document`. Contoh: `aw.License().set_license("Aspose.Words.lic")`. |

Menangani kasus tepi ini memastikan bahwa **extract equations latex** berfungsi secara andal di berbagai file sumber.

## Simpan Word sebagai TXT sambil mempertahankan persamaan – pendekatan alternatif

Jika Anda lebih menyukai format output lain, Aspose.Words juga mendukung:

* **HTML** – `aw.saving.HtmlSaveOptions` dengan `office_math_export_mode = LATEX`.
* **Markdown** – `aw.saving.MarkdownSaveOptions` dengan mode ekspor yang sama.

Kedua alternatif mempertahankan markup LaTeX tetap utuh, memberi Anda fleksibilitas untuk format mirip **save word as txt** yang lebih cocok untuk alat downstream.

## Ekstrak persamaan LaTeX dari dokumen – skrip validasi cepat

Setelah Anda memiliki `out.txt`, Anda mungkin ingin mengisolasi hanya persamaan LaTeX. Potongan kode berikut menunjukkan ekstraksi sederhana menggunakan ekspresi reguler:

```python
import re

def extract_latex_equations(txt_path: str) -> list[str]:
    """
    Returns a list of LaTeX equation strings found in a plain‑text file.
    """
    with open(txt_path, "r", encoding="utf-8") as f:
        content = f.read()
    # Matches LaTeX between \[ and \] or $$...$$
    pattern = r"\\\[(.*?)\\\]|\\\$(.*?)\\\$"
    matches = re.findall(pattern, content, re.DOTALL)
    # Flatten the tuple results and strip whitespace
    equations = [eq.strip() for pair in matches for eq in pair if eq]
    return equations

# Example usage
eqs = extract_latex_equations("YOUR_DIRECTORY/out.txt")
print("Found equations:", len(eqs))
for i, eq in enumerate(eqs, 1):
    print(f"{i}: {eq}")
```

Menjalankan skrip ini mencetak setiap potongan LaTeX yang diekstrak, mengonfirmasi bahwa **export word equations latex** berhasil.

## Kesimpulan

Anda kini tahu **cara mengekspor LaTeX** dari dokumen Word menggunakan Aspose.Words, cara **mengonversi DOCX ke LaTeX**, cara **menyimpan Word sebagai TXT** sambil mempertahankan markup persamaan, dan cara **mengekstrak persamaan LaTeX** untuk pemrosesan lebih lanjut. Contoh lengkap menunjukkan konversi satu‑langkah yang andal dan berfungsi dengan file Word modern apa pun yang berisi objek Office Math.

Dari sini Anda dapat menjelajahi:

* Membuat struktur proyek LaTeX lengkap (preamble, `

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Simpan DOCX sebagai TXT – Ekspor Persamaan Word ke LaTeX](/words/english/net/programming-with-txtsaveoptions/save-docx-as-txt-export-word-equations-to-latex/)
- [Konversi docx ke txt – Ekspor Persamaan Word sebagai LaTeX](/words/english/net/basic-conversions/convert-docx-to-txt-export-word-equations-as-latex/)
- [Cara Mengonversi Persamaan di Word ke LaTeX – Simpan sebagai TXT](/words/english/net/programming-with-officemath/how-to-convert-equations-in-word-to-latex-save-as-txt/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}