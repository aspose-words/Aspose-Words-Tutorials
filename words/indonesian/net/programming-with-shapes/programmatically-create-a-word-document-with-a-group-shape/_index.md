---
category: general
date: 2026-09-27
description: Buat dokumen Word secara programatik dengan bentuk grup menggunakan Aspose.Words
  di C#. Ikuti panduan langkah demi langkah ini untuk menghasilkan file dan pelajari
  tip berguna.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- how to create group shape word
- Aspose.Words group shape
- C# Word automation
- StructuredDocumentTag example
language: id
lastmod: 2026-09-27
og_description: Buat dokumen Word secara programatis dengan bentuk grup menggunakan
  Aspose.Words. Tutorial ini memandu Anda melalui kode C# lengkap, menjelaskan setiap
  langkah, dan menampilkan output akhir.
og_image_alt: Screenshot of a Word document containing a group shape with a text placeholder
og_title: Membuat dokumen Word secara programatik dengan grup shape – panduan C#
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  headline: Programmatically create a Word document with a group shape
  type: TechArticle
- description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  name: Programmatically create a Word document with a group shape
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works with .NET Framework 4.7+). - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`). - A C# IDE such as
      Visual Studio 2022 or VS Code with the C# extension.'
  - name: Expected output screenshot (conceptual)
    text: '``` +-----------------------------------------------------------+ | ┌───────────────────────────────────────────────┐
      | | │ [Enter text here] │ | | └───────────────────────────────────────────────┘
      | +-----------------------------------------------------------+ ```'
  - name: Adding more child shapes
    text: 'You can enrich the group by appending additional drawing objects, such
      as pictures or text boxes:'
  - name: Controlling wrapping style
    text: 'If you need the group shape to stay behind text or to have tight wrapping,
      set the `WrapType` property:'
  - name: 'Edge case: Empty group shape'
    text: A `GroupShape` without children renders as an invisible placeholder. Always
      verify that at least one child (e.g., an SDT or a picture) is added; otherwise
      Word may drop the group during saving.
  - name: Compatibility note
    text: Aspose.Words 23.10+ fully supports `GroupShape` and `StructuredDocumentTag`.
      If you target older versions, the `AppendChild` method may behave differently,
      and you might need to call `UpdatePageLayout` after saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Membuat dokumen Word secara programatik dengan bentuk grup
url: /id/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat dokumen Word secara programatis dengan bentuk grup

Jika Anda perlu **membuat dokumen Word secara programatis** yang berisi gambar yang dikelompokkan, panduan ini menunjukkan secara tepat cara melakukannya dengan Aspose.Words untuk .NET. Baik Anda sedang membangun generator kontrak, pembuat laporan, atau alat pengisian formulir, Anda akan mempelajari kode C# lengkap, mengapa setiap panggilan API penting, dan cara menangani kasus tepi yang umum.

Membuat bentuk grup di Word dapat terasa rumit karena model objek Word memperlakukan group shape sebagai wadah untuk objek gambar lainnya. Tutorial ini tidak hanya menjawab **cara membuat group shape word** dokumen, tetapi juga menunjukkan cara menyematkan StructuredDocumentTag (SDT) teks biasa di dalam grup sehingga bentuk tersebut dapat menampung konten yang dapat diedit.

## Apa yang akan Anda capai

- Menginisialisasi dokumen Word kosong baru dengan `Document` dan `DocumentBuilder`.
- Menyisipkan `GroupShape` pada posisi kursor saat ini.
- Menambahkan `StructuredDocumentTag` (SDT) teks biasa ke dalam group shape.
- Menyimpan file sebagai `.docx` yang dapat dibuka di Microsoft Word.
- Memahami properti kunci `GroupShape` dan `StructuredDocumentTag` untuk ekstensi di masa mendatang.

### Prasyarat

- .NET 6.0 atau lebih baru (kode ini juga berfungsi dengan .NET Framework 4.7+).
- Paket NuGet Aspose.Words untuk .NET (`Install-Package Aspose.Words`).
- IDE C# seperti Visual Studio 2022 atau VS Code dengan ekstensi C#.

---

## Membuat dokumen Word secara programatis – menyiapkan proyek

1. **Buat proyek konsol baru**  
   ```bash
   dotnet new console -n WordGroupShapeDemo
   cd WordGroupShapeDemo
   dotnet add package Aspose.Words
   ```
2. **Buka proyek di IDE Anda** dan ganti isi `Program.cs` dengan kode yang ditunjukkan pada bagian berikut.

> **Pro tip:** Jaga folder proyek Anda tetap bersih; Aspose.Words menulis file output ke direktori kerja kecuali Anda memberikan path absolut.

## Langkah 1: Inisialisasi dokumen dan builder

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

// Create a new blank document.
Document doc = new Document();

// DocumentBuilder gives you a cursor to insert nodes.
DocumentBuilder builder = new DocumentBuilder(doc);

// Optional: set the page size or margins if your shape must fit a specific area.
builder.PageSetup.PageWidth = 595;   // A4 width in points
builder.PageSetup.PageHeight = 842;  // A4 height in points
```

**Mengapa ini penting:**  
`Document` mewakili seluruh file Word, sementara `DocumentBuilder` memungkinkan Anda menempatkan elemen baru tanpa harus menavigasi pohon node secara manual. Menetapkan dimensi halaman sejak awal memastikan group shape tidak melampaui halaman.

