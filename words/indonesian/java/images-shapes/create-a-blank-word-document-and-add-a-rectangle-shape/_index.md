---
category: general
date: 2026-10-23
description: Buat dokumen Word kosong, tambahkan bentuk persegi panjang, dan sembunyikan
  bentuk tersebut di Word menggunakan Aspose.Words. Kode langkah demi langkah untuk
  pengembang .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- how to insert shape
- hide shape word
language: id
lastmod: 2026-10-23
og_description: Buat dokumen Word kosong, tambahkan bentuk persegi panjang, dan sembunyikan
  bentuk tersebut di Word dengan Aspose.Words. Ikuti contoh lengkap C#.
og_image_alt: Screenshot of a Word document containing a hidden rectangle shape
og_title: Buat dokumen Word kosong dan tambahkan bentuk persegi panjang tersembunyi
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create a blank Word document, add a rectangle shape, and hide the shape
    in Word using Aspose.Words. Step‑by‑step code for .NET developers.
  headline: Create a blank Word document and add a rectangle shape
  type: TechArticle
tags:
- Aspose.Words
- .NET
- Word automation
title: Buat dokumen Word kosong dan tambahkan bentuk persegi panjang
url: /id/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen Word kosong dan tambahkan bentuk persegi panjang

Jika Anda perlu **membuat dokumen Word kosong**, panduan ini menunjukkan cara melakukannya dengan Aspose.Words for .NET. Anda juga akan belajar **cara menyisipkan bentuk**—khususnya sebuah persegi panjang—dan **menyembunyikan bentuk kata** sehingga tidak memengaruhi tata letak.

Tutorial ini menelusuri setiap baris kode, menjelaskan mengapa setiap langkah penting, dan mencakup jebakan umum seperti visibilitas bentuk tersembunyi dalam berbagai mode tampilan Word. Pada akhir tutorial, Anda akan memiliki file `.docx` yang berfungsi penuh yang berisi bentuk persegi panjang tersembunyi yang dapat Anda tampilkan kembali atau manipulasi secara programatis.

## Prasyarat

- .NET 6.0 atau lebih baru (kode ini juga bekerja dengan .NET Framework 4.6+)
- Paket NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Lingkungan pengembangan seperti Visual Studio 2022 atau VS Code dengan ekstensi C#
- Familiaritas dasar dengan sintaks C# dan konsep dokumen Word

Tidak diperlukan instalasi Office tambahan karena Aspose.Words berfungsi sepenuhnya di memori.

## Buat dokumen Word kosong

Langkah pertama adalah menginstansiasi objek `Document` yang kosong. Objek ini mewakili file Word yang belum berisi bagian, paragraf, atau konten apa pun.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

**Mengapa ini penting:**  
`Document` kosong memberi Anda kanvas bersih. Jika Anda memulai dari templat yang ada, bentuk tersembunyi dapat mewarisi gaya yang tidak diinginkan. Memulai dari awal memastikan bentuk persegi panjang yang Anda tambahkan nanti menjadi satu‑satunya konten yang Anda kendalikan.

## Tambahkan bentuk persegi panjang ke dokumen

Selanjutnya, kita memerlukan `DocumentBuilder` untuk menempatkan konten ke dalam dokumen. Metode `InsertShape` pada builder adalah cara standar **untuk menyisipkan bentuk** objek, seperti persegi panjang, lingkaran, atau gambar kustom.

```csharp
// Step 2: Initialize a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(document);

// Step 3: Insert a rectangle shape of size 200x100 points
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Mengapa ini penting:**  
`InsertShape` mengembalikan objek `Shape` yang dapat Anda konfigurasi lebih lanjut (warna, gaya garis, dll.). Dimensi diberikan dalam poin (1 poin = 1/72 inci), yang sesuai dengan sistem pengukuran internal Word.

### Opsional: gaya persegi panjang (opsional)

Jika Anda ingin persegi panjang memiliki batas yang terlihat saat Anda menampilkannya kembali, Anda dapat mengatur ketebalan garis dan warnanya:

```csharp
rectangleShape.LineWeight = 0.5;               // Thin border
rectangleShape.LineColor = System.Drawing.Color.Blue;
```

Baris-baris ini opsional karena bentuk akan disembunyikan pada langkah berikutnya.

## Sembunyikan bentuk di Word

Word memungkinkan bentuk disembunyikan dari tata letak sementara masih menjadi bagian dari model objek dokumen. Menetapkan properti `Hidden` ke `true` membuat bentuk tidak terlihat dalam tampilan normal tetapi masih dapat dipilih melalui API.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
rectangleShape.Hidden = true;
```

**Mengapa ini penting:**  
Bentuk tersembunyi berguna untuk menyimpan metadata, placeholder untuk pemrosesan selanjutnya, atau konten bersyarat yang Anda tampilkan hanya dalam keadaan tertentu (mis., saat menghasilkan laporan akhir). Bentuk tetap ada dalam file, sehingga Anda dapat secara programatis menampilkannya kembali nanti dengan `rectangleShape.Hidden = false;`.

