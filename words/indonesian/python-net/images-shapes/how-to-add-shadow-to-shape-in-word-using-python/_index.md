---
category: general
date: 2026-11-25
description: Pelajari cara menambahkan bayangan pada bentuk di Word dengan Aspose.Words
  untuk Python – kode langkah demi langkah, penjelasan, dan praktik terbaik.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add shadow to shape in word
- Aspose.Words shadow formatting
- Python shape shadow
- Word document shape manipulation
- configure shadow offset
- set shape shadow color
language: id
lastmod: 2026-11-25
og_description: Cara menambahkan bayangan pada bentuk di Word dengan Aspose.Words
  untuk Python. Ikuti tutorial ini untuk mengaktifkan dan menyesuaikan bayangan bentuk
  dalam dokumen Anda.
og_image_alt: Screenshot showing a Word shape with a black shadow applied using Python
og_title: Cara menambahkan bayangan pada bentuk di Word menggunakan Python – panduan
  lengkap
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to add shadow to shape in Word with Aspose.Words for Python
    – step‑by‑step code, explanations, and best practices.
  headline: How to add shadow to shape in Word using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- Shape formatting
title: Cara menambahkan bayangan pada bentuk di Word menggunakan Python
url: /id/python/images-shapes/how-to-add-shadow-to-shape-in-word-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menambahkan bayangan ke bentuk di Word menggunakan Python

Jika Anda perlu **menambahkan bayangan ke bentuk di Word**, panduan ini menunjukkan langkah‑langkah tepat dengan Aspose.Words untuk Python. Pada akhir tutorial Anda akan memiliki dokumen Word di mana bentuk pertama menampilkan bayangan hitam dengan offset dan blur yang dapat disesuaikan.

Anda juga akan melihat bagaimana teknik yang sama bekerja untuk bentuk apa pun dalam dokumen, memudahkan peningkatan laporan, selebaran, atau materi pemasaran. Tidak diperlukan pengalaman sebelumnya dengan Aspose.Words—hanya pengetahuan dasar Python.

## Apa yang Anda butuhkan

- Python 3.8+ (kode ini bekerja di Windows, macOS, dan Linux)  
- Paket `aspose-words` (`pip install aspose-words`)  
- File `.docx` yang berisi setidaknya satu bentuk (misalnya, persegi panjang atau gambar yang disisipkan)  

## Langkah 1: Siapkan Aspose.Words untuk Python

Pertama instal pustaka dan impor namespace yang diperlukan. Paket `aspose.words` memberi Anda akses penuh ke model objek Word, termasuk properti bayangan bentuk.

```python
# Install the package (run once in your terminal)
# pip install aspose-words

import aspose.words as aw
```

> **Tip pro:** Gunakan lingkungan virtual untuk menjaga ketergantungan terisolasi dari proyek lain.

## Langkah 2: Muat dokumen Word

Memuat dokumen sangat sederhana dengan `aw.Document`. Ganti `"YOUR_DIRECTORY/input.docx"` dengan jalur ke file sumber Anda.

```python
# Load the Word document
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

Objek `Document` mewakili seluruh file Word dan menyediakan metode untuk menavigasi pohon node-nya.

## Langkah 3: Dapatkan bentuk pertama dalam dokumen

Sebuah bentuk adalah node dengan tipe `NodeType.SHAPE`. Metode `get_child` mencari pohon dokumen dan mengembalikan node pertama yang cocok.

```python
# Retrieve the first shape (index 0) in the document
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
```

Jika dokumen Anda berisi banyak bentuk, ubah indeks untuk menargetkan yang lain. Flag `True` memastikan pencarian mendalam (yaitu, mencakup header, footer, dan tabel).

## Langkah 4: Terapkan format bayangan pada bentuk

Setiap bentuk memiliki properti `shadow_format` yang mengontrol visibilitas, warna, offset, blur, dan lainnya. Di bawah ini kami mengaktifkan bayangan, mengatur warnanya menjadi hitam, serta mengonfigurasi offset horizontal/vertikal dan radius blur.

```python
# Access the shape's shadow formatting object
shadow_format = first_shape.shadow_format

