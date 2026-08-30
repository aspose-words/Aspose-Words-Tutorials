---
category: general
date: 2026-05-04
description: Pelajari cara membuat bentuk persegi panjang, menambahkan bentuk dengan
  bayangan, mengubah warna bayangan, mengatur jarak bayangan, dan menyimpan dokumen
  sebagai PDF menggunakan Aspose.Words untuk Python.
draft: false
keywords:
- create rectangle shape
- how to add shape
- change shadow color
- save document as pdf
- set shadow distance
language: id
og_description: Buat bentuk persegi panjang dengan Aspose.Words untuk Python, pelajari
  cara menambahkan bentuk, mengubah warna bayangan, mengatur jarak bayangan, dan menyimpan
  dokumen sebagai PDF.
og_title: Buat bentuk persegi panjang – Tambahkan bayangan, ubah warna, dan simpan
  sebagai PDF
tags:
- Aspose.Words
- Python
- PDF generation
title: Membuat bentuk persegi panjang di Python – Panduan Lengkap Menambahkan Bayangan
  & Menyimpan sebagai PDF
url: /id/python/images-shapes/create-rectangle-shape-in-python-full-guide-to-adding-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat Bentuk Persegi Panjang – Tutorial Lengkap untuk Pengembang Python

Pernahkah Anda perlu **membuat bentuk persegi panjang** dalam dokumen Word dan bertanya‑tanya bagaimana memberi bayangan yang halus? Mungkin Anda sedang membangun generator laporan dan tampilan visual sangat penting—terutama ketika output akhir berupa PDF. Kabar baiknya? Dengan Aspose.Words untuk Python Anda tidak hanya dapat **menambahkan bentuk**, tetapi juga menyesuaikan setiap properti bayangan, mulai dari warna hingga jarak, dan kemudian **menyimpan dokumen sebagai pdf** dalam satu alur yang mulus.

Dalam panduan ini kami akan membahas seluruh proses langkah demi langkah. Anda akan melihat kode persis yang dapat Anda salin‑tempel, memahami *mengapa* setiap baris penting, dan mendapatkan beberapa tips untuk menangani kasus tepi (seperti bayangan transparan atau DPI non‑standar). Pada akhir tutorial Anda akan dapat **membuat bentuk persegi panjang**, menyesuaikan bayangannya, dan mengekspor PDF yang tajam tanpa kesulitan.

## Prasyarat

- Python 3.8+ terpasang di mesin Anda.  
- Aspose.Words untuk Python via `pip install aspose-words`.  
- Familiaritas dasar dengan Python berorientasi objek (tidak ada yang rumit).  

Jika Anda sudah memiliki lingkungan virtual, cukup jalankan perintah instalasi dan Anda siap mulai.

## Langkah 1: Inisialisasi Dokumen dan Builder

Sebelum Anda dapat **menambahkan bentuk**, Anda memerlukan dokumen kosong untuk bekerja. Kelas `Document` mewakili seluruh file, dan `DocumentBuilder` adalah kuas Anda.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder to edit it
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

*Mengapa ini penting:* `Document` menyimpan semua bagian, halaman, dan sumber daya. `DocumentBuilder` memberi Anda API yang fluida untuk menyisipkan konten tepat di tempat yang Anda inginkan—bayangkan seperti kursor di pengolah kata.

## Langkah 2: Sisipkan Bentuk Persegi Panjang

Sekarang kita benar‑benar **menambahkan bentuk**. Metode `insert_shape` memerlukan tipe bentuk dan dimensinya (dalam poin). Di sini kami memilih persegi panjang 200 × 100 pt dan memberi isian biru‑muda.

```python
# Step 2: Insert a rectangle shape and give it a light‑blue fill
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,  # shape type
    200,                            # width in points
    100)                            # height in points
rectangle_shape.fill_color = aw.Color.light_blue
```

*Tip profesional:* Jika Anda perlu menyesuaikan bentuk dengan teks yang sudah ada, gunakan `builder.move_to` sebelum menyisipkan, atau sesuaikan properti `left`/`top` setelah pembuatan.

## Langkah 3: Aktifkan Bayangan

Sebuah bentuk tanpa bayangan terlihat datar. Untuk **mengatur jarak bayangan** dan membuat efeknya terlihat, ambil format bayangan dan aktifkan.

```python
# Step 3: Access the shape's shadow format and make the shadow visible
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
```

*Mengapa langkah ini:* Format bayangan adalah objek terpisah; mengubah `visible` adalah hal pertama yang harus dilakukan, jika tidak semua properti bayangan lainnya akan diabaikan.

## Langkah 4: Gaya Bayangan – Warna, Blur, Jarak, Arah

Inilah bagian di mana keajaiban terjadi. Kami akan **mengubah warna bayangan**, menyesuaikan radius blur, menentukan seberapa jauh bayangan berada dari persegi panjang, dan memutarnya 45°.

```python
# Step 4: Configure the appearance of the shadow
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER   # outer shadow
rectangle_shadow.blur_radius = 10.0                    # blur amount (pixels)
rectangle_shadow.distance = 5.0                        # distance from the shape
rectangle_shadow.direction = 45.0                     # angle in degrees
rectangle_shadow.color = aw.Color.gray                 # shadow colour
```

*Penjelasan tiap properti:*

