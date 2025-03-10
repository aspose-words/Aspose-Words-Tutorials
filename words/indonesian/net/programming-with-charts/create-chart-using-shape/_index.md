---
title: Membuat & Menyesuaikan Bagan Menggunakan Bentuk
linktitle: Membuat & Menyesuaikan Bagan Menggunakan Bentuk
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara membuat dan menyesuaikan bagan dalam dokumen Word menggunakan Aspose.Words for .NET dengan panduan langkah demi langkah ini. Sempurna untuk visualisasi data.
weight: 10
url: /id/net/programming-with-charts/create-chart-using-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat & Menyesuaikan Bagan Menggunakan Bentuk

## Perkenalan

Membuat dan menyesuaikan diagram pada dokumen Anda merupakan keterampilan penting dalam dunia yang digerakkan oleh data saat ini. Diagram dapat membantu memvisualisasikan data, sehingga informasi yang kompleks menjadi lebih mudah dipahami. Aspose.Words untuk .NET merupakan pustaka canggih yang memungkinkan Anda membuat dan memanipulasi dokumen Word secara terprogram. Dalam tutorial ini, kami akan memandu Anda melalui proses pembuatan dan penyesuaian diagram garis menggunakan Aspose.Words untuk .NET. Di akhir panduan ini, Anda akan dapat membuat diagram yang tampak profesional dengan mudah.

## Prasyarat

Sebelum menyelami kode, pastikan Anda memiliki hal berikut:

-  Pustaka Aspose.Words untuk .NET: Anda dapat mengunduhnya[Di Sini](https://releases.aspose.com/words/net/).
- Visual Studio: Versi apa pun yang mendukung .NET.
- Pengetahuan Dasar C#: Memahami dasar-dasar C# akan membantu Anda mengikuti tutorial.

## Mengimpor Ruang Nama

Untuk memulai, Anda perlu mengimpor namespace yang diperlukan. Langkah ini penting karena memungkinkan Anda menggunakan kelas dan metode yang disediakan oleh Aspose.Words untuk .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Langkah 1: Buat Dokumen Baru

Pertama, Anda perlu membuat dokumen Word baru. Dokumen ini akan berfungsi sebagai kanvas untuk bagan Anda.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Langkah 2: Masukkan Bagan

 Berikutnya, Anda akan memasukkan diagram garis ke dalam dokumen.`DocumentBuilder.InsertChart` metode ini digunakan untuk tujuan ini.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
```

## Langkah 3: Sesuaikan Judul Bagan

Menyesuaikan judul bagan dapat membantu memberikan konteks untuk data yang ditampilkan. Anda dapat menampilkan judul dan mengatur teksnya menggunakan kode berikut:

```csharp
chart.Title.Show = true;
chart.Title.Text = "Line Chart Title";
chart.Title.Overlay = false;
// Harap perhatikan jika nilai null atau kosong ditentukan sebagai teks judul, judul yang dibuat secara otomatis akan ditampilkan.
```

## Langkah 4: Sesuaikan Posisi Legenda

Legenda membantu mengidentifikasi rangkaian data yang berbeda dalam bagan Anda. Anda dapat menyesuaikan posisi dan pengaturan overlay seperti ini:

```csharp
chart.Legend.Position = LegendPosition.Left;
chart.Legend.Overlay = true;
```

## Langkah 5: Simpan Dokumen

Terakhir, Anda perlu menyimpan dokumen tersebut. Langkah ini memastikan bahwa semua perubahan Anda ditulis ke dalam berkas.

```csharp
doc.Save(dataDir + "WorkingWithCharts.CreateChartUsingShape.docx");
```

## Kesimpulan

Dalam tutorial ini, kami membahas cara membuat dan menyesuaikan diagram garis dalam dokumen Word menggunakan Aspose.Words untuk .NET. Dengan mengikuti panduan langkah demi langkah, kini Anda dapat membuat diagram yang menarik secara visual dan mengomunikasikan data Anda secara efektif. Aspose.Words untuk .NET menawarkan berbagai pilihan penyesuaian, yang memungkinkan Anda menyesuaikan diagram dengan kebutuhan spesifik Anda.

## Pertanyaan yang Sering Diajukan

### Dapatkah saya menggunakan Aspose.Words untuk .NET untuk membuat jenis bagan lainnya?

 Ya, Aspose.Words untuk .NET mendukung berbagai jenis bagan, termasuk bagan batang, bagan pai, dan lainnya. Anda dapat menjelajahi dokumentasinya[Di Sini](https://reference.aspose.com/words/net/) untuk lebih jelasnya.

### Bagaimana saya dapat mencoba Aspose.Words untuk .NET sebelum membeli?

 Anda dapat mengunduh versi uji coba gratis dari[Di Sini](https://releases.aspose.com/)Ini memungkinkan Anda menguji pustaka dan fitur-fiturnya sebelum melakukan pembelian.

### Apakah ada cara untuk mendapatkan dukungan jika saya mengalami masalah?

 Tentu saja. Anda dapat mengakses dukungan melalui forum komunitas Aspose[Di Sini](https://forum.aspose.com/c/words/8)Komunitas dan staf Aspose sangat responsif.

### Bagaimana cara membeli lisensi Aspose.Words untuk .NET?

 Anda dapat membeli lisensi langsung dari situs web Aspose[Di Sini](https://purchase.aspose.com/buy)Ada berbagai pilihan lisensi untuk memenuhi berbagai kebutuhan.

### Bagaimana jika saya memerlukan lisensi sementara untuk proyek jangka pendek?

 Aspose menawarkan lisensi sementara, yang dapat Anda minta[Di Sini](https://purchase.aspose.com/temporary-license/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
