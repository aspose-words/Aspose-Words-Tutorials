---
category: general
date: 2026-08-04
description: Simpan file docx secara programatis sambil menambahkan bentuk persegi
  panjang dan mengelompokkan bentuk di Word. Pelajari cara mengatur dimensi bentuk
  dan membuat kotak teks secara programatis.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx file
- add rectangle shape
- group shapes word
- set shape dimensions
- create textbox programmatically
language: id
lastmod: 2026-08-04
og_description: Simpan file docx menggunakan C# dengan menambahkan bentuk persegi
  panjang, mengelompokkan bentuk di Word, mengatur dimensi bentuk, dan membuat kotak
  teks secara programatis.
og_image_alt: Screenshot of a saved docx file that contains a grouped rectangle and
  textbox
og_title: Simpan file docx dengan bentuk yang dikelompokkan di Word – Panduan langkah
  demi langkah C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  headline: Save docx file with grouped shapes in Word using C#
  type: TechArticle
- description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  name: Save docx file with grouped shapes in Word using C#
  steps:
  - name: 1. Create a new document and a builder
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing; using Aspose.Words.Drawing.Shapes;'
  - name: 2. Add rectangle shape to a group
    text: '```csharp // Create a group container that will hold all shapes. GroupShape
      group = new GroupShape(doc) { Width = 400, // Set shape dimensions for the group.
      Height = 200 };'
  - name: 3. Group shapes in Word document
    text: The `GroupShape` class aggregates multiple drawing objects. Grouping is
      useful when you want to treat several objects as a single unit (e.g., moving,
      rotating, or copying them together).
  - name: 4. Set shape dimensions for precise layout
    text: Both the group and its child shapes need explicit dimensions; otherwise
      Word applies default sizes that may not match your design.
  - name: 5. Create textbox programmatically inside the group
    text: '```csharp // Add a textbox shape with custom text. Shape textBox = new
      Shape(doc, ShapeType.TextBox) { Width = 180, Height = 100, Left = 210, // Position
      relative to the group’s coordinate system. Top = 10 };'
  - name: 6. Insert group shape and **save docx file**
    text: '```csharp // Insert the completed group into the document at the current
      cursor position. builder.InsertNode(group);'
  - name: Expected output
    text: '* A file named **GroupShape.docx** appears in the output directory. * Opening
      the file shows a rectangular shape on the left and a textbox containing “Grouped
      text” on the right, both locked together. * Selecting either shape moves the
      entire group, confirming that **group shapes word** functionalit'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Simpan file docx dengan bentuk yang dikelompokkan di Word menggunakan C#
url: /id/net/programming-with-shapes/save-docx-file-with-grouped-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Simpan file docx dengan bentuk yang dikelompokkan di Word menggunakan C#

Jika Anda perlu **save docx file** yang berisi beberapa bentuk yang disusun bersama, panduan ini menunjukkan cara melakukannya dengan C#. Anda akan belajar cara **add rectangle shape**, mengelompokkan beberapa bentuk dalam dokumen Word, **set shape dimensions**, dan **create textbox programmatically**. Solusi ini bekerja dengan Aspose.Words for .NET versi terbaru dan berjalan pada .NET 6 atau yang lebih baru.

Tutorial ini membahas setiap langkah, mulai dari penyiapan proyek hingga pemanggilan `doc.Save` akhir. Pada akhirnya Anda akan memiliki potongan kode yang dapat digunakan kembali dan dapat ditempelkan ke proyek console atau ASP.NET apa pun. Tidak diperlukan skrip eksternal atau penyuntingan manual file DOCX.

## Prerequisites

Sebelum Anda memulai, pastikan Anda memiliki:

* .NET 6 SDK (atau yang lebih baru) terpasang.
* Lisensi yang valid untuk **Aspose.Words for .NET** (versi percobaan gratis cukup untuk pengujian).
* Visual Studio 2022, VS Code, atau IDE apa pun yang dapat membangun proyek .NET.

Kode ini hanya menggunakan namespace Aspose.Words, jadi tidak diperlukan paket NuGet tambahan.

## Save docx file with grouped shapes in Word

Inti solusi adalah membangun sebuah `GroupShape` yang berisi persegi panjang dan kotak teks, kemudian menyisipkan grup tersebut ke dalam dokumen dan memanggil `doc.Save`. Bagian‑bagian berikut memecah proses menjadi potongan‑potongan yang mudah dikelola.

### 1. Create a new document and a builder

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // Initialize a blank document.
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for editing the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Mengapa langkah ini penting* – Objek `Document` baru mewakili file *.docx* yang kosong. `DocumentBuilder` menyediakan metode tingkat tinggi seperti `InsertNode`, yang akan kita gunakan untuk menempatkan grup bentuk.

### 2. Add rectangle shape to a group

```csharp
        // Create a group container that will hold all shapes.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,   // Set shape dimensions for the group.
            Height = 200
        };

        // Add a rectangle shape that will be part of the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,   // Set shape dimensions for the rectangle.
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);
```

*Mengapa langkah ini penting* – Operasi **add rectangle shape** memperlihatkan cara mendefinisikan elemen visual dengan ukuran dan posisi yang tepat. Persegi panjang berada di dalam `group`, sehingga memindahkan grup nanti secara otomatis memindahkan persegi panjang.

### 3. Group shapes in Word document

Kelas `GroupShape` menggabungkan beberapa objek gambar. Pengelompokan berguna ketika Anda ingin memperlakukan beberapa objek sebagai satu unit (misalnya, memindahkan, memutar, atau menyalin mereka bersama‑sama).

