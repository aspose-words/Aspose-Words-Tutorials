---
category: general
date: 2026-03-01
description: Buat dokumen Word menggunakan Aspose.Words dan pelajari cara menambahkan
  bentuk persegi panjang, cara menambahkan bayangan, cara mengatur transparansi, serta
  cara membuat bentuk—semua dalam C#.
draft: false
keywords:
- create word document
- add rectangle shape
- how to add shadow
- how to create shape
- how to set transparency
language: id
og_description: Buat dokumen Word dengan Aspose.Words di C#. Pelajari cara menambahkan
  bentuk persegi panjang, menerapkan bayangan luar, dan mengatur transparansi dalam
  beberapa langkah saja.
og_title: Buat Dokumen Word dengan Bentuk Persegi Panjang dan Bayangan – Panduan
tags:
- Aspose.Words
- C#
- Document Generation
title: Buat Dokumen Word dengan Bentuk Persegi Panjang dan Bayangan – Panduan Langkah
  demi Langkah
url: /id/net/programming-with-shapes/create-word-document-with-a-rectangle-shape-and-shadow-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat Dokumen Word dengan Bentuk Persegi Panjang dan Bayangan – Panduan Langkah‑per‑Langkah

Pernahkah Anda perlu **membuat dokumen word** yang berisi persegi panjang dengan gaya khusus? Mungkin Anda sedang membuat templat laporan dan menginginkan bayangan halus agar tata letaknya lebih menonjol. Anda tidak sendirian—para pengembang sering bertanya, “Bagaimana cara menambahkan bentuk persegi panjang dan bayangan secara programatis?” Kabar baiknya, dengan Aspose.Words Anda dapat melakukannya dalam beberapa baris kode.

Dalam tutorial ini kami akan membahas seluruh proses: mulai dari membuat file Word kosong, menambahkan bentuk persegi panjang, hingga mengonfigurasi bayangan luar dengan transparansi. Pada akhir tutorial Anda akan memiliki `Shadow.docx` yang siap pakai, dapat dibuka di Word, dan langsung menampilkan efeknya. Tanpa alat eksternal, tanpa XML yang rumit—hanya kode C# yang bersih dan penjelasan yang jelas.

## Apa yang Akan Anda Pelajari

- **Cara membuat objek shape** dalam dokumen Word menggunakan Aspose.Words.  
- **Cara menambahkan shape persegi panjang** ke sebuah paragraf tanpa mengganggu konten yang ada.  
- **Cara menambahkan bayangan** (bayangan luar) dan mengontrol warna, offset, blur, serta transparansinya.  
- **Cara mengatur transparansi** pada bayangan agar terlihat profesional.  
- Tips, jebakan, dan variasi yang mungkin Anda perlukan dalam proyek dunia nyata.

### Prasyarat

- .NET 6.0 atau lebih baru (API juga bekerja dengan .NET Framework 4.6+).  
- Aspose.Words untuk .NET terpasang via NuGet (`Install-Package Aspose.Words`).  
- Pemahaman dasar tentang sintaks C#—tidak perlu hal yang rumit, hanya pernyataan `using` dan pembuatan objek biasa.

> **Pro tip:** Jika Anda menggunakan Visual Studio, aktifkan “nullable reference types” untuk menangkap potensi bug referensi null lebih awal.

## Langkah 1 – Buat Dokumen Word Kosong

Untuk **membuat dokumen word** kita mulai dengan kelas `Document`. Anggaplah ini sebagai kanvas kosong; Anda dapat menambahkan bagian, paragraf, tabel, atau shape di kemudian hari.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new blank document
Document document = new Document();
```

Mengapa kita memerlukan instance `Document` yang baru? Karena setiap shape, paragraf, atau gaya hidup di dalam model objek dokumen (DOM). Memulai dengan dokumen bersih menjamin bahwa persegi panjang yang Anda tambahkan tidak akan mengganggu konten yang sudah ada.

## Langkah 2 – Definisikan Bentuk Persegi Panjang

Sekarang kita **cara membuat shape** sebuah persegi panjang. Konstruktor `Shape` menerima dokumen pemilik dan tipe shape. Kami juga mengatur lebar dan tinggi dalam poin (1 pt ≈ 1/72 in).

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width = 200;   // 200 pt ≈ 2.78 in
rectangleShape.Height = 100; // 100 pt ≈ 1.39 in
```

