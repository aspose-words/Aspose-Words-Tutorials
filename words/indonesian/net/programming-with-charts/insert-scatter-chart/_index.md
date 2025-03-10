---
title: Masukkan Bagan Sebar ke dalam Dokumen Word
linktitle: Masukkan Bagan Sebar ke dalam Dokumen Word
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menyisipkan diagram sebar di Word dengan Aspose.Words untuk .NET. Langkah mudah untuk mengintegrasikan representasi data visual ke dalam dokumen Anda.
weight: 10
url: /id/net/programming-with-charts/insert-scatter-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Masukkan Bagan Sebar ke dalam Dokumen Word

## Perkenalan

Dalam tutorial ini, Anda akan mempelajari cara memanfaatkan Aspose.Words for .NET untuk menyisipkan diagram sebar ke dalam dokumen Word Anda. Diagram sebar adalah alat visual canggih yang dapat secara efektif menampilkan titik data berdasarkan dua variabel, membuat dokumen Anda lebih menarik dan informatif.

## Prasyarat

Sebelum kita mulai membuat diagram sebar dengan Aspose.Words untuk .NET, pastikan Anda memiliki prasyarat berikut:

1.  Pemasangan Aspose.Words untuk .NET: Unduh dan pasang Aspose.Words untuk .NET dari[Di Sini](https://releases.aspose.com/words/net/).
   
2. Pengetahuan Dasar C#: Keakraban dengan bahasa pemrograman C# dan kerangka kerja .NET akan bermanfaat.

## Mengimpor Ruang Nama

Untuk memulai, Anda perlu mengimpor namespace yang diperlukan dalam proyek C# Anda:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
```

Sekarang, mari kita uraikan proses penyisipan diagram sebar ke dalam dokumen Word Anda menggunakan Aspose.Words untuk .NET:

## Langkah 1: Inisialisasi Dokumen dan DocumentBuilder

 Pertama, inisialisasikan instance baru dari`Document` kelas dan`DocumentBuilder` kelas untuk mulai membuat dokumen Anda.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Langkah 2: Masukkan Bagan Sebar

 Gunakan`InsertChart` metode dari`DocumentBuilder` kelas untuk menyisipkan diagram sebar ke dalam dokumen.

```csharp
Shape shape = builder.InsertChart(ChartType.Scatter, 432, 252);
Chart chart = shape.Chart;
```

## Langkah 3: Tambahkan Seri Data ke Bagan

Sekarang, tambahkan rangkaian data ke diagram sebar Anda. Contoh ini menunjukkan penambahan rangkaian dengan titik data tertentu.

```csharp
chart.Series.Add("Aspose Series 1", new double[] { 0.7, 1.8, 2.6 }, new double[] { 2.7, 3.2, 0.8 });
```

## Langkah 4: Simpan Dokumen

 Terakhir, simpan dokumen yang dimodifikasi ke lokasi yang Anda inginkan menggunakan`Save` metode dari`Document` kelas.

```csharp
doc.Save(dataDir + "WorkingWithCharts.InsertScatterChart.docx");
```

## Kesimpulan

Selamat! Anda telah berhasil mempelajari cara menyisipkan diagram sebar ke dalam dokumen Word Anda menggunakan Aspose.Words untuk .NET. Diagram sebar adalah alat yang sangat baik untuk memvisualisasikan hubungan data, dan dengan Aspose.Words, Anda dapat dengan mudah mengintegrasikannya ke dalam dokumen Anda untuk meningkatkan kejelasan dan pemahaman.

## Pertanyaan yang Sering Diajukan

### Dapatkah saya menyesuaikan tampilan diagram sebar menggunakan Aspose.Words?
Ya, Aspose.Words memungkinkan kustomisasi ekstensif pada properti bagan seperti warna, sumbu, dan label.

### Apakah Aspose.Words kompatibel dengan berbagai versi Microsoft Word?
Aspose.Words mendukung berbagai versi Microsoft Word, memastikan kompatibilitas di berbagai platform.

### Apakah Aspose.Words menyediakan dukungan untuk jenis bagan lainnya?
Ya, Aspose.Words mendukung berbagai jenis bagan termasuk bagan batang, bagan garis, dan bagan pai.

### Dapatkah saya memperbarui data dalam diagram sebar secara dinamis dan terprogram?
Tentu saja, Anda dapat memperbarui data bagan secara dinamis menggunakan panggilan API Aspose.Words.

### Di mana saya bisa mendapatkan bantuan atau dukungan lebih lanjut untuk Aspose.Words?
 Untuk bantuan lebih lanjut, kunjungi[Forum dukungan Aspose.Words](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
