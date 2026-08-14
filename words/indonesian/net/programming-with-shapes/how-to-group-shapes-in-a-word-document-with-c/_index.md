---
category: general
date: 2026-08-14
description: Cara mengelompokkan bentuk di dokumen Word menggunakan C#. Pelajari cara
  membuat dokumen Word, menyisipkan bentuk persegi panjang, mengelompokkan bentuk
  di Word, dan menyimpan dokumen sebagai docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
language: id
lastmod: 2026-08-14
og_description: Cara mengelompokkan bentuk di dokumen Word menggunakan C#. Ikuti tutorial
  lengkap ini untuk membuat file Word, menyisipkan bentuk persegi panjang, mengelompokkan
  bentuk di Word, dan menyimpan hasilnya sebagai docx.
og_image_alt: Screenshot showing how to group shapes in a Word document using C#
og_title: Cara mengelompokkan bentuk dalam dokumen Word dengan C# – panduan langkah
  demi langkah
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  headline: How to group shapes in a Word document with C#
  type: TechArticle
- description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  name: How to group shapes in a Word document with C#
  steps:
  - name: Create a new blank document
    text: The first thing you do when you want to **create Word document** programmatically
      is instantiate a `Document` object. This object represents the entire .docx
      file in memory.
  - name: Insert a rectangle shape
    text: To demonstrate **insert rectangle shape**, we use the `InsertShape` method.
      The rectangle will act as the first member of the group.
  - name: Insert an ellipse shape
    text: Next, we **insert ellipse shape** (the API calls it `Ellipse`). This will
      be the second member of the group.
  - name: Group the rectangle and ellipse
    text: Now we answer the central question **how to group shapes** in a Word document.
      Aspose.Words provides `AppendGroupShape` to create a group container, and then
      you call `Group()` on that container.
  - name: Save the document as a DOCX file
    text: The final step is to **save document as docx**. You can choose any path
      you like; the example uses a placeholder `"YOUR_DIRECTORY"` that you should
      replace with a real folder.
  - name: Expected output
    text: When you open `groupedShapes.docx` in Microsoft Word, you will see a light‑blue
      rectangle and a light‑coral ellipse locked together. Clicking either shape selects
      both, allowing you to move or resize them as a single unit.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Cara mengelompokkan bentuk di dokumen Word dengan C#
url: /id/net/programming-with-shapes/how-to-group-shapes-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengelompokkan bentuk di dokumen Word dengan C#

Jika Anda perlu **cara mengelompokkan bentuk** dalam dokumen Word, panduan ini menunjukkan langkah‑langkah tepat menggunakan C# dan pustaka Aspose.Words. Anda akan melihat cara membuat dokumen Word, menyisipkan bentuk persegi panjang, mengelompokkan bentuk di Word, dan akhirnya **menyimpan dokumen sebagai docx**—semua dalam satu program yang dapat dijalankan.

Membuat dan memanipulasi bentuk adalah kebutuhan umum saat menghasilkan laporan, kontrak, atau brosur pemasaran secara programatis. Pada akhir tutorial ini Anda akan memiliki potongan kode yang dapat digunakan kembali dan dapat disisipkan ke proyek .NET mana pun.

## Prerequisites

Sebelum Anda memulai, pastikan Anda memiliki:

- .NET 6.0 atau yang lebih baru terpasang  
- Visual Studio 2022 (atau IDE apa pun yang mendukung .NET)  
- Lisensi Aspose.Words untuk .NET (atau percobaan gratis)  
- Pemahaman dasar tentang sintaks C#  

Tidak ada paket NuGet tambahan yang diperlukan selain `Aspose.Words`.

## Cara mengelompokkan bentuk di dokumen Word

Inti solusi adalah proses lima langkah. Setiap langkah dijelaskan secara detail, dan kode sumber lengkap disediakan di akhir artikel.

### Langkah 1: Buat dokumen kosong baru

Hal pertama yang Anda lakukan ketika ingin **membuat dokumen Word** secara programatis adalah menginstansiasi objek `Document`. Objek ini mewakili seluruh file .docx dalam memori.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Obtain a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Mengapa ini penting:** `DocumentBuilder` adalah pembantu tingkat tinggi yang memungkinkan Anda menyisipkan teks, tabel, dan bentuk tanpa harus menangani pohon node secara manual.

### Langkah 2: Sisipkan bentuk persegi panjang

Untuk mendemonstrasikan **menyisipkan bentuk persegi panjang**, kami menggunakan metode `InsertShape`. Persegi panjang akan berfungsi sebagai anggota pertama dari grup.

```csharp
// Insert a rectangle (100x50 points) at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Optional: set a fill color so the shape is visible
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

**Mengapa ini penting:** Bentuk diposisikan relatif terhadap titik sisipan. Menetapkan warna isi membantu Anda melihat bentuk ketika membuka dokumen yang dihasilkan.

### Langkah 3: Sisipkan bentuk elips

Selanjutnya, kami **menyisipkan bentuk elips** (API menyebutnya `Ellipse`). Ini akan menjadi anggota kedua dari grup.

```csharp
// Insert an ellipse (80x40 points) right after the rectangle
Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

**Mengapa ini penting:** Dengan menyisipkan elips segera setelah persegi panjang, kedua bentuk berada dalam paragraf yang sama, yang menyederhanakan pengelompokan nanti.

### Langkah 4: Kelompokkan persegi panjang dan elips

Sekarang kami menjawab pertanyaan utama **cara mengelompokkan bentuk** di dokumen Word. Aspose.Words menyediakan `AppendGroupShape` untuk membuat kontainer grup, lalu Anda memanggil `Group()` pada kontainer tersebut.

