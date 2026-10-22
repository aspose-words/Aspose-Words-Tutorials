---
category: general
date: 2026-10-07
description: Pelajari cara mengekspor Office Math ke LaTeX dalam Python dengan Aspose.Words.
  Panduan langkah demi langkah ini menunjukkan cara mengekspor persamaan dari Word
  ke format LaTeX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to export office math to latex
- how to export equations from word
- Aspose.Words Python
- LaTeX conversion
- Office Math extraction
language: id
lastmod: 2026-10-07
og_description: Cara mengekspor Office Math ke LaTeX di Python menggunakan Aspose.Words.
  Ikuti panduan ini untuk mengekspor persamaan dari Word dengan cepat dan dapat diandalkan.
og_image_alt: Screenshot of LaTeX equation output generated from a Word document
og_title: Ekspor matematika Office ke LaTeX dengan Python – panduan lengkap
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to export office math to LaTeX in Python with Aspose.Words.
    This step‑by‑step guide shows you how to export equations from Word to LaTeX format.
  headline: How to export office math to LaTeX in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- LaTeX
- Office Math
title: Cara mengekspor matematika Office ke LaTeX di Python
url: /id/python/document-conversion/how-to-export-office-math-to-latex-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengekspor Office Math ke LaTeX di Python

Jika Anda perlu mengekspor Office Math ke LaTeX, panduan ini menunjukkan cara mengekspor persamaan dari Word menggunakan Aspose.Words untuk Python. Anda akan melihat contoh lengkap yang dapat dijalankan yang mengonversi file `.docx` yang berisi objek Office Math menjadi kode LaTeX teks‑biasa.

Mengekspor persamaan adalah kebutuhan umum ketika Anda ingin menggunakan kembali konten Word dalam makalah ilmiah, generator situs statis, atau alur kerja apa pun yang bergantung pada LaTeX. Langkah‑langkah di bawah ini mencakup semuanya mulai dari menginstal SDK hingga memverifikasi output yang dihasilkan.

## Prasyarat

Sebelum Anda memulai, pastikan Anda memiliki:

* Python 3.8 atau yang lebih baru terpasang di mesin Anda.
* Lisensi yang valid untuk **Aspose.Words for Python via .NET** (evaluasi gratis dapat digunakan untuk pengujian).
* Akses `pip` untuk menginstal paket `aspose-words`.
* Dokumen Word (`.docx`) yang berisi setidaknya satu objek Office Math (persamaan). Untuk tutorial ini kami mengasumsikan file tersebut bernama `math.docx` dan berada di `YOUR_DIRECTORY`.

> **Tip pro:** Jika Anda tidak memiliki file lisensi, letakkan lisensi percobaan (`Aspose.Words.lic`) di direktori yang sama dengan skrip Anda; SDK akan memuatnya secara otomatis.

## Instal Aspose.Words untuk Python

Langkah pertama adalah menambahkan pustaka Aspose.Words ke lingkungan Python Anda.

```bash
pip install aspose-words
```

Menjalankan perintah tersebut menginstal paket `aspose.words` dan semua komponen runtime .NET yang diperlukan. Setelah instalasi, Anda dapat mengimpor pustaka dengan `import aspose.words as aw`.

## Langkah 1: Muat dokumen Word yang berisi persamaan

Anda harus memuat file `.docx` sumber sebelum dapat memanipulasi isinya. Kelas `Document` membaca file ke dalam memori dan memberi Anda akses ke setiap elemen, termasuk objek Office Math.

```python
import aspose.words as aw

# Replace YOUR_DIRECTORY with the actual path to your files
doc_path = "YOUR_DIRECTORY/math.docx"

# Load the Word document that holds the equations
document = aw.Document(doc_path)
```

Memuat dokumen penting karena proses ekspor bekerja pada representasi dalam memori, bukan langsung pada sistem berkas.

## Langkah 2: Buat opsi penyimpanan TXT dan atur mode ekspor

Aspose.Words menyimpan dokumen sebagai teks biasa menggunakan `TxtSaveOptions`. Secara default, objek Office Math dirender sebagai karakter Unicode, yang menghilangkan struktur matematis. Menetapkan `office_math_export_mode` ke `LATEX` memberi tahu SDK untuk menghasilkan kode LaTeX untuk setiap persamaan.

```python
# Create TXT save options to control the export behavior
txt_options = aw.saving.TxtSaveOptions()

# Export any Office Math (equations) in LaTeX format
txt_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
```

Konstanta `OfficeMathExportMode.LATEX` adalah kunci yang mengaktifkan konversi ke LaTeX. Tanpa ini, output akan berisi perkiraan teks biasa dari persamaan.

