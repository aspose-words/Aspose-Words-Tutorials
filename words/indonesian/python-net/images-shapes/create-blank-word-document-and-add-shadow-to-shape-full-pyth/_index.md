---
category: general
date: 2026-07-20
description: Buat dokumen Word kosong di Python dan pelajari cara menambahkan bayangan
  ke bentuk dengan Aspose.Words, termasuk cara menambahkan bayangan dan menerapkan
  warna bayangan.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add shadow to shape
- how to add shadow
- apply shadow color
language: id
lastmod: 2026-07-20
og_description: Buat dokumen Word kosong di Python dan temukan cara menambahkan bayangan
  pada bentuk, serta tips menerapkan warna bayangan untuk dokumen yang tampak profesional.
og_image_alt: Screenshot showing a blank Word document with a shape that has a shadow
  applied
og_title: Buat Dokumen Word Kosong – Tambahkan Bayangan pada Bentuk dengan Python
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Create blank word document in Python and learn how to add shadow to
    shape with Aspose.Words, including how to add shadow and apply shadow color.
  headline: Create Blank Word Document and Add Shadow to Shape – Full Python Guide
  type: TechArticle
- description: Create blank word document in Python and learn how to add shadow to
    shape with Aspose.Words, including how to add shadow and apply shadow color.
  name: Create Blank Word Document and Add Shadow to Shape – Full Python Guide
  steps:
  - name: Why start with a blank document?
    text: Because it guarantees that no hidden styles or remnants from templates interfere
      with the **shadow** effect we’ll add later. A clean document also speeds up
      processing, especially when you generate thousands of files in a batch job.
  - name: Why these values?
    text: '- A **blur of 5.0** gives a gentle feathered look without making the shape
      look detached. - Offsets of **2.0** create a subtle depth effect—enough to be
      noticeable but not overpowering. - Using **black** is a safe default; however,
      you can replace it with `aw.drawing.Color.from_argb(255, 30, 144, 25'
  - name: Expected Output
    text: '- A single‑page Word file. - A 200 × 100 pt rectangle positioned 100 pt
      from the top‑left corner. - A shadow that is **blurred**, **offset** by 2 pt
      on both axes, and colored **black** (or your custom color).'
  type: HowTo
- questions:
  - answer: It’s the most neutral shape, making the shadow effect obvious.
    question: Why a rectangle?
  - answer: The code safely grabs the first paragraph or creates one, so it works
      on both fresh and populated docs.
    question: What if the document already has content?
  type: FAQPage
tags:
- Aspose.Words
- Python
- Document Automation
- Shape Styling
title: Buat Dokumen Word Kosong dan Tambahkan Bayangan pada Bentuk – Panduan Python
  Lengkap
url: /id/python/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat Dokumen Word Kosong dan Tambahkan Bayangan ke Bentuk – Panduan Python Lengkap

Pernahkah Anda perlu **create blank word document** dari awal dan kemudian membuat sebuah bentuk menonjol dengan bayangan halus? Anda tidak sendirian. Baik Anda sedang membangun mesin templating atau hanya membuat prototipe laporan, menguasai cara menambahkan bayangan ke bentuk dapat memberikan file Word Anda sentuhan profesional.

Dalam tutorial ini kami akan membahas seluruh proses menggunakan Aspose.Words untuk Python via .NET. Kami akan memulai dengan membuat dokumen Word kosong, menyisipkan bentuk sederhana, lalu **add shadow to shape**, menyesuaikan blur dan offset, dan akhirnya **apply shadow color** agar sesuai dengan merek Anda. Pada akhir tutorial Anda akan memiliki skrip yang dapat dijalankan sepenuhnya dan dapat langsung digunakan dalam proyek apa pun.

## Apa yang Akan Anda Pelajari

- Cara **create blank word document** secara programatis dengan Aspose.Words.
- Langkah‑langkah tepat untuk **add shadow to shape** dan mengontrol tampilannya.
- Mengapa detail **how to add shadow** (blur, offset) penting untuk hierarki visual.
- Teknik untuk **apply shadow color** agar gaya konsisten di seluruh dokumen.
- Kesalahan umum (mis., shape tidak ada, format tidak didukung) dan cara menghindarinya.

> **Prerequisites** – Anda memerlukan Python 3.8+ dan paket `aspose-words` terpasang (`pip install aspose-words`). Tidak diperlukan pengalaman sebelumnya dengan Aspose, tetapi pemahaman dasar tentang objek Python akan membantu.

![Create blank word document with a shadowed shape](image.png){alt="Buat dokumen word kosong dengan bentuk yang memiliki bayangan"}

## Buat Dokumen Word Kosong dengan Aspose.Words (Python)

Hal pertama dalam daftar periksa kami adalah **blank Word document** yang dapat kami isi nanti. Aspose.Words membuat ini menjadi satu baris kode:

```python
import aspose.words as aw

