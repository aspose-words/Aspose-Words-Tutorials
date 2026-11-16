---
category: general
date: 2026-11-15
description: Konversi docx ke txt sambil mempertahankan persamaan sebagai LaTeX. Pelajari
  langkah demi langkah cara mengekstrak teks dari Word dan menyimpan Word sebagai
  txt menggunakan Aspose.Words untuk Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- convert docx to txt
- extract text from word
- how to export equations
- export word equations latex
- save word as txt
language: id
lastmod: 2026-11-15
og_description: Konversi docx ke txt secara instan. Tutorial ini menunjukkan cara
  mengekstrak teks dari Word, mengekspor persamaan ke LaTeX, dan menyimpan Word sebagai
  txt menggunakan Aspose.Words.
og_image_alt: Screenshot illustrating convert docx to txt workflow with LaTeX equation
  export
og_title: Konversi docx ke txt dengan ekspor persamaan LaTeX – Panduan Python
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: convert docx to txt while preserving equations as LaTeX. Learn step‑by‑step
    how to extract text from Word and save Word as txt using Aspose.Words for Python.
  headline: How to convert docx to txt and export equations as LaTeX
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
title: Cara mengonversi docx ke txt dan mengekspor persamaan sebagai LaTeX
url: /id/python/document-conversion/how-to-convert-docx-to-txt-and-export-equations-as-latex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengonversi docx ke txt dan mengekspor persamaan sebagai LaTeX

Jika Anda perlu **mengonversi docx ke txt** dan mempertahankan setiap persamaan dalam format LaTeX, panduan ini akan membawa Anda melalui seluruh proses. Anda akan belajar cara **mengekstrak teks dari Word**, mengonfigurasi opsi penyimpanan, dan akhirnya **menyimpan Word sebagai txt** dengan markup LaTeX yang bersih.

Solusi ini bekerja dengan Aspose.Words for Python via .NET, membutuhkan hanya beberapa baris kode, dan dapat dijalankan di platform apa pun yang mendukung Python 3.8+. Tidak diperlukan alat konversi tambahan.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* Python 3.8 atau yang lebih baru terpasang.
* Lisensi Aspose.Words for Python via .NET yang valid (atau kunci evaluasi gratis).
* Paket `aspose-words` terinstal (`pip install aspose-words`).
* Dokumen Word (`.docx`) yang berisi teks biasa dan persamaan Office Math.

## Langkah 1: Siapkan proyek dan impor pustaka

Buat file Python baru, misalnya `convert_docx_to_txt.py`, dan tambahkan pernyataan impor yang diperlukan.

```python
import aspose.words as aw

# Optional: set your license if you have one
# aw.License().set_license("Aspose.Words.lic")
```

**Mengapa langkah ini penting:** Mengimpor `aspose.words` memberi Anda akses ke kelas `Document` dan objek `TxtSaveOptions`, yang esensial untuk mengontrol bagaimana konten DOCX ditulis ke file teks biasa.

## Langkah 2: Muat dokumen Word

```python
# Load the source .docx file
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)
```

**Mengapa langkah ini penting:** Objek `Document` mewakili seluruh file Word dalam memori. Memuat file sekali memungkinkan Anda menggunakan kembali objek yang sama untuk beberapa operasi ekspor, yang meningkatkan kinerja untuk dokumen besar.

## Langkah 3: Konfigurasikan opsi penyimpanan TXT untuk mengekspor persamaan sebagai LaTeX

```python
# Create TXT save options
txt_opts = aw.saving.TxtSaveOptions()

# Export Office Math equations using LaTeX syntax
txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX

# Optional: force UTF‑8 encoding to preserve special characters
txt_opts.encoding = "utf-8"
```

**Mengapa langkah ini penting:** Dengan mengatur `office_math_export_mode` ke `LATEX`, setiap persamaan diubah menjadi representasi LaTeX‑nya alih‑alih dihapus atau dirender sebagai teks biasa. Properti `encoding` memastikan karakter di luar rentang ASCII (misalnya huruf Yunani) disimpan dengan benar.

## Langkah 4: Simpan dokumen sebagai file teks biasa

```python
# Define the output path
output_path = "YOUR_DIRECTORY/output.txt"

# Save using the configured options
doc.save(output_path, txt_opts)
print(f"Document successfully converted and saved to {output_path}")
```

**Mengapa langkah ini penting:** Metode `save` menulis dokumen ke file `.txt` menggunakan opsi yang telah Anda konfigurasikan. Hasilnya adalah file teks bersih di mana paragraf biasa muncul seperti di Word, dan setiap persamaan muncul sebagai blok LaTeX.

## Output yang diharapkan

Anggap `input.docx` berisi paragraf:

```
The quadratic formula is given by:
```

