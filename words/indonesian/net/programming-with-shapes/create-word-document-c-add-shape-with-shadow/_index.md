---
category: general
date: 2026-03-27
description: Buat dokumen Word dengan C# dan pelajari cara menambahkan bentuk, menerapkan
  bayangan pada bentuk, serta mengatur jarak bayangan. Panduan langkah demi langkah
  untuk Aspose.Words.
draft: false
keywords:
- create word document c#
- how to add shape
- apply shadow to shape
- how to create rectangle
- set shadow distance
language: id
og_description: Buat dokumen Word C# dengan bentuk persegi panjang dan bayangan khusus.
  Ikuti tutorial lengkap ini untuk mengatur jarak bayangan dan gaya.
og_title: Buat Dokumen Word C# – Tambahkan Bentuk dengan Bayangan
tags:
- Aspose.Words
- C#
- Document Automation
title: Buat Dokumen Word C# – Tambahkan Bentuk dengan Bayangan
url: /id/net/programming-with-shapes/create-word-document-c-add-shape-with-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat Dokumen Word C# – Tambahkan Bentuk dengan Bayangan

Pernahkah Anda perlu **create word document c#** yang berisi persegi panjang bergaya rapi? Mungkin Anda sedang membuat templat laporan dan menginginkan bayangan drop‑shadow yang halus agar tata letak lebih menonjol. Dalam tutorial ini kami akan membahas tepat itu – cara menambahkan bentuk, menerapkan bayangan pada bentuk, dan bahkan menyesuaikan jarak bayangan menggunakan Aspose.Words.

Kami akan memulai dengan dokumen kosong, menambahkan sebuah persegi panjang, memberikan bayangan preset, dan menyelesaikannya dengan menyimpan file. Pada akhir tutorial Anda akan memiliki .docx siap‑pakai yang dapat dibuka di Word dan melihat efeknya secara langsung. Tanpa alat eksternal, hanya kode C# murni.

## Prasyarat

- .NET 6 (atau .NET Framework terbaru) terpasang.
- Visual Studio 2022 atau VS Code dengan ekstensi C#.
- Paket NuGet Aspose.Words untuk .NET (`Aspose.Words` versi 23.12 atau lebih baru).  
  Anda dapat menambahkannya melalui Package Manager Console:

  ```powershell
  Install-Package Aspose.Words
  ```

Itu saja – tidak diperlukan DLL tambahan atau interop COM.

## Langkah 1: Inisialisasi Dokumen Baru dan Builder – *create word document c#* Dasar

Pertama kita memerlukan objek `Document` yang mewakili file Word dan `DocumentBuilder` untuk mengeditnya.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a blank Word document
Document document = new Document();

// DocumentBuilder lets us add content programmatically
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Mengapa langkah ini penting:** Kelas `Document` adalah wadah untuk semua bagian Word (halaman, gaya, gambar). Builder adalah API tingkat tinggi yang menyembunyikan manipulasi node tingkat rendah, memudahkan untuk **create word document c#** tanpa harus berurusan langsung dengan XML.

## Langkah 2: Sisipkan Bentuk Persegi Panjang – *how to create rectangle*  