Anda mungkin bertanya, “Bisakah saya menggunakan sentimeter alih-alih poin?” API hanya menerima poin, tetapi Anda dapat mengonversinya: `points = centimeters * 28.35`. Konversi kecil ini berguna saat Anda menyelaraskan shape dengan margin halaman.

## Langkah 3 – Tambahkan Bayangan Luar dan Atur Transparansi

Inilah tempat keajaiban terjadi: **cara menambahkan bayangan** dan **cara mengatur transparansi** pada bayangan tersebut. Properti `ShadowFormat` memberi Anda kontrol penuh.

```csharp
// Enable shadow visibility
rectangleShape.ShadowFormat.Visible = true;

// Choose a shadow color
rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;

// Set transparency (0 = opaque, 1 = fully transparent)
rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent

// Position the shadow relative to the shape
rectangleShape.ShadowFormat.OffsetX = 5; // horizontal offset in points
rectangleShape.ShadowFormat.OffsetY = 5; // vertical offset in points

// Blur makes the shadow look softer
rectangleShape.ShadowFormat.BlurRadius = 4;

// Specify that this is an outer shadow (instead of inner)
rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;
```

**Mengapa pengaturan ini?**  
- **Transparansi** memungkinkan tekstur halaman di bawahnya terlihat, sehingga bayangan tidak tampak terlalu berat.  
- **OffsetX/Y** menciptakan ilusi bahwa shape terangkat dari halaman.  
- **BlurRadius** melunakkan tepi—tanpa ini bayangan akan menjadi persegi keras, yang terlihat tidak alami.  

Jika Anda menginginkan efek yang lebih dramatis, naikkan `OffsetX/Y` menjadi 10 dan tingkatkan `BlurRadius` menjadi 8. Sebaliknya, untuk sentuhan halus, pertahankan keduanya pada 2.

## Langkah 4 – Sisipkan Shape ke dalam Dokumen

Kami kini **menambahkan shape persegi panjang** ke paragraf pertama dokumen. Jika dokumen tidak memiliki konten, `FirstParagraph` akan otomatis dibuat untuk Anda.

```csharp
// Append the rectangle to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

Bagaimana jika Anda ingin shape berada di dalam sel tabel tertentu atau paragraf yang lebih jauh? Cukup temukan node tersebut (`doc.GetChild(NodeType.Paragraph, index, true)`) dan panggil `AppendChild` padanya. Objek shape yang sama dapat di‑clone jika Anda memerlukan beberapa salinan.

## Langkah 5 – Simpan Dokumen

Akhirnya, kami **membuat dokumen word** di disk. Gunakan jalur yang sesuai dengan lingkungan Anda; contoh di bawah menggunakan placeholder.

```csharp
// Save the document as a .docx file
document.Save(@"YOUR_DIRECTORY/Shadow.docx");
```

Saat Anda membuka `Shadow.docx` di Microsoft Word, Anda akan melihat persegi panjang berwarna abu‑abu muda dengan bayangan luar lembut yang bergeser ke kanan‑bawah. Transparansi bayangan sebesar 30 % memastikan bayangan tidak mendominasi halaman.

---

![Buat dokumen word dengan shape persegi panjang yang memiliki bayangan](image.png "Buat dokumen word dengan shape persegi panjang yang memiliki bayangan")

*Teks alt gambar: buat dokumen word dengan shape persegi panjang yang memiliki bayangan*

## Kode Lengkap yang Siap Dijalan­kan

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke aplikasi konsol. Tidak ada bagian yang hilang, tidak ada “lihat dokumentasi untuk selengkapnya”.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Add a rectangular shape and define its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width = 200;   // width in points
        rectangleShape.Height = 100;  // height in points

        // Step 3: Configure an outer shadow for the shape
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;
        rectangleShape.ShadowFormat.Transparency = 0.3;   // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;          // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;          // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;
        rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;

        // Step 4: Insert the shape into the first paragraph of the document
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // Step 5: Save the document with the shadowed shape
        document.Save(@"YOUR_DIRECTORY/Shadow.docx");

        Console.WriteLine("Word document created successfully at YOUR_DIRECTORY/Shadow.docx");
    }
}
```

