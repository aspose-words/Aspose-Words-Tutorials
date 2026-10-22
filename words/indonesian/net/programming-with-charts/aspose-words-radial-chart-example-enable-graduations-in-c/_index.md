---
category: general
date: 2026-10-13
description: Contoh diagram radial Aspose.Words yang menunjukkan cara mengaktifkan
  graduasi pada diagram radial menggunakan C# dan Aspose.Words 24.9+.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words radial chart example
- Aspose.Words chart API
- C# radial chart
- graduations visibility
- Aspose.Words version 24.9
- chart manipulation in .NET
language: id
lastmod: 2026-10-13
og_description: Contoh diagram radial Aspose.Words yang menunjukkan cara mengaktifkan
  graduasi pada diagram radial dengan C# dan perpustakaan terbaru versi 24.9+.
og_image_alt: Aspose.Words radial chart example displaying graduations
og_title: Contoh diagram radial Aspose.Words – aktifkan graduasi di C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  headline: 'Aspose.Words radial chart example: enable graduations in C#'
  type: TechArticle
- description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  name: 'Aspose.Words radial chart example: enable graduations in C#'
  steps:
  - name: Load the document that contains a radial chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: Retrieve the first chart shape from the document
    text: '```csharp // NodeType.Shape selects shapes; the third argument (true) searches
      the whole tree. Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
      if (chart == null) { throw new InvalidOperationException("No chart shape found
      in the document."); } ```'
  - name: Enable graduations on the radial chart
    text: '```csharp // This property is available starting with Aspose.Words 24.9.
      chart.RadialChart.IsGraduationsVisible = true; ```'
  - name: Save the modified document
    text: '```csharp string outputPath = Path.Combine(Environment.CurrentDirectory,
      "RadialChart_Graduations.docx"); doc.Save(outputPath); Console.WriteLine($"Document
      saved to {outputPath}"); ```'
  - name: Expected output
    text: When you open `RadialChart_Graduations.docx` in Word, the radial chart will
      display tick marks (graduations) around the circular axis, similar to the screenshot
      shown earlier. The rest of the chart (data series, legend, title) remains unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Charts
title: 'Contoh diagram radial Aspose.Words: aktifkan graduasi di C#'
url: /id/net/programming-with-charts/aspose-words-radial-chart-example-enable-graduations-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Contoh diagram radial Aspose.Words: mengaktifkan graduasi di C#

Jika Anda mencari **contoh diagram radial aspose.words**, Anda berada di tempat yang tepat. Tutorial ini memandu Anda melalui langkah‑langkah tepat untuk mengaktifkan graduasi pada diagram radial menggunakan API Aspose.Words untuk .NET.

Diagram radial berguna untuk memvisualisasikan data siklik seperti metrik waktu‑hari atau tren musiman. Secara default, graduasi (tanda centang di sekitar sumbu melingkar) disembunyikan, yang dapat membuat diagram lebih sulit dibaca. Mengaktifkannya hanya memerlukan satu baris kode, tetapi Anda harus mengetahui model objek yang tepat dan versi yang mendukung fitur tersebut.

Dalam panduan ini Anda akan belajar cara:

* Muat dokumen Word yang sudah berisi diagram radial.  
* Akses bentuk diagram melalui API diagram Aspose.Words.  
* Aktifkan **visibilitas graduasi** (tersedia sejak **Aspose.Words versi 24.9**).  
* Simpan dokumen yang telah dimodifikasi dan verifikasi hasilnya.

Kode lengkap yang dapat dijalankan disertakan, sehingga Anda dapat menyalin‑tempelnya ke dalam proyek konsol baru dan melihat efeknya secara langsung.

![Contoh diagram radial Aspose.Words dengan graduasi](https://example.com/images/radial-chart-graduations.png "Contoh diagram radial Aspose.Words yang menunjukkan graduasi diaktifkan")

## Prasyarat

Sebelum Anda memulai, pastikan Anda memiliki:

| Persyaratan | Mengapa penting |
|-------------|----------------|
| .NET 6.0 atau lebih baru | Aspose.Words untuk .NET 24.9+ menargetkan .NET Standard 2.0 dan bekerja pada .NET 6+. |
| Aspose.Words untuk .NET **24.9** atau lebih baru | Properti `IsGraduationsVisible` diperkenalkan pada versi 24.9. Rilis yang lebih lama akan melempar `MissingMemberException`. |
| Dokumen Word (`RadialChart.docx`) yang berisi diagram radial | Contoh ini memanipulasi diagram yang sudah ada; membuat diagram dari awal adalah topik terpisah. |
| IDE C# (Visual Studio, Rider, VS Code) | IDE apa pun yang dapat mengompilasi proyek .NET akan berfungsi. |
| Paket NuGet `Aspose.Words` | Instal melalui `dotnet add package Aspose.Words --version 24.9.0` (atau yang lebih baru). |

> **Tip pro:** Jika Anda tidak dapat memperbarui ke versi 24.9, Anda masih dapat memodifikasi properti diagram lainnya, tetapi graduasi akan tetap tersembunyi karena API tidak mengekspos flag tersebut.

## Contoh diagram radial Aspose.Words – panduan langkah‑demi‑langkah

Bagian berikut memecah proses menjadi langkah‑langkah terpisah yang mudah diikuti. Setiap langkah menyertakan kode yang tepat yang Anda butuhkan serta penjelasan singkat tentang *mengapa* langkah tersebut ada.

### Langkah 1: Muat dokumen yang berisi diagram radial

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// The file path can be absolute or relative to the executable directory.
string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");

// Load the Word document. Aspose.Words parses the entire file into a DOM tree.
Document doc = new Document(sourcePath);
```

**Mengapa ini penting:**  
`Document` adalah titik masuk **API diagram Aspose.Words**. Ia memuat file DOCX ke dalam memori, memberi Anda akses ke setiap node—paragraf, tabel, dan bentuk diagram. Jika file tidak ditemukan, `Document` akan melempar `FileNotFoundException`, yang sebaiknya Anda tangani dalam kode produksi.

### Langkah 2: Ambil bentuk diagram pertama dari dokumen

```csharp
// NodeType.Shape selects shapes; the third argument (true) searches the whole tree.
Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    throw new InvalidOperationException("No chart shape found in the document.");
}
```

**Mengapa ini penting:**  
Diagram disimpan sebagai node `Shape`. Metode `GetChild` dengan `NodeType.Shape` menelusuri DOM dan mengembalikan bentuk pertama yang cocok. Casting ke `Chart` memberi Anda akses ke properti khusus diagram seperti `RadialChart`. Pemeriksaan null memastikan Anda mendapatkan error yang jelas jika dokumen tidak berisi diagram, yang merupakan kasus tepi umum saat menggunakan kembali templat.

### Langkah 3: Aktifkan graduasi pada diagram radial

```csharp
// This property is available starting with Aspose.Words 24.9.
chart.RadialChart.IsGraduationsVisible = true;
```

**Mengapa ini penting:**  
`IsGraduationsVisible` mengontrol tanda centang di sekitar sumbu melingkar. Ketika diset ke `true`, diagram menampilkan graduasi, meningkatkan keterbacaan bagi pemirsa yang perlu mengukur nilai secara tepat. Properti ini berada di bawah `RadialChart`, yang merupakan sub‑tipe dari `Chart`. Jika Anda mencoba ini pada diagram non‑radial (misalnya, diagram batang), properti `RadialChart` akan `null`, sehingga Anda harus memverifikasi tipe diagram terlebih dahulu dalam skenario yang lebih kompleks.

#### Menangani diagram non‑radial (opsional)

```csharp
if (chart.ChartType == ChartType.Radial)
{
    chart.RadialChart.IsGraduationsVisible = true;
}
else
{
    Console.WriteLine("The chart is not radial; graduations are not applicable.");
}
```

Pengecekan ini membuat kode lebih kuat ketika dokumen sumber mungkin berisi tipe diagram yang berbeda.

### Langkah 4: Simpan dokumen yang telah dimodifikasi

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Mengapa ini penting:**  
Memanggil `Save` menulis DOM dalam memori kembali ke file .docx, menyimpan perubahan yang Anda buat pada diagram. File output dapat dibuka di Microsoft Word, LibreOffice, atau penampil apa pun yang mendukung DOCX. Anda akan melihat diagram radial dengan graduasi yang terlihat.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda tempel ke dalam `Program.cs` pada proyek konsol .NET.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1. Load the source document that contains a radial chart.
        // -----------------------------------------------------------------
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");
        Document doc = new Document(sourcePath);

        // -----------------------------------------------------------------
        // 2. Locate the first chart shape in the document.
        // -----------------------------------------------------------------
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // -----------------------------------------------------------------
        // 3. Enable graduations (tick marks) on the radial chart.
        // -----------------------------------------------------------------
        // Ensure the chart is radial before accessing RadialChart.
        if (chart.ChartType == ChartType.Radial && chart.RadialChart != null)
        {
            chart.RadialChart.IsGraduationsVisible = true;
        }
        else
        {
            Console.WriteLine("The chart is not a radial chart; cannot set graduations.");
            return;
        }

        // -----------------------------------------------------------------
        // 4. Save the updated document.
        // -----------------------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Radial chart with graduations saved to: {outputPath}");
    }
}
```

### Output yang diharapkan

Saat Anda membuka `RadialChart_Graduations.docx` di Word, diagram radial akan menampilkan tanda centang (graduasi) di sekitar sumbu melingkar, mirip dengan tangkapan layar yang ditunjukkan sebelumnya. Sisanya dari diagram (seri data, legenda, judul) tetap tidak berubah.

## Variasi umum dan kasus tepi

| Situasi | Solusi |
|-----------|----------|
| **Older Aspose.Words version (< 24.9)** | Perbarui ke paket NuGet terbaru. Properti `IsGraduationsVisible` tidak ada pada rilis sebelumnya. |
| **Multiple charts in the same document** | Gunakan `doc.GetChild(NodeType.Shape, index, true)` dengan `index` yang sesuai atau iterasi melalui `doc.GetChildNodes(NodeType.Shape, true)` dan saring berdasarkan `ChartType.Radial`. |
| **Chart created programmatically** | Gunakan `DocumentBuilder` untuk menyisipkan diagram, lalu set `RadialChart.IsGraduationsVisible` pada |

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Perbarui Data Seri Diagram dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Hapus Seri Diagram dari Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/programming-with-charts/remove-chart-series/)
- [Sembunyikan Garis Batas Area Plot pada Diagram Kolom dengan Aspose.Words untuk .NET](/words/english/net/programming-with-charts/hide-plot-border/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}