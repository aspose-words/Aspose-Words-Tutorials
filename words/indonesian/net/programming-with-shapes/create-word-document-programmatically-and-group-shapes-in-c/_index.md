---
category: general
date: 2026-08-10
description: Buat dokumen Word secara programatis menggunakan Aspose.Words, pelajari
  cara mengelompokkan beberapa bentuk di Word, menambahkan persegi panjang ke Word,
  dan membuat grup bentuk dalam C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- group multiple shapes word
- add rectangle to word
- how to create group shape
language: id
lastmod: 2026-08-10
og_description: Buat dokumen Word secara programatis dengan Aspose.Words. Panduan
  ini menunjukkan cara mengelompokkan beberapa bentuk di Word, menambahkan persegi
  panjang ke Word, dan menyematkan kontrol konten teks biasa, semuanya dalam C#.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and ellipse with
  a plain‑text content control
og_title: Buat dokumen Word secara programatis – grupkan bentuk di C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  headline: Create word document programmatically and group shapes in C#
  type: TechArticle
- description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  name: Create word document programmatically and group shapes in C#
  steps:
  - name: – Initialize the document and builder
    text: The `Document` object represents the entire DOCX file, while `DocumentBuilder`
      provides a convenient API to add content. Initializing them is the first requirement
      whenever you **create word document programmatically**.
  - name: – Create a group shape container
    text: A `Shape` with `ShapeType.Group` acts as a canvas that can hold other shapes.
      Setting `Width` and `Height` defines the bounding box for the group. This is
      the core of **how to create group shape** in Aspose.Words.
  - name: – Add a rectangle to word
    text: A rectangle is created with `ShapeType.Rectangle`. Its `Left` and `Top`
      properties position it relative to the group’s origin. This step demonstrates
      **add rectangle to word** and shows how you can control exact placement.
  - name: – Add an ellipse (circle) to the group
    text: An ellipse is added the same way as the rectangle, but with `ShapeType.Ellipse`.
      The `Left = 210` moves it to the right of the rectangle, creating a visually
      distinct pair of shapes inside the same group.
  - name: – Insert the completed group shape into the document
    text: '`builder.InsertNode(groupShape)` places the whole group at the current
      cursor location. Because the group already contains its children, you do not
      need additional insert calls for the rectangle or ellipse.'
  - name: – Create a plain‑text StructuredDocumentTag (SDT)
    text: A StructuredDocumentTag is a content control that end users can fill in
      when the document is opened in Word. Setting `Title = "CustomerName"` gives
      the control a meaningful identifier, which is useful for later data extraction.
  - name: – Save the document
    text: '`doc.Save("GroupAndSDT.docx")` writes the file to disk. The resulting DOCX
      contains the grouped shapes and the SDT. Opening the file in Microsoft Word
      will show a rectangle next to a circle, both selectable as a single object,
      followed by a placeholder “Enter name here …”.'
  - name: Using different shape types
    text: You can replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other
      `ShapeType` (e.g., `ShapeType.Polygon`, `ShapeType.Line`). The grouping logic
      remains identical.
  - name: Setting fill color and borders
    text: '```csharp rectangleShape.FillColor = System.Drawing.Color.LightBlue; rectangleShape.StrokeColor
      = System.Drawing.Color.DarkBlue; ellipseShape.FillColor = System.Drawing.Color.LightCoral;
      ``` Adding fill and stroke improves visual distinction, especially when the
      document is shared with non‑technical'
  - name: Rotating the entire group
    text: '```csharp groupShape.Rotation = 45; // rotates both shapes together ```
      Rotating the group is more efficient than rotating each child individually.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Membuat dokumen Word secara programatis dan mengelompokkan bentuk di C#
url: /id/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen Word secara programatis dan grupkan bentuk di C#

