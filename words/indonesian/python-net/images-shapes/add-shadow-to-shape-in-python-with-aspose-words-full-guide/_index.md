---
category: general
date: 2026-06-30
description: Tambahkan bayangan ke bentuk menggunakan Aspose.Words untuk Python. Pelajari
  cara mengatur jarak bayangan, menyesuaikan blur, dan menyimpan PDF dengan bayangan
  bentuk secara cepat.
draft: false
keywords:
- add shadow to shape
- how to set shadow distance
- how to add shape shadow
- Aspose.Words Python shadow
- shape formatting Python
language: id
og_description: Tambahkan bayangan ke bentuk dalam dokumen Word dengan Aspose.Words
  untuk Python. Tutorial ini menunjukkan cara mengatur jarak bayangan, blur, dan warna,
  kemudian menyimpannya sebagai PDF.
og_title: Tambahkan Bayangan pada Bentuk di Python – Panduan Lengkap Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  headline: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  name: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  steps:
  - name: What if I need a different shape?
    text: Replace `aw.drawing.ShapeType.RECTANGLE` with any other enum value, e.g.,
      `aw.drawing.ShapeType.ELLIPSE`. The same shadow properties apply—no extra code
      needed.
  - name: Can I apply a shadow to multiple shapes at once?
    text: 'Yes. Loop over the shapes you create and configure each `shadow_format`
      individually. Here’s a quick snippet:'
  - name: How do I change the shadow’s opacity?
    text: 'Use the `shadow.transparency` property (0 = opaque, 1 = fully transparent):'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Menambahkan Bayangan pada Bentuk di Python dengan Aspose.Words – Panduan Lengkap
url: /id/python/images-shapes/add-shadow-to-shape-in-python-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tambahkan Bayangan ke Bentuk di Python dengan Aspose.Words – Panduan Lengkap

Menambahkan bayangan ke bentuk dalam dokumen Word menggunakan Aspose.Words untuk Python lebih mudah daripada yang Anda kira. Jika Anda pernah bertanya-tanya **cara mengatur jarak bayangan** atau **cara menambahkan bayangan pada bentuk** untuk tampilan yang halus, panduan ini akan membantu Anda.

Dalam beberapa menit ke depan kami akan membahas semua yang Anda perlukan: mulai dari membuat dokumen baru, menyisipkan persegi panjang, menyesuaikan properti bayangannya, hingga akhirnya menyimpan sebagai PDF yang menampilkan efek tersebut. Pada akhir tutorial Anda akan dapat menambahkan bayangan pada bentuk apa pun—persegi panjang, elips, atau gambar khusus—tanpa harus menyelami dokumentasi API.

> **Prasyarat** – Anda harus memiliki Python 3.7+ terpasang, lisensi Aspose.Words untuk Python (atau evaluasi gratis), dan pemahaman dasar tentang skrip Python. Tidak diperlukan pustaka eksternal lainnya.

---

## Tambahkan Bayangan ke Bentuk – Ikhtisar Langkah-demi-Langkah

Berikut adalah peta jalan singkat dari apa yang akan kami capai:

1. **Buat dokumen baru** dan sebuah `DocumentBuilder` untuk mengeditnya.  
2. **Sisipkan bentuk persegi panjang** dengan ukuran yang Anda butuhkan.  
3. **Aktifkan dan sesuaikan bayangan** – di sinilah kata kunci utama bersinar.  
4. **Simpan dokumen** sebagai PDF yang mempertahankan bayangan bentuk.

Setiap langkah dipisahkan ke dalam bagiannya masing‑masing, sehingga Anda dapat menyalin‑tempel potongan kode langsung ke IDE Anda.

---

## Langkah 1: Inisialisasi Dokumen dan Builder

Hal pertama—tanpa `Document` Anda tidak memiliki apa‑apa untuk dikerjakan. `DocumentBuilder` adalah kuas melukis Anda.

```python
import aspose.words as aw

# Create a new, empty Word document
document = aw.Document()

# Attach a builder to the document for easy editing
builder = aw.DocumentBuilder(document)
```

*Mengapa ini penting*: Objek `Document` mewakili seluruh file, sementara `DocumentBuilder` mempermudah penyisipan teks, tabel, dan bentuk. Anggap builder sebagai kursor yang dapat Anda gerakkan di sekitar halaman.

---

## Langkah 2: Sisipkan Bentuk Persegi Panjang

Sekarang kita akan menambahkan persegi panjang—kanvas kita untuk efek bayangan. Anda dapat mengganti `RECTANGLE` dengan `ELLIPSE`, `STAR`, atau `ShapeType` lainnya jika memerlukan geometri yang berbeda.

```python
# Insert a rectangle with width=200pt and height=100pt
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

*Pro tip*: Ukuran diukur dalam poin (1 pt ≈ 1/72 inci). Sesuaikan agar cocok dengan tata letak Anda; bayangan akan otomatis menyesuaikan skala.

---

## Cara Mengatur Jarak Bayangan

Jarak **bayangan** menentukan seberapa jauh bayangan muncul dari bentuk. Jarak yang lebih besar meniru sumber cahaya yang lebih jauh, sementara nilai yang lebih kecil memberikan efek mengangkat yang halus.

```python
# Access the shadow format of the shape
shadow = rectangle_shape.shadow_format

