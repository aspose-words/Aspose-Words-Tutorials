---
category: general
date: 2026-03-30
description: Pelajari cara mengatur bayangan pada bentuk Word menggunakan C#. Panduan
  ini juga menunjukkan cara menambahkan bayangan pada bentuk, menyesuaikan transparansi
  bentuk, dan menambahkan bayangan pada persegi panjang.
draft: false
keywords:
- how to set shadow
- adjust shape transparency
- add shape shadow
- how to add shadow
- add rectangle shadow
language: id
og_description: Cara menambahkan bayangan pada bentuk Word di C#? Ikuti panduan langkah
  demi langkah ini untuk menambahkan bayangan pada bentuk, mengatur transparansi bentuk,
  dan menambahkan bayangan pada persegi panjang.
og_title: Cara Mengatur Bayangan pada Bentuk Word – Tutorial C#
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Cara Mengatur Bayangan pada Bentuk Word – Tutorial C#
url: /id/net/programming-with-shapes/how-to-set-shadow-on-a-word-shape-c-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menetapkan Bayangan pada Bentuk Word – Tutorial C#

Pernah bertanya‑tanya **cara menetapkan bayangan** pada sebuah bentuk di dalam dokumen Word tanpa harus mengutak‑atik UI? Anda tidak sendirian. Dalam banyak laporan atau presentasi pemasaran, bayangan tipis membuat sebuah persegi panjang menonjol, dan melakukannya secara programatik menghemat jam kerja.

Dalam panduan ini kami akan menelusuri contoh lengkap yang siap dijalankan yang tidak hanya menunjukkan **cara menetapkan bayangan**, tetapi juga mencakup **add shape shadow**, **adjust shape transparency**, dan bahkan **add rectangle shadow** untuk kotak penjelasan klasik. Pada akhir tutorial Anda akan memiliki file Word (`output.docx`) yang tampak profesional, dan Anda akan memahami mengapa setiap properti penting.

## Prasyarat

- .NET 6+ (atau .NET Framework 4.7.2) dengan kompiler C#  
- Paket NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- Familiaritas dasar dengan C# dan model objek Word  

Tidak ada pustaka tambahan yang diperlukan—semuanya berada dalam Aspose.Words.

---

## Cara Menetapkan Bayangan pada Bentuk Word di C#

Berikut adalah file sumber lengkap. Simpan sebagai `Program.cs` dan jalankan dari IDE Anda atau `dotnet run`. Kode ini memuat file `.docx` yang sudah ada, menemukan bentuk pertama (biasanya persegi panjang), mengaktifkan bayangannya, menyesuaikan beberapa parameter visual, dan menyimpan hasilnya.

```csharp
// Program.cs
using System;
using System.Drawing;               // For Color
using Aspose.Words;                // Core document API
using Aspose.Words.Drawing;        // Shape and shadow classes

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the shape.
        // Replace YOUR_DIRECTORY with the folder where your files live.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the first shape in the document.
        // If you have multiple shapes, you can loop or use GetChild with a different index.
        Shape rectangleShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (rectangleShape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx contains at least one shape.");
            return;
        }

        // 3️⃣ Enable the shape's shadow and choose a base color.
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Black;   // You can pick any System.Drawing.Color

        // 4️⃣ Fine‑tune the shadow appearance.
        rectangleShape.ShadowFormat.Transparency = 0.3;     // 30 % transparent (adjust shape transparency)
        rectangleShape.ShadowFormat.OffsetX = 5;           // Horizontal offset in points
        rectangleShape.ShadowFormat.OffsetY = 5;           // Vertical offset in points
        rectangleShape.ShadowFormat.BlurRadius = 4;       // Soft edge radius

        // 5️⃣ Save the updated document.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Shadow applied! Check {outputPath}");
    }
}
```

> **Apa yang akan Anda lihat** – Persegi panjang kini memiliki bayangan drop‑shadow hitam dengan transparansi 30 %, bergeser 5 pt ke kanan dan ke bawah, serta blur yang lembut. Buka `output.docx` di Word untuk memverifikasi.

## Sesuaikan Transparansi Bentuk – Mengapa Penting

Transparansi bukan sekadar kontrol estetika; ia memengaruhi keterbacaan. Nilai 0.0 membuat bayangan sepenuhnya tidak tembus, sementara 1.0 menyembunyikannya sepenuhnya. Pada cuplikan di atas kami menggunakan `0.3` untuk menghasilkan efek halus yang bekerja pada latar belakang terang maupun gelap. Silakan bereksperimen:

```csharp
rectangleShape.ShadowFormat.Transparency = 0.1; // Almost solid shadow
rectangleShape.ShadowFormat.Transparency = 0.6; // Very faint
```

Ingat, **adjust shape transparency** juga dapat diterapkan pada warna isi bentuk jika Anda memerlukan persegi panjang semi‑transparent.

