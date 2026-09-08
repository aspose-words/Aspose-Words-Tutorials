---
category: general
date: 2026-09-08
description: Buat bentuk persegi panjang dalam dokumen Word dengan C#. Pelajari cara
  mengatur ukuran bentuk, mengelompokkan beberapa bentuk, dan membuat dokumen Word
  kosong secara programatis.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- set shape size
- group multiple shapes
- create blank word document
language: id
lastmod: 2026-09-08
og_description: Buat bentuk persegi panjang dalam dokumen Word dengan C#. Panduan
  ini menunjukkan cara mengatur ukuran bentuk, mengelompokkan beberapa bentuk, dan
  membuat dokumen Word kosong secara programatis.
og_image_alt: Screenshot showing how to create rectangle shape in a Word document
  using C#
og_title: Buat bentuk persegi panjang dan grupkan bentuk di Word menggunakan C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Create rectangle shape in a Word document with C#. Learn to set shape
    size, group multiple shapes, and create blank Word document programmatically.
  headline: Create rectangle shape and group shapes in Word using C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Buat bentuk persegi panjang dan grupkan bentuk di Word menggunakan C#
url: /id/net/programming-with-shapes/create-rectangle-shape-and-group-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat bentuk persegi panjang dan mengelompokkan bentuk di Word menggunakan C#

Jika Anda perlu **membuat bentuk persegi panjang** di dalam file Word, tutorial ini memberikan solusi lengkap yang siap dijalankan. Anda akan melihat cara mengatur ukuran bentuk, mengelompokkan beberapa bentuk, dan membuat dokumen Word kosong dari awal—semua dengan menggunakan pustaka Aspose.Words untuk .NET.

Bekerja dengan dokumen Word secara programatik sering terasa seperti menyeimbangkan banyak detail kecil. Pada akhir panduan ini Anda akan memiliki satu metode yang menghasilkan file `.docx` berisi persegi panjang dan elips yang dikelompokkan bersama, siap untuk diedit lebih lanjut atau dicetak.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* .NET 6.0 atau yang lebih baru (kode ini juga berfungsi dengan .NET Framework 4.6+)
* Salinan berlisensi **Aspose.Words untuk .NET** (Anda dapat menggunakan kunci evaluasi gratis)
* IDE seperti Visual Studio 2022 atau Visual Studio Code
* Familiaritas dasar dengan sintaks C#

Tidak ada paket NuGet tambahan yang diperlukan selain `Aspose.Words`.

## Langkah 1: Membuat dokumen Word kosong

Langkah pertama adalah membuat dokumen kosong yang akan menjadi tempat bagi bentuk-bentuk tersebut. Ini memenuhi kebutuhan *membuat dokumen word kosong*.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty Word document
Document doc = new Document();

// The document already contains one section and one empty paragraph
// You can add additional sections later if needed
```

Membuat dokumen kosong memberi Anda kanvas yang bersih. Objek `Document` mewakili seluruh file `.docx`, dan `FirstSection.Body.FirstParagraph`‑nya adalah titik sisipan default untuk node baru.

## Langkah 2: Membuat bentuk persegi panjang

Sekarang Anda dapat menambahkan persegi panjang. Di sinilah operasi **membuat bentuk persegi panjang** terjadi.

```csharp
// Initialize a DocumentBuilder to simplify node insertion
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape instance
Shape rectangle = new Shape(doc, ShapeType.Rectangle);

// Set the rectangle's size (width and height) and position
rectangle.Width  = 100;   // points; 1 point = 1/72 inch
rectangle.Height = 50;
rectangle.Left   = 10;    // distance from the left edge of the container
rectangle.Top    = 20;    // distance from the top edge of the container

// Optional: give the rectangle a visible border
rectangle.StrokeColor = Color.Blue;
rectangle.FillColor   = Color.LightGray;
```

Menetapkan dimensi secara langsung menjawab kata kunci **set shape size**. Semua nilai ukuran diekspresikan dalam poin, yang memberikan kontrol presisi atas tampilan bentuk dalam dokumen akhir.

## Langkah 3: Membuat bentuk tambahan (elips)

Kasus penggunaan umum adalah menggabungkan beberapa bentuk. Di sini kita menambahkan elips yang nantinya akan berbagi kontainer yang sama.

```csharp
// Create an ellipse shape instance
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width  = 80;
ellipse.Height = 80;
ellipse.Left   = 120;   // Position it to the right of the rectangle
ellipse.Top    = 30;

// Give the ellipse a distinct border and fill
ellipse.StrokeColor = Color.DarkGreen;
ellipse.FillColor   = Color.LightYellow;
```

Kedua bentuk masih independen pada titik ini. Langkah berikutnya menunjukkan cara **mengelompokkan beberapa bentuk** bersama.

## Langkah 4: Mengelompokkan bentuk di Word

Mengelompokkan bentuk memungkinkan Anda memindahkan, mengubah ukuran, atau memformatnya sebagai satu unit. Ini memenuhi persyaratan **group shapes in word** dan **group multiple shapes**.

```csharp
// Create a GroupShape container that will hold the rectangle and ellipse
GroupShape group = new GroupShape(doc);

