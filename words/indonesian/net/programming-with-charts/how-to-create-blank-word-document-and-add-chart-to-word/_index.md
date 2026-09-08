---
category: general
date: 2026-09-08
description: Buat dokumen Word kosong dan tambahkan grafik ke Word dengan Aspose.Words.
  Pelajari cara menyisipkan grafik radar, mengaktifkan graduasi, dan menyimpan file.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add chart to word
- insert radar chart
- Aspose.Words chart
- C# Word automation
language: id
lastmod: 2026-09-08
og_description: Buat dokumen Word kosong dan tambahkan diagram ke Word menggunakan
  Aspose.Words. Tutorial ini menunjukkan cara menyisipkan diagram radar, mengonfigurasi
  sumbu, dan menyimpan dokumen.
og_image_alt: Radar chart inserted into a blank Word document created with C#
og_title: Buat dokumen Word kosong dan tambahkan diagram radar – panduan langkah demi
  langkah
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: create blank Word document and add chart to Word with Aspose.Words.
    Learn how to insert radar chart, enable graduations, and save the file.
  headline: How to create blank Word document and add chart to Word
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- Chart
title: Cara membuat dokumen Word kosong dan menambahkan grafik ke Word
url: /id/net/programming-with-charts/how-to-create-blank-word-document-and-add-chart-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat dokumen Word kosong dan menambahkan diagram ke Word

Jika Anda perlu **membuat dokumen Word kosong** untuk laporan, templat, atau mail‑merge otomatis, panduan ini akan membawa Anda melalui seluruh proses dengan C# dan Aspose.Words. Anda juga akan belajar cara **menambahkan diagram ke Word**, khususnya cara **menyisipkan diagram radar**, mengaktifkan graduasi, dan menyimpan hasilnya sebagai file .docx.

Tutorial ini mencakup semua hal mulai dari penyiapan proyek hingga langkah verifikasi akhir. Pada akhir tutorial Anda akan memiliki potongan kode yang dapat digunakan kembali dan dapat disisipkan ke dalam aplikasi .NET apa pun. Tidak diperlukan pengalaman sebelumnya dengan Aspose.Words, tetapi Anda harus memiliki pengetahuan dasar C# dan .NET SDK terbaru yang terpasang.

## Prasyarat

- .NET 6.0 SDK atau yang lebih baru  
- Aspose.Words untuk .NET (paket NuGet `Aspose.Words`)  
- IDE seperti Visual Studio 2022 atau VS Code  
- Izin menulis ke folder tempat dokumen akan disimpan  

Anda dapat menginstal pustaka dengan perintah berikut:

```bash
dotnet add package Aspose.Words
```

## Langkah 1: Membuat dokumen Word kosong

Langkah pertama adalah **membuat dokumen Word kosong** di memori. Kelas `Document` mewakili seluruh file, sementara `DocumentBuilder` menyediakan API fluens untuk menambahkan konten.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

public class RadarChartDemo
{
    public static void Main()
    {
        // Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` dimulai dalam keadaan kosong, sehingga Anda memiliki kanvas bersih untuk menempatkan diagram. Menjaga dokumen tetap kosong pada tahap ini memudahkan penggunaan kembali kode yang sama untuk templat yang berbeda.

## Langkah 2: Menambahkan diagram ke Word

Selanjutnya, kita **menambahkan diagram ke Word** dengan memanggil `InsertChart`. Metode ini memerlukan jenis diagram dan dimensi yang diinginkan dalam poin (1 poin = 1/72 inci).

```csharp
        // Insert a radar (radial) chart with a defined size
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`ChartType.Radar` memberi tahu Aspose.Words untuk menghasilkan diagram radial, yang ideal untuk menampilkan data multivariat dalam tata letak melingkar. Nilai ukuran (400 × 300) bekerja dengan baik untuk kebanyakan halaman potret, tetapi Anda dapat menyesuaikannya agar sesuai dengan tata letak Anda.

## Langkah 3: Menyisipkan diagram radar dan mengonfigurasi graduasi

Sekarang kita **menyisipkan diagram radar** dan mengaktifkan graduasi (tanda centang) pada sumbu kategori (X) dan nilai (Y). Graduasi meningkatkan keterbacaan dengan menunjukkan posisi tepat untuk setiap titik data.

```csharp
        // Turn on graduations for both axes
        radarChart.AxisX.HasGraduations = true;   // radial (category) axis
        radarChart.AxisY.HasGraduations = true;   // value axis

        // Optional: define a custom graduation step for the radial axis
        radarChart.AxisX.GraduationStep = 10;
```

Menetapkan `HasGraduations` ke `true` menggambar tanda centang pada sumbu. `GraduationStep` opsional mengontrol jarak antar tanda pada sumbu radial; langkah 10 berarti satu tanda setiap 10 derajat.

### Tips profesional
Jika Anda perlu menampilkan label data, panggil `radarChart.Series[0].HasDataLabel = true;`. Ini menambahkan nilai numerik di sebelah setiap titik, yang berguna untuk presentasi.

## Langkah 4: Mengisi diagram dengan data contoh (opsional)

Diagram radar tanpa data tidak terlihat. Di bawah ini cara cepat menambahkan serangkaian nilai contoh. Anda dapat mengganti blok ini dengan sumber data Anda sendiri.

```csharp
        // Add a series with sample data
        radarChart.Series.Clear(); // Remove any default series
        var series = radarChart.Series.Add("Performance", "Category");
        series.Add(30);
        series.Add(55);
        series.Add(70);
        series.Add(45);
        series.Add(90);
```

Setiap pemanggilan `Add` menyisipkan satu titik ke dalam seri. Urutan titik sesuai dengan posisi sudut di sekitar lingkaran.

## Langkah 5: Menyimpan dokumen yang berisi diagram

Akhirnya, simpan dokumen ke disk. Metode `Save` secara otomatis menulis file .docx, mempertahankan diagram dan semua pemformatan.

```csharp
        // Save the document to a file
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadarChart.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Menjalankan program akan membuat **dokumen Word kosong** yang kini berisi diagram radar yang berfungsi penuh. Buka file tersebut di Microsoft Word untuk melihat hasilnya.

![Diagram radar di dokumen Word](radar_chart.png){alt="Diagram radar disisipkan ke dalam dokumen Word kosong"}

## Variasi umum dan kasus tepi

| Situasi | Apa yang harus diubah |
|-----------|----------------|
| **Ukuran diagram berbeda** | Sesuaikan parameter lebar/tinggi pada `InsertChart`. |
| **Jenis diagram lain** | Ganti `ChartType.Radar` dengan `ChartType.Column`, `ChartType.Pie`, dll., dan pertahankan logika graduasi yang sama. |
| **Menyimpan ke stream** | Gunakan `document.Save(Stream, SaveFormat.Docx)` |

## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}