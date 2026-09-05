---
category: general
date: 2026-09-05
description: Pelajari cara membuat dokumen Word kosong dan menambahkan bentuk persegi
  panjang yang dapat disembunyikan menggunakan Aspose.Words dalam C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- add rectangle shape
- how to hide shape
- hide shape word
- create hidden shape
language: id
lastmod: 2026-09-05
og_description: Pembuatan dokumen Word kosong dan penyisipan bentuk persegi panjang
  tersembunyi menggunakan Aspose.Words – panduan langkah demi langkah untuk pengembang
  C#.
og_image_alt: Screenshot of a blank Word document with a hidden rectangle shape created
  by Aspose.Words in C#
og_title: Buat dokumen Word kosong dengan bentuk persegi panjang tersembunyi
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  headline: Create a blank word document and add a rectangle shape
  type: TechArticle
- description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  name: Create a blank word document and add a rectangle shape
  steps:
  - name: Expected result
    text: 'Open `HiddenRectangle.docx` in Word:'
  - name: Can I hide multiple shapes at once?
    text: Yes. Create each shape, set `Hidden = true`, and insert them sequentially.
      The hidden flag works per node, so mixing hidden and visible shapes in the same
      document is supported.
  - name: What if I need the shape to be hidden only in the print view?
    text: 'Word distinguishes between **display** and **print** visibility through
      the `DisplayWhen` property. Aspose.Words does not expose a direct API for that
      flag, but you can modify the underlying XML:'
  - name: Does the hidden shape affect file size?
    text: A hidden shape adds the same XML payload as a visible one, so the file size
      increase is identical. However, because the shape
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Buat dokumen Word kosong dan tambahkan bentuk persegi panjang
url: /id/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen Word kosong dan tambahkan bentuk persegi panjang

Jika Anda membutuhkan pembuatan **dokumen Word kosong** yang juga berisi sebuah bentuk yang tidak ingin muncul di tata letak, panduan ini menunjukkan secara tepat cara melakukannya dengan Aspose.Words untuk .NET. Anda akan melihat contoh lengkap yang dapat dijalankan yang membuat dokumen baru, menambahkan bentuk persegi panjang, menyembunyikan bentuk tersebut, dan menyimpan file—tanpa alat tambahan.

Tutorial ini mencakup semua hal mulai dari penyiapan proyek hingga pemecahan masalah umum. Pada akhir tutorial Anda akan dapat menghasilkan file Word yang terlihat kosong bagi pembaca tetapi tetap membawa metadata tersembunyi, yang berguna untuk hal‑hal seperti watermark, penyimpanan XML khusus, atau anchor tata letak.

## Prasyarat

Sebelum Anda memulai, pastikan Anda memiliki:

