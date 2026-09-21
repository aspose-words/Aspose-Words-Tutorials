---
category: general
date: 2026-09-21
description: Pelajari cara membuat dokumen Word dengan C# dan menyisipkan diagram
  kolom, mengatur posisi label, serta menampilkan nilai menggunakan Aspose.Words dalam
  panduan langkah demi langkah.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to insert chart
- how to set label
- how to display values
- insert column chart word
language: id
lastmod: 2026-09-21
og_description: Buat dokumen Word C# dengan Aspose.Words. Tutorial ini menunjukkan
  cara menyisipkan diagram kolom, mengatur posisi label, dan menampilkan nilai.
og_image_alt: Screenshot of a Word document created with C# that contains a column
  chart and data labels
og_title: Buat dokumen Word C# – sisipkan diagram kolom, atur label, tampilkan nilai
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  headline: How to create Word document C# with a column chart and formatted labels
  type: TechArticle
- description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  name: How to create Word document C# with a column chart and formatted labels
  steps:
  - name: Expected result
    text: When you open `output.docx`, you should see a single column chart similar
      to the image below. Each column has a numeric label at its top, inside the column,
      displaying the series value.
  - name: Adding custom data to the chart
    text: 'If you need to replace the placeholder data, you can modify the chart’s
      `Series` collection:'
  - name: Changing label font and color
    text: 'You can further customize the label appearance:'
  - name: Inserting multiple charts
    text: The `DocumentBuilder` can insert as many charts as you need. Just call `InsertChart`
      again after moving the cursor with `builder.Writeln()` or `builder.InsertParagraph()`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Charts
title: Cara membuat dokumen Word C# dengan diagram kolom dan label yang diformat
url: /id/net/programming-with-charts/how-to-create-word-document-c-with-a-column-chart-and-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat Word document C# dengan diagram kolom dan label yang diformat

Jika Anda perlu **create Word document C#** yang mencakup diagram, panduan ini menunjukkan secara tepat cara melakukannya. Anda akan belajar cara menyisipkan **column chart**, memposisikan label data‑nya, dan menampilkan nilai label—semua dengan Aspose.Words for .NET.

Membuat file Word yang berisi diagram dulu memerlukan pekerjaan manual di Microsoft Word. Dengan langkah **how to insert chart** yang dijelaskan di sini, Anda dapat mengotomatiskan seluruh proses dari kode, membuat pembuatan laporan menjadi cepat dan dapat diulang. Tutorial ini juga mencakup properti **how to set label** dan **how to display values** sehingga diagram siap untuk pengguna akhir.

Pada akhir artikel ini Anda akan memiliki program C# lengkap yang dapat dijalankan yang membuat file `.docx` berisi diagram kolom dengan label data yang muncul di dalam setiap kolom dan menampilkan nilai numeriknya.

## Prasyarat

* .NET 6.0 SDK atau yang lebih baru terpasang  
* Salinan berlisensi **Aspose.Words for .NET** (versi percobaan gratis dapat digunakan untuk pengujian)  
* IDE seperti Visual Studio 2022 atau Visual Studio Code  

Tidak ada paket NuGet tambahan yang diperlukan selain `Aspose.Words`.

## Langkah 1: Siapkan proyek dan tambahkan Aspose.Words

Buat proyek konsol baru dan tambahkan paket Aspose.Words:

```bash
dotnet new console -n WordChartDemo
cd WordChartDemo
dotnet add package Aspose.Words
```

Perintah `dotnet add package` mengambil versi stabil terbaru dari **Aspose.Words**, yang mencakup API diagram yang digunakan dalam contoh **insert column chart word**.

## Langkah 2: Buat dokumen Word kosong baru

Potongan kode pertama membuat dokumen kosong dan `DocumentBuilder` yang memungkinkan Anda menyisipkan konten. Ini adalah dasar untuk **create word document C#**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 2: Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` mewakili seluruh file `.docx`, sementara `DocumentBuilder` menyediakan metode seperti `InsertParagraph`, `InsertImage`, dan, yang penting untuk tutorial ini, `InsertChart`.

## Langkah 3: Sisipkan diagram kolom (how to insert chart)

Sekarang kita menyisipkan **column chart**. Metode `InsertChart` menerima tipe diagram, lebar, dan tinggi dalam satuan poin.

```csharp
        // Step 3: Insert a column chart with a width of 400 pt and height of 300 pt.
        Chart chart = builder.InsertChart(ChartType.Column, 400, 300);
```

