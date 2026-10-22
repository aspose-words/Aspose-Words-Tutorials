---
category: general
date: 2026-08-17
description: Cara menyimpan PNG menggunakan Aspose.Words untuk Python. Pelajari cara
  menambahkan bayangan pada bentuk, menyimpan dokumen sebagai PDF, dan mengekspor
  Word ke PNG dalam satu panduan.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save png
- add shadow to shape
- save document as pdf
- export word to png
- convert word to pdf
language: id
lastmod: 2026-08-17
og_description: Cara menyimpan PNG dengan Aspose.Words. Tutorial ini menunjukkan cara
  menambahkan bayangan pada bentuk, menyimpan dokumen sebagai PDF, dan mengekspor
  Word ke PNG.
og_image_alt: Screenshot of a Word document with a rectangle shape that has a shadow,
  saved as PNG and PDF
og_title: Cara menyimpan PNG dan menambahkan bayangan pada bentuk dengan Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  headline: How to save PNG and add shadow to shape with Aspose.Words
  type: TechArticle
- description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  name: How to save PNG and add shadow to shape with Aspose.Words
  steps:
  - name: Pro tip
    text: If you need a sharper shadow, reduce `blur`. For a more pronounced offset,
      increase `distance`. The `Shadow` class also exposes `angle` and `transparency`
      for fine‑tuned control.
  - name: 'Optional: higher‑resolution PNG'
    text: '```python png_options = aw.image.PngSaveOptions() png_options.resolution
      = 300 # DPI doc.save("output/high_res_output.png", png_options) ```'
  - name: Expected output
    text: 'Running the script creates three files:'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Image export
title: Cara menyimpan PNG dan menambahkan bayangan pada bentuk dengan Aspose.Words
url: /id/python/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menyimpan PNG dan menambahkan bayangan ke shape dengan Aspose.Words

Jika Anda membutuhkan **cara menyimpan PNG** dari file Word, panduan ini memberikan solusi lengkap yang dapat dijalankan. Anda juga akan melihat cara **menambahkan bayangan ke shape**, **menyimpan dokumen sebagai PDF**, dan **mengekspor Word ke PNG** tanpa meninggalkan lingkungan Aspose.Words.

Tutorial ini mencakup semua yang diperlukan untuk mengubah dokumen Word kosong menjadi PDF dan gambar PNG, sambil menerapkan efek bayangan sederhana pada shape persegi panjang. Tidak diperlukan alat eksternal, dan kode ini bekerja dengan Aspose.Words for Python via .NET 7 atau yang lebih baru.

## Apa yang akan Anda capai

Pada akhir artikel ini Anda akan dapat:

* Membuat dokumen Word baru secara programatis.  
* Menyisipkan shape persegi panjang dan mengonfigurasi efek bayangan.  
* Menyimpan dokumen yang sama sebagai file PDF.  
* Mengekspor dokumen sebagai gambar PNG.  

Langkah‑langkah ini menjawab pertanyaan umum **cara menyimpan PNG** sekaligus menangani **menambahkan bayangan ke shape** dan **menyimpan dokumen sebagai PDF** dalam satu alur kerja.

## Prasyarat

* Python 3.9 atau lebih baru.  
* Aspose.Words for Python via .NET terinstal (`pip install aspose-words`).  
* Izin menulis ke direktori output yang Anda tentukan.  

Jika Anda belum menginstal Aspose.Words, jalankan:

```bash
pip install aspose-words
```

## Cara menyimpan PNG dengan Aspose.Words

Langkah utama pertama adalah membuat dokumen dan sebuah `DocumentBuilder`. Builder memberikan API yang fluently untuk menyisipkan konten seperti shape, tabel, atau teks.

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` mewakili seluruh file Word dalam memori. `aw.DocumentBuilder` menunjuk ke lokasi penyisipan saat ini, yang pada awalnya berada di awal bagian pertama (dan satu‑satunya).

## Tambahkan bayangan ke shape sebelum mengekspor

Sebuah shape dapat berupa objek gambar apa saja—persegi panjang, elips, atau poligon khusus. Di sini kami membuat persegi panjang 100 × 100 point dan menerapkan bayangan lembut.

```python
# Insert a rectangle shape (100x100 points)
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

# Configure a simple shadow
shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Softness of the shadow edges
shape.shadow.distance = 3.0      # Distance from the shape
shape.shadow.color = aw.Color.black
```

Mengapa mengonfigurasi bayangan sebelum menyimpan? Aspose.Words merender bayangan selama fase ekspor PDF dan PNG, sehingga efek visual tetap terjaga di kedua format output.

### Tips profesional
Jika Anda membutuhkan bayangan yang lebih tajam, kurangi `blur`. Untuk offset yang lebih jelas, tingkatkan `distance`. Kelas `Shadow` juga menyediakan `angle` dan `transparency` untuk kontrol yang lebih halus.

## Simpan dokumen sebagai PDF

Menyimpan dokumen Word sebagai PDF cukup satu baris kode setelah konten siap. Konstanta `SaveFormat.PDF` memberi tahu Aspose.Words untuk melakukan konversi.

```python
# Save the document as PDF (shadow is rendered in the output)
pdf_path = "output/output.pdf"
doc.save(pdf_path, aw.SaveFormat.PDF)
```

PDF yang dihasilkan berisi persegi panjang dengan bayangan persis seperti yang Anda definisikan. Aspose.Words menangani grafik vektor, sehingga ukuran PDF tetap wajar.

## Ekspor Word ke PNG

Ekspor ke PNG membuat gambar raster untuk setiap halaman. Secara default Aspose.Words menggunakan 96 DPI; Anda dapat meningkatkan nilai ini untuk output resolusi lebih tinggi dengan menyediakan objek `PngSaveOptions`.

```python
# Export the same document as PNG
png_path = "output/output.png"
doc.save(png_path, aw.SaveFormat.PNG)
```

Saat Anda **mengekspor Word ke PNG**, setiap halaman disimpan sebagai file PNG terpisah. Karena contoh dokumen kami hanya memiliki satu halaman, hanya satu file PNG yang muncul.

### Opsional: PNG resolusi tinggi

```python
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI
doc.save("output/high_res_output.png", png_options)
```

DPI yang lebih tinggi berguna ketika PNG akan digunakan untuk cetak atau ketika Anda memerlukan thumbnail yang tajam.

## Skrip lengkap – salin, tempel, dan jalankan

Berikut adalah skrip lengkap yang berdiri sendiri dan mengimplementasikan setiap langkah yang dijelaskan di atas. Simpan sebagai `generate_assets.py` dan jalankan dari baris perintah.

```python
import os
import aspose.words as aw

