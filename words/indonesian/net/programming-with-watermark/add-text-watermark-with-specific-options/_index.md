---
title: Tambahkan Tanda Air Teks Dengan Opsi Tertentu
linktitle: Tambahkan Tanda Air Teks Dengan Opsi Tertentu
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menambahkan tanda air teks dengan opsi tertentu ke dokumen Word Anda menggunakan Aspose.Words untuk .NET. Sesuaikan font, ukuran, warna, dan tata letak dengan mudah.
weight: 10
url: /id/net/programming-with-watermark/add-text-watermark-with-specific-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tambahkan Tanda Air Teks Dengan Opsi Tertentu

## Perkenalan

Tanda air dapat menjadi tambahan yang bergaya dan fungsional pada dokumen Word Anda, yang memiliki berbagai tujuan, mulai dari menandai dokumen sebagai rahasia hingga menambahkan sentuhan yang dipersonalisasi. Dalam tutorial ini, kita akan menjelajahi cara menambahkan tanda air teks ke dokumen Word menggunakan Aspose.Words untuk .NET. Kita akan membahas opsi spesifik yang dapat Anda konfigurasikan, seperti jenis font, ukuran font, warna, dan tata letak. Pada akhirnya, Anda akan dapat menyesuaikan tanda air dokumen Anda agar sesuai dengan kebutuhan Anda. Jadi, ambil editor kode Anda, dan mari kita mulai!

## Prasyarat

Sebelum kita mulai, pastikan Anda telah menyiapkan hal-hal berikut:

1.  Pustaka Aspose.Words untuk .NET: Anda perlu memasang pustaka Aspose.Words. Jika Anda belum melakukannya, Anda dapat mengunduhnya dari[Tautan Unduhan Aspose.Words](https://releases.aspose.com/words/net/).
2. Pemahaman Dasar tentang C#: Tutorial ini akan menggunakan C# sebagai bahasa pemrograman. Pemahaman dasar tentang sintaksis C# akan sangat membantu.
3. Lingkungan Pengembangan .NET: Pastikan Anda telah menyiapkan lingkungan pengembangan (seperti Visual Studio) tempat Anda dapat membuat dan menjalankan aplikasi .NET Anda.

## Mengimpor Ruang Nama

Untuk bekerja dengan Aspose.Words, Anda perlu menyertakan namespace yang diperlukan dalam proyek Anda. Berikut ini yang perlu Anda impor:

```csharp
using Aspose.Words;
using Aspose.Words.Rendering;
using System.Drawing;
```

## Langkah 1: Siapkan Dokumen Anda

 Pertama, Anda perlu memuat dokumen yang ingin Anda kerjakan. Untuk tutorial ini, kami akan menggunakan contoh dokumen bernama`Document.docx`Pastikan dokumen ini ada di direktori yang Anda tentukan.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

 Pada langkah ini, Anda menentukan direktori tempat dokumen Anda berada dan memuatnya ke dalam contoh`Document` kelas.

## Langkah 2: Konfigurasikan Opsi Tanda Air

Selanjutnya, konfigurasikan opsi untuk tanda air teks Anda. Anda dapat menyesuaikan berbagai aspek, seperti jenis font, ukuran font, warna, dan tata letak. Mari kita atur opsi-opsi ini.

```csharp
TextWatermarkOptions options = new TextWatermarkOptions()
{
    FontFamily = "Arial",
    FontSize = 36,
    Color = Color.Black,
    Layout = WatermarkLayout.Horizontal,
    IsSemitrasparent = false
};
```

Berikut ini fungsi masing-masing opsi:
- `FontFamily`: Menentukan jenis huruf teks tanda air.
- `FontSize`: Mengatur ukuran teks tanda air.
- `Color`: Menentukan warna teks tanda air.
- `Layout`Menentukan orientasi tanda air (horizontal atau diagonal).
- `IsSemitrasparent`: Mengatur apakah tanda air semi-transparan.

## Langkah 3: Tambahkan Teks Tanda Air

Sekarang, terapkan tanda air pada dokumen Anda menggunakan opsi yang telah dikonfigurasi sebelumnya. Pada langkah ini, Anda akan mengatur teks tanda air menjadi "Uji" dan menerapkan opsi yang Anda tentukan.

```csharp
doc.Watermark.SetText("Test", options);
```

Baris kode ini menambahkan tanda air dengan teks "Uji" ke dokumen, menerapkan opsi yang ditentukan.

## Langkah 4: Simpan Dokumen

Terakhir, simpan dokumen dengan tanda air baru yang telah diterapkan. Anda dapat menyimpannya dengan nama baru untuk menghindari penimpaan dokumen asli.

```csharp
doc.Save(dataDir + "WorkWithWatermark.AddTextWatermarkWithSpecificOptions.docx");
```

Potongan kode ini menyimpan dokumen yang dimodifikasi dalam direktori yang sama dengan nama file baru.

## Kesimpulan

Menambahkan tanda air teks ke dokumen Word Anda menggunakan Aspose.Words for .NET merupakan proses yang mudah jika dipecah menjadi beberapa langkah yang mudah dikelola. Dengan mengikuti tutorial ini, Anda telah mempelajari cara mengonfigurasi berbagai opsi tanda air, termasuk font, ukuran, warna, tata letak, dan transparansi. Dengan keterampilan ini, kini Anda dapat menyesuaikan dokumen Anda agar lebih memenuhi kebutuhan Anda atau menyertakan informasi penting seperti kerahasiaan atau pencitraan merek.

 Jika Anda memiliki pertanyaan atau memerlukan bantuan lebih lanjut, jangan ragu untuk memeriksa[Dokumentasi Aspose.Words](https://reference.aspose.com/words/net/) atau kunjungi[Forum Dukungan Aspose](https://forum.aspose.com/c/words/8) untuk bantuan lebih lanjut.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menggunakan font yang berbeda untuk tanda air?

 Ya, Anda dapat memilih font apa pun yang terinstal di sistem Anda dengan menentukan`FontFamily` properti di`TextWatermarkOptions`.

### Bagaimana cara mengubah warna tanda air?

 Anda dapat mengubah warna tanda air dengan mengatur`Color` properti di`TextWatermarkOptions` untuk apa pun`System.Drawing.Color` nilai.

### Apakah mungkin untuk menambahkan beberapa tanda air ke sebuah dokumen?

Aspose.Words mendukung penambahan satu tanda air dalam satu waktu. Untuk menambahkan beberapa tanda air, Anda perlu membuat dan menerapkannya secara berurutan.

### Bisakah saya menyesuaikan posisi tanda air?

 Itu`WatermarkLayout`properti menentukan orientasi, tetapi penyesuaian posisi yang tepat tidak didukung secara langsung. Anda mungkin perlu menggunakan teknik lain untuk penempatan yang tepat.

### Bagaimana jika saya membutuhkan tanda air semi-transparan?

 Mengatur`IsSemitrasparent`properti untuk`true` untuk membuat tanda air Anda semi-transparan.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
