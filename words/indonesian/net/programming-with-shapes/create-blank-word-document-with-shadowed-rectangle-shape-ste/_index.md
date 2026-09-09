---
category: general
date: 2026-01-08
description: Buat dokumen Word kosong dan pelajari cara menambahkan bayangan pada
  bentuk persegi panjang. Sisipkan file Word berisi bentuk dan tambahkan bayangan
  bentuk menggunakan C# dengan Aspose.Words.
draft: false
keywords:
- create blank word
- how to add shadow
- rectangle shape word
- insert shape word
- add shape shadow
language: id
og_description: Buat dokumen Word kosong dan lihat cara menambahkan bayangan pada
  bentuk persegi panjang menggunakan C#. Kode lengkap, penjelasan, dan tips.
og_title: Buat Dokumen Word Kosong – Tambahkan Bentuk Persegi Panjang Berbayang
tags:
- Aspose.Words
- C#
- Document Automation
title: Buat Dokumen Word Kosong dengan Bentuk Persegi Panjang Berbayang – Panduan
  Langkah demi Langkah
url: /id/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat Dokumen Word Kosong dengan Bentuk Persegi Panjang Berbayang – Tutorial Lengkap

Pernah perlu **membuat Word kosong** secara programatis dan kemudian menghiasnya dengan persegi panjang berbayang yang bagus? Anda bukan satu-satunya. Banyak pengembang menemui kendala ketika mereka menemukan bahwa menyisipkan bentuk dan menerapkan efek tidak semudah mengetik teks.

Dalam panduan ini kami akan membahas seluruh proses—dari membuat `.docx` kosong hingga **cara menambahkan bayangan** ke objek **rectangle shape word**, dan akhirnya **menyisipkan konten shape word** dengan efek **add shape shadow** yang halus. Pada akhir tutorial Anda akan memiliki potongan kode siap pakai yang bekerja dengan Aspose.Words for .NET terbaru.

---

## Apa yang Anda Butuhkan

- **Aspose.Words for .NET** (v24.10 atau lebih baru) – perpustakaan yang mendukung semua hal di bawah ini.  
- Lingkungan pengembangan .NET (Visual Studio, Rider, atau `dotnet` CLI).  
- Pengetahuan dasar C# – jika Anda dapat menulis “Hello World”, Anda siap.  

Tidak diperlukan paket NuGet tambahan; semuanya berada di dalam `Aspose.Words` dan `System.Drawing`.

---

## Langkah 1: Buat Dokumen Word Kosong

Hal pertama yang harus dilakukan adalah membuat objek `Document` kosong. Anggaplah ini sebagai kanvas baru—seperti membuka file Word baru secara manual.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a brand‑new blank Word document
Document document = new Document();   // This creates an empty .docx in memory
```

*Mengapa ini penting:*  
Sebuah instance `Document` mewakili seluruh file Word. Memulai dengan yang kosong memberi Anda kontrol penuh atas setiap elemen yang akan Anda tambahkan nanti, mulai dari paragraf hingga bentuk.

---

## Langkah 2: Definisikan Bentuk Persegi Panjang (Rectangle Shape Word)

Sekarang kita membutuhkan sebuah bentuk untuk dikerjakan. Persegi panjang adalah geometri paling sederhana dan cocok untuk spanduk, placeholder, atau mock‑up UI sederhana.

```csharp
// Step 2: Create a rectangle shape with specific dimensions
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};
```

*Mengapa ini penting:*  
Menetapkan `Width` dan `Height` memungkinkan Anda mengontrol jejak visual bentuk. `ShapeType.Rectangle` memberi tahu Aspose untuk merender kotak klasik—sempurna untuk mendemonstrasikan **add shape shadow** nanti.

---

## Langkah 3: Terapkan Bayangan pada Bentuk (Cara Menambahkan Bayangan)

Bayangan memberikan kedalaman, membuat persegi panjang datar terasa seperti objek fisik. Aspose.Words menyediakan properti `Shadow` dimana Anda dapat menyesuaikan warna, jarak, blur, dan transparansi.

```csharp
// Step 3: Enable and configure the shadow effect
rectangleShape.Shadow.Enabled      = true;               // Turn the shadow on
rectangleShape.Shadow.Color        = Color.Gray;         // Shadow color
rectangleShape.Shadow.Distance    = 5.0;                // How far the shadow is offset
rectangleShape.Shadow.BlurRadius  = 3.0;                // Softness of the edge
rectangleShape.Shadow.Transparency = 0.2;               // 0 = opaque, 1 = fully transparent
```

*Mengapa ini penting:*  
Setiap properti memengaruhi petunjuk visual:

- **Enabled** – tanpa ini pengaturan lain diabaikan.  
- **Color** – pilih warna yang cocok dengan tema dokumen Anda.  
- **Distance** – nilai yang lebih besar memindahkan bayangan lebih jauh.  
- **BlurRadius** – angka yang lebih tinggi membuat bayangan lebih lembut.  
- **Transparency** – sesuaikan opasitas untuk kesan halus.

Silakan bereksperimen; untuk efek dramatis, naikkan `Distance` menjadi `10` dan atur `Transparency` menjadi `0.5`.

---

## Langkah 4: Sisipkan Bentuk ke dalam Dokumen (Insert Shape Word)

Setelah persegi panjang siap, kita membutuhkan tempat untuk menaruhnya. Tempat paling sederhana adalah paragraf pertama dari badan dokumen.

```csharp
// Step 4: Append the shape to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

