---
category: general
date: 2026-07-20
description: Buat dokumen Word kosong dengan Aspose.Words dan tambahkan bayangan pada
  bentuk. Pelajari cara mengubah opasitas dan transparansi bayangan dalam beberapa
  langkah saja.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add shadow to shape
- add shadow effect
- change shadow transparency
- change shadow opacity
language: id
lastmod: 2026-07-20
og_description: Buat dokumen Word kosong menggunakan Aspose.Words dan tambahkan efek
  bayangan pada sebuah bentuk. Ubah opasitas dan transparansi bayangan dengan contoh
  kode yang jelas.
og_image_alt: Screenshot showing a Word document with a shape that has a semi‑transparent
  shadow
og_title: Buat Dokumen Word Kosong dan Tambahkan Bayangan pada Bentuk – Panduan Langkah
  demi Langkah
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Create blank Word document with Aspose.Words and add shadow to shape.
    Learn how to change shadow opacity and transparency in just a few steps.
  headline: Create Blank Word Document and Add Shadow to Shape – Full Tutorial
  type: TechArticle
- description: Create blank Word document with Aspose.Words and add shadow to shape.
    Learn how to change shadow opacity and transparency in just a few steps.
  name: Create Blank Word Document and Add Shadow to Shape – Full Tutorial
  steps:
  - name: Expected Output
    text: When you open **ShadowedShape.docx**, you should see a rectangle with a
      gray, semi‑transparent shadow that has a gentle blur. The shadow will be offset
      slightly down and to the right, giving the illusion that the shape is lifted
      off the page.
  - name: What if the document already contains multiple shapes?
    text: 'The current script grabs the *first* shape (`index 0`). To target a specific
      shape, change the index or iterate over all shapes:'
  - name: Can I change the shadow color?
    text: 'Absolutely. Shadow color is another property:'
  - name: How do I make the shadow offset differently?
    text: 'Adjust `distance_x` and `distance_y`:'
  - name: Does this work with older Word versions?
    text: Aspose.Words writes the modern OOXML format (`.docx`). Word 2007+ can open
      it without issues. For legacy `.doc` files, call `doc.save("file.doc", aw.SaveFormat.DOC)`—the
      shadow properties will still be preserved.
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
- Word Shapes
title: Buat Dokumen Word Kosong dan Tambahkan Bayangan pada Bentuk – Tutorial Lengkap
url: /id/python/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-tuto/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat Dokumen Word Kosong dan Tambahkan Bayangan ke Bentuk – Tutorial Lengkap

Pernah membutuhkan untuk **create blank Word document** dan kemudian membuat sebuah bentuk menonjol dengan bayangan halus? Anda bukan satu-satunya. Dalam banyak laporan, selebaran, atau dasbor internal, sedikit kedalaman dapat mengubah persegi panjang datar menjadi isyarat visual yang menarik perhatian.  

Dalam panduan ini kami akan menjelaskan cara membuat file Word baru dengan Aspose.Words untuk Python, mengambil bentuk pertama, dan kemudian **add shadow to shape** sambil menyesuaikan opacity dan blur-nya. Pada akhir tutorial Anda akan memiliki dokumen yang tampak halus—tanpa perlu mengutak‑atik secara manual.

> **What you’ll get** – sebuah skrip lengkap yang dapat dijalankan, penjelasan tentang *mengapa* setiap baris penting, dan tip untuk menangani dokumen yang belum berisi bentuk.

## Prasyarat

- Python 3.8+ terinstal (versi terbaru apa pun dapat digunakan)
- Aspose.Words untuk Python via `pip install aspose-words`
- Familiaritas dasar dengan Python dan konsep “shape” di Word (misalnya text box, picture, atau auto‑shape)

Tidak diperlukan pustaka lain; kode ini berdiri sendiri.

## Langkah 1: Buat Dokumen Word Kosong dengan Aspose.Words

Pertama-tama, kita membutuhkan kanvas bersih. Aspose.Words membuat ini mudah—cukup buat objek `Document`.

