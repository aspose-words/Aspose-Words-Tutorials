---
category: general
date: 2026-06-27
description: Pelajari cara menyisipkan bentuk persegi panjang dalam Python menggunakan
  Aspose.Words, mengubah warna bayangan, menambahkan bayangan luar, dan menerapkan
  efek bayangan pada bentuk—semua dalam satu tutorial.
draft: false
keywords:
- how to insert rectangle shape
- how to change shadow color
- how to add outer shadow
- apply shadow effect to shape
language: id
og_description: Kuasi cara menyisipkan bentuk persegi panjang di Python, mengubah
  warna bayangannya, menambahkan bayangan luar, dan menerapkan efek bayangan pada
  bentuk dengan Aspose.Words.
og_title: Cara Menyisipkan Bentuk Persegi Panjang di Python – Tutorial Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  headline: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  name: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: Pro tip
    text: If you need the rectangle positioned at a specific location, use `builder.move_to`
      before inserting, or adjust `rectangle.left` and `rectangle.top` after creation.
  - name: Edge case
    text: If you forget to set `shadow.opacity`, the default is fully opaque, which
      can make the shadow look like a solid shape. Always pair a color change with
      an appropriate opacity level.
  - name: Common pitfalls
    text: '- **Missing directory:** `doc.save` will raise an error if the folder doesn’t
      exist. Create it first or use `os.makedirs`. - **Version mismatch:** The shadow
      API requires Aspose.Words 22.9+; older versions silently ignore shadow settings.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: Cara Menyisipkan Bentuk Persegi Panjang di Python – Panduan Lengkap Aspose.Words
url: /id/python/images-shapes/how-to-insert-rectangle-shape-in-python-complete-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menyisipkan Bentuk Persegi Panjang di Python – Panduan Lengkap Aspose.Words

Pernah bertanya-tanya **bagaimana cara menyisipkan bentuk persegi panjang** ke dalam dokumen Word menggunakan Python? Anda bukan satu-satunya—banyak pengembang mengalami kendala ini saat mengotomatisasi laporan atau membuat templat. Kabar baiknya, Aspose.Words membuatnya sangat mudah, dan dalam tutorial ini kami akan membahas seluruh proses, mulai dari menggambar persegi panjang hingga memberikan bayangan luar yang halus.

Kami juga akan membahas **cara mengubah warna bayangan**, **cara menambahkan bayangan luar**, dan langkah akhir **menerapkan efek bayangan ke bentuk**. Pada akhir tutorial, Anda akan memiliki persegi panjang yang sepenuhnya bergaya yang dapat Anda sisipkan ke dalam file .docx apa pun secara programatis.

## Prasyarat

- Python 3.8+ terpasang di mesin Anda  
- Aspose.Words untuk Python via `pip install aspose-words`  
- Familiaritas dasar dengan skrip Python (tidak memerlukan pengetahuan mendalam tentang Word‑API)

Jika Anda sudah memiliki semuanya, bagus—mari kita mulai. Jika belum, dapatkan dulu pustaka tersebut; sisanya panduan mengasumsikan impor berhasil tanpa masalah.

## Cara Menyisipkan Bentuk Persegi Panjang dengan Aspose.Words untuk Python

Langkah pertama persis seperti yang dijanjikan oleh kata kunci utama: **bagaimana cara menyisipkan bentuk persegi panjang**. Kami akan membuat dokumen baru, memanggil `DocumentBuilder`, dan menempatkan persegi panjang pada halaman.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a fresh document and a builder to add content
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle shape of 200x100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Optional: give the rectangle a light fill so the shadow is visible
rectangle.fill_color = aw.drawing.Color.light_blue
```

> **Mengapa ini penting:** Pemanggilan `insert_shape` adalah inti dari *bagaimana cara menyisipkan bentuk persegi panjang*. Ia mengembalikan objek `Shape` yang dapat Anda manipulasi kemudian—ukuran, posisi, isi, batas, apa saja. Perhatikan juga kami menetapkan `fill_color`; tanpa itu bayangan mungkin menyatu dengan halaman putih, sehingga sulit terlihat.

### Tips Pro
Jika Anda memerlukan persegi panjang ditempatkan pada lokasi tertentu, gunakan `builder.move_to` sebelum menyisipkan, atau sesuaikan `rectangle.left` dan `rectangle.top` setelah dibuat.

## Mengubah Warna Bayangan Bentuk

Sekarang persegi panjang sudah berada dalam dokumen, mari jawab **cara mengubah warna bayangan**. Aspose.Words menyediakan objek `ShadowEffect` di mana Anda dapat mengatur properti `color` ke nilai RGB apa pun.

```python
# Create a shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # we’ll also cover outer shadow later
shadow.blur_radius = 8.0                  # smooth edges
shadow.distance = 6.0                     # how far the shadow sits from the shape
shadow.direction = 45                     # angle in degrees
shadow.opacity = 0.6                      # semi‑transparent

# Change the shadow color to a deep gray instead of black
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)

