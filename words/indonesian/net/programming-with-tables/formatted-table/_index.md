---
title: Tabel yang diformat
linktitle: Tabel yang diformat
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara membuat dan memformat tabel dalam dokumen Word menggunakan Aspose.Words untuk .NET dengan panduan langkah demi langkah terperinci ini.
weight: 10
url: /id/net/programming-with-tables/formatted-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tabel yang diformat

## Perkenalan

Membuat dan memformat tabel dalam dokumen Word secara terprogram mungkin tampak seperti tugas yang sulit, tetapi dengan Aspose.Words untuk .NET, hal itu menjadi mudah dan dapat dikelola. Dalam tutorial ini, kami akan memandu Anda untuk membuat tabel yang diformat dalam dokumen Word menggunakan Aspose.Words untuk .NET. Kami akan membahas semuanya mulai dari menyiapkan lingkungan Anda hingga menyimpan dokumen Anda dengan tabel yang diformat dengan indah.

## Prasyarat

Sebelum menyelami kodenya, mari pastikan Anda memiliki semua yang dibutuhkan:

1. Pustaka Aspose.Words untuk .NET: Unduh dari[Di Sini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: IDE seperti Visual Studio.
3. .NET Framework: Pastikan Anda telah menginstal .NET Framework di komputer Anda.

## Mengimpor Ruang Nama

Sebelum menulis kode sebenarnya, Anda perlu mengimpor namespace yang diperlukan:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Langkah 1: Siapkan Direktori Dokumen Anda

Pertama, Anda perlu menentukan jalur tempat dokumen Anda akan disimpan.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Mengganti`"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya tempat Anda ingin menyimpan dokumen.

## Langkah 2: Inisialisasi Dokumen dan DocumentBuilder

Sekarang, inisialisasi dokumen baru dan objek DocumentBuilder.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Itu`DocumentBuilder` adalah kelas pembantu yang menyederhanakan proses pembuatan dokumen.

## Langkah 3: Mulai Tabel

 Selanjutnya, mulailah membuat tabel menggunakan`StartTable` metode.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

Memasukkan sel diperlukan untuk memulai tabel.

## Langkah 4: Terapkan Pemformatan Seluruh Tabel

Anda dapat menerapkan format yang memengaruhi seluruh tabel. Misalnya, mengatur indentasi kiri:

```csharp
table.LeftIndent = 20.0;
```

## Langkah 5: Format Baris Header

Atur tinggi, perataan, dan properti lainnya untuk baris tajuk.

```csharp
builder.RowFormat.Height = 40.0;
builder.RowFormat.HeightRule = HeightRule.AtLeast;
builder.CellFormat.Shading.BackgroundPatternColor = Color.FromArgb(198, 217, 241);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Font.Size = 16;
builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.CellFormat.Width = 100.0;
builder.Write("Header Row,\n Cell 1");
```

Pada langkah ini, kita membuat baris header menonjol dengan mengatur warna latar belakang, ukuran font, dan perataan.

## Langkah 6: Masukkan Sel Header Tambahan

Masukkan lebih banyak sel untuk baris tajuk:

```csharp
builder.InsertCell();
builder.Write("Header Row,\n Cell 2");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Header Row,\n Cell 3");
builder.EndRow();
```

## Langkah 7: Format Baris Isi

Setelah mengatur header, format badan tabel:

```csharp
builder.CellFormat.Shading.BackgroundPatternColor = Color.White;
builder.CellFormat.Width = 100.0;
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.RowFormat.Height = 30.0;
builder.RowFormat.HeightRule = HeightRule.Auto;
```

## Langkah 8: Masukkan Baris Tubuh

Masukkan baris isi dengan konten:

```csharp
builder.InsertCell();
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Write("Row 1, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 1, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 1, Cell 3 Content");
builder.EndRow();
```

Ulangi untuk baris tambahan:

```csharp
builder.InsertCell();
builder.CellFormat.Width = 100.0;
builder.Write("Row 2, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 2, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 2, Cell 3 Content.");
builder.EndRow();
builder.EndTable();
```

## Langkah 9: Simpan Dokumen

Terakhir, simpan dokumen ke direktori yang ditentukan:

```csharp
doc.Save(dataDir + "WorkingWithTables.FormattedTable.docx");
```

Ini akan membuat dan menyimpan dokumen Word dengan tabel yang diformat.

## Kesimpulan

Nah, itu dia! Dengan mengikuti langkah-langkah ini, Anda dapat membuat tabel yang diformat dengan baik dalam dokumen Word menggunakan Aspose.Words for .NET. Pustaka canggih ini memudahkan manipulasi dokumen Word secara terprogram, sehingga menghemat waktu dan tenaga Anda.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?
Aspose.Words untuk .NET adalah pustaka yang hebat untuk membuat, mengedit, dan mengonversi dokumen Word secara terprogram.

### Bisakah saya menggunakan warna yang berbeda untuk baris yang berbeda?
Ya, Anda dapat menerapkan format yang berbeda, termasuk warna, ke baris atau sel yang berbeda.

### Apakah Aspose.Words untuk .NET gratis?
 Aspose.Words untuk .NET adalah pustaka berbayar, tetapi Anda bisa mendapatkannya[uji coba gratis](https://releases.aspose.com/).

### Bagaimana cara mendapatkan dukungan untuk Aspose.Words untuk .NET?
 Anda bisa mendapatkan dukungan dari[Forum komunitas Aspose](https://forum.aspose.com/c/words/8).

### Bisakah saya membuat jenis dokumen lain dengan Aspose.Words untuk .NET?
Ya, Aspose.Words untuk .NET mendukung berbagai format dokumen, termasuk PDF, HTML, dan TXT.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