# Make the shadow visible
shadow.visible = True

# Set the distance (in points) from the shape
shadow.distance = 4.0          # <-- this is the "how to set shadow distance" part
```

> **Catatan**: Jarak bekerja bersama dengan `angle`. Mengubah sudut memutar bayangan di sekitar bentuk, sementara `distance` mendorongnya ke luar.

---

## Cara Menambahkan Bayangan pada Bentuk – Menyesuaikan Blur, Warna, dan Sudut

Menambahkan bayangan bukan sekadar mengaktifkannya; Anda sering ingin menyesuaikan blur, warna, dan arah untuk efek yang realistis.

```python
# Define how blurry the shadow should be (larger = softer)
shadow.blur_radius = 5.0       # Soft edge for a natural look

# Choose the direction (in degrees). 45° points down‑right.
shadow.angle = 45

# Set the shadow color – black works for most cases
shadow.color = aw.drawing.Color.black
```

*Mengapa pengaturan ini?*  
- **Blur radius** menjadikan tepi lebih lembut, mencegah siluet yang keras.  
- **Angle** meniru sumber cahaya; 45° adalah nilai default umum yang tampak seimbang.  
- **Color** bisa berupa objek `Color` apa saja; coba `Color.gray` untuk efek yang lebih lembut.

---

## Langkah 4: Simpan Dokumen sebagai PDF

Setelah bentuk dan bayangannya siap, menyimpan hasilnya menjadi sangat mudah. Aspose.Words menangani konversi ke PDF secara otomatis, menjaga kesetiaan visual.

```python
# Save the document to a PDF file (adjust the path as needed)
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"Document saved to {output_path}")
```

*Output yang diharapkan*: Buka file `ShadowShape.pdf` yang dihasilkan. Anda akan melihat satu halaman dengan persegi panjang 200 × 100 pt, bayangannya terletak 4 pt dari bentuk dengan sudut 45°, diburamkan sebesar 5 pt. Bayangan akan muncul sebagai halo abu‑abu‑hitam yang halus mengelilingi bentuk.

---

## Pertanyaan Umum & Kasus Tepi

### Bagaimana jika saya membutuhkan bentuk lain?

Ganti `aw.drawing.ShapeType.RECTANGLE` dengan nilai enum lain, misalnya `aw.drawing.ShapeType.ELLIPSE`. Properti bayangan yang sama tetap berlaku—tidak perlu kode tambahan.

### Bisakah saya menerapkan bayangan pada beberapa bentuk sekaligus?

Ya. Loop melalui bentuk‑bentuk yang Anda buat dan konfigurasikan masing‑masing `shadow_format` secara individual. Berikut cuplikan singkat:

```python
for shape_type in [aw.drawing.ShapeType.RECTANGLE, aw.drawing.ShapeType.ELLIPSE]:
    shp = builder.insert_shape(shape_type, 150, 80)
    shp.shadow_format.visible = True
    shp.shadow_format.distance = 3.0
    shp.shadow_format.blur_radius = 4.0
```

### Bagaimana cara mengubah opasitas bayangan?

Gunakan properti `shadow.transparency` (0 = opaque, 1 = sepenuhnya transparan):

```python
shadow.transparency = 0.3   # 30 % transparent
```

---

## Contoh Lengkap yang Berfungsi

Berikut adalah skrip lengkap—salin, sesuaikan folder output, dan jalankan. Tidak ada bagian yang hilang.

```python
import aspose.words as aw

# 1️⃣ Create a new document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert a rectangle shape (200 × 100 pt)
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Enable and configure the shadow (add shadow to shape)
shadow = rectangle_shape.shadow_format
shadow.visible = True                # Show the shadow
shadow.blur_radius = 5.0             # Soft edges
shadow.distance = 4.0                # How far the shadow lies from the shape
shadow.angle = 45                    # Direction of the light source
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.0            # Fully opaque (optional)

# 4️⃣ Save as PDF
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"PDF with shape shadow saved at: {output_path}")
```

Jalankan skrip, lalu buka PDF yang dihasilkan. Anda akan melihat persegi panjang dengan bayangan yang tajam dan teroffset—tepat seperti yang dijanjikan oleh **add shadow to shape**.

---

## Kesimpulan

Kami baru saja mendemonstrasikan cara **menambahkan bayangan ke bentuk** dalam dokumen Word menggunakan Aspose.Words untuk Python, mencakup langkah‑langkah penting untuk **mengatur jarak bayangan**, menyesuaikan blur, sudut, dan warna, serta akhirnya mengekspor PDF yang mempertahankan efek tersebut. Teknik ini bekerja untuk semua jenis bentuk, dan Anda dapat memperluasnya dengan loop, penyesuaian opasitas, atau bahkan bayangan gradien.

Siap untuk tantangan berikutnya? Cobalah menggabungkan beberapa bayangan, menumpuk bentuk, atau menghasilkan laporan di mana setiap diagram memiliki bayangan yang distilisasi sendiri. Bereksperimen akan memperkuat konsep dan mengungkap kemungkinan baru untuk otomatisasi dokumen.

Jika Anda menemukan panduan ini berguna, jangan ragu untuk membagikannya, memberi bintang pada repositori Aspose.Words, atau meninggalkan komentar dengan tips penyesuaian bayangan Anda sendiri. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang erat dengan teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}