---
"description": "Pelajari cara menyisipkan diagram area ke dalam dokumen menggunakan Aspose.Words untuk .NET. Tambahkan data seri dan simpan dokumen dengan diagram tersebut."
"linktitle": "Masukkan Bagan Area Ke Dalam Dokumen Word"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Masukkan Bagan Area Ke Dalam Dokumen Word"
"url": "/id/net/programming-with-charts/insert-area-chart/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Masukkan Bagan Area Ke Dalam Dokumen Word

## Perkenalan

Selamat datang di panduan langkah demi langkah tentang cara menyisipkan bagan area ke dalam dokumen Word menggunakan Aspose.Words untuk .NET. Baik Anda pengembang berpengalaman atau baru memulai, tutorial ini akan memandu Anda melalui semua hal yang perlu Anda ketahui untuk membuat bagan area yang menakjubkan dan informatif dalam dokumen Word Anda. Kami akan membahas prasyaratnya, menunjukkan kepada Anda cara mengimpor namespace yang diperlukan, dan memandu Anda melalui setiap langkah proses dengan petunjuk yang jelas dan mudah diikuti.

## Prasyarat

Sebelum kita mulai, mari pastikan Anda memiliki semua yang dibutuhkan untuk memulai:

1. Aspose.Words untuk .NET: Pastikan Anda telah menginstal Aspose.Words untuk .NET. Anda dapat mengunduhnya [Di Sini](https://releases.aspose.com/words/net/).
2. .NET Framework: Pastikan Anda telah menginstal .NET Framework di komputer Anda.
3. IDE: Lingkungan Pengembangan Terpadu (IDE) seperti Visual Studio untuk menulis dan mengeksekusi kode Anda.
4. Pengetahuan Dasar C#: Pemahaman dasar tentang pemrograman C# akan sangat membantu.

Setelah Anda memiliki prasyarat ini, Anda siap untuk mulai membuat bagan area yang indah di dokumen Word Anda.

## Mengimpor Ruang Nama

Pertama-tama, mari impor namespace yang diperlukan. Namespace ini menyediakan kelas dan metode yang diperlukan untuk bekerja dengan dokumen dan grafik Word di Aspose.Words for .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
```

Sekarang setelah kita mengimpor namespace penting, mari lanjutkan ke pembuatan dokumen dan penyisipan bagan area langkah demi langkah.

## Langkah 1: Buat Dokumen Word Baru

Mari kita mulai dengan membuat dokumen Word baru. Ini akan menjadi dasar tempat kita akan menyisipkan diagram area.

```csharp
// Jalur ke direktori dokumen Anda 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

Pada langkah ini, kita menginisialisasi yang baru `Document` objek yang mewakili dokumen Word kita.

## Langkah 2: Gunakan DocumentBuilder untuk Menyisipkan Bagan

Selanjutnya, kita akan menggunakan `DocumentBuilder` kelas untuk menyisipkan bagan area ke dalam dokumen kita.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
```

Di sini, kita membuat `DocumentBuilder` objek dan menggunakannya untuk menyisipkan bagan area dengan dimensi tertentu (432x252) ke dalam dokumen kita.

## Langkah 3: Akses Objek Bagan

Setelah memasukkan grafik, kita perlu mengakses `Chart` objek untuk menyesuaikan bagan area kami.

```csharp
Chart chart = shape.Chart;
```

Baris kode ini mengambil `Chart` objek dari bentuk yang baru saja kita masukkan.

## Langkah 4: Tambahkan Data Seri ke Bagan

Sekarang, saatnya menambahkan beberapa data ke bagan kita. Kita akan menambahkan rangkaian dengan tanggal dan nilai yang sesuai.

```csharp
chart.Series.Add("Aspose Series 1", new []
{
    new DateTime(2002, 05, 01),
    new DateTime(2002, 06, 01),
    new DateTime(2002, 07, 01),
    new DateTime(2002, 08, 01),
    new DateTime(2002, 09, 01)
}, 
new double[] { 32, 32, 28, 12, 15 });
```

Pada langkah ini, kami menambahkan seri bernama "Aspose Series 1" dengan serangkaian tanggal dan nilai yang sesuai.

## Langkah 5: Simpan Dokumen

Terakhir, kita akan menyimpan dokumen kita dengan bagan area yang disisipkan.

```csharp
doc.Save(dataDir + "WorkingWithCharts.InsertAreaChart.docx");
```

Baris kode ini menyimpan dokumen ke direktori yang ditentukan dengan nama file yang diberikan.

## Kesimpulan

Selamat! Anda telah berhasil memasukkan diagram area ke dalam dokumen Word menggunakan Aspose.Words untuk .NET. Panduan ini telah memandu Anda melalui setiap langkah, mulai dari menyiapkan lingkungan hingga menyimpan dokumen akhir. Dengan Aspose.Words untuk .NET, Anda dapat membuat berbagai diagram dan elemen kompleks lainnya dalam dokumen Word, sehingga laporan dan presentasi Anda menjadi lebih dinamis dan informatif.

## Pertanyaan yang Sering Diajukan

### Dapatkah saya menggunakan Aspose.Words untuk .NET dengan bahasa .NET lainnya?
Ya, Aspose.Words untuk .NET mendukung bahasa .NET lainnya seperti VB.NET.

### Apakah mungkin untuk menyesuaikan tampilan grafik?
Tentu saja! Aspose.Words untuk .NET menyediakan berbagai opsi untuk menyesuaikan tampilan grafik Anda.

### Bisakah saya menambahkan beberapa bagan ke satu dokumen Word?
Ya, Anda dapat menyisipkan bagan sebanyak yang Anda perlukan ke dalam satu dokumen Word.

### Apakah Aspose.Words untuk .NET mendukung jenis bagan lainnya?
Ya, Aspose.Words untuk .NET mendukung berbagai jenis bagan termasuk batang, garis, pai, dan banyak lagi.

### Di mana saya bisa mendapatkan lisensi sementara untuk Aspose.Words untuk .NET?
Anda dapat memperoleh lisensi sementara dari [Di Sini](https://purchase.aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}