Jika Anda perlu **create word document programmatically**, tutorial ini menunjukkan cara membangun file DOCX dengan Aspose.Words dan **group multiple shapes word** bersama-sama. Kami juga akan membahas **add rectangle to word** dan **how to create group shape** yang berisi baik persegi panjang maupun elips, plus StructuredDocumentTag teks polos untuk input pengguna.

Anda akan selesai dengan file Word siap pakai yang berisi bentuk grup persegi panjang‑elips dan kontrol konten di mana pengguna dapat mengetikkan nama. Tidak diperlukan penyuntingan manual di Word setelah kode dijalankan.

## Apa yang Anda Butuhkan

- .NET 6.0 atau lebih baru (contoh menarget .NET 6, tetapi versi .NET terbaru mana pun dapat digunakan)
- Lisensi Aspose.Words untuk .NET (versi percobaan gratis dapat digunakan untuk pengujian)
- Visual Studio 2022 atau IDE C# lain yang Anda sukai
- Familiaritas dasar dengan sintaks C#

## Buat dokumen Word secara programatis – alur kerja keseluruhan

Proses terdiri dari tiga fase logis:

1. **Initialize** sebuah `Document` dan `DocumentBuilder` – fondasi untuk setiap file Word yang Anda hasilkan.
2. **Build a group shape** yang menampung persegi panjang dan elips – menunjukkan **group multiple shapes word** dan **how to create group shape**.
3. **Insert a StructuredDocumentTag (SDT)** – kontrol konten teks polos yang memungkinkan pengguna akhir mengisi data, menggambarkan **add rectangle to word** sebagai bagian dari tata letak dokumen keseluruhan.

Berikut adalah kode lengkap yang dapat dijalankan diikuti dengan penjelasan langkah demi langkah.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1 – Initialize the document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2 – Create a group shape container
            Shape groupShape = new Shape(doc, ShapeType.Group)
            {
                Width = 400,
                Height = 200
            };

            // Step 3 – Add a rectangle to the group
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 0,
                Top = 0
            };
            groupShape.GroupShape.AddChild(rectangleShape);

            // Step 4 – Add an ellipse (circle) to the group
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse)
            {
                Width = 100,
                Height = 100,
                Left = 210, // Position next to the rectangle
                Top = 0
            };
            groupShape.GroupShape.AddChild(ellipseShape);

            // Step 5 – Insert the completed group shape into the document
            builder.InsertNode(groupShape);

            // Step 6 – Create a plain‑text StructuredDocumentTag for user input
            StructuredDocumentTag sdtTag = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Block)
            {
                Title = "CustomerName"
            };
            builder.InsertNode(sdtTag);
            builder.Writeln("Enter name here …");

            // Step 7 – Save the document
            doc.Save("GroupAndSDT.docx");
            Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Langkah 1 – Inisialisasi dokumen dan builder
`Document` mewakili seluruh file DOCX, sementara `DocumentBuilder` menyediakan API yang nyaman untuk menambahkan konten. Menginisialisasinya adalah persyaratan pertama setiap kali Anda **create word document programmatically**.

> **Pro tip:** Jika Anda berencana menggunakan kembali dokumen yang sama pada beberapa operasi, pertahankan satu instance `DocumentBuilder` untuk menghindari pembuatan objek yang tidak perlu.

### Langkah 2 – Buat kontainer group shape
`Shape` dengan `ShapeType.Group` berfungsi sebagai kanvas yang dapat menampung bentuk lain. Menetapkan `Width` dan `Height` menentukan kotak pembatas untuk grup. Ini adalah inti dari **how to create group shape** di Aspose.Words.

> **Edge case:** Jika lebar grup lebih kecil daripada lebar gabungan anak‑anaknya, anak‑anak akan terpotong. Selalu buat grup cukup besar untuk menampung setiap bentuk anak.

