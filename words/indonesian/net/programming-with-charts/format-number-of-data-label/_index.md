---
title: Format Nomor Label Data Dalam Bagan
linktitle: Format Nomor Label Data Dalam Bagan
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara memformat label data dalam bagan menggunakan Aspose.Words untuk .NET dengan panduan langkah demi langkah ini. Sempurnakan dokumen Word Anda dengan mudah.
weight: 10
url: /id/net/programming-with-charts/format-number-of-data-label/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Format Nomor Label Data Dalam Bagan

## Perkenalan

Membuat dokumen yang menarik dan informatif sering kali melibatkan penyertaan bagan dengan label data yang diformat dengan baik. Jika Anda seorang pengembang .NET yang ingin menyempurnakan dokumen Word Anda dengan bagan yang canggih, Aspose.Words for .NET adalah pustaka yang fantastis untuk membantu Anda mencapainya. Tutorial ini akan memandu Anda melalui proses pemformatan label angka dalam bagan menggunakan Aspose.Words for .NET, langkah demi langkah.

## Prasyarat

Sebelum menyelami kodenya, ada beberapa prasyarat yang perlu Anda penuhi:

-  Aspose.Words untuk .NET: Pastikan Anda telah menginstal pustaka Aspose.Words untuk .NET. Jika Anda belum menginstalnya, Anda dapat[unduh disini](https://releases.aspose.com/words/net/).
- Lingkungan Pengembangan: Anda harus menyiapkan lingkungan pengembangan .NET. Visual Studio sangat direkomendasikan.
- Pengetahuan Dasar C#: Keakraban dengan pemrograman C# sangat penting karena tutorial ini melibatkan penulisan dan pemahaman kode C#.
-  Lisensi Sementara: Untuk menggunakan Aspose.Words tanpa batasan apa pun, Anda bisa mendapatkan lisensi sementara.[lisensi sementara](https://purchase.aspose.com/temporary-license/).

Sekarang, mari selami proses langkah demi langkah dalam memformat label angka dalam bagan.

## Mengimpor Ruang Nama

Pertama-tama, kita perlu mengimpor namespace yang diperlukan untuk bekerja dengan Aspose.Words untuk .NET. Tambahkan baris berikut di bagian atas file C# Anda:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Langkah 1: Siapkan Direktori Dokumen Anda

Sebelum Anda dapat mulai memanipulasi dokumen Word, Anda perlu menentukan direktori tempat dokumen akan disimpan. Hal ini penting untuk operasi penyimpanan nanti.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Mengganti`"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya ke direktori dokumen Anda.

## Langkah 2: Inisialisasi Dokumen dan DocumentBuilder

 Langkah selanjutnya adalah menginisialisasi yang baru`Document` dan sebuah`DocumentBuilder` . Itu`DocumentBuilder` adalah kelas pembantu yang memungkinkan kita menyusun konten dokumen.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Langkah 3: Masukkan Bagan ke dalam Dokumen

 Sekarang, mari masukkan grafik ke dalam dokumen menggunakan`DocumentBuilder`Dalam tutorial ini, kita akan menggunakan diagram garis sebagai contoh.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
chart.Title.Text = "Data Labels With Different Number Format";
```

Di sini, kita menyisipkan bagan Garis dengan lebar dan tinggi tertentu, dan menetapkan judul bagan.

## Langkah 4: Hapus Seri Default dan Tambahkan Seri Baru

Secara default, diagram akan memiliki beberapa seri yang telah dibuat sebelumnya. Kita perlu menghapusnya dan menambahkan seri kita sendiri dengan titik data tertentu.

```csharp
// Hapus seri yang dihasilkan secara default.
chart.Series.Clear();

// Tambahkan seri baru dengan titik data khusus.
ChartSeries series1 = chart.Series.Add("Aspose Series 1", 
	new string[] { "Category 1", "Category 2", "Category 3" }, 
	new double[] { 2.5, 1.5, 3.5 });
```

## Langkah 5: Aktifkan Label Data

Untuk menampilkan label data pada bagan, kita perlu mengaktifkannya untuk seri kita.

```csharp
series1.HasDataLabels = true;
series1.DataLabels.ShowValue = true;
```

## Langkah 6: Format Label Data

Inti dari tutorial ini adalah memformat label data. Kita dapat menerapkan format angka yang berbeda pada setiap label data secara individual.

```csharp
series1.DataLabels[0].NumberFormat.FormatCode = "\"$\"#,##0.00"; // Format mata uang
series1.DataLabels[1].NumberFormat.FormatCode = "dd/mm/yyyy"; // Format tanggal
series1.DataLabels[2].NumberFormat.FormatCode = "0.00%"; // Format persentase
```

 Selain itu, Anda dapat menautkan format label data ke sel sumber. Saat ditautkan,`NumberFormat` akan diatur ulang ke umum dan diwarisi dari sel sumber.

```csharp
series1.DataLabels[2].NumberFormat.IsLinkedToSource = true;
```

## Langkah 7: Simpan Dokumen

Terakhir, simpan dokumen ke direktori yang ditentukan.

```csharp
doc.Save(dataDir + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

Ini akan menyimpan dokumen Anda dengan nama yang ditentukan dan memastikan bagan Anda dengan label data yang diformat dipertahankan.

## Kesimpulan

Memformat label data dalam bagan menggunakan Aspose.Words untuk .NET dapat meningkatkan keterbacaan dan profesionalisme dokumen Word Anda. Dengan mengikuti panduan langkah demi langkah ini, Anda sekarang dapat membuat bagan, menambahkan seri data, dan memformat label data sesuai kebutuhan Anda. Aspose.Words untuk .NET adalah alat canggih yang memungkinkan kustomisasi dan otomatisasi dokumen Word secara ekstensif, menjadikannya aset yang sangat berharga bagi pengembang .NET.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?
Aspose.Words untuk .NET adalah pustaka yang hebat untuk membuat, memanipulasi, dan mengonversi dokumen Word secara terprogram menggunakan C#.

### Bisakah saya memformat jenis bagan lain dengan Aspose.Words untuk .NET?
Ya, Aspose.Words untuk .NET mendukung berbagai jenis bagan, termasuk batang, kolom, pai, dan banyak lagi.

### Bagaimana cara mendapatkan lisensi sementara untuk Aspose.Words untuk .NET?
Anda bisa mendapatkan lisensi sementara[Di Sini](https://purchase.aspose.com/temporary-license/).

### Apakah mungkin untuk menghubungkan label data ke sel sumber di Excel?
Ya, Anda dapat menautkan label data ke sel sumber, yang memungkinkan format angka diwarisi dari sel sumber.

### Di mana saya dapat menemukan dokumentasi yang lebih rinci untuk Aspose.Words untuk .NET?
 Anda dapat menemukan dokumentasi yang lengkap[Di Sini](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