# Step 1: Instantiate a new, empty document
doc = aw.Document()
```

Baris itu memberi kami kanvas bersih—bayangkan seperti selembar kertas baru. Di balik layar, Aspose membuat struktur dokumen yang diperlukan (section, body, dll.) sehingga Anda tidak perlu khawatir tentang XML tingkat rendah.

### Mengapa memulai dengan dokumen kosong?

Karena hal ini menjamin tidak ada gaya tersembunyi atau sisa dari template yang mengganggu efek **shadow** yang akan kami tambahkan nanti. Dokumen bersih juga mempercepat proses, terutama ketika Anda menghasilkan ribuan file dalam pekerjaan batch.

## Sisipkan Bentuk Sebelum Menambahkan Bayangan

Anda tidak dapat menambahkan bayangan ke sesuatu yang tidak ada, kan? Jadi mari letakkan sebuah persegi panjang sederhana pada halaman pertama. Ini juga menunjukkan alur kerja **add shadow to shape** dalam skenario yang realistis.

```python
# Step 2: Create a rectangle shape (200x100 points) and add it to the first section
shape = aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
shape.width = 200
shape.height = 100
shape.left = 100   # Horizontal position from the left margin
shape.top = 100    # Vertical position from the top margin

# Add the shape to the document’s first paragraph (creates one if missing)
first_section = doc.first_section
first_paragraph = first_section.body.first_paragraph
if first_paragraph is None:
    first_paragraph = aw.Paragraph(doc)
    first_section.body.append_child(first_paragraph)

first_paragraph.append_child(shape)
```

Beberapa catatan:

- **Why a rectangle?** Itu adalah bentuk paling netral, membuat efek bayangan menjadi jelas.
- **What if the document already has content?** Kode dengan aman mengambil paragraf pertama atau membuatnya, sehingga berfungsi baik pada dokumen baru maupun yang sudah berisi.

## Tambahkan Bayangan ke Bentuk – Implementasi Langkah‑per‑Langkah

Sekarang kita memiliki bentuk, saatnya menjawab pertanyaan **how to add shadow**. Aspose.Words menyediakan objek `Shadow` dengan beberapa properti yang dapat kita atur.

```python
# Step 3: Enable a shadow on the shape
shape.shadow = aw.drawing.Shadow()
```

Baris itu mengaktifkan fitur bayangan. Secara default, bayangan berwarna hitam, dengan blur sedang dan offset nol. Mari kita sesuaikan.

## Cara Menambahkan Bayangan: Mengonfigurasi Blur, Offset, dan Warna

Dampak visual sebuah bayangan sangat dipengaruhi oleh tiga parameter:

1. **Blur radius** – mengontrol seberapa lembut tepi terlihat.
2. **Offset X/Y** – menggeser bayangan secara horizontal dan vertikal.
3. **Color** – memungkinkan Anda menyesuaikan dengan palet perusahaan.

```python
# Step 4: Set the blur radius (higher = softer)
shape.shadow.blur = 5.0          # 5 points blur

# Step 5: Define horizontal and vertical offsets
shape.shadow.offset_x = 2.0      # 2 points to the right
shape.shadow.offset_y = 2.0      # 2 points down

# Step 6: Choose the shadow color (apply shadow color)
shape.shadow.color = aw.drawing.Color.black  # You can use any RGB value
```

### Mengapa nilai-nilai ini?

- **blur of 5.0** memberikan tampilan lembut tanpa membuat bentuk tampak terlepas.
- Offset **2.0** menciptakan efek kedalaman halus—cukup terlihat namun tidak berlebihan.
- Menggunakan **black** adalah default yang aman; namun, Anda dapat menggantinya dengan `aw.drawing.Color.from_argb(255, 30, 144, 255)` untuk bayangan biru dingin yang cocok dengan warna aksen merek.

## Terapkan Warna Bayangan untuk Styling yang Tepat

Jika Anda memerlukan bayangan bukan hitam, langkah **apply shadow color** sangat sederhana. Aspose memungkinkan Anda mendefinisikan warna ARGB apa pun:

```python
# Example: Apply a navy blue shadow
navy = aw.drawing.Color.from_argb(255, 0, 0, 128)  # Fully opaque, RGB(0,0,128)
shape.shadow.color = navy
```

> **Pro tip:** Saat bekerja dengan template perusahaan, simpan warna merek Anda dalam file JSON dan muat saat runtime. Dengan cara ini Anda dapat mengganti warna bayangan di seluruh dokumen tanpa mengubah kode.

## Simpan Dokumen dan Verifikasi Hasil

Semua proses berat telah selesai; kita hanya perlu menyimpan file. Aspose mendukung banyak format, tetapi mari gunakan DOCX yang paling umum.

```python
# Step 7: Save the document to disk
output_path = "ShadowedShape.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Buka `ShadowedShape.docx` di Microsoft Word (atau LibreOffice) dan Anda akan melihat persegi panjang dengan bayangan bersih dan lembut—tepat seperti yang kami konfigurasikan.

