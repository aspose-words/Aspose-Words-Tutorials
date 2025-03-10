---
title: Mengatur Opsi Default untuk Label Data dalam Bagan
linktitle: Mengatur Opsi Default untuk Label Data dalam Bagan
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menetapkan opsi default untuk label data dalam bagan menggunakan Aspose.Words untuk .NET. Ikuti panduan langkah demi langkah kami untuk membuat dan menyesuaikan bagan dengan mudah.
weight: 10
url: /id/net/programming-with-charts/default-options-for-data-labels/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mengatur Opsi Default untuk Label Data dalam Bagan

## Perkenalan

Hai! Apakah Anda bersemangat untuk terjun ke dunia otomatisasi dokumen? Hari ini, kita akan menjelajahi cara menggunakan Aspose.Words untuk .NET guna membuat dokumen yang menakjubkan secara terprogram. Aspose.Words adalah pustaka canggih yang memungkinkan Anda memanipulasi dokumen Word dengan mudah, dan dalam tutorial ini, kita akan fokus pada pengaturan opsi default untuk label data dalam bagan. Baik Anda pengembang berpengalaman atau pemula, panduan ini akan memandu Anda melalui setiap langkah agar Anda dapat langsung menggunakannya.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki semua yang dibutuhkan untuk mengikuti tutorial ini. Berikut ini daftar periksa singkatnya:

