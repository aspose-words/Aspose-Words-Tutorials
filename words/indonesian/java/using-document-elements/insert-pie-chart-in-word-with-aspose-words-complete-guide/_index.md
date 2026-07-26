---
category: general
date: 2026-07-26
description: Masukkan diagram lingkaran ke dalam dokumen Word menggunakan Aspose.Words.
  Pelajari cara menambahkan diagram, memisahkan irisan, dan menampilkan persentase
  dalam beberapa langkah saja.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to add chart
- how to explode slice
- add chart to word
- how to show percentages
language: id
lastmod: 2026-07-26
og_description: Masukkan diagram lingkaran ke dalam file Word dengan Aspose.Words.
  Ikuti panduan ini untuk mempelajari cara menambahkan diagram, memisahkan irisan,
  dan menampilkan persentase dengan cepat.
og_image_alt: Screenshot illustrating insert pie chart in a Word document
og_title: Menyisipkan Diagram Lingkaran di Word – Tutorial Aspose.Words Langkah demi
  Langkah
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert pie chart into a Word document using Aspose.Words. Learn how
    to add chart, explode slice, and show percentages in just a few steps.
  headline: Insert Pie Chart in Word with Aspose.Words – Complete Guide
  type: TechArticle
- questions:
  - answer: Just add additional `ChartSeries` objects to `chart.Series`. Each series
      can have its own data set, colors, and explode settings.
    question: What if I need more than one series?
  - answer: Yes. Each `ChartPoint` has a `Format.Fill.ForeColor` property you can
      set to any `System.Drawing.Color`.
    question: Can I change the chart’s colors?
  - answer: The `ChartType` enum includes bar, line, doughnut, and many more. Swap
      `ChartType.Pie` for whichever visual you need.
    question: What about different chart types?
  - answer: Absolutely. Word treats the chart as a native Office chart, so users can
      double‑click it to open the built‑in chart editor.
    question: Is the chart editable in Word after insertion?
  type: FAQPage
tags:
- Aspose.Words
- Chart Automation
- .NET Development
title: Menyisipkan Diagram Lingkaran di Word dengan Aspose.Words – Panduan Lengkap
url: /id/java/using-document-elements/insert-pie-chart-in-word-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menyisipkan Diagram Lingkaran di Word dengan Aspose.Words – Panduan Lengkap

Pernah perlu **menyisipkan diagram lingkaran** ke dalam laporan Word tetapi tidak yakin harus mulai dari mana? Anda tidak sendirian. Dalam banyak aplikasi bisnis, visualisasi diagram lingkaran membuat data langsung dapat dipahami, dan Aspose.Words memungkinkan hal itu dengan hanya beberapa baris kode.

Dalam tutorial ini kami akan membahas langkah‑langkah **menambahkan diagram ke Word**, me‑explode sebuah irisan untuk penekanan, dan menampilkan persentase pada label data. Pada akhir tutorial Anda akan memiliki contoh siap‑jalankan yang dapat Anda masukkan ke proyek .NET mana pun.

---

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki:

- .NET 6.0 atau yang lebih baru (kode ini bekerja dengan .NET Core dan .NET Framework)
- Paket NuGet Aspose.Words untuk .NET terpasang  
  ```bash
  dotnet add package Aspose.Words
  ```
- Pemahaman dasar tentang sintaks C#—tidak diperlukan hal yang rumit
- IDE pilihan Anda (Visual Studio, Rider, atau VS Code)

Itu saja. Mari kita mulai.

---

## Menyisipkan Diagram Lingkaran ke Dokumen Word

Hal pertama yang kita butuhkan adalah objek `Document` baru dan sebuah `DocumentBuilder`. Anggap builder sebagai pena yang menulis langsung pada kanvas Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
using Aspose.Words.Charts;

// Step 1: Create a new document and a builder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Mengapa ini penting:** `Document` mewakili seluruh file .docx, sementara `DocumentBuilder` memberikan API yang nyaman untuk menyisipkan elemen seperti diagram, tabel, dan teks. Ini adalah fondasi untuk setiap operasi **cara menambahkan diagram**.

---

## Cara Menambahkan Diagram ke Word

Setelah kita memiliki builder, kita dapat benar‑benar **menyisipkan diagram lingkaran**. Metode `insertChart` menerima tipe diagram dan dimensi yang diinginkan dalam poin (1 poin = 1/72 inci).

```csharp
// Step 2: Insert a pie chart of size 400x300 points
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

> **Tip:** Jika Anda memerlukan ukuran berbeda, cukup ubah nilai lebar dan tinggi. Diagram akan otomatis menyesuaikan diri dengan margin halaman.

---

## Cara Me‑explode Irisan untuk Penekanan

Salah satu penyesuaian visual yang umum adalah “me‑explode” sebuah irisan sehingga keluar dari lingkaran. Ini menarik perhatian pembaca ke segmen yang paling penting.

```csharp
// Step 3: Access the first series (the data set)
ChartSeries series = chart.Series[0];

