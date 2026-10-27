---
category: general
date: 2026-10-04
description: Cara membuat dokumen di Python dan menambahkan bayangan ke bentuk menggunakan
  Aspose.Words. Pelajari cara mengatur warna bayangan, menyisipkan bentuk persegi
  panjang, dan menyesuaikan bayangan luar.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create document
- add shadow to shape
- set shadow color
- insert rectangle shape
- how to add shadow
language: id
lastmod: 2026-10-04
og_description: Cara membuat dokumen di Python dan menambahkan bayangan pada bentuk.
  Panduan ini menunjukkan cara mengatur warna bayangan, menyisipkan bentuk persegi
  panjang, dan menerapkan bayangan luar menggunakan Aspose.Words.
og_image_alt: Python code inserting a rectangle shape with a visible shadow into a
  Word document
og_title: Cara membuat dokumen dengan bentuk persegi panjang dan bayangan di Python
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  headline: How to create document with a rectangle shape and shadow in Python
  type: TechArticle
- description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  name: How to create document with a rectangle shape and shadow in Python
  steps:
  - name: Why does the shadow sometimes appear invisible?
    text: The shadow is only rendered if `shadow.visible` is set to `True` **and**
      the shape’s `wrap_type` allows it to be displayed. An inline shape works reliably;
      floating shapes may require additional layout adjustments.
  - name: How can I change the shadow color to match a brand palette?
    text: 'Replace `aw.drawing.Color.black` with a custom RGB value:'
  - name: What if I need the shape to appear behind text?
    text: Set the wrap type to `WrapType.BEHIND` and adjust the `z_order_position`
      if necessary. Keep in mind that some viewers may render behind‑text shapes differently.
  - name: Can I apply the same shadow settings to multiple shapes?
    text: Yes. Create a helper function that configures the shadow and call it for
      each shape you insert. This promotes code reuse and ensures consistent styling.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Cara membuat dokumen dengan bentuk persegi panjang dan bayangan di Python
url: /id/python/images-shapes/how-to-create-document-with-a-rectangle-shape-and-shadow-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat dokumen dengan bentuk persegi panjang dan bayangan di Python

Jika Anda perlu **cara membuat dokumen** yang berisi persegi panjang bergaya, panduan ini menyediakan solusi lengkap. Anda akan melihat cara **menambahkan bayangan ke bentuk**, mengatur warna bayangan, serta mengontrol offset dan blur‑nya—semua dengan Aspose.Words for Python. Pada akhir tutorial Anda dapat menghasilkan file `.docx` yang tampak rapi dan siap didistribusikan.

Langkah‑langkah di bawah mencakup semua hal mulai dari menginstal pustaka hingga menyesuaikan tampilan bayangan. Tidak diperlukan dokumentasi eksternal; kode siap disalin, dijalankan, dan disesuaikan dengan proyek Anda. Anda juga akan belajar cara **menyisipkan bentuk persegi panjang**, memilih **gaya bayangan luar**, dan menangani masalah umum seperti bayangan yang tidak terlihat atau pengaturan wrap yang salah.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* Python 3.8 atau lebih baru terpasang.
* Lisensi aktif Aspose.Words for Python (atau kunci evaluasi gratis).
* Familiaritas dasar dengan skrip Python.
* Akses ke lokasi sistem berkas tempat dokumen yang dihasilkan akan disimpan.

Anda dapat menginstal SDK dengan pip:

```bash
pip install aspose-words
```

## Langkah 1: Impor pustaka dan buat dokumen kosong baru

Membuat dokumen baru adalah tindakan pertama dalam setiap skenario otomatisasi Word. Konstruktor `aw.Document()` memberi Anda file kosong yang dapat diisi dengan teks, gambar, atau bentuk.

```python
import aspose.words as aw

# Create a new blank document
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

Objek `DocumentBuilder` menyederhanakan penyisipan konten. Ia melacak posisi kursor saat ini, sehingga Anda dapat menambahkan elemen secara berurutan tanpa harus mengelola bagian secara manual.

## Langkah 2: Sisipkan bentuk persegi panjang dengan ukuran yang diinginkan

Bentuk persegi panjang berfungsi sebagai wadah untuk elemen visual. Anda dapat menentukan lebar dan tinggi dalam poin (1 pt ≈ 1/72 in).

```python
# Insert a rectangle shape that is 150 pt wide and 80 pt tall
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

