---
category: general
date: 2026-09-21
description: Cara membuat histogram di Word dengan Aspose.Words. Pelajari cara mengatur
  bin histogram dan mengkonfigurasi bin histogram untuk visualisasi data yang tepat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create histogram in word
- how to set histogram bins
- configure histogram bins
language: id
lastmod: 2026-09-21
og_description: Cara membuat histogram di Word dengan Aspose.Words. Tutorial ini menunjukkan
  cara mengatur bin histogram dan mengonfigurasi bin histogram untuk grafik yang akurat.
og_image_alt: Screenshot of a Word document showing a histogram chart created with
  Aspose.Words
og_title: Buat histogram di Word dengan Aspose.Words – panduan lengkap
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to create histogram in Word with Aspose.Words. Learn how to set
    histogram bins and configure histogram bins for precise data visualisation.
  headline: How to create histogram in Word with Aspose.Words
  type: TechArticle
- description: How to create histogram in Word with Aspose.Words. Learn how to set
    histogram bins and configure histogram bins for precise data visualisation.
  name: How to create histogram in Word with Aspose.Words
  steps:
  - name: Prepare the development environment.
    text: Prepare the development environment.
  - name: Build a blank Word document and obtain a `DocumentBuilder`.
    text: Build a blank Word document and obtain a `DocumentBuilder`.
  - name: Insert a histogram chart and adjust its properties.
    text: Insert a histogram chart and adjust its properties.
  - name: Save the document and verify the result.
    text: Save the document and verify the result.
  type: HowTo
tags:
- histogram
- Aspose.Words
- C#
- Word automation
title: Cara membuat histogram di Word dengan Aspose.Words
url: /id/net/programming-with-charts/how-to-create-histogram-in-word-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat histogram di Word dengan Aspose.Words

Jika Anda perlu membuat histogram di Word, Aspose.Words membuat prosesnya menjadi sederhana. Panduan ini membawa Anda melalui setiap langkah, mulai dari menyiapkan proyek hingga mengonfigurasi bin histogram untuk penyajian data yang jelas. Anda juga akan melihat cara mengatur bin histogram dan mengonfigurasi bin histogram agar sesuai dengan kebutuhan pelaporan Anda.

## Cara membuat histogram di Word – alur kerja keseluruhan

Alur kerja keseluruhan terdiri dari empat fase logis:

1. Menyiapkan lingkungan pengembangan.  
2. Membuat dokumen Word kosong dan memperoleh `DocumentBuilder`.  
3. Menyisipkan diagram histogram dan menyesuaikan propertinya.  
4. Menyimpan dokumen dan memverifikasi hasilnya.

Setiap fase dibahas secara detail di bawah ini, dan kode sumber lengkap disediakan di akhir artikel.

## Menyiapkan lingkungan pengembangan

Sebelum Anda menulis kode apa pun, pastikan Anda memiliki prasyarat berikut:

| Prasyarat | Alasan |
|-----------|--------|
| .NET 6.0 atau lebih baru | Menyediakan runtime untuk proyek C#. |
| Visual Studio 2022 (atau IDE apa pun yang mendukung .NET) | Memungkinkan Anda mengompilasi dan men-debug contoh. |
| Paket NuGet Aspose.Words untuk .NET | Menyediakan kelas `Document`, `DocumentBuilder`, dan kelas diagram. |

Anda dapat menambahkan paket Aspose.Words dengan NuGet CLI:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Gunakan versi tetap (misalnya, `23.9.0`) di produksi untuk menghindari perubahan yang tidak terduga.

## Menyisipkan diagram histogram

Setelah lingkungan siap, buat proyek konsol baru dan buka file `Program.cs`. Dua baris kode pertama membuat dokumen kosong dan `DocumentBuilder` yang memungkinkan Anda memanipulasi dokumen:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new blank document and a DocumentBuilder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Selanjutnya, panggil `InsertChart` untuk menambahkan histogram. Metode ini memerlukan tipe diagram, lebar, dan tinggi dalam poin:

