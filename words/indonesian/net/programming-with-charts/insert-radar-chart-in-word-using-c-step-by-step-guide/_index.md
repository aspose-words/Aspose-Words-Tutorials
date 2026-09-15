---
category: general
date: 2026-09-14
description: Masukkan diagram radar di Word dengan C#. Pelajari cara mengatur judul
  diagram, menambahkan beberapa seri, dan membuat diagram secara programatis dalam
  hanya beberapa baris.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert radar chart
- set chart title
- create radar chart word
- multiple series radar chart
- create chart programmatically
language: id
lastmod: 2026-09-14
og_description: Masukkan diagram radar di Word menggunakan C#. Tutorial ini menunjukkan
  cara mengatur judul diagram, menambahkan beberapa seri, dan membuat diagram secara
  programatis.
og_image_alt: Screenshot of a Word document displaying a radar chart with sales data
og_title: Menyisipkan diagram radar di Word dengan C# – panduan pemrograman cepat
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Insert radar chart in Word with C#. Learn how to set chart title, add
    multiple series, and create the chart programmatically in just a few lines.
  headline: Insert radar chart in Word using C# – step‑by‑step guide
  type: TechArticle
tags:
- radar chart
- C#
- Aspose.Words
title: Menyisipkan diagram radar di Word menggunakan C# – panduan langkah demi langkah
url: /id/net/programming-with-charts/insert-radar-chart-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sisipkan diagram radar di Word menggunakan C# – panduan langkah‑demi‑langkah

Jika Anda perlu **menyisipkan diagram radar** ke dalam dokumen Word, panduan ini menunjukkan cara melakukannya secara programatis dengan C#. Anda juga akan belajar cara **mengatur judul diagram**, menambahkan **diagram radar dengan beberapa seri**, dan menyimpan file tanpa meninggalkan IDE Anda.

Tutorial ini mencakup semuanya mulai dari penyiapan proyek hingga pemanggilan `doc.Save` terakhir, sehingga Anda dapat menyalin‑tempel contoh lengkap dan menjalankannya segera. Tidak diperlukan pencarian dokumentasi eksternal.

## Prasyarat

* .NET 6 (atau lebih baru) terpasang.
* Lisensi Aspose.Words untuk .NET yang valid (atau kunci evaluasi sementara).
* Visual Studio 2022 atau IDE C# apa pun yang Anda sukai.

> **Tips pro:** Jika Anda menggunakan versi percobaan gratis, ingatlah untuk mengatur lisensi sebelum pembuatan `Document` pertama guna menghindari watermark evaluasi.

## Langkah 1: Sisipkan diagram radar ke dalam dokumen Word

Operasi pertama adalah membuat `Document` baru dan `DocumentBuilder`. Builder memberikan Anda akses ke konten dokumen dan memungkinkan Anda menempatkan **diagram radar** tepat di tempat yang Anda inginkan.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new blank Word document.
Document doc = new Document();

// DocumentBuilder provides methods to insert content.
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a radar (radial) chart at the current cursor position.
Chart chart = builder.InsertChart(ChartType.Radar);
```

*Mengapa langkah ini penting:* `InsertChart` membuat objek diagram yang dapat Anda konfigurasikan sepenuhnya sebelum dokumen disimpan. Menggunakan `ChartType.Radar` memberi tahu Word untuk menampilkan diagram radial alih‑alih diagram kolom atau garis.

## Langkah 2: Atur judul diagram dan graduasi sumbu

Diagram tanpa judul dapat membingungkan. Di sini kami **mengatur judul diagram** menjadi “Sales Radar” dan mengaktifkan graduasi pada kedua sumbu (tersedia mulai Aspose.Words 24.9).

```csharp
// Give the chart a meaningful title.
chart.Title.Text = "Sales Radar";

// Enable graduations (grid lines) on both X and Y axes.
chart.AxisX.HasGraduations = true;
chart.AxisY.HasGraduations = true;
```

*Mengapa langkah ini penting:* Judul memberikan konteks bagi pembaca, dan graduasi meningkatkan keterbacaan dengan menunjukkan di mana setiap titik data berada pada skala.

## Langkah 3: Buat beberapa seri untuk diagram radar

**Diagram radar dengan beberapa seri** memungkinkan Anda membandingkan periode yang berbeda berdampingan. Di bawah ini kami menambahkan dua seri—Q1 dan Q2—masing‑masing dengan tiga titik data.

```csharp
// Series 1: Q1 data.
chart.Series.Add(
    "Q1",                                 // Series name
    new[] { "Jan", "Feb", "Mar" },        // Category labels
    new[] { 10, 20, 30 }                  // Values
);

