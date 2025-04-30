---
"description": "Pelajari cara menyesuaikan label data bagan menggunakan Aspose.Words untuk .NET dalam panduan langkah demi langkah. Sempurna untuk pengembang .NET."
"linktitle": "Sesuaikan Label Data Bagan"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Sesuaikan Label Data Bagan"
"url": "/id/net/programming-with-charts/chart-data-label/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sesuaikan Label Data Bagan

## Perkenalan

Apakah Anda ingin mempercantik aplikasi .NET Anda dengan kemampuan pemrosesan dokumen yang dinamis dan disesuaikan? Aspose.Words untuk .NET mungkin jawabannya! Dalam panduan ini, kita akan menyelami lebih dalam penyesuaian label data bagan menggunakan Aspose.Words untuk .NET, pustaka yang hebat untuk membuat, memodifikasi, dan mengonversi dokumen Word. Apakah Anda seorang pengembang berpengalaman atau baru memulai, tutorial ini akan memandu Anda melalui setiap langkah, memastikan Anda memahami cara menggunakan alat ini secara efektif.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

1. Visual Studio: Instal Visual Studio 2019 atau yang lebih baru.
2. .NET Framework: Pastikan Anda memiliki .NET Framework 4.0 atau yang lebih baru.
3. Aspose.Words untuk .NET: Unduh dan instal Aspose.Words untuk .NET dari [tautan unduhan](https://releases.aspose.com/words/net/).
4. Pengetahuan Dasar C#: Keakraban dengan pemrograman C# sangatlah penting.
5. Lisensi yang Sah: Dapatkan Lisensi yang Sah [lisensi sementara](https://purchase.aspose.com/temporary-license/) atau membeli satu dari [tautan pembelian](https://purchase.aspose.com/buy).

## Mengimpor Ruang Nama

Untuk memulai, Anda perlu mengimpor namespace yang diperlukan ke dalam proyek C# Anda. Langkah ini penting karena memastikan bahwa Anda memiliki akses ke semua kelas dan metode yang disediakan oleh Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Charts;
```

## Langkah 1: Inisialisasi Dokumen dan DocumentBuilder

Untuk membuat dan memanipulasi dokumen Word, pertama-tama kita perlu menginisialisasi instance dari `Document` kelas dan a `DocumentBuilder` obyek.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Penjelasan

- Dokumen doc: Membuat contoh baru kelas Dokumen.
- Pembangun DocumentBuilder: DocumentBuilder membantu memasukkan konten ke dalam objek Dokumen.

## Langkah 2: Masukkan Bagan

Selanjutnya, kita akan memasukkan diagram batang ke dalam dokumen menggunakan `DocumentBuilder` obyek.

```csharp
Shape shape = builder.InsertChart(ChartType.Bar, 432, 252);
Chart chart = shape.Chart;
```

### Penjelasan

- Bentuk bentuk: Mewakili bagan sebagai bentuk dalam dokumen.
- builder.InsertChart(ChartType.Bar, 432, 252): Menyisipkan diagram batang dengan dimensi yang ditentukan.

## Langkah 3: Akses Seri Bagan

Untuk menyesuaikan label data, pertama-tama kita perlu mengakses seri dalam bagan.

```csharp
ChartSeries series0 = shape.Chart.Series[0];
```

### Penjelasan

- ChartSeries series0: Mengambil seri pertama bagan, yang akan kita sesuaikan.

## Langkah 4: Kustomisasi Label Data

Label data dapat disesuaikan untuk menampilkan berbagai informasi. Kami akan mengonfigurasi label untuk menampilkan kunci legenda, nama seri, dan nilai, sambil menyembunyikan nama kategori dan persentase.

```csharp
ChartDataLabelCollection labels = series0.DataLabels;
labels.ShowLegendKey = true;
labels.ShowLeaderLines = true;
labels.ShowCategoryName = false;
labels.ShowPercentage = false;
labels.ShowSeriesName = true;
labels.ShowValue = true;
labels.Separator = "/";
```

### Penjelasan

- Label ChartDataLabelCollection: Mengakses label data seri.
- label.ShowLegendKey: Menampilkan kunci legenda.
- labels.ShowLeaderLines: Menampilkan garis pemimpin untuk label data yang diposisikan jauh di luar titik data.
- label.ShowCategoryName: Menyembunyikan nama kategori.
- label.ShowPercentage: Menyembunyikan nilai persentase.
- label.ShowSeriesName: Menampilkan nama seri.
- label.ShowValue: Menampilkan nilai titik data.
- labels.Separator: Mengatur pemisah untuk label data.

## Langkah 5: Simpan Dokumen

Terakhir, simpan dokumen ke direktori yang ditentukan.

```csharp
doc.Save(dataDir + "WorkingWithCharts.ChartDataLabel.docx");
```

### Penjelasan

- doc.Save: Menyimpan dokumen dengan nama yang ditentukan dalam direktori yang disediakan.

## Kesimpulan

Selamat! Anda telah berhasil menyesuaikan label data bagan menggunakan Aspose.Words untuk .NET. Pustaka ini menawarkan solusi yang kuat untuk menangani dokumen Word secara terprogram, sehingga memudahkan pengembang untuk membuat aplikasi pemrosesan dokumen yang canggih dan dinamis. Pelajari lebih lanjut [dokumentasi](https://reference.aspose.com/words/net/) untuk menjelajahi lebih banyak fitur dan kemampuan.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?
Aspose.Words untuk .NET adalah pustaka pemrosesan dokumen canggih yang memungkinkan pengembang untuk membuat, memodifikasi, dan mengonversi dokumen Word secara terprogram.

### Bagaimana cara menginstal Aspose.Words untuk .NET?
Anda dapat mengunduh dan menginstalnya dari [tautan unduhan](https://releases.aspose.com/words/net/)Ikuti petunjuk instalasi yang diberikan.

### Dapatkah saya mencoba Aspose.Words untuk .NET secara gratis?
Ya, Anda bisa mendapatkannya [uji coba gratis](https://releases.aspose.com/) atau sebuah [lisensi sementara](https://purchase.aspose.com/temporary-license/) untuk mengevaluasi produk.

### Apakah Aspose.Words untuk .NET kompatibel dengan .NET Core?
Ya, Aspose.Words untuk .NET kompatibel dengan .NET Core, .NET Standard, dan .NET Framework.

### Di mana saya bisa mendapatkan dukungan untuk Aspose.Words untuk .NET?
Anda dapat mengunjungi [forum dukungan](https://forum.aspose.com/c/words/8) untuk bantuan dan asistensi dari komunitas dan pakar Aspose.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}