Pada titik ini bentuk belum memiliki gaya visual, sehingga muncul sebagai garis tepi polos. Langkah selanjutnya akan memberi kedalaman dan warna.

## Langkah 3: Atur bentuk agar mengalir inline dengan teks di sekitarnya

Ketika sebuah bentuk **inline**, ia berperilaku seperti karakter dalam paragraf. Ini memastikan persegi panjang tetap berada di tempat yang Anda harapkan dalam tata letak dokumen.

```python
# Make the shape inline so it follows the text flow
rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE
```

Jika Anda lebih suka bentuk mengapung di atas teks, Anda dapat menggunakan `WrapType.SQUARE` atau `WrapType.TOP_BOTTOM`, tetapi untuk kebanyakan laporan bentuk inline membuat tata letak lebih dapat diprediksi.

## Langkah 4: Buat bayangan terlihat dan pilih warnanya

Bayangan yang tidak terlihat tidak memberikan manfaat visual. Flag `visible` mengaktifkan efek, dan properti `color` menentukan nuansanya. Menggunakan hitam memberikan kedalaman klasik yang halus.

```python
# Enable the shadow and set its color to black
rectangle_shape.shadow.visible = True
rectangle_shape.shadow.color = aw.drawing.Color.black
```

Anda dapat mengganti `aw.drawing.Color.black` dengan warna lain, seperti `aw.drawing.Color.gray` atau nilai RGB khusus (`aw.drawing.Color.from_argb(255, 128, 128, 128)`).

## Langkah 5: Tentukan offset dan blur bayangan untuk memberi kedalaman

Offset mengontrol seberapa jauh bayangan dipindahkan dari bentuk, sementara radius blur melunakkan tepi‑tepinya. Nilai kecil menghasilkan bayangan tajam; nilai lebih besar menghasilkan tampilan yang lebih lembut.

```python
# Horizontal and vertical offset of 5 pt each
rectangle_shape.shadow.offset_x = 5
rectangle_shape.shadow.offset_y = 5

# Blur radius of 3 pt for a gentle feather
rectangle_shape.shadow.blur = 3
```

Bereksperimenlah dengan angka‑angka ini untuk menyesuaikan dengan pedoman desain Anda. Untuk bayangan jatuh yang kuat, Anda dapat meningkatkan baik offset maupun blur.

## Langkah 6: Pilih gaya bayangan luar

Aspose.Words menawarkan beberapa gaya bayangan, seperti `INNER`, `OUTER`, dan `PERSPECTIVE`. Gaya **outer** menempatkan bayangan di luar batas bentuk, yang ideal untuk tampilan bersih dan profesional.

```python
# Apply an outer shadow style
rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

Jika Anda menginginkan efek yang lebih dramatis, coba `ShadowStyle.PERSPECTIVE`—ia menambahkan kemiringan tiga dimensi.

## Langkah 7: Simpan dokumen dengan bayangan berbentuk

Menyimpan menyelesaikan file dan menuliskan semua pemformatan ke disk. Pilih direktori yang Anda miliki hak menulis, dan beri nama file yang deskriptif.

```python
# Save the document to the desired location
output_path = "output/ShapeWithShadow.docx"
document.save(output_path)
print(f"Document saved to {output_path}")
```

Menjalankan skrip menghasilkan file Word yang berisi persegi panjang dengan bayangan berwarna yang terlihat. Buka file tersebut di Microsoft Word atau LibreOffice untuk memverifikasi hasilnya.

## Contoh lengkap yang dapat dijalankan

Berikut adalah skrip lengkap yang menggabungkan semua langkah yang dibahas. Salin kode ke file bernama `create_shadowed_shape.py` dan jalankan dengan `python create_shadowed_shape.py`.

```python
import aspose.words as aw
import os

