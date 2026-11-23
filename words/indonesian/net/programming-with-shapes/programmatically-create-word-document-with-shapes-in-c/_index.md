---
category: general
date: 2026-11-22
description: Membuat dokumen Word secara programatis di C# dan menyisipkan bentuk
  persegi panjang, menyisipkan beberapa bentuk, serta menulis bentuk ke Word menggunakan
  Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- insert rectangle shape
- insert multiple shapes
- write shapes to word
language: id
lastmod: 2026-11-22
og_description: Membuat dokumen Word secara programatis di C# dengan menyisipkan bentuk
  persegi panjang, menyisipkan beberapa bentuk, dan menulis bentuk ke Word menggunakan
  Aspose.Words.
og_image_alt: Screenshot of a Word document showing a rectangle and an ellipse grouped
  together
og_title: Membuat dokumen Word dengan bentuk secara programatis di C#
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  headline: Programmatically create Word document with shapes in C#
  type: TechArticle
- description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  name: Programmatically create Word document with shapes in C#
  steps:
  - name: '**Initialize** a new `Document` and a `DocumentBuilder`.'
    text: '**Initialize** a new `Document` and a `DocumentBuilder`.'
  - name: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
    text: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
  - name: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
    text: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Membuat dokumen Word dengan bentuk secara programatis di C#
url: /id/net/programming-with-shapes/programmatically-create-word-document-with-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat Dokumen Word Secara Programatis dengan Bentuk di C#

Jika Anda perlu **membuat dokumen Word secara programatis** yang berisi grafik khusus, panduan ini menunjukkan cara melakukannya dengan Aspose.Words untuk .NET. Anda akan belajar menyisipkan bentuk persegi panjang, menambahkan bentuk tambahan, mengelompokkannya, dan akhirnya menulis bentuk-bentuk tersebut ke Word—semua dalam beberapa baris kode C#.

Membuat file Word dengan grafik tidak lagi memerlukan penyuntingan manual atau skrip makro. Pada akhir tutorial ini Anda akan memiliki metode yang dapat digunakan kembali yang menghasilkan file `.docx` berisi persegi panjang dan elips yang dikelompokkan bersama, siap untuk pemrosesan lanjutan atau pelaporan.

## Apa yang Anda butuhkan

