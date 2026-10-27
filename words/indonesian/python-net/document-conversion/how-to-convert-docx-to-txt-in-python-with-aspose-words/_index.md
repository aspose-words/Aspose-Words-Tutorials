---
category: general
date: 2026-09-27
description: Konversi docx ke txt di Python menggunakan Aspose.Words. Pelajari cara
  memuat dokumen Word, mengatur enkoding UTF‑8, dan mengekspor dokumen Word ke txt
  dalam beberapa baris.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- convert docx to txt
- convert word to plain text
- save word as plain text
- export word document txt
- load word document python
language: id
lastmod: 2026-09-27
og_description: Konversi docx ke txt di Python dengan Aspose.Words. Tutorial ini menunjukkan
  cara memuat dokumen Word, mengonfigurasi pengkodean, dan menyimpan Word sebagai
  teks biasa.
og_image_alt: Screenshot of Python code that converts a DOCX file to a TXT file
og_title: Mengonversi docx ke txt di Python – panduan langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Convert docx to txt in Python using Aspose.Words. Learn to load a Word
    document, set UTF‑8 encoding, and export Word document txt in a few lines.
  headline: How to convert docx to txt in Python with Aspose.Words
  type: TechArticle
tags:
- Python
- Aspose.Words
- Document conversion
title: Cara mengonversi docx ke txt di Python dengan Aspose.Words
url: /id/python/document-conversion/how-to-convert-docx-to-txt-in-python-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengonversi docx ke txt di Python dengan Aspose.Words

Jika Anda perlu **convert docx to txt** dengan cepat, panduan ini menunjukkan solusi lengkap di Python. Anda akan belajar cara **load word document python**, mengonfigurasi enkoding UTF‑8, dan **export word document txt** dengan hanya beberapa baris kode.

Tutorial ini mencakup semua yang Anda perlukan untuk menjalankan konversi pada platform apa pun yang mendukung Python 3. Pada akhir artikel Anda akan dapat **save word as plain text** secara andal, bahkan ketika dokumen sumber berisi karakter khusus atau simbol non‑ASCII.

## Prasyarat

Sebelum Anda mulai, pastikan Anda memiliki:

* Python 3.8 atau yang lebih baru terpasang.
* Lisensi Aspose.Words for Python yang aktif (versi percobaan gratis dapat digunakan untuk evaluasi).
* Paket `aspose-words` terpasang melalui `pip install aspose-words`.
* File DOCX yang ingin Anda konversi (contoh menggunakan `input.docx`).

> **Pro tip:** Simpan file lisensi Anda (`Aspose.Words.lic`) di folder yang sama dengan skrip Anda atau tetapkan jalur `Aspose.Words.License` secara eksplisit untuk menghindari watermark mode evaluasi.

## Instal Aspose.Words

Jalankan perintah berikut di terminal atau command prompt Anda:

```bash
pip install aspose-words
```

Paket ini menyertakan namespace `aw` yang digunakan di seluruh contoh kode.

## Langkah 1 – Muat dokumen Word (convert docx to txt)

Operasi pertama adalah membaca file DOCX ke dalam objek `aw.Document`. Langkah ini sesuai dengan kebutuhan **load word document python**.