# Apply the shadow to our rectangle
rectangle.shadow = shadow
```

> **Mengapa Anda menginginkannya:** Bayangan hitam pekat dapat terlalu keras, terutama pada dokumen berwarna terang. Menyesuaikan warna memungkinkan Anda mencocokkan merek perusahaan atau sekadar mencapai efek visual yang lebih lembut.

### Kasus Tepi
Jika Anda lupa mengatur `shadow.opacity`, nilai defaultnya sepenuhnya tidak tembus, yang dapat membuat bayangan terlihat seperti bentuk padat. Selalu padukan perubahan warna dengan tingkat opasitas yang sesuai.

## Menambahkan Efek Bayangan Luar

Pertanyaan berikutnya yang sering diajukan adalah **cara menambahkan bayangan luar**. Flag `ShadowStyle.OUTER` memberi tahu Aspose.Words untuk merender bayangan di luar kontur bentuk, bukan di dalamnya.

Potongan kode di atas sudah menggunakan `ShadowStyle.OUTER`, tetapi mari kita pisahkan pengaturan ini untuk kejelasan:

```python
# Ensure the shadow style is outer
shadow.style = ShadowStyle.OUTER
```

Jika Anda beralih ke `ShadowStyle.INNER`, bayangan akan muncul *di dalam* persegi panjang, yang berguna untuk efek emboss. Untuk sebagian besar skenario desain dokumen, gaya luar memberikan tampilan bayangan jatuh yang alami.

## Menerapkan Efek Bayangan ke Bentuk Anda

Kami sudah **menerapkan efek bayangan ke bentuk** dengan menetapkan `rectangle.shadow = shadow`. Mari gabungkan semuanya dan simpan dokumen, memastikan efek tersebut tetap ada.

```python
# Save the document – choose a folder you have write access to
output_path = "output/RectangleWithShadow.docx"
doc.save(output_path)

print(f"Document saved to {output_path}. Open it to see the rectangle with its outer shadow.")
```

Saat Anda membuka `RectangleWithShadow.docx` di Microsoft Word, Anda akan melihat persegi panjang berwarna biru muda dengan bayangan luar abu-abu halus yang terlempar pada sudut 45°. Bayangan akan sedikit kabur dan bergeser, persis seperti yang kami konfigurasikan.

### Kesalahan Umum
- **Direktori tidak ada:** `doc.save` akan menghasilkan error jika folder tidak ada. Buat dulu atau gunakan `os.makedirs`.
- **Versi tidak cocok:** API bayangan memerlukan Aspose.Words 22.9+; versi lama akan mengabaikan pengaturan bayangan secara diam-diam.

## Contoh Lengkap yang Berfungsi

Berikut adalah skrip lengkap yang siap dijalankan yang menggabungkan semua langkah. Salin‑tempel ke dalam file bernama `rectangle_shadow.py` dan jalankan dengan `python rectangle_shadow.py`.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Create a new document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2️⃣ Insert the rectangle shape (how to insert rectangle shape)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle.fill_color = aw.drawing.Color.light_blue   # make the shape visible

# 3️⃣ Define the shadow (how to change shadow color, how to add outer shadow)
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # outer shadow
shadow.blur_radius = 8.0
shadow.distance = 6.0
shadow.direction = 45
shadow.opacity = 0.6
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)  # custom gray

# 4️⃣ Apply the shadow (apply shadow effect to shape)
rectangle.shadow = shadow

# 5️⃣ Save the file
output_path = os.path.join(output_dir, "RectangleWithShadow.docx")
doc.save(output_path)

print(f"✅ Document generated: {output_path}")
```

**Output yang diharapkan:** Dokumen Word (`RectangleWithShadow.docx`) yang berisi satu persegi panjang dengan bayangan luar abu-abu. Buka di Word untuk memverifikasi efek visual.

## Pertanyaan yang Sering Diajukan

| Pertanyaan | Jawaban |
|------------|---------|
| *Apakah saya dapat menggunakan tipe bentuk lain?* | Tentu—ganti `ShapeType.RECTANGLE` dengan `ShapeType.OVAL`, `ShapeType.TRIANGLE`, dll., dan logika bayangan yang sama tetap berlaku. |
| *Bagaimana jika saya membutuhkan batas yang lebih tebal?* | Setel `rectangle.line_width = 2.0` (points) sebelum menerapkan bayangan. |
| *Apakah memungkinkan untuk menganimasikan bayangan?* | Tidak secara langsung dengan Aspose.Words; Anda harus mengekspor ke HTML/CSS untuk animasi. |
| *Apakah ini bekerja di macOS?* | Ya—Aspose.Words bersifat platform‑agnostik selama Python dapat dijalankan. |

## Kesimpulan

Kami telah membahas **cara menyisipkan bentuk persegi panjang**, mendemonstrasikan **cara mengubah warna bayangan**, menjelaskan **cara menambahkan bayangan luar**, dan akhirnya menunjukkan cara **menerapkan efek bayangan ke bentuk** menggunakan Aspose.Words untuk Python. Skrip lengkap siap disisipkan ke dalam pipeline otomasi apa pun, memberikan Anda persegi panjang berpenampilan profesional dengan bayangan halus dalam hitungan detik.

Siap untuk langkah berikutnya? Coba ganti warna isi, bereksperimen dengan sudut `direction` yang berbeda, atau tambahkan beberapa bentuk ke halaman yang sama. Anda juga dapat menjelajahi API pemformatan teks kaya Aspose.Words untuk menggabungkan bayangan dengan teks bergaya—sempurna untuk laporan yang menarik perhatian.

Jika Anda menemukan tutorial ini bermanfaat, beri jempol, bagikan kepada rekan tim, atau tinggalkan komentar dengan variasi Anda sendiri. Selamat coding!

![Diagram yang menunjukkan cara menyisipkan bentuk persegi panjang dengan bayangan luar yang diterapkan dalam dokumen Word](/images/rectangle-shadow.png)


## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Tutorial Bayangan Bentuk Aspose.Words – Tambahkan Bayangan ke Bentuk Word dalam C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Buat bentuk persegi panjang di Word menggunakan C# – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}