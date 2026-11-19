---
category: general
date: 2026-11-18
description: Contoh bayangan bentuk Aspose.Words menunjukkan cara menambahkan bayangan
  pada bentuk Word menggunakan Python. Ikuti panduan langkah demi langkah ini untuk
  memodifikasi dan menyimpan dokumen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words shape shadow example
- python shape shadow
- Aspose.Words for Python
- modify shape shadow
- document manipulation Aspose
language: id
lastmod: 2026-11-18
og_description: Contoh bayangan bentuk Aspose.Words menunjukkan cara menambahkan bayangan
  pada bentuk Word dengan Python. Pelajari kode lengkapnya, mengapa setiap langkah
  penting, dan cara menyesuaikannya.
og_image_alt: Aspose.Words shape shadow example – Word document displaying a shape
  with a shadow applied using Python
og_title: Contoh bayangan bentuk Aspose.Words – Panduan Python
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Aspose.Words shape shadow example shows how to add a shadow to a Word
    shape using Python. Follow this step‑by‑step guide to modify and save the document.
  headline: Aspose.Words shape shadow example in Python
  type: TechArticle
- description: Aspose.Words shape shadow example shows how to add a shadow to a Word
    shape using Python. Follow this step‑by‑step guide to modify and save the document.
  name: Aspose.Words shape shadow example in Python
  steps:
  - name: Expected outcome
    text: Open `output.docx` in Microsoft Word. The first shape you added should now
      display a soft shadow that is offset by 2 pt horizontally and vertically, with
      a blur radius of 5 pt. All other content remains unchanged.
  - name: 'Alternative: Find a shape by name'
    text: 'If your document contains several shapes, you might prefer to locate a
      specific one:'
  - name: Working with multiple shapes
    text: 'If you need to apply the same shadow to every shape, iterate over the node
      collection:'
  - name: Applying a shadow to a specific shape type
    text: You can filter by `ShapeType` (e.g., `aw.ShapeType.IMAGE`). This is useful
      when you only want to affect pictures, not AutoShapes.
  - name: Handling documents without shapes
    text: The script already raises a clear `ValueError` if no shape is found. In
      production code you might log the issue and continue processing other files.
  - name: Compatibility notes
    text: '* The code works with **Aspose.Words for Python via .NET** version 23.10
      and later. * The shadow effect is supported in Word 2007+ (`.docx`). Older formats
      (`.doc`) will lose the effect after conversion.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Contoh bayangan bentuk Aspose.Words dalam Python
url: /id/python/images-shapes/aspose-words-shape-shadow-example-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Contoh bayangan shape Aspose.Words di Python

Contoh bayangan shape Aspose.Words memperlihatkan cara menambahkan efek bayangan ke sebuah shape dalam dokumen Word menggunakan Python. Pada tutorial ini Anda akan mendapatkan skrip lengkap yang dapat dijalankan, yang memuat dokumen, mengonfigurasi bayangan, dan menyimpan hasilnya.

Menambahkan bayangan ke sebuah shape adalah cara umum untuk meningkatkan hierarki visual dalam laporan, brosur, atau faktur. Kode di bawah ini bekerja dengan Aspose.Words untuk Python via .NET dan tidak memerlukan pustaka pihak ketiga tambahan.

## Apa yang akan Anda pelajari

* Cara memuat file `.docx` dengan **Aspose.Words for Python**.  
* Cara menemukan shape pertama (termasuk shape di dalam tabel atau grup).  
* Cara mengonfigurasi blur, offset horizontal, dan offset vertikal bayangan.  
* Cara menyimpan dokumen yang telah dimodifikasi sambil mempertahankan semua konten lainnya.  

**Prasyarat**

* Python 3.8 atau lebih baru.  
* Aspose.Words for Python via .NET terpasang (`pip install aspose-words`).  
* Dokumen Word (`input.docx`) yang berisi setidaknya satu shape (misalnya gambar, AutoShape, atau kotak teks).  

