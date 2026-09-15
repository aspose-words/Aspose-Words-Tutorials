---
category: general
date: 2025-12-29
description: Buat bentuk persegi panjang dalam dokumen Word menggunakan Aspose.Words
  C#. Pelajari cara mengatur transparansi bentuk, mengatur warna bayangan, dan menyimpan
  dokumen Word dengan mudah.
draft: false
keywords:
- create rectangle shape
- set shape transparency
- set shadow color
- save word document
- create word document
language: id
og_description: Buat bentuk persegi panjang dalam dokumen Word dengan Aspose.Words
  C#. Panduan ini menunjukkan cara mengatur transparansi bentuk, mengatur warna bayangan,
  dan menyimpan dokumen Word.
og_title: Buat bentuk persegi panjang di Word – Tutorial Lengkap Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Membuat bentuk persegi panjang di Word dengan Aspose.Words – Panduan langkah
  demi langkah
url: /id/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat bentuk persegi panjang di Word – Tutorial Lengkap Aspose.Words

Pernah membutuhkan untuk **create rectangle shape** dalam dokumen Word tetapi tidak yakin harus mulai dari mana? Anda tidak sendirian; banyak pengembang mengalami hal ini saat mengotomatiskan laporan atau faktur. Dalam panduan ini kami akan menjelaskan langkah‑langkah tepat untuk membuat bentuk persegi panjang, mengatur transparansi bentuk, mengatur warna bayangan, dan akhirnya **save word document** menggunakan Aspose.Words untuk .NET.  

Kami akan membahas semuanya mulai dari objek dokumen awal hingga file `.docx` akhir di disk, sehingga pada akhir Anda dapat **create word document** secara programatis tanpa menebak‑nebak. Tanpa refer eksternal, hanya solusi mandiri yang dapat Anda salin‑tempel ke dalam proyek Anda.

## Prasyarat

- .NET 6.0 atau lebih baru (kode juga berfungsi dengan .NET Framework 4.7+)
- Paket NuGet Aspose.Words untuk .NET (`Install-Package Aspose.Words`)
- Familiaritas dasar dengan sintaks C#
- IDE pilihan Anda (Visual Studio, Rider, VS Code, dll.)

> **Pro tip:** Jika Anda menggunakan percobaan gratis Aspose.Words, perpustakaan akan menambahkan watermark ke file output. Untuk produksi Anda memerlukan lisensi yang valid.

## Langkah 1: Inisialisasi Dokumen dan Builder

Hal pertama yang kami lakukan adalah membuat dokumen Word baru yang kosong dan `DocumentBuilder` yang memungkinkan kami menyisipkan konten. Anggap builder sebagai pena virtual yang menggambar di halaman.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();

// The builder provides methods to add text, tables, shapes, etc.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Why this matters:** Tanpa `DocumentBuilder` Anda harus memanipulasi pohon node tingkat‑rendah secara langsung, yang rawan kesalahan dan lebih sulit dibaca.

## Langkah 2: Membuat bentuk persegi panjang

Sekarang kami benar‑benar **create rectangle shape**. Metode `InsertShape` menerima enum `ShapeType`, lebar, dan tinggi (dalam poin). Objek `Shape` yang dikembalikan memungkinkan kami menyesuaikan properti visual nanti.

```csharp
// Insert a rectangle 150 pts wide and 80 pts tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Pada titik ini persegi panjang adalah kotak hitam padat yang terikat pada paragraf saat ini. Anda dapat memindahkannya, mengubah ukurannya, atau bahkan memutarnya nanti jika diperlukan.

![membuat bentuk persegi panjang dengan bayangan](/images/rectangle-shadow.png "Dokumen Word yang menampilkan bentuk persegi panjang dengan bayangan abu‑abu")

*Teks alt gambar: membuat bentuk persegi panjang dengan bayangan dalam dokumen Word*

## Langkah 3: Mengatur transparansi bentuk

Transparansi adalah tingkat “tembus pandang” dari isi bentuk. Aspose.Words menggunakan properti `Transparency` yang berkisar dari `0.0` (tidak tembus) hingga `1.0` (sepenuhnya tembus). Di sini kami **set shape transparency** ke 40 % sehingga teks di bawahnya tetap dapataca.

```csharp
// Make the rectangle 40 % transparent
rectangleShape.Fill.Transparency = 0.4; // 0.0 = opaque, 1.0 = invisible
```

> **Edge case:** Jika Anda membutuhkan bentuk yang sepenuhnya tidak terlihat tetapi masih menginginkan bayangan muncul, set `Transparency` ke `1.0` dan beri bentuk lebar outline yang tidak nol.

## Langkah 4: Mengonfigurasi bayangan

Bayangan drop yang halus menambah kedalaman. Kami akan **set shadow color** ke abu‑abu sedang, menyesuaikan radius blur‑nya, dan menggesernya beberapa poin baik secara horizontal maupun vertikal.

```csharp
// Enable the shadow effect
rectangleShape.Shadow.Enabled = true;