```csharp
        // The group now contains the rectangle; we will add more shapes next.
```

*Mengapa kita mengelompokkan* – Pengelompokan mengurangi kompleksitas tata letak. Alih‑alih memposisikan setiap bentuk secara individual pada halaman, Anda cukup mengatur `Left`, `Top`, `Width`, dan `Height` grup sekali saja.

### 4. Set shape dimensions for precise layout

Baik grup maupun bentuk anaknya memerlukan dimensi eksplisit; jika tidak, Word akan menerapkan ukuran default yang mungkin tidak sesuai dengan desain Anda.

```csharp
        // Example of adjusting the group’s overall size.
        group.Width = 400;   // Overall width of the grouped area.
        group.Height = 200;  // Overall height of the grouped area.
```

*Mengapa kita mengatur dimensi* – Pengukuran yang tepat memastikan bahwa persegi panjang dan kotak teks tidak saling tumpang tindih secara tidak sengaja dan bahwa **save docx file** akhir cocok dengan tata letak yang diinginkan.

### 5. Create textbox programmatically inside the group

```csharp
        // Add a textbox shape with custom text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,   // Position relative to the group’s coordinate system.
            Top = 10
        };

        // Populate the textbox with a paragraph containing a run.
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);

        // Append the textbox to the same group.
        group.AppendChild(textBox);
```

*Mengapa langkah ini penting* – Segmen **create textbox programmatically** menunjukkan cara menyematkan teks kaya di dalam sebuah bentuk. Menggunakan `Paragraph` dan `Run` memberi Anda kontrol penuh atas pemformatan nantinya.

### 6. Insert group shape and **save docx file**

```csharp
        // Insert the completed group into the document at the current cursor position.
        builder.InsertNode(group);

        // Save the document to the file system.
        doc.Save("GroupShape.docx");   // The file now contains a rectangle and a textbox grouped together.
    }
}
```

*Mengapa langkah akhir ini penting* – Pemanggilan `InsertNode` menempatkan bentuk yang dikelompokkan tepat pada posisi kursor builder. Metode `doc.Save` melakukan operasi **save docx file**, menulis dokumen Word lengkap ke disk.

> **Hasil:** Membuka *GroupShape.docx* di Microsoft Word menampilkan sebuah persegi panjang di sebelah kiri dan kotak teks di sebelah kanan, keduanya terkunci bersama dalam satu grup. Anda dapat memindahkan grup sebagai satu unit, mengubah ukurannya, atau menerapkan pemformatan tambahan.

## Full, runnable example

Salin kode di bawah ini ke dalam proyek console baru (`dotnet new console`) dan jalankan `dotnet run`. Program akan membuat `GroupShape.docx` di folder output proyek.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a group shape container.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,
            Height = 200
        };

        // 3. Add rectangle shape.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);

        // 4. Add textbox shape with text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,
            Top = 10
        };
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);
        group.AppendChild(textBox);

        // 5. Insert the group into the document.
        builder.InsertNode(group);

        // 6. Save the document.
        doc.Save("GroupShape.docx");
    }
}
```

### Expected output

* Sebuah file bernama **GroupShape.docx** muncul di direktori output.
* Membuka file menampilkan bentuk persegi panjang di sebelah kiri dan kotak teks yang berisi “Grouped text” di sebelah kanan, keduanya terkunci bersama.
* Memilih salah satu bentuk memindahkan seluruh grup, mengonfirmasi bahwa fungsionalitas **group shapes word** bekerja sebagaimana mestinya.

## Common variations and edge cases

| Situation | Recommendation |
|-----------|----------------|
| Membutuhkan lebih dari dua bentuk | Tambahkan objek `Shape` tambahan ke `group` sebelum memanggil `builder.InsertNode`. |
| Ingin grup muncul pada halaman tertentu | Pindahkan kursor builder dengan `builder.MoveToDocumentEnd()` atau `builder.MoveToPage(pageNumber)`. |
| Memerlukan satuan berbeda (misalnya sentimeter) | Gunakan `ConvertUtil.InchToPoint(1.0)` untuk mengonversi inci ke poin, satuan yang diharapkan Word. |
| Ingin kotak teks membungkus teks | Atur `textBox.TextBoxWrap = TextBoxWrapType.Square` setelah membuat kotak teks. |
| Bekerja dengan versi .NET Framework yang lebih lama | API yang sama bekerja dengan .NET Framework 4.7+, tetapi pastikan Anda merujuk pada versi Aspose.Words yang tepat. |

**Tips pro:** Selalu atur `Width` dan `Height` grup *setelah* menambahkan semua bentuk anak. Ini menjamin grup sepenuhnya melingkupi isinya, mencegah pemotongan ketika dokumen dibuka di Word.

## Conclusion

Anda kini tahu cara **save docx file** sambil **add rectangle shape**, **group shapes word**, **set shape dimensions**, dan **create textbox programmatically** menggunakan Aspose.Words for .NET. Contoh lengkap ini memperlihatkan pola bersih dan dapat diulang yang dapat Anda sesuaikan untuk tata letak yang lebih kompleks, seperti diagram, gambar,

## What Should You Learn Next?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat bentuk persegi panjang di Word menggunakan C# – Panduan Langkah-demi-Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Buat Group Shape di Dokumen Word Menggunakan Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Tutorial Bayangan Bentuk Aspose.Words – Tambahkan Bayangan ke Bentuk Word di C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}