Jika Anda perlu menginstal pustaka, jalankan:

```bash
pip install aspose-words
```

## Contoh bayangan shape Aspose.Words – ikhtisar

Skrip berikut adalah solusi lengkap. Skrip ini mengikuti empat langkah logis dari alur kerja **manipulasi dokumen Aspose** tipikal: muat, temukan, ubah, dan simpan.

```python
import aspose.words as aw

# ----------------------------------------------------------------------
# Step 1: Load the Word document
# ----------------------------------------------------------------------
# Replace YOUR_DIRECTORY with the path that contains input.docx.
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)

# ----------------------------------------------------------------------
# Step 2: Access the first shape (including descendants)
# ----------------------------------------------------------------------
# NodeType.SHAPE searches for any shape node. The third argument (True)
# tells Aspose.Words to search recursively through all child nodes.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# Verify that a shape was found; raise a clear error if not.
if shape is None:
    raise ValueError("No shape found in the document. Ensure input.docx contains a shape.")

# ----------------------------------------------------------------------
# Step 3: Configure the shape's shadow
# ----------------------------------------------------------------------
# The Shadow object controls visual appearance. Adjust the properties
# to achieve the desired effect.
shape.shadow.blur = 5          # Softness of the shadow (0‑15 is typical)
shape.shadow.offset_x = 2      # Horizontal displacement in points
shape.shadow.offset_y = 2      # Vertical displacement in points

# Optional: Change shadow color or transparency if needed.
# shape.shadow.color = aw.Color.black
# shape.shadow.transparency = 0.5

# ----------------------------------------------------------------------
# Step 4: Save the modified document
# ----------------------------------------------------------------------
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)

print(f"Shadow applied successfully. Saved to {output_path}")
```

### Hasil yang diharapkan

Buka `output.docx` di Microsoft Word. Shape pertama yang Anda tambahkan kini harus menampilkan bayangan lembut yang bergeser 2 pt secara horizontal dan vertikal, dengan radius blur 5 pt. Semua konten lain tetap tidak berubah.

## Langkah 1: Muat dokumen Word

Memuat dokumen adalah operasi pertama dalam setiap alur kerja **Aspose.Words for Python**. Kelas `Document` mem-parsing file dan membangun model objek di memori. Karena pustaka ini berjalan di platform .NET, ia dapat menangani file besar secara efisien.

*Mengapa ini penting:* Memuat dokumen sekali dan menyimpan referensi (`doc`) menghindari I/O berulang, yang meningkatkan kinerja saat Anda perlu menerapkan banyak modifikasi.

## Langkah 2: Akses shape

Shape dapat menjadi anak langsung dari badan dokumen, atau dapat berada di dalam tabel, grup, atau kanvas gambar. Menggunakan `get_child(NodeType.SHAPE, 0, True)` mencari secara rekursif dan mengembalikan shape pertama yang cocok.

*Mengapa ini penting:* Flag `True` memastikan Anda tidak melewatkan shape yang tersembunyi di dalam node lain. Jika Anda menghilangkannya, hanya shape tingkat atas yang akan dipertimbangkan, dan banyak dokumen dunia nyata akan mengembalikan `None`.

### Alternatif: Temukan shape berdasarkan nama

Jika dokumen Anda berisi beberapa shape, Anda mungkin ingin menemukan shape tertentu:

```python
shape = doc.get_child(aw.NodeType.SHAPE, lambda n: n.name == "MyLogo", True)
```

Potongan kode ini memperlihatkan variasi **python shape shadow** yang memfilter berdasarkan properti `name` pada shape.

## Langkah 3: Konfigurasi bayangan shape

Properti `shadow` dari objek `Shape` memberi Anda kontrol detail atas efek visual. Tiga atribut yang paling sering disesuaikan adalah:

