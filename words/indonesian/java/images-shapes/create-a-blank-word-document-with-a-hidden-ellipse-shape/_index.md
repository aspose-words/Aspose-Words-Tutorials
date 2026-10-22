---
category: general
date: 2026-09-18
description: Buat dokumen Word kosong dan sembunyikan bentuk elips menggunakan Aspose.Words.
  Pelajari cara menyembunyikan bentuk di Word, cara menyisipkan elips, dan membuat
  bentuk tersembunyi dengan cepat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to hide shape
- how to insert ellipse
- hide shape in word
- create hidden shape
language: id
lastmod: 2026-09-18
og_description: Buat dokumen Word kosong dan sembunyikan bentuk elips di Word. Panduan
  ini menunjukkan langkah demi langkah cara menyisipkan elips, menyembunyikan bentuk
  di Word, dan membuat bentuk tersembunyi dengan Aspose.Words.
og_image_alt: Screenshot of a blank Word document containing a hidden ellipse shape
  created with Aspose.Words
og_title: Buat dokumen Word kosong dengan bentuk elips tersembunyi
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  headline: Create a blank Word document with a hidden ellipse shape
  type: TechArticle
- description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  name: Create a blank Word document with a hidden ellipse shape
  steps:
  - name: Pro tip
    text: If you later need to make the shape visible again, simply set `ellipse.Hidden
      = false;` and save the document.
  - name: What if the shape still appears?
    text: '* Ensure you are using Aspose.Words 23.9 or later – older versions had
      a bug where `Hidden` was ignored for some shape types. * Verify that you are
      not applying any additional formatting (e.g., `WrapType`) that forces the shape
      to occupy layout space.'
  - name: Can I hide other shape types?
    text: Yes. The same `Hidden` property works for `ShapeType.Rectangle`, `ShapeType.Picture`,
      etc. Just replace `ShapeType.Ellipse` with the desired type.
  - name: How to list hidden shapes later?
    text: '```csharp foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
      { if (shape.Hidden) Console.WriteLine($"Hidden shape: {shape.ShapeType}"); }
      ```'
  - name: Next steps
    text: '* Explore **how to hide shape** conditionally based on document content.
      * Learn **how to unhide shape** when generating a final version of the document.
      * Combine hidden shapes with **custom document properties** to embed machine‑readable
      data.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Buat dokumen Word kosong dengan bentuk elips tersembunyi
url: /id/java/images-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen Word kosong dengan bentuk elips tersembunyi

Jika Anda perlu **create a blank Word document** yang berisi bentuk yang tidak ingin muncul di tata letak, panduan ini menunjukkan cara melakukannya secara tepat. Dengan menggunakan Aspose.Words untuk .NET Anda dapat secara programatis menyisipkan sebuah elips dan kemudian menyembunyikan bentuk tersebut sehingga dokumen tetap kosong secara visual sementara masih menyimpan data bentuk.

Dalam tutorial ini Anda akan belajar:

* cara **create blank Word document** objek,
* cara **insert ellipse** menggunakan `DocumentBuilder`,
* cara **hide shape in Word** sehingga tidak memengaruhi halaman,
* cara **create hidden shape** objek untuk pemrosesan selanjutnya.

Langkah‑langkah ini bekerja dengan .NET 6+ dan versi terbaru Aspose.Words (23.9 pada saat penulisan). Tidak diperlukan instalasi Office tambahan.

## Prasyarat

* Visual Studio 2022 (atau IDE C# apa saja)
* .NET 6 SDK atau yang lebih baru
* Paket NuGet Aspose.Words untuk .NET  
  ```bash
  dotnet add package Aspose.Words
  ```
* Pengetahuan dasar tentang C# dan konsep dokumen Word

## Langkah 1: Buat dokumen Word kosong

Hal pertama yang harus Anda lakukan adalah menginstansiasi objek `Document`. Objek ini mewakili file `.docx` kosong dan menjadi fondasi untuk semua operasi selanjutnya.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document doc = new Document();   // <-- creates a blank Word document in memory
```

Membuat **blank Word document** memberi Anda kanvas bersih – tanpa paragraf, tanpa bagian, hanya struktur paket di bawahnya. Ini adalah titik awal yang ideal ketika Anda hanya membutuhkan bentuk tersembunyi dan tidak ada hal lain.

## Langkah 2: Inisialisasi DocumentBuilder

`DocumentBuilder` menyediakan API yang nyaman untuk menambahkan konten ke `Document`. Ia berfungsi seperti kursor yang Anda gerakkan melalui dokumen.

