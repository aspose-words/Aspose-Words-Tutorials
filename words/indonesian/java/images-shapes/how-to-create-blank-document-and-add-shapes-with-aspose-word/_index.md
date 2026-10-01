---
category: general
date: 2026-09-30
description: Buat dokumen kosong dan sisipkan bentuk persegi panjang, elips, serta
  grup beberapa bentuk dalam C# menggunakan Aspose.Words. Pelajari cara menyisipkan
  bentuk dan cara membuat grup.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- insert rectangle shape
- group multiple shapes
- how to insert shapes
- how to create group
language: id
lastmod: 2026-09-30
og_description: Buat dokumen kosong di C# dan pelajari cara menyisipkan bentuk serta
  mengelompokkan beberapa bentuk dengan Aspose.Words. Ikuti tutorial langkah demi
  langkah.
og_image_alt: Screenshot of a C# program that creates a blank document, inserts a
  rectangle and ellipse, and groups them together.
og_title: Buat dokumen kosong dan kelompokkan bentuk di C# – Panduan Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Create blank document and insert rectangle shape, ellipse, and group
    multiple shapes in C# using Aspose.Words. Learn how to insert shapes and how to
    create group.
  headline: How to create blank document and add shapes with Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
- shapes
title: Cara membuat dokumen kosong dan menambahkan bentuk dengan Aspose.Words di C#
url: /id/java/images-shapes/how-to-create-blank-document-and-add-shapes-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat dokumen kosong dan menambahkan bentuk dengan Aspose.Words di C#

Jika Anda perlu **membuat dokumen kosong** dan mengisinya dengan grafik, panduan ini menunjukkan cara melakukannya secara tepat. Anda akan melihat cara **menyisipkan bentuk persegi panjang**, menambahkan objek gambar lainnya, dan kemudian **mengelompokkan beberapa bentuk** sehingga berperilaku sebagai satu unit.

Bekerja dengan bentuk adalah kebutuhan umum saat menghasilkan kontrak, sertifikat, atau laporan khusus. Dalam tutorial ini Anda akan mempelajari alur kerja lengkap, mulai dari menginisialisasi dokumen hingga menyimpan file akhir, menggunakan API Aspose.Words untuk .NET.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* .NET 6.0 (atau lebih baru) SDK terinstal  
* Lisensi Aspose.Words untuk .NET yang valid (versi percobaan gratis dapat digunakan untuk contoh ini)  
* IDE seperti Visual Studio 2022 atau Visual Studio Code  

Tidak ada paket NuGet tambahan yang diperlukan selain `Aspose.Words`.

## Cara membuat dokumen kosong dan bekerja dengan bentuk

Langkah pertama adalah menginstansiasi objek `Document`. Objek ini mewakili file Word dalam memori dan memberi Anda akses ke `DocumentBuilder`, yang merupakan alat utama untuk menyisipkan konten.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Mengapa ini penting:** Dokumen kosong memberi Anda kanvas bersih. `DocumentBuilder` mempertahankan titik sisipan saat ini, sehingga setiap bentuk yang Anda tambahkan secara otomatis ditempatkan pada halaman yang tepat.

## Menyisipkan bentuk persegi panjang dan bentuk lainnya

Selanjutnya, kita menambahkan sebuah persegi panjang dan sebuah elips. Kedua pemanggilan menggunakan metode `InsertShape` yang sama, yang merupakan cara yang direkomendasikan **bagaimana cara menyisipkan bentuk** di Aspose.Words.

```csharp
        // Step 2: Insert a rectangle shape (100 × 50 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;   // optional styling
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Insert an ellipse shape (80 × 80 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;
```

*Metode `InsertShape` secara otomatis menempatkan bentuk pada lokasi kursor saat ini.* Jika Anda memerlukan penempatan yang tepat, Anda dapat menyesuaikan `Shape.Left` dan `Shape.Top` setelah penyisipan.

## Mengelompokkan beberapa bentuk menjadi satu objek

Sekarang kita menggabungkan persegi panjang dan elips menjadi satu entitas logis. Pengelompokan berguna ketika Anda ingin memindahkan atau mengubah ukuran beberapa bentuk sekaligus.

