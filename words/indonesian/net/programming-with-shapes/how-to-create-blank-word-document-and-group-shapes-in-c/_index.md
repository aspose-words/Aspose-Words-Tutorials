---
category: general
date: 2026-10-07
description: Buat dokumen Word kosong dalam C# dan pelajari cara menambahkan bentuk
  persegi panjang, menyisipkan bentuk gambar, serta mengelompokkan beberapa bentuk
  untuk laporan dinamis.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- insert image shape
- group multiple shapes
- add image to word
language: id
lastmod: 2026-10-07
og_description: Buat dokumen Word kosong di C# dengan Aspose.Words. Pelajari cara
  menambahkan bentuk persegi panjang, menyisipkan bentuk gambar, dan mengelompokkan
  beberapa bentuk untuk dokumen profesional.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and logo created
  with C#
og_title: Buat dokumen Word kosong dan grupkan bentuk di C# – panduan langkah demi
  langkah
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create blank Word document in C# and learn to add rectangle shape,
    insert image shape, and group multiple shapes for dynamic reports.
  headline: How to create blank Word document and group shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Cara membuat dokumen Word kosong dan mengelompokkan bentuk di C#
url: /id/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat dokumen Word kosong dan mengelompokkan bentuk di C#

Jika Anda perlu **create blank Word document** secara programatis, panduan ini menunjukkan secara tepat cara melakukannya. Anda akan melihat cara **add rectangle shape**, **insert image shape**, dan **group multiple shapes** sehingga mereka berperilaku sebagai satu objek ketika Anda **add image to Word** nanti.

Bekerja dengan file Word dari kode dapat terasa menakutkan, tetapi Aspose.Words membuat prosesnya sederhana. Pada akhir tutorial ini Anda akan memiliki potongan kode C# yang dapat digunakan kembali yang menghasilkan file Word bersih dan kosong yang berisi sebuah rectangle yang dikelompokkan dan logo. Anda dapat menyematkan hasilnya dalam faktur, laporan, atau alur kerja dokumen otomatis apa pun.

## Prasyarat

* .NET 6.0 atau lebih baru (kode juga berfungsi dengan .NET Framework 4.7+).  
* Lisensi Aspose.Words for .NET yang valid atau kunci evaluasi gratis.  
* File gambar (misalnya `logo.png`) yang ditempatkan di folder yang dapat Anda referensikan dari kode.  
* Visual Studio 2022 atau IDE kompatibel C# apa pun.

Tidak ada paket NuGet tambahan yang diperlukan selain `Aspose.Words`.

## Cara membuat dokumen Word kosong dengan Aspose.Words

Langkah pertama selalu untuk **create blank Word document**. Objek ini akan menampung semua bentuk selanjutnya.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// 1️⃣ Initialize a new empty document.
Document doc = new Document();

// 2️⃣ Prepare a DocumentBuilder – it simplifies adding content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` mewakili seluruh file `.docx`. Pada titik ini file kosong, yang memenuhi persyaratan *create blank Word document*.

## Buat kontainer untuk mengelompokkan beberapa bentuk

Mengelompokkan bentuk memungkinkan Anda memindahkan, memutar, atau mengubah ukuran mereka secara bersamaan. Aspose.Words menyediakan kelas `GroupShape` untuk tujuan ini.

```csharp
// 3️⃣ Create a GroupShape that will hold our drawing objects.
GroupShape group = new GroupShape(doc)
{
    // Define the container’s position and size on the page.
    Bounds = new Rectangle(50, 50, 300, 200)
};

// Append the group to the first paragraph of the first section.
doc.FirstSection.Body.FirstParagraph.AppendChild(group);
```

Rectangle `Bounds` menentukan di mana grup muncul di halaman. Dengan menempatkan grup di paragraf pertama Anda memastikan bahwa **create blank Word document** akan segera berisi kontainer visual.

## Cara menambahkan rectangle shape di dalam grup

Kebutuhan umum adalah **add rectangle shape** sebagai latar belakang atau batas. Kode berikut membuat rectangle dan menambahkannya ke grup yang telah didefinisikan sebelumnya.

```csharp
// 4️⃣ Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 100,
    Height = 80,
    Left = 20,
    Top = 20,
    // Optional: give the rectangle a light gray fill.
    FillColor = Color.LightGray
};

// Add the rectangle to the group.
group.AppendChild(rectangle);
```

Karena rectangle berada di dalam `GroupShape`, ia akan bergerak bersama bentuk lain yang Anda tambahkan nanti. Ini adalah inti dari fungsionalitas **group multiple shapes**.

## Cara menyisipkan image shape di dalam grup

