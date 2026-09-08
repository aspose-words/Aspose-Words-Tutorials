---
category: general
date: 2026-09-08
description: Pelajari cara mengelompokkan bentuk di Word dengan DocumentBuilder, membuat
  dokumen Word kosong, dan menyisipkan bentuk persegi panjang hanya dalam beberapa
  baris kode C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create blank word doc
- insert rectangle shape word
- how to use documentbuilder
language: id
lastmod: 2026-09-08
og_description: Kelompokkan bentuk di Word menggunakan DocumentBuilder. Tutorial ini
  menunjukkan cara membuat dokumen Word kosong, menyisipkan bentuk persegi panjang,
  dan menggabungkan bentuk menjadi GroupShape.
og_image_alt: Screenshot of a Word document showing grouped shapes – group shapes
  in Word example
og_title: Mengelompokkan bentuk di Word dengan DocumentBuilder – contoh lengkap C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to group shapes in Word with a DocumentBuilder, create a
    blank Word doc, and insert a rectangle shape in just a few lines of C# code.
  headline: How to group shapes in Word using DocumentBuilder – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Cara mengelompokkan bentuk di Word menggunakan DocumentBuilder – panduan langkah
  demi langkah
url: /id/net/programming-with-shapes/how-to-group-shapes-in-word-using-documentbuilder-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengelompokkan bentuk di Word menggunakan DocumentBuilder – panduan langkah demi langkah

Jika Anda perlu **mengelompokkan bentuk di Word** secara programatis, tutorial ini menunjukkan solusi lengkap dalam C#. Anda akan melihat cara **membuat dokumen Word kosong**, menggunakan **DocumentBuilder**, dan **menyisipkan bentuk persegi panjang** sebelum mengelompokkannya dengan elips. Hasilnya adalah satu `GroupShape` yang dapat Anda pindahkan, ubah ukuran, atau beri gaya sebagai satu objek.

Panduan ini mencakup semua yang perlu Anda ketahui untuk menghasilkan dokumen Word dengan grafik yang dikelompokkan menggunakan pustaka Aspose.Words untuk .NET. Pada akhir artikel Anda akan memiliki proyek yang dapat dijalankan yang menghasilkan `GroupedShapes.docx` berisi persegi panjang dan elips yang digabungkan menjadi satu bentuk.

## Prasyarat

- .NET 6.0 atau lebih baru (kode juga berfungsi dengan .NET Framework 4.7.2+)
- Paket NuGet Aspose.Words untuk .NET (`Aspose.Words`) – versi 23.12 atau lebih baru
- IDE C# seperti Visual Studio 2022 atau Visual Studio Code
- Familiaritas dasar dengan sintaks C# dan pemrograman berorientasi objek

> **Pro tip:** Instal paket NuGet dari baris perintah untuk menjaga proyek Anda tetap rapi:  
> `dotnet add package Aspose.Words --version 23.12.0`

## Langkah 1: Membuat dokumen Word kosong

Operasi pertama adalah menginstansiasi objek `Document`, yang mewakili file Word kosong, dan `DocumentBuilder` yang memungkinkan Anda menambahkan konten.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Step 1: Create a blank Word document and a DocumentBuilder
        Document document = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Mengapa ini penting:** `Document` menyediakan wadah file, sementara `DocumentBuilder` menawarkan API yang fluent untuk menyisipkan teks, gambar, dan bentuk. Tanpa `DocumentBuilder` Anda harus memanipulasi pohon node dokumen secara manual, yang rawan kesalahan.

## Langkah 2: Menyisipkan bentuk persegi panjang

Persegi panjang adalah blok bangunan umum untuk diagram. Gunakan `InsertShape` dengan `ShapeType.Rectangle` dan tentukan lebar serta tinggi dalam poin (1 pt ≈ 1/72 in).

```csharp
        // Step 2: Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;   // distance from the left margin (points)
        rectangleShape.Top = 50;    // distance from the top margin (points)
```

**Mengapa ini penting:** Menetapkan posisi `Left` dan `Top` menempatkan persegi panjang secara tepat pada halaman, yang penting ketika Anda nanti mengelompokkannya dengan bentuk lain. Metode `InsertShape` secara otomatis menambahkan bentuk ke paragraf saat ini.