```csharp
// Get the first paragraph of the document (where the shapes live)
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;

// Create a group shape that contains the rectangle and ellipse
Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });

// Turn the container into a true group – the shapes will move and scale together
groupedShape.Group();
```

**Mengapa ini penting:** Setelah dikelompokkan, setiap transformasi (pindah, ubah ukuran, putar) yang diterapkan pada `groupedShape` secara otomatis memengaruhi baik persegi panjang maupun elips. Ini penting untuk menjaga konsistensi tata letak dalam dokumen yang dihasilkan.

### Langkah 5: Simpan dokumen sebagai file DOCX

Langkah terakhir adalah **menyimpan dokumen sebagai docx**. Anda dapat memilih jalur apa pun yang diinginkan; contoh menggunakan placeholder `"YOUR_DIRECTORY"` yang harus Anda ganti dengan folder yang sebenarnya.

```csharp
// Define the output path (ensure the directory exists)
string outputPath = @"C:\Temp\groupedShapes.docx";

// Save the document in DOCX format
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

**Mengapa ini penting:** Menyimpan sebagai DOCX mempertahankan metadata pengelompokan, sehingga ketika Anda membuka file di Microsoft Word Anda akan melihat persegi panjang dan elips berperilaku sebagai satu objek.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang menggabungkan semua lima langkah. Salin ke proyek konsol baru, pulihkan paket NuGet Aspose.Words, dan jalankan.

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
            // Step 1: Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a rectangle shape (100x50 points)
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangleShape.FillColor = System.Drawing.Color.LightBlue;

            // Step 3: Insert an ellipse shape (80x40 points)
            Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
            ellipseShape.FillColor = System.Drawing.Color.LightCoral;

            // Step 4: Group the rectangle and ellipse
            Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
            Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });
            groupedShape.Group();

            // Step 5: Save the document as DOCX
            string outputPath = @"C:\Temp\groupedShapes.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

### Output yang diharapkan

Saat Anda membuka `groupedShapes.docx` di Microsoft Word, Anda akan melihat persegi panjang berwarna biru muda dan elips berwarna merah muda yang terkunci bersama. Mengklik salah satu bentuk akan memilih keduanya, memungkinkan Anda memindahkan atau mengubah ukuran keduanya sebagai satu unit.

## Pertanyaan umum dan kasus tepi

| Pertanyaan | Jawaban |
|------------|---------|
| **Apakah saya dapat mengelompokkan lebih dari dua bentuk?** | Ya. Berikan sejumlah objek `Shape` apa pun ke `AppendGroupShape`. Metode ini menerima array, sehingga Anda dapat membangun koleksi secara dinamis. |
| **Bagaimana jika saya perlu grup terikat pada sel tabel?** | Sisipkan bentuk-bentuk di dalam paragraf sel, lalu panggil `AppendGroupShape` pada paragraf tersebut. Grup akan mewarisi penempatan sel. |
| **Apakah pengelompokan memengaruhi XML yang mendasarinya?** | Aspose.Words menulis elemen `<w:grpSp>` yang berisi bentuk anak. Word mengenali ini sebagai grup, mempertahankan posisi relatif. |
| **Bagaimana cara meng-ungrup nanti?** | Panggil `groupedShape.Ungroup()`; metode ini mengembalikan bentuk‑bentuk individual sehingga Anda dapat memanipulasinya secara terpisah. |
| **Apakah ada dampak kinerja saat mengelompokkan banyak bentuk?** | Pengelompokan itu sendiri tidak mahal, tetapi merender grup yang sangat besar (ratusan bentuk) dapat meningkatkan ukuran file. Pertimbangkan untuk meratakan gambar jika ukuran menjadi masalah. |

## Tips profesional

- **Atur posisi eksplisit** (`Left`, `Top`) jika Anda memerlukan penyelarasan tepat sebelum mengelompokkan.  
- **Gunakan `Shape.WrapType = WrapType.Inline`** ketika Anda ingin grup berperilaku seperti elemen paragraf bukan objek mengambang.  
- **Terapkan gaya garis** pada grup (`groupedShape.LineFormat`) untuk memberi seluruh koleksi border.  
- **Gunakan kembali grup**: setelah memanggil `Group()`, Anda dapat mengkloning `groupedShape` dan menyisipkan klon tersebut di tempat lain dalam dokumen.

## Langkah selanjutnya

Sekarang Anda sudah mengetahui **cara mengelompokkan bentuk** di dokumen Word, Anda dapat menjelajahi topik terkait seperti:

- **Sisipkan bentuk persegi panjang** dengan teks atau gambar khusus di dalam bentuk.  
- **Buat diagram kompleks** dengan menumpuk grup (grup dalam grup).  
- **Ekspor dokumen sebagai PDF** sambil mempertahankan pengelompokan bentuk (`doc.Save("output.pdf", SaveFormat.Pdf)`).  

Masing‑masing ini dibangun di atas dasar yang sama yang dibahas di sini, sehingga Anda berada pada posisi yang tepat untuk memperluas toolkit otomatisasi Word Anda.

## Kesimpulan

Tutorial ini menunjukkan **cara mengelompokkan bentuk** di dokumen Word menggunakan C#. Anda telah belajar **membuat dokumen Word**, **menyisipkan bentuk persegi panjang**, **mengelompokkan bentuk di Word**, dan akhirnya **menyimpan dokumen sebagai docx**. Dengan contoh lengkap yang dapat dijalankan dan tips praktis yang diberikan, Anda dapat mengintegrasikan pengelompokan bentuk ke dalam alur kerja pembuatan dokumen apa pun. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait dan membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑per‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Group Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Sisipkan Bentuk dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Buat bentuk persegi panjang di Word menggunakan C# – Panduan Langkah‑per‑Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}