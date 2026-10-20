---
category: general
date: 2026-07-29
description: Tambahkan bayangan pada bentuk di Word menggunakan Python dan Aspose.Words.
  Pelajari cara menerapkan efek bayangan pada dokumen Word dengan cepat melalui contoh
  kode lengkap.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- apply shadow effect word
language: id
lastmod: 2026-07-29
og_description: Tambahkan bayangan pada bentuk di dokumen Word dengan Python. Panduan
  ini menunjukkan cara menerapkan efek bayangan pada file Word menggunakan Aspose.Words,
  lengkap dengan kode dan tips.
og_image_alt: Word document displaying a rectangle shape with a soft gray shadow applied
og_title: Tambahkan Bayangan pada Bentuk di Word – Tutorial Python
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add shadow to shape in Word using Python and Aspose.Words. Learn how
    to apply shadow effect Word documents quickly with a full code example.
  headline: Add Shadow to Shape in Word with Python – Complete Guide
  type: TechArticle
- description: Add shadow to shape in Word using Python and Aspose.Words. Learn how
    to apply shadow effect Word documents quickly with a full code example.
  name: Add Shadow to Shape in Word with Python – Complete Guide
  steps:
  - name: '**No shape found** – If your document only contains text, the script will
      raise a `ValueError`. Add a shape first or extend the script to iterate over
      all `Shape` nodes.'
    text: '**No shape found** – If your document only contains text, the script will
      raise a `ValueError`. Add a shape first or extend the script to iterate over
      all `Shape` nodes.'
  - name: '**License watermark** – Running the code without a proper license inserts
      an “Aspose.Words Evaluation” watermark on each page. Grab a trial license from
      the Aspose portal to keep the output clean.'
    text: '**License watermark** – Running the code without a proper license inserts
      an “Aspose.Words Evaluation” watermark on each page. Grab a trial license from
      the Aspose portal to keep the output clean.'
  - name: '**Incorrect file paths** – Using relative paths can cause `FileNotFoundError`
      when the script’s working directory differs. Prefer `os.path.abspath` or pass
      absolute paths.'
    text: '**Incorrect file paths** – Using relative paths can cause `FileNotFoundError`
      when the script’s working directory differs. Prefer `os.path.abspath` or pass
      absolute paths.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word Automation
title: Tambahkan Bayangan pada Bentuk di Word dengan Python – Panduan Lengkap
url: /id/python/images-shapes/add-shadow-to-shape-in-word-with-python-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menambahkan Bayangan ke Bentuk di Word dengan Python – Panduan Lengkap

Pernah membutuhkan **add shadow to shape** dalam dokumen Word tetapi tidak yakin harus mulai dari mana? Dalam tutorial ini kami akan memandu Anda melalui cara praktis untuk **apply shadow effect Word** file menggunakan pustaka Aspose.Words for Python.

Jika Anda pernah bermain-main dengan UI dan berpikir, “Harus ada cara programatis untuk melakukan ini,” Anda berada di tempat yang tepat. Pada akhir tutorial Anda akan memiliki skrip yang dapat dijalankan yang menambahkan bayangan tepi lembut pada bentuk apa pun yang Anda pilih.

## Prasyarat

- Python 3.8+ terpasang (versi terbaru apa pun dapat digunakan)
- Lisensi aktif Aspose.Words for Python atau percobaan gratis (API berfungsi tanpa lisensi tetapi menambahkan watermark)
- Dokumen Word (`.docx`) yang sudah berisi setidaknya satu bentuk (segi empat, gambar, atau SmartArt)
- Familiaritas dasar dengan impor Python dan penanganan pengecualian

> **Pro tip:** Jika Anda belum memiliki bentuk, buka Word, sisipkan segi empat sederhana, dan simpan file sebagai `input.docx` di folder yang dapat Anda referensikan dari skrip Anda.

## Instal Aspose.Words untuk Python

Jalankan perintah pip berikut di terminal Anda:

```bash
pip install aspose-words
```