## Langkah 3: Simpan dokumen sebagai file teks‑biasa menggunakan opsi yang telah dikonfigurasi

Sekarang tulis dokumen ke file `.txt`. SDK menerapkan opsi yang Anda atur pada langkah sebelumnya, menghasilkan file di mana setiap persamaan muncul sebagai fragmen LaTeX.

```python
# Destination path for the exported LaTeX text file
out_path = "YOUR_DIRECTORY/out.txt"

# Save the document using the TXT options that include LaTeX conversion
document.save(out_path, txt_options)

print(f"LaTeX export completed. File saved to: {out_path}")
```

Setelah skrip selesai, `out.txt` berisi teks Word asli ditambah representasi LaTeX dari setiap objek Office Math.

## Verifikasi output LaTeX

Buka `out.txt` dengan editor teks apa pun untuk melihat hasilnya. Persamaan tipikal seperti *\(a^2 + b^2 = c^2\)* akan muncul sebagai:

```
\[
a^{2}+b^{2}=c^{2}
\]
```

Jika Anda lebih suka melihat LaTeX langsung di konsol, Anda dapat membaca kembali file tersebut dan mencetak isinya:

```python
with open(out_path, "r", encoding="utf-8") as f:
    latex_content = f.read()
    print("--- LaTeX content start ---")
    print(latex_content)
    print("--- LaTeX content end ---")
```

Output harus cocok dengan persamaan di dokumen Word asli, mempertahankan pecahan, superskrip, subskrip, dan simbol matematika lainnya.

## Cara mengekspor persamaan dari Word – menangani kasus tepi

Meskipun alur dasar bekerja untuk kebanyakan dokumen, beberapa skenario memerlukan perhatian ekstra:

| Situasi | Pendekatan yang disarankan |
|-----------|----------------------|
| **Dokumen berisi MathML dan Office Math campuran** | Gunakan `OfficeMathExportMode.MATHML` untuk output MathML, atau jalankan proses kedua dengan `LATEX` setelah mengonversi MathML ke LaTeX secara manual. |
| **Dokumen besar menyebabkan tekanan memori** | Proses dokumen per bagian: muat satu bagian, ekspor, lalu buang sebelum melanjutkan ke bagian berikutnya. |
| **Persamaan berada di dalam header atau catatan kaki** | Mode ekspor menangani mereka secara otomatis, tetapi pastikan teks di sekitarnya tidak terpotong oleh opsi penyimpanan khusus. |
| **Lisensi tidak ada menyebabkan watermark evaluasi** | Pastikan file lisensi dimuat sebelum operasi `Document` apa pun: `aw.License().set_license("Aspose.Words.lic")`. |

Menangani kasus tepi ini memastikan bahwa **cara mengekspor Office Math ke LaTeX** berfungsi secara andal di berbagai file Word.

## Skrip lengkap

Berikut adalah skrip Python lengkap yang dapat Anda salin, tempel, dan jalankan. Skrip ini mencakup penanganan kesalahan dan komentar untuk kejelasan.

```python
import aspose.words as aw
import os
import sys

def export_office_math_to_latex(input_docx: str, output_txt: str) -> None:
    """
    Exports Office Math objects from a Word document to LaTeX format.
    Parameters
    ----------
    input_docx : str
        Path to the source .docx file containing equations.
    output_txt : str
        Path where the LaTeX‑enhanced plain‑text file will be saved.
    """
    if not os.path.isfile(input_docx):
        sys.exit(f"Error: Input file not found – {input_docx}")

    # Load the document
    document = aw.Document(input_docx)

    # Configure TXT save options for LaTeX conversion
    txt_options = aw.saving.TxtSaveOptions()
    txt_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX

    # Save the result
    document.save(output_txt, txt_options)
    print(f"LaTeX export completed. File saved to: {output_txt}")

if __name__ == "__main__":
    # Update these paths to match your environment
    INPUT_PATH = "YOUR_DIRECTORY/math.docx"
    OUTPUT_PATH = "


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang erat yang membangun pada teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Convert docx to markdown – Export Math Equations to LaTeX with Aspose.Words](/words/english/java/document-conversion-and-export/convert-docx-to-markdown-export-math-equations-to-latex-with/)
- [Save docx as txt – Export Equations to LaTeX with Aspose.Words](/words/english/net/programming-with-officemath/save-docx-as-txt-export-equations-to-latex-with-aspose-words/)
- [How to Export LaTeX from Word – Convert DOCX to Markdown](/words/english/python-net/document-conversion/how-to-export-latex-from-word-convert-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}