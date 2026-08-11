---
category: general
date: 2026-08-10
description: Buat dokumen Word berisi diagram pai menggunakan Aspose.Words. Pelajari
  cara menyisipkan diagram, menyesuaikan warna diagram pai, dan mengubah warna irisan
  diagram pai di C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- customize pie chart colors
- how to style pie
- how to insert chart
- change pie slice color
language: id
lastmod: 2026-08-10
og_description: Buat dokumen Word dengan diagram pai menggunakan Aspose.Words. Panduan
  ini menjelaskan cara menyisipkan diagram, menyesuaikan warna diagram pai, dan mengubah
  warna irisan pai dalam aplikasi C#.
og_image_alt: Screenshot of a Word document containing a styled pie chart generated
  by Aspose.Words
og_title: Buat diagram lingkaran di dokumen Word – Panduan Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create pie chart Word document using Aspose.Words. Learn how to insert
    chart, customize pie chart colors, and change pie slice color in C#.
  headline: Create pie chart Word document with Aspose.Words
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, .NET
      6, and later. Just reference the same NuGet package.
    question: Does this work with .NET Core?
  - answer: Replace `ChartType.Pie` with `ChartType.Doughnut`. The same styling APIs
      (`Explosion`, `ForeColor`) apply.
    question: What if I need a donut chart instead of a pie?
  - answer: Open the existing file with `new Document("Existing.docx")`, create a
      `DocumentBuilder` for that document, and call `InsertChart` at the desired cursor
      position.
    question: Can I insert the chart into an existing document?
  - answer: 'Pie charts are best for a limited number of categories (typically < 10).
      For many categories, consider a bar or column chart instead. ## Full source
      code recap Below is the complete program in one block for easy copy‑paste: ```csharp
      using System; using System.Drawing; using Aspose.Words; using Aspo'
    question: How do I handle large datasets?
  type: FAQPage
tags:
- Aspose.Words
- C#
- pie chart
title: Buat dokumen Word diagram lingkaran dengan Aspose.Words
url: /id/net/programming-with-charts/create-pie-chart-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen Word diagram pai dengan Aspose.Words

Jika Anda perlu **membuat dokumen Word diagram pai** secara programatis, tutorial ini menunjukkan secara tepat cara melakukannya. Kami akan membahas cara menyisipkan diagram, **menyesuaikan warna diagram pai**, dan **mengubah warna irisan pai** menggunakan Aspose.Words untuk .NET.

Anda akan melihat contoh lengkap yang dapat dijalankan yang dapat Anda salin ke Visual Studio, jalankan, dan langsung membuka *.docx* yang dihasilkan untuk memverifikasi diagram pai yang bergaya. Tidak diperlukan dokumentasi eksternal—semua yang Anda butuhkan ada dalam panduan ini.

## Prasyarat

Sebelum Anda memulai, pastikan Anda memiliki:

* .NET 6.0 SDK atau yang lebih baru terpasang  
* Lisensi Aspose.Words untuk .NET yang valid (atau kunci evaluasi sementara)  
* Visual Studio 2022 (atau IDE C# apa pun)  

Kode hanya menggunakan namespace `Aspose.Words` dan `Aspose.Words.Drawing.Charts`, jadi tidak diperlukan paket NuGet tambahan selain pustaka Aspose.Words.

## Buat dokumen Word diagram pai – contoh lengkap

Program C# berikut membuat dokumen Word baru, menyisipkan diagram pai, memberi gaya pada dua irisan pertama, dan menyimpan file. Setiap langkah dijelaskan secara detail.

```csharp
using System;
using System.Drawing;                // For Color
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Initialize a blank document and a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a pie chart of size 400x300 points.
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            // Step 3: Populate the chart with sample data (optional but makes the chart visible).
            // Aspose.Words creates an empty series by default; we add a series with three values.
            chart.Series.Clear(); // Remove the default empty series.
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30); // Slice 1
            series.DataPoints.Add(45); // Slice 2
            series.DataPoints.Add(25); // Slice 3

            // Step 4: Explode the first slice to emphasize it.
            series.Points[0].Explosion = 20; // 20% explosion makes the slice pop out.

            // Step 5: **Customize pie chart colors** – set the first two slices.
            series.Points[0].Format.Fill.ForeColor = Color.Orange; // Slice 1 color
            series.Points[1].Format.Fill.ForeColor = Color.Green;  // Slice 2 color

            // Step 6: **Change pie slice color** for any additional slices if needed.
            // Example: set the third slice to a custom blue.
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            // Step 7: Save the document containing the styled pie chart.
            string outputPath = @"PieChartStyled.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Penjelasan setiap langkah

