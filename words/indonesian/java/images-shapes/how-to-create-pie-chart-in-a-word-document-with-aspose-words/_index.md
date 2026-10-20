---
category: general
date: 2026-10-20
description: Buat diagram lingkaran dalam dokumen Word menggunakan Aspose.Words –
  panduan langkah demi langkah yang menunjukkan cara mengatur warna, memisahkan irisan,
  dan menyimpan dokumen Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save word document
- how to create chart
- how to explode slice
- how to set color
language: id
lastmod: 2026-10-20
og_description: Buat diagram pai dalam dokumen Word dengan Aspose.Words. Pelajari
  cara mengatur warna, memisahkan irisan, dan menyimpan dokumen Word dalam satu contoh
  yang dapat dijalankan.
og_image_alt: Screenshot of a Word document containing a customized pie chart with
  an exploded red slice
og_title: Buat diagram lingkaran di dokumen Word – panduan lengkap C#
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create pie chart in a Word document using Aspose.Words – step‑by‑step
    guide that shows how to set color, explode slice, and save Word document.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart automation
title: Cara membuat diagram lingkaran dalam dokumen Word dengan Aspose.Words
url: /id/java/images-shapes/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat pie chart dalam dokumen Word dengan Aspose.Words

Jika Anda perlu **membuat pie chart** di dalam file Word, panduan ini menunjukkan secara tepat cara melakukannya. Anda akan melihat cara mengatur warna khusus, meledakkan sebuah irisan untuk penekanan, dan akhirnya **menyimpan dokumen Word** dengan diagram yang disematkan.

Membuat diagram secara programatik menghilangkan langkah manual membuka Word, menyisipkan diagram, dan menyesuaikan tampilannya. Pada akhir tutorial ini Anda akan memiliki aplikasi konsol C# yang lengkap dan dapat dijalankan yang membuat pie chart, menyesuaikannya, dan menulis hasilnya ke disk.

## Prasyarat

* .NET 6.0 SDK atau yang lebih baru terinstal  
* Lisensi Aspose.Words untuk .NET yang valid (atau kunci evaluasi gratis)  
* IDE seperti Visual Studio 2022 atau VS Code  

Tidak ada paket NuGet tambahan yang diperlukan selain `Aspose.Words`.

## Cara membuat pie chart dalam dokumen Word

Langkah pertama adalah menginstansiasi sebuah `Document` dan `DocumentBuilder`. Builder memberikan Anda akses ke fitur Word tingkat tinggi, termasuk penyisipan diagram.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a blank document and a builder.
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Step 2: Insert a 400x300‑point pie chart.
            Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data.
            // Series 0, Category 0‑2 correspond to three slices.
            pieChart.Series[0].DataPoints.Clear();
            pieChart.Series[0].DataPoints.Add(30); // Slice A
            pieChart.Series[0].DataPoints.Add(45); // Slice B
            pieChart.Series[0].DataPoints.Add(25); // Slice C

            // The chart is now part of the document; further customization follows.
```

Pada titik ini dokumen sudah berisi pie chart dasar. Bagian selanjutnya menjelaskan **cara meledakkan irisan**, **cara mengatur warna**, dan **cara menyimpan dokumen Word**.

## Cara meledakkan irisan untuk penekanan

Meleledakkan sebuah irisan memisahkannya dari sisa pie, menarik perhatian pembaca. API Aspose.Words memungkinkan Anda menentukan jarak ledakan dalam poin.

```csharp
            // Step 3: Explode the first slice (index 0) by 20 points.
            // This moves the slice outward while keeping the rest of the chart intact.
            pieChart.Series[0].SetExplosion(0, 20);
```

Mengapa meledakkan irisan? Dalam laporan yang menyoroti kategori tertentu—seperti “Produk terlaris”—pemisahan visual membuat titik data langsung dikenali.

## Cara mengatur warna pada irisan diagram

Warna khusus meningkatkan konsistensi merek dan keterbacaan. Anda dapat menetapkan `System.Drawing.Color` apa pun ke titik data tertentu.

```csharp
            // Step 4: Apply a red fill to the same slice we just exploded.
            // The Fill property controls the interior color of the slice.
            pieChart.Series[0].DataPoints[0].Fill.ForeColor = Color.Red;
```

Anda tidak terbatas pada warna yang telah ditentukan; Anda dapat membuat nilai `Color.FromArgb` untuk nuansa yang tepat.

## Cara menyimpan dokumen Word dengan diagram

Setelah diagram terlihat seperti yang Anda inginkan, menyimpan file menjadi sederhana. Metode `Document.Save` menulis dokumen dalam format yang Anda tentukan—di sini kami menggunakan `.docx` default.

```csharp
            // Step 5: Save the document to the desired location.
            string outputPath = @"C:\Temp\PieChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Menjalankan program menghasilkan `PieChart.docx`. Membuka file di Microsoft Word menampilkan pie chart di mana irisan pertama meledak dan berwarna merah, persis seperti yang ditentukan dalam kode.

