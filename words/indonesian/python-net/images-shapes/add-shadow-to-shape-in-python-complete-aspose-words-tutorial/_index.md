---
category: general
date: 2026-06-08
description: Tambahkan bayangan pada bentuk menggunakan Aspose.Words untuk Python
  dan atur warna isi bentuk dalam beberapa langkah saja. Pelajari alur kerja lengkap
  dengan kode yang dapat dijalankan.
draft: false
keywords:
- add shadow to shape
- set shape fill color
- Aspose.Words Python shadow
- shape formatting Python
- PDF generation Aspose
language: id
og_description: Tambahkan bayangan pada bentuk dengan Aspose.Words untuk Python dan
  atur warna isi bentuk secara instan. Ikuti tutorial langkah demi langkah ini untuk
  membuat output PDF.
og_title: Tambahkan Bayangan pada Bentuk di Python – Panduan Lengkap Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Add shadow to shape using Aspose.Words for Python and set shape fill
    color in just a few steps. Learn the full workflow with runnable code.
  headline: Add Shadow to Shape in Python – Complete Aspose.Words Tutorial
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python and set shape fill
    color in just a few steps. Learn the full workflow with runnable code.
  name: Add Shadow to Shape in Python – Complete Aspose.Words Tutorial
  steps:
  - name: Create the Document and Builder
    text: '```python import aspose.words as aw from aspose.words.drawing import ShadowEffect,
      ShadowType, Color'
  - name: Insert a Rectangle Shape and Set Its Fill Color
    text: '```python # Insert a rectangle shape of width 200 points and height 100
      points. rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE,
      200, 100)'
  - name: Define the Shadow Effect
    text: '```python # Create a new shadow effect object. shape_shadow = ShadowEffect()
      shape_shadow.type = ShadowType.OUTER # outer shadow around the shape shape_shadow.blur_radius
      = 10.0 # softer edges shape_shadow.distance = 5.0 # how far the shadow sits
      from the shape shape_shadow.direction = 45 # angle in'
  - name: Apply the Shadow to the Shape
    text: '```python # Attach the shadow effect to the rectangle. rectangle_shape.shadow_effect
      = shape_shadow ```'
  - name: Save the Document as PDF
    text: '```python # Choose a folder you have write access to. output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
      doc.save(output_path) print(f"Document saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: Menambahkan Bayangan pada Bentuk di Python – Tutorial Lengkap Aspose.Words
url: /id/python/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menambahkan Bayangan ke Bentuk di Python – Tutorial Lengkap Aspose.Words

Pernah bertanya-tanya bagaimana cara **menambahkan bayangan ke bentuk** saat menghasilkan dokumen dengan Aspose.Words untuk Python? Anda tidak sendirian. Baik Anda membuat templat laporan, selebaran pemasaran, atau diagram teknis, bayangan halus dapat membuat persegi panjang menonjol dan terlihat lebih profesional.  

Dalam panduan ini kami juga akan menunjukkan **cara menetapkan warna isi bentuk**, sehingga Anda mendapatkan persegi panjang yang sepenuhnya bergaya siap untuk diekspor ke PDF. Solusinya sederhana, kode siap‑jalan, dan alasan di balik setiap baris dijelaskan dalam bahasa Inggris yang mudah dipahami.

## Apa yang Dibahas dalam Tutorial Ini

- Menginisialisasi dokumen Aspose.Words dan builder.  
- Menyisipkan bentuk persegi panjang dan **menetapkan warna isi**.  
- Mendefinisikan dan menerapkan **efek bayangan** ke bentuk tersebut.  
- Menyimpan hasil sebagai PDF.  
- Contoh lengkap yang dapat dijalankan serta tips untuk menghindari jebakan umum.

Di akhir artikel Anda akan dapat menambahkan persegi panjang bergaya ke file Word atau PDF apa pun dengan hanya beberapa baris Python. Tanpa alat eksternal, tanpa tebak‑tebakan.

> **Prasyarat** – Anda memerlukan Python 3.7+ dan paket `aspose-words` (`pip install aspose-words`). IDE atau editor teks pilihan Anda sudah cukup; Visual Studio Code bekerja dengan baik.

---

## Menambahkan Bayangan ke Bentuk – Langkah demi Langkah

Di bawah ini kami membagi proses menjadi bagian‑bagian logis. Setiap langkah menyertakan kode tepat yang Anda perlukan, penjelasan singkat tentang *mengapa* hal itu penting, dan tip cepat agar tidak terjebak di kemudian hari.

### Langkah 1: Membuat Dokumen dan Builder

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowType, Color

# Create a new, empty document.
doc = aw.Document()

# DocumentBuilder gives us a convenient way to add content.
builder = aw.DocumentBuilder(doc)
```

**Mengapa ini penting:** `Document` adalah wadah untuk segala hal—halaman, gaya, gambar, dan bentuk. `DocumentBuilder` adalah API tingkat tinggi yang memungkinkan kita menempatkan objek tanpa harus memikirkan struktur node tingkat rendah.

### Langkah 2: Menyisipkan Bentuk Persegi Panjang dan Menetapkan Warna Isi

```python
# Insert a rectangle shape of width 200 points and height 100 points.
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Set the interior color of the shape.
rectangle_shape.fill_color = Color.BLUE   # <-- set shape fill color
```

**Mengapa ini penting:** Bentuk berfungsi seperti kanvas untuk bayangan kita. Dengan **menetapkan warna isi bentuk** kita memastikan persegi panjang bukan sekadar kotak transparan; ia menjadi elemen yang terlihat sehingga bayangan dapat menekankannya. Anda dapat mengganti `Color.BLUE` dengan nilai RGB apa pun atau bahkan gradien jika memerlukan tampilan lebih menarik.

> **Tip pro:** Jika Anda berencana menggunakan warna yang sama pada banyak bentuk, simpan dalam variabel (`my_fill = Color.from_argb(0, 120, 200, 255)`) dan gunakan kembali referensi tersebut.

### Langkah 3: Mendefinisikan Efek Bayangan

```python
# Create a new shadow effect object.
shape_shadow = ShadowEffect()
shape_shadow.type = ShadowType.OUTER          # outer shadow around the shape
shape_shadow.blur_radius = 10.0               # softer edges
shape_shadow.distance = 5.0                   # how far the shadow sits from the shape
shape_shadow.direction = 45                   # angle in degrees (45° = diagonal)
shape_shadow.color = Color.from_argb(128, 0, 0, 0)  # semi‑transparent black
```

**Mengapa ini penting:** Bayangan bukan sekadar gimmick visual; ia menyampaikan kedalaman dan hierarki. `blur_radius` mengontrol kelembutan, `distance` menentukan offset, dan `direction` memungkinkan Anda mensimulasikan sumber cahaya. Sesuaikan nilai‑nilai ini agar cocok dengan bahasa desain Anda.

### Langkah 4: Menerapkan Bayangan ke Bentuk

```python
# Attach the shadow effect to the rectangle.
rectangle_shape.shadow_effect = shape_shadow
```

**Mengapa ini penting:** Sampai baris ini dijalankan, bentuk tetap datar. Menetapkan `shadow_effect` memberi tahu Aspose.Words untuk merender persegi panjang dengan bayangan yang telah didefinisikan saat dokumen disimpan.

### Langkah 5: Menyimpan Dokumen sebagai PDF

```python
# Choose a folder you have write access to.
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

**Mengapa ini penting:** Menyimpan sebagai PDF mengunci gaya visual, membuat bayangan muncul persis seperti yang Anda rancang. Anda juga dapat menyimpan sebagai `.docx` jika membutuhkan penyuntingan lebih lanjut—Aspose.Words menangani kedua format dengan mulus.

---

## Menetapkan Warna Isi Bentuk – Menyesuaikan Penampilan

Jika Anda membutuhkan nuansa yang berbeda, ganti penugasan `Color.BLUE` dengan salah satu contoh berikut:

```python
# Solid RGB color
rectangle_shape.fill_color = Color.from_argb(255, 255, 165, 0)   # orange

# Semi‑transparent fill
rectangle_shape.fill_color = Color.from_argb(128, 0, 128, 0)    # 50% transparent green
```

> **Mengapa Anda mungkin menginginkannya:** Isi semi‑transparan yang dipadukan dengan bayangan dapat menciptakan efek “kaca” yang populer dalam mock‑up UI modern.

---

## Contoh Lengkap yang Berfungsi

Berikut seluruh skrip dalam satu blok. Salin‑tempel ke file bernama `shadow_shape.py` dan jalankan—dengan asumsi Anda telah menginstal `aspose-words`.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowType, Color

# 1️⃣ Create document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2️⃣ Insert rectangle and set fill color
rect = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
rect.fill_color = Color.BLUE          # set shape fill color

# 3️⃣ Configure shadow
shadow = ShadowEffect()
shadow.type = ShadowType.OUTER
shadow.blur_radius = 10.0
shadow.distance = 5.0
shadow.direction = 45
shadow.color = Color.from_argb(128, 0, 0, 0)

# 4️⃣ Apply shadow
rect.shadow_effect = shadow

# 5️⃣ Save as PDF
output = "ShadowShape.pdf"
doc.save(output)
print(f"✅ PDF generated: {output}")
```

**Output yang diharapkan:** Buka `ShadowShape.pdf` dan Anda akan melihat persegi panjang biru dengan bayangan hitam lembut, diagonal, yang bergeser ke kanan‑bawah. Bayangan akan tampak sedikit blur, memberi kesan bentuk terangkat.

---

## Kesalahan Umum & Tip Pro

| Masalah | Mengapa Terjadi | Solusi |
|------|----------------|-----|
| **Bayangan tidak terlihat** | Isi bentuk sepenuhnya transparan atau penampil PDF menonaktifkan bayangan. | Pastikan `fill_color` tidak transparan (`alpha = 255`) atau sesuaikan opasitas `color` pada bayangan. |
| **Kesalahan jalur file** | `YOUR_DIRECTORY` tidak ada atau Anda tidak memiliki izin menulis. | Gunakan `os.makedirs("YOUR_DIRECTORY", exist_ok=True)` sebelum `doc.save`. |
| **Import tidak tepat** | Mencoba mengimpor `ShadowEffect` dari sub‑modul yang salah. | Impor persis seperti yang ditunjukkan: `from aspose.words.drawing import ShadowEffect, ShadowType, Color`. |
| **Warna tidak sesuai harapan** | Menggunakan `Color.from_argb` dengan urutan yang salah (alpha, merah, hijau, biru). | Ingat urutannya: **alpha**, **red**, **green**, **blue**. |

---

## Langkah Selanjutnya – Perluas Toolkit Bentuk Anda

Sekarang Anda tahu cara **menambahkan bayangan ke bentuk** dan **menetapkan warna isi bentuk**, Anda dapat menjelajahi:

- **Isi gradien** (`LinearGradientBrush`) untuk latar belakang yang lebih kaya.  
- **Beberapa bayangan** (inner + outer) dengan menumpuk objek `ShadowEffect`.  
- **Jenis bentuk lain** (`Ellipse`, `Polygon`) untuk membuat ikon atau elemen diagram alur.  
- **Menyematkan PDF** ke respons web atau lampiran email menggunakan Flask atau Django.

Setiap topik ini dibangun di atas konsep inti yang dibahas di sini, sehingga Anda akan merasa nyaman melanjutkannya.

---

## Kesimpulan

Kami telah membahas proses lengkap **menambahkan bayangan ke bentuk** di Aspose.Words untuk Python sekaligus **menetapkan warna isi bentuk**. Dari pembuatan dokumen hingga ekspor PDF, kode bersifat mandiri dan siap pakai dalam produksi.  

Silakan sesuaikan radius blur, jarak, atau warna agar sesuai dengan pedoman merek Anda. Jika Anda menemukan kasus khusus atau memiliki permintaan fitur, tinggalkan komentar di bawah—selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang memperluas teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Menyiapkan Lisensi Aspose.Words di Python](/words/english/python-net/getting-started/aspose-words-license-python-setup/)
- [Membuat bentuk persegi panjang di Word dengan Aspose.Words – Panduan Langkah demi Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Tutorial Bayangan Bentuk Aspose.Words – Menambahkan Bayangan ke Bentuk Word dalam C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}