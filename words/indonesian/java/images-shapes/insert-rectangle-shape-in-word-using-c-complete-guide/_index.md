---
category: general
date: 2026-08-04
description: Masukkan bentuk persegi panjang dalam dokumen Word dengan C#. Pelajari
  cara mengelompokkan bentuk di Word, menyimpan dokumen sebagai docx, dan menggunakan
  DocumentBuilder untuk tata letak lanjutan.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to group shapes
- group shapes in word
- save document as docx
- how to use builder
language: id
lastmod: 2026-08-04
og_description: Masukkan bentuk persegi panjang dalam file Word menggunakan C# dan
  kemudian grupkan bentuk-bentuk untuk tata letak lanjutan. Tutorial ini juga mencakup
  penyimpanan dokumen sebagai docx dan penggunaan DocumentBuilder secara efisien.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with C# DocumentBuilder
og_title: Menyisipkan bentuk persegi panjang di Word – panduan langkah demi langkah
  C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Insert rectangle shape in a Word document with C#. Learn how to group
    shapes in Word, save document as docx, and use DocumentBuilder for advanced layouts.
  headline: Insert rectangle shape in Word using C# – complete guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Menyisipkan bentuk persegi panjang di Word menggunakan C# – panduan lengkap
url: /id/java/images-shapes/insert-rectangle-shape-in-word-using-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sisipkan bentuk persegi panjang di Word menggunakan C# – panduan lengkap

Jika Anda perlu **insert rectangle shape** dalam dokumen Word menggunakan C#, tutorial ini menunjukkan secara tepat caranya. Anda juga akan belajar **how to group shapes** di Word, **save document as docx**, dan **how to use Builder** untuk kode yang bersih dan mudah dipelihara.

Bekerja dengan bentuk merupakan kebutuhan umum saat menghasilkan laporan, sertifikat, atau tata letak khusus secara programatis. Pada akhir panduan ini Anda akan memiliki contoh yang dapat dijalankan sepenuhnya yang membuat sebuah persegi panjang, menambahkan sebuah elips, mengelompokkannya, dan menyimpan hasilnya sebagai file DOCX.

## Prasyarat

