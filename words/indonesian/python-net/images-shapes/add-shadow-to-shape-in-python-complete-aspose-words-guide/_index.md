---
category: general
date: 2026-08-11
description: Tambahkan bayangan ke bentuk menggunakan Aspose.Words untuk Python. Pelajari
  cara menambahkan bayangan pada bentuk, menerapkan blur pada bentuk, dan menyesuaikan
  offset serta warna.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- add shape shadow
- apply blur to shape
- Aspose.Words shadow effect
- Python Word shape styling
language: id
lastmod: 2026-08-11
og_description: Tambahkan bayangan pada bentuk dengan Aspose.Words untuk Python. Panduan
  ini menunjukkan cara menerapkan blur pada bentuk, mengatur offset, dan memilih warna
  bayangan hanya dengan beberapa baris kode.
og_image_alt: Word document screenshot showing a shape with a black shadow applied
og_title: Tambahkan bayangan pada bentuk di Python – tutorial Aspose.Words langkah
  demi langkah
schemas:
- author: Aspose
  dateModified: '2026-08-11'
  description: Add shadow to shape using Aspose.Words for Python. Learn how to add
    shape shadow, apply blur to shape, and customize offset and color.
  headline: Add shadow to shape in Python – complete Aspose.Words guide
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python. Learn how to add
    shape shadow, apply blur to shape, and customize offset and color.
  name: Add shadow to shape in Python – complete Aspose.Words guide
  steps:
  - name: Adding shadow to a specific shape by name
    text: 'If your document contains several shapes, you may want to target one by
      its `name` property:'
  - name: Skipping non‑visual nodes
    text: Sometimes a shape node can be a placeholder (e.g., a drawing canvas without
      visual content). Guard against this by checking `shape.is_image` or `shape.is_picture_frame`
      before applying the shadow.
  - name: Working with grouped shapes
    text: When shapes are grouped, the group itself is a `Shape` node. To apply a
      shadow to each member, iterate through `shape.get_child_nodes(aw.NodeType.SHAPE,
      True)`.
  - name: What’s next?
    text: '- Explore **apply blur to shape** for other effects like glow or soft edges.
      - Combine shadows with **shape borders** or **reflection** to create richer
      graphics. - Convert the edited document to PDF (`doc.save("output.pdf", aw.SaveFormat.PDF)`)
      for distribution.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Menambahkan bayangan pada bentuk di Python – panduan lengkap Aspose.Words
url: /id/python/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tambahkan bayangan ke bentuk di Python – panduan lengkap Aspose.Words

Jika Anda perlu **add shadow to shape** dalam dokumen Word, tutorial ini menunjukkan secara tepat cara melakukannya dengan Aspose.Words untuk Python. Baik Anda sedang membangun generator laporan atau layanan templat dokumen, Anda akan belajar menambahkan bayangan pada bentuk, menerapkan blur pada bentuk, dan menyesuaikan tampilan bayangan hanya dengan beberapa baris kode.

Panduan ini mencakup semua yang Anda perlukan: impor yang diperlukan, menemukan bentuk target (termasuk node bersarang), mengonfigurasi properti bayangan, menangani kasus tepi umum, dan menyimpan dokumen yang telah dimodifikasi. Pada akhir tutorial Anda akan memiliki potongan kode yang dapat digunakan kembali dan dapat disisipkan ke proyek Python apa pun yang bekerja dengan file .docx.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

- **Python 3.8+** terpasang.
- **Aspose.Words for Python via .NET** (pasang dengan `pip install aspose-words`).
- Dokumen Word (`input.docx`) yang berisi setidaknya satu bentuk (misalnya persegi panjang, gambar, atau SmartArt).
- Pengetahuan dasar tentang Python dan model objek Aspose.Words.

## Langkah 1: Impor Aspose.Words dan buka dokumen

Langkah pertama adalah mengimpor paket `aspose.words` (biasanya disingkat menjadi `aw`) dan memuat dokumen sumber.

```python
import aspose.words as aw

# Load the Word document from the file system
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)
```

*Mengapa ini penting*: Membuka dokumen memberi Anda akses ke pohon node tempat bentuk berada. Kelas `aw.Document` adalah titik masuk untuk semua manipulasi selanjutnya.

## Langkah 2: Temukan bentuk pertama (termasuk node bersarang)

