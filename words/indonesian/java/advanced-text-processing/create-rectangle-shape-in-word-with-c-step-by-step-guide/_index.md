---
category: general
date: 2026-03-04
description: Pelajari cara membuat bentuk persegi panjang, menambahkan bayangan pada
  bentuk, dan menerapkan efek bayangan dalam dokumen Word, kemudian menyimpan dokumen
  Word secara otomatis.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- save word document
- create blank document
language: id
og_description: Buat bentuk persegi panjang, tambahkan bayangan ke bentuk, dan terapkan
  efek bayangan dalam dokumen Word menggunakan C#. Ikuti panduan ini untuk menyimpan
  dokumen Word dengan mudah.
og_title: Buat bentuk persegi panjang di Word – Tutorial C# Lengkap
tags:
- C#
- Aspose.Words
- Document Automation
title: Create rectangle shape in Word with C# – Step‑by‑Step Guide
url: /id/java/advanced-text-processing/create-rectangle-shape-in-word-with-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat bentuk persegi panjang di Word dengan C# – Tutorial Pemrograman Lengkap

Pernah membutuhkan untuk **create rectangle shape** dalam file Word tetapi tidak yakin harus mulai dari mana? Anda tidak sendirian—banyak pengembang mengalami kebingungan yang sama saat pertama kali menyelam ke pembuatan dokumen secara programatik. Kabar baiknya, dengan beberapa baris C# Anda dapat menyisipkan sebuah persegi panjang, **add shadow to shape**, dan **apply shadow effect** tanpa pernah membuka Word secara manual. Dalam panduan ini kami akan membahas seluruh proses, mulai dari **create blank document** yang baru hingga menyimpan **save word document** akhir ke disk.

Kami akan membahas semua yang Anda perlukan: paket NuGet yang diperlukan, API yang tepat, mengapa setiap properti penting, dan beberapa tips untuk menghindari jebakan paling umum. Pada akhir tutorial, Anda akan memiliki contoh yang dapat dijalankan sepenuhnya yang dapat Anda masukkan ke dalam proyek .NET apa pun.

## Prasyarat

- .NET 6.0 atau lebih baru (kode ini juga bekerja dengan .NET Framework 4.7+)
- Visual Studio 2022 atau IDE apa pun yang Anda sukai
- **Aspose.Words for .NET** terinstal via NuGet (`Install-Package Aspose.Words`)
- Familiaritas dasar dengan sintaks C#

Tidak diperlukan pustaka interop Word tambahan—Aspose.Words menangani semuanya di memori.

## Langkah 1 – Create a blank document

Hal pertama yang kami lakukan adalah **create blank document**. Anggaplah itu sebagai kanvas kosong tempat kami nanti akan **create rectangle shape**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a new blank document
Document doc = new Document();   // This gives us a fresh Word file
```

> **Why this matters:** Memulai dengan objek `Document` yang bersih menjamin bahwa tidak ada gaya atau bagian tersembunyi yang mengganggu penempatan shape nantinya.

## Langkah 2 – Insert a rectangle shape into the document

Sekarang kami benar‑benar **create rectangle shape**. Kami akan mengatur ukuran, posisi, dan memberi tahu Word untuk tidak membungkus teks di sekitarnya.

```csharp
// Step 2: Add a rectangle shape
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 200;          // Width in points (1 point = 1/72 inch)
rectangle.Height = 100;         // Height in points
rectangle.WrapType = WrapType.None; // No text wrapping
```

> **Pro tip:** Jika Anda perlu persegi panjang berada di dalam sel tabel, ubah `WrapType` menjadi `WrapType.Inline`. Untuk kebanyakan laporan, `None` membuat shape mengambang di atas teks.

## Langkah 3 – Add shadow to shape and configure its appearance

Inilah tempat keajaiban terjadi: kami **add shadow to shape** dan **apply shadow effect**. Bayangan membuat persegi panjang lebih menonjol di halaman, terutama saat dicetak.

```csharp
// Step 3: Enable shadow and set its properties
rectangle.ShadowFormat.Visible = true;          // Turn on the shadow
rectangle.ShadowFormat.BlurRadius = 5.0;        // Softness of the shadow edge
rectangle.ShadowFormat.Transparency = 0.3;      // 30 % transparent
rectangle.ShadowFormat.OffsetX = 8;             // Horizontal shift
rectangle.ShadowFormat.OffsetY = 8;             // Vertical shift
rectangle.ShadowFormat.Color = Color.Blue;     // Shadow colour
```

> **Why these values?**  
> - **BlurRadius** mengontrol seberapa kabur tepi terlihat; nilai sekitar `5` memberikan tampilan halus dan profesional.  
> - **Transparency** memungkinkan teks di bawah tetap dapat dibaca.  
> - **OffsetX/Y** memindahkan bayangan menjauh dari shape, menciptakan kedalaman.  
> - Menggunakan warna **blue** hanya contoh—semua `System.Drawing.Color` dapat digunakan.

## Langkah 4 – Add the configured shape to the document body

Dengan persegi panjang yang sudah sepenuhnya diatur, kami kini **add rectangle shape** ke bagian pertama dokumen. Langkah ini benar‑benar menempatkan shape ke dalam file.

```csharp
// Step 4: Append the shape to the first section's body
doc.FirstSection.Body.AppendChild(rectangle);
```

> **Edge case:** Jika dokumen Anda sudah berisi beberapa bagian, Anda mungkin ingin menargetkan bagian tertentu (`doc.Sections[2]` misalnya). Kode di atas bekerja untuk dokumen satu‑bagian, yang umum untuk laporan cepat.

## Langkah 5 – Save the Word document

Akhirnya, kami **save word document** ke disk. File tersebut akan berisi persegi panjang dengan bayangannya, siap dibuka di Microsoft Word.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\shadowed_rectangle.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Tip:** Gunakan `doc.Save(outputPath, SaveFormat.Docx)` jika Anda perlu menyatakan format secara eksplisit. Metode `Save` secara otomatis mendeteksi ekstensi, tetapi menyatakan secara eksplisit dapat menghindari kebingungan ketika path dihasilkan secara programatik.

## Contoh Lengkap yang Dapat Dijalankan

Di bawah ini adalah program lengkap yang dapat Anda salin‑tempel ke aplikasi konsol. Program ini mencakup semua pernyataan `using` dan metode `Main`, sehingga Anda dapat langsung menjalankannya.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document
            Document doc = new Document();

            // 2️⃣ Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 200;
            rectangle.Height = 100;
            rectangle.WrapType = WrapType.None;

            // 3️⃣ Apply shadow effect
            rectangle.ShadowFormat.Visible = true;
            rectangle.ShadowFormat.BlurRadius = 5.0;
            rectangle.ShadowFormat.Transparency = 0.3;
            rectangle.ShadowFormat.OffsetX = 8;
            rectangle.ShadowFormat.OffsetY = 8;
            rectangle.ShadowFormat.Color = Color.Blue;

            // 4️⃣ Insert the shape into the document body
            doc.FirstSection.Body.AppendChild(rectangle);

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\shadowed_rectangle.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document saved at {outputPath}");
        }
    }
}
```