### Hasil yang diharapkan

* File Word bernama **PieChart.docx** di `C:\Temp`.  
* Dokumen berisi satu pie chart, berukuran 400 × 300 poin.  
* Irisan 0 dipindahkan sebesar 20 poin dan diisi dengan merah, sementara irisan lain tetap menggunakan warna default.  

Anda dapat memverifikasi ledakan dan warna dengan memilih diagram di Word dan memeriksa properti irisan.

## Tips profesional dan jebakan umum

* **Tips pro:** Jika Anda perlu mengubah judul diagram atau legenda, gunakan properti `pieChart.Title.Text` dan `pieChart.Legend` sebelum menyimpan.  
* **Waspadai:** Lupa membersihkan titik data default dapat menyebabkan irisan tambahan yang tidak diinginkan. Selalu panggil `Series[0].DataPoints.Clear()` sebelum menambahkan data Anda sendiri.  
* **Tips kinerja:** Untuk dokumen besar, gunakan kembali satu instance `DocumentBuilder` alih-alih membuat banyak builder; ini mengurangi beban memori.

## Cara membuat diagram menggunakan Aspose.Words (konteks tambahan)

Metode `InsertChart` mendukung banyak tipe diagram selain pie chart, seperti diagram kolom, garis, dan area. Untuk beralih ke tipe lain, ganti `ChartType.Pie` dengan nilai enum yang diinginkan, misalnya `ChartType.Column`. Langkah-langkah penyesuaian lainnya (meledakkan irisan, mengatur warna) mengikuti pola yang sama, meskipun tidak semua tipe diagram memiliki properti “explosion”.

## Cara meledakkan irisan pada tipe diagram lain

Hanya diagram tipe pie yang menyediakan metode `SetExplosion`. Jika Anda mencoba memanggilnya pada diagram batang, API akan melempar `ArgumentException`. Dalam kasus tersebut, pertimbangkan menggunakan label data atau callout untuk menyoroti batang tertentu.

## Cara mengatur warna pada seri alih-alih satu irisan

Jika Anda ingin setiap irisan dalam sebuah seri memiliki warna yang sama, lakukan loop pada titik data:

```csharp
foreach (ChartDataPoint point in pieChart.Series[0].DataPoints)
{
    point.Fill.ForeColor = Color.Blue;
}
```

Pendekatan ini berguna ketika Anda memerlukan skema warna seragam di beberapa diagram.

## Cara menyimpan dokumen Word dalam format lain

Aspose.Words dapat mengekspor ke PDF, HTML, dan banyak format lainnya. Ubah ekstensi file dalam `Save` dan opsional berikan objek `SaveOptions`:

```csharp
document.Save(@"C:\Temp\PieChart.pdf", SaveFormat.Pdf);
```

Mesin rendering diagram secara otomatis mengonversi diagram ke format target, mempertahankan warna dan pengaturan ledakan.

## Kesimpulan

Anda kini tahu cara **membuat pie chart** dalam dokumen Word, menyesuaikan tampilannya dengan **meledakkan irisan** dan **mengatur warna**, serta akhirnya **menyimpan dokumen Word** dengan diagram yang disematkan. Contoh end‑to‑end ini memberi Anda dasar yang kuat untuk mengotomatisasi pembuatan laporan, dasbor, atau skenario apa pun di mana data visual perlu disisipkan secara programatik.

### Langkah selanjutnya

* Jelajahi tipe diagram lain (`ChartType.Column`, `ChartType.Line`) untuk memperluas toolkit pelaporan Anda.  
* Gabungkan beberapa diagram dalam satu dokumen untuk membangun dasbor komprehensif.  
* Bereksperimen dengan `ChartDataLabel` untuk menampilkan persentase atau nilai langsung pada irisan.  

Silakan sesuaikan kode dengan sumber data Anda sendiri—baik Anda mengambil nilai dari basis data, API, atau file CSV, alur kerja Aspose.Words yang sama berlaku. Selamat membuat diagram!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Melelehkan Irisan Pie Chart di C# dengan Aspose.Words – Panduan Lengkap](/words/english/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/)
- [Sisipkan Diagram Kolom Kustom dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/programming-with-charts/insert-custom-chart/)
- [Perbarui Data Seri Diagram dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}