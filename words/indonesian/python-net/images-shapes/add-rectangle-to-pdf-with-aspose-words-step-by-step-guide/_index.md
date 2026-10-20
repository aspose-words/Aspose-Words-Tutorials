---
category: general
date: 2026-03-01
description: Tambahkan persegi panjang ke PDF dengan cepat menggunakan Aspose.Words.
  Pelajari cara menyisipkan bentuk ke PDF, menambahkan grafik ke PDF, dan membuat
  dokumen PDF secara programatis dengan bayangan khusus.
draft: false
keywords:
- add rectangle to pdf
- insert shape pdf
- add graphics to pdf
- create pdf document programmatically
- create pdf with shape
language: id
og_description: Tambahkan persegi panjang ke PDF menggunakan Aspose.Words. Tutorial
  ini menunjukkan cara menyisipkan bentuk ke PDF, menambahkan grafik ke PDF, dan membuat
  dokumen PDF secara programatis dengan C#.
og_title: Tambahkan persegi panjang ke PDF dengan Aspose.Words – Panduan Lengkap
tags:
- pdf
- aspnet
- csharp
- graphics
title: Tambahkan persegi panjang ke PDF dengan Aspose.Words – Panduan Langkah demi
  Langkah
url: /id/python/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tambahkan persegi panjang ke PDF dengan Aspose.Words – Panduan Lengkap

Pernah perlu **menambahkan persegi panjang ke PDF** tetapi tidak yakin panggilan API mana yang tepat? Anda bukan satu-satunya—para pengembang terus bertanya, “Bagaimana cara menyisipkan shape ke PDF dan tetap menjaga file tetap ringan?” Kabar baiknya, Aspose.Words membuatnya sangat mudah. Dalam tutorial ini kami akan membahas seluruh proses, mulai dari membuat dokumen PDF secara programatis hingga menata persegi panjang dengan bayangan.

Kami juga akan menambahkan beberapa hal ekstra: Anda akan belajar cara **menambahkan grafik ke PDF**, melihat langkah‑langkah tepat untuk **menyisipkan shape PDF**, dan mengakhiri dengan contoh siap‑jalankan yang **membuat PDF dengan shape**. Tanpa referensi eksternal, hanya solusi mandiri yang dapat Anda salin‑tempel hari ini.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki:

- .NET 6.0 atau lebih baru (Aspose.Words bekerja dengan .NET Standard 2.0+)
- Lisensi Aspose.Words for .NET yang valid atau kunci evaluasi sementara
- Visual Studio 2022 (atau IDE lain yang Anda sukai)
- Pengetahuan dasar C#—tidak perlu hal yang rumit, cukup kemampuan menjalankan aplikasi console

Itu saja. Jika Anda sudah memiliki semua itu, Anda siap melanjutkan.

## Langkah 1: Buat dokumen PDF secara programatis

Hal pertama yang Anda lakukan ketika ingin **menambahkan persegi panjang ke PDF** adalah memulai dokumen kosong. Anggap kelas `Document` sebagai kanvas kosong; semua yang Anda tambahkan nanti akan berada di dalamnya.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – initialise a new empty document
        Document doc = new Document();

        // The rest of the steps follow...
```

Mengapa memulai dengan dokumen kosong? Karena itu menjamin Anda memiliki kontrol penuh atas setiap elemen—tidak ada header atau footer halaman tersembunyi yang harus dihadapi kemudian.

## Langkah 2: Inisialisasi DocumentBuilder untuk menyisipkan shape PDF

`DocumentBuilder` adalah kuas menggambar Anda. Ia tahu cara menempatkan teks, gambar, dan, yang paling penting bagi kita, shape. Tanpa builder, Anda harus memanipulasi pohon node tingkat rendah secara manual—sebuah mimpi buruk bagi kebanyakan pengembang.

```csharp
        // Step 2 – create a builder that will let us add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Perhatikan bahwa kami belum menambahkan halaman apa pun. Builder akan secara otomatis membuat halaman pertama kali Anda menyisipkan sesuatu, sehingga kode tetap rapi.

## Langkah 3: Sisipkan bentuk persegi panjang – inti dari “menambahkan persegi panjang ke PDF”

Sekarang bagian yang menyenangkan: menyisipkan persegi panjang. Metode `InsertShape` mendukung puluhan nilai `ShapeType`; kami akan memilih `ShapeType.Rectangle` dan memberinya ukuran 200 × 100 poin.

```csharp
        // Step 3 – insert a rectangle (200 × 100 points) into the document
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

Pada titik ini PDF sudah berisi persegi panjang polos. Jika Anda membuka file sekarang, Anda akan melihat sebuah kotak sederhana berada di pojok kiri atas halaman pertama. Itulah dasar untuk **menambahkan grafik ke PDF**.

## Langkah 4: Gaya persegi panjang – menambahkan bayangan khusus

Persegi panjang tanpa gaya terasa membosankan. Mari beri bayangan halus sehingga ia *menonjol* saat PDF dirender. Objek `ShadowFormat` mengontrol segala hal mulai dari radius blur hingga opacity.

```csharp
        // Step 4 – configure a custom shadow for the shape
        ShadowFormat shadow = rectangle.ShadowFormat;
        shadow.Visible = true;
        shadow.BlurRadius = 8.0;          // pixels
        shadow.Distance = 5.0;           // points from the shape
        shadow.Direction = 45.0;         // degrees clockwise
        shadow.Opacity = 0.6;            // 0‑1 range
        shadow.Color = Color.Black;
