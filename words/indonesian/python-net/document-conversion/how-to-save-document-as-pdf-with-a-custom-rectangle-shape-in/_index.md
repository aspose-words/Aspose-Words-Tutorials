---
category: general
date: 2026-10-07
description: Pelajari cara menyimpan dokumen sebagai PDF sambil menambahkan bentuk
  persegi panjang dan bayangan khusus menggunakan Aspose.Words untuk Python. Kode
  langkah demi langkah disertakan.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as pdf
- add rectangle shape
- export word to pdf
- set rectangle dimensions
- draw rectangle word
language: id
lastmod: 2026-10-07
og_description: Simpan dokumen sebagai PDF dengan bentuk persegi panjang khusus menggunakan
  Aspose.Words untuk Python. Ikuti contoh lengkap untuk menggambar, memberi gaya,
  dan mengekspor Word ke PDF.
og_image_alt: Screenshot of the generated PDF showing the rectangle shape after save
  document as pdf
og_title: Simpan dokumen sebagai PDF dengan bentuk persegi panjang – panduan lengkap
  Python
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  headline: How to save document as PDF with a custom rectangle shape in Python
  type: TechArticle
- description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  name: How to save document as PDF with a custom rectangle shape in Python
  steps:
  - name: Initialize a new blank document
    text: '```python import aspose.words as aw'
  - name: Add rectangle shape to the document
    text: '```python # Create a rectangle shape and attach it to the document. rectangle
      = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)'
  - name: Set rectangle dimensions
    text: '```python # Define width and height in points (1 point = 1/72 inch). rectangle.width
      = 200 # 200 points ≈ 2.78 inches rectangle.height = 100 # 100 points ≈ 1.39
      inches ```'
  - name: (Optional) Apply a visible custom shadow
    text: '```python shadow = rectangle.shadow_format shadow.visible = True # Show
      the shadow shadow.blur = 5.0 # Softness of the shadow edge shadow.distance =
      3.0 # How far the shadow is offset shadow.angle = 45 # Direction in degrees
      shadow.color = aw.drawing.Color.black ```'
  - name: Save document as PDF
    text: '```python output_path = "output/shadow_rectangle.pdf" document.save(output_path)
      print(f"PDF saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Word automation
title: Cara menyimpan dokumen sebagai PDF dengan bentuk persegi panjang khusus di
  Python
url: /id/python/document-conversion/how-to-save-document-as-pdf-with-a-custom-rectangle-shape-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menyimpan dokumen sebagai PDF dengan bentuk persegi panjang khusus di Python

Jika Anda perlu **save document as PDF** sambil menambahkan grafik khusus, panduan ini akan menunjukkan caranya. Kami akan melangkah melalui pembuatan file Word kosong, **drawing a rectangle shape**, mengatur ukurannya, menerapkan bayangan yang terlihat, dan akhirnya **export Word to PDF** menggunakan pustaka Aspose.Words untuk Python.

Anda akan selesai dengan PDF yang berisi persegi panjang yang diposisikan dengan sempurna, siap untuk laporan, faktur, atau skenario otomatisasi dokumen apa pun. Tidak diperlukan alat eksternal—hanya Python dan paket Aspose.Words.

## Apa yang Anda perlukan

| Persyaratan | Mengapa penting |
|-------------|-----------------|
| Python 3.8+ | API Aspose.Words untuk Python menargetkan interpreter modern. |
| `aspose-words` package (`pip install aspose-words`) | Menyediakan namespace `aw` yang digunakan dalam contoh kode. |
| Basic familiarity with Python and object‑oriented programming | Tutorial ini memanipulasi objek seperti `Document` dan `Shape`. |
| Write permission to a folder where the PDF will be saved | Langkah `save document as pdf` menulis file ke disk. |

> **Tip Pro:** Gunakan lingkungan virtual (`python -m venv venv`) untuk menjaga dependensi terisolasi.

## Cara menyimpan dokumen sebagai PDF dengan bentuk persegi panjang

Berikut adalah contoh lengkap yang dapat dijalankan. Setiap langkah dijelaskan sehingga Anda memahami **mengapa** kami melakukan aksi tersebut, bukan hanya **apa** yang dilakukan kode.

### Langkah 1: Inisialisasi dokumen kosong baru

```python
import aspose.words as aw

# Create an empty Word document – this is the canvas for our shape.
document = aw.Document()
```

Membuat objek `Document` baru memberikan Anda koleksi halaman yang bersih. Anda juga dapat memuat *.docx* yang ada jika ingin **export Word to PDF** nanti, tetapi memulai dengan kosong membuat contoh tetap fokus.

### Langkah 2: Tambahkan bentuk persegi panjang ke dokumen

```python
# Create a rectangle shape and attach it to the document.
rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

# The shape must be placed inside a paragraph before it appears.
paragraph = document.first_section.body.first_paragraph
paragraph.append_child(rectangle)
```

Langkah `add rectangle shape` menggunakan `ShapeType.RECTANGLE`. Dengan menambahkan bentuk ke paragraf, Aspose.Words mengetahui di mana menampilkannya dalam PDF akhir.

### Langkah 3: Atur dimensi persegi panjang

```python
# Define width and height in points (1 point = 1/72 inch).
rectangle.width = 200   # 200 points ≈ 2.78 inches
rectangle.height = 100  # 100 points ≈ 1.39 inches
```

Menetapkan **rectangle dimensions** secara eksplisit memastikan bentuk terlihat konsisten di semua platform. Anda juga dapat menggunakan pembantu `convert_to_inches` jika lebih suka satuan imperial.

### Langkah 4: (Opsional) Terapkan bayangan khusus yang terlihat

```python
shadow = rectangle.shadow_format
shadow.visible = True          # Show the shadow
shadow.blur = 5.0              # Softness of the shadow edge
shadow.distance = 3.0          # How far the shadow is offset
shadow.angle = 45              # Direction in degrees
shadow.color = aw.drawing.Color.black
```

Bayangan membuat persegi panjang menonjol dalam PDF. Flag `shadow.visible` diperlukan; tanpa itu properti lain tidak berpengaruh.

### Langkah 5: Simpan dokumen sebagai PDF

```python
output_path = "output/shadow_rectangle.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Memanggil `document.save` dengan ekstensi **.pdf** secara otomatis **save document as pdf** menggunakan renderer PDF bawaan Aspose.Words. Tidak diperlukan langkah konversi tambahan, itulah mengapa metode ini direkomendasikan untuk **export Word to PDF**.

> **Mengapa ini berhasil:** Aspose.Words menulis tata letak dokumen, termasuk persegi panjang dan bayangannya, langsung ke aliran PDF. Proses ini tanpa kehilangan data dan mempertahankan kualitas vektor.

## Kode sumber lengkap (skrip tunggal)

```python
import aspose.words as aw

def create_pdf_with_rectangle(output_path: str):
    """
    Creates a PDF that contains a single rectangle shape with a custom shadow.
    The function demonstrates:
    • add rectangle shape
    • set rectangle dimensions
    • export Word to PDF (save document as pdf)
    """
    # 1️⃣ Create a new blank document
    document = aw.Document()

    # 2️⃣ Insert a rectangle shape
    rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

    # 3️⃣ Set the shape's size
    rectangle.width = 200   # points
    rectangle.height = 100  # points

    # 4️⃣ Configure a visible shadow
    shadow = rectangle.shadow_format
    shadow.visible = True
    shadow.blur = 5.0
    shadow.distance = 3.0
    shadow.angle = 45
    shadow.color = aw.drawing.Color.black

    # 5️⃣ Add shape to the first paragraph
    paragraph = document.first_section.body.first_paragraph
    paragraph.append_child(rectangle)

    # 6️⃣ Save the document as PDF
    document.save(output_path)
    print(f"PDF successfully saved to: {output_path}")

if __name__ == "__main__":
    create_pdf_with_rectangle("output/shadow_rectangle.pdf")
```

Menjalankan skrip ini menghasilkan `shadow_rectangle.pdf` yang terlihat seperti ini:

![Diagram PDF yang dihasilkan menampilkan bentuk persegi panjang setelah save document as pdf](placeholder-image.png)

*PDF berisi satu halaman dengan persegi panjang berbayangan hitam yang terpusat di dokumen.*

## Pertanyaan umum dan kasus tepi

| Pertanyaan | Jawaban |
|------------|---------|
| **Bisakah saya menempatkan persegi panjang pada lokasi tertentu?** | Ya. Atur `rectangle.left` dan `rectangle.top` (dalam poin) sebelum menyimpan. |
| **Bagaimana jika saya membutuhkan banyak bentuk?** | Buat objek `Shape` tambahan, konfigurasikan masing‑masing, dan tambahkan ke paragraf yang sama atau berbeda. |
| **Apakah bayangan memengaruhi ukuran PDF?** | Hanya sedikit; bayangan disimpan sebagai metadata vektor, bukan gambar raster. |
| **Bisakah saya menggunakan ini untuk mengonversi file *.docx* yang ada?** | Tentu saja. Ganti `aw.Document()` dengan `aw.Document("input.docx")` dan langkah‑langkah lainnya tetap tidak berubah. |
| **Apakah ada cara mengubah warna isi persegi panjang?** | Atur `rectangle.fill_color = aw.drawing.Color.light_blue` (atau `Color` apa pun yang Anda inginkan). |

## Langkah selanjutnya

Sekarang Anda tahu cara **save document as PDF** dengan persegi panjang khusus, Anda mungkin ingin menjelajahi:

* **Export Word to PDF** dengan header, footer, dan nomor halaman.  
* **Add other drawing objects** (`Ellipse`, `Polygon`) menggunakan kelas `Shape` yang sama.  
* **Batch process** folder file Word, menerapkan overlay persegi panjang yang sama pada masing‑masing.  

Ekstensi ini mengikuti pola yang sama: buat bentuk, konfigurasikan propertinya, dan **save document as pdf**.

---

**Ringkasan:** Tutorial ini menunjukkan cara **save document as PDF** sambil **add rectangle shape**, **set rectangle dimensions**, dan menerapkan bayangan khusus menggunakan Aspose.Words untuk Python. Skrip lengkap siap untuk disalin, dijalankan, dan disesuaikan dengan pipeline otomatisasi dokumen Anda sendiri. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat bentuk persegi panjang, tambahkan bayangan & simpan PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Tambahkan persegi panjang ke PDF dengan Aspose.Words – Panduan Langkah‑per‑Langkah](/words/english/python-net/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/)
- [Simpan Dokumen sebagai PDF dengan Aspose.Words – Panduan Lengkap C#](/words/english/net/programming-with-pdfsaveoptions/save-document-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}