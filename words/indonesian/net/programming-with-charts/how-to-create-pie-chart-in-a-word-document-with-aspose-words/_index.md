---
category: general
date: 2026-09-21
description: Pelajari cara membuat diagram lingkaran dan menyisipkan diagram ke dalam
  Word menggunakan Aspose.Words, menambahkan label data ke diagram lingkaran, serta
  menampilkan persentase pada diagram lingkaran dalam beberapa langkah saja.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- insert chart into word
- add data labels to pie chart
- show percentages on pie chart
- how to display percentages in chart
language: id
lastmod: 2026-09-21
og_description: Buat diagram pai di Word menggunakan Aspose.Words, sisipkan diagram
  ke Word, tambahkan label data ke diagram pai, dan tampilkan persentase pada diagram
  pai—semua dengan contoh kode yang jelas.
og_image_alt: Screenshot of a Word document containing a pie chart with percentage
  data labels displayed outside each slice
og_title: Buat diagram lingkaran di Word dengan Aspose.Words – panduan langkah demi
  langkah
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
- description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  name: How to create pie chart in a Word document with Aspose.Words
  steps:
  - name: Expected output
    text: 'When you open the generated document, you should see:'
  - name: Adding a title to the chart
    text: '```csharp chart.Title.Text = "Sales Distribution Q1"; chart.Title.Show
      = true; ```'
  - name: Changing slice colors
    text: '```csharp series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
      series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen; ```'
  - name: Handling an empty series
    text: 'If your data source might be empty, guard against `IndexOutOfRangeException`:'
  - name: Exporting to PDF instead of Word
    text: '```csharp doc.Save("PieChart.pdf", SaveFormat.Pdf); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- charting
- Word automation
title: Cara membuat diagram lingkaran di dokumen Word dengan Aspose.Words
url: /id/net/programming-with-charts/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat diagram pai dalam dokumen Word dengan Aspose.Words

Jika Anda perlu **membuat diagram pai** secara programatis, Aspose.Words mempermudahnya. Pada tutorial ini Anda akan melihat cara **menyisipkan diagram ke dalam Word**, mengonfigurasi seri, **menambahkan label data ke diagram pai**, dan akhirnya **menampilkan persentase pada diagram pai** sehingga visual menampilkan nilai yang tepat. Pada akhir tutorial Anda akan memiliki contoh lengkap yang dapat dijalankan dan dapat langsung dimasukkan ke proyek .NET mana pun.

Panduan ini mencakup semua yang perlu Anda ketahui: paket NuGet yang diperlukan, sumber C# lengkap, penjelasan mengapa setiap panggilan API penting, serta tips untuk menyesuaikan diagram. Tidak diperlukan dokumentasi eksternal—cukup salin, jalankan, dan sesuaikan.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* .NET 6.0 SDK atau yang lebih baru terpasang.  
* Visual Studio 2022 (atau IDE apa pun yang mendukung .NET).  
* Lisensi Aspose.Words for .NET (versi percobaan gratis dapat digunakan untuk pengujian).  
* Familiaritas dasar dengan C# dan struktur dokumen Word.

Jika semua sudah tersedia, Anda dapat langsung melanjutkan ke kode.

## Langkah 1: Siapkan proyek dan impor Aspose.Words

Buat proyek konsol baru dan tambahkan paket NuGet Aspose.Words:

```bash
dotnet new console -n PieChartDemo
cd PieChartDemo
dotnet add package Aspose.Words
```

Paket tersebut mencakup namespace `Aspose.Words.Drawing.Charts`, yang berisi kelas `Chart` dan `ChartSeries` yang akan kita gunakan.

> **Pro tip:** Simpan file lisensi Anda (`Aspose.Words.lic`) di root proyek dan muat pada saat startup untuk menghindari watermark evaluasi.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: Apply your license
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");
```

## Langkah 2: Buat dokumen kosong dan DocumentBuilder

`Document` mewakili file Word, sementara `DocumentBuilder` menyediakan API yang fluently untuk menyisipkan konten.

```csharp
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder will let us add a chart
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Mengapa ini penting:** `DocumentBuilder` menjaga titik sisipan saat ini, memastikan diagram muncul tepat di tempat yang Anda inginkan dalam alur dokumen.

## Langkah 3: Sisipkan diagram pai ke dalam dokumen Word

Sekarang kita **menyisipkan diagram ke dalam Word**. Metode `InsertChart` menerima tipe diagram, lebar, dan tinggi (dalam poin).

```csharp
        // Insert a pie chart of size 400x300 points
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

Pada titik ini diagram berisi seri data default dengan nilai placeholder (25, 25, 25, 25). Anda dapat menggantinya nanti jika diperlukan.

## Langkah 4: Akses seri pertama dan sesuaikan label data

Diagram pai biasanya memiliki satu seri. Untuk **menambahkan label data ke diagram pai**, kita mengambilnya dan mengaktifkan tampilan persentase.

```csharp
        // Access the first (and only) series of the chart
        ChartSeries series = chart.Series[0];

        // Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // Position the labels outside the slices for readability
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

