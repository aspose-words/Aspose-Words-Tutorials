---
category: general
date: 2026-10-16
description: Buat dokumen Word kosong, sisipkan bentuk di Word, tambahkan bayangan
  luar, dan simpan sebagai PDF menggunakan Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert shape in word
- save as pdf python
- add outer shadow shape
- create pdf with shape
language: id
lastmod: 2026-10-16
og_description: Buat dokumen Word kosong dengan bentuk bayangan luar menggunakan Aspose.Words
  untuk Python. Panduan ini menunjukkan cara menyisipkan bentuk, menerapkan bayangan,
  dan menyimpan file sebagai PDF.
og_image_alt: Screenshot of a Word document containing a rectangle shape with an outer
  shadow, saved as PDF
og_title: Buat dokumen Word kosong dengan bayangan bentuk – Panduan Python
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document, insert shape in Word, add outer shadow,
    and save as PDF using Python.
  headline: Create blank Word document with shadowed shape in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- PDF generation
- Shape styling
title: Buat dokumen Word kosong dengan bentuk berbayang di Python
url: /id/python/word-automation/create-blank-word-document-with-shadowed-shape-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen Word kosong dengan bentuk berbayang di Python

Jika Anda perlu **membuat dokumen Word kosong** dan menambahkan grafik khusus, panduan ini akan membantu Anda. Kami akan menjelaskan cara **menyisipkan bentuk di Word**, menerapkan **bentuk bayangan luar**, dan akhirnya **menyimpan sebagai PDF menggunakan Python**.

Anda akan belajar cara menyiapkan Aspose.Words untuk Python, membuat sebuah persegi panjang, menata bayangannya, dan menghasilkan PDF yang mempertahankan efek visual tersebut. Tidak diperlukan pengalaman sebelumnya dengan API Aspose, tetapi Anda sebaiknya memiliki pengetahuan dasar Python dan instalasi Python 3.10 atau yang lebih baru.

## Prasyarat

* Python 3.10 atau yang lebih baru terinstal.
* Lisensi aktif Aspose.Words untuk Python (versi percobaan gratis dapat digunakan untuk evaluasi).
* `pip` akses untuk menginstal paket `aspose-words`.
* Izin menulis ke direktori tempat PDF akan disimpan.

Anda dapat menginstal pustaka dengan satu perintah:

```bash
pip install aspose-words
```

## Membuat dokumen Word kosong – penyiapan lingkungan

Langkah pertama adalah membuat file Word kosong yang akan berfungsi sebagai kanvas untuk bentuk.

```python
import aspose.words as aw

# Initialize a new, empty document
doc = aw.Document()
# DocumentBuilder provides convenient methods for adding content
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` mewakili file Word yang sepenuhnya kosong. Dengan menggunakan `DocumentBuilder` Anda mendapatkan akses ke metode seperti `insert_shape`, yang akan kita gunakan pada langkah berikutnya.

## Menyisipkan bentuk di Word dan mengatur dimensi

Sekarang kita menambahkan sebuah persegi panjang yang nanti akan menerima bayangan luar. Ukuran dinyatakan dalam poin (1 pt ≈ 1/72 inci).

```python
# Insert a rectangle shape with a width of 200 pt and a height of 100 pt
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)
```

Pemanggilan `insert_shape` mengembalikan objek `Shape` yang dapat Anda sesuaikan lebih lanjut. Pada titik ini dokumen sudah berisi persegi panjang yang terlihat ketika dibuka di Microsoft Word.

## Menambahkan bentuk bayangan luar – menyesuaikan efek

Aspose.Words menyediakan kelas `ShadowEffect` untuk mendefinisikan properti bayangan seperti style, blur, distance, dan color.

```python
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a new shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # Choose an outer shadow
shadow.blur = 5.0                         # Softness of the shadow edges
shadow.distance = 3.0                     # Offset distance from the shape
shadow.color = aw.Color.black             # Shadow color

# Apply the shadow to the rectangle
rectangle.shadow = shadow
```

