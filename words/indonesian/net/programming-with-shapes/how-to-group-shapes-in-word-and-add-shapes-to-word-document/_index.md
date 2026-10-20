---
category: general
date: 2026-08-07
description: Cara mengelompokkan bentuk di Word dengan Aspose.Words dan menambahkan
  bentuk ke dokumen Word menggunakan C#. Ikuti panduan langkah demi langkah ini untuk
  kode yang bersih dan dapat digunakan kembali.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- add shapes to word document
language: id
lastmod: 2026-08-07
og_description: Cara mengelompokkan bentuk di Word menggunakan Aspose.Words untuk
  .NET. Tutorial ini menunjukkan cara menambahkan bentuk ke dokumen Word, mengelompokkannya,
  dan menyimpan file dengan kode C# yang jelas.
og_image_alt: Screenshot of a rectangle and ellipse grouped in a Word document created
  with Aspose.Words
og_title: Cara mengelompokkan bentuk di Word – panduan C# cepat
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  headline: How to group shapes in Word and add shapes to Word document
  type: TechArticle
- description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  name: How to group shapes in Word and add shapes to Word document
  steps:
  - name: Create a document and a builder
    text: A `Document` object represents the entire DOCX file. `DocumentBuilder` provides
      a convenient API for editing the document.
  - name: Add the rectangle shape
    text: A rectangle is created by specifying `ShapeType.Rectangle`. Width, height,
      and location are set in points (1 pt ≈ 1/72 in).
  - name: Add the ellipse shape
    text: The ellipse uses `ShapeType.Ellipse`. Its size and position are independent
      of the rectangle, which allows you to control the final layout of the group.
  - name: Group the two shapes
    text: '`GroupShape` acts as a container that treats its children as a single object.
      This is the essential operation for **how to group shapes in Word**.'
  - name: Insert the grouped shape into the document
    text: '`DocumentBuilder.InsertNode` places the `GroupShape` at the current cursor
      location. Because we have not moved the builder, the group appears at the start
      of the first page.'
  - name: Save the document
    text: Finally, write the DOCX file to disk. Use a full path that your application
      can write to.
  - name: Expected output
    text: Open `GroupShape.docx`. You will see a single visual object that contains
      a blue rectangle on the left and a green ellipse on the right. Selecting the
      object in Word highlights both shapes simultaneously—proof that **how to group
      shapes in Word** succeeded.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Cara mengelompokkan bentuk di Word dan menambahkan bentuk ke dokumen Word
url: /id/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengelompokkan bentuk di Word dan menambahkan bentuk ke dokumen Word

Jika Anda perlu **how to group shapes in Word**, panduan ini akan memandu Anda melalui proses lengkap menggunakan Aspose.Words for .NET. Anda juga akan mempelajari **add shapes to Word document** dengan beberapa baris kode C#, sehingga hasilnya siap untuk skenario pelaporan atau templat apa pun.

Tutorial ini mencakup semua yang Anda butuhkan: paket NuGet yang diperlukan, file sumber lengkap, dan penjelasan mengapa setiap langkah penting. Pada akhir tutorial Anda dapat menghasilkan file DOCX yang berisi persegi panjang dan elips yang digabungkan menjadi satu bentuk grup.

## Prasyarat

Sebelum Anda memulai, pastikan Anda memiliki:

* .NET 6.0 SDK atau yang lebih baru terpasang  
* Visual Studio 2022 (atau IDE apa pun yang mendukung .NET)  
* Paket NuGet Aspose.Words untuk .NET (`Aspose.Words`) – percobaan gratis dapat digunakan untuk pengujian, tetapi lisensi menghilangkan watermark evaluasi  

Item-item ini adalah satu-satunya dependensi eksternal untuk **add shapes to Word document**.

## Cara mengelompokkan bentuk di Word

Inti solusi adalah membuat bentuk‑bentuk individual, menempatkannya pada halaman, dan kemudian membungkusnya dalam `GroupShape`. Langkah‑langkah berikut mencerminkan urutan logis kode.

### Langkah 1: Membuat dokumen dan builder

Objek `Document` mewakili seluruh file DOCX. `DocumentBuilder` menyediakan API yang nyaman untuk mengedit dokumen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create an empty Word document
Document doc = new Document();

// DocumentBuilder lets you insert nodes, text, and shapes
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this matters*: `Document` adalah wadah untuk semua elemen Word. `DocumentBuilder` melacak posisi kursor saat ini, yang diperlukan ketika Anda nanti menyisipkan bentuk yang dikelompokkan.

### Langkah 2: Menambahkan bentuk persegi panjang

Persegi panjang dibuat dengan menentukan `ShapeType.Rectangle`. Lebar, tinggi, dan lokasi diatur dalam poin (1 pt ≈ 1/72 in).

```csharp
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;               // 100 pt wide
rectangleShape.Height = 50;               // 50 pt tall
rectangleShape.Left = 0;                  // X‑coordinate
rectangleShape.Top = 0;                   // Y‑coordinate
rectangleShape.StrokeColor = Color.Blue; // Outline color
```

*Why this matters*: Menetapkan `StrokeColor` membuat bentuk terlihat ketika dokumen dibuka. Anda juga dapat mengisi bentuk dengan `FillColor` jika interior padat diperlukan.

