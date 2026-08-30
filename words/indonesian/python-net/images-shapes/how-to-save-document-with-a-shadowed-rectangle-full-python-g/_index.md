---
category: general
date: 2026-06-17
description: Pelajari cara menyimpan dokumen sambil menambahkan bayangan khusus ke
  bentuk persegi panjang di Python menggunakan Aspose.Words. Termasuk cara menambahkan
  bayangan, membuat persegi panjang, menerapkan bayangan, dan mengatur opasitas.
draft: false
keywords:
- how to save document
- how to add shadow
- how to create rectangle
- how to apply shadow
- how to set opacity
language: id
og_description: Panduan langkah demi langkah tentang cara menyimpan dokumen, menambahkan
  bayangan, membuat persegi panjang, menerapkan bayangan, dan mengatur opasitas menggunakan
  Aspose.Words untuk Python.
og_title: Cara Menyimpan Dokumen dengan Persegi Panjang Berbayang – Tutorial Python
  Lengkap
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Learn how to save document while adding a custom shadow to a rectangle
    shape in Python using Aspose.Words. Includes how to add shadow, create rectangle,
    apply shadow, and set opacity.
  headline: How to Save Document with a Shadowed Rectangle – Full Python Guide
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document Automation
title: Cara Menyimpan Dokumen dengan Persegi Panjang Berbayang – Panduan Python Lengkap
url: /id/python/images-shapes/how-to-save-document-with-a-shadowed-rectangle-full-python-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menyimpan Dokumen dengan Persegi Panjang Berbayang – Panduan Python Lengkap

Pernah bertanya-tanya **cara menyimpan dokumen** yang berisi persegi panjang berbayang dengan indah? Mungkin Anda sedang membangun generator laporan dan membutuhkan sentuhan visual tambahan—​Anda tidak sendirian. Dalam tutorial ini kami akan membahas **cara menambahkan bayangan** ke sebuah bentuk, **cara membuat persegi panjang**, **cara menerapkan bayangan**, dan akhirnya **cara mengatur opacity** sebelum kita benar‑benar **menyimpan dokumen**.

Kami akan menggunakan Aspose.Words for Python via .NET, sebuah pustaka kuat yang memungkinkan Anda memanipulasi file Word tanpa harus menginstal Office. Pada akhir panduan ini Anda akan memiliki skrip siap‑jalankan yang menghasilkan *.docx* dengan persegi panjang yang tampak seolah terangkat dari halaman. Tanpa basa‑basi, hanya solusi praktis dari awal hingga akhir.

## Apa yang Akan Anda Pelajari

- Kode tepat yang diperlukan untuk **membuat bentuk persegi panjang** secara programatis.  
- Cara mengaktifkan **efek bayangan khusus** dan menyesuaikan blur, jarak, arah, warna, serta **opacity**.  
- Panggilan tepat yang **menyimpan dokumen** ke disk, termasuk pertimbangan jalur folder.  
- Tips untuk menyesuaikan parameter bayangan bagi berbagai gaya visual.  

**Prasyarat:** Python 3.8+, Aspose.Words for Python via .NET (pasang dengan `pip install aspose-words`), dan folder yang dapat ditulisi di mesin Anda. Itu saja—tanpa ketergantungan tambahan.

![Tangkapan layar yang menunjukkan cara menyimpan dokumen dengan persegi panjang berbayang](shadowed_rectangle.png "cara menyimpan dokumen dengan persegi panjang berbayang")

## Langkah 1: Siapkan Proyek dan Impor Aspose.Words

Sebelum kita menyelam ke bentuk, pastikan pustaka tersedia.

```python
# Install Aspose.Words if you haven’t already:
# pip install aspose-words

import aspose.words as aw
```

> **Tips Pro:** Gunakan lingkungan virtual agar instalasi Python global Anda tetap bersih. Ini juga memudahkan mengunci versi Aspose.Words yang Anda uji.

## Langkah 2: Cara Membuat Bentuk Persegi Panjang

