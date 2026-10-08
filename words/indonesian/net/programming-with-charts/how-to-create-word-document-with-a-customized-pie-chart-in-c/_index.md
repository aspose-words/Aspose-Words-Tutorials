---
category: general
date: 2026-10-07
description: Pelajari cara membuat dokumen Word dan menyisipkan diagram lingkaran
  menggunakan Aspose.Words di C#. Panduan ini juga menunjukkan cara menghasilkan file
  Word dengan label diagram khusus.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- generate word file
- customize pie chart
- how to add pie chart
language: id
lastmod: 2026-10-07
og_description: Buat dokumen Word dan sisipkan diagram lingkaran di C#. Ikuti panduan
  langkah demi langkah ini untuk menghasilkan file Word dengan label diagram yang
  sepenuhnya disesuaikan.
og_image_alt: Screenshot of a Word document that contains a customized pie chart created
  with C#
og_title: Buat dokumen Word dengan diagram lingkaran yang disesuaikan di C#
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to create word document and insert pie chart using Aspose.Words
    in C#. The guide also shows how to generate word file with custom chart labels.
  headline: How to create word document with a customized pie chart in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart
title: Cara membuat dokumen Word dengan diagram pai yang disesuaikan di C#
url: /id/net/programming-with-charts/how-to-create-word-document-with-a-customized-pie-chart-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat dokumen Word dengan diagram pai yang disesuaikan di C#

Jika Anda perlu **membuat dokumen Word** secara programatis, tutorial ini menunjukkan cara **menyisipkan diagram pai** dan menyesuaikan label data-nya menggunakan Aspose.Words untuk .NET. Anda juga akan belajar cara **menghasilkan file Word** yang berisi diagram yang sepenuhnya bergaya, mencakup semua hal mulai dari penyiapan proyek hingga menyimpan dokumen akhir.

Panduan ini menjelaskan setiap langkah yang diperlukan untuk menambahkan diagram, menyesuaikan posisi label, mengaktifkan garis penghubung, dan akhirnya menyimpan hasilnya sebagai file `.docx`. Tidak ada alat eksternal yang diperlukan selain pustaka Aspose.Words, dan kode sumber lengkap disediakan sehingga Anda dapat menyalin, menempel, dan menjalankannya secara langsung.

## Prasyarat

* .NET 6.0 SDK atau yang lebih baru terpasang  
* Lisensi Aspose.Words untuk .NET yang valid (atau kunci evaluasi gratis)  
* IDE seperti Visual Studio 2022 atau Visual Studio Code  

Anda juga perlu menambahkan paket NuGet berikut ke proyek Anda:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.Drawing.Charts
```

Paket-paket ini menyediakan kelas `Document`, `DocumentBuilder`, dan kelas terkait diagram yang digunakan dalam contoh di bawah.

## Buat dokumen Word dan tambahkan diagram

Langkah pertama adalah **membuat dokumen Word** dan mendapatkan `DocumentBuilder` yang memungkinkan Anda menyisipkan konten. Builder berfungsi seperti kursor yang ditempatkan di dalam dokumen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

Objek `Document` mewakili seluruh file Word, sementara `DocumentBuilder` menyediakan metode seperti `InsertChart` yang menempatkan objek secara langsung ke alur dokumen.

## Sisipkan diagram pai ke dalam dokumen

Setelah builder siap, Anda dapat **menyisipkan diagram pai** dengan ukuran tertentu. Diagram ditambahkan pada posisi saat ini dari builder.

```csharp
        // Step 3: Insert a pie chart with the desired size (400x300 points)
        Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

        // Populate the chart with sample data
        pieChart.Series.Clear();
        ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                                new[] { 25.0, 35.0, 20.0, 20.0 });
```

`InsertChart` mengembalikan objek `Chart` yang dapat Anda manipulasi lebih lanjut. Data contoh membuat empat irisan yang mewakili penjualan kuartalan.

## Sesuaikan label data diagram pai

Agar diagram lebih mudah dibaca, Anda sering perlu **menyesuaikan diagram pai** label—menempatkannya di luar irisan dan menampilkan garis penghubung. Di sinilah `ChartDataLabelCollection` berperan.

```csharp
        // Step 4: Get the data label collection of the first series
        ChartDataLabelCollection dataLabels = pieChart.Series[0].DataLabels;

        // Step 5: Position the data labels outside each slice
        dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Step 6: Enable leader lines for clearer label connections
        dataLabels.ShowLeaderLines = true;

        // Optional: Show the actual value and percentage
        dataLabels.ShowValue = true;
        dataLabels.ShowPercentage = true;