Selanjutnya, Anda akan **insert image shape** (logo) dan menempatkannya di samping rectangle. Ini menunjukkan alur kerja **add image to Word**.

```csharp
// 5️⃣ Create an image shape.
Shape picture = new Shape(doc, ShapeType.Image)
{
    Width = 80,
    Height = 80,
    Left = 150,
    Top = 30
};

// Load the image from disk. Replace the path with your actual image location.
picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));

// Add the image shape to the same group.
group.AppendChild(picture);
```

Metode `SetImage` membaca file dan menyematkannya langsung ke dalam dokumen Word, memastikan gambar tetap ada bahkan ketika file sumber dipindahkan. Ini menyelesaikan langkah **insert image shape** dan memenuhi persyaratan **add image to Word**.

## Simpan dokumen

Akhirnya, simpan file ke disk. File yang disimpan berisi dokumen kosong, rectangle yang dikelompokkan, dan logo yang disematkan.

```csharp
// 6️⃣ Save the document with the grouped shapes.
doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
```

Saat Anda membuka `GroupShape.docx` di Microsoft Word, Anda akan melihat satu grup yang mencakup rectangle berwarna abu‑abu muda dan logo yang ditempatkan berdampingan. Memilih bagian mana pun dari grup memungkinkan Anda memindahkan atau mengubah ukuran seluruh koleksi, membuktikan bahwa bentuk‑bentuk tersebut memang **group multiple shapes**.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin, tempel, dan jalankan. Ganti `YOUR_DIRECTORY` dengan jalur absolut atau relatif yang ada di mesin Anda.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank Word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Create a GroupShape to hold the rectangle and image.
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new Rectangle(50, 50, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);

        // Step 3: Add a rectangle shape inside the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 100,
            Height = 80,
            Left = 20,
            Top = 20,
            FillColor = Color.LightGray
        };
        group.AppendChild(rectangle);

        // Step 4: Insert an image shape inside the group.
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            Width = 80,
            Height = 80,
            Left = 150,
            Top = 30
        };
        picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));
        group.AppendChild(picture);

        // Step 5: Save the document.
        doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
    }
}
```

### Output yang diharapkan

* Sebuah file bernama `GroupShape.docx` yang terletak di `YOUR_DIRECTORY`.  
* Membuka file di Word menampilkan satu grup visual yang berisi rectangle abu‑abu di sebelah kiri dan `logo.png` di sebelah kanan.  
* Memilih bagian mana pun dari grup visual memungkinkan Anda memindahkan atau mengubah ukuran seluruh koleksi, mengonfirmasi bahwa bentuk‑bentuk tersebut benar‑benar **group multiple shapes**.

## Pertanyaan umum dan penanganan kasus tepi

| Question | Answer |
|---|---|
| **Bisakah saya menambahkan lebih dari dua bentuk ke grup yang sama?** | Ya. Panggil `group.AppendChild(yourShape)` untuk setiap `Shape` tambahan. Grup dapat berisi sejumlah objek gambar apa pun. |
| **Bagaimana jika file gambar tidak ada?** | `SetImage` akan melempar `FileNotFoundException`. Bungkus pemanggilan tersebut dalam blok try‑catch dan sediakan fallback (misalnya, shape placeholder). |
| **Apakah saya perlu mengatur `WrapType` untuk bentuk‑bentuk?** | Secara default bentuk‑bentuk bersifat inline. Jika Anda memerlukan perilaku mengambang, atur `picture.WrapType = WrapType.Inline;` atau mode wrap lain sebelum menambahkannya ke grup. |
| **Bagaimana ukuran dokumen memengaruhi batas grup?** | Rectangle `Bounds` didefinisikan dalam poin (1 pt ≈ 1/72 in). Sesuaikan ukuran jika Anda menempatkan grup pada tata letak halaman yang berbeda (mis., A4 vs. Letter). |
| **Bisakah saya menggunakan kembali grup yang sama di dokumen lain?** | Ya. Kloning grup dengan `GroupShape cloned = (GroupShape)group.Clone(true);` dan sisipkan ke dalam `Document` yang berbeda. |

## Tips profesional

* **Reuse the `DocumentBuilder`** untuk menambahkan teks sebelum atau sesudah grup. Itu secara otomatis menghormati posisi kursor saat ini.  
* **Set `Shape.StrokeColor`** jika Anda memerlukan batas yang terlihat di sekitar rectangle.  
* **Use high‑resolution PNGs** untuk logo agar menghindari pixelation ketika

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Group Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Buat rectangle shape di Word menggunakan C# – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Sisipkan Inline Image dalam Dokumen Word menggunakan Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}