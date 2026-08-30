---
category: general
date: 2026-08-14
description: Cara menambahkan bayangan pada bentuk Word menggunakan Python – pelajari
  cara menerapkan efek bayangan, membuat efek bayangan, dan menyimpan dokumen Word
  secara efisien.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add shadow
- apply shadow effect
- create shadow effect
- save word document
- add shadow to shape
language: id
lastmod: 2026-08-14
og_description: Cara menambahkan bayangan pada bentuk Word menggunakan Python. Ikuti
  tutorial lengkap ini untuk menerapkan efek bayangan, membuat efek bayangan, dan
  menyimpan dokumen Word dengan tampilan profesional.
og_image_alt: Screenshot illustrating how to add shadow to a Word shape using Python
og_title: Cara menambahkan bayangan pada bentuk Word menggunakan Python – panduan
  langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add shadow to a Word shape using Python – learn to apply shadow
    effect, create shadow effect, and save Word document efficiently.
  headline: How to add shadow to a Word shape using Python
  type: TechArticle
- description: How to add shadow to a Word shape using Python – learn to apply shadow
    effect, create shadow effect, and save Word document efficiently.
  name: How to add shadow to a Word shape using Python
  steps:
  - name: Load the Word document
    text: '```python import aspose.words as aw'
  - name: Retrieve the target shape
    text: '```python # Get the first shape in the document tree. shape = doc.get_child(aw.NodeType.SHAPE,
      0, True) ```'
  - name: Create a shadow object for the shape
    text: '```python # Instantiate a Shadow object and assign it to the shape. shape.shadow
      = aw.Shadow() ```'
  - name: Configure the shadow’s appearance
    text: '```python # Adjust the softness of the shadow edges. shape.shadow.blur
      = 5 # Higher values = softer edges'
  - name: Save the document to apply the changes
    text: '```python # Save the modified document. Overwrite or specify a new file
      name. doc.save("YOUR_DIRECTORY/output.docx") ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word:'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
- Document styling
title: Cara menambahkan bayangan pada bentuk Word menggunakan Python
url: /id/python/images-shapes/how-to-add-shadow-to-a-word-shape-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menambahkan bayangan ke bentuk Word menggunakan Python

Jika Anda perlu **menambahkan bayangan** ke sebuah bentuk di dalam dokumen Word, panduan ini menunjukkan langkah‑langkah tepatnya. Anda akan belajar cara menerapkan efek bayangan, membuat efek bayangan, dan menyimpan dokumen Word tanpa meninggalkan IDE Anda.

Menambahkan bayangan visual membuat diagram, catatan, dan ikon lebih menonjol, meningkatkan keterbacaan bagi pengguna akhir. Tutorial ini mengasumsikan Anda memiliki pengetahuan dasar Python dan versi terbaru dari pustaka Aspose.Words untuk Python terpasang.

## Prasyarat

* Python 3.8 atau yang lebih baru terpasang.
* Paket `aspose-words` (`pip install aspose-words`) – pustaka yang memanipulasi file DOCX.
* Dokumen Word (`input.docx`) yang berisi setidaknya satu bentuk (misalnya, AutoShape atau gambar).

Persyaratan ini menjamin bahwa kode dapat dijalankan tanpa perubahan di Windows, macOS, atau Linux.

## Cara menambahkan bayangan ke bentuk dalam dokumen Word

Bagian‑bagian berikut membagi tugas menjadi langkah‑langkah yang jelas dan bernomor. Setiap langkah menjelaskan **mengapa** operasi tersebut penting, bukan hanya **apa** yang harus diketik.

### Langkah 1: Muat dokumen Word

```python
import aspose.words as aw

# Load the existing DOCX file. Replace YOUR_DIRECTORY with the actual path.
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*Mengapa ini penting:* Memuat dokumen membuat representasi dalam memori yang dapat Anda manipulasi. Tanpa objek ini, Anda tidak dapat mengakses bentuk atau menerapkan gaya.

### Langkah 2: Dapatkan bentuk target

```python
# Get the first shape in the document tree.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
```

*Mengapa ini penting:* `get_child` menelusuri hierarki node dokumen dan mengembalikan tipe node yang diminta. Argumen ketiga (`True`) memberi tahu Aspose.Words untuk mencari secara rekursif, memastikan Anda menemukan bentuk meskipun berada di dalam paragraf atau tabel.

> **Pro tip:** Jika dokumen Anda berisi banyak bentuk, iterasikan dengan `doc.get_child_nodes(aw.NodeType.SHAPE, True)` dan pilih yang Anda butuhkan berdasarkan indeks atau dengan memeriksa `shape.title` atau `shape.alt_text`.

### Langkah 3: Buat objek bayangan untuk bentuk

```python
# Instantiate a Shadow object and assign it to the shape.
shape.shadow = aw.Shadow()
```

*Mengapa ini penting:* Instance `Shadow` menyimpan semua parameter visual (blur, distance, color, dll.). Menetapkannya ke bentuk memberi tahu Word untuk menampilkan bayangan saat dokumen dibuka.

### Langkah 4: Konfigurasikan tampilan bayangan

```python
# Adjust the softness of the shadow edges.
shape.shadow.blur = 5          # Higher values = softer edges

# Set how far the shadow is offset from the shape.
shape.shadow.distance = 3     # Measured in points

# Optional: change the shadow color to a light gray.
shape.shadow.color = aw.Color.gray