| Properti | Fungsinya | Nilai umum |
|----------|-----------|------------|
| `style` | Menentukan apakah bayangan *inner* atau *outer*. | `OUTER` (paling umum) |
| `blur_radius` | Mengontrol kelembutan; nilai lebih tinggi = tepi lebih kabur. | 0–20 px biasanya |
| `distance` | Seberapa jauh bayangan dipindahkan dari bentuk. | 0–10 pt untuk halus, >10 untuk dramatis |
| `direction` | Sudut sumber cahaya, diukur searah jarum jam dari sumbu x. | 0‑360° |
| `color` | Warna bayangan. | Semua `aw.Color` (misalnya `gray`, `dark_red`) |

*Kasus tepi:* Jika Anda menetapkan `distance` ke `0` bayangan akan berada tepat di bawah bentuk, sehingga menghilangkan tampilan isian bentuk. Jaga nilai di atas `0` agar offset terlihat.

## Langkah 5: Simpan Dokumen sebagai PDF

Akhirnya, kami **menyimpan dokumen sebagai pdf**. Aspose.Words secara otomatis merasterisasi bayangan, sehingga PDF terlihat persis seperti tampilan Word.

```python
# Step 5: Save the document as a PDF with the shadowed shape
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

*Mengapa PDF?* PDF mempertahankan tata letak di semua platform, menjadikannya sempurna untuk laporan, faktur, atau artefak yang akan dicetak.

---

![Create rectangle shape with shadow](https://example.com/images/rectangle-shadow.png){: .align-center alt="contoh membuat bentuk persegi panjang dengan bayangan"}

*Gambar di atas menunjukkan output PDF akhir – persegi panjang biru‑muda dengan bayangan luar abu‑abu lembut, persis seperti yang kami konfigurasikan.*

## Pertanyaan Umum & Variasi

### Bagaimana jika saya membutuhkan bayangan yang **transparan**?

Atur kanal alfa pada warna bayangan:

```python
transparent_gray = aw.Color.from_argb(128, 0, 0, 0)  # 50% opacity black
rectangle_shadow.color = transparent_gray
```

### Bisakah saya menerapkan bayangan yang sama ke beberapa bentuk?

Ya. Ambil `ShadowFormat` dari satu bentuk dan tetapkan ke bentuk lain:

```python
another_shape = builder.insert_shape(aw.drawing.ShapeType.ELLIPSE, 150, 150)
another_shape.shadow_format = rectangle_shadow.clone()
```

### Bagaimana cara mengubah bayangan untuk **tipe bentuk lain**?

Semua tipe bentuk menggunakan properti `ShadowFormat` yang sama, jadi Anda dapat menggunakan kembali blok konfigurasi yang sama—cukup ganti `ShapeType.RECTANGLE` dengan `ShapeType.OVAL`, `ShapeType.TRIANGLE`, dll.

### Bagaimana dengan **PDF resolusi tinggi** untuk cetak?

Tentukan `PdfSaveOptions` dengan DPI yang lebih tinggi:

```python
options = aw.saving.PdfSaveOptions()
options.image_resolution = 300  # 300 DPI for print quality
document.save(output_path, options)
```

## Ringkasan

Kami telah membahas semua yang Anda perlukan untuk **membuat bentuk persegi panjang**, **menambahkan bentuk**, menyesuaikan **warna bayangan**, **mengatur jarak bayangan**, dan akhirnya **menyimpan dokumen sebagai pdf**. Skrip lengkap yang dapat dijalankan terlihat seperti ini:

```python
import aspose.words as aw

# Initialise document
document = aw.Document()
builder = aw.DocumentBuilder(document)

# Insert rectangle shape
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle_shape.fill_color = aw.Color.light_blue

# Enable and style shadow
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER
rectangle_shadow.blur_radius = 10.0
rectangle_shadow.distance = 5.0
rectangle_shadow.direction = 45.0
rectangle_shadow.color = aw.Color.gray

# Save as PDF
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Jalankan skrip, buka `ShadowedShape.pdf` yang dihasilkan, dan Anda akan melihat persegi panjang tajam dengan bayangan abu‑abu halus—tepat seperti yang diharapkan dari laporan yang diformat secara profesional.

## Apa Selanjutnya?

- **Jelajahi tipe bentuk lain** (`ShapeType.OVAL`, `ShapeType.LINE`) untuk memperkaya dokumen Anda.  
- **Gabungkan beberapa bayangan** dengan menumpuk bentuk; Anda bahkan dapat membuat efek “glow” menggunakan bayangan dalam dengan warna cerah.  
- **Otomatisasi pemrosesan batch**: iterasi koleksi baris data, hasilkan satu bentuk per baris, dan gabungkan semuanya menjadi satu PDF.  
- **Integrasikan dengan pustaka Aspose lainnya** (misalnya Aspose.Slides) jika Anda perlu mengekspor visual yang sama ke PowerPoint.

Silakan bereksperimen—ubah `blur_radius`, mainkan `direction`, atau ganti `gray` dengan warna khas merek Anda. API cukup fleksibel sehingga beberapa penyesuaian dapat mengubah dampak visual secara signifikan.

Punya pertanyaan atau skenario rumit? Tinggalkan komentar di bawah atau sapa forum komunitas Aspose. Selamat coding, dan nikmati persegi panjang dengan bayangan yang indah!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}