```csharp
// Step 2: Initialise a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder secara otomatis membuat bagian pertama dan paragraf default, sehingga Anda dapat mulai menyisipkan bentuk tanpa harus menambahkan bagian secara manual.

## Langkah 3: Sisipkan bentuk elips

Sekarang kita **insert ellipse** menggunakan metode `InsertShape`. Metode ini menerima enumerasi `ShapeType`, lebar, dan tinggi (dalam poin).

```csharp
// Step 3: Insert an ellipse shape with a width of 100 points and a height of 50 points
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
```

Mengapa elips? Elips adalah bentuk vektor yang dapat disembunyikan tanpa memengaruhi aliran teks di sekitarnya. Lebar 100 pt dan tinggi 50 pt bersifat arbitrer; Anda dapat menyesuaikannya sesuai kebutuhan pemrosesan selanjutnya.

## Langkah 4: Sembunyikan bentuk agar tidak muncul di tata letak

Untuk **hide shape in Word**, setel properti `Hidden` pada objek `Shape` menjadi `true`. Saat dokumen dibuka di Microsoft Word, bentuk akan tidak terlihat dan tidak mengambil ruang dalam tata letak.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
ellipse.Hidden = true;   // <-- this hides the shape in Word
```

Flag `Hidden` disimpan dalam XML bentuk (`<w:hidden/>`). Word menghormati atribut ini selama proses rendering, itulah mengapa dokumen tampak sepenuhnya kosong meskipun bentuknya ada.

### Tips Pro

Jika Anda kemudian perlu membuat bentuk terlihat kembali, cukup setel `ellipse.Hidden = false;` dan simpan dokumen.

## Langkah 5: Simpan dokumen dengan bentuk tersembunyi

Akhirnya, persistenkan dokumen ke disk. File tersebut akan menjadi `.docx` biasa yang dapat dibuka oleh program pengolah Word apa pun.

```csharp
// Step 5: Save the document with the hidden shape
doc.Save(@"C:\Temp\HiddenEllipse.docx");
```

File yang disimpan, `HiddenEllipse.docx`, adalah **create blank word document** yang berisi elips tersembunyi. Membukanya di Microsoft Word menampilkan halaman kosong, tetapi bentuk masih ada dalam struktur Open XML.

## Contoh kerja lengkap

Berikut adalah program lengkap yang dapat Anda salin, tempel, dan jalankan.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();

            // 2️⃣ Initialise DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse shape (width: 100pt, height: 50pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the shape so it does not affect layout
            ellipse.Hidden = true;

            // 5️⃣ Save the result
            string outputPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Output yang diharapkan**

* Sebuah file bernama `HiddenEllipse.docx` muncul di `C:\Temp`.
* Membuka file di Microsoft Word menampilkan halaman yang sepenuhnya kosong.
* Jika Anda memeriksa dokumen dengan Open XML SDK atau penampil zip, Anda akan menemukan elemen `<w:shape>` dengan `<w:hidden/>` di dalam bagian dokumen.

## Pertanyaan umum dan kasus tepi

### Bagaimana jika bentuk masih muncul?

* Pastikan Anda menggunakan Aspose.Words 23.9 atau yang lebih baru – versi lama memiliki bug di mana `Hidden` diabaikan untuk beberapa tipe bentuk.
* Verifikasi bahwa Anda tidak menerapkan pemformatan tambahan (misalnya, `WrapType`) yang memaksa bentuk menempati ruang tata letak.

### Bisakah saya menyembunyikan tipe bentuk lain?

Ya. Properti `Hidden` yang sama berfungsi untuk `ShapeType.Rectangle`, `ShapeType.Picture`, dll. Cukup ganti `ShapeType.Ellipse` dengan tipe yang diinginkan.

### Bagaimana cara daftar bentuk tersembunyi nanti?

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.Hidden)
        Console.WriteLine($"Hidden shape: {shape.ShapeType}");
}
```

Potongan kode ini mengiterasi semua bentuk dan mencetak yang tersembunyi, yang berguna untuk alur kerja **create hidden shape** di mana Anda kemudian perlu memproses atau menampilkan kembali bentuk tersebut.

## Kesimpulan

Anda kini tahu cara **create a blank Word document**, **insert ellipse**, dan **hide shape in Word** untuk menghasilkan **create hidden shape** yang tetap tidak terlihat oleh pembaca. Teknik ini berguna untuk menyimpan metadata, bookmark, atau XML khusus dalam dokumen tanpa mengubah penampilan visualnya.

### Langkah selanjutnya

* Jelajahi **how to hide shape** secara kondisional berdasarkan konten dokumen.
* Pelajari **how to unhide shape** saat menghasilkan versi final dokumen.
* Gabungkan bentuk tersembunyi dengan **custom document properties** untuk menyematkan data yang dapat dibaca mesin.

Silakan bereksperimen dengan berbagai tipe bentuk, ukuran, dan logika status tersembunyi untuk menyesuaikan skenario otomatisasi Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait dan membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Dokumen Word Kosong dengan Bentuk Persegi Panjang Bayangan – Panduan Langkah demi Langkah](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Buat bentuk persegi panjang di Word dengan Aspose.Words – Panduan Langkah demi Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Buat Bentuk Grup dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}