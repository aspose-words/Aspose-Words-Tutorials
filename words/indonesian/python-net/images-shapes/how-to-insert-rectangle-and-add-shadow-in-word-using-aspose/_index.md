---
category: general
date: 2026-05-30
description: Cara menyisipkan persegi panjang dan menambahkan bayangan di Word menggunakan
  Aspose – panduan Python langkah demi langkah untuk membuat dokumen Word dengan efek
  bayangan bentuk.
draft: false
keywords:
- how to insert rectangle
- add shadow to shape
- how to add shape shadow
- apply shadow effect word
- create word document aspose
language: id
og_description: Cara menyisipkan persegi panjang dan menambahkan bayangan di Word
  menggunakan Aspose – pelajari cara membuat dokumen Word dengan efek bayangan bentuk
  menggunakan Python.
og_title: Cara menyisipkan persegi panjang dan menambahkan bayangan di Word menggunakan
  Aspose
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  headline: How to insert rectangle and add shadow in Word using Aspose
  type: TechArticle
- description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  name: How to insert rectangle and add shadow in Word using Aspose
  steps:
  - name: What each property does
    text: '| Property | Effect | Typical Range | |----------|--------|---------------|
      | `visible` | Turns the shadow on/off | `True` / `False` | | `distance` | How
      far the shadow sits from the shape | 2 – 10 pts | | `blur` | Softness of the
      shadow edges | 4 – 12 pts | | `color` | Shadow hue; dark gray is a sa'
  - name: Adding Multiple Shapes
    text: If you need more than one rectangle, simply repeat the `insert_shape` call.
      Remember to move the builder’s cursor (`builder.move_to(shape)`) or adjust `shape.left`/`shape.top`
      to avoid overlap.
  - name: Changing the Shape Type
    text: While this guide focuses on rectangles, the same pattern works for ovals,
      stars, or custom free‑form shapes. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`,
      `ShapeType.CLOUD`, etc., and the shadow settings remain identical.
  - name: Saving to Other Formats
    text: 'Aspose.Words can export to PDF, PNG, or even XPS with a single line:'
  - name: Handling Large Documents
    text: When generating massive reports, consider calling `doc.update_page_layout()`
      after inserting all shapes. This forces a layout pass and can improve performance
      when you later convert to PDF.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word Automation
title: Cara menyisipkan persegi panjang dan menambahkan bayangan di Word menggunakan
  Aspose
url: /id/python/images-shapes/how-to-insert-rectangle-and-add-shadow-in-word-using-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menyisipkan persegi panjang dan menambahkan bayangan di Word menggunakan Aspose

Pernah bertanya-tanya **cara menyisipkan persegi panjang** ke dalam file Word tanpa membuka UI? Anda tidak sendirian. Banyak pengembang perlu menghasilkan laporan, faktur, atau sertifikat secara dinamis, dan menggambar persegi panjang sederhana dengan bayangan yang bagus dapat membuat output terlihat lebih rapi. Dalam tutorial ini kami akan memandu Anda langkah demi langkah untuk membuat dokumen Word, menambahkan bentuk persegi panjang, dan menerapkan bayangan realistis menggunakan Aspose.Words untuk Python.

Kami akan membahas semuanya mulai dari menyiapkan paket Aspose hingga menyesuaikan jarak, blur, dan opasitas bayangan. Pada akhir tutorial Anda akan memiliki potongan kode yang dapat digunakan kembali dan dapat disisipkan ke dalam pipeline otomatisasi apa pun. Tidak ada sihir, hanya kode yang jelas dan beberapa tips praktis.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki:

- Python 3.8+ terpasang (kode ini bekerja pada 3.9, 3.10, dan versi lebih baru)
- Lisensi aktif Aspose.Words untuk Python atau kunci evaluasi gratis
- Paket `aspose-words` terpasang via `pip install aspose-words`
- Folder yang dapat ditulisi tempat **create word document aspose** yang dihasilkan akan disimpan

Itu saja—tidak ada DLL tambahan, tidak ada interop COM, hanya Python murni.

## Langkah 1: Inisialisasi Dokumen (How to create word document aspose)

Hal pertama yang perlu Anda lakukan: buat objek `Document` baru. Anggap saja ini sebagai kanvas kosong. Kode berikut membuat dokumen dan `DocumentBuilder` yang akan memungkinkan kita menyisipkan bentuk.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

*Mengapa ini penting:* `DocumentBuilder` memberi Anda API tingkat tinggi untuk menambahkan paragraf, tabel, dan—ya—bentuk tanpa harus berurusan dengan pohon node tingkat rendah. Jika Anda melewatkan builder dan memanipulasi node secara langsung, Anda akan berakhir dengan kode yang bertele‑tele dan lebih sulit dipelihara.

## Langkah 2: Sisipkan Persegi Panjang (how to insert rectangle)

Sekarang kita benar‑benar **cara menyisipkan persegi panjang**. Aspose.Words memperlakukan persegi panjang sebagai tipe bentuk generik. Anda menentukan lebar dan tinggi dalam poin (1 poin ≈ 1/72 inci). Silakan sesuaikan angka-angka tersebut agar cocok dengan tata letak Anda.

```python
# Step 2: Insert a rectangle shape of the desired size
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

> **Pro tip:** Jika Anda perlu menempatkan persegi panjang pada lokasi tertentu di halaman, atur `shape.left` dan `shape.top` setelah penyisipan. Ini memberi Anda kontrol pixel‑perfect.

## Langkah 3: Akses ShadowFormat Bentuk (add shadow to shape)

Gaya visual sebuah bentuk berada di dalam `ShadowFormat`‑nya. Dengan mengambilnya, kita mendapatkan akses ke setiap properti yang menentukan tampilan bayangan.