// Shadow color – a neutral gray
rectangleShape.Shadow.Color = System.Drawing.Color.Gray;

// 40 % transparent shadow (same as shape's fill)
rectangleShape.Shadow.Transparency = 0.4;

// Blur radius makes the edge softer
rectangleShape.Shadow.Blur = 6;

// Horizontal and vertical offsets (in points)
rectangleShape.Shadow.OffsetX = 5;
rectangleShape.Shadow.OffsetY = 5;
```

> **Why this matters:** Bayangan yang terlalu tajam atau terlalu gelap dapat terlihat seperti artefak pencetakan. Sesuaikan `Blur` dan `Transparency` sampai terasa alami.

## Langkah 5: Menyimpan dokumen Word

Akhirnya kami **save document** ke disk. Metode `Save` secara otomatis menentukan format file dari ekstensi; `.docx` adalah format OpenXML modern.

```csharp
// Save the document to the desired folder
document.Save(@"C:\Temp\ShadowRectangle.docx");
```

Jika folder tidak ada, Aspose.Words akan melempar `ArgumentException`. Pastikan jalur valid atau buat direktori terlebih dahulu.

## Contoh Lengkap yang Berfungsi

Berikut adalah program lengkap yang siap dijalankan yang menggabungkan semua langkah. Salin ini ke dalam proyek konsol baru dan tekan **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert rectangle shape
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Set shape transparency (40 % transparent)
            rectangleShape.Fill.Transparency = 0.4;

            // 4️⃣ Configure shadow (color, blur, offset, transparency)
            rectangleShape.Shadow.Enabled = true;
            rectangleShape.Shadow.Color = System.Drawing.Color.Gray;
            rectangleShape.Shadow.Transparency = 0.4;
            rectangleShape.Shadow.Blur = 6;
            rectangleShape.Shadow.OffsetX = 5;
            rectangleShape.Shadow.OffsetY = 5;

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\ShadowRectangle.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Hasil yang Diharapkan

Buka `ShadowRectangle.docx` di Microsoft Word. Anda akan melihat persegi panjang abu‑abu muda dengan bayangan lembut yang sedikit bergeser, keduanya dirender pada 40 % transparansi. Bentuk tersebut berada di halaman kosong, siap untuk konten tambahan.

## Pertanyaan Umum & Variasi

**Bagaimana jika saya membutuhkan bentuk lain?**  
Ganti `ShapeType.Rectangle` dengan nilai enum lain (`Ellipse`, `Triangle`, `Star`, dll.). Sisanya kode tetap sama.

**Apakah saya dapat mengubah warna outline?**  
Ya—gunakan `rectangleShape.StrokeColor = System.Drawing.Color.Blue;` dan opsional set `rectangleShape.StrokeWeight = 1.5;`.

**Bagaimana cara menempatkan bentuk pada lokasi tertentu di halaman?**  
Set `rectangleShape.WrapType = WrapType.None;` lalu sesuaikan properti `rectangleShape.Left` dan `rectangleShape.Top` (nilai dalam poin).

**Apakah memungkinkan menambahkan teks di dalam persegi panjang?**  
Tentu saja. Setelah membuat bentuk, Anda dapat memanggil `rectangleShape.AppendChild(new Paragraph(document))` dan kemudian menambahkan `Run` dengan teks Anda. Ingat untuk mengatur properti `rectangleShape.TextBox` jika Anda menginginkan pemformatan yang lebih kaya.

## Tips Pro & Jebakan

- **License early:** Jika Anda lupa menerapkan lisensi, Aspose.Words akan menyisipkan watermark pada halaman pertama, yang dapat membingungkan selama pengujian.
- **Performance tip:** Saat menghasilkan banyak dokumen dalam loop, gunakan kembali satu instance `Document` dan panggil `document.RemoveAllChildren();` setelah setiap penyimpanan untuk menghindari tekanan GC berlebih.
- **Shadow visibility:** Pada layar beresolusi rendah bayangan halus mungkin tampak tidak terlihat. Tingkatkan `Blur` atau `OffsetX/Y` untuk debugging, lalu kurangi kembali untuk produksi.

## Langkah Selanjutnya

Sekarang Anda tahu cara **create rectangle shape**, **set shape transparency**, **set shadow color**, dan **save word document**, pertimbangkan untuk memperluas tutorial:

- Tambahkan beberapa bentuk dan grupkan mereka.
- Sisipkan persegi panjang di dalam sel tabel untuk tata letak laporan.
- Gabungkan bentuk dengan `DocumentBuilder.InsertHtml` untuk menimpa konten bergaya HTML.
- Jelajahi efek visual lain seperti `Glow` atau `Reflection` untuk dokumen yang lebih kaya seperti UI.

Bereksperimen, pecahkan sesuatu, lalu perbaiki—generasi dokumen secara programatis adalah arena bermain di mana desain visual bertemu kode.

---

*Selamat coding! Jika Anda mengalami kendala, tinggalkan komentar di bawah dan kami akan membantu memecahkan bersama.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}