Pada tahap ini diagram berisi seri data default dengan nilai placeholder. Anda dapat mengganti data seri jika memerlukan angka khusus, tetapi untuk mendemonstrasikan **how to set label** dan **how to display values**, data default sudah cukup.

## Langkah 4: Posisi label data di dalam setiap kolom (how to set label)

Label data adalah teks yang muncul pada setiap kolom. Agar diagram lebih mudah dibaca, kami memindahkan label ke dalam kolom dan mengaktifkan nilai numeriknya.

```csharp
        // Step 4: Access the first data label of the first series.
        ChartDataLabel label = chart.DataLabels[0];

        // Position the label at the inside end of the column.
        label.Position = ChartDataLabelPosition.InsideEnd;

        // Show the numeric value of each data point.
        label.ShowValue = true;
```

`ChartDataLabelPosition.InsideEnd` menempatkan label di bagian atas kolom namun tetap berada di dalam bentuk kolom, yang merupakan gaya visual umum untuk laporan. Menetapkan `ShowValue` ke `true` memenuhi persyaratan **how to display values**.

## Langkah 5: Simpan dokumen

Akhirnya, tulis dokumen ke disk. File dapat dibuka dengan Microsoft Word, LibreOffice, atau penampil apa pun yang mendukung format Open XML.

```csharp
        // Step 5: Save the document to the output folder.
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Menjalankan program menghasilkan `output.docx` yang berisi diagram kolom dengan label data yang diposisikan di dalam setiap kolom dan menampilkan nilainya.

### Hasil yang Diharapkan

Saat Anda membuka `output.docx`, Anda akan melihat satu diagram kolom yang mirip dengan gambar di bawah. Setiap kolom memiliki label numerik di bagian atasnya, di dalam kolom, menampilkan nilai seri.

![Diagram dalam dokumen Word yang dibuat dengan C#](/images/word-chart-example.png "Diagram dalam dokumen Word yang dibuat dengan C# – create word document C#")

*Teks alternatif:* *Diagram dalam dokumen Word yang dibuat dengan C# yang menunjukkan cara menyisipkan column chart word dan menampilkan nilai.*

## Variasi umum dan kasus tepi

### Menambahkan data khusus ke diagram

Jika Anda perlu mengganti data placeholder, Anda dapat memodifikasi koleksi `Series` diagram:

```csharp
// Replace the default series with custom values.
chart.Series.Clear();
ChartSeries series = chart.Series.Add(ChartType.Column);
series.Name = "Sales Q1";
series.AddCategory("Jan", 120);
series.AddCategory("Feb", 150);
series.AddCategory("Mar", 180);
```

### Mengubah font dan warna label

Anda dapat menyesuaikan tampilan label lebih lanjut:

```csharp
label.Font.Name = "Arial";
label.Font.Size = 10;
label.Font.Color = System.Drawing.Color.DarkBlue;
```

### Menyisipkan beberapa diagram

`DocumentBuilder` dapat menyisipkan sebanyak mungkin diagram yang Anda perlukan. Cukup panggil `InsertChart` lagi setelah memindahkan kursor dengan `builder.Writeln()` atau `builder.InsertParagraph()`.

## Tips Pro

* **Pro tip:** Set `chart.HasTitle = true` dan tetapkan `chart.Title.Text` untuk memberikan diagram judul yang deskriptif. Ini meningkatkan aksesibilitas bagi pembaca layar.
* **Watch out for:** Saat menyimpan ke jaringan bersama, pastikan aplikasi memiliki izin menulis; jika tidak `doc.Save` akan melempar `UnauthorizedAccessException`.
* **Performance tip:** Gunakan kembali satu instance `DocumentBuilder` untuk beberapa penyisipan; membuat builder baru untuk setiap operasi menambah beban yang tidak perlu.

## Kesimpulan

Sekarang Anda tahu cara **create Word document C#** yang berisi diagram kolom, cara menyisipkan elemen **insert chart**, mengatur posisi **set label**, dan **display values** di dalam setiap kolom. Contoh kode lengkap di atas siap dijalankan, dan Anda dapat memperluasnya dengan data khusus, gaya, atau diagram tambahan.

Selanjutnya, jelajahi topik terkait seperti **how to insert picture**, **how to generate tables**, atau **how to apply document themes** untuk membuat laporan otomatis Anda lebih kaya. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Sisipkan Diagram Kolom di Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Sisipkan Diagram Kolom Sederhana di Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Sisipkan Diagram Area di Dokumen Word | Aspose.Words untuk .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}