def main():
    # Ensure the output directory exists
    output_dir = "output"
    os.makedirs(output_dir, exist_ok=True)

    # Step 1: Create a new blank document
    document = aw.Document()
    builder = aw.DocumentBuilder(document)

    # Step 2: Insert a rectangle shape of the desired size
    rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

    # Step 3: Set the shape to be inline with the text flow
    rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE

    # Step 4: Make the shadow visible and choose its color
    rectangle_shape.shadow.visible = True
    rectangle_shape.shadow.color = aw.drawing.Color.black

    # Step 5: Define the shadow's offset and blur to give it depth
    rectangle_shape.shadow.offset_x = 5   # horizontal offset in points
    rectangle_shape.shadow.offset_y = 5   # vertical offset in points
    rectangle_shape.shadow.blur = 3       # blur radius in points

    # Step 6: Choose an outer shadow style
    rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER

    # Step 7: Save the document with the shaped shadow
    output_path = os.path.join(output_dir, "ShapeWithShadow.docx")
    document.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    main()
```

**Output yang diharapkan**

Saat Anda membuka `ShapeWithShadow.docx`, Anda akan melihat satu persegi panjang yang terpusat di halaman. Persegi panjang tersebut dilengkapi dengan bayangan hitam halus yang bergeser ke kanan‑bawah, sedikit blur untuk menciptakan kedalaman. Bayangan mengikuti gaya outer, sehingga tidak menembus interior persegi panjang.

## Pertanyaan umum dan kasus tepi

### Mengapa bayangan kadang‑kadang tidak terlihat?

Bayangan hanya dirender jika `shadow.visible` diset ke `True` **dan** `wrap_type` bentuk mengizinkannya ditampilkan. Bentuk inline bekerja secara andal; bentuk mengapung mungkin memerlukan penyesuaian tata letak tambahan.

### Bagaimana cara mengubah warna bayangan agar sesuai dengan palet merek?

Ganti `aw.drawing.Color.black` dengan nilai RGB khusus:

```python
rectangle_shape.shadow.color = aw.drawing.Color.from_argb(255, 0, 120, 215)  # corporate blue
```

### Bagaimana jika saya ingin bentuk muncul di belakang teks?

Setel `wrap_type` ke `WrapType.BEHIND` dan sesuaikan `z_order_position` bila diperlukan. Perlu diingat bahwa beberapa penampil mungkin merender bentuk di belakang teks secara berbeda.

### Bisakah saya menerapkan pengaturan bayangan yang sama ke beberapa bentuk?

Ya. Buat fungsi pembantu yang mengonfigurasi bayangan dan panggil fungsi tersebut untuk setiap bentuk yang Anda sisipkan. Ini mempromosikan penggunaan kembali kode dan memastikan konsistensi gaya.

```python
def apply_shadow(shape, color=aw.drawing.Color.black, offset=5, blur=3):
    shape.shadow.visible = True
    shape.shadow.color = color
    shape.shadow.offset_x = offset
    shape.shadow.offset_y = offset
    shape.shadow.blur = blur
    shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

## Kesimpulan

Anda kini tahu **cara membuat dokumen** yang berisi bentuk persegi panjang dengan bayangan yang disesuaikan menggunakan Aspose.Words for Python. Tutorial ini mencakup penyisipan persegi panjang, menjadikan bentuk inline, mengaktifkan bayangan, mengatur warnanya, offset, blur, dan gaya, serta akhirnya menyimpan file.

Mulai dari sini Anda dapat menjelajahi topik terkait seperti **add shadow to shape** untuk tipe bentuk lain, **set shadow color** secara dinamis berdasarkan data, atau **how to add shadow** ke gambar dan kotak teks. Bereksperimenlah dengan dimensi, warna, dan gaya bayangan yang berbeda untuk menyesuaikan dengan pedoman merek atau sistem desain Anda.

Siap mengotomatisasi lebih banyak dokumen Word? Cobalah menambahkan tabel, header, atau konten dinamis berikutnya—setiap langkah membangun atas prinsip yang sama yang ditunjukkan di sini. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang berhubungan erat dan membangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang dapat dijalankan dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [How to Manage Document Variables with Aspose.Words in Python&#58; A Complete Guide](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}