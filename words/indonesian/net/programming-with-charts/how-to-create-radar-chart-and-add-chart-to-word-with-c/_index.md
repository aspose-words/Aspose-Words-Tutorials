---
category: general
date: 2026-09-05
description: Buat diagram radar di Word menggunakan C#. Pelajari cara menghasilkan
  dokumen Word kosong, menambahkan diagram radar, mengatur ukuran diagram, dan mengaktifkan
  tanda skala dengan cepat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radar chart
- add chart to word
- add radar chart
- generate blank word document
- set chart size word
language: id
lastmod: 2026-09-05
og_description: Buat diagram radar di Word menggunakan C#. Panduan ini menunjukkan
  cara membuat dokumen Word kosong, menambahkan diagram radar, mengatur ukuran diagram,
  dan mengaktifkan tanda penanda—semua dalam hitungan menit.
og_image_alt: Screenshot of a Word document with a created radar chart
og_title: Buat diagram radar di Word – panduan C# langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create radar chart in Word using C#. Learn to generate a blank Word
    document, add a radar chart, set chart size, and enable tick marks quickly.
  headline: How to create radar chart and add chart to Word with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Chart
- Word automation
title: Cara membuat diagram radar dan menambahkan diagram ke Word dengan C#
url: /id/net/programming-with-charts/how-to-create-radar-chart-and-add-chart-to-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat radar chart dan menambahkan chart ke Word dengan C#

Jika Anda perlu **create radar chart** di dalam file Word, panduan ini akan memandu Anda melalui seluruh proses. Anda akan belajar cara **generate blank word document**, menyisipkan radar chart, **set chart size word**, dan mengaktifkan graduasi sumbu—semua dengan beberapa baris kode C#.

Menambahkan data visual ke laporan adalah kebutuhan umum, dan menggunakan Aspose.Words membuatnya mudah. Pada langkah-langkah di bawah ini kami juga membahas cara **add chart to word** dokumen secara programatis, sehingga Anda dapat mengotomatisasi dasbor, ringkasan keuangan, atau konten berbasis data apa pun.

## Prasyarat

