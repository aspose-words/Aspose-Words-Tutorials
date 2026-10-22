---
category: general
date: 2026-09-21
description: Cara memformat seri dalam diagram garis Word menggunakan C#. Pelajari
  cara membuat dokumen Word, menyisipkan diagram garis, dan menerapkan format angka
  khusus.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format series
- create word document
- insert line chart
- add chart to word
- apply custom number format
language: id
lastmod: 2026-09-21
og_description: Cara memformat seri dalam diagram garis Word menggunakan C#. Tutorial
  ini menunjukkan cara membuat dokumen Word, menyisipkan diagram garis, dan menerapkan
  format angka khusus.
og_image_alt: Screenshot of a Word document showing a line chart with percentage‑formatted
  Y‑axis values
og_title: Cara memformat seri dalam diagram garis Word dengan C# – panduan langkah
  demi langkah
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to format series in a Word line chart using C#. Learn to create
    a Word document, insert a line chart, and apply a custom number format.
  headline: How to format series in a Word line chart with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart
- Word automation
title: Cara memformat seri dalam diagram garis Word dengan C#
url: /id/net/programming-with-charts/how-to-format-series-in-a-word-line-chart-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara memformat seri dalam diagram garis Word dengan C#

Jika Anda perlu **memformat seri** dalam diagram garis Word, panduan ini memberi Anda solusi lengkap yang siap dijalankan. Anda akan melihat cara **membuat dokumen Word**, **menyisipkan diagram garis**, dan **menerapkan format angka khusus** pada nilai Y — semuanya dengan Aspose.Words untuk .NET.

Otomatisasi Word menjadi sederhana setelah Anda memahami model objek diagram. Pada akhir tutorial ini Anda akan memiliki file Word yang berisi diagram garis dengan seri data yang ditampilkan sebagai persentase dengan dua tempat desimal.

## Apa yang akan Anda capai

* Menghasilkan file `.docx` kosong secara programatis.  
* Menambahkan diagram garis berukuran 400 × 300 point.  
* Mengakses seri data pertama pada diagram.  
* Menerapkan kode format `#,##0.00%` sehingga nilai Y muncul sebagai persentase.  

Tidak diperlukan alat eksternal selain paket NuGet Aspose.Words.

## Prasyarat