## Langkah 2: Sisipkan GroupShape pada lokasi kursor saat ini

```csharp
// Create an empty GroupShape container.
GroupShape groupShape = new GroupShape(doc)
{
    // Give the group a size that comfortably holds its children.
    Width = 300,
    Height = 150,

    // Position the group relative to the page (you can also use RelativeHorizontalPosition).
    Left = 100,
    Top = 100
};

// Insert the group shape into the document where the builder is currently positioned.
builder.InsertNode(groupShape);
```

**Penjelasan:**  
`GroupShape` adalah objek gambar yang dapat menampung bentuk lain, gambar, atau kotak teks. Dengan mengatur `Width`, `Height`, `Left`, dan `Top`, Anda mengontrol penempatan tepatnya di halaman. Metode `InsertNode` menempatkan bentuk dalam alur dokumen utama, berperilaku seperti objek mengambang.

## Langkah 3: Tambahkan StructuredDocumentTag (SDT) teks biasa di dalam grup

```csharp
// Create a plain‑text SDT that will act as a content placeholder.
StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Provide a helpful tag title that appears as a tooltip in Word.
    Title = "GroupShapeText",
    // Set default placeholder text.
    PlaceholderName = "Enter text here"
};

// Append the SDT to the group shape's child collection.
groupShape.AppendChild(sdtTag);
```

**Mengapa menggunakan SDT?**  
StructuredDocumentTag adalah kontrol konten native Word. Mereka memungkinkan pengguna mengedit teks langsung di dokumen yang disimpan, dan dapat diakses secara programatis nanti untuk ekstraksi data. Menempatkan SDT di dalam group shape memungkinkan Anda menggabungkan pengelompokan visual dengan konten yang dapat diedit.

## Langkah 4: Simpan dokumen

```csharp
// Define the output path – replace with your desired directory.
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShapeDemo.docx");

// Save the document in DOCX format.
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to: {outputPath}");
```

**Hasil:**  
Membuka `GroupShapeDemo.docx` di Microsoft Word menampilkan persegi panjang mengambang (group shape) yang berisi placeholder teks “Enter text here”. Pengguna dapat mengklik di dalam bentuk dan mengetik langsung.

### Screenshot output yang diharapkan (konseptual)

```
+-----------------------------------------------------------+
|   ┌───────────────────────────────────────────────┐   |
|   │  [Enter text here]                               │   |
|   └───────────────────────────────────────────────┘   |
+-----------------------------------------------------------+
```

Kotak luar adalah `GroupShape`; area abu-abu dalam adalah `StructuredDocumentTag`.

---

## Cara membuat group shape word – pertimbangan tambahan

### Menambahkan lebih banyak bentuk anak

Anda dapat memperkaya grup dengan menambahkan objek gambar tambahan, seperti gambar atau kotak teks:

```csharp
// Example: add a picture inside the same group.
Shape picture = new Shape(doc, ShapeType.Image)
{
    ImageData = ImageData.FromFile("logo.png"),
    Width = 100,
    Height = 50,
    Left = 10,
    Top = 80
};
groupShape.AppendChild(picture);
```

### Mengontrol gaya pembungkus

Jika Anda memerlukan group shape berada di belakang teks atau memiliki pembungkus ketat, atur properti `WrapType`:

```csharp
groupShape.WrapType = WrapType.Inline; // Makes the shape behave like a paragraph.
```

### Kasus tepi: Group shape kosong

`GroupShape` tanpa anak akan dirender sebagai placeholder tak terlihat. Selalu pastikan setidaknya satu anak (misalnya, SDT atau gambar) ditambahkan; jika tidak, Word mungkin menghapus grup saat menyimpan.

### Catatan kompatibilitas

Aspose.Words 23.10+ sepenuhnya mendukung `GroupShape` dan `StructuredDocumentTag`. Jika Anda menargetkan versi lebih lama, metode `AppendChild` mungkin berperilaku berbeda, dan Anda mungkin perlu memanggil `UpdatePageLayout` setelah menyimpan.

---

## Contoh lengkap yang dapat dijalankan

Salin seluruh potongan kode di bawah ini ke `Program.cs` dan jalankan proyek. Kode ini mencakup semua langkah di atas dalam satu program yang berdiri sendiri.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.PageSetup.PageWidth = 595;
        builder.PageSetup.PageHeight = 842;

        // 2️⃣ Create and insert a GroupShape.
        GroupShape groupShape = new GroupShape(doc)
        {
            Width = 300,
            Height = 150,
            Left = 100,
            Top = 100
        };
        builder.InsertNode(groupShape);

        // 3️⃣ Add a plain‑text StructuredDocumentTag (SDT) inside the group.
        StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
        {
            Title = "GroupShapeText",
            PlaceholderName = "Enter text here"
        };
        groupShape.AppendChild(sdtTag);

        // 4️⃣ Optional: add a picture to demonstrate multiple children.
        // Uncomment and adjust the path if you want to test this.
        /*
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            ImageData = ImageData.FromFile("logo.png"),
            Width = 100,
            Height = 50,
            Left


## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun pada teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Group Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Buat bentuk persegi panjang di Word menggunakan C# – Panduan Langkah demi Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Buat dokumen Word kosong dengan Aspose.Words – Panduan Langkah demi Langkah](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}