```csharp
// Insert a histogram chart with a specific size (400x300 points)
Chart histogram = builder.InsertChart(ChartType.Histogram, 400, 300);
```

Pada titik ini dokumen berisi placeholder histogram kosong. Saat Anda membuka file *.docx* yang dihasilkan, Anda akan melihat area diagram berwarna abu-abu yang siap diisi data.

![Histogram placeholder in Word document](/images/histogram-placeholder.png){: .img-fluid alt="Tangkapan layar dokumen Word yang menampilkan placeholder diagram histogram yang dibuat dengan Aspose.Words"}

## Cara mengatur bin histogram

Histogram memvisualisasikan distribusi data numerik dengan mengelompokkan nilai ke dalam *bin*. Properti `HistogramBins` mengontrol berapa banyak bin yang ditampilkan diagram. Mengatur properti ini sebelum menambahkan data memastikan diagram menyisihkan jumlah batang yang tepat.

```csharp
// Set the number of bins (bars) in the histogram
histogram.HistogramBins = 10;
```

Anda dapat menyesuaikan jumlah bin agar sesuai dengan granularitas kumpulan data Anda. Misalnya, kumpulan data dengan rentang 0 hingga 100 dan jumlah bin 10 menghasilkan interval 10 unit masing‑masing (0‑9, 10‑19, …, 90‑100).

> **Mengapa penting:** Memilih terlalu sedikit bin dapat menyembunyikan pola penting, sementara terlalu banyak bin dapat menghasilkan diagram yang berisik. Uji beberapa nilai untuk menemukan titik optimal bagi data spesifik Anda.

## Mengonfigurasi bin histogram agar lebih mudah dibaca

Selain jumlah bin, Anda biasanya ingin memberi label setiap bin sehingga pembaca dapat melihat hitungan tepat. Properti `ShowBinLabels` mengatur visibilitas label tersebut:

```csharp
// Display the value of each bin on the chart
histogram.ShowBinLabels = true;
```

Ketika `ShowBinLabels` diatur ke `true`, Word menampilkan label numerik di atas setiap batang. Langkah konfigurasi kecil ini sangat meningkatkan interpretabilitas diagram, terutama dalam laporan di mana audiens mungkin tidak memiliki kumpulan data asli.

Anda juga dapat menyesuaikan tampilan label, seperti ukuran font atau warna, melalui objek `HistogramLabel` (tersedia pada versi Aspose.Words yang lebih baru). Potongan kode berikut menunjukkan penyesuaian umum:

```csharp
// Optional: make bin labels bold and increase font size
histogram.HistogramLabel.Font.Size = 10;
histogram.HistogramLabel.Font.Bold = true;
```

> **Kasus khusus:** Jika Anda mengatur `HistogramBins` ke nilai yang lebih besar daripada jumlah titik data yang berbeda, beberapa bin akan muncul kosong. Diagram tetap akan dirender dengan benar, tetapi visualnya mungkin terlihat jarang. Pertimbangkan mengurangi jumlah bin dalam skenario tersebut.

## Menambahkan seri data ke histogram

Histogram memerlukan satu seri data yang mewakili nilai numerik dasar. Anda dapat mengisi seri tersebut menggunakan array, `List<double>`, atau koleksi enumerable apa pun. Berikut contoh singkat yang menambahkan kumpulan data acak:

```csharp
// Create a data series for the histogram
ChartSeries series = histogram.Series[0];
double[] sampleData = { 12, 45, 23, 67, 34, 89, 54, 31, 22, 78, 41, 60 };
series.DataPoints.AddRange(sampleData);
```

Metode `AddRange` mengonversi setiap nilai menjadi bin sesuai dengan `HistogramBins` yang telah didefinisikan sebelumnya. Setelah langkah ini, diagram menampilkan histogram yang terisi penuh.

## Menyimpan dan melihat dokumen hasil