- Visual Studio atau IDE lain yang kompatibel dengan .NET: Di sinilah Anda menulis dan menjalankan kode Anda.
-  Aspose.Words untuk .NET: Anda dapat[unduh versi terbaru](https://releases.aspose.com/words/net/) dan menginstalnya di proyek Anda.
- Pengetahuan dasar pemrograman C#: Meskipun panduan ini ramah bagi pemula, sedikit pengetahuan tentang C# akan sangat membantu.
- .NET Framework terinstal: Pastikan Anda telah menginstal .NET Framework di komputer Anda.
-  Lisensi sementara untuk Aspose.Words: Dapatkan satu[Di Sini](https://purchase.aspose.com/temporary-license/) untuk membuka fungsionalitas penuh.

Setelah Anda menyelesaikan prasyarat ini, kita siap berangkat!

## Mengimpor Ruang Nama

Pertama-tama, mari kita siapkan proyek kita dan impor namespace yang diperlukan. Namespace ini penting untuk mengakses fungsionalitas Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.ReportingServices;
```

## Langkah 1: Buat Dokumen Baru


 Perjalanan dimulai dengan membuat dokumen baru dan menginisialisasi`DocumentBuilder` . Itu`DocumentBuilder` Kelas menyediakan serangkaian metode untuk memanipulasi konten dokumen dengan mudah.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Buat dokumen baru
Document doc = new Document();

// Inisialisasi DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Penjelasan

 Pada langkah ini, kami telah menyiapkan dokumen dan pembangun yang akan kami gunakan untuk memasukkan dan memformat konten kami.`dataDir` Variabel ini menyimpan jalur tempat kita menyimpan dokumen akhir kita.

## Langkah 2: Masukkan Bagan

 Selanjutnya, kita akan menambahkan diagram lingkaran ke dokumen kita.`InsertChart` metode dari`DocumentBuilder` kelas membuat hal ini sangat mudah.

```csharp
// Masukkan diagram lingkaran
Shape shape = builder.InsertChart(ChartType.Pie, 432, 252);

// Mengakses objek bagan
Chart chart = shape.Chart;
```

### Penjelasan

Di sini, kita memasukkan diagram lingkaran ke dalam dokumen kita.`InsertChart` Metode ini memerlukan tipe grafik, lebar, dan tinggi sebagai parameter. Setelah memasukkan grafik, kita mengakses objek grafik untuk memanipulasinya lebih lanjut.

## Langkah 3: Sesuaikan Seri Bagan

Sekarang, kita akan menghapus seri yang ada di bagan dan menambahkan seri kustom kita. Seri ini akan mewakili titik data kita.

```csharp
// Hapus rangkaian grafik yang ada
chart.Series.Clear();

// Tambahkan seri baru ke bagan
ChartSeries series = chart.Series.Add("Aspose Series 1",
    new string[] { "Category 1", "Category 2", "Category 3" },
    new double[] { 2.7, 3.2, 0.8 });
```

### Penjelasan

Pada langkah ini, kami memastikan bagan kami kosong dengan menghapus semua seri yang sudah ada sebelumnya. Kemudian, kami menambahkan seri baru dengan kategori dan nilai khusus, yang akan ditampilkan dalam bagan pai kami.

## Langkah 4: Tetapkan Opsi Default untuk Label Data

Label data sangat penting untuk membuat bagan Anda informatif. Kami akan menetapkan opsi untuk menampilkan persentase, nilai, dan menyesuaikan pemisah.

```csharp
// Mengakses koleksi label data
ChartDataLabelCollection labels = series.DataLabels;

// Tetapkan opsi label data
labels.ShowPercentage = true;
labels.ShowValue = true;
labels.ShowLeaderLines = false;
labels.Separator = " - ";
```

### Penjelasan

 Di sini, kita mengakses`DataLabels`properti seri kami untuk menyesuaikan tampilan dan informasi yang ditampilkan pada setiap label data. Kami telah memilih untuk menampilkan persentase dan nilai, menyembunyikan garis pembatas, dan menetapkan pemisah khusus.

## Langkah 5: Simpan Dokumen

Terakhir, kita akan menyimpan dokumen kita ke direktori yang ditentukan. Langkah ini memastikan bahwa semua perubahan kita ditulis ke dalam sebuah berkas.

```csharp
// Simpan dokumen
doc.Save(dataDir + "WorkingWithCharts.DefaultOptionsForDataLabels.docx");
```

### Penjelasan

 Pada langkah terakhir ini, kita menyimpan dokumen kita menggunakan`Save` metode. Dokumen akan disimpan di direktori yang ditentukan oleh`dataDir`, dengan nama "WorkingWithCharts.DefaultOptionsForDataLabels.docx".

## Kesimpulan

Nah, itu dia! Anda telah berhasil membuat dokumen Word dengan diagram lingkaran yang disesuaikan menggunakan Aspose.Words untuk .NET. Pustaka canggih ini memudahkan Anda mengotomatiskan pembuatan dan manipulasi dokumen, sehingga menghemat waktu dan tenaga. Baik Anda membuat laporan, faktur, atau jenis dokumen lainnya, Aspose.Words siap membantu Anda.

 Jangan ragu untuk menjelajahi[Dokumentasi Aspose.Words](https://reference.aspose.com/words/net/) untuk fitur dan contoh lebih lanjut. Selamat membuat kode!

## Pertanyaan yang Sering Diajukan

### Dapatkah saya menggunakan Aspose.Words secara gratis?
Anda dapat menggunakan Aspose.Words secara gratis dengan[lisensi sementara](https://purchase.aspose.com/temporary-license/) atau jelajahi fitur-fiturnya menggunakan[uji coba gratis](https://releases.aspose.com/).

### Bagaimana cara mendapatkan dukungan untuk Aspose.Words?
 Anda bisa mendapatkan dukungan melalui[Forum dukungan Aspose.Words](https://forum.aspose.com/c/words/8).

### Bisakah saya menambahkan jenis grafik lainnya?
 Ya, Aspose.Words mendukung berbagai jenis grafik seperti grafik batang, garis, dan kolom. Periksa[dokumentasi](https://reference.aspose.com/words/net/) untuk lebih jelasnya.

### Apakah Aspose.Words kompatibel dengan .NET Core?
 Ya, Aspose.Words kompatibel dengan .NET Core. Anda dapat menemukan informasi lebih lanjut di[dokumentasi](https://reference.aspose.com/words/net/).

### Bagaimana saya dapat membeli lisensi untuk Aspose.Words?
 Anda dapat membeli lisensi dari[Toko Aspose](https://purchase.aspose.com/buy).


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
