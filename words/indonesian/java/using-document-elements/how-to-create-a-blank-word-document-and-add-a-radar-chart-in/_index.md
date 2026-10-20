---
category: general
date: 2026-09-21
description: Buat dokumen Word kosong dan pelajari cara menyisipkan diagram radar
  dalam file Word menggunakan DocumentBuilder – panduan langkah demi langkah.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert radar chart
- insert chart word file
- generate word document chart
- add radial chart word
language: id
lastmod: 2026-09-21
og_description: Buat dokumen Word kosong dan sisipkan diagram radar dalam file Word
  dengan Aspose.Words. Ikuti tutorial ini untuk menghasilkan diagram dokumen Word
  dengan cepat.
og_image_alt: Screenshot showing a blank Word document with a radar chart inserted
og_title: Buat dokumen Word kosong dan tambahkan diagram radar – panduan lengkap C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  headline: How to create a blank Word document and add a radar chart in C#
  type: TechArticle
- description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  name: How to create a blank Word document and add a radar chart in C#
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET (NuGet package `Aspose.Words` version 23.9 or newer). * Basic familiarity
      with C# and Visual Studio or your preferred IDE.'
  - name: Expected output
    text: '* A `RadialChartExample.docx` file on your desktop. * The first page contains
      a radar chart with five data points labeled “Series 1”. * No additional text
      appears because the document started blank.'
  - name: 1. Changing chart size after insertion
    text: 'If the initial dimensions don’t fit your layout, resize the chart like
      this:'
  - name: 2. Inserting the chart into a specific location
    text: You can move the builder’s cursor to a bookmark, table cell, or paragraph
      before calling `InsertChart`.
  - name: 3. Customizing chart appearance
    text: Aspose.Words exposes the full chart object model, allowing you to set titles,
      axis labels, and colors.
  - name: 4. Dealing with missing fonts
    text: 'If the target environment lacks a font used in the chart, Aspose.Words
      substitutes a default font. To guarantee consistency, embed the required fonts:'
  - name: 5. Exporting to other formats
    text: 'The same document can be saved as PDF, HTML, or PNG without extra code
      changes:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart generation
title: Cara membuat dokumen Word kosong dan menambahkan diagram radar di C#
url: /id/java/using-document-elements/how-to-create-a-blank-word-document-and-add-a-radar-chart-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat dokumen Word kosong dan menambahkan diagram radar di C#

Jika Anda perlu **membuat dokumen Word kosong** dan menyematkan diagram radar (radial), tutorial ini menyediakan solusi siap‑jalankan. Anda akan melihat cara menggunakan Aspose.Words .NET untuk menghasilkan file, menyisipkan diagram, dan menyimpan hasilnya—semua dalam beberapa langkah singkat.

Dokumen kosong menyediakan kanvas bersih untuk skenario pelaporan otomatis apa pun, dan menambahkan diagram radar memungkinkan Anda memvisualisasikan data multidimensi langsung di dalam Word. Pada akhir panduan ini Anda akan dapat menghasilkan diagram dokumen Word tanpa penyuntingan manual.

## Apa yang akan Anda pelajari

* Cara **membuat dokumen Word kosong** secara programatis dengan C#.
* Kode tepat untuk **menyisipkan diagram radar** menggunakan `DocumentBuilder`.
* Cara **menyisipkan diagram ke file Word** dan menyesuaikan ukurannya.
* Cara **menghasilkan diagram dokumen Word** dan memverifikasi outputnya.
* Tips untuk **menambahkan file diagram radial ke Word**, termasuk jebakan umum.

### Prasyarat

* .NET 6.0 atau lebih baru (kode ini juga berfungsi dengan .NET Framework 4.6+).
* Aspose.Words untuk .NET (paket NuGet `Aspose.Words` versi 23.9 atau lebih baru).
* Familiaritas dasar dengan C# dan Visual Studio atau IDE pilihan Anda.

## Membuat dokumen Word kosong dengan C#

Langkah pertama adalah menginstansiasi objek `Document` yang kosong. Objek ini mewakili file `.docx` yang sepenuhnya kosong.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Step 1: Create a new blank document
Document doc = new Document();
```

`Document` membuat struktur file tetapi belum berisi bagian atau halaman apa pun. Aspose.Words secara otomatis menambahkan bagian default ketika Anda mulai menambahkan konten, sehingga langkah berikutnya berfungsi tanpa konfigurasi tambahan.

## Cara menyisipkan diagram radar ke dalam file Word

Diagram radar (juga disebut diagram radial) memvisualisasikan titik data pada sumbu yang memancar dari titik pusat. Aspose.Words menyediakan `DocumentBuilder.insertChart` untuk tujuan ini.

```csharp
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);

// Step 3: Insert a radar (radial) chart with the desired size (width: 400pt, height: 300pt)
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`InsertChart` mengembalikan objek `Chart` yang dapat Anda konfigurasikan lebih lanjut. Diagram muncul pada halaman pertama dokumen kosong karena builder berada pada posisi awal dokumen secara default.

## Menyisipkan diagram ke dalam file Word – menambahkan seri data

Diagram tanpa data tidak terlihat. Isi diagram radar dengan satu atau lebih seri agar menjadi bermakna.

