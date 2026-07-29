---
category: general
date: 2026-07-29
description: Cara mengedit grafik dalam dokumen Word—pelajari cara mengubah posisi
  label grafik, menyesuaikan label grafik batang, memodifikasi label data grafik,
  dan mengubah font label grafik.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- change chart label position
- adjust bar chart labels
- modify chart data labels
- change chart label font
language: id
lastmod: 2026-07-29
og_description: Cara mengedit grafik di Word dengan cepat. Kuasai mengubah posisi
  label grafik, menyesuaikan label grafik batang, memodifikasi label data grafik,
  dan mengubah font label grafik.
og_image_alt: Screenshot of a Word bar chart with custom label positions and larger
  font size
og_title: Cara Mengedit Grafik di Word – Ubah Label & Font
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  headline: 'How to Edit Chart in Word: Change Label Position, Font & More'
  type: TechArticle
- description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  name: 'How to Edit Chart in Word: Change Label Position, Font & More'
  steps:
  - name: What if the document contains multiple charts?
    text: 'The code above grabs the *first* chart (`GetChild(NodeType.Shape, 0, true)`).
      To edit all charts, replace the single retrieval with a loop:'
  - name: How to **change chart label font** for a specific series only?
    text: 'Each `ChartSeries` has its own `DataLabelCollection`. Target a series by
      index:'
  - name: Does this work with pie or line charts?
    text: Yes—`ChartDataLabelPosition` supports values like `InsideEnd`, `OutsideEnd`,
      and `BestFit`. For a pie chart you might prefer `OutsideEnd` to keep labels
      readable.
  - name: What about localization (e.g., different decimal separators)?
    text: Aspose.Words respects the document’s locale settings. If you need to enforce
      a specific format, adjust `label.NumberFormat` before saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: 'Cara Mengedit Grafik di Word: Mengubah Posisi Label, Font, dan Lainnya'
url: /id/net/working-with-charts/how-to-edit-chart-in-word-change-label-position-font-more/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Mengedit Chart di Word: Mengubah Posisi Label, Font & Lainnya

Mengedit chart dalam dokumen Word adalah kebutuhan umum ketika Anda ingin laporan terlihat rapi. Pernah mengalami kesulitan untuk **change chart label position** atau membuat label dapat dibaca tanpa harus menggali menu yang tak berujung? Anda tidak sendirian—banyak pengembang menghadapi hal ini saat mengotomatisasi pembuatan laporan. Dalam panduan ini kami akan membahas contoh lengkap yang dapat dijalankan yang menunjukkan cara **adjust bar chart labels**, **modify chart data labels**, dan **change chart label font** menggunakan C# dan library Aspose.Words.

## Apa yang Akan Anda Pelajari

- Muat file .docx yang sudah berisi grafik batang.  
- Ambil shape grafik pertama dan akses koleksi data‑labelnya.  
- **Change chart label position** untuk membuat batang terlihat lebih bersih.  
- **Adjust bar chart labels** ukuran font untuk keterbacaan yang lebih baik.  
- Simpan dokumen yang telah dimodifikasi kembali ke disk.  

Tanpa alat eksternal, tanpa langkah UI manual—hanya kode murni yang dapat Anda sisipkan ke proyek .NET mana pun. Pada akhir tutorial Anda akan memiliki solusi mandiri yang dapat digunakan kembali pada puluhan dokumen.

> **Prerequisites**  
> - .NET 6.0 atau lebih baru (kode juga berfungsi pada .NET Framework 4.7+).  
> - Aspose.Words untuk .NET (tersedia via NuGet).  
> - File Word (`BarChart.docx`) yang sudah berisi grafik batang.  

Jika Anda belum memiliki salah satu dari ini, dapatkan paket Aspose.Words terbaru sekarang:

```bash
dotnet add package Aspose.Words
```

---

## Cara Mengedit Chart: Mengambil Chart dari Dokumen Word

Langkah pertama dalam **how to edit chart** objek adalah memuat dokumen dan menemukan shape chart. Aspose.Words memperlakukan chart sebagai node `Shape`, sehingga kita dapat menggunakan `GetChild` dengan `NodeType.Shape` untuk mengambil chart pertama yang ditemukan.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the Word document that contains a chart
Document document = new Document(@"C:\Temp\BarChart.docx");

