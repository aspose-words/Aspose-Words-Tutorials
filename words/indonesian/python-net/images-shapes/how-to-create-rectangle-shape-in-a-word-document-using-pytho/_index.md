---
category: general
date: 2026-09-30
description: Pelajari cara membuat bentuk persegi panjang, menerapkan bayangan pada
  bentuk, dan menyimpan dokumen Word dengan bentuk menggunakan Aspose.Words untuk
  Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- how to add shape
- apply shadow to shape
- set shadow blur
- save word with shape
language: id
lastmod: 2026-09-30
og_description: Buat bentuk persegi panjang dalam dokumen Word dengan cepat. Tutorial
  ini menunjukkan cara menambahkan bentuk, menerapkan bayangan pada bentuk, mengatur
  keburaman bayangan, dan menyimpan Word dengan bentuk.
og_image_alt: Screenshot of a Word document showing a rectangle shape with a soft
  shadow
og_title: Buat bentuk persegi panjang di Word dengan Python – panduan langkah demi
  langkah
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Learn how to create rectangle shape, apply shadow to shape, and save
    Word with shape using Aspose.Words for Python.
  headline: How to create rectangle shape in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- Shapes
title: Cara membuat bentuk persegi panjang dalam dokumen Word menggunakan Python
url: /id/python/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat bentuk persegi panjang dalam dokumen Word menggunakan Python

Jika Anda perlu **membuat bentuk persegi panjang** dalam file Word, panduan ini menunjukkan solusi lengkap yang dapat dijalankan. Anda akan melihat cara menambahkan bentuk, menerapkan efek bayangan, menyesuaikan blur, dan akhirnya **menyimpan Word dengan bentuk** sehingga hasilnya dapat dibuka di Microsoft Word atau penampil kompatibel lainnya.

Contoh ini menggunakan **Aspose.Words for Python via .NET**, sebuah pustaka yang memungkinkan Anda memanipulasi dokumen Word tanpa harus menginstal Microsoft Office. Tidak diperlukan pengalaman sebelumnya dengan API—hanya pengetahuan dasar Python.

## Apa yang akan Anda capai

- Masukkan persegi panjang ke dalam bagian pertama dari dokumen baru.  
- Konfigurasikan bayangan lembut dengan mengatur blur, offset, dan warna.  
- Simpan dokumen ke disk dan verifikasi hasil visual.

## Prasyarat

- Python 3.8 atau lebih baru.  
- `aspose-words` package terinstal (`pip install aspose-words`).  
- Izin menulis ke direktori output.

## Buat bentuk persegi panjang dan konfigurasikan tampilannya

Langkah pertama adalah membuat dokumen kosong dan menambahkan bentuk persegi panjang ke dalamnya. Bentuk tersebut akan berfungsi sebagai kanvas untuk efek bayangan.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Step 1: Create a new blank document
doc = aw.Document()

# Step 2: Add a rectangle shape to the first section
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Optional: Define the shape’s size and position (in points)
shape.width = aw.ConvertUtil.inch_to_point(2)   # 2 inches wide
shape.height = aw.ConvertUtil.inch_to_point(1)  # 1 inch tall
shape.left = aw.ConvertUtil.inch_to_point(1)    # 1 inch from the left margin
shape.top = aw.ConvertUtil.inch_to_point(1)     # 1 inch from the top margin
```

**Mengapa ini penting:**  
Membuat persegi panjang memberi Anda objek konkret (`shape`) yang dapat Anda stilkan nanti. Menetapkan dimensi secara eksplisit memastikan bentuk terlihat sama di setiap platform.

## Cara menambahkan bentuk ke dokumen Word

Meskipun kode di atas sudah menambahkan persegi panjang, Anda mungkin perlu menambahkan bentuk tambahan (mis., lingkaran, panah) nanti. Pola yang sama berlaku: panggil `append_child` pada body dokumen dan berikan `ShapeType` yang diinginkan.

```python
# Example: Adding a second shape – an ellipse
ellipse = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.ELLIPSE)
)
ellipse.width = aw.ConvertUtil.inch_to_point(1.5)
ellipse.height = aw.ConvertUtil.inch_to_point(1)
ellipse.left = aw.ConvertUtil.inch_to_point(3.5)
ellipse.top = aw.ConvertUtil.inch_to_point(1)
```

**Tip:** Gunakan enumerasi `ShapeType` untuk menjelajahi semua bentuk yang didukung. Ini membuat kode Anda lebih mudah dibaca dan menghindari angka misterius.

## Terapkan bayangan ke bentuk dan atur blur bayangan

Bayangan menambah kedalaman dan ketertarikan visual. Kelas `ShadowEffect` memungkinkan Anda mengontrol blur, offset, dan warna. Di bawah ini kami menerapkan bayangan hitam lembut pada persegi panjang.

```python
# Step 3: Configure a shadow effect for the rectangle
shadow = ShadowEffect()
shadow.blur = 5.0          # Sets the softness of the shadow edge
shadow.offset_x = 2.0      # Horizontal displacement from the shape
shadow.offset_y = 2.0      # Vertical displacement from the shape
shadow.color = aw.Color.black

