---
category: general
date: 2026-06-05
description: Contoh Python membuat dokumen Word yang menunjukkan cara menambahkan
  bayangan ke bentuk, menerapkan efek bayangan di Word dengan Aspose.Words.
draft: false
keywords:
- create word document python
- how to add shadow
- add shadow to shape
- apply shadow effect word
- insert shape with shadow
language: id
og_description: Tutorial Python membuat dokumen Word ini memandu Anda menambahkan
  bayangan pada sebuah bentuk, serta menerapkan efek bayangan di Word menggunakan
  Aspose.Words.
og_title: Buat Dokumen Word dengan Python – Tambahkan Bayangan pada Bentuk
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: Create Word document Python example shows how to add shadow to a shape,
    applying shadow effect in Word with Aspose.Words.
  headline: Create Word Document Python – Add Shadow to Shape Guide
  type: TechArticle
- questions:
  - answer: Absolutely. Use `builder.insert_image(...)` to place an image, then access
      `image_shape.shadow_format` just like we did with the rectangle.
    question: Can I add a shadow to a picture instead of a shape?
  - answer: Yes. Aspose.Words preserves shape effects during conversion, so the PDF
      will retain the shadow.
    question: Does the shadow survive when I convert the document to PDF?
  - answer: Call `builder.insert_shape` for each shape, then configure each shape’s
      `shadow_format` independently. No shared state.
    question: What if I need multiple shapes with different shadows?
  - answer: 'Minimal for typical documents. If you’re generating thousands of shapes,
      consider batch processing or limiting blur radius to keep rendering fast. ##
      Conclusion We’ve just demonstrated how to **create Word document python** code
      that inserts a rectangle and **adds shadow to shape** using Aspose.Word'
    question: Is there a performance impact when adding many shadows?
  type: FAQPage
tags:
- python
- aspose-words
- document automation
title: Buat Dokumen Word Python – Panduan Menambahkan Bayangan pada Bentuk
url: /id/python/images-shapes/create-word-document-python-add-shadow-to-shape-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat Dokumen Word dengan Python – Panduan Menambahkan Bayangan pada Bentuk

Pernah bertanya-tanya bagaimana cara **create Word document python** kode yang tidak hanya menyisipkan sebuah bentuk tetapi juga memberikannya bayangan yang halus? Anda bukan satu-satunya. Dalam banyak laporan, faktur, atau selebaran pemasaran, bayangan yang halus dapat membuat sebuah persegi panjang terasa seolah terangkat dari halaman, menambah kedalaman tanpa grafik tambahan.

Dalam tutorial ini kami akan menelusuri contoh lengkap yang dapat dijalankan yang menunjukkan secara tepat **how to add shadow** ke sebuah bentuk menggunakan Aspose.Words untuk Python. Pada akhir tutorial Anda akan memiliki file `.docx` dengan persegi panjang yang memancarkan bayangan lembut berderajat 45 – sempurna untuk membuat dokumen Anda tampak rapi dan profesional.

## Apa yang Dibahas dalam Panduan Ini

Kami akan memulai dengan menyiapkan lingkungan, kemudian membuat dokumen Word baru, menyisipkan persegi panjang, mengonfigurasi properti bayangannya, dan akhirnya menyimpan file. Sepanjang proses kami akan membahas mengapa setiap pengaturan penting, jebakan umum, dan beberapa trik tambahan yang dapat Anda coba. Tidak diperlukan referensi eksternal; semua yang Anda butuhkan ada di sini.

**Prasyarat**

- Python 3.8+ terpasang  
- Paket `aspose-words` (`pip install aspose-words`)  
- Familiaritas dasar dengan sintaks Python (jika Anda pernah menulis “Hello, World!” sebelumnya, Anda sudah siap)

Siap? Mari kita mulai.

## Langkah 1: Inisialisasi Dokumen – Dasar **Create Word Document Python**