diikuti oleh persamaan *x = \frac{-b \pm \sqrt{b^2-4ac}}{2a}*.

Setelah menjalankan skrip, `output.txt` akan berisi:

```
The quadratic formula is given by:
$x = \frac{-b \pm \sqrt{b^2-4ac}}{2a}$
```

Semua bagian teks lainnya dipertahankan persis seperti yang muncul di DOCX asli.

## Langkah 5: Menangani kasus tepi dan tip praktik terbaik

| Situasi | Penanganan yang direkomendasikan |
|-----------|----------------------|
| **Dokumen tanpa persamaan** | Skrip tetap berfungsi; `office_math_export_mode` diabaikan, dan Anda mendapatkan teks biasa. |
| **Dokumen besar ( > 100 MB )** | Muat dokumen dalam `MemoryStream` untuk menghindari konsumsi memori berlebih, atau proses halaman secara bertahap jika Anda perlu men-stream output. |
| **Akhiran baris khusus** | Atur `txt_opts.add_bidi_marks = False` dan `txt_opts.save_format = aw.SaveFormat.TEXT` untuk mengontrol perilaku pemutusan baris. |
| **Sistem target non‑UTF‑8** | Ubah `txt_opts.encoding` ke halaman kode yang diperlukan (misalnya, `"windows-1252"`). |
| **Mempertahankan pemisah halaman** | Aktifkan `txt_opts.save_format = aw.SaveFormat.TEXT` dan `txt_opts.export_page_breaks = True`. |

**Tip pro:** Jika Anda berencana memasukkan file `.txt` yang dihasilkan ke kompiler LaTeX, bungkus seluruh file dengan header dokumen LaTeX minimal (`\documentclass{article} … \begin{document}`) sebelum kompilasi.

## Skrip lengkap untuk salin‑tempel cepat

```python
import aspose.words as aw

def convert_docx_to_txt(
    input_path: str,
    output_path: str,
    encoding: str = "utf-8",
    export_equations_as_latex: bool = True,
) -> None:
    """
    Convert a DOCX file to a TXT file while optionally exporting equations as LaTeX.
    
    Parameters
    ----------
    input_path : str
        Path to the source .docx file.
    output_path : str
        Destination path for the generated .txt file.
    encoding : str, optional
        Text encoding for the output file. Default is UTF‑8.
    export_equations_as_latex : bool, optional
        When True, Office Math equations are written as LaTeX. When False, they are omitted.
    """
    # Load the document
    doc = aw.Document(input_path)

    # Configure save options
    txt_opts = aw.saving.TxtSaveOptions()
    txt_opts.encoding = encoding

    if export_equations_as_latex:
        txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
    else:
        txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.NONE

    # Save the TXT file
    doc.save(output_path, txt_opts)
    print(f"convert docx to txt completed: {output_path}")

# Example usage
if __name__ == "__main__":
    convert_docx_to_txt(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.txt"
    )
```

Menjalankan skrip akan mencetak baris konfirmasi dan menghasilkan file teks yang **mengekstrak teks dari Word** sambil mempertahankan setiap persamaan dalam bentuk LaTeX.

## Kesimpulan

Anda kini tahu cara **mengonversi docx ke txt**, **mengekstrak teks dari Word**, dan **mengekspor persamaan Word ke LaTeX** menggunakan Aspose.Words for Python. Solusi lengkap ini menunjukkan mengapa setiap konfigurasi penting, mencakup kasus tepi umum, dan menyediakan fungsi yang dapat digunakan kembali untuk proyek di masa depan.

**Langkah selanjutnya**

* Jelajahi flag `TxtSaveOptions` lainnya seperti `preserve_table_layout` jika Anda perlu mempertahankan struktur tabel.
* Gabungkan konversi ini dengan pemroses batch untuk menangani banyak file DOCX dalam satu folder.
* Jika Anda memerlukan output PDF alih‑alih TXT, ganti `TxtSaveOptions` dengan `PdfSaveOptions` dan pertahankan mode ekspor LaTeX yang sama.

Silakan sesuaikan skrip dengan alur kerja Anda, bereksperimen dengan berbagai encoding, dan integrasikan ke dalam pipeline pemrosesan dokumen yang lebih besar. Selamat coding!


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [convert docx to txt and export equations from Word as LaTeX – Complete Guide](/words/english/python-net/document-conversion/convert-docx-to-txt-and-export-equations-from-word-as-latex/)
- [save docx as txt – Export Word Math to LaTeX with Python](/words/english/python-net/document-conversion/save-docx-as-txt-export-word-math-to-latex-with-python/)
- [save docx as txt – Complete Guide to Export Word Equations](/words/english/python-net/document-conversion/save-docx-as-txt-complete-guide-to-export-word-equations/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}