Membuat persegi panjang adalah fondasi—​tanpa bentuk tidak ada yang dapat diberi bayangan. Kelas `DocumentBuilder` memberi kita cara yang lancar untuk menyisipkan bentuk langsung ke dalam dokumen.

```python
# Step 2: Create a new blank document and a builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# Insert a rectangle of 200x100 points (about 2.78 x 1.39 inches)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

**Mengapa ini penting:** Metode `insert_shape` mengembalikan objek `Shape` yang dapat kita modifikasi nanti. Dimensi dinyatakan dalam poin (1 pt = 1/72 in), yang memberi Anda kontrol halus atas ukuran akhir.

### Menyesuaikan Persegi Panjang (Opsional)

Anda mungkin ingin mengubah isi atau garis tepi:

```python
rectangle.fill_color = aw.drawing.Color.light_blue
rectangle.line_format.width = 2.0  # points
rectangle.line_format.color = aw.drawing.Color.dark_blue
```

Baris-baris ini opsional tetapi menggambarkan cara Anda dapat menata persegi panjang sebelum menambahkan bayangan.

## Langkah 3: Cara Menambahkan Bayangan – Mengaktifkan Efek

Sekarang bagian yang menyenangkan: menambahkan bayangan. Aspose.Words menyediakan properti `shadow_effect` yang menyimpan semua pengaturan bayangan.

```python
# Step 3: Enable and configure a custom shadow for the rectangle
shadow = rectangle.shadow_effect
shadow.enabled = True               # Turn the shadow on
shadow.blur_radius = 5.0            # Softness of the shadow edge (points)
shadow.distance = 3.0               # How far the shadow is offset (points)
shadow.direction = 45               # Angle in degrees (0 = left, 90 = down)
shadow.color = aw.drawing.Color.black
shadow.opacity = 0.6                # 60% opaque – this is where we **how to set opacity**
```

**Mengapa kami mengatur setiap properti:**

- **`blur_radius`** melunakkan tepi, membuat bayangan tampak lebih alami.  
- **`distance`** memindahkan bayangan menjauh dari bentuk; nilai yang lebih besar menciptakan efek “mengapung”.  
- **`direction`** menentukan dari mana sumber cahaya datang—​45° memberikan bayangan diagonal.  
- **`color`** dan **`opacity`** mengontrol berat visual; hitam semi‑transparan bekerja baik pada kebanyakan dokumen.

### Kasus Tepi & Variasi

- **Blur sangat besar:** Jika Anda mengatur `blur_radius` di atas 20, bayangan mungkin tidak dapat dibedakan dari bentuk—​gunakan dengan hemat.  
- **Opacity penuh:** Menetapkan `opacity = 1.0` menghasilkan bayangan hitam solid; cocok untuk judul dramatis.  
- **Tanpa blur:** `blur_radius = 0` menciptakan bayangan tepi keras yang tajam, mengingatkan pada grafik vektor.

## Langkah 4: Cara Menerapkan Pengaturan Bayangan dan Menyimpan Dokumen

Dengan persegi panjang dan bayangannya yang telah dikonfigurasi, langkah akhir adalah menyimpan file. Di sinilah kami akhirnya menjawab **cara menyimpan dokumen**.

```python
# Step 4: Save the document with the shadowed rectangle
output_path = "output/shadowed_rectangle.docx"
document.save(output_path)

print(f"Document saved successfully at: {output_path}")
```

**Catatan penting tentang penyimpanan:**

- Folder (`output/` dalam contoh) harus ada; jika tidak `document.save` akan melempar `FileNotFoundError`. Gunakan `os.makedirs('output', exist_ok=True)` sebelumnya jika Anda perlu membuatnya secara programatis.  
- Aspose.Words secara otomatis menentukan format file dari ekstensi, jadi `.docx` memberi Anda dokumen Word modern. Anda juga dapat menyimpan sebagai `.pdf` dengan mengubah ekstensi.

## Skrip Lengkap – Semua Langkah dalam Satu Tempat

Menggabungkan semuanya, berikut skrip lengkap yang siap dijalankan:

```python
import os
import aspose.words as aw

