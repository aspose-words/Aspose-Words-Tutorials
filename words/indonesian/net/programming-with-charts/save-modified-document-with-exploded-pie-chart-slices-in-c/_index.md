---
category: general
date: 2026-10-13
description: 'Simpan dokumen yang telah dimodifikasi setelah menyesuaikan diagram
  lingkaran: memisahkan irisan, mengubah sudut irisan pertama, dan menampilkan label
  persentase dalam C#.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save modified document
- show percentage labels
- explode pie chart slices
- display percentages pie
- change first slice
language: id
lastmod: 2026-10-13
og_description: Simpan dokumen yang telah dimodifikasi setelah menyesuaikan diagram
  lingkaran di C#. Pelajari cara memisahkan irisan diagram lingkaran, mengubah sudut
  irisan pertama, dan menampilkan label persentase.
og_image_alt: Screenshot of a Word document where the pie chart slices are exploded
  and percentage labels are displayed after saving the modified document
og_title: Simpan dokumen yang dimodifikasi dengan potongan diagram lingkaran yang
  terpisah – Panduan C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 'Save modified document after customizing a pie chart: explode slices,
    change first slice angle, and show percentage labels in C#.'
  headline: Save modified document with exploded pie chart slices in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word chart
- pie chart
- document manipulation
title: Simpan dokumen yang dimodifikasi dengan irisan diagram lingkaran yang terpisah
  di C#
url: /id/net/programming-with-charts/save-modified-document-with-exploded-pie-chart-slices-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Simpan dokumen yang dimodifikasi dengan irisan diagram pai yang meledak di C#

Jika Anda perlu **save modified document** setelah mengubah diagram pai Word, panduan ini menunjukkan cara melakukannya secara tepat. Anda akan belajar meledakkan irisan diagram pai, mengubah sudut irisan pertama, dan menampilkan label persentase—semua dengan beberapa baris kode C#.

Menyesuaikan diagram adalah kebutuhan umum saat menghasilkan laporan, faktur, atau dasbor secara programatik. Pada akhir tutorial ini Anda akan dapat memuat file DOCX, mengubah tampilan diagram, dan **save modified document** siap untuk didistribusikan.

## Prasyarat

- .NET 6.0 atau yang lebih baru (kode juga berfungsi dengan .NET Framework 4.6+)
- Aspose.Words untuk .NET 23.10 atau yang lebih baru (versi percobaan gratis atau salinan berlisensi)
- File Word (`input.docx`) yang berisi satu diagram pai
- Visual Studio 2022 atau IDE C# apa pun

> **Tip:** Paket NuGet Aspose.Words ditambahkan dengan `dotnet add package Aspose.Words`.

## Langkah 1: Muat dokumen Word yang berisi diagram

Langkah pertama adalah membuka file DOCX sumber. Kelas `Document` mewakili seluruh file Word dalam memori.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

Memuat dokumen memberi Anda akses penuh ke setiap node, termasuk shape yang menampung diagram.

## Langkah 2: Dapatkan shape diagram pertama dari dokumen

Diagram disimpan di dalam node `Shape`. Anda dapat menemukan diagram pertama dengan `GetChild`.

```csharp
        // Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
```

Jika dokumen berisi beberapa diagram, sesuaikan indeks (`0`) atau iterasi melalui koleksi. Baris ini memastikan Anda memiliki referensi ke objek `Chart` yang akan dimodifikasi.

## Langkah 3: Meledakkan irisan diagram pai

Meleledakkan sebuah irisan memisahkannya dari sisa diagram pai, sehingga diagram lebih mudah dibaca. Properti `Explode` bekerja untuk seluruh seri.

```csharp
        // Enable slice explosion so each slice is separated from the pie
        chart.PieChart.Explode = true;
```

Mengatur `Explode` ke `true` **explodes pie chart slices** untuk seluruh seri, yang berguna ketika Anda ingin setiap irisan menonjol.

## Langkah 4: Ubah sudut irisan pertama

Kadang-kadang Anda perlu irisan pertama dimulai pada sudut khusus, misalnya untuk disesuaikan dengan pedoman desain.

```csharp
        // Set a custom start angle for the first slice (30 degrees)
        chart.PieChart.FirstSliceAngle = 30;
```

Properti `FirstSliceAngle` **changes first slice** orientasi, memutar seluruh diagram pai sehingga irisan pertama dimulai pada 30 derajat.