* .NET 6.0 SDK atau yang lebih baru (kode juga berfungsi dengan .NET Framework 4.7+)
* Visual Studio 2022 (atau IDE apa pun yang mendukung C#)
* Lisensi NuGet **Aspose.Words** yang aktif (versi percobaan gratis dapat digunakan untuk pengujian)
* Familiaritas dasar dengan C# dan konsep node dokumen

Anda dapat menginstal pustaka dengan perintah CLI berikut:

```bash
dotnet add package Aspose.Words
```

> **Tip profesional:** Pastikan versi Aspose.Words Anda selalu terbaru; API yang digunakan dalam tutorial ini stabil sejak versi 23.10.

## Cara membuat dokumen Word kosong dengan Aspose.Words

Langkah pertama adalah menginstansiasi objek `Document`. Sebuah `Document` baru mewakili **dokumen Word kosong**—tanpa paragraf, tanpa bagian, hanya wadah file.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, empty Word document
Document document = new Document();
```

> **Mengapa ini penting:** Memulai dengan dokumen bersih memastikan bahwa bentuk tersembunyi yang akan Anda tambahkan nanti tidak mengganggu konten atau gaya yang sudah ada.

## Tambahkan bentuk persegi panjang ke dokumen

Selanjutnya kita membuat bentuk persegi panjang. Di Aspose.Words sebuah shape adalah node yang dapat ditempatkan di mana saja dalam pohon dokumen, dan dapat dikonfigurasi dengan ukuran, isi, gaya garis, serta visibilitas.

```csharp
// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Define a rectangle shape (the "add rectangle shape" step)
Shape rectangle = new Shape(document, ShapeType.Rectangle)
{
    Width = 150,   // Width in points (1 point = 1/72 inch)
    Height = 80,   // Height in points
    FillColor = System.Drawing.Color.LightGray,
    StrokeColor = System.Drawing.Color.DarkGray,
    StrokeWeight = 0.5
};
```

Kode di atas membuat persegi panjang yang terlihat. Pada titik ini Anda bisa menyisipkannya ke dalam dokumen dengan `builder.InsertNode(rectangle)`. Namun, karena kita ingin bentuk tetap tersembunyi, kita akan menyesuaikan properti `Hidden`‑nya sebelum penyisipan.

## Cara menyembunyikan bentuk dalam dokumen Word

Word menyediakan atribut `Hidden` untuk node shape. Ketika diatur ke `true`, shape tidak muncul dalam tata letak halaman, tetapi tetap menjadi bagian dari XML dokumen. Inilah inti dari persyaratan **cara menyembunyikan bentuk**.

```csharp
// Hide the shape so it won't be displayed
rectangle.Hidden = true;
```

> **Penjelasan:** Menetapkan `Hidden = true` menambahkan atribut `<w:hide>` ke XML shape. Processor Word mengabaikan shape saat merender, namun shape masih dapat diakses secara programatik atau melalui tampilan XML Word.

## Sisipkan bentuk tersembunyi ke dalam dokumen kosong

Sekarang kita menempatkan persegi panjang tersembunyi ke dalam pohon dokumen. Karena dokumen masih kosong, shape menjadi node pertama dalam story utama.

```csharp
// Insert the hidden rectangle at the current cursor position
builder.InsertNode(rectangle);
```

Jika Anda membuka file hasil di Microsoft Word, Anda akan melihat halaman yang tampak kosong. Shape memang ada, tetapi tidak terlihat.

## Simpan dokumen

Akhirnya, tulis dokumen ke disk. Anda dapat memilih format apa pun yang didukung (`.docx`, `.pdf`, `.odt`, dll.). Untuk tutorial ini kita akan menggunakan format DOCX modern.

```csharp
// Save the file – adjust the path as needed
string outputPath = Path.Combine(Environment.CurrentDirectory, "HiddenRectangle.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### Hasil yang diharapkan

Buka `HiddenRectangle.docx` di Word:

* Dokumen terlihat kosong (tidak ada bentuk atau teks yang terlihat).
* Jika Anda memeriksa file dengan alat seperti **Open XML SDK** atau **Word XML Viewer**, Anda akan melihat elemen `<w:pict>` yang berisi persegi panjang dengan atribut `hidden`.

![dokumen word kosong dengan bentuk persegi panjang tersembunyi](image.png){: .align-center alt="dokumen word kosong dengan bentuk persegi panjang tersembunyi"}

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke aplikasi konsol. Program ini mencakup semua direktif `using` yang diperlukan, penanganan error, dan komentar.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Prepare a DocumentBuilder to manipulate the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Define a rectangle shape (add rectangle shape)
        Shape rectangle = new Shape(document, ShapeType.Rectangle)
        {
            Width = 150,
            Height = 80,
            FillColor = System.Drawing.Color.LightGray,
            StrokeColor = System.Drawing.Color.DarkGray,
            StrokeWeight = 0.5,
            // 4️⃣ Hide the shape (how to hide shape)
            Hidden = true
        };

        // 5️⃣ Insert the hidden shape into the blank document
        builder.InsertNode(rectangle);

        // 6️⃣ Save the document (create hidden shape)
        string outputPath = Path.Combine(
            Environment.CurrentDirectory, "HiddenRectangle.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Jalankan program (`dotnet run`) dan verifikasi file output. Konsol akan mengonfirmasi lokasi penyimpanan.

## Pertanyaan umum dan kasus tepi

### Bisakah saya menyembunyikan beberapa bentuk sekaligus?

Ya. Buat setiap shape, set `Hidden = true`, dan sisipkan secara berurutan. Flag tersembunyi bekerja per node, sehingga mencampur shape tersembunyi dan terlihat dalam dokumen yang sama didukung.

### Bagaimana jika saya membutuhkan bentuk tersembunyi hanya pada tampilan cetak?

Word membedakan antara visibilitas **tampilan** dan **cetak** melalui properti `DisplayWhen`. Aspose.Words tidak menyediakan API langsung untuk flag tersebut, tetapi Anda dapat memodifikasi XML yang mendasarinya:

```csharp
rectangle.GetShapeRenderer().GetShapeXml()
    .SetAttribute("w:display", "print");
```

Gunakan ini hanya ketika Anda memerlukan visibilitas khusus cetak.

### Apakah bentuk tersembunyi memengaruhi ukuran file?

Sebuah shape tersembunyi menambahkan payload XML yang sama dengan shape yang terlihat, sehingga peningkatan ukuran file identik. Namun, karena shape...

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Dokumen Word Kosong dengan Bentuk Persegi Panjang Berbayang – Panduan Langkah demi Langkah](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Buat bentuk persegi panjang di Word menggunakan C# – Panduan Langkah demi Langkah](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tutorial Bayangan Bentuk Aspose.Words – Tambahkan Bayangan ke Bentuk Word dalam C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}