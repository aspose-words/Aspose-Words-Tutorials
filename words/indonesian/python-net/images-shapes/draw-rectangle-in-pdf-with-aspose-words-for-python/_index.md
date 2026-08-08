---
category: general
date: 2026-08-07
description: Gambar persegi panjang di PDF menggunakan Aspose.Words untuk Python dan
  pelajari cara menambahkan bayangan ke bentuk, mengonfigurasi bayangan bentuk, serta
  menyimpan dokumen sebagai PDF.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle in pdf
- add shadow to shape
- save document as pdf
- configure shape shadow
language: id
lastmod: 2026-08-07
og_description: Gambar persegi panjang di PDF dengan Aspose.Words untuk Python. Tutorial
  ini menunjukkan cara menambahkan bayangan ke bentuk, mengonfigurasi bayangan bentuk,
  dan menyimpan dokumen sebagai PDF untuk pembuatan dokumen profesional.
og_image_alt: PDF page showing a rectangle shape with a visible shadow created by
  Aspose.Words for Python
og_title: Gambar persegi panjang di PDF dengan Aspose.Words untuk Python – panduan
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Draw rectangle in PDF using Aspose.Words for Python and learn how to
    add shadow to shape, configure shape shadow, and save document as PDF.
  headline: Draw rectangle in PDF with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF
- Shape
- Shadow
title: Gambar persegi panjang di PDF dengan Aspose.Words untuk Python
url: /id/python/images-shapes/draw-rectangle-in-pdf-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menggambar persegi panjang di PDF dengan Aspose.Words untuk Python

Jika Anda perlu **draw rectangle in PDF** saat bekerja dengan Python, panduan ini memberi Anda solusi lengkap yang siap‑to‑run. Anda akan melihat secara tepat cara **add shadow to shape**, mengonfigurasi bayangan tersebut, dan akhirnya **save document as PDF** untuk distribusi atau pengarsipan.

Membuat persegi panjang berbayang adalah kebutuhan umum untuk laporan, faktur, atau anotasi visual. Pada akhir tutorial ini Anda akan memiliki satu skrip yang menghasilkan PDF berisi persegi panjang dengan bayangan realistis, dan Anda akan memahami cara menyesuaikan ukuran, warna, dan offset agar sesuai dengan desain apa pun.

## Prasyarat

* Python 3.8+ terinstal.
* Paket Aspose.Words untuk Python via .NET (`aspose-words`) – instal dengan:

```bash
pip install aspose-words
```

* Izin menulis ke folder tempat Anda ingin menyimpan PDF.

Tidak ada pustaka tambahan yang diperlukan; Aspose.Words menangani pembuatan shape, konfigurasi bayangan, dan ekspor PDF secara internal.

## Langkah 1: Membuat dokumen kosong baru (draw rectangle in PDF – initialize)

Langkah pertama adalah menginstansiasi objek `Document`. Objek ini mewakili seluruh file PDF dan menyediakan kontainer untuk section, paragraph, dan shape.

```python
import aspose.words as aw

# Create an empty Word document – it will become a PDF later
doc = aw.Document()
```

**Mengapa ini penting:** Aspose.Words memperlakukan pembuatan PDF sebagai konversi dari model dokumen Word, jadi kita memulai dengan `Document` meskipun output akhir adalah PDF.

## Langkah 2: Menyisipkan shape persegi panjang ke dalam body dokumen

Persegi panjang adalah `ShapeType` tertentu. Kami menambahkannya ke body section pertama, yang secara otomatis membuat halaman baru saat disimpan sebagai PDF.

```python
# Append a rectangle shape to the first section's body
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Set the rectangle's dimensions (points = 1/72 inch)
rectangle.width = 200   # 200 pt ≈ 2.78 in
rectangle.height = 100  # 100 pt ≈ 1.39 in

# Optional: give the shape some visible text
rectangle.text = "Shadow demo"
```

**Penjelasan:** Properti `width` dan `height` mengontrol ukuran visual shape dalam PDF. Menambahkan teks membuat persegi panjang lebih mudah diverifikasi selama pengujian.

## Langkah 3: Menambahkan bayangan ke shape – mengaktifkan dan menyesuaikan

Sekarang kami mengaktifkan efek bayangan dan menyesuaikan tampilannya secara halus. Di sinilah kata kunci **add shadow to shape** berperan.

```python
# Access the shape's shadow effect object
shadow = rectangle.shadow_effect

# Make the shadow visible
shadow.visible = True

# Configure blur radius (pt) – higher values produce a softer edge
shadow.blur = 8

# Set the distance (offset) from the shape in points
shadow.distance = 5

# Define the direction of the shadow in degrees (0 = right, 90 = down)
shadow.angle = 45

# Choose a shadow color – black works for most documents
shadow.color = aw.drawing.Color.black
```