```python
import aspose.words as aw

# Load the source DOCX file
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*Mengapa ini penting*: Memuat dokumen membuat representasi dalam memori yang dapat dimanipulasi oleh Aspose.Words, terlepas dari format file asli.

## Langkah 2 – Konfigurasi opsi penyimpanan TXT (convert word to plain text)

Aspose.Words menyediakan `TxtSaveOptions` untuk mengontrol bagaimana output teks biasa dihasilkan. Menetapkan properti `encoding` ke `"utf-8"` memastikan semua karakter Unicode dipertahankan.

```python
# Create TXT save options and set UTF‑8 encoding
txt_options = aw.saving.TxtSaveOptions()
txt_options.encoding = "utf-8"
```

*Mengapa ini penting*: Tanpa enkoding eksplisit, halaman kode sistem default dapat menggantikan karakter non‑ASCII dengan tanda tanya. UTF‑8 adalah pilihan paling aman untuk dokumen multibahasa.

## Langkah 3 – Simpan dokumen sebagai teks biasa (save word as plain text)

Sekarang tulis dokumen ke file `.txt` menggunakan opsi yang telah didefinisikan di atas.

```python
# Export the document to a plain‑text file
output_path = "YOUR_DIRECTORY/out.txt"
doc.save(output_path, txt_options)
print(f"Document exported successfully to {output_path}")
```

File `out.txt` yang dihasilkan hanya berisi konten teks dari `input.docx`, dengan pemisah baris yang sesuai dengan struktur paragraf asli.

### Output yang Diharapkan

Jika `input.docx` berisi kalimat:

> **“Hello, world! Привет мир!”**

maka `out.txt` yang dihasilkan akan menampilkan:

```
Hello, world! Привет мир!
```

Semua karakter tetap utuh karena enkoding UTF‑8 telah diterapkan.

## Menangani kasus tepi umum

| Situasi | Pendekatan yang disarankan |
|-----------|----------------------|
| **Dokumen berisi tabel** | Aspose.Words meratakan sel tabel menjadi teks biasa yang dipisahkan oleh tab. Jika Anda memerlukan pemisah khusus, atur `txt_options.table_cell_separator` sesuai kebutuhan. |
| **File besar (≥ 100 MB)** | Stream dokumen untuk menghindari konsumsi memori tinggi: gunakan `doc.save(output_stream, txt_options)` dimana `output_stream` adalah objek file yang dibuka dalam mode biner. |
| **Font yang hilang** | Instal font yang diperlukan pada mesin host atau sematkan dalam DOCX sebelum konversi. Font yang hilang hanya memengaruhi tampilan visual, bukan ekstraksi teks biasa. |
| **DOCX yang dilindungi password** | Berikan password saat memuat: `doc = aw.Document("secure.docx", aw.LoadOptions(password="MySecret"))`. |

## Skrip lengkap – siap dijalankan

Simpan kode berikut sebagai `convert_docx_to_txt.py` dan jalankan dengan `python convert_docx_to_txt.py`.

```python
import aspose.words as aw
import os

def convert_docx_to_txt(input_path: str, output_path: str, encoding: str = "utf-8") -> None:
    """
    Converts a DOCX file to a TXT file using Aspose.Words.

    Args:
        input_path: Path to the source .docx file.
        output_path: Desired path for the resulting .txt file.
        encoding: Text encoding for the output file (default UTF‑8).
    """
    if not os.path.isfile(input_path):
        raise FileNotFoundError(f"Input file not found: {input_path}")

    # Load the Word document (load word document python)
    document = aw.Document(input_path)

    # Configure TXT save options (convert word to plain text)
    txt_options = aw.saving.TxtSaveOptions()
    txt_options.encoding = encoding

    # Save as plain‑text (save word as plain text)
    document.save(output_path, txt_options)
    print(f"Conversion complete: {output_path}")

if __name__ == "__main__":
    INPUT_FILE = "YOUR_DIRECTORY/input.docx"
    OUTPUT_FILE = "YOUR_DIRECTORY/out.txt"
    convert_docx_to_txt(INPUT_FILE, OUTPUT_FILE)
```

Menjalankan skrip akan mencetak baris konfirmasi dan membuat `out.txt` di direktori yang ditentukan.

## Verifikasi hasil

Setelah eksekusi, buka `out.txt` di editor teks apa pun (mis., VS Code, Notepad++) dan pastikan kontennya cocok dengan teks DOCX asli. Jika Anda melihat karakter rusak, periksa kembali bahwa `txt_options.encoding` disetel ke `"utf-8"`.

## Langkah selanjutnya dan topik terkait

* **Convert docx to pdf** – gunakan `aw.saving.PdfSaveOptions` untuk output PDF dengan fidelitas tinggi.
* **Extract images from a Word document** – jelajahi `aw.NodeType.SHAPE` dan kelas `Shape`.
* **Batch conversion** – iterasi melalui folder berisi file DOCX dan panggil `convert_docx_to_txt` untuk setiap entri.
* **Advanced encoding** – bereksperimen dengan `txt_options.add_bidi_marks` saat menangani skrip kanan‑ke‑kiri.

Dengan menguasai langkah-langkah di atas, Anda dapat **export word document txt** dalam pipeline otomatisasi apa pun, baik Anda membangun alat baris perintah, mengintegrasikan dengan layanan web, atau memproses dokumen di cloud.

---

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Convert docx to txt – Panduan Lengkap Menyimpan Word sebagai Teks Biasa](/words/english/net/programming-with-txtsaveoptions/convert-docx-to-txt-complete-guide-to-saving-word-as-plain-t/)
- [Aspose.Words – Simpan docx sebagai txt dan Ekspor Persamaan Word sebagai LaTeX – Panduan Lengkap](/words/english/net/basic-conversions/save-docx-as-txt-complete-guide-to-export-word-equations-as/)
- [Tutorial Word ke PDF: Konversi DOCX ke PDF dengan Aspose.Words](/words/english/net/basic-conversions/word-to-pdf-tutorial-convert-docx-to-pdf-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}