# ------------------------------------------------------------------
# 1. Prepare output folder
# ------------------------------------------------------------------
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# ------------------------------------------------------------------
# 2. Create a new blank document and a builder
# ------------------------------------------------------------------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ------------------------------------------------------------------
# 3. Insert a rectangle shape and add a shadow
# ------------------------------------------------------------------
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Soft edges
shape.shadow.distance = 3.0      # Offset from shape
shape.shadow.color = aw.Color.black

# ------------------------------------------------------------------
# 4. Save as PDF (demonstrates "save document as pdf")
# ------------------------------------------------------------------
pdf_path = os.path.join(output_dir, "output.pdf")
doc.save(pdf_path, aw.SaveFormat.PDF)

# ------------------------------------------------------------------
# 5. Export as PNG (demonstrates "how to save png")
# ------------------------------------------------------------------
png_path = os.path.join(output_dir, "output.png")
doc.save(png_path, aw.SaveFormat.PNG)

# ------------------------------------------------------------------
# 6. Optional high‑resolution PNG (demonstrates "export word to png")
# ------------------------------------------------------------------
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI for sharper output
high_res_png_path = os.path.join(output_dir, "high_res_output.png")
doc.save(high_res_png_path, png_options)

print(f"Files written to {os.path.abspath(output_dir)}")
```

### Output yang diharapkan

Menjalankan skrip akan membuat tiga file:

* `output/output.pdf` – PDF dengan persegi panjang yang memancarkan bayangan hitam.  
* `output/output.png` – PNG 96 DPI yang merender halaman yang sama.  
* `output/high_res_output.png` – PNG 300 DPI untuk kualitas lebih tinggi.

Buka salah satu file tersebut di penampil favorit Anda untuk memverifikasi bahwa bayangan muncul persis seperti yang didefinisikan.

## Pertanyaan umum dan kasus tepi

**Bagaimana jika direktori output tidak ada?**  
Skrip memanggil `os.makedirs(output_dir, exist_ok=True)`, yang secara otomatis membuat folder tersebut. Ini mencegah `FileNotFoundError` selama operasi penyimpanan.

**Apakah saya dapat menambahkan beberapa shape dengan bayangan berbeda?**  
Ya. Buat objek `Shape` tambahan, konfigurasikan properti `shadow` masing‑masing secara independen, dan sisipkan dengan `builder.insert_node(shape)` sebelum menyimpan.

**Apakah bayangan akan tetap ada saat mengonversi ke format raster lain (misalnya JPEG)?**  
Aspose.Words merender bayangan untuk semua format raster yang didukung oleh `SaveFormat`. Anda dapat mengganti `aw.SaveFormat.PNG` dengan `aw.SaveFormat.JPEG` dan bayangan tetap akan muncul.

**Bagaimana ini berbeda dari “convert word to pdf”?**  
`convert word to pdf` pada dasarnya adalah operasi yang sama yang dilakukan pada langkah 4. Panggilan `doc.save` dengan `SaveFormat.PDF` menangani konversi secara internal, mempertahankan tata letak, font, dan grafik seperti bayangan.

**Apakah ada batas ukuran shape?**  
Shape diukur dalam point (1 pt ≈ 1/72 inci). Dimensi yang sangat besar dapat meningkatkan ukuran file yang dihasilkan, tetapi Aspose.Words tidak memberlakukan batas keras. Sesuaikan argumen `width` dan `height` saat membuat `aw.Shape` sesuai kebutuhan tata letak Anda.

## Kesimpulan

Sekarang Anda tahu **cara menyimpan PNG** dari dokumen Word sekaligus belajar **menambahkan bayangan ke shape**, **menyimpan dokumen sebagai PDF**, dan **mengekspor Word ke PNG** menggunakan Aspose.Words for Python. Skrip lengkap menunjukkan pola bersih dan dapat diulang yang dapat Anda adaptasi untuk dokumen yang lebih besar, banyak halaman, atau efek grafis yang lebih kompleks.

Langkah selanjutnya dapat meliputi:

* Bereksperimen dengan nilai `ShapeType` lain (elips, awan, dll.).  
* Menggunakan `

## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik yang berhubungan erat dan membangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [How to Convert DOCX to PNG in Java – Aspose.Words](/words/english/java/document-converting/converting-documents-images/)
- [Save Word Documents as PostScript in Python Using Aspose.Words: A Comprehensive Guide](/words/english/python-net/document-operations/save-docs-as-postscript-using-aspose-words-python/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}