* .NET 6.0 SDK atau yang lebih baru.  
* Visual Studio 2022 (atau IDE C# apa pun).  
* Aspose.Words untuk .NET 23.10 atau yang lebih baru – instal melalui `dotnet add package Aspose.Words`.  

Kode ini bekerja di Windows, Linux, dan macOS karena Aspose.Words bersifat lintas‑platform.

## Membuat dokumen Word dengan Aspose.Words

Langkah pertama adalah menginstansiasi objek `Document`. Objek ini mewakili seluruh file Word dalam memori.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document.
        Document doc = new Document();

        // The document currently has no content.
        // We will add a chart in the next step.
```

*Mengapa ini penting*: `Document` adalah titik masuk untuk semua operasi pemrosesan Word. Tanpa itu Anda tidak dapat menambahkan paragraf, tabel, atau diagram.

## Menyisipkan diagram garis ke dalam dokumen

`DocumentBuilder` menulis konten ke dalam `Document`. Memanggil `InsertChart` membuat bentuk diagram pada halaman saat ini.

```csharp
        // Step 2: Initialize a DocumentBuilder to construct the document content.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a line chart with the desired size (400 × 300 points).
        Chart chart = builder.InsertChart(ChartType.Line, 400, 300);
```

*Mengapa ini penting*: `InsertChart` mengembalikan objek `Chart` yang memberi Anda kontrol penuh atas seri, sumbu, dan pemformatan. Parameter ukuran dinyatakan dalam point (1 point = 1/72 inci).

## Mengakses seri data pertama

Setiap diagram berisi satu atau lebih `ChartSeries`. Seri pertama berada pada indeks 0.

```csharp
        // Step 4: Access the first data series of the chart.
        ChartSeries series = chart.Series[0];
```

*Mengapa ini penting*: Objek `ChartSeries` menyimpan nilai Y, nilai X, dan opsi pemformatan untuk satu garis dalam diagram garis. Memodifikasi objek ini mengubah representasi visual data.

## Menerapkan format angka khusus pada seri

Properti `FormatCode` mengontrol bagaimana nilai numerik ditampilkan. Menetapkannya ke `#,##0.00%` memberi tahu Word untuk memperlakukan nilai tersebut sebagai persentase dengan dua tempat desimal.

```csharp
        // Step 5: Apply a custom number format to the Y‑values.
        // This displays the numbers as percentages with two decimals.
        series.YValues.FormatCode = "#,##0.00%";

        // Optional: Populate the series with sample data.
        series.YValues.Add(0.15);
        series.YValues.Add(0.30);
        series.YValues.Add(0.45);
        series.YValues.Add(0.60);
```

*Mengapa ini penting*: Tanpa format khusus, Word menampilkan angka desimal mentah (mis., `0.15`). Kode format mengubahnya menjadi `15.00%`, yang sering diperlukan dalam laporan bisnis.

## Menyimpan dokumen dan memverifikasi hasil

```csharp
        // Save the document to the file system.
        string outputPath = "FormattedSeriesLineChart.docx";
        doc.Save(outputPath);
        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Saat Anda membuka `FormattedSeriesLineChart.docx` di Microsoft Word, Anda akan melihat diagram garis di mana label sumbu Y menampilkan `15.00%`, `30.00%`, `45.00%`, dan `60.00%`. Ukuran diagram sesuai dengan dimensi yang diberikan pada `InsertChart`.

### Tangkapan layar output yang diharapkan

> *Gambar: Halaman dokumen Word yang menampilkan diagram garis dengan nilai sumbu Y yang diformat persentase.*  
> *(Teks alternatif: Tangkapan layar dokumen Word yang menampilkan diagram garis dengan nilai sumbu Y yang diformat persentase)*

## Variasi umum dan kasus tepi

| Situasi | Penyesuaian |
|-----------|------------|
| **Beberapa seri** | Loop melalui `chart.Series` dan set `FormatCode` untuk setiap seri. |
| **Jenis diagram berbeda** | Ganti `ChartType.Line` dengan `ChartType.Column`, `ChartType.Pie`, dll. |
| **Pemisah khusus lokal** | Gunakan string format yang memperhatikan `CultureInfo`, mis., `"# ##0,00 %"` untuk lokal Prancis. |
| **Sumber data dinamis** | Isi `series.YValues` dari basis data atau file CSV sebelum menerapkan format. |

**Tips profesional:** Selalu terapkan format **setelah** Anda menambahkan nilai Y. Mengubah format terlebih dahulu lalu menambahkan nilai juga dapat berhasil, tetapi menerapkannya kemudian menjamin format diterapkan pada set data akhir.

## Ringkasan

Anda sekarang tahu **cara memformat seri** dalam diagram garis Word menggunakan C#. Tutorial ini mencakup:

* Membuat dokumen Word (`create word document`).  
* Menyisipkan diagram garis (`insert line chart`, `add chart to word`).  
* Mengakses seri pertama diagram.  
* Menerapkan format angka khusus (`apply custom number format`) untuk menampilkan persentase.

## Langkah Selanjutnya

* Bereksperimen dengan nilai `ChartType` yang berbeda untuk melihat bagaimana visualisasi lain berperilaku.  
* Tambahkan judul, label sumbu, dan legenda menggunakan `chart.Title`, `chart.AxisX.Title`, dan `chart.AxisY.Title`.  
* Ekspor diagram sebagai gambar (`chart.Save` dengan `SaveFormat.Png`) untuk digunakan dalam laporan web.

Silakan sesuaikan pola ini untuk menghasilkan dasbor, laporan keuangan, atau dokumen apa pun yang memerlukan pembuatan diagram secara programatis. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Diagram Garis di Word menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Sisipkan Diagram Kolom dalam Dokumen Word](/words/english/net/programming-with-charts/insert-column-chart/)
- [Sisipkan Diagram Area di Dokumen Word | Aspose.Words untuk .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}