---
title: Tambahkan Nilai Tanggal Waktu Ke Sumbu Bagan
linktitle: Tambahkan Nilai Tanggal Waktu Ke Sumbu Bagan
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menambahkan nilai tanggal dan waktu ke sumbu bagan menggunakan Aspose.Words untuk .NET dalam panduan langkah demi langkah yang komprehensif ini.
weight: 10
url: /id/net/programming-with-charts/date-time-values-to-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tambahkan Nilai Tanggal Waktu Ke Sumbu Bagan

## Perkenalan

Membuat bagan dalam dokumen dapat menjadi cara yang ampuh untuk memvisualisasikan data. Saat menangani data deret waktu, menambahkan nilai tanggal dan waktu ke sumbu bagan sangat penting untuk kejelasan. Dalam tutorial ini, kami akan memandu Anda melalui proses menambahkan nilai tanggal dan waktu ke sumbu bagan menggunakan Aspose.Words untuk .NET. Panduan langkah demi langkah ini akan membantu Anda menyiapkan lingkungan, menulis kode, dan memahami setiap bagian dari proses. Mari kita mulai!

## Prasyarat

Sebelum kita memulai, pastikan Anda memiliki prasyarat berikut:

1. Visual Studio atau IDE .NET apa pun: Anda memerlukan lingkungan pengembangan untuk menulis dan menjalankan kode .NET Anda.
2.  Aspose.Words untuk .NET: Anda harus menginstal pustaka Aspose.Words untuk .NET. Anda dapat mengunduhnya dari[Di Sini](https://releases.aspose.com/words/net/).
3. Pengetahuan dasar C#: Tutorial ini mengasumsikan Anda memiliki pemahaman dasar tentang pemrograman C#.
4.  Lisensi Aspose yang valid: Anda dapat memperoleh lisensi sementara dari[Di Sini](https://purchase.aspose.com/temporary-license/).

## Mengimpor Ruang Nama

Untuk memulai, pastikan Anda telah mengimpor namespace yang diperlukan ke dalam proyek Anda. Langkah ini penting untuk mengakses kelas dan metode Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Langkah 1: Siapkan Direktori Dokumen Anda

Pertama, Anda perlu menentukan direktori tempat dokumen Anda akan disimpan. Hal ini penting untuk mengatur berkas-berkas Anda dan memastikan kode Anda berjalan dengan benar.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Langkah 2: Buat Dokumen Baru dan DocumentBuilder

 Selanjutnya, buat instance baru dari`Document` kelas dan a`DocumentBuilder` objek. Objek-objek ini akan membantu Anda membuat dan memanipulasi dokumen Anda.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Langkah 3: Masukkan Bagan ke dalam Dokumen

 Sekarang, masukkan bagan ke dalam dokumen Anda menggunakan`DocumentBuilder` objek. Dalam contoh ini, kami menggunakan bagan kolom, tetapi Anda juga dapat memilih jenis lain.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## Langkah 4: Hapus Seri yang Ada

Hapus semua seri yang ada dalam bagan untuk memastikan Anda memulai dengan lembar kosong. Langkah ini penting untuk data kustom.

```csharp
chart.Series.Clear();
```

## Langkah 5: Tambahkan Nilai Tanggal dan Waktu ke Seri

Tambahkan nilai tanggal dan waktu ke rangkaian bagan. Langkah ini melibatkan pembuatan array untuk tanggal dan nilai terkait.

```csharp
chart.Series.Add("Aspose Series 1",
    new[]
    {
        new DateTime(2017, 11, 06), new DateTime(2017, 11, 09), new DateTime(2017, 11, 15),
        new DateTime(2017, 11, 21), new DateTime(2017, 11, 25), new DateTime(2017, 11, 29)
    },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2, 5.3 });
```

## Langkah 6: Konfigurasikan Sumbu X

Atur skala dan tanda centang untuk sumbu X. Ini memastikan tanggal Anda ditampilkan dengan benar dan pada interval yang tepat.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.Scaling.Minimum = new AxisBound(new DateTime(2017, 11, 05).ToOADate());
xAxis.Scaling.Maximum = new AxisBound(new DateTime(2017, 12, 03).ToOADate());
xAxis.MajorUnit = 7;
xAxis.MinorUnit = 1;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
```

## Langkah 7: Simpan Dokumen

Terakhir, simpan dokumen Anda ke direktori yang ditentukan. Langkah ini mengakhiri proses, dan dokumen Anda sekarang akan berisi bagan dengan nilai tanggal dan waktu pada sumbu X.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DateTimeValuesToAxis.docx");
```

## Kesimpulan

Menambahkan nilai tanggal dan waktu ke sumbu bagan dalam dokumen merupakan proses yang mudah dengan Aspose.Words untuk .NET. Dengan mengikuti langkah-langkah yang diuraikan dalam tutorial ini, Anda dapat membuat bagan yang jelas dan informatif yang memvisualisasikan data deret waktu secara efektif. Baik Anda sedang mempersiapkan laporan, presentasi, atau dokumen apa pun yang memerlukan representasi data terperinci, Aspose.Words menyediakan alat yang Anda butuhkan untuk berhasil.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menggunakan jenis bagan lain dengan Aspose.Words untuk .NET?

Ya, Aspose.Words mendukung berbagai jenis bagan, termasuk garis, batang, pai, dan banyak lagi.

### Bagaimana saya dapat menyesuaikan tampilan grafik saya?

Anda dapat menyesuaikan tampilan dengan mengakses properti bagan dan mengatur gaya, warna, dan banyak lagi.

### Apakah mungkin untuk menambahkan beberapa seri ke bagan?

 Tentu saja! Anda dapat menambahkan beberapa seri ke bagan Anda dengan memanggil`Series.Add` metode beberapa kali dengan data yang berbeda.

### Bagaimana jika saya perlu memperbarui data grafik secara dinamis?

Anda dapat memperbarui data bagan secara dinamis dengan memanipulasi properti seri dan sumbu secara terprogram berdasarkan kebutuhan Anda.

### Di mana saya dapat menemukan dokumentasi yang lebih rinci untuk Aspose.Words untuk .NET?

 Anda dapat menemukan dokumentasi yang lebih rinci[Di Sini](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