// Retrieve the first chart shape from the document
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
```

> **Why this matters:**  
> Dengan mengakses objek `Chart` secara langsung, Anda menghindari beban membuka file di Word dan menyesuaikan setiap label secara manual. Ini adalah dasar dari setiap otomatisasi **modify chart data labels**.

## Sesuaikan Label Chart Batang: Ubah Posisi Label Chart

Sekarang kita memiliki instance `Chart`, mari iterasi `DataLabelCollection`-nya. Tujuannya adalah **change chart label position** sehingga setiap label berada dengan rapi di dalam dasar batangnya, bukan melayang canggung di atasnya.

```csharp
// Loop through each data label in the chart
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Place label inside the base of the bar
    dataLabel.Position = ChartDataLabelPosition.InsideBase;
}
```

> **Pro tip:**  
> `InsideBase` bekerja baik untuk chart batang vertikal. Jika Anda menggunakan chart batang horizontal, coba `InsideEnd` sebagai gantinya. Bereksperimen dengan posisi itu murah—cukup jalankan ulang kode dan buka dokumen yang disimpan.

## Ubah Font Label Chart: Sesuaikan Ukuran Font untuk Keterbacaan

Font yang sangat kecil adalah pembunuh diam-diam kejelasan laporan. Untuk **change chart label font**, cukup atur properti `Font.Size` pada setiap `ChartDataLabel`. Kami akan menaikkannya menjadi 9 pt, yang merupakan ukuran ideal untuk kebanyakan laporan cetak.

```csharp
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Set a readable font size (9 points)
    dataLabel.Font.Size = 9;
}
```

> **Why we do this:**  
> Menyesuaikan ukuran font adalah bagian dari praktik terbaik **modify chart data labels**. Font yang lebih besar meningkatkan aksesibilitas dan mengurangi kebutuhan pemrosesan manual setelahnya.

## Simpan Dokumen yang Diperbarui

Setelah menyesuaikan posisi dan font, langkah terakhir dalam **how to edit chart** adalah menyimpan perubahan. Aspose.Words membuat ini menjadi satu baris kode.

```csharp
// Save the modified document with new label settings
document.Save(@"C:\Temp\BarChartCustomLabels.docx");
```

Buka `BarChartCustomLabels.docx` di Word dan Anda akan melihat label berada rapat di dalam batang, ditampilkan dengan font 9 pt yang jelas. Tidak lagi harus mengerutkan mata melihat angka-angka kecil.

---

## Contoh Lengkap yang Berfungsi (Semua Langkah dalam Satu File)

Berikut adalah program konsol lengkap yang siap dijalankan yang mendemonstrasikan seluruh alur—dari memuat dokumen hingga menyimpan versi yang diperbarui. Salin‑tempel ke proyek konsol .NET baru dan tekan **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source document (must contain a bar chart)
            string sourcePath = @"C:\Temp\BarChart.docx";

            // Path where the edited document will be saved
            string destPath = @"C:\Temp\BarChartCustomLabels.docx";

            // Load the Word document
            Document doc = new Document(sourcePath);

            // Retrieve the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Iterate over each data label
            foreach (ChartDataLabel label in chart.DataLabelCollection)
            {
                // Change chart label position
                label.Position = ChartDataLabelPosition.InsideBase;

                // Change chart label font size
                label.Font.Size = 9;
            }

            // Save the updated document
            doc.Save(destPath);
            Console.WriteLine($"Chart labels updated and saved to: {destPath}");
        }
    }
}
```

**Output yang diharapkan** ketika Anda menjalankan program:

```
Chart labels updated and saved to: C:\Temp\BarChartCustomLabels.docx
```

Buka file yang dihasilkan dan Anda akan melihat **adjust bar chart labels** berada di dalam batang dengan ukuran font yang nyaman.

---

## Pertanyaan Umum & Kasus Tepi

### Bagaimana jika dokumen berisi beberapa chart?

Kode di atas mengambil chart *pertama* (`GetChild(NodeType.Shape, 0, true)`). Untuk mengedit semua chart, ganti pengambilan tunggal dengan loop:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shape in shapes)
{
    if (shape.HasChart)
    {
        Chart chart = shape.GetChart();
        // Apply label changes as shown earlier
    }
}
```

### Cara **change chart label font** untuk satu series saja?

Setiap `ChartSeries` memiliki `DataLabelCollection` masing-masing. Targetkan series dengan indeks:

```csharp
ChartSeries series = chart.Series[1]; // second series (zero‑based)
foreach (ChartDataLabel label in series.DataLabelCollection)
{
    label.Font.Size = 10; // larger for this series only
}
```

### Apakah ini bekerja dengan chart pie atau line?

Ya—`ChartDataLabelPosition` mendukung nilai seperti `InsideEnd`, `OutsideEnd`, dan `BestFit`. Untuk chart pie Anda mungkin lebih suka `OutsideEnd` agar label tetap terbaca.

### Bagaimana dengan lokalisasi (mis., pemisah desimal yang berbeda)?

Aspose.Words menghormati pengaturan lokal dokumen. Jika Anda perlu memaksa format tertentu, sesuaikan `label.NumberFormat` sebelum menyimpan.

---

## Ringkasan & Langkah Selanjutnya

Kami telah membahas **how to edit chart** objek dalam dokumen Word dari awal hingga akhir: memuat file, mengambil chart, **changing chart label position**, **adjusting bar chart labels**, **modifying chart data labels**, dan akhirnya **changing chart label font** sebelum menyimpan. Contoh lengkapnya siap produksi dan dapat disisipkan ke dalam pipeline otomatisasi apa pun.

Siap untuk meningkatkan level? Pertimbangkan ide-ide berikut:

- **Add data label colors** (`dataLabel.Font.Color = Color.Blue;`).  
- **Show values as percentages** (`dataLabel.NumberFormat = "0%";`).  
- **Create charts programmatically** instead of loading existing ones.  

Semua ini dibangun di atas antarmuka API yang sama yang kami gunakan hari ini, sehingga Anda akan merasa familiar.

Jika Anda mengalami kendala, tinggalkan komentar di bawah atau periksa dokumentasi Aspose.Words untuk opsi kustomisasi chart yang lebih mendalam. Selamat coding, dan nikmati chart dengan label yang indah!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}