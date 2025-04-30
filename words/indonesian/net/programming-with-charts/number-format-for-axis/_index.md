---
"description": "Pelajari cara memformat angka sumbu bagan menggunakan Aspose.Words untuk .NET dengan panduan langkah demi langkah ini. Tingkatkan keterbacaan dan profesionalisme dokumen Anda dengan mudah."
"linktitle": "Format Angka Untuk Sumbu Dalam Bagan"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Format Angka Untuk Sumbu Dalam Bagan"
"url": "/id/net/programming-with-charts/number-format-for-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Format Angka Untuk Sumbu Dalam Bagan

## Perkenalan

Hai! Pernahkah Anda bekerja dengan diagram dalam dokumen Anda dan berharap dapat memformat angka pada sumbu agar terlihat lebih profesional? Nah, Anda beruntung! Dalam tutorial ini, kita akan membahas secara mendalam cara mencapainya dengan menggunakan Aspose.Words untuk .NET. Pustaka canggih ini memungkinkan Anda menangani dokumen Word semudah membuat pai. Dan hari ini, kami berfokus untuk memberikan perubahan pada sumbu diagram tersebut dengan format angka khusus.

## Prasyarat

Sebelum kita mulai, mari pastikan Anda memiliki semua yang Anda butuhkan. Berikut daftar periksa singkatnya:

- Aspose.Words untuk .NET: Pastikan Anda telah menginstalnya. Jika belum, Anda dapat [unduh disini](https://releases.aspose.com/words/net/).
- .NET Framework: Pastikan Anda telah menginstal .NET Framework yang kompatibel.
- Lingkungan Pengembangan: IDE seperti Visual Studio akan bekerja dengan sempurna.
- Pengetahuan Dasar C#: Ini akan membantu Anda mengikuti contoh pengkodean.

## Mengimpor Ruang Nama

Pertama-tama, Anda perlu mengimpor namespace yang diperlukan dalam proyek Anda. Ini seperti meletakkan fondasi sebelum membangun rumah. Tambahkan perintah berikut di bagian atas berkas kode Anda:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Reporting;
```

Sekarang, mari kita uraikan prosesnya menjadi langkah-langkah yang sederhana dan mudah diikuti.

## Langkah 1: Menyiapkan Dokumen

Judul: Inisialisasi Dokumen Anda

Pertama, Anda perlu membuat dokumen baru dan pembuat dokumen. Anggaplah langkah ini sebagai persiapan kanvas dan kuas sebelum memulai karya agung Anda.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Di Sini, `dataDir` adalah jalur ke direktori dokumen tempat Anda akan menyimpan file akhir. `Document` Dan `DocumentBuilder` adalah kelas dari Aspose.Words yang membantu Anda membuat dan memanipulasi dokumen Word.

## Langkah 2: Memasukkan Bagan

Judul: Tambahkan Bagan ke Dokumen Anda

Selanjutnya, mari tambahkan diagram ke dokumen Anda. Di sinilah keajaiban dimulai. Kita akan menyisipkan diagram kolom yang akan berfungsi sebagai kanvas kosong.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

Itu `InsertChart` metode menyisipkan bagan dengan jenis tertentu (Kolom dalam kasus ini) dan dimensi ke dalam dokumen.

## Langkah 3: Menyesuaikan Seri Bagan

Judul: Isi Bagan Anda dengan Data

Sekarang, kita perlu menambahkan beberapa data ke bagan kita. Langkah ini sama seperti mengisi bagan Anda dengan informasi yang bermakna.

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1900000, 850000, 2100000, 600000, 1500000 });
```

Di sini, kami menambahkan seri baru yang disebut "Aspose Series 1" dengan lima titik data. `Series.Clear` metode ini memastikan semua data yang sudah ada sebelumnya dihapus sebelum menambahkan seri baru kami.

## Langkah 4: Memformat Angka Sumbu

Judul: Percantik Angka Poros Anda

Terakhir, mari kita format angka-angka pada sumbu Y agar lebih mudah dibaca. Ini seperti memberikan sentuhan akhir pada karya seni Anda.

```csharp
chart.AxisY.NumberFormat.FormatCode = "#,##0";
```

Itu `FormatCode` properti memungkinkan Anda untuk mengatur format khusus untuk angka pada sumbu. Dalam contoh ini, `#,##0` memastikan bahwa angka besar ditampilkan dengan koma untuk ribuan.

## Langkah 5: Menyimpan Dokumen

Judul: Simpan Karya Agung Anda

Setelah semuanya diatur, saatnya menyimpan dokumen Anda. Langkah ini merupakan pengungkapan besar-besaran atas hasil kerja Anda.

```csharp
doc.Save(dataDir + "WorkingWithCharts.NumberFormatForAxis.docx");
```

Di sini, `Save` metode menyimpan dokumen ke jalur yang ditentukan dengan nama file `WorkingWithCharts.NumberFormatForAxis.docx`.

## Kesimpulan

Nah, itu dia! Anda telah berhasil memformat angka pada sumbu Y bagan Anda menggunakan Aspose.Words untuk .NET. Ini tidak hanya membuat bagan Anda tampak lebih profesional, tetapi juga meningkatkan keterbacaan. Aspose.Words menawarkan banyak fitur yang dapat membantu Anda membuat dokumen Word yang menakjubkan secara terprogram. Jadi, mengapa tidak mencoba lebih jauh dan melihat apa lagi yang dapat Anda lakukan?

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?
Aspose.Words untuk .NET adalah pustaka hebat yang memungkinkan pengembang untuk membuat, memanipulasi, dan mengonversi dokumen Word secara terprogram.

### Bisakah saya memformat aspek lain dari bagan selain nomor sumbu?
Tentu saja! Aspose.Words untuk .NET memungkinkan Anda memformat judul, label, dan bahkan menyesuaikan tampilan bagan.

### Apakah ada uji coba gratis yang tersedia untuk Aspose.Words untuk .NET?
Ya, Anda bisa mendapatkannya [uji coba gratis di sini](https://releases.aspose.com/).

### Dapatkah saya menggunakan Aspose.Words untuk .NET dengan bahasa .NET lain selain C#?
Ya, Aspose.Words untuk .NET kompatibel dengan bahasa .NET apa pun, termasuk VB.NET dan F#.

### Di mana saya dapat menemukan dokumentasi yang lebih rinci?
Dokumentasi terperinci tersedia di [Halaman dokumentasi Aspose.Words untuk .NET](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}