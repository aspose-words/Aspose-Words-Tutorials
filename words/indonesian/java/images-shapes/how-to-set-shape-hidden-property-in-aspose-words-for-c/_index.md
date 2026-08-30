---
category: general
date: 2026-08-20
description: Pelajari cara mengatur properti tersembunyi shape di Aspose.Words untuk
  C#. Panduan ini menunjukkan cara menyisipkan gambar dan menyembunyikan shape sehingga
  tidak pernah muncul di UI atau output cetak.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set shape hidden property
- insert image into document
- hide shape in Aspose.Words
- C# shape hidden property
- Aspose.Words DocumentBuilder
- prevent shape from printing
language: id
lastmod: 2026-08-20
og_description: Atur properti tersembunyi shape di Aspose.Words dengan C#. Sisipkan
  gambar, sembunyikan shape, dan pastikan tidak pernah muncul di UI atau output cetak.
og_image_alt: Diagram illustrating set shape hidden property on a Word document shape
og_title: Mengatur properti tersembunyi shape di Aspose.Words – panduan lengkap C#
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to set shape hidden property in Aspose.Words for C#. This
    guide shows inserting an image and hiding the shape so it never appears in the
    UI or print output.
  headline: How to set shape hidden property in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Automation
- Shape Handling
title: Cara mengatur properti tersembunyi shape di Aspose.Words untuk C#
url: /id/java/images-shapes/how-to-set-shape-hidden-property-in-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengatur properti tersembunyi shape di Aspose.Words untuk C#

Jika Anda perlu **mengatur properti tersembunyi shape** dalam dokumen Word, tutorial ini menunjukkan langkah‑langkah tepat menggunakan Aspose.Words untuk .NET. Baik Anda sedang membangun mesin templat, menghasilkan laporan, atau menyisipkan logo yang harus tetap tidak terlihat, Anda akan belajar cara menyisipkan gambar dan menyembunyikan shape sehingga tidak pernah muncul di UI atau output cetak.

Dalam panduan ini kami juga membahas **menyisipkan gambar ke dalam dokumen**, menjelaskan mengapa menyembunyikan shape penting untuk pencetakan, dan menelusuri kode lengkap yang dapat dijalankan. Tidak diperlukan referensi eksternal—cukup salin, tempel, dan jalankan.

## Prerequisites

Sebelum Anda memulai, pastikan Anda memiliki:

* .NET 6.0 atau lebih baru (versi terbaru Aspose.Words menargetkan .NET 6+)
* Lisensi Aspose.Words untuk .NET yang valid (atau gunakan mode evaluasi gratis)
* Visual Studio 2022 atau IDE C# apa pun yang Anda sukai
* File gambar (misalnya `logo.png`) yang ditempatkan di folder yang dapat Anda referensikan dari kode

## Step 1: Create a new Document and DocumentBuilder

Kelas `DocumentBuilder` adalah titik masuk untuk membangun konten Word secara programatis. Ia memungkinkan Anda menyisipkan paragraf, tabel, dan shape seperti gambar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Initialize a new blank document
        Document doc = new Document();
        // DocumentBuilder provides methods to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Mengapa langkah ini?*  
Membuat `Document` memberi Anda representasi dalam memori dari file .docx, sementara `DocumentBuilder` menyediakan API fluent yang menyisipkan objek. Tanpa objek-objek ini Anda tidak dapat menempatkan shape di dokumen.

## Step 2: Insert the image as a shape

Aspose.Words memperlakukan setiap gambar sebagai `Shape`. Metode `InsertImage` mengembalikan instance `Shape` tersebut, yang kemudian dapat Anda manipulasi.

```csharp
        // Step 2: Insert an image into the document
        // The returned Shape object lets us modify properties like size, rotation, and visibility.
        Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");
```

*Mengapa langkah ini?*  
Menggunakan `InsertImage` tidak hanya menambahkan gambar ke alur teks tetapi juga memberi Anda referensi (`picture`) yang dapat Anda konfigurasikan. Ini penting untuk **properti tersembunyi shape C#** yang akan kami atur selanjutnya.

## Step 3: Set the shape hidden property

Properti `Hidden` mengontrol apakah shape berpartisipasi dalam UI dan pencetakan. Menetapkannya ke `true` membuat shape tidak terlihat di UI Word dan memastikan tidak akan dicetak.

```csharp
        // Step 3: Hide the inserted shape so it won't appear in the UI or print output
        picture.Hidden = true;
```

*Mengapa langkah ini?*  
Ketika sebuah shape ditandai sebagai tersembunyi, Word memperlakukannya seperti komentar—ada dalam struktur dokumen tetapi tidak pernah dirender. Inilah inti dari **mengatur properti tersembunyi shape**.

## Step 4: Save the document

Akhirnya, tulis dokumen ke disk. Anda dapat memilih format apa pun yang didukung oleh Aspose.Words (`.docx`, `.pdf`, `.html`, dll.).

