---
category: general
date: 2026-08-07
description: Buat diagram lingkaran di Word dengan C# secara cepat. Pelajari cara
  menyisipkan diagram lingkaran, menambahkan label data pada diagram, menampilkan
  persentase diagram, dan menyesuaikan label data diagram.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- show percentage chart
- add data labels pie
- insert pie chart
- customize chart data labels
language: id
lastmod: 2026-08-07
og_description: Buat diagram lingkaran di Word dengan C# menggunakan Aspose.Words.
  Tutorial ini menunjukkan cara menyisipkan diagram lingkaran, menambahkan label data
  pada diagram lingkaran, dan menampilkan persentase diagram sambil menyesuaikan label
  data diagram.
og_image_alt: Word document displaying a pie chart with percentage labels outside
  each slice
og_title: Buat diagram lingkaran di C# – tutorial lengkap
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  headline: Create pie chart word in C# – step‑by‑step guide
  type: TechArticle
- description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  name: Create pie chart word in C# – step‑by‑step guide
  steps:
  - name: Call `chart.Series.Add()` for each additional series.
    text: Call `chart.Series.Add()` for each additional series.
  - name: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
    text: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
  - name: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
    text: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
  type: HowTo
tags:
- pie chart
- C#
- Aspose.Words
- chart customization
title: Membuat diagram lingkaran di C# – panduan langkah demi langkah
url: /id/net/programming-with-charts/create-pie-chart-word-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat pie chart word di C# – panduan langkah demi langkah

Jika Anda perlu **create pie chart word** dokumen di C#, panduan ini menyediakan solusi lengkap yang siap dijalankan. Anda akan melihat cara **insert pie chart**, **add data labels pie**, dan **show percentage chart** sambil **customize chart data labels** untuk tampilan yang halus.

Membuat diagram secara programatik menghemat Anda dari penyuntingan manual, terutama ketika laporan atau dasbor harus dihasilkan secara otomatis. Pada bagian berikut Anda akan mempelajari semua yang diperlukan untuk menyematkan diagram lingkaran berlabel lengkap ke dalam file Word menggunakan Aspose.Words for .NET.

## Prasyarat dan penyiapan