## Tambahkan Bayangan pada Berbagai Objek

Kode yang kami gunakan menargetkan objek `Shape`, tetapi properti `ShadowFormat` yang sama ada pada **Image**, **Chart**, dan bahkan **TextBox**. Berikut pola cepat yang dapat Anda salin‑tempel:

```csharp
// Assuming 'image' is an Aspose.Words.Drawing.Image object
image.ShadowFormat.Visible = true;
image.ShadowFormat.Color = Color.Gray;
image.ShadowFormat.OffsetX = 3;
image.ShadowFormat.OffsetY = 3;
image.ShadowFormat.BlurRadius = 2;
```

Jadi apakah Anda **add shape shadow** pada logo atau ikon dekoratif, pendekatannya tetap sama.

## Cara Menambahkan Bayangan pada Bentuk Apa Pun – Kasus Khusus

1. **Bentuk tanpa kotak pembatas** – Beberapa bentuk Word (seperti coretan bebas) tidak mendukung bayangan. Mencoba mengatur `ShadowFormat.Visible` akan gagal secara diam‑diam. Periksa `shape.IsShadowSupported` bila Anda memerlukan keamanan.  
2. **Versi Word lama** – Properti bayangan berhubungan dengan fitur Word 2007+. Jika Anda harus mendukung Word 2003, bayangan akan diabaikan saat file dibuka.  
3. **Multiple shadows** – Aspose.Words saat ini hanya mendukung satu bayangan per bentuk. Jika Anda memerlukan efek lapisan ganda, duplikat bentuk, geser posisinya, dan terapkan pengaturan bayangan yang berbeda.

## Tambahkan Bayangan Persegi Panjang – Kasus Penggunaan Dunia Nyata

Bayangkan Anda sedang menghasilkan laporan triwulanan dan setiap judul bagian berupa persegi panjang berwarna. Menambahkan **add rectangle shadow** memberikan tampilan “kartu” pada halaman. Langkahnya identik dengan contoh dasar; pastikan bentuk yang Anda targetkan memang persegi panjang (`shape.ShapeType == ShapeType.Rectangle`). Jika Anda perlu membuat persegi panjang dari awal, lihat cuplikan di bawah:

```csharp
// Create a new rectangle shape programmatically
Shape newRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,
    Height = 50,
    WrapType = WrapType.Inline
};
newRect.FillColor = Color.LightBlue;

// Apply shadow (same settings as before)
newRect.ShadowFormat.Visible = true;
newRect.ShadowFormat.Color = Color.Black;
newRect.ShadowFormat.Transparency = 0.25;
newRect.ShadowFormat.OffsetX = 4;
newRect.ShadowFormat.OffsetY = 4;
newRect.ShadowFormat.BlurRadius = 3;

// Insert into the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(newRect);
```

Menjalankan program lengkap dengan penambahan ini akan menghasilkan persegi panjang baru yang sudah memiliki efek **add rectangle shadow** yang diinginkan.

---

![Word shape with shadow](placeholder-image.png){alt="cara menetapkan bayangan pada bentuk di Word"}

*Gambar: Persegi panjang setelah pengaturan bayangan diterapkan.*

## Ringkasan Cepat (Cheat Sheet Poin‑Poin)

- **Load** dokumen dengan `new Document(path)`.  
- **Locate** bentuk melalui `doc.GetChild(NodeType.Shape, index, true)`.  
- **Enable** bayangan: `shape.ShadowFormat.Visible = true;`.  
- **Set color** dengan warna apa saja dari `System.Drawing.Color`.  
- **Adjust transparency** (`0.0–1.0`) untuk mengontrol opasitas.  
- **OffsetX / OffsetY** memindahkan bayangan secara horizontal/vertikal (dalam point).  
- **BlurRadius** melunakkan tepi—nilai lebih tinggi = bayangan lebih kabur.  
- **Save** file dan buka di Word untuk melihat hasilnya.

## Apa yang Bisa Dicoba Selanjutnya?

- **Warna dinamis** – Ambil warna bayangan dari tema atau input pengguna.  
- **Bayangan bersyarat** – Terapkan bayangan hanya ketika lebar bentuk melebihi ambang tertentu.  
- **Pemrosesan batch** – Loop melalui semua bentuk dalam dokumen dan **add shape shadow** secara otomatis.  

Jika Anda telah mengikuti langkah‑langkah ini, kini Anda tahu **cara menetapkan bayangan**, cara **menyesuaikan transparansi bentuk**, dan cara **menambahkan bayangan persegi panjang** untuk sentuhan profesional. Silakan bereksperimen, pecahkan masalah, dan perbaiki kembali—coding adalah guru terbaik.

---

*Selamat coding! Jika tutorial ini membantu Anda, tinggalkan komentar atau bagikan trik bayangan Anda sendiri. Semakin banyak kita belajar satu sama lain, semakin cantik dokumen Word kita.* 

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}