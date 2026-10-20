---
category: general
date: 2026-06-24
description: Buat bentuk persegi panjang di Python dengan Aspose.Words, pelajari cara
  menambahkan bayangan ke bentuk, mengatur sudut bayangan, dan menyimpan dokumen sebagai
  PDF dalam hitungan menit.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shape shadow
- set shadow angle
language: id
og_description: Buat bentuk persegi panjang di Python, tambahkan bayangan ke bentuk,
  atur sudut bayangan, dan simpan dokumen sebagai PDF dengan Aspose.Words. Ikuti panduan
  langkah demi langkah ini.
og_title: Buat Bentuk Persegi Panjang di Python – Tutorial Lengkap Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  headline: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  name: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: What if I need a different shape?
    text: Aspose.Words supports many `ShapeType` values (ellipse, star, callout, etc.).
      Simply replace `aw.drawing.ShapeType.RECTANGLE` with the desired enum, like
      `aw.drawing.ShapeType.ELLIPSE`.
  - name: Can I add multiple shadows?
    text: The API exposes only one `ShadowFormat` per shape, but you can simulate
      multiple shadows by duplicating the shape, offsetting each copy, and adjusting
      transparency.
  - name: How do I change the shadow color to match my brand?
    text: Just set `shadow.color` to any `aw.drawing.Color`. For a brand blue, use
      `aw.drawing.Color.from_argb(255, 0, 120, 215)`.
  - name: What about saving as DOCX instead of PDF?
    text: Replace `document.save(pdf_path)` with `document.save("output/shadowed_rectangle.docx")`.
      The shadow rendering is preserved across both formats.
  - name: Does the shadow work on older PDF viewers?
    text: Aspose.Words renders the shadow as a vector effect, which is widely supported.
      However, very old viewers might flatten the effect; testing on your target audience’s
      devices is always a good habit.
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Buat Bentuk Persegi Panjang di Python – Panduan Lengkap Aspose.Words
url: /id/python/images-shapes/create-rectangle-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat Bentuk Persegi Panjang di Python – Panduan Lengkap Aspose.Words

Pernah bertanya-tanya bagaimana cara **create rectangle shape** dalam dokumen Word menggunakan Python? Mungkin Anda membutuhkan kotak panggilan tebal, petunjuk visual untuk diagram, atau sekadar persegi panjang yang menarik untuk laporan. Apapun itu, Anda berada di tempat yang tepat. Dalam tutorial ini kami akan membahas seluruh proses—dari menyisipkan persegi panjang, menambahkan bayangan halus, menyesuaikan sudut bayangan, hingga akhirnya **save document as PDF** sehingga Anda dapat membagikannya kepada siapa saja.

Kami akan menggunakan **Aspose.Words for Python via .NET**, sebuah perpustakaan kuat yang memungkinkan Anda memanipulasi file Word tanpa harus membuka Word itu sendiri. Pada akhir panduan ini Anda akan dapat menjawab pertanyaan *“how to add shape shadow”* dengan percaya diri, dan Anda akan memiliki skrip siap‑jalankan yang dapat Anda masukkan ke dalam proyek apa pun.

---

## Apa yang Anda Butuhkan

- **Python 3.8+** terinstal di mesin Anda.  
- **Aspose.Words for Python via .NET** (`aspose-words` package). Instal dengan:

  ```bash
  pip install aspose-words
  ```

- Folder yang dapat ditulisi dimana PDF yang dihasilkan akan disimpan.  
- (Opsional) IDE atau editor teks—VS Code sangat cocok.

Itu saja. Tidak ada DLL tambahan, tidak perlu instalasi Office, hanya satu paket pip.

## Langkah 1: Siapkan Dokumen dan Builder

Hal pertama yang perlu Anda lakukan adalah membuat objek yang ramah **create rectangle shape**: sebuah `Document` dan `DocumentBuilder`. Anggap builder sebagai pena Anda; ia menggambar semuanya untuk Anda.

```python
import aspose.words as aw

# Initialize a new blank document
document = aw.Document()

# DocumentBuilder gives us a convenient way to add content
builder = aw.DocumentBuilder(document)
```

