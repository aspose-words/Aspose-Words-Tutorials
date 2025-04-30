---
"description": "Pelajari cara menyembunyikan sumbu bagan dalam dokumen Word menggunakan Aspose.Words untuk .NET dengan tutorial langkah demi langkah terperinci kami."
"linktitle": "Sembunyikan Sumbu Bagan Dalam Dokumen Word"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Sembunyikan Sumbu Bagan Dalam Dokumen Word"
"url": "/id/net/programming-with-charts/hide-chart-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sembunyikan Sumbu Bagan Dalam Dokumen Word

## Perkenalan

Membuat dokumen Word yang dinamis dan menarik secara visual sering kali melibatkan penyertaan diagram dan grafik. Salah satu skenario tersebut mungkin memerlukan penyembunyian sumbu diagram untuk presentasi yang lebih rapi. Aspose.Words untuk .NET menyediakan API yang komprehensif dan mudah digunakan untuk tugas tersebut. Tutorial ini akan memandu Anda melalui langkah-langkah untuk menyembunyikan sumbu diagram dalam dokumen Word menggunakan Aspose.Words untuk .NET.

## Prasyarat

Sebelum kita masuk ke tutorial, pastikan Anda memiliki prasyarat berikut:

- Aspose.Words untuk .NET: Anda dapat mengunduhnya dari [Di Sini](https://releases.aspose.com/words/net/).
- Lingkungan Pengembangan: Setiap IDE yang mendukung pengembangan .NET, seperti Visual Studio.
- .NET Framework: Pastikan Anda telah menginstal .NET Framework di komputer Anda.
- Pengetahuan Dasar C#: Keakraban dengan bahasa pemrograman C# akan bermanfaat.

## Mengimpor Ruang Nama

Untuk mulai bekerja dengan Aspose.Words untuk .NET, Anda perlu mengimpor namespace yang diperlukan dalam proyek Anda. Berikut cara melakukannya:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

Mari kita uraikan prosesnya menjadi langkah-langkah yang sederhana dan mudah diikuti.

## Langkah 1: Inisialisasi Dokumen dan DocumentBuilder

Langkah pertama melibatkan pembuatan dokumen Word baru dan menginisialisasi objek DocumentBuilder.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Pada langkah ini, kita tentukan jalur penyimpanan dokumen. Kemudian kita buat jalur baru `Document` objek dan sebuah `DocumentBuilder` objek untuk mulai membangun dokumen kita.

## Langkah 2: Masukkan Bagan

Selanjutnya kita akan memasukkan grafik ke dalam dokumen menggunakan `DocumentBuilder` obyek.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

Di sini, kami menyisipkan bagan kolom dengan dimensi yang ditentukan. `InsertChart` metode mengembalikan `Shape` objek yang berisi bagan.

## Langkah 3: Hapus Seri yang Ada

Sebelum menambahkan data baru ke bagan, kita perlu menghapus semua seri yang ada.

```csharp
chart.Series.Clear();
```

Langkah ini memastikan bahwa semua data default pada bagan dihapus, memberi ruang bagi data baru yang akan kita tambahkan berikutnya.

## Langkah 4: Tambahkan Data Seri

Sekarang, mari tambahkan seri data kita sendiri ke bagan.

```csharp
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2 });
```

Pada langkah ini, kami menambahkan seri berjudul "Aspose Series 1" dengan kategori dan nilai yang sesuai.

## Langkah 5: Sembunyikan Sumbu Y

Untuk menyembunyikan sumbu Y pada grafik, kita cukup mengatur `Hidden` properti sumbu Y ke `true`.

```csharp
chart.AxisY.Hidden = true;
```

Baris kode ini menyembunyikan sumbu Y, membuatnya tidak terlihat dalam bagan.

## Langkah 6: Simpan Dokumen

Terakhir, simpan dokumen ke direktori yang ditentukan.

```csharp
doc.Save(dataDir + "WorkingWithCharts.HideChartAxis.docx");
```

Perintah ini menyimpan dokumen Word beserta bagan ke jalur yang ditentukan.

## Kesimpulan

Selamat! Anda telah berhasil mempelajari cara menyembunyikan sumbu grafik dalam dokumen Word menggunakan Aspose.Words for .NET. Pustaka canggih ini memudahkan manipulasi dokumen Word secara terprogram. Dengan mengikuti langkah-langkah ini, Anda dapat membuat dokumen yang disesuaikan dan tampak profesional dengan usaha minimal.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?
Aspose.Words untuk .NET adalah API yang hebat untuk membuat, mengedit, mengonversi, dan memanipulasi dokumen Word dalam aplikasi .NET.

### Bisakah saya menyembunyikan sumbu X dan Y dalam bagan?
Ya, Anda dapat menyembunyikan kedua sumbu dengan mengatur `Hidden` milik keduanya `AxisX` Dan `AxisY` ke `true`.

### Apakah ada uji coba gratis yang tersedia untuk Aspose.Words untuk .NET?
Ya, Anda bisa mendapatkan uji coba gratis [Di Sini](https://releases.aspose.com/).

### Di mana saya dapat menemukan dokumentasi lebih lanjut?
Anda dapat menemukan dokumentasi terperinci di Aspose.Words untuk .NET [Di Sini](https://reference.aspose.com/words/net/).

### Bagaimana saya bisa mendapatkan dukungan untuk Aspose.Words untuk .NET?
Anda bisa mendapatkan dukungan dari komunitas Aspose [Di Sini](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}