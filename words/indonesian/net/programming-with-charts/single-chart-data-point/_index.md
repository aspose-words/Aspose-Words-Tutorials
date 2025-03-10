---
title: Menyesuaikan Titik Data Bagan Tunggal Dalam Bagan
linktitle: Menyesuaikan Titik Data Bagan Tunggal Dalam Bagan
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menyesuaikan titik data grafik tunggal menggunakan Aspose.Words untuk .NET dalam panduan langkah demi langkah yang terperinci. Sempurnakan grafik Anda dengan penanda dan ukuran yang unik.
weight: 10
url: /id/net/programming-with-charts/single-chart-data-point/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menyesuaikan Titik Data Bagan Tunggal Dalam Bagan

## Perkenalan

Pernahkah Anda bertanya-tanya bagaimana Anda dapat membuat grafik Anda menonjol dengan titik data yang unik? Nah, hari ini adalah hari keberuntungan Anda! Kami akan membahas cara menyesuaikan satu titik data grafik menggunakan Aspose.Words untuk .NET. Bersiaplah untuk mengikuti tutorial langkah demi langkah yang tidak hanya informatif tetapi juga menyenangkan dan mudah diikuti.

## Prasyarat

Sebelum kita memulai, mari pastikan Anda telah menyiapkan semua hal penting:

-  Aspose.Words untuk Pustaka .NET: Pastikan Anda memiliki versi terbaru.[Unduh di sini](https://releases.aspose.com/words/net/).
- .NET Framework: Pastikan Anda telah menginstal .NET Framework di komputer Anda.
- Pemahaman Dasar C#: Pemahaman dasar tentang pemrograman C# akan sangat membantu.
- Lingkungan Pengembangan Terpadu (IDE): Visual Studio direkomendasikan.

## Mengimpor Ruang Nama

Hal pertama yang harus dilakukan, mari impor namespace yang diperlukan untuk memulai:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Langkah 1: Inisialisasi Dokumen dan DocumentBuilder

Baiklah, mari kita mulai dengan menginisialisasi dokumen baru dan DocumentBuilder. Ini akan menjadi kanvas untuk bagan kita.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Di Sini,`dataDir` adalah jalur direktori tempat Anda menyimpan dokumen Anda.`DocumentBuilder` kelas membantu dalam menyusun dokumen.

## Langkah 2: Masukkan Bagan

Selanjutnya, mari masukkan diagram garis ke dalam dokumen. Ini akan menjadi tempat kita untuk menyesuaikan titik data.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
```

 Itu`InsertChart` Metode ini mengambil tipe grafik, lebar, dan tinggi sebagai parameter. Dalam kasus ini, kita memasukkan grafik garis dengan lebar 432 dan tinggi 252.

## Langkah 3: Akses Seri Bagan

Sekarang, saatnya mengakses rangkaian dalam bagan kita. Bagan dapat memiliki beberapa rangkaian, dan setiap rangkaian berisi titik data.

```csharp
ChartSeries series0 = chart.Series[0];
ChartSeries series1 = chart.Series[1];
```

Di sini, kita mengakses dua seri pertama dalam bagan kita. 

## Langkah 4: Kustomisasi Titik Data

Di sinilah keajaiban terjadi! Mari kita sesuaikan titik data tertentu dalam rangkaian kita.

```csharp
ChartDataPointCollection dataPointCollection = series0.DataPoints;
ChartDataPoint dataPoint00 = dataPointCollection[0];
ChartDataPoint dataPoint01 = dataPointCollection[1];
```

Kami mengambil titik data dari seri pertama. Sekarang, mari kita sesuaikan titik-titik ini.

### Sesuaikan Titik Data 00

```csharp
dataPoint00.Explosion = 50;
dataPoint00.Marker.Symbol = MarkerSymbol.Circle;
dataPoint00.Marker.Size = 15;
```

 Untuk`dataPoint00`, kami menetapkan ledakan (berguna untuk diagram lingkaran), mengubah simbol penanda menjadi lingkaran, dan menetapkan ukuran penanda menjadi 15.

### Sesuaikan Titik Data 01

```csharp
dataPoint01.Marker.Symbol = MarkerSymbol.Diamond;
dataPoint01.Marker.Size = 20;
```

 Untuk`dataPoint01`, kita mengubah simbol penanda menjadi berlian dan mengatur ukuran penanda menjadi 20.

### Kustomisasi Titik Data di Seri 1

```csharp
ChartDataPoint dataPoint12 = series1.DataPoints[2];
dataPoint12.InvertIfNegative = true;
dataPoint12.Marker.Symbol = MarkerSymbol.Star;
dataPoint12.Marker.Size = 20;
```

 Untuk titik data ketiga di`series1`, kita mengaturnya untuk terbalik jika nilainya negatif, mengubah simbol penanda menjadi bintang, dan mengatur ukuran penanda menjadi 20.

## Langkah 5: Simpan Dokumen

Terakhir, mari simpan dokumen kita dengan semua penyesuaian.

```csharp
doc.Save(dataDir + "WorkingWithCharts.SingleChartDataPoint.docx");
```

 Baris ini menyimpan dokumen di direktori yang Anda tentukan dengan nama`WorkingWithCharts.SingleChartDataPoint.docx`.

## Kesimpulan

Nah, itu dia! Anda telah berhasil menyesuaikan titik data individual dalam bagan menggunakan Aspose.Words for .NET. Dengan mengubah beberapa properti, Anda dapat membuat bagan Anda jauh lebih informatif dan menarik secara visual. Jadi, silakan bereksperimen dengan berbagai penanda dan ukuran untuk melihat mana yang paling cocok untuk data Anda.

## Pertanyaan yang Sering Diajukan

### Dapatkah saya menyesuaikan titik data pada jenis bagan lainnya?

Tentu saja! Anda dapat menyesuaikan titik data dalam berbagai jenis bagan, termasuk bagan batang, bagan pai, dan lainnya. Prosesnya serupa di berbagai jenis bagan.

### Apakah mungkin untuk menambahkan label khusus ke titik data?

 Ya, Anda dapat menambahkan label khusus ke titik data menggunakan`ChartDataPoint.Label` properti. Hal ini memungkinkan Anda untuk memberikan lebih banyak konteks untuk setiap titik data.

### Bagaimana cara menghapus titik data dari suatu seri?

 Anda dapat menghapus titik data dengan menyetel visibilitasnya menjadi salah menggunakan`dataPoint.IsVisible = false`.

### Dapatkah saya menggunakan gambar sebagai penanda titik data?

Meskipun Aspose.Words tidak mendukung penggunaan gambar secara langsung sebagai penanda, Anda dapat membuat bentuk khusus dan menggunakannya sebagai penanda.

### Mungkinkah menganimasikan titik data pada bagan?

Aspose.Words untuk .NET tidak mendukung animasi untuk titik data bagan. Namun, Anda dapat membuat bagan animasi menggunakan alat lain dan menyematkannya ke dalam dokumen Word Anda.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