Menetapkan `style` ke `OUTER` memastikan bayangan muncul di luar batas persegi panjang, memberikan tampilan 3‑D yang halus. Anda dapat bereksperimen dengan `blur` dan `distance` untuk menghasilkan bayangan yang lebih ketat atau lebih tersebar.

## Menyimpan sebagai PDF python – menyelesaikan dokumen

Setelah menata bentuk, dokumen dapat disimpan langsung sebagai PDF. Aspose.Words menangani konversi secara internal, mempertahankan efek bayangan.

```python
output_path = "output/shape_with_shadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Saat Anda membuka `shape_with_shadow.pdf` di penampil PDF apa pun, Anda akan melihat persegi panjang dengan bayangan luar persis seperti yang muncul di Word.

## Contoh lengkap yang berfungsi

Berikut adalah skrip lengkap yang menggabungkan semua langkah. Salin ke dalam file bernama `create_word_with_shadow.py` dan jalankan.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1. Create a blank Word document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2. Insert a rectangle shape
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)

# 3. Define and apply an outer shadow
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER
shadow.blur = 5.0
shadow.distance = 3.0
shadow.color = aw.Color.black
rectangle.shadow = shadow

# 4. Save the document as PDF
pdf_path = os.path.join(output_dir, "shape_with_shadow.pdf")
doc.save(pdf_path)

print(f"PDF generated at: {pdf_path}")
```

**Output yang diharapkan**

Menjalankan skrip mencetak baris konfirmasi, misalnya:

```
PDF generated at: output/shape_with_shadow.pdf
```

Membuka PDF yang dihasilkan menampilkan satu halaman yang berisi persegi panjang 200 pt × 100 pt dengan bayangan luar hitam lembut.

## Variasi umum dan kasus tepi

* **Mengubah warna bayangan** – Ganti `aw.Color.black` dengan nilai `aw.Color` lain, seperti `aw.Color.red` atau `aw.Color.from_argb(255, 0, 120, 215)`.
* **Menggunakan bentuk yang berbeda** – Ubah `aw.drawing.ShapeType.RECTANGLE` menjadi `OVAL`, `DIAMOND`, atau nilai enum lain yang didukung.
* **Menyimpan sebagai DOCX alih-alih PDF** – Panggil `doc.save("output/shape.docx")` untuk mempertahankan format Word.
* **Banyak bentuk** – Buat bentuk tambahan dengan memanggil `builder.insert_shape` lagi; setiap bentuk dapat memiliki `ShadowEffect` masing‑masing.

**Pro tip:** Jika Anda perlu menempatkan bentuk pada lokasi tertentu, atur `rectangle.left` dan `rectangle.top` setelah penyisipan. Ini memberi Anda kontrol pixel‑perfect atas penempatan.

## Kesimpulan

Anda sekarang tahu cara **membuat dokumen Word kosong**, **menyisipkan bentuk di Word**, **menambahkan bentuk bayangan luar**, dan **menyimpan sebagai PDF menggunakan Python**. Contoh kode lengkap menunjukkan alur kerja end‑to‑end, dan penjelasan menjelaskan mengapa setiap panggilan API diperlukan.

Dari sini Anda dapat menjelajahi opsi penataan yang lebih maju, menambahkan teks di dalam bentuk, atau menggabungkan beberapa bentuk untuk membangun diagram kompleks. Bereksperimenlah dengan berbagai parameter bayangan untuk menyesuaikan bahasa visual merek Anda, dan integrasikan pendekatan ini ke dalam pipeline pembuatan dokumen yang lebih besar.

Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat bentuk persegi panjang, tambahkan bayangan & simpan PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Buat PDF dari Word – Panduan Python Lengkap dengan Aspose.Words](/words/english/python-net/document-conversion/create-pdf-from-word-complete-python-guide-with-aspose-words/)
- [Tambahkan Bayangan ke Bentuk di Word dengan Aspose.Words – Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}