* .NET 6.0 SDK atau yang lebih baru terpasang.  
* Lisensi Aspose.Words for .NET yang valid (atau kunci evaluasi sementara).  
* Visual Studio 2022 (atau IDE apa pun yang mendukung C#).  

Add the Aspose.Words NuGet package to your project:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Jika Anda berencana menghasilkan banyak diagram, aktifkan mode **Free‑Form Drawing** (`DocumentBuilder.UseFreeFormDrawing = true`) untuk kinerja yang lebih baik.

## Membuat pie chart word dengan Aspose.Words

Langkah utama pertama adalah membuat dokumen Word kosong dan sebuah `DocumentBuilder`. Objek ini mengendalikan semua penyisipan selanjutnya.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new blank document and a DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Mengapa ini penting*: `Document` mewakili seluruh file `.docx`, sementara `DocumentBuilder` menyediakan API yang fluently untuk menambahkan paragraf, tabel, dan diagram. Memulai dengan dokumen bersih memastikan tidak ada pemformatan tersembunyi yang mengganggu tata letak diagram.

## Sisipkan pie chart ke dalam dokumen

Sekarang kita menempatkan pie chart dengan ukuran yang diinginkan. Metode `InsertChart` mengembalikan objek `Chart` yang dapat kita konfigurasikan lebih lanjut.

```csharp
// Step 2: Insert a pie chart of the desired size
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

*Mengapa ini penting*: Flag `ChartType.Pie` memberi tahu Aspose.Words untuk menghasilkan diagram melingkar. Lebar (`400`) dan tinggi (`300`) dinyatakan dalam poin, memberikan kontrol yang tepat atas jejak visual.

## Isi diagram dengan data

Sebuah pie chart membutuhkan setidaknya satu seri nilai numerik. Di sini kami menambahkan tiga kategori: “Apples”, “Bananas”, dan “Cherries”.

```csharp
// Populate the first series with sample data
chart.Series[0].AddCategory("Apples", 40);
chart.Series[0].AddCategory("Bananas", 35);
chart.Series[0].AddCategory("Cherries", 25);
```

*Mengapa ini penting*: Setiap pemanggilan `AddCategory` membuat sebuah irisan. Nilai numerik menentukan ukuran irisan, sementara label menjadi nama kategori yang ditampilkan ketika label data diaktifkan.

## Tambahkan data labels pie dan tampilkan persentase diagram

Agar diagram informatif, kami mengaktifkan data labels, menempatkannya di luar irisan, dan meminta Aspose.Words menampilkan baik nama kategori maupun persentasenya.

```csharp
// Step 3: Access the first series' data label collection
ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;

// Step 4: Position labels outside the slices and show useful information
labels.Position = ChartDataLabelPosition.OutsideEnd; // places label outside each slice
labels.ShowCategoryName = true;                     // displays "Apples", "Bananas", …
labels.ShowPercentage = true;                       // displays "40%" etc.
```

*Mengapa ini penting*: Menetapkan `Position` ke `OutsideEnd` meningkatkan keterbacaan, terutama ketika irisan kecil. Mengaktifkan `ShowCategoryName` dan `ShowPercentage` memenuhi persyaratan **show percentage chart** dan memenuhi tujuan **add data labels pie**.

## Kustomisasi label data diagram lebih lanjut (opsional)

Anda mungkin ingin mengubah font, menambahkan garis penghubung, atau menyembunyikan legenda. Potongan kode berikut menunjukkan kustomisasi umum:

```csharp
// Optional: customize label font and leader lines
labels.Font.Size = 10;
labels.Font.Color = System.Drawing.Color.DarkBlue;
labels.ShowLeaderLines = true;

// Optional: hide the default legend because labels already contain the needed info
chart.HasLegend = false;
```

*Mengapa ini penting*: Menyesuaikan tampilan label memastikan diagram sesuai dengan panduan gaya dokumen Anda. Menghapus legenda mengurangi kekacauan visual ketika label data sudah menyampaikan informasi yang sama.

## Simpan dokumen dengan diagram yang telah dikustomisasi

Akhirnya, tulis dokumen ke disk. Pilih jalur yang Anda memiliki akses menulis.

```csharp
// Step 5: Save the document with the customized chart
doc.Save("YOUR_DIRECTORY/ChartWithCustomLabels.docx");
```

Saat Anda membuka `ChartWithCustomLabels.docx` di Microsoft Word, Anda akan melihat sebuah pie chart di mana setiap irisan diberi label dengan nama kategori dan persentasenya, ditempatkan di luar irisan, dan bergaya dengan pengaturan font khusus.

### Output yang diharapkan

| Irisan | Nilai | Persentase | Label yang ditampilkan di Word |
|--------|-------|------------|-------------------------------|
| Apples | 40    | 40 %       | Apples – 40 %                 |
| Bananas| 35    | 35 %       | Bananas – 35 %                |
| Cherries| 25   | 25 %       | Cherries – 25 %               |

Diagram seharusnya terlihat mirip dengan ilustrasi di bawah ini:

![Dokumen Word menampilkan pie chart dengan label persentase di luar setiap irisan](pie-chart-word.png "Contoh create pie chart word")

*Teks alt gambar mencakup kata kunci utama untuk SEO.*

## Menangani beberapa seri dan kasus tepi

Contoh dasar menggunakan satu seri, yang umum untuk pie chart. Jika Anda perlu menampilkan beberapa seri (mis., membandingkan dua tahun), Anda harus:

1. Panggil `chart.Series.Add()` untuk setiap seri tambahan.  
2. Pastikan setiap seri menggunakan kategori yang sama; jika tidak, Aspose.Words akan melempar `ArgumentException`.  
3. Opsional, atur `labels.ShowSeriesName = true` untuk membedakan irisan.

```csharp
// Adding a second series (e.g., sales in 2025)
chart.Series.Add("2025");
chart.Series[1].AddCategory("Apples", 45);
chart.Series[1].AddCategory("Bananas", 30);
chart.Series[1].AddCategory("Cherries", 25);
```

Ketika beberapa seri ada, diagram secara otomatis dirender sebagai **clustered pie** (juga disebut “pie of pies”). Tinjau output untuk memastikan label tetap dapat dibaca.

## Kesalahan umum dan cara menghindarinya

| Masalah | Penyebab | Solusi |
|---------|----------|--------|
| Label tumpang tindih irisan | Area diagram kecil atau banyak kategori | Tingkatkan dimensi diagram (`InsertChart(width, height)`) atau ubah `Position` ke `InsideEnd`. |
| Persentase tidak berjumlah 100 % | Kesalahan pembulatan pada data | Gunakan `labels.ShowPercentage = true` (Aspose.Words secara otomatis menormalkan). |
| Diagram muncul kosong di Word | Lisensi hilang atau batas waktu evaluasi | Pastikan lisensi Aspose.Words yang valid dimuat sebelum membuat dokumen. |
| Warna font berbeda dari tema Word | Font khusus diatur dalam kode | Hapus pengaturan font khusus atau sesuaikan dengan warna tema Word (`System.Drawing.Color.Black`). |

## Kode sumber lengkap (dapat dijalankan)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load license (optional for evaluation)
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a pie chart
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 3. Add data to the first series
        chart.Series[0].AddCategory("Apples", 40);
        chart.Series[0].AddCategory("Bananas", 35);
        chart.Series[0].AddCategory("Cherries", 25);

        // 4. Configure data labels
        ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;
        labels.Position = ChartDataLabelPosition.OutsideEnd;
        labels.ShowCategoryName = true;
        labels.ShowPercentage = true;

        // Optional: further customization
        labels.Font.Size = 10;
        labels.Font.Color = Color.DarkBlue;
        labels.ShowLeaderLines = true;
        chart.HasLegend = false;

        // 5. Save the document
        doc.Save("ChartWithCustomLabels.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Menjalankan program menghasilkan `ChartWithCustomLabels.docx`, yang berisi contoh **create pie chart word** yang memenuhi semua persyaratan yang tercantum dalam tutorial.

## Kesimpulan

Anda kini tahu cara **create pie chart word** dokumen di C# menggunakan Aspose.Words. Panduan ini mencakup penyisipan pie chart, **add data labels pie**, **show percentage chart**, dan **customize chart data labels** untuk menghasilkan file Word yang profesional dan berbasis data.

Dari sini Anda dapat menjelajahi topik terkait seperti **insert pie chart** ke dalam paragraf yang ada, menghasilkan diagram **bar** atau **line**, atau mengotomatiskan pembuatan batch laporan dengan set data yang bervariasi. Bereksperimenlah dengan posisi label yang berbeda, gaya font, dan konfigurasi multi‑seri untuk menyesuaikan output dengan kebutuhan pelaporan spesifik Anda.

Selamat membuat diagram!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Sesuaikan Label Data Diagram](/words/english/net/programming-with-charts/chart-data-label/)
- [Atur Opsi Default untuk Label Data dalam Diagram](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Sisipkan Diagram Kolom dalam Dokumen Word](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}