# Enable the shadow and configure its appearance
shadow_format.visible = True                     # Make the shadow visible
shadow_format.color = aw.drawing.Color.black    # Set shadow color to black
shadow_format.offset_x = 4                      # Horizontal offset (points)
shadow_format.offset_y = 4                      # Vertical offset (points)
shadow_format.blur = 6                          # Blur radius (points)
```

### Mengapa pengaturan ini penting

- `visible = True` mengaktifkan efek; tanpa ini properti lain tidak berpengaruh.  
- `color` menentukan nuansa bayangan; hitam memberikan kontras paling kuat.  
- `offset_x` dan `offset_y` mengontrol seberapa jauh bayangan dipindahkan dari bentuk; nilai yang sama menghasilkan bayangan diagonal.  
- `blur` melunakkan tepi, membuat bayangan tampak lebih alami.

Anda dapat bereksperimen dengan warna lain (`aw.drawing.Color.red`) atau offset yang lebih besar untuk efek dramatis. Fleksibilitas ini merupakan bagian dari **Aspose.Words shadow formatting**.

## Langkah 5: Simpan dokumen yang dimodifikasi (opsional)

Setelah mengonfigurasi bayangan, tulis perubahan kembali ke disk. Anda dapat menimpa file asli atau membuat file baru.

```python
# Save the updated document
doc.save("YOUR_DIRECTORY/output.docx")
```

Membuka `output.docx` di Microsoft Word akan menampilkan bentuk pertama dengan bayangan hitam yang terlihat, offset 4 pt secara horizontal dan vertikal, serta blur 6 pt.

![tangkapan layar cara menambahkan bayangan ke bentuk di Word](image.png){alt="cara menambahkan bayangan ke bentuk di Word menggunakan Python"}

## Variasi umum dan kasus tepi

| Situasi | Cara menyesuaikan kode |
|-----------|------------------------|
| **Beberapa bentuk** | Lakukan perulangan melalui `doc.get_child_nodes(aw.NodeType.SHAPE, True)` dan terapkan `shadow_format` yang sama pada setiap bentuk. |
| **Warna bayangan yang berbeda** | Setel `shadow_format.color = aw.drawing.Color.from_argb(255, 255, 0, 0)` untuk bayangan merah. |
| **Tidak perlu bayangan pada beberapa bentuk** | Tambahkan pemeriksaan kondisional: `if shape.name == "TitleShape": continue`. |
| **Menyimpan sebagai PDF** | Gunakan `doc.save("output.pdf")`; bayangan dipertahankan dalam rendering PDF. |
| **Versi Word lama** | Aspose.Words bekerja dengan .doc dan .docx secara serupa; API yang sama berlaku. |

Variasi ini menunjukkan luasnya **Word document shape manipulation** yang dapat Anda capai dengan beberapa baris Python.

## Kesimpulan

Anda kini tahu **cara menambahkan bayangan ke bentuk di Word** secara programatis dengan Aspose.Words untuk Python. Alur kerja lengkap—menyiapkan pustaka, memuat dokumen, mengambil bentuk, mengonfigurasi bayangannya, dan menyimpan hasilnya—mencakup kasus penggunaan paling umum dan memberi Anda fondasi kuat untuk format bentuk yang lebih maju.

Selanjutnya, coba gabungkan teknik ini dengan opsi format lain seperti **set shape shadow color**, **configure shadow offset**, atau bahkan menerapkan gradien dan refleksi. Menjelajahi fitur‑fitur tersebut akan memungkinkan Anda membuat dokumen siap cetak yang halus sepenuhnya dari kode.

*Siap mengotomatisasi lebih banyak fitur Word? Lihat tutorial kami tentang “cara mengubah warna isi bentuk di Word” dan “cara menyisipkan watermark dengan Aspose.Words”.*

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait dan membangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Menambahkan Bayangan ke Bentuk dalam Python dengan Aspose.Words – Panduan Lengkap](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-with-aspose-words-full-guide/)
- [Cara menerapkan efek bayangan ke bentuk Word dengan Aspose.Words](/words/english/python-net/images-shapes/how-to-apply-shadow-effect-to-a-word-shape-with-aspose-words/)
- [Buat Dokumen Word Python – Panduan Menambahkan Bayangan ke Bentuk](/words/english/python-net/images-shapes/create-word-document-python-add-shadow-to-shape-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}