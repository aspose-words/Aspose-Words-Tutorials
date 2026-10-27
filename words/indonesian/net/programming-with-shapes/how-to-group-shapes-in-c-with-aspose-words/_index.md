---
category: general
date: 2026-08-23
description: Pelajari cara mengelompokkan bentuk di C# menggunakan Aspose.Words. Panduan
  ini juga mencakup cara menyisipkan bentuk persegi panjang dan menambahkan bentuk
  ke dokumen Word yang kompleks.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- add shapes word
- group multiple shapes
- how to start group
language: id
lastmod: 2026-08-23
og_description: Bagaimana cara mengelompokkan bentuk di C# dengan Aspose.Words. Ikuti
  tutorial lengkap ini untuk menyisipkan bentuk persegi panjang, menambahkan bentuk
  ke Word, dan mengelompokkan beberapa bentuk secara efisien.
og_image_alt: How to group shapes in C# using Aspose.Words
og_title: Cara mengelompokkan bentuk di C# – panduan langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  headline: How to group shapes in C# with Aspose.Words
  type: TechArticle
- description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  name: How to group shapes in C# with Aspose.Words
  steps:
  - name: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
    text: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
  - name: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
    text: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
  - name: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
    text: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the existing `Shape` objects, call `builder.StartGroupShape()`,
      re‑insert them with `builder.InsertShape(existingShape)`, then call `EndGroupShape()`.
    question: Can I group shapes that already exist in the document?
  - answer: Aspose.Words adds a `<w:grpSp>` element that contains each shape’s `<w:sp>`
      node. This is fully compliant with the Office Open XML specification.
    question: Does grouping affect the underlying XML?
  - answer: 'There is no direct “ungroup” API, but you can iterate through the child
      shapes of the group (`group.GroupShape.Children`) and copy them out to the document
      body. ## Next steps Now that you know **how to group shapes**, consider exploring
      these related topics: - **Apply complex formatting to grouped '
    question: What if I need to ungroup later?
  type: FAQPage
tags:
- Aspose.Words
- C#
- shapes
- document automation
title: Cara mengelompokkan bentuk di C# dengan Aspose.Words
url: /id/net/programming-with-shapes/how-to-group-shapes-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengelompokkan bentuk di C# dengan Aspose.Words

Jika Anda perlu **how to group shapes** dalam dokumen Word secara programatis, tutorial ini menunjukkan langkah‑langkah tepat menggunakan Aspose.Words untuk .NET. Baik Anda sedang membangun generator laporan, mesin templat, atau alat diagram, Anda akan belajar cara memulai grup, menyisipkan bentuk persegi panjang, dan menambahkan konten **add shapes word**‑level pada bentuk tanpa meninggalkan kode Anda.

Anda juga akan melihat cara **group multiple shapes** bersama‑sama, yang penting ketika Anda ingin memindahkan, memutar, atau memberi gaya pada kumpulan objek sebagai satu entitas. Contoh di bawah ini bekerja dengan rilis terbaru Aspose.Words 24.x dan memerlukan .NET 6 atau yang lebih baru.

## Prasyarat

- .NET 6 SDK (atau versi .NET apa pun yang didukung oleh Aspose.Words)
- Visual Studio 2022 atau VS Code
- Paket NuGet Aspose.Words untuk .NET (`Install-Package Aspose.Words`)
- Familiaritas dasar dengan C# dan model objek Aspose.Words

> **Pro tip:** Gunakan lisensi evaluasi gratis dari Aspose untuk menghindari batasan watermark saat pengujian.

## Cara mengelompokkan bentuk dengan Aspose.Words