```csharp
// Step 4: Populate the chart with series data
ChartSeries series = radarChart.Series.Add("Series 1");

// Add data points (example values)
series.DataPoints.Add(4);
series.DataPoints.Add(7);
series.DataPoints.Add(3);
series.DataPoints.Add(6);
series.DataPoints.Add(5);
```

Anda dapat menambahkan sebanyak seri yang diperlukan. Setiap seri dapat memiliki nama yang berbeda, yang akan muncul di legenda diagram. Titik data berkorespondensi dengan sumbu radial; urutan penambahannya menentukan posisi mereka di sekitar lingkaran.

## Menghasilkan diagram dokumen Word – menyimpan file

Setelah membangun diagram, simpan dokumen ke disk. Pilih lokasi yang Anda miliki hak tulisnya.

```csharp
// Step 5: Save the document containing the radar chart
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), 
                                 "RadialChartExample.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Saat Anda membuka file `.docx` yang dihasilkan di Microsoft Word, Anda akan melihat halaman kosong dengan diagram radar berukuran 400 × 300 poin, terisi dengan data contoh.

### Output yang diharapkan

* File `RadialChartExample.docx` di desktop Anda.
* Halaman pertama berisi diagram radar dengan lima titik data berlabel “Series 1”.
* Tidak ada teks tambahan karena dokumen dimulai dari keadaan kosong.

## Menambahkan diagram radial ke Word – menangani kasus tepi umum

### 1. Mengubah ukuran diagram setelah penyisipan

Jika dimensi awal tidak cocok dengan tata letak Anda, ubah ukuran diagram seperti ini:

```csharp
radarChart.Width = 500;   // width in points
radarChart.Height = 350;  // height in points
```

### 2. Menyisipkan diagram ke lokasi tertentu

Anda dapat memindahkan kursor builder ke bookmark, sel tabel, atau paragraf sebelum memanggil `InsertChart`.

```csharp
builder.MoveToBookmark("ChartLocation");
Chart chartInTable = builder.InsertChart(ChartType.Radar, 350, 250);
```

### 3. Menyesuaikan tampilan diagram

Aspose.Words mengekspos model objek diagram lengkap, memungkinkan Anda mengatur judul, label sumbu, dan warna.

```csharp
radarChart.Title.Text = "Sales Performance";
radarChart.Series[0].FillFormat.ForeColor = System.Drawing.Color.Blue;
radarChart.AxisX.Title.Text = "Quarter";
radarChart.AxisY.Title.Text = "Revenue (M)";
```

### 4. Menangani font yang hilang

Jika lingkungan target tidak memiliki font yang digunakan dalam diagram, Aspose.Words akan menggantinya dengan font default. Untuk menjamin konsistensi, sematkan font yang diperlukan:

```csharp
doc.FontSettings.SubstitutionSettings.DefaultFontName = "Arial";
```

### 5. Mengekspor ke format lain

Dokumen yang sama dapat disimpan sebagai PDF, HTML, atau PNG tanpa perubahan kode tambahan:

```csharp
doc.Save("RadialChartExample.pdf");
```

## Contoh lengkap yang dapat dijalankan

Menggabungkan semua bagian memberikan Anda satu program yang dapat Anda salin, tempel, dan jalankan.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class RadarChartDemo
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();

        // Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a radar chart (400pt x 300pt)
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

        // Add a data series with sample values
        ChartSeries series = radarChart.Series.Add("Quarterly Sales");
        series.DataPoints.Add(4);
        series.DataPoints.Add(7);
        series.DataPoints.Add(3);
        series.DataPoints.Add(6);
        series.DataPoints.Add(5);

        // Optional: customize appearance
        radarChart.Title.Text = "Quarterly Sales Radar";
        radarChart.AxisX.Title.Text = "Quarter";
        radarChart.AxisY.Title.Text = "Units Sold";

        // Save the document
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialChartExample.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Jalankan program ini, buka file yang dihasilkan, dan Anda akan melihat diagram radar profesional siap didistribusikan.

## Kesimpulan

Anda kini tahu cara **membuat dokumen Word kosong**, **menyisipkan diagram radar**, dan **menghasilkan diagram dokumen Word** menggunakan Aspose.Words. Dengan mengikuti langkah‑langkah di atas Anda juga dapat **menambahkan file diagram radial ke Word** ke dalam pipeline pelaporan otomatis apa pun, menyesuaikan ukuran, gaya, dan mengekspor ke format tambahan.

**Langkah selanjutnya**

* Jelajahi tipe diagram lain (`ChartType.Column`, `ChartType.Pie`) untuk memperluas toolkit pelaporan Anda.
* Gabungkan beberapa diagram pada satu halaman dengan memanggil `InsertChart` berulang kali.
* Integrasikan data dari basis data atau file CSV untuk mengisi seri secara dinamis.
* Tinjau dokumentasi Aspose.Words untuk opsi pemformatan lanjutan seperti label data bersyarat dan templat diagram.

Silakan bereksperimen dengan kode, sesuaikan dimensi, atau ganti data contoh dengan metrik bisnis nyata. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Menyisipkan Diagram Kolom di Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Membuat Diagram Scatter di Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Menyisipkan Diagram Bubble di Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}