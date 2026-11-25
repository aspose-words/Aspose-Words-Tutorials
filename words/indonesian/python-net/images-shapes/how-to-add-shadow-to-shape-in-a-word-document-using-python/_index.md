---
category: general
date: 2026-11-25
description: Tambahkan bayangan pada bentuk di dokumen Word dengan Python. Pelajari
  cara menyisipkan bentuk persegi panjang di Word dan menerapkan bayangan transparan
  menggunakan Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- insert rectangle shape word
- how to create word document python
- Aspose.Words Python
- shape formatting Python
language: id
lastmod: 2026-11-25
og_description: Tambahkan bayangan pada bentuk di dokumen Word menggunakan Python.
  Tutorial ini menunjukkan cara menyisipkan bentuk persegi panjang di Word dan mengatur
  bayangan transparan 30 % dengan Aspose.Words.
og_image_alt: Add shadow to shape example in a Word document created by Python
og_title: Tambahkan bayangan pada bentuk di dokumen Word dengan Python – panduan langkah
  demi langkah
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Add shadow to shape in a Word document with Python. Learn how to insert
    rectangle shape in Word and apply a transparent shadow using Aspose.Words.
  headline: How to add shadow to shape in a Word document using Python
  type: TechArticle
tags:
- Python
- Aspose.Words
- Word automation
title: Cara menambahkan bayangan pada bentuk di dokumen Word menggunakan Python
url: /id/python/images-shapes/how-to-add-shadow-to-shape-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menambahkan bayangan pada bentuk di dokumen Word menggunakan Python

Jika Anda perlu **menambahkan bayangan pada bentuk** di dokumen Word, panduan ini menunjukkan solusi lengkap yang dapat dijalankan. Anda akan melihat cara membuat file Word, menyisipkan bentuk persegi panjang, dan menerapkan bayangan transparan 30 %—semua dengan pustaka Aspose.Words untuk Python.

Bekerja dengan dokumen Word secara programatik menghemat Anda dari format manual dan memungkinkan pembuatan laporan, kontrak, atau selebaran pemasaran secara skala. Pada akhir tutorial ini Anda akan dapat menjawab “**bagaimana cara membuat dokumen Word python**” dengan contoh kode siap‑jalankan.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* Python 3.8 atau yang lebih baru terpasang.
* Lisensi Aspose.Words untuk Python yang aktif (versi percobaan gratis dapat digunakan untuk evaluasi).
* Paket `aspose-words` terpasang melalui `pip install aspose-words`.
* Folder tempat file output dapat ditulis (ganti `YOUR_DIRECTORY` dalam kode).

Tidak ada ketergantungan tambahan yang diperlukan.

## Langkah 1: Buat dokumen Word baru

Langkah pertama adalah menginstansiasi objek `Document`. Objek ini mewakili seluruh file .docx di memori.

```python
import aspose.words as aw

# Create an empty Word document
doc = aw.Document()
# DocumentBuilder provides a convenient API for adding content
builder = aw.DocumentBuilder(doc)
```

`DocumentBuilder` berfungsi seperti kursor virtual. Ketika Anda memanggil metodenya, pustaka menyisipkan elemen yang bersesuaian pada lokasi kursor saat ini.

## Langkah 2: Sisipkan bentuk persegi panjang di Word

Selanjutnya Anda **menyisipkan bentuk persegi panjang di Word** menggunakan metode `insert_shape` builder. Metode ini memerlukan tipe bentuk dan ukurannya dalam poin (1 poin = 1/72 inci).

```python
# Insert a rectangle shape that is 100 points wide and 50 points tall
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)
```

Anda dapat mengubah dimensi agar sesuai dengan desain Anda. Persegi panjang menjadi bagian dari lapisan gambar dokumen, yang berarti Anda dapat memodifikasi isian, garis tepi, atau bayangannya nanti.

## Langkah 3: Akses format bayangan bentuk

Setiap objek gambar mengekspos properti `shadow_format` yang mengontrol tampilan bayangan. Ambil properti ini agar Anda dapat menyesuaikan transparansi, offset, blur, dan warna.

```python
# Get the ShadowFormat object for the rectangle
shadow = shape.shadow_format
```

Pada titik ini bentuk memiliki bayangan default (tanpa bayangan). Objek `ShadowFormat` menyimpan semua parameter yang Anda perlukan untuk membuat efek realistis.

## Langkah 4: Buat bayangan 30 % transparan

Transparansi dinyatakan sebagai nilai antara `0` (sepenuhnya tidak tembus) dan `1` (sepenuhnya tembus). Menetapkannya ke `0.3` menghasilkan bayangan transparan 30 %, yang biasanya cukup untuk menambah kedalaman tanpa mengaburkan teks.

```python
# Apply a 30 % transparent shadow
shadow.transparency = 0.3
# Optional: adjust other shadow properties for a nicer look
shadow.visible = True               # Ensure the shadow is turned on
shadow.distance = 4                 # Distance of the shadow from the shape (points)
shadow.blur = 4                     # Amount of blur applied to the shadow
shadow.color = aw.Color.black       # Shadow color
```

Properti tambahan ini tidak wajib, tetapi mereka menggambarkan cara Anda dapat menyempurnakan efek. Flag `visible` sangat penting; jika Anda lupa menambahkannya, bayangan tidak akan muncul meskipun pengaturan lain sudah dikonfigurasi.