> **Mengapa ini penting:** Objek `Document` mewakili seluruh file .docx, sementara `DocumentBuilder` menyediakan metode seperti `insert_shape` yang memudahkan menggambar bentuk.

## Langkah 2: Sisipkan Bentuk Persegi Panjang

Sekarang kita memiliki builder, kita akhirnya dapat **create rectangle shape**. Metode `insert_shape` membutuhkan tiga argumen: tipe bentuk, lebar, dan tinggi. Kami akan menggunakan lebar 200 pt dan tinggi 100 pt untuk proporsi yang bagus.

```python
# Insert a rectangle with a width of 200 points and a height of 100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

Pada titik ini Anda telah berhasil **create rectangle shape** dalam dokumen Anda. Jika Anda membuka DOCX yang dihasilkan (kami akan melakukannya nanti), Anda akan melihat persegi panjang polos yang berada di tempat kursor berada.

## Langkah 3: Akses Objek Shadow Formatting

Untuk **add shadow to shape**, pertama-tama kita perlu mengambil format bayangan bentuk tersebut. Setiap bentuk di Aspose.Words memiliki properti `shadow_format` yang menampilkan semua pengaturan terkait bayangan.

```python
# Grab the shadow formatting object for later tweaks
shadow = rectangle.shadow_format
```

Memiliki referensi `shadow` memungkinkan kita mengatur visibilitas, blur, jarak, sudut, warna, dan transparansi—semua dalam beberapa baris kode.

## Langkah 4: Aktifkan Bayangan dan Konfigurasikan Penampilannya

Inilah tempat keajaiban terjadi. Kami akan **add shadow to shape**, membuatnya sedikit blur, menggesernya sedikit, mengatur arah (bagian **set shadow angle**), dan memberikan nuansa hitam semi‑transparan.

```python
# Turn the shadow on
shadow.visible = True

# Soften the edges – a blur radius of 8 points looks natural
shadow.blur_radius = 8.0

# Push the shadow away from the rectangle by 5 points
shadow.distance = 5.0

# Set the direction of the light source – 45 degrees creates a diagonal drop
shadow.angle = 45

# Choose a color; black works well for most documents
shadow.color = aw.drawing.Color.black

# Make the shadow 30 % transparent for a subtle effect
shadow.transparency = 0.3
```

> **Tips pro:** Jika Anda pernah membutuhkan efek yang lebih dramatis, tingkatkan `blur_radius` atau turunkan `transparency`. Sebaliknya, bayangan tajam dan sepenuhnya tidak transparan dapat dicapai dengan `blur_radius = 0` dan `transparency = 0`.

## Langkah 5: Simpan Dokumen sebagai PDF

Kami telah **create rectangle shape**, kami telah **add shadow to shape**, dan sekarang kami akan **save document as PDF** sehingga hasilnya terlihat identik di perangkat apa pun. Aspose.Words membuat ini menjadi satu baris kode.

```python
# Define where you want the PDF to land
output_path = "output/shadowed_rectangle.pdf"

# Save the whole document (including the rectangle with its shadow) as PDF
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Menjalankan skrip akan menghasilkan `shadowed_rectangle.pdf` di folder `output`. Buka dengan penampil PDF apa pun dan Anda akan melihat persegi panjang bersih dengan bayangan lembut berderajat 45—tepat seperti yang kami konfigurasikan.

## Contoh Lengkap yang Berfungsi

Berikut adalah skrip lengkap yang siap dijalankan yang menggabungkan semua langkah di atas. Salin‑tempel ke dalam file bernama `create_rectangle_with_shadow.py` dan jalankan `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Initialize document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert the rectangle shape (200 pt × 100 pt)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Access shadow formatting
shadow = rectangle.shadow_format

# 4️⃣ Configure shadow – visible, blurred, offset, angled, colored, semi‑transparent
shadow.visible = True
shadow.blur_radius = 8.0          # softer edges
shadow.distance = 5.0            # how far the shadow sits from the shape
shadow.angle = 45                # direction in degrees – this is the **set shadow angle** step
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.3        # 30 % transparent

# 5️⃣ Save the document as PDF
pdf_path = os.path.join(output_dir, "shadowed_rectangle.pdf")
document.save(pdf_path)

print(f"✅ PDF created at: {pdf_path}")
```

