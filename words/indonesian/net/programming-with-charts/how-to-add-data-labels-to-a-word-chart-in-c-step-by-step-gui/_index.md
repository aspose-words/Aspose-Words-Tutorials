---
category: general
date: 2026-08-04
description: Cara menambahkan label data di C# dengan Aspose.Words. Pelajari cara
  mengedit diagram, memusatkan label data diagram, menampilkan persentase dalam diagram,
  dan menyesuaikan label data diagram.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add data labels
- how to edit chart
- center chart data labels
- show percentages in chart
- customize chart data labels
language: id
lastmod: 2026-08-04
og_description: Cara menambahkan label data di C# menggunakan Aspose.Words. Tutorial
  ini menunjukkan cara mengedit diagram, memusatkan label data diagram, menampilkan
  persentase dalam diagram, dan menyesuaikan label data diagram.
og_image_alt: Screenshot of a Word chart with data labels added using C#
og_title: Cara menambahkan label data ke diagram Word di C# – panduan lengkap
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  headline: How to add data labels to a Word chart in C# – step‑by‑step guide
  type: TechArticle
- description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  name: How to add data labels to a Word chart in C# – step‑by‑step guide
  steps:
  - name: – Load the Word document containing the chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: – Retrieve the first chart from the document
    text: '```csharp // Find the first shape that contains a chart. Shape chartShape
      = (Shape)document.GetChild(NodeType.Shape, 0, true); Chart chart = chartShape.GetChart();
      ```'
  - name: – Enable data label customization and show percentages in chart
    text: '```csharp // Access the first series of the chart. ChartSeries series =
      chart.Series[0];'
  - name: – Change the label placement to the center of each data point
    text: '```csharp // Position the labels at the center of each point. dataLabels.Position
      = ChartDataLabelPosition.Center; // center chart data labels ```'
  - name: – Further customize chart data labels (optional)
    text: 'If you need more control, you can adjust font, color, or leader lines:'
  - name: – Save the modified document
    text: '```csharp // Persist the changes to a new file. document.Save("YOUR_DIRECTORY/output.docx");
      ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word, the chart will display:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Cara menambahkan label data ke diagram Word di C# – panduan langkah demi langkah
url: /id/net/programming-with-charts/how-to-add-data-labels-to-a-word-chart-in-c-step-by-step-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menambahkan label data ke diagram Word di C# – panduan langkah demi langkah

Jika Anda perlu **how to add data labels** ke diagram yang berada di dalam dokumen Word, panduan ini menunjukkan kode tepat yang harus Anda jalankan. Anda akan melihat cara mengedit properti diagram, menempatkan label data diagram di tengah, menampilkan persentase dalam diagram, dan menyesuaikan label data diagram untuk skenario apa pun.

Tutorial ini mencakup semua yang diperlukan untuk memodifikasi diagram yang sudah ada, mulai dari memuat dokumen hingga menyimpan perubahan. Tidak diperlukan referensi eksternal—hanya pustaka Aspose.Words untuk .NET dan lingkungan pengembangan C# dasar.

## Prasyarat

Sebelum Anda mulai, pastikan Anda memiliki:

* .NET 6.0 (atau lebih baru) terinstal.
* Aspose.Words untuk .NET versi 23.9 atau lebih baru.  
  Anda dapat menginstalnya melalui NuGet:

```bash
dotnet add package Aspose.Words
```

* File Word (`input.docx`) yang berisi setidaknya satu diagram.

## Cara menambahkan label data ke diagram Word di C#

Bagian-bagian berikut akan memandu Anda melalui setiap langkah. Kata kunci utama **how to add data labels** muncul secara alami dalam narasi dan komentar kode, menjaga kepadatan dalam rentang yang direkomendasikan.

### Langkah 1 – Muat dokumen Word yang berisi diagram

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

*Mengapa langkah ini penting*: Objek `Document` mewakili seluruh file Word. Memuatnya memberi Anda akses ke setiap node, termasuk shape yang menampung diagram.

### Langkah 2 – Ambil diagram pertama dari dokumen

```csharp
// Find the first shape that contains a chart.
Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
Chart chart = chartShape.GetChart();
```

*Mengapa langkah ini penting*: Diagram disimpan di dalam node `Shape`. Dengan meng-cast node yang diambil ke `Shape` dan memanggil `GetChart()`, Anda memperoleh objek `Chart` yang menampilkan seri, sumbu, dan koleksi label.

### Langkah 3 – Aktifkan penyesuaian label data dan tampilkan persentase dalam diagram

```csharp
// Access the first series of the chart.
ChartSeries series = chart.Series[0];

// Turn on data labels and request percentage values.
ChartDataLabelCollection dataLabels = series.DataLabels;
dataLabels.ShowPercentage = true;   // show percentages in chart
dataLabels.ShowValue = true;        // optional: also show raw values
```

*Mengapa langkah ini penting*: Menetapkan `ShowPercentage` memberi tahu Aspose.Words untuk menghitung dan menampilkan kontribusi setiap irisan terhadap total. Ini secara langsung menanggapi kata kunci sekunder **show percentages in chart**.

### Langkah 4 – Ubah penempatan label ke tengah setiap titik data

```csharp
// Position the labels at the center of each point.
dataLabels.Position = ChartDataLabelPosition.Center; // center chart data labels
```