## Langkah 5: Simpan dokumen untuk melihat hasilnya

Akhirnya, tulis dokumen ke disk. Membuka file `.docx` yang dihasilkan di Microsoft Word atau penampil kompatibel lainnya akan menampilkan persegi panjang dengan bayangan transparan yang diterapkan.

```python
# Save the document to the desired location
output_path = r"YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Saat Anda membuka `output.docx`, Anda akan melihat persegi panjang polos dengan bayangan abu‑abu halus yang bergeser ke kanan‑bawah. Transparansi bayangan 30 % membuat bentuk tampak terangkat dari halaman.

![Add shadow to shape example](placeholder-image.png){: .align-center alt="Contoh menambahkan bayangan pada bentuk dalam dokumen Word yang dibuat dengan Python"}

## Skrip lengkap yang dapat dijalankan

Menggabungkan semua bagian menghasilkan skrip mandiri yang dapat Anda salin, tempel, dan jalankan segera.

```python
import aspose.words as aw

def create_word_with_shadow(output_path: str):
    """
    Creates a Word document that contains a rectangle shape
    with a 30 % transparent shadow.
    """
    # Step 1: Initialize document and builder
    doc = aw.Document()
    builder = aw.DocumentBuilder(doc)

    # Step 2: Insert rectangle shape
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)

    # Step 3: Access shadow format
    shadow = shape.shadow_format

    # Step 4: Configure shadow properties
    shadow.visible = True
    shadow.transparency = 0.3
    shadow.distance = 4
    shadow.blur = 4
    shadow.color = aw.Color.black

    # Step 5: Save the document
    doc.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    # Replace with a valid folder on your machine
    create_word_with_shadow(r"YOUR_DIRECTORY/output.docx")
```

**Output yang diharapkan:** Membuka `output.docx` yang dihasilkan menampilkan satu halaman dengan persegi panjang yang memancarkan bayangan ringan, semi‑transparan. Tidak ada format tambahan yang diperlukan.

## Variasi umum dan kasus tepi

| Situasi | Cara menyesuaikan kode |
|-----------|-----------------------|
| **Tipe bentuk berbeda** (misalnya elips) | Ganti `aw.drawing.ShapeType.RECTANGLE` dengan `aw.drawing.ShapeType.ELLIPSE`. |
| **Warna bayangan khusus** | Setel `shadow.color = aw.Color.from_argb(255, 128, 0, 0)` untuk bayangan kemerahan. |
| **Beberapa bentuk** | Panggil `builder.insert_shape` berulang kali; setiap pemanggilan mengembalikan objek `Shape` terpisah yang dapat Anda gaya secara independen. |
| **Menyimpan sebagai PDF** | Ganti `doc.save(output_path)` dengan `doc.save(output_path.replace('.docx', '.pdf'))` dan gunakan ekstensi `.pdf`. |
| **Menjalankan tanpa lisensi** | Versi percobaan gratis menambahkan watermark pada halaman pertama. Dapatkan lisensi untuk menghilangkannya pada penggunaan produksi. |

Variasi ini menunjukkan bahwa pola yang sama—membuat dokumen, menyisipkan bentuk, menyesuaikan `shadow_format`, menyimpan—mencakup sebagian besar skenario otomasi.

## Tips dan praktik terbaik

* **Gunakan kembali builder**: Pertahankan satu instance `DocumentBuilder` untuk seluruh dokumen agar menghindari pembuatan objek yang tidak perlu.
* **Bebaskan sumber daya**: Pada layanan yang berjalan lama, panggil `doc.dispose()` setelah menyimpan untuk membebaskan memori native.
* **Validasi output**: Gunakan `doc.validate(aw.ValidationType.FULL_VALIDATION)` sebelum menyimpan jika Anda perlu memastikan kepatuhan terhadap standar Open XML.
* **Kompatibilitas versi**: Kode ini bekerja dengan Aspose.Words untuk Python ≥ 22.9. Pastikan paket Anda terbaru dengan `pip install --upgrade aspose-words`.

## Kesimpulan

Sekarang Anda tahu cara **menambahkan bayangan pada bentuk** di dokumen Word menggunakan Python. Dengan mengikuti lima langkah—membuat dokumen, **menyisipkan bentuk persegi panjang di Word**, mengonfigurasi bayangan, dan menyimpan—Anda dapat mengotomatisasi pembuatan dokumen yang tampak profesional untuk laporan, faktur, atau materi pemasaran.  

Selanjutnya Anda dapat menjelajahi opsi format lain seperti isian gradien, pembungkus teks, atau mengonversi dokumen ke PDF. Semua topik tersebut dibangun di atas konsep `DocumentBuilder` dan format bentuk yang diperkenalkan dalam tutorial ini.

Selamat coding, dan nikmati kedalaman visual yang dibawa oleh bayangan sederhana pada dokumen Word otomatis Anda!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang memperluas teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara membuat bentuk persegi panjang di dokumen Word menggunakan Python](/words/english/python-net/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/)
- [Menambahkan Bayangan pada Bentuk di Python – Tutorial Lengkap Aspose.Words](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [Buat Dokumen Word Kosong dan Tambahkan Bayangan pada Bentuk – Panduan Python Lengkap](/words/english/python-net/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}