// Step 4: Explode the first slice to emphasize it
series.Points[0].Exploded = true;
```

> **Mengapa me‑explode irisan?** Ketika Anda ingin menyoroti kategori tertentu—misalnya, “pendapatan Q1” dalam laporan keuangan—me‑explode irisan membuatnya langsung terlihat tanpa teks tambahan.

---

## Cara Menampilkan Persentase pada Label Data

Sebagian besar diagram lingkaran terlihat lebih baik ketika setiap irisan menampilkan persentasenya. Aspose.Words memungkinkan kita mengaktifkannya dengan satu properti.

```csharp
// Step 5: Show percentages on the data labels of the first series
series.DataLabelFormat.ShowPercentage = true;
```

> **Catatan cepat:** Flag `ShowPercentage` berlaku untuk semua titik dalam seri, jadi Anda tidak perlu mengaturnya per irisan.

---

## Menyimpan Dokumen yang Memuat Diagram

Akhirnya, kita menulis dokumen ke disk. Pilih folder mana saja yang Anda suka; pastikan jalurnya sudah ada.

```csharp
// Step 6: Save the document containing the chart
doc.Save(@"C:\Temp\PieChart.docx");
```

Saat Anda membuka `PieChart.docx` di Microsoft Word, Anda akan melihat diagram lingkaran yang terrender sempurna dengan irisan pertama yang me‑explode dan persentase yang ditampilkan—tepat seperti yang diharapkan dari laporan bisnis yang rapi.

---

## Contoh Kerja Lengkap

Berikut adalah program lengkap yang siap disalin‑tempel. Jalankan sebagai aplikasi konsol dan verifikasi file outputnya.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a pie chart (400x300 points)
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data
            ChartSeries series = chart.Series[0];
            series.Name = "Sales Q1";
            series.Add(30); // Product A
            series.Add(45); // Product B
            series.Add(25); // Product C

            // Explode the first slice (Product A)
            series.Points[0].Exploded = true;

            // Show percentages on data labels
            series.DataLabelFormat.ShowPercentage = true;

            // Save the document
            string outputPath = @"C:\Temp\PieChart.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Hasil yang diharapkan:** Buka `PieChart.docx` yang dihasilkan. Anda akan melihat diagram lingkaran tiga irisan berjudul “Sales Q1”, dengan irisan pertama ditarik keluar dan setiap irisan berlabel “30 %”, “45 %”, dan “25 %”. Visualnya cocok dengan data yang kami masukkan.

---

## Pertanyaan Umum & Kasus Khusus

- **Bagaimana jika saya membutuhkan lebih dari satu seri?**  
  Cukup tambahkan objek `ChartSeries` tambahan ke `chart.Series`. Setiap seri dapat memiliki kumpulan data, warna, dan pengaturan explode masing‑masing.

- **Bisakah saya mengubah warna diagram?**  
  Ya. Setiap `ChartPoint` memiliki properti `Format.Fill.ForeColor` yang dapat Anda atur ke warna `System.Drawing.Color` apa pun.

- **Bagaimana dengan tipe diagram lain?**  
  Enum `ChartType` mencakup bar, line, doughnut, dan banyak lagi. Ganti `ChartType.Pie` dengan tipe yang Anda butuhkan.

- **Apakah diagram dapat diedit di Word setelah disisipkan?**  
  Tentu saja. Word memperlakukan diagram sebagai diagram Office native, sehingga pengguna dapat double‑click untuk membuka editor diagram bawaan.

---

## Kesimpulan

Anda kini tahu persis cara **menyisipkan diagram lingkaran** ke dalam dokumen Word menggunakan Aspose.Words, **cara menambahkan diagram ke Word**, **cara me‑explode irisan**, dan **cara menampilkan persentase** pada label data. Contoh lengkap di atas siap dijalankan, dan Anda dapat memperluasnya dengan data khusus, styling, atau seri tambahan.

Siap untuk langkah berikutnya? Coba ganti diagram lingkaran dengan diagram donat, atau hasilkan batch laporan dengan kumpulan data berbeda secara otomatis. Jika Anda penasaran dengan visualisasi lain, lihat panduan kami tentang **cara menambahkan diagram** untuk diagram batang dan garis, atau jelajahi referensi API **add chart to word** untuk kustomisasi lebih dalam.

Selamat coding, dan semoga dokumen Anda selalu sejelas potongan pai yang sempurna!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang memperluas teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Menyisipkan Diagram Kolom di Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Menyisipkan Diagram Area di Dokumen Word | Aspose.Words untuk .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Membuat Diagram Scatter di Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}