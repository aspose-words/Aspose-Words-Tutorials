---
category: general
date: 2026-08-04
description: Penempatan Label Data Kustom untuk Grafik di C# memungkinkan Anda menempatkan
  label di tengah irisan grafik. Ikuti panduan langkah demi langkah ini menggunakan
  API grafik Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Custom Data‑Label Placement for Charts
- chart data label positioning
- Aspose.Words chart API
- C# chart manipulation
- Word document chart automation
language: id
lastmod: 2026-08-04
og_description: Penempatan Label Data Kustom untuk Diagram di C# menunjukkan cara
  memusatkan semua label data pada setiap irisan diagram Word. Kuasai penempatan label
  data diagram dengan Aspose.Words.
og_image_alt: Screenshot of a Word chart with centered data labels after applying
  C# code
og_title: Penempatan Label Data Kustom untuk Grafik di C# – panduan langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Custom Data‑Label Placement for Charts in C# lets you center labels
    on chart slices. Follow this step‑by‑step guide using Aspose.Words chart API.
  headline: Custom Data‑Label Placement for Charts in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart
- Data Labels
title: Penempatan Label Data Kustom untuk Grafik di C#
url: /id/net/programming-with-charts/custom-data-label-placement-for-charts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Penempatan Data‑Label Kustom untuk Diagram di C#

**Penempatan Data‑Label Kustom untuk Diagram** memungkinkan Anda mengontrol secara tepat di mana setiap label muncul pada diagram di dalam dokumen Word. Dalam tutorial ini Anda akan belajar cara menengahkan semua label data pada setiap irisan menggunakan C# dan API diagram Aspose.Words.

Anda akan mendapatkan contoh lengkap yang dapat dijalankan yang memuat file `.docx`, mengakses shape diagram pertama, mengubah `Position` setiap label menjadi `Center`, dan menyimpan dokumen yang telah diperbarui. Tidak diperlukan referensi eksternal—hanya pustaka Aspose.Words untuk .NET dan lingkungan pengembangan C# dasar.

**Apa yang akan Anda pelajari**

* Cara memuat dokumen Word yang berisi diagram.  
* Cara menemukan shape diagram dengan API diagram Aspose.Words.  
* Cara menerapkan **penempatan label data diagram** ke setiap seri dalam diagram.  
* Cara menyimpan dokumen sehingga label yang ditengahkan muncul di Word.  

**Prasyarat**