Perintah tersebut mengunduh rilis 23.x terbaru, yang mendukung properti bayangan pada node `Shape`.

## Langkah 1: Muat Dokumen Word

Hal pertama yang kami lakukan adalah membuka file `.docx` yang ada. Di sinilah operasi **add shadow to shape** dimulai.

```python
import aspose.words as aw

# Load the source document
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)
```

> **Mengapa ini penting:** `aw.Document` mengurai seluruh file Word menjadi struktur mirip DOM, memungkinkan kami menelusuri node seperti bentuk, paragraf, dan tabel.

## Langkah 2: Temukan Bentuk Target

Aspose.Words menyediakan metode pencarian mendalam `get_child` yang dapat mengambil bentuk pertama terlepas dari tingkat penumpukan. Jika Anda memiliki banyak bentuk, Anda dapat menyesuaikan indeks atau melakukan loop pada semua bentuk.

```python
# Retrieve the first shape (deep search = True)
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

if shape is None:
    raise ValueError("No shape found in the document. Add a shape and try again.")
```

> **Kasus khusus:** Beberapa dokumen hanya berisi objek gambar (misalnya, foto). Objek‑objek tersebut juga direpresentasikan sebagai node `Shape`, sehingga kode ini bekerja untuk segi empat maupun gambar.

## Langkah 3: Konfigurasikan Penampilan Bayangan

Sekarang masuk ke inti **add shadow to shape**—menetapkan properti bayangan. Nilai‑nilai berikut memberikan tampilan yang halus dan profesional:

```python
# Softness of the shadow edges
shape.shadow_blur = 5.0

# Horizontal and vertical offsets (in points)
shape.shadow_offset_x = 2.0
shape.shadow_offset_y = 2.0

# Transparency – 0 is invisible, 1 is solid
shape.shadow_opacity = 0.7
```

Anda dapat bereksperimen dengan angka‑angka ini:

- Tingkatkan `shadow_blur` untuk tepi yang lebih kabur.
- Gunakan offset negatif untuk menggeser bayangan ke kiri atau ke atas.
- Sesuaikan `shadow_opacity` agar bayangan lebih menonjol.

> **Mengapa nilai default ini?** Blur sebesar 5 point meniru bayangan default Word, sementara opacity 0.7 membuat efek terlihat tanpa mengalahkan warna isi bentuk.

## Langkah 4: Simpan Dokumen yang Dimodifikasi

Akhirnya, tulis perubahan ke file baru. Menjaga file asli tetap tidak tersentuh memudahkan proses debugging.

```python
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Shadow applied! Saved updated file to {output_path}")
```

Pada titik ini Anda telah berhasil **add shadow to shape** dan dapat membuka `output.docx` untuk melihat efeknya.

## Contoh Kerja Lengkap

Menggabungkan semuanya, berikut skrip mandiri yang dapat Anda salin‑tempel dan jalankan langsung:

```python
import aspose.words as aw
import os

def add_shadow_to_first_shape(input_file: str, output_file: str) -> None:
    """
    Loads a Word document, adds a soft shadow to the first shape,
    and saves the result to a new file.

    Parameters
    ----------
    input_file : str
        Path to the source .docx file.
    output_file : str
        Destination path for the modified document.
    """
    # Verify the input exists
    if not os.path.isfile(input_file):
        raise FileNotFoundError(f"Input file not found: {input_file}")

    # Load the document
    doc = aw.Document(input_file)

    # Find the first shape (deep search)
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

    if shape is None:
        raise ValueError("No shape found in the document. Insert a shape and retry.")

    # Apply shadow settings
    shape.shadow_blur = 5.0
    shape.shadow_offset_x = 2.0
    shape.shadow_offset_y = 2.0
    shape.shadow_opacity = 0.7

    # Save the updated document
    doc.save(output_file)

if __name__ == "__main__":
    INPUT_DOC = "YOUR_DIRECTORY/input.docx"
    OUTPUT_DOC = "YOUR_DIRECTORY/output.docx"
    add_shadow_to_first_shape(INPUT_DOC, OUTPUT_DOC)
    print("✅ Shadow added successfully.")
```