### Hasil yang Diharapkan

Saat Anda membuka *shadowed_rectangle.docx* di Microsoft Word, Anda akan melihat sebuah persegi panjang berpinggiran biru mengambang di dekat bagian atas halaman pertama, dengan bayangan biru lembut yang bergeser 8 pt ke kanan dan bawah. Tidak ada teks tambahan di sekitarnya karena kami mengatur `WrapType.None`.

## Pertanyaan yang Sering Diajukan & Variasi

| Question | Answer |
|----------|--------|
| **Bisakah saya mengubah shape menjadi ellipse?** | Ya—ganti `ShapeType.Rectangle` dengan `ShapeType.Ellipse`. Semua properti bayangan tetap sama. |
| **Bagaimana jika saya membutuhkan banyak shape?** | Cukup ulangi Langkah 2‑4 untuk setiap instance `Shape` baru, sesuaikan `OffsetX/Y` atau `Left/Top` agar tidak tumpang tindih. |
| **Apakah ada cara agar warna bayangan cocok dengan isi shape?** | Tentu saja. Atur `rectangle.FillColor` terlebih dahulu, kemudian tetapkan `rectangle.ShadowFormat.Color = rectangle.FillColor;`. |
| **Bagaimana cara menyisipkan shape ke dalam sel tabel?** | Gunakan `cell.FirstParagraph.AppendChild(rectangle);` setelah menemukan objek `Cell` yang diinginkan. |
| **Apakah ini akan bekerja di .NET Core?** | Ya—Aspose.Words bersifat lintas‑platform. Pastikan Anda merujuk pada versi paket NuGet yang sesuai untuk .NET Core/5/6. |

## Kesalahan Umum & Tips Profesional

- **Pitfall:** Lupa mengatur `ShadowFormat.Visible = true`. Properti bayangan akan diabaikan secara diam‑diam.  
  **Fix:** Selalu aktifkan visibilitas sebelum mengubah parameter bayangan lainnya.

- **Pitfall:** Menggunakan `BlurRadius` yang sangat besar (mis., 20) dapat membuat bayangan tampak kabur dan tidak profesional.  
  **Fix:** Tetap gunakan nilai antara `3` dan `8` untuk kebanyakan dokumen bisnis.

- **Pro tip:** Jika Anda membutuhkan shape dapat dipilih nanti (mis., untuk penyuntingan oleh pengguna akhir), hindari mengatur `WrapType.Inline`. Shape mengambang (`WrapType.None`) lebih mudah dipindahkan secara programatik.

- **Pro tip:** Saat menghasilkan banyak dokumen dalam loop, gunakan kembali satu instance `Document` dan panggil `doc.Clone(true)` untuk setiap iterasi guna meningkatkan kinerja.

## Topik Terkait yang Mungkin Anda Jelajahi Selanjutnya

- **Add text inside a rectangle shape** – pelajari cara menggunakan `Shape.TextPath` untuk label.  
- **Create complex diagrams** – gabungkan beberapa shape, konektor, dan pengelompokan.  
- **Export to PDF** – konversi dokumen yang sama ke PDF dengan satu perintah `doc.Save("output.pdf")`.  
- **Apply different fill styles** – gradien, tekstur, atau bahkan gambar di dalam shape.

## Kesimpulan

Kami baru saja **create rectangle shape**, **add shadow to shape**, dan **apply shadow effect** dalam file Word menggunakan C#. Dengan mengikuti lima langkah singkat ini, Anda kini memiliki pola yang dapat digunakan kembali untuk skenario otomatisasi dokumen apa pun, dan Anda tahu cara **save word document** secara andal. Jangan ragu untuk menyesuaikan dimensi, warna, atau bahkan mengganti persegi panjang dengan geometri lain—Aspose.Words membuat semuanya mudah.

Jika Anda menemukan tutorial ini bermanfaat, beri bintang di GitHub, atau bagikan variasi Anda sendiri di komentar. Selamat coding, dan semoga dokumen Anda selalu tampak sehalus persegi panjang berbayang ini!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}