Berikut ini program lengkap yang dapat dijalankan yang menunjukkan **how to start group**, menambahkan persegi panjang, dan menyelesaikan grup. Kode ini mengikuti alur logika yang sama seperti potongan kode yang Anda berikan, tetapi menambahkan konteks, penanganan kesalahan, dan komentar untuk kejelasan.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Get a DocumentBuilder to insert content.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Start a group shape – all shapes added after this call belong to the group.
            // This is the “how to start group” step.
            Shape group = builder.StartGroupShape();

            // 4️⃣ Insert individual shapes inside the group.
            //    a) Insert a rectangle shape (demonstrates “insert rectangle shape”).
            builder.InsertShape(ShapeType.Rectangle, 150, 80);
            //    b) Insert a simple ellipse for visual variety.
            builder.InsertShape(ShapeType.Ellipse, 100, 60);
            //    c) Add a WordArt‑style text shape – shows “add shapes word”.
            builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            builder.Writeln("Grouped Text"); // adds text inside the last shape

            // 5️⃣ Close the group shape to finalize the grouping.
            builder.EndGroupShape();

            // Optional: Save the document to verify the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Mengapa setiap langkah penting

| Step | Purpose | How it relates to the keywords |
|------|---------|--------------------------------|
| **Buat dokumen kosong baru** | Menyediakan kanvas bersih untuk operasi bentuk. | Menyiapkan panggung untuk **add shapes word** nanti. |
| **Inisialisasi DocumentBuilder** | Builder adalah API utama untuk menyisipkan objek. | Diperlukan sebelum Anda dapat **how to start group**. |
| **StartGroupShape** | Memulai wadah logis; semua bentuk berikut menjadi anggota grup ini. | Langsung menjawab **how to start group**. |
| **InsertShape** (rectangle, ellipse, text) | Menempatkan bentuk individu di dalam grup. Pemanggilan persegi panjang memenuhi **insert rectangle shape**; bentuk teks memenuhi **add shapes word**. | Menunjukkan **group multiple shapes**. |
| **EndGroupShape** | Menyelesaikan grup sehingga Anda dapat memindahkan atau memberi gaya sebagai satu unit. | Menyelesaikan alur kerja **how to group shapes**. |

## Menyisipkan bentuk persegi panjang – penjelasan mendalam

Metode `InsertShape` menerima enum `ShapeType`, lebar, dan tinggi. Untuk **insert rectangle shape** dengan gaya khusus, Anda dapat memperluas contoh berikut:

```csharp
// Insert a styled rectangle
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rect.FillColor = System.Drawing.Color.LightBlue;
rect.StrokeColor = System.Drawing.Color.DarkBlue;
rect.LineWidth = 2.0;
```

> **Why style it?** Styling memastikan persegi panjang menonjol ketika grup dipindahkan kembali nanti. Ini juga menunjukkan bahwa properti bentuk dapat diatur *sebelum* grup ditutup.

## Menambahkan bentuk tingkat‑Word (add shapes word)