| Property | Kisaran tipikal | Dampak visual |
|----------|-----------------|---------------|
| `blur`   | 0 – 15          | Nilai yang lebih tinggi menghasilkan tepi yang lebih lembut. |
| `offset_x` | –10 – 10     | Nilai positif menggeser bayangan ke kanan. |
| `offset_y` | –10 – 10     | Nilai positif menggeser bayangan ke bawah. |

Anda juga dapat memodifikasi `color`, `transparency`, `visible`, dan `style`. Contoh ini menetapkan blur yang moderat dan offset ringan agar bayangan tetap halus.

**Tip pro:** Ketika sebuah shape sudah memiliki bayangan, properti di atas akan menimpa pengaturan yang ada. Jika Anda perlu mempertahankan gaya asli, baca nilai saat ini sebelum mengubahnya.

## Langkah 4: Simpan dokumen yang telah dimodifikasi

Memanggil `doc.save()` menulis kembali representasi di memori ke file `.docx`. Aspose.Words secara otomatis memperbarui semua hubungan internal, sehingga file output tetap sepenuhnya kompatibel dengan Microsoft Word.

*Mengapa ini penting:* Menyimpan hanya sekali di akhir proses mengurangi risiko korupsi file dan meningkatkan kecepatan keseluruhan, terutama saat memproses banyak dokumen dalam pekerjaan batch.

## Variasi umum dan kasus tepi

### Bekerja dengan banyak shape

Jika Anda perlu menerapkan bayangan yang sama ke setiap shape, iterasikan koleksi node:

```python
for shp in doc.get_child_nodes(aw.NodeType.SHAPE, True):
    shp.shadow.blur = 5
    shp.shadow.offset_x = 2
    shp.shadow.offset_y = 2
```

### Menerapkan bayangan ke tipe shape tertentu

Anda dapat memfilter berdasarkan `ShapeType` (misalnya `aw.ShapeType.IMAGE`). Ini berguna ketika Anda hanya ingin memengaruhi gambar, bukan AutoShape.

```python
for shp in doc.get_child_nodes(aw.NodeType.SHAPE, True):
    if shp.shape_type == aw.ShapeType.IMAGE:
        shp.shadow.blur = 4
```

### Menangani dokumen tanpa shape

Skrip sudah menghasilkan `ValueError` yang jelas jika tidak ada shape yang ditemukan. Pada kode produksi, Anda mungkin mencatat masalah tersebut dan melanjutkan pemrosesan file lain.

### Catatan kompatibilitas

* Kode bekerja dengan **Aspose.Words for Python via .NET** versi 23.10 dan yang lebih baru.  
* Efek bayangan didukung di Word 2007+ (`.docx`). Format lama (`.doc`) akan kehilangan efek setelah konversi.

## Kesimpulan

**Contoh bayangan shape aspose.words** ini memandu Anda melalui proses memuat file Word, menemukan shape, mengonfigurasi bayangannya, dan menyimpan hasilnya dengan **Aspose.Words for Python**. Anda kini memiliki pola yang dapat dipakai ulang untuk skenario **manipulasi dokumen Aspose** apa pun yang melibatkan peningkatan visual.

Selanjutnya, Anda dapat menjelajahi:

* Menambahkan isian gradien atau gaya garis ke shape (`modify shape shadow` dan properti visual lainnya).  
* Menggabungkan konfigurasi bayangan dengan pemformatan teks untuk membuat templat yang sepenuhnya bergaya.  
* Mengotomatiskan proses untuk sekumpulan dokumen menggunakan `os.listdir` dan pola yang ditunjukkan di atas.

Silakan bereksperimen dengan tingkat blur, offset, dan warna yang berbeda untuk menyesuaikan pedoman merek Anda. Selamat coding!


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Add Shadow to Shape in Python – Complete Aspose.Words Tutorial](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [How to set shadow on a shape in Aspose.Words for Python](/words/english/python-net/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-for-python/)
- [How to save PNG and add shadow to shape with Aspose.Words](/words/english/python-net/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}