Sekarang kita akan menempatkan persegi panjang pada halaman. Ukurannya dinyatakan dalam poin (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle 200 pt wide and 100 pt tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue fill so we can see it clearly
rectangleShape.FillColor = Color.LightBlue;
```

> **Tip pro:** Jika Anda membutuhkan bentuk lain, cukup ganti `ShapeType.Rectangle` dengan `ShapeType.Ellipse`, `ShapeType.Triangle`, dll. Kode yang sama bekerja untuk **how to add shape** dari jenis apa pun.

## Langkah 3: Terapkan Bayangan Preset dan Sesuaikan – *apply shadow to shape*  

Aspose.Words menyediakan beberapa format bayangan preset. Kita akan menggunakan `Preset1` dan kemudian menyesuaikan jarak, blur, transparansi, dan warna.

```csharp
// Choose a predefined shadow style
rectangleShape.Shadow.Format = ShadowFormat.Preset1;

// Adjust the shadow distance – this is the offset from the shape
rectangleShape.Shadow.Distance = 5; // measured in points

// Make the edge of the shadow a little fuzzy
rectangleShape.Shadow.BlurRadius = 3;

// Set the shadow to be 40 % transparent (0 = opaque, 1 = fully transparent)
rectangleShape.Shadow.Transparency = 0.4;

// Pick a gray tone for the shadow color
rectangleShape.Shadow.Color = Color.Gray;
```

> **Mengapa menyesuaikan bayangan?** Properti `Distance` mengontrol seberapa jauh bayangan berada dari persegi panjang – anggap sebagai “angkat” yang Anda lihat pada render 3‑D. Mengubah `BlurRadius` melunakkan tepi, sementara `Transparency` memungkinkan Anda menciptakan tampilan yang halus dan profesional. Ini memenuhi kebutuhan **set shadow distance** dan menunjukkan cara **apply shadow to shape** secara fleksibel.

## Langkah 4: Simpan Dokumen – *create word document c#* Penyelesaian

Akhirnya, tulis dokumen ke disk. Sesuaikan path ke folder yang Anda miliki hak menulis.

```csharp
// Save the document as a .docx file
string outputPath = @"C:\Temp\ShadowShape.docx";
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Buka file hasilnya di Microsoft Word, dan Anda akan melihat persegi panjang berwarna biru muda dengan bayangan abu‑abu lembut yang bergeser sebesar 5 pt. Itu bukti visual bahwa Anda berhasil **create word document c#** dengan bentuk yang bergaya.

![Create Word Document C# with Shadowed Shape](shadow-example.png){: .img alt="contoh create word document c# menampilkan persegi panjang dengan bayangan"}

## Variasi Opsional & Kasus Tepi

| Skenario | Apa yang Diubah | Mengapa Penting |
|----------|----------------|-----------------|
| **Gaya bayangan berbeda** | `rectangleShape.Shadow.Format = ShadowFormat.Preset3;` | Memberikan tampilan yang lebih dramatis tanpa kode tambahan. |
| **Tanpa preset – bayangan khusus** | Hilangkan `Format` dan atur `OffsetX`, `OffsetY` secara manual. | Kontrol penuh atas arah dan kedalaman. |
| **Beberapa bentuk** | Panggil `builder.InsertShape` lagi sebelum menyimpan. | Berguna untuk templat kompleks dengan ikon, logo, dll. |
| **Kompatibilitas dengan versi Aspose lama** | Gunakan kelas `ShadowEffect` (tersedia di v20.x). | Memastikan kode Anda berjalan pada proyek lama. |
| **Menyimpan sebagai PDF** | `document.Save("ShadowShape.pdf");` | Rendering bayangan yang sama muncul pada output PDF. |

> **Pertanyaan umum:** *Bagaimana jika bayangan tidak muncul di Word?*  
> Pastikan Anda menggunakan versi terbaru Aspose.Words (≥ 22.9). Rilis lama memiliki dukungan bayangan terbatas. Juga pastikan dokumen dibuka dengan versi Word terbaru (2016+).

## Contoh Lengkap yang Berfungsi

Berikut adalah program lengkap yang siap disalin‑tempel. Program ini mencakup semua direktif `using`, komentar, dan penanganan error untuk pengalaman yang mulus.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShadowShapeDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document and a builder
                Document doc = new Document();
                DocumentBuilder builder = new DocumentBuilder(doc);

                // 2️⃣ Insert a rectangle (200 pt × 100 pt) and fill it
                Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
                rect.FillColor = Color.LightBlue;

                // 3️⃣ Apply a preset shadow and tweak its properties
                rect.Shadow.Format = ShadowFormat.Preset1;   // predefined style
                rect.Shadow.Distance = 5;                    // set shadow distance
                rect.Shadow.BlurRadius = 3;                  // soften edges
                rect.Shadow.Transparency = 0.4;              // semi‑transparent
                rect.Shadow.Color = Color.Gray;              // shadow color

                // 4️⃣ Save the document
                string outPath = @"C:\Temp\ShadowShape.docx";
                doc.Save(outPath);

                Console.WriteLine($"✅ Document created successfully at {outPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Error: {ex.Message}");
            }
        }
    }
}
```

Jalankan program, buka `C:\Temp\ShadowShape.docx`, dan Anda akan melihat persegi panjang dengan bayangan tepat seperti yang kami konfigurasikan.

## Ringkasan & Langkah Selanjutnya

- Anda kini tahu cara **create word document c#**, menyisipkan persegi panjang, dan **apply shadow to shape** dengan **set shadow distance** khusus.  
- Contoh ini menggunakan Aspose.Words, yang menyembunyikan kompleksitas OpenXML dan menjamin rendering konsisten di semua versi Word.  
- Ingin melangkah lebih jauh? Coba gabungkan beberapa bentuk, tambahkan teks di dalam persegi panjang, atau ekspor dokumen yang sama sebagai PDF untuk melihat bagaimana bayangan diterjemahkan.

### Topik Terkait yang Mungkin Anda Jelajahi

- **How to add shape** ke header/footer untuk branding.  
- Menggunakan **Aspose.Words** untuk menyisipkan diagram dan tabel secara programatis.  
- Menyesuaikan **shadow effects** pada gambar alih-alih bentuk vektor.  
- Mengotomatiskan pembuatan dokumen massal untuk faktur atau sertifikat.

Silakan bereksperimen, memecahkan kode, dan kemudian membangunnya kembali – itu cara tercepat untuk memahami konsep. Jika Anda mengalami kendala, tinggalkan komentar di bawah atau periksa dokumentasi resmi Aspose.Words untuk wawasan API yang lebih mendalam.

Selamat coding, dan nikmati membuat file Word Anda tampak lebih rapi!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}