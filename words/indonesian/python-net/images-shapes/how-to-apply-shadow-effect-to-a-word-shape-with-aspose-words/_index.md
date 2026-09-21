---
category: general
date: 2026-09-21
description: Pelajari cara menerapkan efek bayangan pada bentuk Word menggunakan Aspose.Words
  untuk Python. Panduan ini menunjukkan cara menambahkan bayangan, mengatur warna
  bayangan, dan menyimpan dokumen yang telah diedit.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- apply shadow effect
- how to add shadow
- add shadow to shape
- set shadow color
- save edited document
language: id
lastmod: 2026-09-21
og_description: Terapkan efek bayangan pada bentuk Word menggunakan Aspose.Words untuk
  Python. Ikuti panduan langkah demi langkah untuk menambahkan bayangan, mengatur
  warna bayangan, dan menyimpan dokumen yang diedit secara efisien.
og_image_alt: Screenshot of a Word document showing a shape with a custom shadow applied
  via Aspose.Words Python code
og_title: Terapkan efek bayangan pada bentuk Word dengan Aspose.Words di Python
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to apply shadow effect to a Word shape using Aspose.Words
    for Python. This guide shows how to add shadow, set shadow color, and save edited
    document.
  headline: How to apply shadow effect to a Word shape with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- shadow effect
title: Cara menerapkan efek bayangan pada bentuk Word dengan Aspose.Words
url: /id/python/images-shapes/how-to-apply-shadow-effect-to-a-word-shape-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menerapkan efek bayangan pada bentuk Word dengan Aspose.Words

Jika Anda perlu **menerapkan efek bayangan** pada sebuah bentuk dalam dokumen Word, tutorial ini menunjukkan secara tepat caranya. Dengan menggunakan Aspose.Words untuk Python Anda dapat **menambahkan bayangan ke bentuk**, mengontrol **mengatur warna bayangan**, dan **menyimpan dokumen yang telah diedit** tanpa harus membuka Word secara manual.

Pada bagian di bawah ini Anda akan mempelajari alur kerja lengkap—dari memuat file .docx, mengambil bentuk target, mengonfigurasi properti bayangan, hingga menulis hasilnya kembali ke disk. Tidak diperlukan alat eksternal, dan kode ini bekerja dengan Aspose.Words 23.9 atau yang lebih baru.

## Prasyarat

* Python 3.8 atau yang lebih baru terpasang.
* Lisensi Aspose.Words untuk Python yang aktif (atau kunci evaluasi gratis).
* File Word (`input.docx`) yang berisi setidaknya satu bentuk (misalnya, persegi panjang atau gambar).

Anda dapat menginstal pustaka dengan pip:

```bash
pip install aspose-words
```

## Langkah 1: Muat dokumen Word

Langkah pertama dalam **cara menambahkan bayangan** adalah membuka file sumber. Aspose.Words merepresentasikan sebuah dokumen dengan kelas `Document`.

```python
# Import the Aspose.Words library
import aspose.words as aw

# Load the Word document from the local folder
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*Mengapa ini penting:* Memuat file membuat model objek dalam memori yang dapat Anda manipulasi secara programatik. Instance `Document` memberi Anda akses ke setiap node, termasuk bentuk.

## Langkah 2: Ambil bentuk yang ingin Anda modifikasi

Sebuah dokumen Word dapat berisi banyak bentuk. Untuk kesederhanaan, contoh ini mengambil **bentuk pertama** (indeks 0). Jika Anda membutuhkan bentuk tertentu, Anda dapat mengiterasi `doc.get_child_nodes`.

```python
# Retrieve the first shape in the document hierarchy
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
```

*Tip:* Gunakan `True` untuk parameter `isDeep` agar mencari seluruh pohon dokumen, bukan hanya anak langsung.

## Langkah 3: Konfigurasikan tampilan bayangan bentuk

Sekarang kita **menambahkan bayangan ke bentuk** dan menyesuaikan properti visualnya. Objek `Shadow` mengontrol blur, offset, dan warna.

```python
# Configure shadow blur (softness)
shape.shadow.blur = 5.0               # Higher value = softer shadow

# Set horizontal and vertical offsets
shape.shadow.offset_x = 2.0           # Moves shadow right
shape.shadow.offset_y = 2.0           # Moves shadow down