## Langkah 5: Tampilkan label persentase pada irisan diagram pai

Menampilkan kontribusi numerik setiap irisan sering diperlukan dalam laporan. Flag `DataLabel.ShowPercentage` mengaktifkan nilai persentase.

```csharp
        // Display percentage values on the data labels of the pie slices
        chart.PieChart.DataLabel.ShowPercentage = true;
```

Langkah ini **show percentage labels** langsung pada diagram, yang juga memenuhi persyaratan **display percentages pie**.

## Langkah 6: Simpan dokumen yang dimodifikasi

Setelah semua penyesuaian diterapkan, simpan perubahan ke file baru. Metode `Save` menulis DOCX yang diperbarui ke disk.

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY\output.docx");
    }
}
```

Sekarang Anda memiliki **save modified document** yang berisi diagram pai yang meledak, irisan pertama yang diputar, dan label persentase yang terlihat.

![Save modified document showing exploded pie chart](/images/pie-chart-exploded.png "Save modified document with exploded pie chart slices and percentage labels")

*Tangkapan layar ini menggambarkan output akhir setelah dokumen disimpan.*

## Contoh lengkap yang dapat dijalankan

Menggabungkan semua bagian, berikut program lengkap yang dapat Anda salin‑tempel ke dalam proyek konsol:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace PieChartCustomizer
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source DOCX
            Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

            // 2️⃣ Get the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Explode all slices
            chart.PieChart.Explode = true;

            // 4️⃣ Rotate the first slice to 30°
            chart.PieChart.FirstSliceAngle = 30;

            // 5️⃣ Show percentages on each slice
            chart.PieChart.DataLabel.ShowPercentage = true;

            // 6️⃣ Persist the changes
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Hasil yang diharapkan

Membuka `output.docx` akan menampilkan diagram pai dimana:

- Setiap irisan sedikit terpisah (**exploded pie chart slices**)
- Irisan pertama dimulai pada offset 30 derajat (**change first slice**)
- Setiap irisan menampilkan kontribusinya sebagai persentase (**show percentage labels**, **display percentages pie**)
- File telah **save modified document** tanpa mengubah yang asli.

## Pertanyaan umum dan kasus tepi

| Pertanyaan | Jawaban |
|------------|---------|
| **Bagaimana jika dokumen tidak memiliki diagram?** | Kode memeriksa `null` setelah `GetChild`. Jika tidak ada diagram, Anda dapat menambahkan satu secara programatik atau menghentikan dengan pesan yang jelas. |
| **Apakah saya dapat meledakkan hanya satu irisan?** | Ya. Gunakan `chart.PieChart.Series[0].DataPoints[i].Explosion = true;` dimana `i` adalah indeks irisan. |
| **Bagaimana cara mengubah format label (mis., tampilkan nilai + %)?** | Atur `chart.PieChart.DataLabel.ShowValue = true;` dan secara opsional `chart.PieChart.DataLabel.ShowPercentage = true;` untuk menggabungkan keduanya. |
| **Apakah gaya diagram dipertahankan setelah disimpan?** | Aspose.Words mempertahankan semua gaya, termasuk warna dan font, ketika Anda **save modified document**. |
| **Apakah saya dapat memproses beberapa diagram dalam file yang sama?** | Iterasi melalui semua node `Shape` dengan `NodeType.Shape` dan saring dengan `shape.HasChart`. Terapkan langkah yang sama pada setiap diagram. |

## Kesimpulan

Anda sekarang tahu cara **save modified document** setelah menyesuaikan diagram pai di Word secara programatik. Panduan ini mencakup meledakkan irisan diagram pai, mengubah sudut irisan pertama, dan menampilkan label persentase—memenuhi persyaratan **show percentage labels**, **explode pie chart slices**, **display percentages pie**, dan **change first slice**.

Selanjutnya, pertimbangkan untuk mengeksplorasi:

- Menambahkan seri data secara dinamis (`chart.Series.Add(...)`)  
- Menyesuaikan penempatan legenda dan judul diagram  
- Mengonversi DOCX ke PDF sambil mempertahankan gaya diagram  

Silakan bereksperimen dengan sudut yang berbeda, pengaturan ledakan, atau format label untuk menyesuaikan kebutuhan pelaporan Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [How to Save Edited Document in C# with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-docsaveoptions/how-to-save-edited-document-in-c-with-aspose-words-step-by-s/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}