*Mengapa ini penting:*  
`FirstSection.Body.FirstParagraph` selalu ada dalam `Document` baru. Dengan menambahkan bentuk di sini, Anda memastikan bentuk muncul di bagian atas file—berguna untuk header atau spanduk judul.

Jika Anda perlu menyisipkan bentuk di tempat lain, Anda dapat menemukan `Paragraph` atau `Run` tertentu dan menggunakan `InsertAfter` atau `InsertBefore`.

---

## Langkah 5: Simpan File Word

Langkah terakhir adalah menyimpan dokumen dalam memori ke disk. Pilih folder yang Anda memiliki hak menulis, dan beri file nama yang bermakna.

```csharp
// Step 5: Save the document with the shadowed rectangle
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
document.Save(outputPath);
```

*Mengapa ini penting:*  
Memanggil `Save` menulis file `.docx` yang sepenuhnya sesuai standar. Buka di Microsoft Word, LibreOffice, atau penampil apa pun, dan Anda akan melihat persegi panjang dengan bayangan abu‑abu lembut—tepat seperti yang kami atur.

---

## Contoh Lengkap yang Berfungsi

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke aplikasi konsol. Program ini mencakup semua direktif `using`, pembuatan bentuk, konfigurasi bayangan, penyisipan, dan penyimpanan.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Define a rectangle shape (rectangle shape word)
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
        {
            Width  = 200,
            Height = 100
        };

        // 3️⃣ How to add shadow – configure the shadow effect
        rectangleShape.Shadow.Enabled      = true;
        rectangleShape.Shadow.Color        = Color.Gray;
        rectangleShape.Shadow.Distance    = 5.0;
        rectangleShape.Shadow.BlurRadius  = 3.0;
        rectangleShape.Shadow.Transparency = 0.2;

        // 4️⃣ Insert shape word into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 5️⃣ Save the file (add shape shadow persisted)
        string outputPath = @"C:\Temp\ShadowedRectangle.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Output yang diharapkan:**  
Buka `ShadowedRectangle.docx` dan Anda akan melihat persegi panjang abu‑abu muda yang terpusat di bagian atas halaman dengan bayangan halus yang bergeser 5 pts. Tidak ada teks tambahan, hanya bentuk—tepat seperti yang dihasilkan kode.

---

## Pertanyaan Umum & Kasus Tepi

### Bagaimana jika saya membutuhkan bentuk lain?

Ganti `ShapeType.Rectangle` dengan nilai enum `ShapeType` lain apa pun (`Ellipse`, `Triangle`, `Star`, dll.). Properti bayangan bekerja dengan cara yang sama.

### Bisakah saya menambahkan beberapa bayangan?

Aspose.Words hanya mendukung satu bayangan per bentuk. Jika Anda membutuhkan efek berlapis, buat dua bentuk yang tumpang tindih dengan pengaturan bayangan yang berbeda.

### Bagaimana cara kerja ini di .NET Core?

API yang sama bekerja pada .NET 6/7/8. Pastikan Anda merujuk paket **Aspose.Words.NETCore** (atau paket standar, yang kini lintas‑platform).

### Apakah `System.Drawing` masih didukung di Linux?

`System.Drawing.Common` hanya tersedia untuk Windows mulai .NET 6. Untuk proyek lintas‑platform, gunakan `Aspose.Drawing` (NuGet terpisah) atau tetap gunakan warna yang didefinisikan oleh `Aspose.Words` itu sendiri.

### Bagaimana dengan skala DPI?

Dimensi bentuk dalam poin (1 pt = 1/72 inci). Jika Anda membutuhkan ukuran pixel‑perfect untuk DPI tertentu, hitung poin sebagai `pixels * 72 / dpi`.

---

## Tips Pro & Hal-hal yang Perlu Diwaspadai

- **Pro tip:** Atur `rectangleShape.WrapType = WrapType.Inline;` jika Anda ingin bentuk mengalir bersama teks alih‑alih melayang di atasnya.  
- **Waspadai:** Lupa mengaktifkan bayangan (`Enabled = true`). Pengaturan lain akan diabaikan secara diam‑diam.  
- **Catatan kinerja:** Menambahkan banyak bentuk dalam loop ketat dapat memperlambat. Kelompokkan dalam satu `Section` dan panggil `document.UpdatePageLayout()` sekali di akhir.  
- **Pemeriksaan versi:** API bayangan diperkenalkan di Aspose.Words 20.2. Jika Anda menggunakan versi lebih lama, tingkatkan untuk menghindari properti yang hilang.

---

## Kesimpulan

Kami telah **membuat dokumen Word kosong**, membangun **rectangle shape word**, mempelajari **cara menambahkan bayangan**, dan akhirnya **menyisipkan konten shape word** dengan efek **add shape shadow** yang halus—semua menggunakan Aspose.Words untuk .NET.  

Potongan kode ini dapat dijalankan sepenuhnya, berfungsi di Windows dan .NET lintas‑platform, serta dapat diperluas ke bentuk lain, warna, atau bahkan GIF animasi. Selanjutnya, Anda dapat mengeksplor menambahkan teks di dalam persegi panjang, menerapkan isian gradien, atau menghasilkan seluruh laporan dengan banyak bentuk bergaya.

Punya ide lain? Coba ganti bayangan abu‑abu dengan biru, tingkatkan blur untuk tampilan dreamy, atau gabungkan beberapa bentuk menjadi logo khusus. Langit adalah batasnya, dan kini Anda memiliki blok bangunan untuk melakukannya.

Selamat coding, semoga dokumen Anda selalu tampak tajam (dengan jumlah bayangan yang tepat)!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}