```

Mengapa repot menambahkan bayangan? Selain meningkatkan estetika, bayangan dapat membantu membedakan grafik yang tumpang tindih—sesuatu yang mungkin Anda perlukan saat **menambahkan grafik ke PDF** dalam laporan yang lebih kompleks.

## Langkah 5: Simpan file – menyelesaikan alur kerja “membuat PDF dengan shape”

Baris terakhir menuliskan semuanya ke disk. Aspose.Words secara otomatis memilih versi PDF yang tepat dan menyematkan sumber daya yang diperlukan.

```csharp
        // Step 5 – save the document as a PDF file
        doc.Save(@"C:\Temp\ShapeWithShadow.pdf");
    }
}
```

Buka `ShapeWithShadow.pdf` dan Anda akan melihat persegi panjang dengan bayangan yang indah berdiri megah di halaman. Itulah seluruh alur **membuat dokumen pdf secara programatis**, dibungkus dalam kurang dari 30 baris kode.

## Contoh Kerja Penuh – membuat PDF dengan bentuk dari awal hingga selesai

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke proyek Console App baru. Ia mencakup semua pernyataan `using`, metode `Main`, dan header komentar singkat untuk referensi di masa mendatang.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectanglePdfDemo
{
    /// <summary>
    /// Demonstrates how to add a rectangle to PDF, configure a shadow,
    /// and save the result using Aspose.Words for .NET.
    /// </summary>
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create an empty PDF document
            Document doc = new Document();

            // 2️⃣ Initialise a DocumentBuilder – the tool that lets us add content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a rectangle shape (200 × 100 points) – this is the core of "add rectangle to pdf"
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

            // 4️⃣ Apply a custom shadow – makes the graphic stand out
            ShadowFormat shadow = rect.ShadowFormat;
            shadow.Visible = true;
            shadow.BlurRadius = 8.0;   // pixels
            shadow.Distance = 5.0;    // points
            shadow.Direction = 45.0;  // degrees
            shadow.Opacity = 0.6;     // semi‑transparent
            shadow.Color = Color.Black;

            // 5️⃣ Save the document – the final step in creating a PDF with shape
            string outputPath = @"C:\Temp\ShapeWithShadow.pdf";
            doc.Save(outputPath);

            Console.WriteLine($"PDF saved successfully to {outputPath}");
        }
    }
}
```

**Hasil yang diharapkan:** PDF satu halaman di mana persegi panjang 200 × 100 poin berada di dekat pojok kiri atas, dihiasi dengan bayangan lembut berderajat 45. Buka file tersebut di penampil PDF apa pun untuk memverifikasi.

## Pertanyaan Umum & Kasus Tepi

### Apakah ini bekerja dengan tipe shape lain?
Tentu saja. Ganti `ShapeType.Rectangle` dengan `ShapeType.Ellipse`, `ShapeType.Triangle`, atau salah satu dari lebih dari 150 opsi yang didukung Aspose.Words. Properti `ShadowFormat` yang sama tetap berlaku.

### Bagaimana jika saya membutuhkan persegi panjang pada halaman tertentu?
Setelah menyisipkan shape, Anda dapat memindahkannya ke halaman lain dengan menyesuaikan properti `CurrentPage` builder sebelum memanggil `InsertShape`. Contohnya:

```csharp
builder.MoveToPage(3);
Shape rectOnPage3 = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

### Bisakah saya mengubah warna isi persegi panjang?
Tentu. Gunakan properti `FillColor`:

```csharp
rect.FillColor = Color.LightBlue;
```

### Bagaimana ini memengaruhi ukuran file?
Menambahkan shape sederhana dan bayangan hanya menambah beberapa kilobyte. Jika Anda mulai menumpuk banyak grafik, pertimbangkan mengompresi gambar atau menggunakan shape berbasis vektor agar PDF tetap ringan.

### Apakah lisensi diperlukan untuk produksi?
Aspose.Words dapat berjalan dalam mode evaluasi, tetapi PDF output akan berisi watermark. Beli lisensi untuk penggunaan tanpa batas dan menghilangkan watermark.

## Tips & Trik (Tingkat Pro)

- **Penyisipan batch:** Jika Anda membutuhkan puluhan persegi panjang, lakukan loop pada koleksi koordinat dan gunakan kembali `DocumentBuilder` yang sama—kinerja tetap linear.
- **Layering:** Atur `rect.WrapType = WrapType.Inline` jika Anda ingin persegi panjang mengalir bersama teks, atau `WrapType.Square` agar teks melilit di sekitarnya.
- **Kepatuhan PDF/A:** Panggil `doc.CompatibilityOptions.OptimizeForPdfA = true;` sebelum menyimpan jika Anda memerlukan PDF yang ramah arsip.

## Ringkasan Visual

![contoh menambahkan persegi panjang ke pdf](https://example.com/rectangle-shadow.png "contoh menambahkan persegi panjang ke pdf")

Gambar ini menggambarkan tata letak PDF akhir: persegi panjang bersih dengan bayangan halus, persis seperti yang dihasilkan kode kami.

## Kesimpulan

Anda kini tahu **cara menambahkan persegi panjang ke PDF** menggunakan Aspose.Words, **cara menyisipkan shape PDF**, dan **cara menambahkan grafik ke PDF** dengan gaya khusus—semua sambil **membuat dokumen PDF secara programatis** dan menyelesaikan contoh **membuat PDF dengan shape** yang dapat Anda gunakan kembali besok.  

Selanjutnya, coba ganti persegi panjang dengan logo, atau gabungkan beberapa shape untuk membangun diagram sederhana. Anda juga dapat mengeksplorasi pembungkus teks, rotasi, atau bahkan menyematkan hyperlink di dalam shape. API ini cukup kaya untuk mengubah PDF statis menjadi laporan interaktif yang kaya grafik tanpa pernah meninggalkan C#.

Silakan bereksperimen, dan jika Anda menemui kendala, tinggalkan komentar di bawah. Selamat coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}