* .NET 6.0 atau yang lebih baru terpasang  
* Visual Studio 2022 (atau IDE apa pun yang mendukung C#)  
* Library **Aspose.Words for .NET** (tersedia melalui NuGet)  

Anda dapat menambahkan library dengan perintah berikut:

```bash
dotnet add package Aspose.Words
```

## Sisipkan bentuk persegi panjang dengan DocumentBuilder

Langkah pertama adalah membuat `Document` baru dan `DocumentBuilder`. Builder memberikan API yang fluent untuk menyisipkan konten, termasuk bentuk.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document.
        Document document = new Document();

        // Initialize the builder that will edit the document.
        DocumentBuilder builder = new DocumentBuilder(document);
```

`Instance DocumentBuilder` adalah objek inti yang akan Anda gunakan untuk **insert rectangle shape** dan elemen lainnya. Ia melacak posisi kursor saat ini di dalam dokumen, sehingga setiap penyisipan terjadi tepat di tempat yang Anda inginkan.

## Cara menyisipkan bentuk persegi panjang

Dengan builder siap, panggil `InsertShape`. Anda menentukan `ShapeType`, lebar, dan tinggi dalam poin (1 pt ≈ 1/72 in).

```csharp
        // Insert a rectangle of 100 pt width and 50 pt height.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
```

*Mengapa ini penting*: Menetapkan `FillColor` dan `StrokeColor` membuat persegi panjang terlihat berbeda secara visual, yang membantu ketika Anda nanti mengelompokkan dengan bentuk lain.

## Cara mengelompokkan bentuk di Word

Mengelompokkan bentuk memungkinkan Anda memindahkan, memutar, atau memformat beberapa objek sebagai satu entitas. Setelah menyisipkan persegi panjang, tambahkan bentuk lain (sebuah elips dalam contoh ini) dan kemudian buat `GroupShape`.

```csharp
        // Insert an ellipse of 80 pt diameter.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // Insert an empty group container.
        GroupShape groupShape = builder.InsertGroupShape();

        // Add the rectangle and ellipse to the group.
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
```

Pemanggilan `InsertGroupShape` membuat placeholder yang dapat menampung sejumlah bentuk anak. Dengan menambahkan persegi panjang dan elips, Anda secara efektif **group shapes in Word**. Grup berperilaku seperti satu bentuk—Anda dapat memposisikannya kembali, menerapkan border, atau mengubah ukurannya tanpa memengaruhi tata letak internal masing‑masing anak.

### Tips pro

Setelah mengelompokkan, Anda dapat mengubah posisi grup relatif terhadap halaman:

```csharp
        // Move the whole group 150 pt right and 100 pt down.
        groupShape.Left = 150;
        groupShape.Top = 100;
```

## Simpan dokumen sebagai docx

Setelah bentuk-bentuk diatur, Anda perlu menyimpan file tersebut. Metode `Document.Save` secara otomatis menentukan format dari ekstensi file. Untuk **save document as docx**, berikan path yang berakhiran `.docx`.

```csharp
        // Save the document to the output folder.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

Menjalankan program menghasilkan `output.docx`. Buka file tersebut di Microsoft Word, dan Anda akan melihat persegi panjang berwarna biru muda dan elips berwarna merah muda muda dikelompokkan bersama. Anda dapat mengklik grup dan memindahkannya sebagai satu objek.

## Cara menggunakan DocumentBuilder secara efektif

`DocumentBuilder` lebih dari sekadar penyisip bentuk; ia juga menangani teks, tabel, header, dan footer. Saat Anda menggabungkan pembuatan bentuk dengan teks, ingatlah untuk mereset kursor jika Anda perlu menyisipkan konten di tempat lain:

```csharp
        // Move the cursor to a new paragraph after the group.
        builder.Writeln(); // Inserts a line break.
        builder.Font.Size = 12;
        builder.Writeln("Shapes have been added and grouped successfully.");
```

Menjaga status builder secara eksplisit menghindari penimpaan tidak sengaja dan membuat kode lebih mudah dipelihara.

## Kasus tepi dan variasi

| Situasi | Pendekatan yang disarankan |
|-----------|----------------------|
| **Lebih dari dua bentuk** | Sisipkan setiap bentuk, lalu panggil `AppendChild` untuk setiap bentuk sebelum menyimpan. |
| **Grup bersarang** | Buat sebuah grup, tambahkan bentuk, lalu sisipkan grup tersebut ke dalam `GroupShape` lain. |
| **Unit pengukuran yang berbeda** | Gunakan `builder.ConvertPixelsToPoints` jika Anda memiliki dimensi dalam piksel. |
| **Kompatibilitas dengan versi Word lama** | Simpan sebagai `.doc` dengan mengubah ekstensi; sebagian besar fitur bentuk masih berfungsi. |

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke dalam proyek konsol baru. Tidak ada cuplikan tambahan yang diperlukan.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;

        // 3️⃣ Insert an ellipse shape.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // 4️⃣ Create a group shape and add both shapes.
        GroupShape groupShape = builder.InsertGroupShape();
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Optional: reposition the group.
        groupShape.Left = 150;
        groupShape.Top = 100;

        // 5️⃣ Add a caption below the group.
        builder.Writeln();
        builder.Font.Size = 12;
        builder.Writeln("Grouped rectangle and ellipse created with DocumentBuilder.");

        // 6️⃣ Save the document as DOCX.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

**Hasil yang diharapkan**: Membuka `output.docx` menampilkan persegi panjang berwarna biru muda dan elips berwarna merah muda muda yang dikelompokkan bersama, diposisikan 150 pt dari margin kiri dan 100 pt dari atas. Keterangan muncul di bawah grup.

## Kesimpulan

Anda sekarang tahu cara **insert rectangle shape** dalam file Word menggunakan C#, **how to group shapes in Word**, dan **how to save document as docx** dengan Aspose.Words `DocumentBuilder`. Dengan menguasai langkah‑langkah ini Anda dapat membangun tata letak kompleks—sertifikat, laporan, atau formulir khusus—sepenuhnya melalui kode.

Selanjutnya, jelajahi topik terkait seperti **adding text boxes**, **working with tables**, atau **exporting to PDF**. Masing‑masing topik ini dibangun di atas dasar `DocumentBuilder` yang sama yang baru saja Anda praktikkan.

Siap mengotomatisasi dokumen Word Anda? Cobalah memperluas contoh dengan lebih banyak bentuk, menerapkan gradien, atau melakukan loop data untuk menghasilkan laporan lengkap dalam satu kali jalankan. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun pada teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Group Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Sisipkan Bentuk dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Buat bentuk persegi panjang di Word dengan Aspose.Words – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}