```python
# Step 3: Access the shape's shadow format
shadow = shape.shadow_format
```

Pada titik ini bayangan tidak terlihat—anggap saja sebagai lapisan tersembunyi yang menunggu instruksi Anda.

## Langkah 4: Konfigurasi Bayangan (how to add shape shadow, apply shadow effect word)

Inilah saat magis terjadi. Kita akan mengaktifkan bayangan dan menyesuaikan tampilannya. Nilai‑nilai di bawah menghasilkan bayangan lembut diagonal yang cocok untuk kebanyakan dokumen, tetapi Anda dapat bereksperimen.

```python
# Step 4: Make the shadow visible and configure its appearance
shadow.visible = True                # Show the shadow
shadow.distance = 5.0                # Distance from the shape (points)
shadow.blur = 8.0                    # Blur radius (points)
shadow.color = aw.Color.dark_grey   # Shadow color
shadow.opacity = 0.6                 # Opacity (0‑1)
shadow.angle = 45.0                  # Direction in degrees
```

### Apa yang dilakukan setiap properti

| Property | Efek | Rentang Umum |
|----------|------|--------------|
| `visible` | Mengaktifkan/mematikan bayangan | `True` / `False` |
| `distance` | Seberapa jauh bayangan berada dari bentuk | 2 – 10 pts |
| `blur` | Kelembutan tepi bayangan | 4 – 12 pts |
| `color` | Warna bayangan; abu‑abu gelap adalah nilai aman | Any `aw.Color` |
| `opacity` | Transparansi; 0 = tidak terlihat, 1 = padat | 0.3 – 0.8 untuk tampilan halus |
| `angle` | Arah cahaya datang | 0 – 360° |

**Mengapa menyesuaikan ini?** Bayangan yang diatur dengan baik dapat membuat persegi panjang datar tampak terangkat dari halaman, menambah kedalaman tanpa gambar. Jika Anda mengatur `opacity` terlalu tinggi, bayangan akan terlihat keras; terlalu rendah dan bayangan akan menghilang.

## Langkah 5: Simpan Dokumen (create word document aspose)

Akhirnya, tulis file ke disk. Anda dapat menggunakan ekstensi apa pun yang didukung oleh Aspose.Words (`.docx`, `.pdf`, `.html`). Untuk tutorial ini kami akan tetap menggunakan `.docx`.

```python
# Step 5: Save the document with the shaped shadow
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Buka file yang dihasilkan di Microsoft Word, dan Anda akan melihat persegi panjang tajam dengan bayangan halus—tepat seperti yang Anda harapkan dari templat yang dirancang secara profesional.

![cara menyisipkan bentuk persegi panjang dengan bayangan menggunakan Aspose.Words](/images/rectangle-shadow.png){alt="cara menyisipkan bentuk persegi panjang dengan bayangan menggunakan Aspose.Words"}

*Cuplikan layar (di atas) menunjukkan persegi panjang dengan bayangan yang diterapkan. Perhatikan blur yang lembut dan sudut 45°, yang memberikan tampilan alami.*

## Variasi Umum dan Kasus Tepi

### Menambahkan Beberapa Bentuk

Jika Anda memerlukan lebih dari satu persegi panjang, cukup ulangi pemanggilan `insert_shape`. Ingat untuk memindahkan kursor builder (`builder.move_to(shape)`) atau sesuaikan `shape.left`/`shape.top` agar tidak tumpang tindih.

```python
# Example: Insert a second rectangle 200 points to the right
second_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
second_shape.left = shape.left + 200
second_shape.top = shape.top
```

### Mengubah Tipe Bentuk

Meskipun panduan ini berfokus pada persegi panjang, pola yang sama berlaku untuk oval, bintang, atau bentuk bebas khusus. Ganti `ShapeType.RECTANGLE` dengan `ShapeType.OVAL`, `ShapeType.CLOUD`, dll., dan pengaturan bayangan tetap sama.

### Menyimpan ke Format Lain

Aspose.Words dapat mengekspor ke PDF, PNG, atau bahkan XPS dengan satu baris kode:

```python
doc.save("output/ShapeWithShadow.pdf")
```

Rendering bayangan dipertahankan di semua format, sehingga PDF Anda akan terlihat persis seperti file Word.

### Menangani Dokumen Besar

Saat menghasilkan laporan besar, pertimbangkan memanggil `doc.update_page_layout()` setelah menyisipkan semua bentuk. Ini memaksa proses layout dan dapat meningkatkan kinerja ketika Anda kemudian mengonversi ke PDF.

## Contoh Lengkap yang Berfungsi (Semua Langkah Digabung)

Berikut adalah skrip lengkap yang dapat Anda salin‑tempel ke dalam file bernama `rectangle_shadow.py`. Jalankan dengan `python rectangle_shadow.py` dan periksa folder `output`.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
os.makedirs("output", exist_ok=True)

# Initialize the document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

# Configure the shadow
shadow = shape.shadow_format
shadow.visible = True
shadow.distance = 5.0
shadow.blur = 8.0
shadow.color = aw.Color.dark_grey
shadow.opacity = 0.6
shadow.angle = 45.0

# Save the document
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Menjalankan skrip ini menghasilkan dokumen yang persis sama dengan yang kami bahas sebelumnya. Silakan ubah angka‑angka sesuai kebutuhan; kode ini sengaja dibuat sederhana agar Anda dapat bereksperimen tanpa rasa takut.

## Pertanyaan yang Sering Diajukan

**Q: Apakah ini bekerja di Linux?**


## Apa yang Harus Anda Pelajari Selanjutnya?

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}