## Simpan dokumen

Akhirnya, tulis dokumen ke disk. Ekstensi file menentukan format Word; `.docx` adalah format Open XML modern.

```csharp
// Step 5: Save the document with the hidden shape
string outputPath = @"C:\Temp\HiddenShape.docx";
document.Save(outputPath);
```

**Hasil:**  
Membuka `HiddenShape.docx` di Microsoft Word menampilkan halaman yang **kosong**. Persegi panjang tidak terlihat, tetapi jika Anda pergi ke **Home → Select → Selection Pane**, Anda akan melihat bentuk terdaftar dan dapat mengubah visibilitasnya.

## Contoh lengkap yang berfungsi

Berikut adalah program lengkap yang dapat Anda salin, tempel, dan jalankan. Program ini mencakup semua pernyataan `using` yang diperlukan serta komentar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for content insertion
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape (200x100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Optional styling (comment out if not needed)
        rectangleShape.LineWeight = 0.5;
        rectangleShape.LineColor = System.Drawing.Color.Blue;

        // Hide the shape so it does not appear in the layout
        rectangleShape.Hidden = true;

        // Save the document
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Output yang diharapkan:**  

- Konsol mencetak jalur penyimpanan.  
- `HiddenShape.docx` terbuka sebagai halaman kosong di Word.  
- Bentuk persegi panjang ada tetapi tersembunyi; Anda dapat memverifikasinya melalui *Selection Pane* atau dengan secara programatis mengatur `Hidden = false` dan membuka kembali file.

## Pertanyaan umum dan kasus tepi

| Question | Answer |
|----------|--------|
| **Bisakah saya menyembunyikan tipe bentuk lain?** | Ya. Setiap `Shape` (mis., `ShapeType.Ellipse`, `ShapeType.Picture`) mendukung properti `Hidden`. |
| **Apakah bentuk tersembunyi akan meningkatkan ukuran file?** | Peningkatannya dapat diabaikan (beberapa kilobyte) karena data bentuk disimpan sebagai XML dalam paket `.docx`. |
| **Bagaimana jika saya membutuhkan bentuk muncul hanya dalam tampilan cetak?** | Gunakan properti `Shape.IsPrint` alih-alih `Hidden`. Menetapkan `IsPrint = false` menyembunyikan bentuk dari output cetak tetapi tetap terlihat di layar. |
| **Bagaimana cara menampilkan kembali bentuk nanti?** | Muat dokumen, temukan bentuk (mis., dengan `Shape.Name`), lalu set `shape.Hidden = false;` dan simpan. |
| **Apakah ini bekerja dengan format .doc (biner)?** | Ya, Aspose.Words dapat menyimpan ke `.doc` menggunakan `document.Save("file.doc");`. Flag tersembunyi tetap dipertahankan. |

## Tips profesional

- **Berikan nama pada bentuk Anda**: `rectangleShape.Name = "PlaceholderRectangle";` memudahkan pencarian nanti melalui `document.GetChildNodes(NodeType.Shape, true).Cast<Shape>().FirstOrDefault(s => s.Name == "PlaceholderRectangle")`.
- **Pemrosesan batch**: Jika Anda perlu menambahkan bentuk tersembunyi ke banyak dokumen, bungkus kode dalam sebuah metode dan gunakan kembali instance `DocumentBuilder`.
- **Kinerja**: Membuat bentuk tidak memakan banyak sumber daya, tetapi menyimpan dokumen besar secara sering dapat menjadi bottleneck I/O. Pertimbangkan menggunakan `MemoryStream` untuk pemrosesan menengah.

## Kesimpulan

Anda kini tahu cara **membuat dokumen Word kosong**, **menambahkan bentuk persegi panjang**, dan **menyembunyikan bentuk kata** menggunakan Aspose.Words for .NET. Teknik ini memungkinkan Anda menyematkan placeholder tak terlihat yang dapat Anda tampilkan atau manipulasi nanti, sebuah pola yang berguna untuk pembuatan laporan dinamis, konten bersyarat, dan templating dokumen.

Langkah selanjutnya yang dapat Anda jelajahi:

- Ganti persegi panjang dengan gambar atau diagram menggunakan `ShapeType.Picture`.
- Gunakan **cara menyisipkan bentuk** di bagian header/footer untuk placeholder bergaya watermark.
- Gabungkan bentuk tersembunyi dengan validasi data berbasis **menambahkan bentuk persegi panjang** (mis., menyimpan JSON dalam properti `AlternativeText` bentuk).

Selamat coding, dan silakan bereksperimen dengan tipe bentuk lain serta opsi visibilitas untuk menyesuaikan kebutuhan otomatisasi dokumen Anda!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat dan membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Dokumen Word – Cara Menambahkan Bentuk Persegi Panjang dan Bayangan](/words/english/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/)
- [Buat Group Shape dalam Dokumen Word Menggunakan Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Buat Dokumen Word Kosong dengan Bentuk Elips Tersembunyi – Panduan C# Lengkap](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}