# Optional: set the shadow's transparency (0 = opaque, 255 = fully transparent).
shape.shadow.transparency = 50
```

*Mengapa ini penting:* `blur` mengontrol difusi bayangan, sedangkan `distance` menentukan offset. Menyesuaikan nilai‑nilai ini memungkinkan Anda mencapai efek angkat halus atau bayangan jatuh yang dramatis. Mengatur `color` dan `transparency` lebih lanjut menyesuaikan tampilan, yang penting ketika dokumen mengikuti panduan gaya perusahaan.

### Langkah 5: Simpan dokumen untuk menerapkan perubahan

```python
# Save the modified document. Overwrite or specify a new file name.
doc.save("YOUR_DIRECTORY/output.docx")
```

*Mengapa ini penting:* Metode `save` menuliskan perubahan dalam memori kembali ke file DOCX fisik. Setelah disimpan, membuka `output.docx` di Microsoft Word akan menampilkan bentuk dengan bayangan yang telah dikonfigurasi.

## Skrip lengkap yang dapat Anda jalankan hari ini

Berikut adalah program Python lengkap yang siap dijalankan. Ganti `YOUR_DIRECTORY` dengan folder yang berisi file Anda.

```python
import aspose.words as aw

# 1️⃣ Load the source document.
doc = aw.Document("YOUR_DIRECTORY/input.docx")

# 2️⃣ Retrieve the first shape (you can loop for multiple shapes).
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# 3️⃣ Attach a new Shadow object.
shape.shadow = aw.Shadow()

# 4️⃣ Configure shadow properties.
shape.shadow.blur = 5
shape.shadow.distance = 3
shape.shadow.color = aw.Color.gray
shape.shadow.transparency = 50

# 5️⃣ Save the updated document.
doc.save("YOUR_DIRECTORY/output.docx")
```

### Hasil yang diharapkan

Saat Anda membuka `output.docx` di Microsoft Word:

* Bentuk pertama akan menampilkan bayangan abu‑abu lembut dengan offset tiga poin.
* Tepi bayangan akan tampak blur, memberikan bentuk sedikit efek tiga dimensi.
* Tidak ada konten lain dalam dokumen yang berubah.

Jika Anda tidak melihat bayangan, pastikan bahwa bentuk tersebut bukan gambar dengan transparansi 100 % atau bahwa mode tampilan dokumen (Print Layout) aktif.

## Variasi umum dan kasus tepi

| Situasi | Cara menyesuaikan kode |
|-----------|-----------------------|
| **Banyak bentuk** | Gunakan `doc.get_child_nodes(aw.NodeType.SHAPE, True)` dan iterasikan koleksi, menerapkan konfigurasi bayangan yang sama pada setiap bentuk. |
| **Hanya bentuk tertentu yang membutuhkan bayangan** | Periksa `shape.name` atau `shape.title` di dalam loop dan terapkan bayangan hanya ketika nama cocok dengan kriteria Anda. |
| **Warna bayangan berbeda** | Setel `shape.shadow.color = aw.Color(255, 0, 0)` untuk bayangan merah, atau gunakan `aw.Color.from_argb(alpha, r, g, b)` untuk opasitas khusus. |
| **Tidak ada bentuk yang ada** | Bungkus pengambilan dalam blok `try/except`; jika `shape` bernilai `None`, buat `Shape` baru (misalnya, persegi panjang) dan tambahkan ke dokumen sebelum menerapkan bayangan. |
| **Menyimpan ke PDF** | Setelah menambahkan bayangan, panggil `doc.save("output.pdf")` – bayangan akan terrender dengan benar pada ekspor PDF. |

Variasi ini memastikan tutorial tetap berguna baik Anda memproses satu templat maupun sekumpulan dokumen.

## Cara menambahkan bayangan tanpa Aspose.Words (alternatif)

Jika Anda lebih menyukai pustaka `python-docx`, Anda tidak dapat langsung mengatur bayangan karena pustaka tersebut tidak mengekspos elemen bayangan VML/OOXML yang mendasarinya. Dalam kasus itu, Anda harus memanipulasi XML secara manual:

```python
from docx import Document
from lxml import etree

doc = Document("input.docx")
shape = doc.inline_shapes[0]._inline
# Insert <v:shadow> element here (complex XML manipulation)
```

Karena Aspose.Words menyediakan API `Shadow` tingkat tinggi, **menambahkan bayangan** jauh lebih sederhana dengan pustaka ini.

## Langkah selanjutnya

Sekarang Anda sudah tahu **cara menambahkan bayangan** ke sebuah bentuk, Anda dapat:

* **menerapkan efek bayangan** pada tabel atau kotak teks menggunakan kelas `Shadow` yang sama.
* **membuat efek bayangan** dengan kombinasi blur dan distance yang berbeda untuk keperluan branding.
* Jelajahi **menambahkan bayangan ke bentuk** bersama opsi pemformatan lain seperti ketebalan garis, warna isi, dan rotasi.
* Otomatiskan pemrosesan massal dengan membaca folder berisi file DOCX, menerapkan bayangan, dan menyimpan masing‑masing dengan nama berstempel waktu.

Ekstensi ini memungkinkan Anda membangun pipeline styling dokumen lengkap yang memenuhi standar desain perusahaan.

---

*Anda telah mempelajari cara menambahkan bayangan ke bentuk Word menggunakan Python, cara menerapkan efek bayangan, cara membuat efek bayangan, dan cara menyimpan dokumen Word dengan styling baru.* Jangan ragu bereksperimen dengan parameter, dan bagikan hasil Anda di kolom komentar!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Tutorial Bayangan Bentuk Aspose.Words – Tambahkan Bayangan ke Bentuk Word dalam C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Cara Menyimpan Markdown dari Word – Panduan Python Lengkap](/words/english/python-net/document-conversion/how-to-save-markdown-from-word-complete-python-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}