**Mengapa kami mengatur `ShowPercentage`:** Flag ini memberi tahu Aspose.Words untuk menghitung kontribusi tiap irisan dan menampilkannya sebagai persentase. Properti `Position` memastikan label tidak menindih irisan, yang meningkatkan keterbacaan—terutama ketika irisan kecil.

## Langkah 5: (Opsional) Ganti data placeholder

Jika Anda menginginkan nilai tertentu, ganti titik default:

```csharp
        // Clear existing points
        series.Points.Clear();

        // Add custom data points
        series.Points.Add(new ChartPoint(40)); // 40%
        series.Points.Add(new ChartPoint(30)); // 30%
        series.Points.Add(new ChartPoint(20)); // 20%
        series.Points.Add(new ChartPoint(10)); // 10%
```

Persentase yang ditampilkan akan secara otomatis menyesuaikan untuk mencerminkan nilai baru.

## Langkah 6: Simpan dokumen

Akhirnya, tulis dokumen ke disk. Ekstensi menentukan format; `.docx` menghasilkan file Word modern.

```csharp
        // Save the document containing the pie chart
        doc.Save("PieChart.docx");
    }
}
```

Menjalankan program akan menghasilkan file bernama **PieChart.docx** di folder output. Membukanya di Microsoft Word akan menampilkan diagram pai dengan tiap irisan berlabel persentasenya, ditempatkan di luar irisan.

### Output yang diharapkan

Saat Anda membuka dokumen yang dihasilkan, Anda akan melihat:

* Satu diagram pai, berukuran 400 × 300 pt.  
* Empat irisan (atau sebanyak titik yang Anda tambahkan).  
* Label persentase seperti “40 %”, “30 %”, dll., ditampilkan di luar tiap irisan.

Jika label muncul di dalam irisan, periksa kembali bahwa `ChartDataLabelPosition.OutsideEnd` telah diatur dengan benar.

## Langkah 7: Variasi umum dan kasus tepi

### Menambahkan judul ke diagram

```csharp
chart.Title.Text = "Sales Distribution Q1";
chart.Title.Show = true;
```

### Mengubah warna irisan

```csharp
series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen;
```

### Menangani seri kosong

Jika sumber data Anda mungkin kosong, lindungi dari `IndexOutOfRangeException`:

```csharp
if (series.Points.Count == 0)
{
    // Provide a fallback to avoid runtime errors
    series.Points.Add(new ChartPoint(100));
}
```

### Mengekspor ke PDF alih-alih Word

```csharp
doc.Save("PieChart.pdf", SaveFormat.Pdf);
```

Logika rendering diagram tetap sama; Aspose.Words secara otomatis mengonversi tata letak Word ke PDF.

## Daftar sumber lengkap

Berikut adalah program lengkap yang siap dijalankan. Salin ke `Program.cs` dan jalankan `dotnet run`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: apply your license to remove evaluation watermarks
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Create a DocumentBuilder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a pie chart (400x300 points)
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 4. Access the first series
        ChartSeries series = chart.Series[0];

        // 5. Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // 6. Position data labels outside the slices
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Optional: replace placeholder data with custom values
        series.Points.Clear();
        series.Points.Add(new ChartPoint(40));
        series.Points.Add(new ChartPoint(30));
        series.Points.Add(new ChartPoint(20));
        series.Points.Add(new ChartPoint(10));

        // Optional: add a title
        chart.Title.Text = "Quarterly Sales Breakdown";
        chart.Title.Show = true;

        // 7. Save the document
        doc.Save("PieChart.docx"); // Change extension to .pdf for PDF output
    }
}
```

## Kesimpulan

Anda kini tahu cara **membuat diagram pai** dalam file Word menggunakan Aspose.Words, **menyisipkan diagram ke dalam Word**, **menambahkan label data ke diagram pai**, dan **menampilkan persentase pada diagram pai**. Contoh ini memperlihatkan alur kerja penuh—dari penyiapan proyek hingga dokumen akhir—sehingga Anda dapat menyesuaikannya untuk dasbor, laporan, atau pembuatan faktur otomatis.  

Selanjutnya, jelajahi topik terkait seperti **cara menampilkan persentase di legenda diagram**, menyesuaikan warna diagram, atau mengonversi dokumen Word ke PDF untuk distribusi. Bereksperimenlah dengan tipe diagram lain (Bar, Line) menggunakan metode `InsertChart` yang sama untuk memperluas kemampuan otomatisasi Anda.

Selamat membuat diagram!


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik yang sangat terkait dan membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}