// Series 2: Q2 data.
chart.Series.Add(
    "Q2",
    new[] { "Jan", "Feb", "Mar" },
    new[] { 15, 25, 35 }
);
```

*Mengapa langkah ini penting:* Menambahkan beberapa seri menunjukkan cara membandingkan kumpulan data pada radar yang sama, sebuah kebutuhan umum untuk penjualan, kinerja, atau hasil survei.

## Langkah 4: Simpan dokumen Word secara programatis

Akhirnya, Anda **membuat diagram secara programatis** dan menyimpan dokumen ke disk. Metode `Save` menulis file `.docx` yang dapat dibuka di Microsoft Word.

```csharp
// Define the output path. Adjust the directory as needed.
string outputPath = Path.Combine(
    Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
    "RadialGraduations.docx"
);

// Save the document containing the radar chart.
doc.Save(outputPath);
```

Saat Anda membuka `RadialGraduations.docx`, Anda akan melihat diagram radar berjudul “Sales Radar” dengan dua seri (Q1 dan Q2) yang dipetakan terhadap bulan Jan‑Mar.

### Output yang diharapkan

![Radar chart in Word](https://example.com/radar-chart.png){: .align-center alt="Dokumen Word yang menampilkan diagram radar dengan dua seri data"}

Tangkapan layar (atau file sebenarnya) mengonfirmasi bahwa diagram telah disisipkan, diberi judul, dan terisi dengan benar.

## Contoh lengkap yang dapat dijalankan

Menggabungkan semuanya, berikut adalah program mandiri yang dapat Anda kompilasi dan jalankan:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a radar chart.
        Chart chart = builder.InsertChart(ChartType.Radar);

        // 3. Set chart title and enable axis graduations.
        chart.Title.Text = "Sales Radar";
        chart.AxisX.HasGraduations = true;
        chart.AxisY.HasGraduations = true;

        // 4. Add two data series.
        chart.Series.Add("Q1", new[] { "Jan", "Feb", "Mar" }, new[] { 10, 20, 30 });
        chart.Series.Add("Q2", new[] { "Jan", "Feb", "Mar" }, new[] { 15, 25, 35 });

        // 5. Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialGraduations.docx"
        );
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Jalankan program, buka file yang dihasilkan, dan verifikasi bahwa operasi **menyisipkan diagram radar** berhasil.

## Pertanyaan umum & kasus tepi

| Pertanyaan | Jawaban |
|----------|--------|
| **Apakah saya dapat mengubah tipe diagram setelah penyisipan?** | Ya. Setelah `InsertChart`, tetapkan `ChartType` baru ke `chart.Type`. Namun, membuat diagram dengan tipe yang tepat sejak awal lebih efisien. |
| **Bagaimana jika saya membutuhkan lebih dari dua seri?** | Panggil `chart.Series.Add` untuk setiap seri tambahan. Diagram akan secara otomatis menyesuaikan legenda dan warna. |
| **Bagaimana cara menyesuaikan warna atau penanda?** | Gunakan `chart.Series[i].Format.Fill.ForeColor` untuk warna isi dan `chart.Series[i].Marker` untuk gaya penanda. |
| **Apakah API kompatibel dengan .NET Framework?** | Kode yang sama berfungsi dengan .NET Framework 4.7+; cukup referensikan DLL Aspose.Words yang sesuai. |
| **Bagaimana jika saya menggunakan versi Aspose.Words yang lebih lama?** | Graduasi (`HasGraduations`) diperkenalkan pada versi 24.9. Untuk versi yang lebih lama, Anda dapat menambahkan garis kisi secara manual menggunakan `chart.AxisX.MajorGridLines` dan `chart.AxisY.MajorGridLines`. |

## Kesimpulan

Anda sekarang tahu cara **menyisipkan diagram radar** ke dalam dokumen Word menggunakan C#, **mengatur judul diagram**, menambahkan **diagram radar dengan beberapa seri**, dan **membuat diagram secara programatis**. Solusi menyeluruh ini memungkinkan Anda mengotomatisasi pelaporan, dasbor, atau skenario apa pun yang memerlukan perbandingan visual kategori.

Selanjutnya, jelajahi topik terkait seperti **menyesuaikan warna diagram**, **mengekspor diagram sebagai gambar**, atau **menyematkan diagram dalam file PDF**. Bereksperimenlah dengan kumpulan data yang berbeda untuk melihat bagaimana visualisasi radar beradaptasi.

Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Sisipkan Diagram Kolom di Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Sisipkan Diagram Gelembung di Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-charts/insert-bubble-chart/)
- [Sisipkan Diagram Area di Dokumen Word | Aspose.Words untuk .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}