Hal pertama yang Anda perlukan adalah objek dokumen kosong dan `DocumentBuilder` yang memungkinkan Anda menambahkan konten. Anggap builder sebagai pena yang menulis ke dalam file Word.

```python
import aspose.words as aw

# Create a new, empty Word document
doc = aw.Document()

# DocumentBuilder gives us a convenient way to add elements
builder = aw.DocumentBuilder(doc)
```

*Mengapa ini penting:* `aw.Document()` adalah titik masuk untuk setiap operasi Aspose.Words. Tanpa itu Anda tidak dapat menambahkan bentuk, teks, atau elemen lain. Builder menyimpan referensi ke dokumen, sehingga Anda tidak perlu mengoper dokumen secara manual.

## Langkah 2: Menyisipkan Persegi Panjang – Menggunakan Logika **Insert Shape With Shadow**

Sekarang kita akan menempatkan persegi panjang pada halaman. Dimensi diukur dalam poin (1 pt ≈ 1/72 inci), jadi 150 × 100 pt memberikan kotak dengan proporsi yang bagus.

```python
# Insert a rectangle shape of 150x100 points
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
```

*Tips pro:* Jika Anda membutuhkan bentuk lain, cukup ganti `ShapeType.RECTANGLE` dengan `ShapeType.ELLIPSE`, `ShapeType.CLOUD`, dll. Kode konfigurasi bayangan yang sama bekerja untuk bentuk apa pun yang Anda pilih.

## Langkah 3: Menerapkan Efek Bayangan – **How To Add Shadow** Secara Tepat

Inilah tempat keajaiban terjadi. Objek `shadow_format` mengontrol visibilitas, jarak, blur, sudut, warna, dan transparansi. Sesuaikan setiap properti untuk mendapatkan tampilan yang Anda inginkan.

```python
# Grab the shadow formatting object
shadow = rectangle_shape.shadow_format

# Make the shadow visible
shadow.visible = True

# Set how far the shadow sits from the shape (in points)
shadow.distance = 5.0

# Blur radius controls softness; higher = fuzzier edges
shadow.blur = 3.0

# Angle determines the light source direction (degrees clockwise from the x‑axis)
shadow.angle = 45

# Choose a color – black works for most professional documents
shadow.color = aw.drawing.Color.black

# Transparency is a float from 0 (opaque) to 1 (fully transparent)
shadow.transparency = 0.4   # 40 % transparent gives a subtle effect
```

**Mengapa setiap pengaturan penting**

| Properti | Penggunaan Umum | Dampak Visual |
|----------|-----------------|---------------|
| `visible` | Mengaktifkan/mematikan efek | Tidak ada bayangan jika `False` |
| `distance` | Mengontrol offset dari bentuk | Nilai lebih besar memindahkan bayangan lebih jauh |
| `blur` | Melunakkan tepi | Blur lebih tinggi = bayangan lebih tersebar |
| `angle` | Mensimulasikan arah cahaya | 0° = bayangan ke kanan, 90° = ke bawah |
| `color` | Menyesuaikan dengan merek atau tema | Bayangan putih jarang masuk akal |
| `transparency` | Menyesuaikan opasitas | 0.0 = solid, 0.8 = hampir tidak terlihat |

*Jebakan umum:* Lupa mengatur `shadow.visible = True` menghasilkan bentuk yang sempurna tetapi tanpa bayangan—mudah terlewat ketika Anda fokus pada warna atau ukuran.

## Langkah 4: Menyimpan Dokumen – Langkah Akhir **Create Word Document Python**

Setelah mengonfigurasi bentuk, cukup tulis dokumen ke disk. Anda dapat memilih format apa pun yang didukung (`.docx`, `.pdf`, `.html`, dll.). Untuk panduan ini kami tetap pada format klasik `.docx`.