```python
import aspose.words as aw

# Step 1: Create a new blank document
doc = aw.Document()
print("✅ Blank Word document created.")
```

*Mengapa ini penting*: Kelas `Document` adalah titik masuk untuk setiap operasi. Memulai dengan dokumen baru menjamin tidak ada kejutan format tersembunyi di kemudian hari.

## Langkah 2: Sisipkan Bentuk Contoh (agar ada yang dapat diberi bayangan)

Jika Anda menjalankan skrip pada file kosong, Anda akan menemui masalah saat mencoba mengambil sebuah shape—karena tidak ada shape. Mari tambahkan persegi panjang sederhana sehingga langkah selanjutnya memiliki target.

```python
# Step 2: Add a rectangle shape to the first page
builder = aw.DocumentBuilder(doc)
builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
print("🔲 Rectangle shape inserted.")
```

> **Pro tip**: Sesuaikan nilai lebar/tinggi (200, 100) agar sesuai dengan kebutuhan desain Anda. Bentuk yang lebih besar menampilkan bayangan lebih jelas.

## Langkah 3: Ambil Bentuk Pertama dalam Dokumen

Sekarang kita memiliki shape, kita dapat dengan aman mengambilnya. Metode `get_child` menelusuri pohon node dan mengembalikan node pertama dari tipe yang diminta.

```python
# Step 3: Retrieve the first shape (index 0) – true = deep search
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

if shape is None:
    raise ValueError("No shape found in the document.")
print(f"🕵️ Retrieved shape of type: {shape.shape_type}")
```

*Mengapa kami memeriksa `None`*: Dalam skenario dunia nyata dokumen mungkin dihasilkan di tempat lain, dan shape yang hilang akan menyebabkan `AttributeError` yang membingungkan. Melempar pengecualian yang jelas menghemat waktu debugging.

## Langkah 4: Tambahkan Efek Bayangan – Ubah Opacity Bayangan

Bayangan bukan sekadar hiasan visual; ia dapat menyampaikan hierarki. Mari buat semi‑transparent dengan mengatur opacity menjadi 75 %.

```python
# Step 4: Set shadow opacity (0.0 = fully transparent, 1.0 = fully opaque)
shape.shadow.opacity = 0.75
print(f"🌫️ Shadow opacity set to {shape.shadow.opacity}")
```

**Memahami opacity**: Nilainya adalah float antara 0 dan 1. Angka yang lebih rendah membuat bayangan memudar ke latar belakang, angka yang lebih tinggi membuatnya menonjol. Untuk kebanyakan dokumen bergaya UI, 0.5–0.8 terlihat alami.

## Langkah 5: Definisikan Blur Bayangan – Ubah Transparansi Bayangan

Radius blur mengontrol seberapa lembut tepi bayangan muncul. Radius yang lebih besar menghasilkan fade yang lebih halus, meniru difusi cahaya alami.

```python
# Step 5: Define blur radius (in points) for a softer edge
shape.shadow.blur_radius = 8.0
print(f"🔍 Blur radius set to {shape.shadow.blur_radius} points")
```

*Mengapa blur penting*: Bayangan dengan tepi keras dapat terlihat murahan, sementara blur halus menambah kedalaman tanpa membebani konten.

## Langkah 6: Simpan Dokumen dan Verifikasi Hasil

Akhirnya, kami menulis dokumen ke disk. Buka file `.docx` yang dihasilkan di Word untuk melihat persegi panjang dengan bayangan barunya.

```python
output_path = "ShadowedShape.docx"
doc.save(output_path)
print(f"💾 Document saved as '{output_path}'. Open it in Word to see the effect.")
```

### Output yang Diharapkan

Saat Anda membuka **ShadowedShape.docx**, Anda akan melihat persegi panjang dengan bayangan abu‑abu, semi‑transparent yang memiliki blur lembut. Bayangan akan sedikit bergeser ke bawah dan ke kanan, memberi ilusi bahwa shape terangkat dari halaman.