*Mengapa langkah ini penting*: Properti `Position` mengontrol di mana label muncul relatif terhadap titik data. Menggunakan `Center` memenuhi kata kunci sekunder **center chart data labels** dan meningkatkan keterbacaan untuk diagram pai atau donat.

### Langkah 5 – Sesuaikan lebih lanjut label data diagram (opsional)

Jika Anda memerlukan kontrol lebih, Anda dapat menyesuaikan font, warna, atau garis penghubung:

```csharp
// Example: make labels bold and red.
dataLabels.Font.Bold = true;
dataLabels.Font.Color = System.Drawing.Color.Red;

// Example: add leader lines for better separation.
dataLabels.ShowLeaderLines = true;
```

Pengaturan ini menggambarkan kata kunci sekunder **customize chart data labels** dan menunjukkan bagaimana Anda dapat menyesuaikan tampilan agar sesuai dengan pedoman merek.

### Langkah 6 – Simpan dokumen yang telah dimodifikasi

```csharp
// Persist the changes to a new file.
document.Save("YOUR_DIRECTORY/output.docx");
```

*Mengapa langkah ini penting*: Menyimpan menuliskan diagram yang diperbarui kembali ke dalam dokumen Word, sehingga label data baru terlihat ketika file dibuka di Microsoft Word.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin, tempel, dan jalankan. Program ini mencakup semua direktif `using` yang diperlukan serta komentar yang menjelaskan setiap baris.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class AddDataLabelsDemo
{
    static void Main()
    {
        // 1. Load the Word document.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first chart.
        Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
        Chart chart = chartShape.GetChart();

        // 3. Enable data labels and show percentages.
        ChartSeries series = chart.Series[0];
        ChartDataLabelCollection dataLabels = series.DataLabels;
        dataLabels.ShowPercentage = true;
        dataLabels.ShowValue = true;

        // 4. Center the labels on each data point.
        dataLabels.Position = ChartDataLabelPosition.Center;

        // 5. Optional: further customize appearance.
        dataLabels.Font.Bold = true;
        dataLabels.Font.Color = System.Drawing.Color.DarkBlue;
        dataLabels.ShowLeaderLines = true;

        // 6. Save the modified document.
        document.Save("YOUR_DIRECTORY/output.docx");

        Console.WriteLine("Data labels added and document saved successfully.");
    }
}
```

### Hasil yang diharapkan

Saat Anda membuka `output.docx` di Microsoft Word, diagram akan menampilkan:

* Nilai persentase di sebelah setiap irisan (misalnya **25 %**, **40 %**, …).
* Label yang ditempatkan di tengah setiap titik data.
* Gaya tambahan apa pun yang Anda terapkan, seperti teks merah tebal.

Petunjuk visual ini membuat diagram lebih mudah dipahami, terutama dalam presentasi atau laporan.

## Cara mengedit properti diagram selain label data

Meskipun fokus panduan ini adalah **how to add data labels**, Anda mungkin juga ingin **how to edit chart** pengaturan seperti judul, penempatan legenda, atau pemformatan sumbu. Objek `Chart` menyediakan properti seperti `Title`, `Legend`, dan `AxisX/AxisY`. Misalnya, untuk mengubah judul diagram:

```csharp
chart.Title.Text = "Quarterly Sales Breakdown";
chart.Title.Font.Size = 14;
```

Semua modifikasi diagram mengikuti pola yang sama: ambil diagram, sesuaikan propertinya, lalu simpan dokumen.

## Kesalahan umum dan tips praktik terbaik

| Jebakan | Mengapa terjadi | Perbaikan yang disarankan |
|---|---|---|
| Diagram berada di dalam shape yang dikelompokkan. | `GetChild(NodeType.Shape, …)` mengembalikan grup luar, bukan diagram dalam. | Cari secara rekursif shape dengan `shape.HasChart`. |
| Label data tidak muncul setelah disimpan. | `ShowValue` atau `ShowPercentage` tidak diatur ke `true`. | Secara eksplisit atur kedua `ShowValue` dan `ShowPercentage` sesuai kebutuhan. |
| Label saling tumpang tindih pada irisan kecil. | Penempatan di tengah dapat menyebabkan kepadatan. | Gunakan `ChartDataLabelPosition.OutSideEnd` untuk penempatan di luar, atau aktifkan `LeaderLines`. |

## Kesimpulan

Anda sekarang tahu **how to add data labels** ke diagram Word menggunakan C#. Tutorial ini mencakup cara mengambil diagram, mengaktifkan visibilitas label, menempatkan label di tengah, menampilkan persentase, dan menyesuaikan tampilan. Dengan pengetahuan ini Anda juga dapat **how to edit chart** detail, **center chart data labels**, **show percentages in chart**, dan **customize chart data labels** untuk skenario pelaporan apa pun.

Siap untuk menjelajah lebih jauh? Cobalah menambahkan beberapa seri, menerapkan pemformatan bersyarat, atau mengekspor diagram sebagai gambar. API Aspose.Words menawarkan kemampuan manipulasi diagram yang luas—bereksperimenlah untuk menemukan representasi visual yang sempurna bagi data Anda.

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Sesuaikan Label Data Diagram](/words/english/net/programming-with-charts/chart-data-label/)
- [Atur Opsi Default untuk Label Data dalam Diagram](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Sesuaikan Satu Titik Data Diagram dalam Diagram](/words/english/net/programming-with-charts/single-chart-data-point/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}