### Hasil yang Diharapkan

- Sebuah file bernama **Shadow.docx** muncul di folder target.  
- Membukanya di Word menampilkan persegi panjang (200 × 100 pt) dengan bayangan luar berwarna abu‑abu gelap.  
- Bayangan tersebut bergeser 5 pt secara horizontal dan vertikal, memiliki blur, dan transparansi 30 %.

## Pertanyaan Umum & Kasus Tepi

| Pertanyaan | Jawaban |
|------------|---------|
| **Bisakah saya mengubah warna bayangan agar sesuai dengan merek saya?** | Tentu—ganti saja `System.Drawing.Color.DarkGray` dengan `Color` pilihan Anda, misalnya `Color.FromArgb(255, 0, 120, 215)` untuk aksen biru. |
| **Bagaimana jika saya membutuhkan bayangan dalam (inner) bukan luar?** | Atur `ShadowFormat.Style = ShadowStyle.InnerShadow`. Properti lainnya berfungsi sama. |
| **Apakah transparansi didukung di versi Word yang lebih lama?** | Ya. Aspose.Words menulis XML yang tepat sehingga Word 2007+ dapat memahaminya. Versi yang lebih lama mungkin mengabaikan nilai transparansi tetapi tetap menampilkan bayangan. |
| **Bisakah saya menambahkan beberapa shape dengan bayangan berbeda?** | Tentu—buat instance `Shape` baru, konfigurasikan masing‑masing bayangannya, lalu tambahkan ke node yang diinginkan. |
| **Bagaimana dengan performa bila ada ratusan shape?** | Membuat banyak shape dapat meningkatkan penggunaan memori. Gunakan satu instance `Document` dan tambahkan shape dalam loop; buang objek sementara bila terjadi tekanan memori. |

## Tips untuk Proyek Dunia Nyata

- **Pembuatan batch:** Saat menghasilkan laporan untuk banyak pengguna, buat satu template `Document` dan clone untuk setiap iterasi. Ganti placeholder sebelum menambahkan shape.  
- **Ukuran dinamis:** Gunakan dimensi halaman (`document.FirstSection.PageSetup.PageWidth`) untuk menghitung ukuran shape relatif terhadap halaman, sehingga tata letak tetap konsisten pada berbagai ukuran kertas.  
- **Pengujian:** Selalu buka file `.docx` yang dihasilkan di Word setelah mengubah parameter bayangan. Umpan balik visual lebih cepat daripada menebak‑tebakan angka.

## Langkah Selanjutnya

Setelah Anda menguasai **cara menambahkan shape persegi panjang**, **cara menambahkan bayangan**, dan **cara mengatur transparansi**, pertimbangkan untuk mengeksplorasi:

- Menambahkan **gradient fill** ke shape (`Shape.FillFormat`).  
- Menyisipkan **gambar** di dalam shape untuk efek watermark.  
- Menggunakan **tabel** untuk menyelaraskan beberapa shape berbayangan dalam grid.  
- Mengekspor dokumen yang sama ke PDF (`document.Save("output.pdf")`) sambil mempertahankan bayangan.

Semua hal ini dibangun di atas konsep inti yang sama, sehingga Anda akan merasa nyaman memperluas kode.

---

### Ringkasan

Kami memulai dengan **membuat dokumen word** menggunakan Aspose.Words, kemudian **cara membuat shape** sebuah persegi panjang, menerapkan **cara menambahkan bayangan**, menyesuaikan **cara mengatur transparansi**, dan menyimpan hasilnya. Seluruh proses terbungkus dalam pola ringkas yang dapat dipakai kembali dan dapat disesuaikan dengan skenario otomasi apa pun.

Silakan bereksperimen—ubah warna, mainkan offset, atau tumpuk beberapa shape bersama. Jika menemui kendala, kembali ke bagian‑bagian di atas; mereka dirancang sebagai referensi cepat. Selamat coding, semoga dokumen Anda selalu tampak profesional!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}