Bentuk dapat menjadi anak langsung dari sebuah `Paragraph` atau bersarang di dalam kontainer lain (seperti tabel). Menggunakan `get_child` dengan flag `is_deep` diset ke `True` memastikan Anda mengambil bentuk pertama terlepas dari tingkat kedalaman.

```python
# Retrieve the first shape in the document, searching recursively
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

if shape is None:
    raise ValueError("No shape found in the document. Add a shape before applying a shadow.")
```

*Mengapa ini penting*: Operasi **add shape shadow** memerlukan objek `Shape`. Pencarian mendalam mencegah Anda melewatkan bentuk yang tersembunyi di dalam tabel atau grup.

## Langkah 3: Aktifkan bayangan dan atur properti dasar

Aspose.Words merepresentasikan bayangan dengan beberapa properti. Pertama, aktifkan bayangan dengan mengatur `shadow_visible` ke `True`.

```python
# Enable the shadow effect
shape.shadow_visible = True
```

Sekarang Anda dapat mengonfigurasi radius blur, offset, dan warna.

## Langkah 4: Terapkan blur pada bentuk dan tentukan nilai offset

Radius blur mengontrol seberapa lembut bayangan terlihat. Nilai `5.0` memberikan blur yang terlihat jelas namun tidak berlebihan. Offset menggeser bayangan secara horizontal dan vertikal.

```python
# Apply blur to shape – this is the "apply blur to shape" part
shape.shadow_blur = 5.0          # Blur radius in points

# Define horizontal (X) and vertical (Y) offsets
shape.shadow_offset_x = 2.0     # Move shadow 2 points to the right
shape.shadow_offset_y = 2.0     # Move shadow 2 points down
```

*Mengapa ini penting*: Menyesuaikan `shadow_blur` dan nilai offset memungkinkan Anda menciptakan efek kedalaman realistis yang cocok dengan gaya visual dokumen Anda.

## Langkah 5: Pilih warna bayangan (add shape shadow dengan warna khusus)

Anda dapat menggunakan sembarang `aw.Color`. Di sini kami memilih hitam, tetapi Anda dapat menggantinya dengan `aw.Color.red`, `aw.Color.from_argb(255, 0, 120, 215)`, dll.

```python
# Set the shadow color – black in this example
shape.shadow_color = aw.Color.black
```

*Mengapa ini penting*: Warna menentukan bagaimana bayangan berinteraksi dengan konten di sekitarnya. Bayangan yang lebih gelap lebih terlihat pada latar belakang terang, sementara nuansa lebih terang bekerja lebih baik pada halaman gelap.

## Langkah 6: Simpan dokumen yang telah diperbarui

Akhirnya, tulis perubahan kembali ke disk. Anda dapat menimpa file asli atau membuat file baru.

```python
output_path = "YOUR_DIRECTORY/output_with_shadow.docx"
doc.save(output_path)

print(f"Shadow applied successfully. Saved to {output_path}")
```

Saat Anda membuka `output_with_shadow.docx` di Microsoft Word, bentuk pertama akan menampilkan bayangan hitam lembut dengan blur dan offset yang telah ditentukan.

## Contoh lengkap yang dapat dijalankan

Menggabungkan semua langkah, berikut skrip mandiri yang dapat Anda jalankan langsung:

```python
import aspose.words as aw

def add_shadow_to_first_shape(input_path: str, output_path: str,
                              blur: float = 5.0,
                              offset_x: float = 2.0,
                              offset_y: float = 2.0,
                              color: aw.Color = aw.Color.black) -> None:
    """
    Loads a Word document, finds the first shape (deep search),
    and applies a shadow effect.

    Parameters
    ----------
    input_path : str
        Path to the source .docx file.
    output_path : str
        Path where the modified document will be saved.
    blur : float, optional
        Blur radius for the shadow. Default is 5.0 points.
    offset_x : float, optional
        Horizontal offset of the shadow. Default is 2.0 points.
    offset_y : float, optional
        Vertical offset of the shadow. Default is 2.0 points.
    color : aw.Color, optional
        Shadow color. Default is black.
    """
    # Load the document
    doc = aw.Document(input_path)

    # Retrieve the first shape, searching recursively
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

    if shape is None:
        raise ValueError("No shape found in the document. Insert a shape before calling this function.")

    # Enable shadow and configure its appearance
    shape.shadow_visible = True
    shape.shadow_blur = blur
    shape.shadow_offset_x = offset_x
    shape.shadow_offset_y = offset_y
    shape.shadow_color = color

    # Save the result
    doc.save(output_path)

if __name__ == "__main__":
    INPUT_DOC = "YOUR_DIRECTORY/input.docx"
    OUTPUT_DOC = "YOUR_DIRECTORY/output_with_shadow.docx"
    add_shadow_to_first_shape(INPUT_DOC, OUTPUT_DOC)
```