## Kasus Tepi & Pertanyaan Umum

### Bagaimana jika dokumen sudah berisi banyak shape?

Skrip saat ini mengambil shape *pertama* (`index 0`). Untuk menargetkan shape tertentu, ubah indeks atau iterasi semua shape:

```python
for i in range(doc.get_child_nodes(aw.NodeType.SHAPE, True).count):
    shp = doc.get_child(aw.NodeType.SHAPE, i, True)
    # Apply shadow settings to each shape
    shp.shadow.opacity = 0.6
    shp.shadow.blur_radius = 5.0
```

### Bisakah saya mengubah warna bayangan?

Tentu saja. Warna bayangan adalah properti lain:

```python
shape.shadow.color = aw.drawing.Color.black
```

### Bagaimana cara mengubah offset bayangan secara berbeda?

Sesuaikan `distance_x` dan `distance_y`:

```python
shape.shadow.distance_x = 5   # shift right
shape.shadow.distance_y = 5   # shift down
```

### Apakah ini bekerja dengan versi Word yang lebih lama?

Aspose.Words menulis format OOXML modern (`.docx`). Word 2007+ dapat membuka tanpa masalah. Untuk file `.doc` lama, panggil `doc.save("file.doc", aw.SaveFormat.DOC)`—properti bayangan tetap dipertahankan.

## Ringkasan Skrip Lengkap

Menggabungkan semuanya, berikut contoh lengkap yang siap dijalankan:

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
print("✅ Blank Word document created.")

# Insert a rectangle shape (so we have something to shadow)
builder = aw.DocumentBuilder(doc)
builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
print("🔲 Rectangle shape inserted.")

# Retrieve the first shape in the document
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
if shape is None:
    raise ValueError("No shape found in the document.")
print(f"🕵️ Retrieved shape of type: {shape.shape_type}")

# Add shadow effect – change opacity
shape.shadow.opacity = 0.75
print(f"🌫️ Shadow opacity set to {shape.shadow.opacity}")

# Change shadow transparency – define blur radius
shape.shadow.blur_radius = 8.0
print(f"🔍 Blur radius set to {shape.shadow.blur_radius} points")

# Optional: tweak color and offset
shape.shadow.color = aw.drawing.Color.gray
shape.shadow.distance_x = 4
shape.shadow.distance_y = 4

# Save the document
output_path = "ShadowedShape.docx"
doc.save(output_path)
print(f"💾 Document saved as '{output_path}'. Open it in Word to see the effect.")
```

Jalankan skrip ini, buka file yang dihasilkan, dan Anda akan melihat shape dibalut bayangan yang elegan—tepat apa yang dibutuhkan laporan yang rapi.

## Kesimpulan

Anda kini tahu **how to create blank Word document** dengan Aspose.Words, menyisipkan shape, dan **add shadow to shape** sambil menguasai *change shadow opacity* dan *change shadow transparency*. Langkah-langkahnya sederhana, namun hasil visualnya signifikan.  

Selanjutnya, Anda mungkin ingin menjelajahi **add shadow effect** pada gambar, bereksperimen dengan nilai `blur_radius` yang berbeda, atau menggabungkan beberapa shape menjadi satu grafik komposit. Untuk pendalaman, lihat dokumentasi Aspose pada [Shape Formatting](https://docs.aspose.com/words/python-net/shape/) dan panduan lebih luas [Document Automation](https://docs.aspose.com/words/python-net/).

Ada modifikasi yang Anda coba? Tinggalkan komentar di bawah—berbagi tip dunia nyata membuat komunitas lebih kuat. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Dokumen Word Kosong dengan Bentuk Persegi Panjang Berbayangan – Panduan Langkah‑ demi‑Langkah](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Tutorial Bayangan Shape Aspose.Words – Tambahkan Bayangan ke Shape Word dalam C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Buat Bentuk Persegi Panjang di Word dengan Aspose.Words – Panduan Langkah‑ demi‑Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}