# Set the shadow color – this is the **set shadow color** step
shape.shadow.color = aw.Color.black   # You can use any aw.Color (e.g., aw.Color.red)
```

### Mengapa pengaturan ini?

* **Blur** menentukan seberapa tersebar bayangan terlihat. Nilai `5.0` memberikan tampilan yang halus dan profesional.
* **OffsetX/Y** menggeser bayangan relatif terhadap bentuk, menciptakan kedalaman.
* **Color** memungkinkan Anda menyesuaikan dengan merek atau pedoman desain. Menggunakan `aw.Color.black` adalah default yang aman, tetapi warna RGB apa pun dapat digunakan.

Anda dapat bereksperimen dengan properti lain seperti `shape.shadow.opacity` (rentang 0‑1) untuk bayangan semi‑transparan.

## Langkah 4: Simpan dokumen yang telah diedit

Setelah menerapkan bayangan, Anda harus **menyimpan dokumen yang diedit** untuk mempertahankan perubahan. Aspose.Words menulis file dalam format yang sama dengan yang dimuat, kecuali Anda menentukan format lain.

```python
# Save the document with the updated shape
doc.save("YOUR_DIRECTORY/output.docx")
```

*Hasil:* Membuka `output.docx` di Microsoft Word akan menampilkan bentuk asli yang kini ditampilkan dengan bayangan hitam, sedikit bergeser.

## Contoh lengkap yang dapat dijalankan

Menggabungkan semua langkah memberikan Anda satu skrip yang dapat Anda salin‑tempel dan jalankan:

```python
# ------------------------------------------------------------
# Apply shadow effect to a shape in a Word document using
# Aspose.Words for Python. This script demonstrates:
#   • how to add shadow
#   • add shadow to shape
#   • set shadow color
#   • save edited document
# ------------------------------------------------------------

import aspose.words as aw

# 1️⃣ Load the source document
doc = aw.Document("YOUR_DIRECTORY/input.docx")

# 2️⃣ Get the first shape (change the index if needed)
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# 3️⃣ Apply shadow settings
shape.shadow.blur = 5.0               # Soft shadow
shape.shadow.offset_x = 2.0           # Horizontal shift
shape.shadow.offset_y = 2.0           # Vertical shift
shape.shadow.color = aw.Color.black   # Shadow color (black)

# 4️⃣ Write the result back to disk
doc.save("YOUR_DIRECTORY/output.docx")

print("Shadow effect applied and document saved as output.docx")
```

### Output yang diharapkan

* Konsol mencetak: `Shadow effect applied and document saved as output.docx`.
* Membuka `output.docx` menampilkan bentuk dengan bayangan hitam lembut yang bergeser 2 pts secara horizontal dan vertikal.

## Pertanyaan umum dan kasus tepi

| Pertanyaan | Jawaban |
|------------|---------|
| **Apakah saya dapat menargetkan bentuk tertentu berdasarkan nama?** | Ya. Gunakan `doc.get_child_nodes(aw.NodeType.SHAPE, True)` untuk mengiterasi dan mencocokkan `shape.name`. |
| **Bagaimana jika dokumen tidak memiliki bentuk?** | `shape` akan menjadi `None`. Lindungi kode: `if shape is None: raise ValueError("No shape found.")`. |
| **Bagaimana cara menggunakan warna RGB khusus?** | Buat `aw.Color` dengan `aw.Color.from_argb(alpha, red, green, blue)`. Contoh: `aw.Color.from_argb(255, 255, 0, 0)` untuk merah terang. |
| **Apakah bayangan terlihat di semua penampil Word?** | Bayangan merupakan bagian dari format bentuk dan muncul di Word, Word Online, serta sebagian besar penampil pihak ketiga yang menghormati styling OOXML. |
| **Bisakah saya menerapkan bayangan yang sama ke beberapa bentuk?** | Lakukan perulangan pada koleksi bentuk dan tetapkan properti `shadow` yang sama untuk setiap elemen. |

## Tips profesional untuk penggunaan produksi

* **Pemrosesan batch:** Bungkus skrip dalam fungsi yang menerima jalur input dan output, lalu panggil dalam loop untuk memproses puluhan file.
* **Kinerja:** Menggunakan kembali satu instance `Document` untuk banyak edit mengurangi beban memori.
* **Lisensi:** Saat menggunakan lisensi percobaan, dokumen yang disimpan akan berisi watermark. Terapkan lisensi yang tepat untuk menghilangkannya.

## Kesimpulan

Sekarang Anda tahu cara **menerapkan efek bayangan** pada bentuk Word dengan Aspose.Words untuk Python, termasuk langkah-langkah untuk **menambahkan bayangan ke bentuk**, **mengatur warna bayangan**, dan **menyimpan dokumen yang diedit**. Dengan contoh lengkap yang dapat dijalankan, Anda dapat mengintegrasikan styling bayangan ke dalam pipeline pembuatan dokumen otomatis apa pun.

**Langkah selanjutnya:** Jelajahi opsi format bentuk lainnya seperti border, glow, atau rotasi 3‑D (`shape.line_format`, `shape.rotation`). Anda juga dapat menggabungkan teknik ini dengan mail‑merge Aspose.Words untuk menghasilkan laporan pribadi yang memiliki gaya visual konsisten.

Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Tambahkan Efek Bayangan ke Bentuk Word – Panduan Lengkap C#](/words/english/net/programming-with-shapes/add-shadow-effect-to-word-shapes-complete-c-guide/)
- [Tambahkan bayangan ke bentuk di Word – Panduan Lengkap Aspose.Words](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [Buat bentuk persegi panjang di Word dengan Aspose.Words – Panduan Langkah‑ demi‑ Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}