**Output yang diharapkan**: Membuka `output_with_shadow.docx` menampilkan bentuk pertama dengan bayangan hitam halus yang diblur, bergeser 2 pt secara horizontal dan vertikal, sesuai dengan parameter yang Anda berikan.

## Menangani banyak bentuk dan kasus tepi

### Menambahkan bayangan ke bentuk tertentu berdasarkan nama

Jika dokumen Anda berisi beberapa bentuk, Anda mungkin ingin menargetkan satu berdasarkan properti `name`‑nya:

```python
target_name = "MyRectangle"
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)  # start with first shape
while shape is not None and shape.name != target_name:
    shape = shape.next_sibling(aw.NodeType.SHAPE)

if shape is None:
    raise ValueError(f"Shape named '{target_name}' not found.")
```

### Melewati node non‑visual

Kadang‑kadang node bentuk dapat berupa placeholder (misalnya kanvas gambar tanpa konten visual). Lindungi kode Anda dengan memeriksa `shape.is_image` atau `shape.is_picture_frame` sebelum menerapkan bayangan.

```python
if not shape.is_image and not shape.is_picture_frame:
    # Proceed only if the shape can display a shadow
    shape.shadow_visible = True
```

### Bekerja dengan bentuk yang dikelompokkan

Ketika bentuk dikelompokkan, grup itu sendiri adalah node `Shape`. Untuk menerapkan bayangan pada setiap anggota, iterasikan melalui `shape.get_child_nodes(aw.NodeType.SHAPE, True)`.

```python
if shape.is_group:
    for child in shape.get_child_nodes(aw.NodeType.SHAPE, True):
        child.shadow_visible = True
        child.shadow_blur = blur
        child.shadow_offset_x = offset_x
        child.shadow_offset_y = offset_y
        child.shadow_color = color
```

Variasi ini memastikan kode Anda berfungsi secara andal di berbagai tata letak dokumen.

## Tips profesional untuk bayangan yang sempurna

- **Konsistensi**: Gunakan radius blur dan offset yang sama untuk semua bentuk dalam laporan agar bahasa visual tetap konsisten.
- **Kinerja**: Menerapkan bayangan pada puluhan gambar beresolusi tinggi dapat meningkatkan ukuran file. Uji ukuran output jika Anda berencana menghasilkan PDF nanti.
- **Kontras warna**: Pada latar belakang halaman gelap, pertimbangkan bayangan yang lebih terang (`aw.Color.gray`) untuk menjaga keterlihatan.
- **Pratinjau**: UI “Shadow” di Word mencerminkan properti Aspose.Words, sehingga Anda dapat bereksperimen secara manual, lalu menyalin nilai yang dihasilkan ke dalam skrip Anda.

## Kesimpulan

Sekarang Anda tahu cara **add shadow to shape** dalam dokumen Word menggunakan Aspose.Words untuk Python. Panduan ini mencakup menemukan bentuk, mengaktifkan bayangan, **add shape shadow** dengan blur, offset, dan warna khusus, serta menyimpan hasilnya. Dengan fungsi yang dapat digunakan kembali di atas, Anda dapat mengintegrasikan efek ini ke dalam pipeline pembuatan dokumen apa pun.

### Apa selanjutnya?

- Jelajahi **apply blur to shape** untuk efek lain seperti glow atau tepi lembut.
- Gabungkan bayangan dengan **shape borders** atau **reflection** untuk menciptakan grafis yang lebih kaya.
- Konversi dokumen yang telah diedit ke PDF (`doc.save("output.pdf", aw.SaveFormat.PDF)`) untuk distribusi.

Silakan bereksperimen dengan warna, tingkat blur, dan nilai offset yang berbeda untuk menyesuaikan dengan pedoman merek Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}