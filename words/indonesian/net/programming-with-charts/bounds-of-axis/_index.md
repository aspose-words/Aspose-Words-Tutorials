---
"description": "Pelajari cara menetapkan batas sumbu dalam bagan menggunakan Aspose.Words untuk .NET yang mengontrol rentang nilai yang ditampilkan pada sumbu."
"linktitle": "Batas Sumbu Dalam Bagan"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Batas Sumbu Dalam Bagan"
"url": "/id/net/programming-with-charts/bounds-of-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Batas Sumbu Dalam Bagan

## Perkenalan

Apakah Anda ingin membuat dokumen profesional dengan bagan di .NET? Anda berada di tempat yang tepat! Panduan ini akan memandu Anda melalui proses penggunaan Aspose.Words untuk .NET guna menetapkan batas sumbu dalam bagan. Kami akan menguraikan setiap langkah untuk memastikan Anda dapat mengikutinya dengan mudah, meskipun Anda baru mengenal pustaka ini. Jadi, mari kita mulai!

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

- Aspose.Words untuk .NET: Anda dapat [Unduh](https://releases.aspose.com/words/net/) versi terbaru atau menggunakan [uji coba gratis](https://releases.aspose.com/).
- .NET Framework: Pastikan Anda telah menginstal .NET di sistem Anda.
- IDE: Lingkungan pengembangan seperti Visual Studio.

Setelah semuanya siap, kita dapat melanjutkan ke langkah berikutnya.

## Mengimpor Ruang Nama

Untuk memulai, Anda perlu mengimpor namespace yang diperlukan. Ini akan memungkinkan Anda mengakses pustaka Aspose.Words dan fitur pembuatan bagannya.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Langkah 1: Siapkan Direktori Dokumen Anda

Pertama-tama, Anda perlu mengatur direktori tempat dokumen Anda akan disimpan. Ini adalah langkah sederhana tetapi penting untuk mengatur berkas Anda.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Langkah 2: Buat Dokumen Baru

Selanjutnya, buat objek dokumen baru. Dokumen ini akan berfungsi sebagai wadah untuk bagan Anda.

```csharp
Document doc = new Document();
```

## Langkah 3: Inisialisasi Pembuat Dokumen

Kelas DocumentBuilder menyediakan cara cepat dan mudah untuk membuat dokumen. Inisialisasikan kelas ini dengan dokumen Anda.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Langkah 4: Masukkan Bagan

Sekarang, saatnya memasukkan diagram ke dalam dokumen Anda. Dalam contoh ini, kita akan menggunakan diagram Kolom.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## Langkah 5: Hapus Seri yang Ada

Untuk memastikan bahwa Anda memulai dengan keadaan yang bersih, hapus semua seri yang ada dari bagan.

```csharp
chart.Series.Clear();
```

## Langkah 6: Tambahkan Data ke Bagan

Di sini, kami menambahkan data ke bagan. Ini termasuk menentukan nama seri dan titik data.

```csharp
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2 });
```

## Langkah 7: Tetapkan Batas Sumbu

Menetapkan batas untuk sumbu Y memastikan bahwa bagan Anda diskalakan dengan benar.

```csharp
chart.AxisY.Scaling.Minimum = new AxisBound(0);
chart.AxisY.Scaling.Maximum = new AxisBound(6);
```

## Langkah 8: Simpan Dokumen

Terakhir, simpan dokumen Anda ke direktori yang ditentukan.

```csharp
doc.Save(dataDir + "WorkingWithCharts.BoundsOfAxis.docx");
```

Selesai! Anda telah berhasil membuat dokumen dengan bagan menggunakan Aspose.Words for .NET. 

## Kesimpulan

Dengan menggunakan Aspose.Words untuk .NET, Anda dapat dengan mudah membuat dan memanipulasi bagan dalam dokumen Anda. Panduan langkah demi langkah ini telah menunjukkan kepada Anda cara mengatur batas sumbu dalam bagan, sehingga penyajian data Anda menjadi lebih tepat dan profesional. Baik Anda membuat laporan, presentasi, atau dokumen lainnya, Aspose.Words menyediakan alat yang Anda butuhkan.

## Tanya Jawab Umum

### Apa itu Aspose.Words untuk .NET?
Aspose.Words untuk .NET adalah pustaka yang memungkinkan Anda membuat, memodifikasi, dan mengonversi dokumen Word secara terprogram menggunakan kerangka kerja .NET.

### Bagaimana cara mengatur Aspose.Words untuk .NET?
Anda dapat mengunduhnya dari [Di Sini](https://releases.aspose.com/words/net/) dan ikuti petunjuk instalasi yang disediakan.

### Bisakah saya menggunakan Aspose.Words secara gratis?
Ya, Anda bisa menggunakan [uji coba gratis](https://releases.aspose.com/) atau dapatkan [lisensi sementara](https://purchase.aspose.com/temporary-license/).

### Di mana saya dapat menemukan dokumentasi untuk Aspose.Words untuk .NET?
Dokumentasi terperinci tersedia [Di Sini](https://reference.aspose.com/words/net/).

### Bagaimana saya bisa mendapatkan dukungan untuk Aspose.Words?
Anda dapat mengunjungi [forum dukungan](https://forum.aspose.com/c/words/8) untuk bantuan.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}