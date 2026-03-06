---
category: general
date: 2026-03-06
description: Buat bentuk persegi panjang di Word dan tambahkan bayangan bentuk dengan
  Aspose.Words. Pelajari cara menyisipkan persegi panjang di Word dan cara menambahkan
  bayangan pada bentuk menggunakan C#.
draft: false
keywords:
- create rectangle shape
- add shape shadow
- how to insert rectangle in word
- how to add shadow to shape
language: id
og_description: Buat bentuk persegi panjang di Word dan tambahkan bayangan bentuk
  dengan Aspose.Words. Panduan langkah demi langkah tentang cara menyisipkan persegi
  panjang di Word dan cara menambahkan bayangan pada bentuk.
og_title: Buat bentuk persegi panjang dengan bayangan di Word menggunakan Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Buat bentuk persegi panjang dengan bayangan di Word menggunakan Aspose.Words
url: /id/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-word-using-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat bentuk persegi panjang dengan bayangan di Word menggunakan Aspose.Words

Pernahkah Anda perlu **create rectangle shape** dalam dokumen Word tetapi tidak yakin bagaimana memberi tampilan yang halus? Anda tidak sendirian—banyak pengembang mengalami kendala yang sama saat pertama kali mencoba menambahkan sentuhan visual ke dokumen otomatis. Kabar baiknya? Dengan Aspose.Words untuk .NET Anda dapat **create rectangle shape** dan **add shape shadow** hanya dengan beberapa baris C#.

Dalam tutorial ini kami akan menjelaskan secara tepat **how to insert rectangle in Word**, kemudian menunjukkan **how to add shadow to shape** sehingga bentuk tersebut tampak menonjol dari halaman. Pada akhir tutorial Anda akan memiliki `Shadow.docx` yang siap disimpan, yang dapat Anda buka di Word dan melihat persegi panjang berwarna abu‑abu dengan bayangan lembut. Tanpa file gambar tambahan, tanpa penyetelan manual—hanya kode.

## Apa yang Akan Anda Pelajari

- Pernyataan C# yang tepat diperlukan untuk **create rectangle shape** dengan Aspose.Words.  
- Cara mengaktifkan dan mengonfigurasi bayangan menggunakan objek `Shadow`.  
- Mengapa setiap properti penting (mis., `Transparency`, `Blur`, `Angle`).  
- Kesulitan umum (satuan, kompatibilitas versi) dan solusi cepat.  
- Program lengkap yang siap disalin‑tempel yang dapat Anda jalankan hari ini.

### Prasyarat

- .NET 6+ (atau .NET Framework 4.7+).  
- Aspose.Words untuk .NET 23.10 atau yang lebih baru (paket NuGet-nya adalah `Aspose.Words`).  
- Pemahaman dasar tentang C# dan Visual Studio (atau IDE apa pun yang Anda sukai).  

Jika Anda sudah memiliki semuanya, mari langsung mulai.

---

## Langkah 1: Siapkan proyek dan impor namespace

Pertama, buat aplikasi console baru (atau gunakan yang sudah ada) dan tambahkan paket NuGet Aspose.Words:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Selanjutnya, impor namespace yang diperlukan ke dalam `Program.cs` Anda:

```csharp
using System.Drawing;               // For Color
using Aspose.Words;                  // Core document classes
using Aspose.Words.Drawing;          // Shape and Shadow types
```

> **Pro tip:** Jika Anda menargetkan .NET 6+, Anda dapat mengaktifkan direktif `using` global untuk menghindari pengulangan baris ini di setiap file.

---

## Langkah 2: **Create rectangle shape** dalam dokumen Word kosong

Kami akan memulai dengan objek `Document` baru dan `DocumentBuilder` untuk memanipulasinya. Metode `InsertShape` pada builder adalah tempat keajaiban terjadi.