// Define the container's bounding box – it must be large enough for all children
group.Bounds = new RectangleF(0, 0, 300, 200);

// Append the group to the document's first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(group);

// Add the rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

Properti `GroupShape.Bounds` menentukan sistem koordinat untuk bentuk anak. Dengan menempatkan persegi panjang dan elips di dalam `GroupShape` yang sama, Anda dapat memindahkan atau memutar keduanya bersama dengan satu pemanggilan.

## Langkah 5: Menyimpan dokumen

Akhirnya, tulis dokumen ke disk. File tersebut akan berisi bentuk yang telah dikelompokkan yang baru saja Anda buat.

```csharp
// Choose an output path – ensure the directory exists and you have write permission
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");

// Save the document in DOCX format
doc.Save(outputPath);
```

Setelah menjalankan program, buka `GroupedShapes.docx` di Microsoft Word. Anda akan melihat sebuah persegi panjang dan sebuah elips yang dikelompokkan bersama; memilih satu bentuk juga akan memilih bentuk lainnya, menegaskan bahwa pengelompokan berhasil.

## Kode sumber lengkap

Salin program lengkap berikut ke dalam proyek console‑app baru dan jalankan. Tidak ada kode tambahan yang diperlukan.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
using System.Drawing;
using System.IO;

class Program
{
    static void Main()
    {
        // Step 1: create a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: create rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 100,
            Height = 50,
            Left   = 10,
            Top    = 20,
            StrokeColor = Color.Blue,
            FillColor   = Color.LightGray
        };

        // Step 3: create ellipse shape
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width  = 80,
            Height = 80,
            Left   = 120,
            Top    = 30,
            StrokeColor = Color.DarkGreen,
            FillColor   = Color.LightYellow
        };

        // Step 4: group the shapes
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new RectangleF(0, 0, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);
        group.AppendChild(rectangle);
        group.AppendChild(ellipse);

        // Step 5: save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Output yang diharapkan

Menjalankan program menghasilkan `GroupedShapes.docx`. Membuka file tersebut di Word menampilkan:

* Sebuah **persegi panjang** (100 pt × 50 pt) dengan batas biru dan isi abu‑abu muda.
* Sebuah **elips** (80 pt × 80 pt) dengan batas hijau tua dan isi kuning muda.
* Kedua bentuk berada dalam satu grup, sehingga memindahkan satu akan memindahkan yang lain.

## Pertanyaan umum dan kasus tepi

| Pertanyaan | Jawaban |
|------------|---------|
| **Apakah saya dapat menambahkan lebih dari dua bentuk ke dalam grup?** | Ya. Buat objek `Shape` tambahan dan panggil `group.AppendChild(yourShape)` untuk masing‑masing. |
| **Bagaimana jika saya perlu memutar grup?** | Atur `group.RotationAngle = 45;` (derajat). Semua bentuk anak akan berputar bersama. |
| **Apakah memungkinkan mengelompokkan bentuk setelah dokumen disimpan?** | Anda harus memodifikasi struktur dokumen sebelum menyimpan; jika tidak, Anda perlu memuat file, menemukan bentuk‑bentuknya, dan membuat ulang grup. |
| **Apakah saya perlu membuang (dispose) objek apa pun?** | Aspose.Words mengelola sumber dayanya sendiri, tetapi Anda harus membuang objek `FileStream` jika membuka aliran secara manual. |
| **Apakah kode ini akan bekerja dengan format .doc (biner)?** | Ya, ubah menjadi `doc.Save("output.doc")`. Perilaku pengelompokan tetap sama. |

## Kesimpulan

Anda kini tahu cara **membuat bentuk persegi panjang**, **menetapkan ukuran bentuk**, dan **mengelompokkan beberapa bentuk** di dalam file Word menggunakan C#. Pendekatan ini memungkinkan Anda membangun diagram kompleks, watermark, atau laporan berbasis templat secara programatik tanpa harus mengedit secara manual.

### Langkah selanjutnya

* Jelajahi **group shapes in word** lebih jauh dengan menambahkan kotak teks atau gambar ke dalam grup yang sama.
* Gunakan pola `SetShapeSize` untuk menghitung dimensi secara dinamis berdasarkan tata letak halaman.
* Gabungkan teknik ini dengan bidang mail‑merge untuk menghasilkan dokumen yang dipersonalisasi dalam skala besar.

Silakan bereksperimen dengan berbagai jenis bentuk, warna, dan transformasi grup. Selamat coding!


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik yang berhubungan erat dan membangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Word Document with a Shadowed Rectangle – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}