### Langkah 3 – Tambahkan persegi panjang ke Word
Persegi panjang dibuat dengan `ShapeType.Rectangle`. Properti `Left` dan `Top` menempatkannya relatif terhadap asal grup. Langkah ini menunjukkan **add rectangle to word** dan memperlihatkan cara Anda dapat mengontrol penempatan tepat.

> **Common mistake:** Lupa mengatur `Left`/`Top` menyebabkan persegi panjang muncul di asal default grup (0,0), yang mungkin tumpang tindih dengan anak lain.

### Langkah 4 – Tambahkan elips (lingkaran) ke grup
Elips ditambahkan dengan cara yang sama seperti persegi panjang, tetapi dengan `ShapeType.Ellipse`. `Left = 210` memindahkannya ke kanan persegi panjang, menciptakan pasangan bentuk yang terlihat berbeda di dalam grup yang sama.

> **Why use a group?** Pengelompokan memungkinkan Anda memindahkan, memutar, atau mengubah ukuran kedua bentuk sekaligus dengan satu operasi nanti, mempertahankan tata letak relatif mereka.

### Langkah 5 – Sisipkan group shape yang selesai ke dalam dokumen
`builder.InsertNode(groupShape)` menempatkan seluruh grup pada lokasi kursor saat ini. Karena grup sudah berisi anak‑anaknya, Anda tidak memerlukan panggilan insert tambahan untuk persegi panjang atau elips.

### Langkah 6 – Buat StructuredDocumentTag (SDT) teks polos
StructuredDocumentTag adalah kontrol konten yang dapat diisi oleh pengguna akhir ketika dokumen dibuka di Word. Menetapkan `Title = "CustomerName"` memberi kontrol identifier yang bermakna, yang berguna untuk ekstraksi data selanjutnya.

> **Why a plain‑text SDT?** Ini membatasi input ke teks polos, mencegah pemformatan tidak sengaja yang dapat merusak proses selanjutnya.

### Langkah 7 – Simpan dokumen
`doc.Save("GroupAndSDT.docx")` menulis file ke disk. DOCX yang dihasilkan berisi bentuk yang dikelompokkan dan SDT. Membuka file di Microsoft Word akan menampilkan persegi panjang di sebelah lingkaran, keduanya dapat dipilih sebagai satu objek, diikuti dengan placeholder “Enter name here …”.

#### Output yang Diharapkan
- Sebuah file bernama **GroupAndSDT.docx** di folder eksekusi.
- Di Word: sebuah group shape (persegi panjang + elips) yang dapat Anda pindahkan sebagai satu unit.
- Tepat di bawah grup, kontrol konten berbayang abu‑abu yang meminta pengguna mengetikkan nama.

## Variasi tambahan dan praktik terbaik

### Menggunakan tipe shape yang berbeda
Anda dapat mengganti `ShapeType.Rectangle` atau `ShapeType.Ellipse` dengan `ShapeType` lain apa pun (mis., `ShapeType.Polygon`, `ShapeType.Line`). Logika pengelompokan tetap sama.

### Menetapkan warna isi dan batas
```csharp
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```
Menambahkan isi dan garis tepi meningkatkan perbedaan visual, terutama ketika dokumen dibagikan dengan pemangku kepentingan non‑teknis.

### Memutar seluruh grup
```csharp
groupShape.Rotation = 45; // rotates both shapes together
```
Memutar grup lebih efisien daripada memutar setiap anak secara terpisah.

### Mengekspor ke PDF
Jika Anda memerlukan versi PDF, cukup panggil:
```csharp
doc.Save("GroupAndSDT.pdf", SaveFormat.Pdf);
```
Semua bentuk yang dikelompokkan dan SDT (ditampilkan sebagai bidang teks) akan muncul di PDF.

## Kesulitan umum dan cara menghindarinya

| Gejala | Penyebab | Solusi |
|--------|----------|--------|

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Group Shape di Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Buat shape persegi panjang di Word menggunakan C# – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Buat Dokumen Word Kosong dengan Shape Persegi Panjang Berbayang – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}