# Step 4: Apply the shadow effect to the shape
shape.shadow = shadow
```

**Mengapa mengatur blur?**  
`blur` menentukan seberapa tersebar bayangan tersebut. Nilai rendah (mis., 1.0) menghasilkan tepi yang tajam, sementara nilai lebih tinggi (mis., 5.0) menciptakan fade yang lembut, yang seringkali lebih estetis.

**Kasus tepi:** Jika Anda mengatur `blur` ke 0, bayangan menjadi siluet padat. Beberapa penampil mungkin merendernya dengan artefak aliasing, jadi pilih nilai lebih besar dari 0 untuk output yang lebih halus.

## Simpan Word dengan bentuk

Menyimpan dokumen memfinalisasi semua perubahan. Metode `save` menulis file `.docx` yang dapat dibuka oleh prosesor Word modern mana pun.

```python
# Step 5: Save the document to see the result
output_path = "output.docx"   # Adjust the path as needed
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Saat Anda membuka `output.docx`, Anda akan melihat persegi panjang yang ditempatkan satu inci dari sudut kiri‑atas, dengan bayangan hitam lembut yang dipindahkan dua poin ke kanan dan ke bawah. Blur bayangan membuatnya tampak seperti bentuk terangkat dari halaman.

**Pro tip:** Jika Anda perlu menghasilkan banyak dokumen dalam sebuah loop, gunakan kembali instance `Document` yang sama dan bersihkan body-nya di antara iterasi untuk mengurangi beban memori.

## Variasi umum dan pemecahan masalah

| Situasi | Apa yang diubah | Alasan |
|-----------|----------------|--------|
| Different shadow color | `shadow.color = aw.Color.red` | Gunakan warna merek atau sorot bentuk penting. |
| Larger shadow offset | Increase `shadow.offset_x`/`offset_y` | Tekankan kedalaman untuk mock‑up UI. |
| No shadow at all | Omit the `shape.shadow = shadow` line | Berguna untuk laporan minimalis. |
| Export to PDF instead of DOCX | `doc.save("output.pdf")` | PDF ideal untuk distribusi hanya-baca. |

Jika bentuk tidak muncul, pastikan Anda menambahkannya ke bagian yang tepat (`get_first_section()`) dan dokumen disimpan setelah modifikasi.

## Contoh lengkap yang dapat dijalankan

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Create a new blank document
doc = aw.Document()

# Add a rectangle shape
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
shape.width = aw.ConvertUtil.inch_to_point(2)
shape.height = aw.ConvertUtil.inch_to_point(1)
shape.left = aw.ConvertUtil.inch_to_point(1)
shape.top = aw.ConvertUtil.inch_to_point(1)

# Configure and apply a shadow
shadow = ShadowEffect()
shadow.blur = 5.0
shadow.offset_x = 2.0
shadow.offset_y = 2.0
shadow.color = aw.Color.black
shape.shadow = shadow

# Save the document
output_path = "output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Menjalankan skrip menghasilkan `output.docx` yang berisi persegi panjang dengan bayangan lembut. Buka file tersebut di Microsoft Word untuk memastikan efek visual sesuai dengan deskripsi.

## Kesimpulan

Anda sekarang tahu cara **membuat bentuk persegi panjang**, **menambahkan bentuk** ke dokumen Word, **menerapkan bayangan ke bentuk**, **mengatur blur bayangan**, dan akhirnya **menyimpan Word dengan bentuk** menggunakan Aspose.Words for Python. Pola yang sama dapat diperluas ke tipe bentuk lain, warna, dan efek, memberi Anda kontrol penuh atas grafik dokumen tanpa bergantung pada otomasi Office.

**Langkah selanjutnya**

- Bereksperimen dengan `Shape.fill` untuk menambahkan latar belakang gradien atau gambar.  
- Gunakan objek `Paragraph` untuk menempatkan teks di dalam persegi panjang.  
- Gabungkan beberapa bentuk untuk membuat diagram kompleks, lalu ekspor ke PDF untuk distribusi.  

Silakan sesuaikan kode untuk kebutuhan pelaporan atau templating Anda, dan bagikan hasilnya di komentar!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Buat bentuk persegi panjang, tambahkan bayangan & simpan PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Tutorial Bayangan Bentuk Aspose.Words – Tambahkan Bayangan ke Bentuk Word dalam C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}