```csharp
        // Step 4: Save the document to a .docx file
        doc.Save(@"OUTPUT\HiddenImageDocument.docx");
        // Optional: Save as PDF to verify the shape really stays hidden when printed
        doc.Save(@"OUTPUT\HiddenImageDocument.pdf");
    }
}
```

*Mengapa langkah ini?*  
Menyimpan menyelesaikan perubahan dalam memori. Membuka `.docx` yang dihasilkan di Microsoft Word tidak menampilkan gambar, dan ekspor PDF mengonfirmasi shape tidak pernah muncul dalam output cetak.

## Full, runnable example

Menggabungkan semuanya, berikut program lengkap yang dapat Anda kompilasi dan jalankan:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeHiddenDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize a blank document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert an image as a shape
            // Replace YOUR_DIRECTORY with the actual folder that contains logo.png
            Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");

            // 3️⃣ Set the shape hidden property
            picture.Hidden = true; // This hides the shape in UI and when printing

            // 4️⃣ Save the document in both DOCX and PDF formats
            doc.Save(@"OUTPUT\HiddenImageDocument.docx");
            doc.Save(@"OUTPUT\HiddenImageDocument.pdf");

            Console.WriteLine("Document created successfully. The image is hidden.");
        }
    }
}
```

**Output yang diharapkan**

* Membuka `HiddenImageDocument.docx` di Microsoft Word tidak menampilkan gambar.
* Mengekspor atau mencetak dokumen (atau membuka PDF) juga tidak menampilkan gambar.
* Shape tersembunyi masih ada dalam XML dokumen, yang dapat Anda verifikasi dengan membuka `.docx` sebagai zip dan memeriksa `word/document.xml` – Anda akan melihat elemen `<w:pict>` dengan `w:hidden="true"`.

## Common variations and edge cases

| Situasi | Apa yang harus dilakukan | Mengapa penting |
|-----------|------------|----------------|
| **File gambar tidak ditemukan** | Bungkus `InsertImage` dalam `try/catch` dan tangani `FileNotFoundException`. | Mencegah aplikasi crash dan memungkinkan Anda mencatat kesalahan yang jelas. |
| **Beberapa shape tersembunyi** | Panggil `picture.Hidden = true` untuk setiap `Shape` yang Anda sisipkan, atau iterasi melalui `doc.GetChildNodes(NodeType.Shape, true)`. | Menjamin setiap elemen visual yang tidak diinginkan tetap tidak terlihat. |
| **Perlu shape terlihat hanya dalam mode edit** | Set `picture.Hidden = false` setelah mengedit, lalu ubah kembali sebelum menyimpan. | Memungkinkan Anda bekerja dengan shape di UI sambil menjaga output akhir tetap bersih. |
| **Mencetak pada versi Word lama** | Verifikasi dokumen dengan Word 2010 atau yang lebih baru; flag tersembunyi didukung di semua versi modern. | Menjamin kompatibilitas di seluruh basis pengguna Anda. |
| **Menggunakan format file berbeda (mis., PDF langsung)** | Flag `Hidden` berfungsi sama; Aspose.Words menghormatinya selama konversi PDF. | Mengonfirmasi bahwa **mencegah shape dicetak** berfungsi untuk semua target ekspor. |

## Pro tip: Verify the hidden flag programmatically

Jika Anda perlu memastikan bahwa sebuah shape tersembunyi sebelum menyimpan, Anda dapat memeriksa properti tersebut:

```csharp
bool isHidden = picture.Hidden;
Console.WriteLine($"Shape hidden? {isHidden}");
```

Pemeriksaan sederhana ini berguna dalam pipeline otomatis di mana Anda harus menjamin kepatuhan dengan kebijakan pembuatan dokumen.

## Conclusion

Anda sekarang tahu cara **mengatur properti tersembunyi shape** di Aspose.Words untuk C#. Dengan menyisipkan gambar, menerapkan `picture.Hidden = true`, dan menyimpan dokumen, shape tetap di luar UI dan tidak pernah muncul dalam output cetak. Teknik ini penting ketika Anda membutuhkan placeholder, watermark, atau elemen branding yang harus tetap tidak terlihat bagi pengguna akhir.

### What’s next?

* Jelajahi properti shape lain seperti `picture.WrapType`, `picture.Rotation`, dan `picture.RelativeHorizontalPosition`.
* Pelajari cara **menyembunyikan shape di Aspose.Words** secara kondisional berdasarkan input pengguna atau konfigurasi.
* Gabungkan shape tersembunyi dengan loop **menyisipkan gambar ke dalam dokumen** untuk menghasilkan penanda dinamis yang tidak terlihat untuk pemrosesan selanjutnya (mis., bidang mail‑merge).

Silakan bereksperimen dengan format gambar berbeda, tata letak dokumen, dan target ekspor. Menyembunyikan shape memberi Anda kontrol detail atas apa yang sebenarnya dilihat pembaca—dan apa yang tetap di balik layar. Selamat coding!

## What Should You Learn Next?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat shape persegi panjang di Word dengan Aspose.Words – Panduan langkah demi langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Buat Group Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Sisipkan Gambar Inline dalam Dokumen Word menggunakan Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}