```csharp
        // Step 4: Create a group shape that will hold multiple shapes
        GroupShape groupShape = builder.InsertGroupShape();

        // Step 5: Add the rectangle and ellipse to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional: Apply a border to the whole group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;
```

**Cara kerjanya:** `InsertGroupShape` membuat sebuah kontainer yang berperilaku seperti `Shape` lainnya. Dengan memanggil `AppendChild`, Anda memindahkan bentuk yang ada ke dalam kontainer, yang secara otomatis memperbarui koordinat relatif mereka.

### Tips praktis

Jika nanti Anda perlu **how to create group** secara programatik untuk lebih dari dua bentuk, cukup ulangi `AppendChild` untuk setiap instance `Shape` tambahan. Grup dapat berisi sejumlah objek gambar, termasuk gambar, kotak teks, atau bahkan grup lain.

## Contoh lengkap – cara menyisipkan bentuk dan menyimpan dokumen

Berikut adalah program lengkap yang dapat dijalankan dan mendemonstrasikan setiap langkah yang telah dibahas. Menjalankan kode ini menghasilkan file `ShapesDemo.docx` yang berisi sebuah persegi panjang, sebuah elips, dan sebuah bentuk yang dikelompokkan.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert rectangle shape
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // 3. Insert ellipse shape
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;

        // 4. Create a group shape
        GroupShape groupShape = builder.InsertGroupShape();

        // 5. Add shapes to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional styling for the group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;

        // 6. Save the document
        string outputPath = "ShapesDemo.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Output yang diharapkan:** Membuka `ShapesDemo.docx` di Microsoft Word menampilkan satu halaman dengan persegi panjang biru, elips hijau, dan batas abu‑abu di sekelilingnya yang mewakili grup. Memindahkan grup akan memindahkan kedua bentuk secara bersamaan, menegaskan bahwa operasi **group multiple shapes** berhasil.

## Pertanyaan umum dan penanganan kasus tepi

| Pertanyaan | Jawaban |
|------------|---------|
| *Bagaimana jika saya membutuhkan bentuk pada halaman tertentu?* | Panggil `builder.MoveToDocumentEnd();` sebelum menyisipkan bentuk, atau gunakan `builder.MoveToSection(sectionIndex);` untuk menargetkan bagian tertentu. |
| *Apakah saya dapat menambahkan teks di dalam bentuk yang dikelompokkan?* | Ya. Buat `Shape` dengan tipe `ShapeType.TextBox`, atur teksnya, lalu `AppendChild` ke `GroupShape`. |
| *Apakah dimensi bentuk menggunakan poin atau piksel?* | Aspose.Words menggunakan **poin** (1 pt = 1/72 inci). Ini memastikan ukuran konsisten di semua printer dan tampilan. |
| *Bagaimana cara mengubah rotasi grup?* | Atur `groupShape.RotationAngle = 45;` (derajat). Semua bentuk anak akan berotasi mengelilingi asal grup. |

## Kesimpulan

Anda kini tahu cara **membuat dokumen kosong**, **menyisipkan bentuk persegi panjang**, **how to insert shapes** seperti elips, dan **mengelompokkan beberapa bentuk** menjadi satu objek menggunakan Aspose.Words untuk .NET. Contoh kode lengkap menunjukkan pendekatan yang direkomendasikan, dan tip di atas membantu Anda menyesuaikan solusi untuk skenario yang lebih kompleks seperti menambahkan kotak teks atau memutar grup.

Siap menjelajah lebih jauh? Cobalah menambahkan bentuk gambar ke dalam grup, bereksperimen dengan warna isi yang berbeda, atau menghasilkan laporan multi‑halaman di mana setiap halaman berisi diagram yang dikelompokkan sendiri. Prinsip yang sama berlaku, sehingga Anda dapat memperluas pola ini ke proyek otomatisasi dokumen apa pun.

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Group Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Sisipkan Bentuk dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Buat dokumen Word kosong dengan Aspose.Words – Panduan Langkah demi Langkah](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}