```python
# Save the document to the desired location
output_path = "shadowed_shape.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Saat Anda membuka `shadowed_shape.docx` di Microsoft Word (atau penampil kompatibel lainnya), Anda akan melihat persegi panjang dengan bayangan tajam berderajat 45 – tepat seperti yang dijelaskan oleh kode di atas.

### Hasil yang Diharapkan

- File Word satu halaman.  
- Satu persegi panjang terpusat di posisi builder.  
- Bayangan hitam semi‑transparan dengan offset 5 pt, blur 3 pt, dan sudut 45°.

Jika bayangan tidak muncul, periksa kembali bahwa `shadow.visible` bernilai `True` dan Anda menggunakan penampil yang mendukung efek bentuk (sebagian besar versi Word modern melakukannya).

## Bonus: Menyesuaikan Bayangan untuk Gaya Berbeda

Anda mungkin menginginkan tampilan yang lebih lembut untuk laporan korporat, atau bayangan berwarna tebal untuk selebaran pemasaran. Berikut beberapa variasi cepat:

```python
# Soft gray shadow for subtle emphasis
shadow.color = aw.drawing.Color.gray
shadow.transparency = 0.6
shadow.blur = 5.0
shadow.distance = 3.0

# Red, dramatic shadow for a creative brochure
shadow.color = aw.drawing.Color.red
shadow.transparency = 0.2
shadow.blur = 2.0
shadow.angle = 120
```

Mencoba nilai‑nilai ini adalah cara terbaik untuk memahami cara kerja **add shadow to shape** secara praktis.

## Pratinjau Visual (Alt Text Disertakan)

![Shadowed rectangle shape in a Word document – create word document python example](/images/shadowed_rectangle.png)

*Alt text:* *Bentuk persegi panjang dengan bayangan dalam dokumen Word – contoh create word document python.*

## Pertanyaan yang Sering Diajukan

**T: Bisakah saya menambahkan bayangan pada gambar alih-alih bentuk?**  
J: Tentu saja. Gunakan `builder.insert_image(...)` untuk menempatkan gambar, lalu akses `image_shape.shadow_format` seperti yang kami lakukan pada persegi panjang.

**T: Apakah bayangan tetap ada ketika saya mengonversi dokumen ke PDF?**  
J: Ya. Aspose.Words mempertahankan efek bentuk selama konversi, sehingga PDF akan tetap menampilkan bayangan.

**T: Bagaimana jika saya membutuhkan banyak bentuk dengan bayangan berbeda?**  
J: Panggil `builder.insert_shape` untuk setiap bentuk, lalu konfigurasikan `shadow_format` masing‑masing secara terpisah. Tidak ada status yang dibagi.

**T: Apakah ada dampak performa saat menambahkan banyak bayangan?**  
J: Minimal untuk dokumen biasa. Jika Anda menghasilkan ribuan bentuk, pertimbangkan pemrosesan batch atau batasi radius blur untuk menjaga kecepatan rendering.

## Kesimpulan

Kami baru saja menunjukkan cara **create Word document python** kode yang menyisipkan persegi panjang dan **adds shadow to shape** menggunakan Aspose.Words. Dengan mengonfigurasi `shadow_format`, Anda dapat **apply shadow effect word** dokumen dengan kontrol detail atas jarak, blur, sudut, warna, dan transparansi. Pola yang sama berlaku untuk bentuk apa pun, gambar, atau bahkan kotak teks, memberi Anda kotak peralatan serbaguna untuk dokumen yang tampak profesional.

Apa selanjutnya? Coba gabungkan beberapa bentuk, lapisi teks di atasnya, atau ekspor ke PDF untuk melihat bayangan tetap ada setelah konversi. Anda juga dapat menjelajahi efek visual lain seperti glow atau reflection—cukup ganti `shadow_format` dengan `glow_format` atau `reflection_format`.

Selamat coding, semoga dokumen Anda selalu memiliki kedalaman ekstra!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Dokumen Word Kosong dengan Persegi Panjang Berbayangan – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Buat Bentuk Persegi Panjang di Word dengan Aspose.Words – Panduan Langkah‑per‑langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Buat Grup Bentuk dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}