**Mengapa mengonfigurasi bayangan shape?** Menyesuaikan `blur`, `distance`, dan `angle` memungkinkan Anda mensimulasikan pencahayaan realistis, yang meningkatkan keterbacaan dan hierarki visual dalam PDF yang dihasilkan.

## Langkah 4: Menyimpan dokumen sebagai PDF – output akhir

Dengan persegi panjang dan bayangannya yang telah didefinisikan, langkah terakhir adalah mengekspor dokumen Word ke PDF. Ini memenuhi persyaratan **save document as pdf**.

```python
# Define the output path – replace YOUR_DIRECTORY with an actual folder
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)
print(f"PDF saved to {output_path}")
```

Saat Anda membuka `shadow_rectangle.pdf`, Anda akan melihat satu halaman yang berisi persegi panjang berpinggir abu‑abu berjudul “Shadow demo” dengan bayangan diagonal yang tajam.

### Output yang Diharapkan

* File PDF bernama `shadow_rectangle.pdf`.
* Satu halaman dengan persegi panjang 200 pt × 100 pt.
* Bayangan yang terlihat dengan offset 5 pt pada sudut 45°, blur sebesar 8 pt.

## Langkah 5: Menjelajahi variasi dan kasus tepi (opsional)

Berikut adalah penyesuaian umum yang mungkin Anda perlukan dalam proyek dunia nyata:

| Variasi | Potongan kode | Kapan digunakan |
|-----------|--------------|-------------|
| **Berbeda tipe shape** (mis., ellipse) | `aw.drawing.ShapeType.OVAL` instead of `RECTANGLE` | Untuk grafik bulat atau lencana |
| **Warna bayangan khusus** | `shadow.color = aw.drawing.Color.from_argb(255, 100, 100, 100)` | Saat bayangan abu‑abu atau khusus merek diperlukan |
| **Beberapa shape** | Repeat the shape‑creation block and adjust `left`/`top` properties | Untuk membangun diagram kompleks |
| **Tanpa teks di dalam shape** | Omit `rectangle.text = "..."` | Saat shape hanya dekoratif |
| **Output DPI lebih tinggi** | `doc.save(output_path, aw.SaveFormat.PDF, aw.PdfSaveOptions())` with `PdfSaveOptions` set for image quality | Untuk PDF siap cetak |

**Pro tip:** Selalu set `shadow.visible = True` sebelum menyesuaikan properti lain; jika tidak, perubahan akan diabaikan secara diam-diam.

## Skrip lengkap – salin, tempel, dan jalankan

```python
import aspose.words as aw

# 1️⃣ Create a new blank document
doc = aw.Document()

# 2️⃣ Add a rectangle shape
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
rectangle.width = 200          # width in points
rectangle.height = 100         # height in points
rectangle.text = "Shadow demo"

# 3️⃣ Configure a visible shadow effect
shadow = rectangle.shadow_effect
shadow.visible = True
shadow.blur = 8                # blur radius (pt)
shadow.distance = 5            # offset distance (pt)
shadow.angle = 45              # direction (degrees)
shadow.color = aw.drawing.Color.black

# 4️⃣ Save the document as a PDF
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)

print(f"PDF successfully created at: {output_path}")
```

Jalankan skrip dari terminal atau IDE Anda. Ganti `YOUR_DIRECTORY` dengan path folder yang nyata, seperti `"/tmp"` atau `"C:\\Users\\Me\\Documents"`.

## Kesimpulan

Anda sekarang tahu cara **draw rectangle in PDF** menggunakan Aspose.Words untuk Python, **add shadow to shape**, **configure shape shadow**, dan **save document as PDF**. Contoh lengkap ini menunjukkan setiap langkah dari pembuatan dokumen hingga ekspor akhir, dan variasi opsional menunjukkan cara menyesuaikan kode untuk skenario yang lebih kompleks.

Selanjutnya, Anda dapat menjelajahi:

* Menambahkan tipe shape lain (`ShapeType.LINE`, `ShapeType.ELLIPSE`).
* Menerapkan isian gradien atau border untuk meningkatkan daya tarik visual.
* Menggunakan `PdfSaveOptions` untuk menyematkan font atau mengontrol kompresi gambar.

Silakan bereksperimen dengan parameter untuk menyesuaikan merek atau panduan desain Anda. Selamat menulis skrip PDF!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Optimize PDF Bookmarks Using Aspose.Words for Python](/words/english/python-net/performance-optimization/optimize-pdf-bookmarks-aspose-words-python/)
- [Optimize Pdf Loading Python Aspose Words Skip Images](/words/hindi/python-net/performance-optimization/optimize-pdf-loading-python-aspose-words-skip-images/)
- [Aspose Words Python Pdf Manipulation](/words/hongkong/python-net/document-operations/aspose-words-python-pdf-manipulation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}