Jika Anda perlu menyematkan teks langsung di dalam bentuk—biasanya disebut “WordArt” atau “text box”—gunakan `ShapeType.TextPlainText`. Setelah menyisipkan, Anda dapat menulis teks ke dalam bentuk dengan `DocumentBuilder.Writeln` atau dengan mengakses properti `TextBox` pada bentuk:

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextPlainText, 250, 50);
textBox.TextBox.Text = "Hello, grouped world!";
```

Ini memenuhi kata kunci **add shapes word** dan menunjukkan bagaimana teks dapat bergerak bersama grup.

## Mengelompokkan beberapa bentuk – skenario praktis

Ketika Anda **group multiple shapes**, Anda dapat memperlakukan mereka seperti satu objek untuk penempatan, rotasi, atau skala. Misalnya, setelah grup ditutup, Anda dapat memindahkan seluruh grup:

```csharp
// Move the entire group 100 points to the right and 50 points down.
group.Left += 100;
group.Top += 50;
```

Atau memutar grup:

```csharp
group.Rotation = 45; // degrees
```

Operasi ini hanya mungkin karena bentuk‑bentuk tersebut berbagi grup induk yang sama.

## Menangani kasus tepi

1. **Nested groups** – Aspose.Words memungkinkan grup di dalam grup. Untuk membuat grup bersarang, panggil `StartGroupShape` lagi sebelum memanggil `EndGroupShape` untuk grup internal.  
2. **Empty groups** – Jika Anda memulai grup tetapi tidak pernah menyisipkan bentuk, `EndGroupShape` tetap akan membuat wadah kosong. Ini tidak berbahaya tetapi dapat sedikit meningkatkan ukuran file.  
3. **Compatibility** – DOCX yang dihasilkan bekerja dengan Word 2010 dan versi lebih baru. Versi lama mungkin mengabaikan metadata pengelompokan, jadi selalu uji dengan versi Word target.

## File sumber lengkap untuk referensi

Simpan berikut ini sebagai `Program.cs` dalam proyek konsol .NET. Kode ini dapat dikompilasi dan dijalankan tanpa modifikasi.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document.
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Start the group – “how to start group”.
            Shape group = builder.StartGroupShape();

            // Step 4a: Insert a rectangle – “insert rectangle shape”.
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);
            rect.FillColor = System.Drawing.Color.LightCoral;
            rect.StrokeColor = System.Drawing.Color.DarkRed;
            rect.LineWidth = 1.5;

            // Step 4b: Insert an ellipse (additional shape for grouping).
            builder.InsertShape(ShapeType.Ellipse, 100, 60);

            // Step 4c: Add a text box – “add shapes word”.
            Shape txt = builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            txt.TextBox.Text = "Grouped Text";

            // Step 5: End the group – completes “how to group shapes”.
            builder.EndGroupShape();

            // Optional: Adjust group position.
            group.Left += 50;
            group.Top += 30;

            // Save the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Output yang diharapkan

Membuka `GroupedShapes.docx` di Microsoft Word akan menampilkan:

- Sebuah persegi panjang berwarna coral muda, sebuah elips, dan sebuah kotak teks—semua terikat secara visual bersama.  
- Memilih bagian mana pun dari grup juga akan memilih seluruh grup (sebuah kotak pembatas tunggal muncul).  
- Memindahkan atau memutar grup akan memindahkan ketiga bentuk secara bersamaan.

## Pertanyaan yang sering diajukan

**Q: Bisakah saya mengelompokkan bentuk yang sudah ada dalam dokumen?**  
A: Ya. Ambil objek `Shape` yang ada, panggil `builder.StartGroupShape()`, sisipkan kembali mereka dengan `builder.InsertShape(existingShape)`, lalu panggil `EndGroupShape()`.

**Q: Apakah pengelompokan memengaruhi XML yang mendasarinya?**  
A: Aspose.Words menambahkan elemen `<w:grpSp>` yang berisi setiap node `<w:sp>` bentuk. Ini sepenuhnya sesuai dengan spesifikasi Office Open XML.

**Q: Bagaimana jika saya perlu membatalkan pengelompokan nanti?**  
A: Tidak ada API “ungroup” langsung, tetapi Anda dapat mengiterasi bentuk anak dari grup (`group.GroupShape.Children`) dan menyalinnya ke badan dokumen.

## Langkah selanjutnya

Sekarang Anda sudah mengetahui **how to group shapes**, pertimbangkan untuk menjelajahi topik terkait berikut:

- **Apply complex formatting to grouped shapes** – pelajari cara mengatur isian gradien, efek bayangan, dan gaya garis.  
- **Export grouped shapes as images** – gunakan `Shape.GetShapeRenderer().Save(...)` untuk merasterkan grup.  
- **Create dynamic diagrams** – gabungkan penempatan berbasis data dengan pengelompokan untuk menghasilkan diagram alur secara otomatis.

Setiap hal ini dibangun di atas fondasi yang dibahas di sini dan akan membantu Anda membuat dokumen Word yang lebih kaya dan interaktif.

---

*Selamat coding! Jika Anda menemukan panduan ini berguna, bagikan kepada rekan tim atau beri bintang pada repositori yang berisi proyek contoh.*

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Menyisipkan Bentuk dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Membuat Bentuk Grup dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Membuat Bentuk Persegi Panjang di Word dengan Aspose.Words – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}