* .NET 6.0 (atau lebih baru) terpasang.  
* Visual Studio 2022 (atau IDE C# apa pun).  
* Referensi ke paket NuGet `Aspose.Words`.  
* File Word (`Chart.docx`) yang berisi setidaknya satu diagram.

---

## Penempatan Data‑Label Kustom untuk Diagram – langkah 1: memuat dokumen

Tindakan pertama adalah membuka file Word yang berisi diagram. `Document` adalah titik masuk untuk setiap manipulasi dengan Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the source Word document.
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

// Verify that the document actually contains a chart.
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
if (shapes.Count == 0)
{
    throw new InvalidOperationException("The document does not contain any shapes.");
}
```

*Mengapa langkah ini penting*: Tanpa memuat dokumen Anda tidak dapat mengakses objek diagram. Validasi memastikan Anda menerima error yang jelas jika file tidak memiliki diagram, mencegah null‑reference di kemudian hari.

---

## Menggunakan API diagram Aspose.Words untuk mengakses shape diagram

Aspose.Words memperlakukan diagram sebagai objek `Chart` yang berada di dalam `Shape`. Anda dapat mengambilnya dengan melakukan casting pada node anak yang sesuai.

```csharp
// Get the first shape that is a chart.
Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (!chartShape.HasChart)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Extract the Chart instance.
Chart chart = chartShape.GetChart();
```

*Mengapa langkah ini penting*: Mengakses `Chart` secara langsung memberi Anda kontrol penuh atas seri, titik data, dan properti label. Jika shape bukan diagram, kode akan berhenti lebih awal dengan pesan informatif.

---

## Menetapkan penempatan label data diagram di C#

Sekarang iterasi melalui setiap seri dan setiap label data, mengatur `Position` menjadi `Center`. Ini adalah inti dari **Penempatan Data‑Label Kustom untuk Diagram**.

```csharp
// Center all data labels on each slice of the chart.
foreach (Series series in chart.Series)
{
    foreach (ChartDataLabel label in series.DataLabels)
    {
        // Position enum values: Center, InsideEnd, OutsideEnd, etc.
        label.Position = ChartDataLabelPosition.Center;
    }
}
```

**Tip pro**: Jika Anda memerlukan penempatan berbeda (mis., `InsideEnd` untuk diagram kolom), ubah nilai enum yang sesuai. Enum `ChartDataLabelPosition` mencakup semua posisi standar yang didukung Word.

*Mengapa langkah ini penting*: Mengubah `label.Position` memperbarui representasi OOXML di bawahnya, sehingga label muncul di tengah ketika dokumen dibuka di Microsoft Word.

---

## Menyimpan dokumen Word dengan label yang diperbarui

Setelah memodifikasi diagram, simpan perubahan kembali ke file. Anda dapat menimpa file asli atau membuat salinan baru.

```csharp
// Save the modified document with centered labels.
doc.Save(@"YOUR_DIRECTORY\ChartLabelsCentered.docx");
```

*Mengapa langkah ini penting*: Menyimpan menuliskan OOXML yang diperbarui ke disk. Membuka `ChartLabelsCentered.docx` di Word akan menampilkan setiap label irisan yang ditengahkan, mengonfirmasi bahwa **Penempatan Data‑Label Kustom untuk Diagram** berhasil.

---

## Kasus tepi dan variasi

| Situation | How to handle |
|-----------|---------------|
| **Multiple charts** dalam dokumen yang sama | Loop over `doc.GetChildNodes(NodeType.Shape, true)` and check `shape.HasChart` for each shape. |
| **Different chart types** (pie, doughnut, bar) | The same `ChartDataLabelPosition.Center` works for pie‑type charts. For bar/column charts you may prefer `InsideEnd` or `OutsideEnd`. |
| **Label text needs formatting** | Access `label.TextProperties` to set font size, color, or boldness. |
| **Running on .NET Core** | Ensure you reference the .NET Standard version of Aspose.Words; the API is identical. |

---

## Contoh kerja lengkap

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke aplikasi konsol. Program ini mencakup semua direktif `using` yang diperlukan dan penanganan error.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Path to the source and destination files.
        const string sourcePath = @"YOUR_DIRECTORY\Chart.docx";
        const string destPath   = @"YOUR_DIRECTORY\ChartLabelsCentered.docx";

        // Load the document.
        Document doc = new Document(sourcePath);

        // Find the first chart shape.
        Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (chartShape == null || !chartShape.HasChart)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Get the Chart object.
        Chart chart = chartShape.GetChart();

        // Center all data labels.
        foreach (Series series in chart.Series)
        {
            foreach (ChartDataLabel label in series.DataLabels)
            {
                label.Position = ChartDataLabelPosition.Center;
            }
        }

        // Save the updated document.
        doc.Save(destPath);
        Console.WriteLine($"Document saved with centered labels to: {destPath}");
    }
}
```

**Hasil yang diharapkan**: Buka `ChartLabelsCentered.docx` di Microsoft Word. Setiap irisan diagram kini menampilkan label datanya tepat di tengah irisan, memberikan tampilan visual yang lebih bersih.

---

## Kesimpulan

Anda kini memiliki solusi lengkap **Penempatan Data‑Label Kustom untuk Diagram** dalam C#. Dengan memuat dokumen, mengakses diagram melalui API diagram Aspose.Words, mengatur `ChartDataLabelPosition.Center` untuk setiap label, dan menyimpan file, Anda dapat mengotomatisasi penempatan label untuk diagram berbasis Word apa pun.

Selanjutnya, jelajahi opsi **penempatan label data diagram** lainnya seperti `InsideEnd` atau `OutsideEnd`, atau bereksperimen dengan **manipulasi diagram C#** untuk mengubah warna, menambahkan legenda, atau membuat diagram dari awal. Ekstensi ini dibangun langsung dari teknik yang dibahas di sini dan memperluas kemampuan Anda dalam otomatisasi diagram dokumen Word. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang dibangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}