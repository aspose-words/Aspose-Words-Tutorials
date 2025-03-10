---
title: Tentukan Properti Sumbu XY Dalam Bagan
linktitle: Tentukan Properti Sumbu XY Dalam Bagan
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menentukan properti sumbu XY dalam bagan menggunakan Aspose.Words untuk .NET dengan panduan langkah demi langkah ini. Sempurna untuk pengembang .NET.
weight: 10
url: /id/net/programming-with-charts/define-xyaxis-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tentukan Properti Sumbu XY Dalam Bagan

## Perkenalan

Bagan merupakan alat yang ampuh untuk memvisualisasikan data. Saat Anda perlu membuat dokumen profesional dengan bagan dinamis, Aspose.Words for .NET merupakan pustaka yang sangat berharga. Artikel ini akan memandu Anda melalui proses mendefinisikan properti sumbu XY dalam bagan menggunakan Aspose.Words for .NET, menguraikan setiap langkah untuk memastikan kejelasan dan kemudahan pemahaman.

## Prasyarat

Sebelum menyelami pengkodean, ada beberapa prasyarat yang perlu Anda siapkan:

1. Aspose.Words untuk .NET: Pastikan Anda memiliki pustaka Aspose.Words untuk .NET. Anda dapat[unduh disini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Anda memerlukan lingkungan pengembangan terintegrasi (IDE) seperti Visual Studio.
3. .NET Framework: Pastikan lingkungan pengembangan Anda disiapkan untuk pengembangan .NET.
4. Pengetahuan Dasar C#: Panduan ini mengasumsikan Anda memiliki pemahaman dasar tentang pemrograman C#.

## Mengimpor Ruang Nama

Untuk memulai, Anda perlu mengimpor namespace yang diperlukan dalam proyek Anda. Ini memastikan Anda memiliki akses ke semua kelas dan metode yang diperlukan untuk membuat dan memanipulasi dokumen dan diagram.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

Kami akan menguraikan prosesnya menjadi beberapa langkah sederhana, yang masing-masing berfokus pada bagian tertentu dalam mendefinisikan properti sumbu XY dalam bagan.

## Langkah 1: Inisialisasi Dokumen dan DocumentBuilder

 Pertama, Anda perlu menginisialisasi dokumen baru dan`DocumentBuilder` objek. Itu`DocumentBuilder` membantu memasukkan konten ke dalam dokumen.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Langkah 2: Masukkan Bagan

Berikutnya, Anda akan menyisipkan diagram ke dalam dokumen. Dalam contoh ini, kita akan menggunakan diagram Area. Anda dapat menyesuaikan dimensi diagram sesuai kebutuhan.

```csharp
// Sisipkan bagan
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
Chart chart = shape.Chart;
```

## Langkah 3: Hapus Seri Default dan Tambahkan Data Kustom

Secara default, bagan akan memiliki beberapa seri yang telah ditentukan sebelumnya. Kita akan menghapusnya dan menambahkan seri data kustom kita.

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
	new DateTime[]
	{
		new DateTime(2002, 01, 01), new DateTime(2002, 06, 01), new DateTime(2002, 07, 01),
		new DateTime(2002, 08, 01), new DateTime(2002, 09, 01)
	},
	new double[] { 640, 320, 280, 120, 150 });
```

## Langkah 4: Tentukan Properti Sumbu X

Sekarang, saatnya menentukan properti untuk sumbu X. Ini termasuk pengaturan jenis kategori, penyesuaian persilangan sumbu, dan penyesuaian tanda centang dan label.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.CategoryType = AxisCategoryType.Category;
xAxis.Crosses = AxisCrosses.Custom;
xAxis.CrossesAt = 3; //Diukur dalam satuan tampilan sumbu Y (ratusan).
xAxis.ReverseOrder = true;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
xAxis.TickLabelOffset = 200;
```

## Langkah 5: Tentukan Properti Sumbu Y

Demikian pula, Anda akan mengatur properti untuk sumbu Y. Ini termasuk pengaturan posisi label tanda centang, unit utama dan minor, unit tampilan, dan skala.

```csharp
ChartAxis yAxis = chart.AxisY;
yAxis.TickLabelPosition = AxisTickLabelPosition.High;
yAxis.MajorUnit = 100;
yAxis.MinorUnit = 50;
yAxis.DisplayUnit.Unit = AxisBuiltInUnit.Hundreds;
yAxis.Scaling.Minimum = new AxisBound(100);
yAxis.Scaling.Maximum = new AxisBound(700);
```

## Langkah 6: Simpan Dokumen

Terakhir, simpan dokumen ke direktori yang Anda tentukan. Ini akan menghasilkan dokumen Word dengan bagan yang disesuaikan.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

## Kesimpulan

Membuat dan menyesuaikan bagan dalam dokumen Word menggunakan Aspose.Words for .NET mudah dilakukan setelah Anda memahami langkah-langkah yang terlibat. Panduan ini memandu Anda melalui proses mendefinisikan properti sumbu XY dalam bagan, mulai dari menginisialisasi dokumen hingga menyimpan produk akhir. Dengan keterampilan ini, Anda dapat membuat bagan terperinci dan tampak profesional yang menyempurnakan dokumen Anda.

## Pertanyaan yang Sering Diajukan

### Jenis bagan apa yang dapat saya buat dengan Aspose.Words untuk .NET?
Anda dapat membuat berbagai jenis bagan, termasuk Area, Batang, Garis, Pai, dan banyak lagi.

### Bagaimana cara menginstal Aspose.Words untuk .NET?
 Anda dapat mengunduh Aspose.Words untuk .NET dari[Di Sini](https://releases.aspose.com/words/net/)dan ikuti petunjuk instalasi yang disediakan.

### Bisakah saya menyesuaikan tampilan grafik saya?
Ya, Aspose.Words untuk .NET memungkinkan kustomisasi bagan yang luas, termasuk warna, font, dan properti sumbu.

### Apakah ada uji coba gratis yang tersedia untuk Aspose.Words untuk .NET?
 Ya, Anda bisa mendapatkan uji coba gratis[Di Sini](https://releases.aspose.com/).

### Di mana saya dapat menemukan lebih banyak tutorial dan dokumentasi?
 Anda dapat menemukan lebih banyak tutorial dan dokumentasi terperinci di[Halaman dokumentasi Aspose.Words untuk .NET](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