# Ensure the output directory exists
os.makedirs("output", exist_ok=True)

# 1️⃣ Create a blank document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert a rectangle (200x100 points)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Optional styling (feel free to comment out)
rectangle.fill_color = aw.drawing.Color.light_blue
rectangle.line_format.width = 2.0
rectangle.line_format.color = aw.drawing.Color.dark_blue

# 3️⃣ Configure shadow effect
shadow = rectangle.shadow_effect
shadow.enabled = True
shadow.blur_radius = 5.0
shadow.distance = 3.0
shadow.direction = 45
shadow.color = aw.drawing.Color.black
shadow.opacity = 0.6  # How to set opacity

# 4️⃣ Save the document (how to save document)
output_file = "output/shadowed_rectangle.docx"
document.save(output_file)

print(f"Document saved successfully at: {output_file}")
```

Menjalankan skrip ini menghasilkan `output/shadowed_rectangle.docx`. Buka di Microsoft Word, dan Anda akan melihat persegi panjang biru muda dengan bayangan hitam semi‑transparan yang halus mengalir ke kanan‑bawah.

## Pertanyaan Umum & Hal-hal yang Perlu Diwaspadai

- **“Bisakah saya menggunakan tipe bentuk lain?”** Tentu saja. Ganti `aw.drawing.ShapeType.RECTANGLE` dengan `CIRCLE`, `ELLIPSE`, atau nilai enum lain yang didukung. API bayangan berfungsi dengan cara yang sama.  
- **“Bagaimana jika saya membutuhkan warna bayangan yang berbeda?”** Cukup atur `shadow.color` ke `aw.drawing.Color` apa pun yang Anda suka, misalnya `aw.drawing.Color.gray`.  
- **“Apakah nilai opacity selalu antara 0 dan 1?”** Ya. Nilai di luar rentang ini akan dipotong, tetapi sebaiknya tetap berada dalam interval 0‑1 untuk hasil yang dapat diprediksi.  
- **“Apakah saya perlu memanggil `document.update_page_layout()` sebelum menyimpan?”** Tidak. Aspose.Words menangani tata letak secara otomatis saat menyimpan, meskipun Anda dapat memanggilnya secara manual jika melakukan modifikasi berat dan memerlukan data tata letak antara.

## Langkah Selanjutnya – Ke Mana Anda Bisa Pergi Dari Sini

Sekarang Anda tahu **cara menyimpan dokumen** dengan persegi panjang berbayang, Anda mungkin ingin menjelajahi:

- **Cara menambahkan bayangan** ke elemen lain seperti gambar atau kotak teks.  
- **Cara membuat persegi panjang** dengan isian gradien untuk visual yang lebih kaya.  
- **Cara menerapkan bayangan** secara dinamis berdasarkan input pengguna (misalnya, membiarkan UI mengontrol radius blur).  
- **Cara mengatur opacity** untuk beberapa bentuk yang tumpang tindih guna menciptakan efek kedalaman.

Setiap topik tersebut dibangun di atas konsep inti yang kami bahas, sehingga Anda berada pada posisi yang tepat untuk memperluas solusi.

---

**Intinya:** Anda baru saja menguasai alur kerja lengkap—dari membuat persegi panjang, mengonfigurasi bayangannya, menyesuaikan opacity, hingga akhirnya **cara menyimpan dokumen** dengan semua pengaturan tersebut tetap utuh. Cobalah, ubah parameter, dan saksikan file Word Anda memperoleh tampilan profesional tiga‑dimensi.

Selamat coding, dan jangan ragu meninggalkan komentar jika Anda menemui kendala!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang dibangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Dokumen Word Kosong dengan Bentuk Persegi Panjang Berbayang – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Cara Menyimpan Markdown dari Word – Panduan Python Lengkap](/words/english/python-net/document-conversion/how-to-save-markdown-from-word-complete-python-guide/)
- [Cara Menambahkan Bayangan di C# – Panduan Pemrograman Lengkap](/words/english/python-net/images-shapes/how-to-add-shadow-in-c-complete-programming-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}