- .NET 6.0 atau lebih baru (kode juga bekerja dengan .NET Framework 4.6+)
- Aspose.Words untuk .NET (paket NuGet `Aspose.Words`)
- IDE seperti Visual Studio 2022 (editor apa pun yang dapat mengkompilasi C# juga dapat digunakan)

> **Tip Pro:** Instal paket dengan perintah CLI `dotnet add package Aspose.Words` sebelum Anda mulai menulis kode.

## Membuat Dokumen Word Secara Programatis – ikhtisar

Alur keseluruhan terdiri dari tiga fase logis:

1. **Inisialisasi** dokumen `Document` baru dan `DocumentBuilder`.  
2. **Sisipkan beberapa bentuk** (sebuah persegi panjang dan sebuah elips) dan tempatkan di dalam `GroupShape`.  
3. **Tulis bentuk ke Word** dengan menyimpan `Document` ke file `.docx`.

Setiap fase dibungkus dalam langkah khusus di bawah ini, sehingga Anda dapat menyalin‑tempel kode langsung ke proyek Anda.

![Programmatically create Word document with grouped shapes](grouped-shapes.png){: .align-center alt="Membuat dokumen Word secara programatis dengan bentuk yang dikelompokkan"}

## Langkah 1: Inisialisasi dokumen dan builder

Kelas `Document` mewakili seluruh file Word, sementara `DocumentBuilder` menyediakan API yang fluently untuk menambahkan konten.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document document = new Document();

// Initialize a DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Mengapa ini penting:* Membuat `Document` terlebih dahulu memberi Anda kanvas bersih. `DocumentBuilder` melacak titik sisipan saat ini, yang penting ketika Anda nanti melampirkan bentuk ke hierarki paragraf.

## Langkah 2: Sisipkan kontainer grup bentuk

`GroupShape` memungkinkan Anda memperlakukan beberapa bentuk individu sebagai satu unit. Ini berguna ketika Anda ingin memindahkan atau mengubah ukuran mereka secara bersamaan.

```csharp
// Insert a group shape container at the current cursor position
GroupShape groupShape = builder.InsertGroupShape();
```

*Penjelasan:* `InsertGroupShape` menyisipkan kontainer kosong dan secara otomatis menjadikannya bentuk saat ini. Semua penyisipan bentuk selanjutnya akan ditambahkan ke kontainer ini sampai Anda menutup grup.

## Sisipkan bentuk persegi panjang

Sekarang kita menambahkan grafik pertama—sebuah persegi panjang. Ini memenuhi persyaratan **menyisipkan bentuk persegi panjang**.

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Persegi panjang mewarisi konteks pemformatan grup, sehingga muncul di dalam `GroupShape`. Anda juga dapat mengatur warna garis, isi, atau teks nanti jika diperlukan.

## Sisipkan beberapa bentuk

Untuk mendemonstrasikan kemampuan **menyisipkan beberapa bentuk**, kami menambahkan sebuah elips tepat setelah persegi panjang. Anda dapat terus menambahkan sejumlah bentuk apa pun (mis., segitiga, bintang) sebelum menutup grup.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

Pada titik ini grup berisi dua bentuk yang berbeda: sebuah persegi panjang dan sebuah elips. Karena mereka berbagi induk yang sama, Anda dapat memindahkannya sebagai satu unit.

## Langkah 3: Lampirkan grup bentuk ke hierarki paragraf

Dokumen Word menyimpan konten dalam pohon paragraf. Untuk membuat grup terlihat dalam file akhir, kita harus melampirkannya ke paragraf saat ini.

```csharp
// Append the group shape to the current paragraph so it becomes part of the document flow
groupShape.AppendChild(builder.CurrentParagraph);
```

*Mengapa langkah ini diperlukan:* Tanpa menambahkan grup ke paragraf, bentuk-bentuk tersebut hanya ada di memori dan akan diabaikan saat dokumen disimpan.

## Langkah 4: Simpan dokumen – tulis bentuk ke Word

Akhirnya, kami menyimpan `Document` yang berada di memori ke disk. Ini memenuhi tujuan **menulis bentuk ke word**.

```csharp
// Define the output path (adjust the folder as needed)
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");

// Save the document in DOCX format
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Ketika Anda membuka `GroupShape.docx` di Microsoft Word, Anda akan melihat sebuah persegi panjang dan sebuah elips yang dikelompokkan bersama, persis seperti yang disisipkan oleh kode.

### Output yang Diharapkan

- File bernama **GroupShape.docx** yang terletak di folder output proyek.  
- Di dalam file Word: satu paragraf yang berisi persegi panjang yang dikelompokkan (100 pt × 50 pt) dan sebuah elips (80 pt × 40 pt). Memilih salah satu bentuk akan memilih seluruh grup.

## Menangani kasus tepi umum

| Situasi | Rekomendasi |
|-----------|----------------|
| **DPI atau ukuran halaman yang berbeda** | Secara eksplisit atur `builder.PageSetup.PaperSize` sebelum menyisipkan bentuk untuk menghindari skala yang tidak terduga. |
| **Perlu memposisikan bentuk secara tepat** | Gunakan `builder.MoveTo` untuk memindahkan titik sisipan, lalu atur properti `groupShape.Left` dan `groupShape.Top` (nilai dalam poin). |

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Dokumen Word – Sisipkan Bentuk Persegi Panjang & Bayangan dalam C#](/words/english/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/)
- [Buat dokumen word secara programatis dan kelompokkan bentuk dalam C#](/words/english/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/)
- [Buat dokumen Word secara programatis dengan grup bentuk](/words/english/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}