## Langkah 3: Menyisipkan bentuk elips

Selanjutnya, tambahkan elips yang akan berada di samping persegi panjang.

```csharp
        // Step 3: Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;
```

**Mengapa ini penting:** Menggunakan `ShapeType` yang berbeda menunjukkan bagaimana API `DocumentBuilder` yang sama dapat membuat grafik yang beragam. Menempatkan elips sehingga tumpang tindih dengan persegi panjang membuat efek pengelompokan menjadi jelas.

## Langkah 4: Mengelompokkan dua bentuk

`GroupShape` berfungsi seperti kontainer. Dengan menambahkan persegi panjang dan elips sebagai anak, mereka berperilaku sebagai satu objek.

```csharp
        // Step 4: Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        // Define the bounding rectangle that encloses all child shapes
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Insert the group into the document body
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);
```

**Mengapa ini penting:** Properti `Bounds` memberi tahu Word di mana grup berada pada halaman. Dengan menambahkan bentuk anak, Anda mempertahankan format individual mereka sambil memungkinkan transformasi kolektif (memindahkan, memutar, mengubah ukuran).

## Langkah 5: Menyimpan dokumen

Akhirnya, tulis dokumen ke disk. Anda dapat mengubah jalur ke folder mana pun yang Anda inginkan.

```csharp
        // Step 5: Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Saat Anda membuka `GroupedShapes.docx` di Microsoft Word, Anda akan melihat persegi panjang dan elips yang dikelompokkan bersama. Memilih grup akan menyorot kedua bentuk, memungkinkan Anda menyeret atau mengubah ukuran mereka sebagai satu unit.

### Output yang Diharapkan

- File Word bernama **GroupedShapes.docx**
- Halaman pertama berisi **persegi panjang** (100 pt × 50 pt) pada posisi (50, 50)
- Sebuah **elips** (80 pt × 80 pt) pada posisi (200, 70)
- Kedua bentuk merupakan bagian dari **GroupShape** dengan kotak pembatas 300 pt × 200 pt

## Variasi umum dan kasus tepi

| Scenario | Adjustment |
|----------|------------|
| **Ukuran halaman berbeda** | Set `document.Sections[0].PageSetup.PageWidth` and `PageHeight` before inserting shapes. |
| **Lebih dari dua bentuk** | Create additional `Shape` objects and call `groupShape.AppendChild(newShape)` for each. |
| **Terapkan warna isi** | `rectangleShape.FillColor = System.Drawing.Color.LightBlue;` |
| **Putar grup** | `groupShape.Rotation = 45;` (degrees) |
| **Ekspor ke PDF** | After saving the DOCX, call `document.Save("GroupedShapes.pdf");` |

## Kode sumber lengkap (siap dijalankan)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Create a blank Word document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;
        rectangleShape.Top = 50;

        // Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;

        // Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);

        // Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Salin kode ke dalam proyek konsol baru, pulihkan paket NuGet Aspose.Words, dan jalankan. Konsol akan mengonfirmasi lokasi file, dan membuka file akan menampilkan grafik yang dikelompokkan.

## Kesimpulan

Anda sekarang tahu **cara mengelompokkan bentuk di Word** dengan `DocumentBuilder` Aspose.Words. Tutorial ini melangkah melalui pembuatan **dokumen Word kosong**, **menyisipkan bentuk persegi panjang**, menambahkan elips, dan menggabungkannya menjadi `GroupShape`. Dengan dasar ini Anda dapat membangun diagram, flowchart, atau grafik khusus yang lebih kaya langsung dari C#.

### Apa selanjutnya?

- Jelajahi **cara menggunakan DocumentBuilder** untuk tabel, header, dan footer.
- Gabungkan teknik **menyisipkan bentuk persegi panjang Word** dengan kotak teks untuk diagram beranotasi.
- Gunakan **membuat dokumen word kosong** sebagai templat untuk pembuatan laporan otomatis.

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Group Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Sisipkan Bentuk dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Buat bentuk persegi panjang di Word menggunakan C# – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}