```csharp
// Step 2: Initialize a new document and builder
Document document = new Document();                     // Blank Word file
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle – 200 × 100 points (≈2.78 × 1.39 inches)
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

Mengapa 200 × 100 poin? Di Word, satu poin sama dengan 1/72 inci, sehingga persegi panjang kira‑kira berukuran 2,8 × 1,4 inci—cukup besar untuk terlihat namun tidak berlebihan. Anda dapat mengubah angka‑angka ini sesuai tata letak Anda; ingat bahwa ukurannya dalam **points**, bukan piksel.

---

## Langkah 3: **Add shape shadow** – mengonfigurasi tampilan

Setelah kita memiliki persegi panjang, mari beri bayangan abu‑abu yang halus. Objek `Shadow` berada pada `Shape` dan menyediakan beberapa properti berguna.

```csharp
// Step 3: Turn on the shadow and tweak its appearance
rectangle.Shadow.Enabled = true;               // Switch the shadow on
rectangle.Shadow.Color = Color.Gray;           // Shadow hue
rectangle.Shadow.Transparency = 0.3;           // 30 % transparent – looks softer
rectangle.Shadow.Blur = 5;                     // Blur radius (points)
rectangle.Shadow.Distance = 4;                 // How far the shadow sits from the shape
rectangle.Shadow.Angle = 45;                   // Direction in degrees (45° = down‑right)
rectangle.Shadow.Size = 100;                   // 100 % of the original shape size
```

### Apa fungsi masing‑masing properti

| Property | Effect | Typical values |
|----------|--------|----------------|
| **Enabled** | Mengaktifkan atau menonaktifkan bayangan | `true` or `false` |
| **Color** | Warna dasar bayangan | Any `System.Drawing.Color` |
| **Transparency** | Kejernihan (0 = padat, 1 = tak terlihat) | 0.0 – 1.0 |
| **Blur** | Kelembutan tepi | 0 – 10 (higher = softer) |
| **Distance** | Jarak antara bentuk dan bayangan | 0 – 20 points |
| **Angle** | Arah cahaya yang tampak datang | 0 – 360 degrees |
| **Size** | Skala bayangan relatif terhadap bentuk | 0 – 200 % |

> **Mengapa repot‑repot dengan pengaturan ini?**  
> Menyetel bayangan secara halus memungkinkan Anda menyesuaikan dengan pedoman merek perusahaan (mis., transparansi 20 % yang halus untuk tampilan profesional) tanpa harus menggunakan editor gambar eksternal.

---

## Langkah 4: Simpan dokumen dan verifikasi hasilnya

Akhirnya, tulis file ke disk. Anda dapat memilih folder mana saja; cukup ganti `YOUR_DIRECTORY` dengan jalur yang sebenarnya.

```csharp
// Step 4: Persist the document
string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Buka `Shadow.docx` di Microsoft Word dan Anda akan melihat persegi panjang abu‑abu dengan bayangan lembut yang bergeser pada sudut 45°. Petunjuk visual ini membuat bentuk terasa “terangkat” dari halaman—tepat seperti yang diharapkan dari laporan atau faktur yang profesional.

---

## Contoh Lengkap yang Berfungsi

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke `Program.cs`. Tidak ada bagian yang hilang; program ini dapat dikompilasi dan dijalankan apa adanya.

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (200 × 100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // 3️⃣ Enable the shape's shadow and configure its appearance
        rectangle.Shadow.Enabled = true;               // Turn the shadow on
        rectangle.Shadow.Color = Color.Gray;           // Shadow colour
        rectangle.Shadow.Transparency = 0.3;           // 30 % transparent
        rectangle.Shadow.Blur = 5;                     // Blur radius
        rectangle.Shadow.Distance = 4;                 // Offset from the shape
        rectangle.Shadow.Angle = 45;                   // Direction in degrees
        rectangle.Shadow.Size = 100;                   // Shadow size as a percentage

        // 4️⃣ Save the document with the shadowed shape
        string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Output yang Diharapkan

- **File:** `Shadow.docx` ditempatkan di folder eksekusi proyek.  
- **Visual:** Sebuah persegi panjang tunggal di tengah halaman, berisi warna putih default, dan bayangan abu‑abu bergeser 4 poin ke kanan‑bawah, sedikit blur untuk tampilan alami.

---

## Pertanyaan Umum & Kasus Tepi

### 1. Bagaimana jika saya membutuhkan satuan berbeda (mis., sentimeter)?

Aspose.Words bekerja dalam poin, tetapi Anda dapat mengonversi sentimeter ke poin dengan rumus sederhana:  
`points = centimeters * 28.3465`.  

```csharp
double cmWidth = 5.0; // 5 cm
double cmHeight = 2.5; // 2.5 cm
Shape rectCm = builder.InsertShape(ShapeType.Rectangle,
                                   (float)(cmWidth * 28.3465),
                                   (float)(cmHeight * 28.3465));
```

### 2. Apakah ini bekerja dengan versi Aspose.Words yang lebih lama?

API `Shadow` diperkenalkan pada versi 14.0. Jika Anda menggunakan rilis yang lebih lama, Anda harus memperbarui melalui NuGet. Sisanya kode (pembuatan bentuk) telah stabil selama bertahun‑tahun, sehingga Anda tidak akan mengalami perubahan yang merusak.

### 3. Bisakah saya menambahkan bayangan ke bentuk lain (mis., lingkaran)?

Tentu saja—setiap objek `Shape` memiliki properti `Shadow`. Cukup ganti `ShapeType.Rectangle` dengan `ShapeType.Ellipse` atau `ShapeType.Cloud`, lalu terapkan pengaturan bayangan yang sama.

### 4. Bagaimana jika saya membutuhkan bayangan berwarna (mis., biru untuk merek)?

Ganti `Color.Gray` dengan `Color` apa pun yang Anda suka:

```csharp
rectangle.Shadow.Color = Color.FromArgb(30, 0, 120); // Dark blue
```

Ingat untuk menyesuaikan `Transparency` agar warna tidak menjadi terlalu dominan.

---

## 🎨 Ringkasan Visual

![membuat bentuk persegi panjang dengan bayangan di Word menggunakan Aspose.Words](image-placeholder.png "membuat bentuk persegi panjang dengan bayangan di Word menggunakan Aspose.Words")

*Alt text: membuat bentuk persegi panjang dengan bayangan di Word menggunakan Aspose.Words*

Screenshot (placeholder) menunjukkan dokumen akhir—hanya persegi panjang dan bayangan abu‑abu lembutnya.

---

## Kesimpulan

Anda sekarang tahu cara **create rectangle shape** dalam file Word, **add shape shadow**, dan menyetel setiap aspek visual menggunakan Aspose.Words untuk .NET. Program singkat yang kami buat mencakup seluruh alur kerja—dari

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}