| Langkah | Apa yang dilakukan | Mengapa penting |
|------|--------------|----------------|
| **1** | Membuat `Document` baru dan `DocumentBuilder`. | `DocumentBuilder` menyediakan metode fluently untuk menyisipkan konten, seperti diagram, ke dalam file Word. |
| **2** | Memanggil `InsertChart` dengan `ChartType.Pie` dan ukuran tetap. | `InsertChart` adalah metode **cara menyisipkan diagram**; menentukan lebar/tinggi memastikan diagram pas dengan baik pada halaman. |
| **3** | Menambahkan seri data dengan tiga kategori dan nilai numerik. | Diagram pai tanpa data tidak terlihat; mengisinya memperlihatkan langkah-langkah styling. |
| **4** | Mengatur `Explosion` pada titik pertama. | Meledakkan sebuah irisan menarik perhatian ke segmen tertentu—berguna untuk menyoroti data utama. |
| **5** | Mengatur `ForeColor` untuk dua titik pertama. | Ini adalah inti dari **menyesuaikan warna diagram pai**; Anda dapat menggunakan `System.Drawing.Color` apa pun. |
| **6** | Menunjukkan cara **mengubah warna irisan pai** untuk irisan tambahan. | Menunjukkan bahwa styling tidak terbatas pada dua irisan pertama; Anda dapat memberi warna pada setiap irisan secara individual. |
| **7** | Menyimpan dokumen sebagai `PieChartStyled.docx`. | Output akhir dapat dibuka di Microsoft Word, Google Docs, atau penampil kompatibel lainnya. |

#### Output yang diharapkan

Membuka `PieChartStyled.docx` menampilkan satu halaman dengan diagram pai 400 × 300 pt:

* Irisan 1 (oranye) meledak ke luar.  
* Irisan 2 (hijau) muncul bersebelahan dengan irisan yang meledak.  
* Irisan 3 (biru‑baja) mengisi segmen yang tersisa.

Diagram mencerminkan nilai data (30, 45, 25) dan warna khusus yang Anda tentukan.

## Cara menata pai – tips tambahan

* **Gunakan warna tema** – alih-alih menuliskan langsung `Color.Orange`, Anda dapat mengambil warna dari tema dokumen:  
  ```csharp
  chart.Series[0].Points[0].Format.Fill.ForeColor = doc.Theme.ColorScheme.Accent1;
  ```
* **Tambahkan label data** – jika Anda ingin persentase ditampilkan pada diagram:  
  ```csharp
  chart.HasDataLabel = true;
  chart.DataLabel.NumberFormat = "#%";
  ```
* **Ubah ukuran secara dinamis** – hitung ukuran diagram berdasarkan margin halaman:  
  ```csharp
  double width = doc.PageSetup.PageWidth - doc.PageSetup.LeftMargin - doc.PageSetup.RightMargin;
  double height = width * 0.75; // 4:3 aspect ratio
  builder.InsertChart(ChartType.Pie, width, height);
  ```

Variasi ini menunjukkan fleksibilitas **cara menata pai** di luar contoh dasar.

## Pertanyaan umum terjawab

**Q: Apakah ini bekerja dengan .NET Core?**  
A: Ya. Aspose.Words untuk .NET kompatibel dengan .NET Core, .NET 5, .NET 6, dan versi selanjutnya. Cukup referensikan paket NuGet yang sama.

**Q: Bagaimana jika saya membutuhkan diagram donat alih-alih pai?**  
A: Ganti `ChartType.Pie` dengan `ChartType.Doughnut`. API styling yang sama (`Explosion`, `ForeColor`) tetap berlaku.

**Q: Bisakah saya menyisipkan diagram ke dalam dokumen yang sudah ada?**  
A: Buka file yang ada dengan `new Document("Existing.docx")`, buat `DocumentBuilder` untuk dokumen tersebut, dan panggil `InsertChart` pada posisi kursor yang diinginkan.

**Q: Bagaimana cara menangani dataset besar?**  
A: Diagram pai paling cocok untuk sejumlah kategori terbatas (biasanya < 10). Untuk banyak kategori, pertimbangkan diagram batang atau kolom sebagai gantinya.

## Ringkasan kode sumber lengkap

Berikut adalah program lengkap dalam satu blok untuk memudahkan salin‑tempel:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            chart.Series.Clear();
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30);
            series.DataPoints.Add(45);
            series.DataPoints.Add(25);

            series.Points[0].Explosion = 20;
            series.Points[0].Format.Fill.ForeColor = Color.Orange;
            series.Points[1].Format.Fill.ForeColor = Color.Green;
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            doc.Save("PieChartStyled.docx");
            Console.WriteLine("Document saved as PieChartStyled.docx");
        }
    }
}
```

Menjalankan kode ini menghasilkan dokumen Word diagram pai yang bergaya seperti yang dijelaskan sebelumnya.

## Kesimpulan

Anda sekarang tahu cara **membuat dokumen Word diagram pai** menggunakan Aspose.Words, **menyesuaikan warna diagram pai**, dan **mengubah warna irisan pai** secara programatis. Panduan ini mencakup penyisipan diagram, mengisi data, meledakkan sebuah irisan, menerapkan warna khusus, dan menyimpan hasilnya.  

Dari sini Anda dapat menjelajahi topik terkait seperti **cara menyisipkan diagram** jenis selain pai, menambahkan legenda, atau menghasilkan laporan multi‑halaman dengan banyak diagram. Bereksperimenlah dengan skema warna dan set data yang berbeda untuk memenuhi kebutuhan pelaporan Anda.

Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan menjelajahi pendekatan implementasi alternatif dalam proyek Anda.

- [Sisipkan Diagram Kolom di Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Sisipkan Diagram Area di Dokumen Word | Aspose.Words untuk .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Buat Diagram Sebar Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}