Akhirnya, tulis dokumen ke disk. Anda dapat memilih lokasi mana saja yang dapat diakses aplikasi Anda. Baris berikut menyimpan file sebagai `output.docx`:

```csharp
// Save the document so you can view the chart
doc.Save("output.docx");
```

Buka `output.docx` di Microsoft Word untuk melihat histogram dengan sepuluh bin, nilai berlabel, dan data contoh yang Anda berikan. Diagram akan terlihat serupa dengan gambar di bawah ini:

![Completed histogram in Word](/images/histogram-complete.png){: .img-fluid alt="Dokumen Word yang menampilkan diagram histogram lengkap dengan sepuluh bin dan label"}

## Contoh lengkap yang dapat dijalankan

Menggabungkan semua bagian, berikut program mandiri yang dapat Anda salin, tempel, dan jalankan:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a histogram chart (400×300 points)
        Chart histogram = builder.InsertChart(ChartType.Histogram, 400, 300);

        // 3️⃣ Configure the histogram
        histogram.HistogramBins = 10;          // How to set histogram bins
        histogram.ShowBinLabels = true;       // Configure histogram bins to show labels
        histogram.HistogramLabel.Font.Size = 10;
        histogram.HistogramLabel.Font.Bold = true;

        // 4️⃣ Add a data series
        ChartSeries series = histogram.Series[0];
        double[] data = { 12, 45, 23, 67, 34, 89, 54, 31, 22, 78, 41, 60 };
        series.DataPoints.AddRange(data);

        // 5️⃣ Save the document
        doc.Save("output.docx");
    }
}
```

**Output yang diharapkan:** Membuka `output.docx` menampilkan histogram dengan sepuluh batang yang berjarak merata, masing‑masing berlabel dengan hitungannya. Diagram mencerminkan distribusi array `data`, sehingga tren terlihat seketika.

## Pertanyaan umum dan pemecahan masalah

| Pertanyaan | Jawaban |
|------------|---------|
| *Bagaimana jika saya membutuhkan lebih dari satu seri data?* | Histogram biasanya mewakili satu distribusi. Jika Anda memerlukan beberapa seri, pertimbangkan menggunakan diagram kolom sebagai gantinya. |
| *Bisakah saya mengubah ukuran diagram setelah penyisipan?* | Ya. Sesuaikan properti `histogram.Width` dan `histogram.Height`, atau panggil kembali `builder.InsertChart` dengan dimensi yang berbeda. |
| *Apakah ini bekerja dengan .NET Framework 4.8?* | Tentu saja. Aspose.Words mendukung .NET Framework 4.5 dan yang lebih baru, sehingga kode yang sama dapat dijalankan tanpa perubahan. |
| *Bagaimana cara mengekspor diagram sebagai gambar?* | Gunakan `histogram.ToImage()` untuk memperoleh `System.Drawing.Image`, lalu simpan dengan `image.Save("chart.png")`. |

## Kesimpulan

Anda kini tahu cara membuat histogram di Word menggunakan Aspose.Words, cara mengatur bin histogram, dan cara mengonfigurasi bin histogram untuk output yang jelas dan berlabel. Contoh lengkap menunjukkan pendekatan siap produksi yang dapat Anda adaptasi untuk skenario pelaporan berbasis data apa pun.  

Selanjutnya, jelajahi topik terkait seperti **cara membuat diagram pai di Word**, **menyesuaikan warna diagram**, dan **menyematkan sumber data Excel**. Masing‑masing topik ini dibangun di atas alur kerja `DocumentBuilder` yang sama, sehingga Anda dapat memperluas solusi dengan usaha minimal.

Selamat membuat diagram!


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara membuat diagram kolom menggunakan Aspose.Words untuk Java](/words/english/java/document-conversion-and-export/using-charts/)
- [cara membuat pdf dari Word – Panduan Lengkap C#](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [Cara Memuat Dokumen Word Menggunakan Aspose.Words LoadOptions](/words/english/net/programming-with-loadoptions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}