### Output yang Diharapkan

- File Word satu halaman.
- Persegi panjang 200 × 100 pt yang ditempatkan 100 pt dari sudut kiri‑atas.
- Bayangan yang **blurred**, **offset** sebesar 2 pt pada kedua sumbu, dan berwarna **black** (atau warna khusus Anda).

Jika bentuk muncul tanpa bayangan, periksa kembali bahwa Anda memanggil `shape.shadow = aw.drawing.Shadow()` *sebelum* mengatur properti lainnya. Urutan penting karena objek `Shadow` harus ada terlebih dahulu.

## Kesalahan Umum dan Kasus Tepi

| Masalah | Mengapa Terjadi | Solusi |
|-------|----------------|-----|
| `shape` is `None` | Mencoba mengambil shape sebelum ada | Sisipkan shape terlebih dahulu (lihat bagian “Insert a Shape”) |
| Bayangan tidak terlihat di Word | Warna bayangan sama dengan latar belakang (mis., putih di atas putih) | Pilih warna kontras atau tingkatkan blur |
| Offset terlalu besar | Bayangan bergerak keluar halaman, tampak terpotong | Jaga offset di bawah 10 pt untuk ukuran halaman standar |
| Penyimpanan gagal dengan `PermissionError` | File terbuka di Word saat skrip dijalankan | Tutup file atau simpan ke jalur lain |

## Contoh Lengkap yang Berfungsi (Siap Salin‑Tempel)

```python
import aspose.words as aw

# 1️⃣ Create a blank Word document
doc = aw.Document()

# 2️⃣ Insert a rectangle shape
shape = aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
shape.width = 200
shape.height = 100
shape.left = 100
shape.top = 100

first_section = doc.first_section
first_paragraph = first_section.body.first_paragraph
if first_paragraph is None:
    first_paragraph = aw.Paragraph(doc)
    first_section.body.append_child(first_paragraph)

first_paragraph.append_child(shape)

# 3️⃣ Enable shadow
shape.shadow = aw.drawing.Shadow()

# 4️⃣ Configure blur, offset, and color
shape.shadow.blur = 5.0
shape.shadow.offset_x = 2.0
shape.shadow.offset_y = 2.0
shape.shadow.color = aw.drawing.Color.black   # Change to any color you like

# 5️⃣ Save the result
output_path = "ShadowedShape.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Jalankan skrip, buka file yang dihasilkan, dan Anda akan melihat persegi panjang dengan bayangan—bukti bahwa Anda telah berhasil **created a blank word document**, **added a shadow to the shape**, dan **applied shadow color**.

## Langkah Selanjutnya dan Topik Terkait

- **Styling Text** – Pelajari cara menambahkan paragraf terformat bersamaan dengan shape.
- **Multiple Shapes** – Lakukan loop pada daftar shape dan beri masing‑masing bayangan unik.
- **Export to PDF** – Konversi DOCX ke PDF sambil mempertahankan efek bayangan (`doc.save("output.pdf")`).
- **Dynamic Colors** – Ambil warna merek dari file konfigurasi dan terapkan secara programatik.

Masing‑masing topik ini dibangun di atas konsep inti yang dibahas di sini, jadi silakan bereksperimen. Semakin Anda bermain dengan Aspose.Words, semakin Anda akan menghargai fleksibilitasnya untuk otomatisasi dokumen.

---

**Secara singkat:** Anda kini tahu cara **create blank word document**, **add shadow to shape**, memahami detail **how to add shadow** (blur, offset), dan dengan percaya diri **apply shadow color** untuk tampilan yang halus. Cobalah dalam proyek pelaporan berikutnya—tidak ada lagi persegi panjang membosankan.

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑per‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Tutorial Bayangan Shape Aspose.Words – Tambahkan Bayangan ke Shape Word di C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Buat Dokumen Word Kosong dengan Bentuk Persegi Panjang Berbayangan – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}