* .NET 6.0 atau yang lebih baru terinstal  
* Lisensi Aspose.Words untuk .NET (atau percobaan gratis) – perpustakaan menyediakan `Document`, `DocumentBuilder`, dan API chart yang digunakan dalam tutorial ini  
* Visual Studio 2022 (atau IDE C# apa pun)  

> **Pro tip:** Jika Anda sedang menguji, letakkan DLL Aspose.Words di folder `bin` proyek Anda dan referensikan melalui NuGet (`Install-Package Aspose.Words`).

## Cara membuat radar chart dalam dokumen Word

Langkah pertama adalah **generate blank word document** yang akan menampung chart. Ini memberi Anda kanvas bersih dan memungkinkan Anda mengontrol metadata dokumen sebelum konten apa pun ditambahkan.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// 1️⃣ Create an empty Word document
Document document = new Document();   // this is a blank .docx file
```

*Mengapa ini penting:* Objek `Document` yang kosong memastikan tidak ada gaya atau bagian tersembunyi yang mengganggu tata letak chart. Ini juga memungkinkan Anda mengatur properti dokumen (penulis, judul) nanti jika diperlukan.

## Cara menambahkan chart ke Word menggunakan Aspose.Words

Selanjutnya, buat `DocumentBuilder`. Builder adalah mesin kerja yang memungkinkan Anda menyisipkan teks, gambar, dan chart ke dalam dokumen.

```csharp
// 2️⃣ Initialize a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

Sekarang Anda dapat **add radar chart** langsung di tempat kursor berada. Metode `InsertChart` menerima enum `ChartType`, lebar, dan tinggi dalam poin.

```csharp
// 3️⃣ Insert a radar (radial) chart with a specific size
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

*Mengapa 400 × 300?* Dimensi ini memberikan chart yang jelas dan dapat dibaca pada halaman A4 standar. Anda dapat menyesuaikan ukuran nanti dengan langkah **set chart size word** jika tata letak Anda memerlukan rasio aspek yang berbeda.

## Mengatur ukuran chart di Word

Jika Anda perlu menyesuaikan ukuran secara halus setelah penyisipan, Anda dapat memodifikasi properti `Width` dan `Height` chart. Ini berguna ketika teks di sekitar atau margin halaman menentukan keseimbangan visual yang berbeda.

```csharp
// 4️⃣ Adjust chart dimensions (optional)
// radarChart.Width = 500;   // width in points
// radarChart.Height = 350;  // height in points
```

> **Catatan:** Overload `InsertChart` sudah mengatur ukuran, jadi kode di atas bersifat opsional dan ditampilkan untuk melengkapi.

## Mengaktifkan tick marks pada sumbu radial

Diagram radar paling berguna ketika sumbu radial menampilkan graduasi yang jelas. Pengaturan berikut mengaktifkan tick marks dan menetapkan interval menjadi 30 derajat, yang sesuai dengan tampilan radar gaya kompas tipikal.

```csharp
// 5️⃣ Turn on graduations (tick marks) and set interval
radarChart.AxisX.HasGraduations = true;      // show tick marks
radarChart.AxisX.GraduationInterval = 30;   // every 30 degrees
```

*Mengapa ini penting:* Graduasi membantu pembaca menilai nilai pada setiap sudut, meningkatkan keterbacaan bagi pemangku kepentingan yang tidak familiar dengan data.

## Simpan dokumen yang berisi chart

Akhirnya, tulis dokumen ke disk. Anda dapat memilih folder mana saja; pastikan jalur tersebut ada.

```csharp
// 6️⃣ Save the Word file
document.Save(@"C:\Temp\RadialChart.docx");
```

Saat Anda membuka `RadialChart.docx` di Microsoft Word, Anda akan melihat radar chart yang sepenuhnya dirender, terpusat di halaman, berukuran sesuai yang ditentukan, dengan tick marks setiap 30 derajat.

### Output yang Diharapkan

* File `.docx` bernama **RadialChart.docx**  
* Halaman pertama berisi radar chart berukuran 400 × 300 poin  
* Sumbu X (sumbu radial) menampilkan tick marks pada 0°, 30°, 60°, …, 330°  

Anda sekarang dapat mengganti seri data placeholder dengan nilai Anda sendiri dengan mengakses `radarChart.Series` – tetapi itu di luar cakupan tutorial dasar **add radar chart** ini.

## Variasi umum dan kasus tepi

| Scenario | Adjustment |
|----------|------------|
| **Different chart type** | Ganti `ChartType.Radar` dengan `ChartType.Column`, `ChartType.Pie`, dll. |
| **Multiple charts** | Panggil `InsertChart` berulang kali; setiap pemanggilan menempatkan chart baru setelah yang sebelumnya. |
| **Large data sets** | Gunakan `radarChart.Series[0].DataPoints.AddDataPointForBarSeries(value)` untuk mengisi banyak poin. |
| **Saving as PDF** | Panggil `document.Save("RadialChart.pdf", SaveFormat.Pdf);` setelah chart ditambahkan. |
| **Running on .NET Core** | Pastikan Anda mereferensikan paket `Aspose.Words.NETCore`; penggunaan API identik. |

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke aplikasi konsol. Program ini mencakup semua langkah, penyesuaian ukuran opsional, dan komentar untuk kejelasan.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace RadarChartDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Generate a blank Word document
            Document document = new Document();

            // 2️⃣ Create a builder to work with the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3️⃣ Insert a radar chart (400 × 300 points)
            Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

            // 4️⃣ (Optional) Change chart size if needed
            // radarChart.Width = 500;
            // radarChart.Height = 350;

            // 5️⃣ Enable tick marks on the radial axis
            radarChart.AxisX.HasGraduations = true;          // show tick marks
            radarChart.AxisX.GraduationInterval = 30;       // every 30 degrees

            // 6️⃣ Populate the chart with sample data (optional)
            radarChart.Series[0].DataPoints.Clear();
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(10);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(20);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(30);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(40);

            // 7️⃣ Save the document
            string outputPath = @"C:\Temp\RadialChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Jalankan program, buka file yang dihasilkan, dan Anda akan melihat radar chart persis seperti yang dijelaskan.

## Kesimpulan

Anda kini tahu cara **create radar chart** dan **add chart to Word** dokumen menggunakan C#. Tutorial ini mencakup pembuatan **blank word document**, menyisipkan radar chart, **set chart size word**, dan mengaktifkan graduasi sumbu. Dengan dasar ini Anda dapat memperluas solusi ke beberapa chart, seri data khusus, atau mengekspor ke PDF.

### Langkah Selanjutnya

* Jelajahi tipe chart lain dengan `ChartType` (mis., `Bar`, `Line`) – lihat kata kunci **add radar chart** untuk contoh terkait.

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Sisipkan Diagram Scatter dalam Dokumen Word](/words/english/net/programming-with-charts/insert-scatter-chart/)
- [Sisipkan Diagram Kolom di Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Sembunyikan Sumbu Diagram dalam Dokumen Word](/words/english/net/programming-with-charts/hide-chart-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}