### Output yang Diharapkan

Buka `output.docx` dan Anda akan melihat bentuk asli kini memiliki bayangan abu‑abu lembut, sedikit bergeser ke kanan dan ke bawah. Efek ini meniru apa yang Anda dapatkan ketika secara manual menerapkan **apply shadow effect word** melalui UI.

![Shadowed shape example](https://example.com/shadowed_shape.png "Word shape with a soft shadow"){: .center-image width="600" alt="Tangkapan layar yang menunjukkan sebuah bentuk dengan bayangan dalam dokumen Word"}

## Menerapkan Shadow Effect Word – Opsi Lanjutan

Jika Anda memerlukan kontrol lebih, Aspose.Words memungkinkan Anda menyesuaikan properti tambahan:

| Properti | Deskripsi | Rentang Umum |
|----------|-----------|--------------|
| `shadow_color` | Warna bayangan (default hitam) | Semua `aw.Color` |
| `shadow_type` | Menentukan apakah bayangan **outer**, **inner**, atau **perspective** | Enum `aw.ShadowType` |
| `shadow_transform` | Menerapkan matriks transformasi khusus untuk bayangan miring | Lanjutan – gunakan dengan hati‑hati |

Contoh mengatur bayangan biru:

```python
shape.shadow_color = aw.Color.from_argb(255, 0, 0, 255)  # Opaque blue
shape.shadow_type = aw.ShadowType.OUTER
```

Pengaturan ini memungkinkan Anda **apply shadow effect Word** pada dokumen dengan cara kreatif, seperti menambahkan drop shadow berwarna pada logo.

## Kesalahan Umum & Cara Menghindarinya

1. **Tidak ada bentuk yang ditemukan** – Jika dokumen Anda hanya berisi teks, skrip akan mengeluarkan `ValueError`. Tambahkan bentuk terlebih dahulu atau perluas skrip untuk mengiterasi semua node `Shape`.
2. **Watermark lisensi** – Menjalankan kode tanpa lisensi yang tepat menambahkan watermark “Aspose.Words Evaluation” pada setiap halaman. Dapatkan lisensi percobaan dari portal Aspose untuk menjaga output tetap bersih.
3. **Path file tidak tepat** – Menggunakan path relatif dapat menyebabkan `FileNotFoundError` ketika direktori kerja skrip berbeda. Lebih baik gunakan `os.path.abspath` atau berikan path absolut.

## Langkah Selanjutnya

Sekarang Anda telah menguasai **add shadow to shape**, Anda mungkin ingin menjelajahi topik terkait:

- **Menerapkan shadow effect Word** ke beberapa bentuk dalam loop
- Mengonversi dokumen yang telah ditambahkan bayangan ke PDF (`doc.save("output.pdf")`)
- Mengubah warna bayangan berdasarkan isi bentuk (styling dinamis)
- Menggunakan Aspose.Words untuk secara programatis menyisipkan bentuk baru sebelum menambahkan bayangan

Setiap ekstensi ini dibangun di atas konsep API yang sama, sehingga kurva belajar tetap ringan.

## Kesimpulan

Kami telah membahas semua yang Anda perlukan untuk **add shadow to shape** dalam file Word menggunakan Python: memuat dokumen, menemukan bentuk, mengonfigurasi parameter bayangan, dan menyimpan hasilnya. Skrip lengkap di atas siap dimasukkan ke dalam pipeline otomatisasi apa pun, dan tip tambahan membantu Anda **apply shadow effect Word** pada dokumen dengan skenario yang lebih canggih.

Cobalah, ubah nilai blur dan opacity, dan lihat bagaimana bayangan kecil dapat membuat perbedaan visual yang besar. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait dan membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Tutorial Bayangan Bentuk Aspose.Words – Tambahkan Bayangan ke Bentuk Word dalam C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Buat Bentuk Segi Empat di Word dengan Aspose.Words – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Buat Dokumen Word Java – Tambahkan Bentuk Segi Empat dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}