```

Mengatur `Position` ke `OutsideEnd` memindahkan setiap label di luar tepi irisan, sementara `ShowLeaderLines` menggambar garis yang menghubungkan label ke irisan tersebut. Flag opsional `ShowValue` dan `ShowPercentage` memberikan pembaca baik angka mentah maupun persentase relatif.

**Tips profesional:** Jika Anda perlu memformat font label, gunakan `dataLabels.Font` untuk mengatur ukuran, warna, dan gaya. Ini memastikan diagram sesuai dengan merek perusahaan Anda.

## Simpan dan hasilkan file Word

Setelah diagram sepenuhnya dikonfigurasi, Anda dapat **menghasilkan file Word** dengan menyimpan instance `Document` ke disk. Pilih format `.docx` untuk kompatibilitas maksimal dengan versi Word modern.

```csharp
        // Step 7: Save the document with the customized chart
        string outputPath = @"C:\Temp\CustomPieChart.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Saat Anda membuka `CustomPieChart.docx`, Anda akan melihat diagram pai dengan empat irisan, masing‑masing berlabel di luar irisan, terhubung oleh garis penghubung, dan menampilkan baik nilai maupun persentase.

![Tangkapan layar dokumen Word yang berisi diagram pai yang disesuaikan dibuat dengan C#](image-placeholder.png)

*Gambar ini menunjukkan hasil akhir dari tutorial **membuat dokumen Word**.*

## Variasi umum dan kasus tepi

| Skenario | Cara menyesuaikan kode |
|----------|------------------------|
| **Beberapa seri** | Tambahkan objek `ChartSeries` tambahan ke `pieChart.Series`. Setiap seri dapat memiliki koleksi `DataLabels` masing‑masing untuk penataan independen. |
| **Ukuran diagram berbeda** | Ubah parameter lebar dan tinggi pada `InsertChart(width, height)`. Nilai dalam satuan poin (1 pt ≈ 1/72 in). |
| **Judul diagram** | Gunakan `pieChart.Title.Text = "Quarterly Sales"` untuk menambahkan judul deskriptif. |
| **Ekspor ke PDF** | Panggil `document.Save("Report.pdf", SaveFormat.Pdf);` setelah diagram selesai dibuat. |
| **Penanganan lisensi** | Tempatkan file lisensi Anda (`Aspose.Words.lic`) di folder aplikasi dan muat dengan `new License().SetLicense("Aspose.Words.lic");` sebelum membuat dokumen. |

Variasi ini memungkinkan Anda menjawab pertanyaan **cara menambahkan diagram pai** dalam banyak skenario dunia nyata, mulai dari laporan sederhana hingga dasbor kompleks.

## Kesimpulan

Anda sekarang tahu cara **membuat dokumen Word**, **menyisipkan diagram pai**, dan **menyesuaikan label diagram pai** menggunakan Aspose.Words untuk .NET. Contoh lengkap menunjukkan alur kerja yang bersih: menginisialisasi dokumen, menambahkan diagram, menyesuaikan posisi label data, mengaktifkan garis penghubung, dan akhirnya **menghasilkan file Word** yang dapat dibagikan kepada siapa saja.

Cobalah memperluas tutorial ini dengan bereksperimen menggunakan tipe diagram berbeda (`ChartType.Column`, `ChartType.Line`) atau dengan menerapkan palet warna khusus agar sesuai dengan merek Anda. Jika Anda mengalami masalah, konsultasikan dokumentasi Aspose.Words atau jelajahi topik terkait seperti “cara menambahkan diagram pai” dengan beberapa seri dan sumber data dinamis.

Selamat coding, dan silakan bagikan hasil Anda atau ajukan pertanyaan lanjutan di kolom komentar!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Sisipkan Diagram Kolom dalam Dokumen Word](/words/english/net/programming-with-charts/insert-column-chart/)
- [Sisipkan Diagram Area ke dalam Dokumen Word](/words/english/net/programming-with-charts/insert-area-chart/)
- [Sisipkan Diagram Sebar dalam Dokumen Word](/words/english/net/programming-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}