**Output yang diharapkan:** Sebuah file PDF yang menampilkan satu persegi panjang dengan bayangan diagonal yang lembut. Tidak ada halaman ekstra, tidak ada artefak tersembunyi—hanya bentuk yang kami buat.

## Pertanyaan Umum & Kasus Tepi

### Bagaimana jika saya membutuhkan bentuk lain?

Aspose.Words mendukung banyak nilai `ShapeType` (ellipse, star, callout, dll.). Cukup ganti `aw.drawing.ShapeType.RECTANGLE` dengan enum yang diinginkan, seperti `aw.drawing.ShapeType.ELLIPSE`.

### Bisakah saya menambahkan beberapa bayangan?

API hanya menyediakan satu `ShadowFormat` per bentuk, tetapi Anda dapat mensimulasikan beberapa bayangan dengan menduplikasi bentuk, menggeser setiap salinan, dan menyesuaikan transparansi.

### Bagaimana cara mengubah warna bayangan agar sesuai dengan merek saya?

Cukup atur `shadow.color` ke `aw.drawing.Color` apa pun. Untuk biru merek, gunakan `aw.drawing.Color.from_argb(255, 0, 120, 215)`.

### Bagaimana dengan menyimpan sebagai DOCX alih-alih PDF?

Ganti `document.save(pdf_path)` dengan `document.save("output/shadowed_rectangle.docx")`. Rendering bayangan dipertahankan di kedua format.

### Apakah bayangan berfungsi pada penampil PDF lama?

Aspose.Words merender bayangan sebagai efek vektor, yang didukung secara luas. Namun, penampil yang sangat lama mungkin meratakan efek tersebut; menguji pada perangkat audiens target Anda selalu merupakan kebiasaan yang baik.

## Tips untuk Mempercantik PDF Anda

- **Add a border:** `rectangle.line_format.width = 1.5` dan atur warna untuk garis tepi yang tajam.  
- **Center the rectangle:** Gunakan `builder.move_to_document_start()` sebelum menyisipkan, lalu `builder.paragraph_format.alignment = aw.ParagraphAlignment.CENTER`.  
- **Combine with text:** Sisipkan `TextFragment` setelah persegi panjang untuk memberi label, misalnya, `"Important Section"`.

Penyesuaian kecil ini dapat mengubah persegi panjang polos menjadi kotak panggilan yang dipoles dan terlihat profesional dalam laporan, proposal, atau e‑book.

## Kesimpulan

Anda kini memiliki resep lengkap, dari awal hingga akhir, untuk **create rectangle shape** di Python, **add shadow to shape**, **set shadow angle**, dan **save document as PDF** menggunakan Aspose.Words. Langkah‑langkahnya sederhana, kode sepenuhnya mandiri, dan Anda telah melihat mengapa setiap baris penting—dari menginisialisasi dokumen hingga memoles PDF akhir.

Selanjutnya, Anda mungkin ingin mengeksplorasi **how to add shape shadow** pada gambar yang lebih kompleks, bereksperimen dengan isian gradien, atau menghasilkan tabel di dalam bentuk Anda. Perpustakaan ini juga mendukung penautan bentuk ke bookmark, yang dapat berguna untuk PDF interaktif.

Ada variasi yang Anda coba? Bagikan di komentar, atau ajukan pertanyaan apa pun yang masih tersisa. Selamat coding, dan nikmati menambahkan kedalaman ekstra pada dokumen Anda!

![Rectangle shape with shadow – example of create rectangle shape in Python](/images/rectangle-shadow.png)


## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Dokumen Word Java – Tambahkan Bentuk Persegi Panjang dengan Efek Bayangan](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Tutorial Bayangan Bentuk Aspose.Words – Tambahkan Bayangan ke Bentuk Word di C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Buat bentuk persegi panjang di Word menggunakan C# – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}