### Langkah 3: Menambahkan bentuk elips

Elips menggunakan `ShapeType.Ellipse`. Ukuran dan posisinya independen dari persegi panjang, yang memungkinkan Anda mengontrol tata letak akhir grup.

```csharp
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;
ellipseShape.Height = 80;
ellipseShape.Left = 120;                  // Placed to the right of the rectangle
ellipseShape.Top = 0;
ellipseShape.StrokeColor = Color.Green;
```

*Why this matters*: Dengan menempatkan elips pada `Left = 120`, bentuk ini tidak tumpang tindih dengan persegi panjang, sehingga grup terlihat berbeda secara visual.

### Langkah 4: Mengelompokkan dua bentuk

`GroupShape` berfungsi sebagai wadah yang memperlakukan anak‑nya sebagai satu objek. Ini adalah operasi penting untuk **how to group shapes in Word**.

```csharp
GroupShape groupShape = new GroupShape(doc);
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);
```

*Why this matters*: Pengelompokan memungkinkan Anda memindahkan, mengubah ukuran, atau memutar kedua bentuk secara bersamaan. Transformasi apa pun yang diterapkan pada `groupShape` akan diteruskan ke anak‑nya.

### Langkah 5: Menyisipkan bentuk yang dikelompokkan ke dalam dokumen

`DocumentBuilder.InsertNode` menempatkan `GroupShape` pada posisi kursor saat ini. Karena kami belum memindahkan builder, grup muncul di awal halaman pertama.

```csharp
builder.InsertNode(groupShape);
```

*Why this matters*: Menyisipkan node secara langsung menghindari kebutuhan paragraf atau sel tabel terpisah. Grup menjadi bagian dari alur dokumen.

### Langkah 6: Menyimpan dokumen

Akhirnya, tulis file DOCX ke disk. Gunakan jalur lengkap yang dapat ditulis oleh aplikasi Anda.

```csharp
doc.Save(@"C:\Temp\GroupShape.docx");
```

*Why this matters*: `doc.Save` menyelesaikan semua perubahan. File yang dihasilkan dapat dibuka di Microsoft Word, LibreOffice, atau penampil apa pun yang mendukung DOCX.

## File sumber lengkap

Salin kode di bawah ini ke dalam proyek konsol baru (`dotnet new console`) dan jalankan. Program akan membuat file bernama `GroupShape.docx` yang berisi persegi panjang dan elips yang dikelompokkan.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeGrouping
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Define a rectangle shape
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
            rectangleShape.Width = 100;
            rectangleShape.Height = 50;
            rectangleShape.Left = 0;
            rectangleShape.Top = 0;
            rectangleShape.StrokeColor = Color.Blue;

            // Step 3: Define an ellipse shape
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
            ellipseShape.Width = 80;
            ellipseShape.Height = 80;
            ellipseShape.Left = 120;
            ellipseShape.Top = 0;
            ellipseShape.StrokeColor = Color.Green;

            // Step 4: Group the two shapes together
            GroupShape groupShape = new GroupShape(doc);
            groupShape.AppendChild(rectangleShape);
            groupShape.AppendChild(ellipseShape);

            // Step 5: Insert the grouped shape into the document
            builder.InsertNode(groupShape);

            // Step 6: Save the document
            doc.Save(@"C:\Temp\GroupShape.docx");
        }
    }
}
```

### Output yang diharapkan

Buka `GroupShape.docx`. Anda akan melihat satu objek visual yang berisi persegi panjang biru di sebelah kiri dan elips hijau di sebelah kanan. Memilih objek di Word menyorot kedua bentuk secara bersamaan—bukti bahwa **how to group shapes in Word** berhasil.

## Pertanyaan umum dan kasus tepi

* **Can I add more than two shapes?**  
  Ya. Panggil `groupShape.AppendChild` untuk setiap `Shape` tambahan sebelum menyisipkan grup.

* **What if I need to rotate the group?**  
  Tetapkan `groupShape.RotationAngle = 45;` (sudut dalam derajat) setelah grup dibangun.

* **Do I need to call `doc.UpdatePageLayout()`?**  
  Tidak untuk skenario ini. Tata letak diperbarui secara otomatis saat dokumen disimpan.

* **How does licensing affect the code?**  
  Dengan lisensi Aspose.Words yang valid (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) dokumen yang dihasilkan tidak mengandung watermark evaluasi.

## Kesimpulan

Anda kini tahu **how to group shapes in Word** dan **add shapes to Word document** menggunakan Aspose.Words for .NET. Tutorial ini mencakup pembuatan dokumen, mendefinisikan bentuk individual, mengelompokkannya, menyisipkan grup, dan menyimpan file.  

Dari sini Anda dapat bereksperimen dengan:

* Menambahkan kotak teks atau gambar ke dalam grup  
* Mengubah warna isi, gaya garis, atau efek bayangan  
* Mengelompokkan bentuk di dalam tabel atau header  

Ekstensi ini memungkinkan Anda membangun templat Word yang canggih secara programatik sambil menjaga kode tetap bersih dan dapat dipelihara. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Group Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Sisipkan Bentuk dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Buat Dokumen Word dengan Aspose.Words – Panduan Langkah‑per‑Langkah](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}