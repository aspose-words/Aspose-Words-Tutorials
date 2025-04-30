---
"description": "Pelajari cara mengonversi dokumen Word menjadi gambar berindeks 1Bpp menggunakan Aspose.Words untuk .NET. Ikuti panduan langkah demi langkah kami untuk konversi yang mudah."
"linktitle": "Format 1Bpp Terindeks"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Format 1Bpp Terindeks"
"url": "/id/net/programming-with-imagesaveoptions/format-1bpp-indexed/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Format 1Bpp Terindeks

## Perkenalan

Pernahkah Anda bertanya-tanya bagaimana cara menyimpan dokumen Word sebagai gambar hitam putih hanya dengan beberapa baris kode? Nah, Anda beruntung! Hari ini, kita akan membahas trik kecil yang menarik menggunakan Aspose.Words untuk .NET yang memungkinkan Anda mengonversi dokumen Anda menjadi gambar berindeks 1Bpp. Format ini sangat cocok untuk jenis pengarsipan digital, pencetakan, atau saat Anda perlu menghemat ruang. Kami akan menguraikan setiap langkah agar semudah mungkin. Siap untuk memulai? Mari kita mulai!

## Prasyarat

Sebelum kita mulai, ada beberapa hal yang perlu Anda persiapkan:

- Aspose.Words untuk .NET: Pastikan Anda telah menginstal pustaka tersebut. Anda dapat [unduh disini](https://releases.aspose.com/words/net/).
- Lingkungan Pengembangan .NET: Visual Studio adalah pilihan yang bagus, tetapi Anda dapat menggunakan lingkungan apa pun yang Anda sukai.
- Pengetahuan Dasar C#: Jangan khawatir, kami akan menjelaskannya dengan sederhana, tetapi sedikit pengetahuan tentang C# akan membantu.
- Dokumen Word: Siapkan contoh dokumen Word yang akan dikonversi.

## Mengimpor Ruang Nama

Pertama-tama, kita perlu mengimpor namespace yang diperlukan. Ini penting karena memungkinkan kita mengakses kelas dan metode yang kita butuhkan dari Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Langkah 1: Siapkan Direktori Dokumen Anda

Anda perlu menentukan jalur ke direktori dokumen Anda. Di sinilah dokumen Word Anda disimpan dan gambar yang dikonversi akan disimpan.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Langkah 2: Muat Dokumen Word

Sekarang, mari kita memuat dokumen Word ke dalam Aspose.Words `Document` objek. Objek ini mewakili berkas Word Anda dan memungkinkan Anda untuk memanipulasinya.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Langkah 3: Konfigurasikan Opsi Penyimpanan Gambar

Selanjutnya, kita perlu mengatur `ImageSaveOptions`Di sinilah keajaiban terjadi. Kami akan mengonfigurasinya untuk menyimpan gambar dalam format PNG dengan mode warna indeks 1Bpp.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1),
    ImageColorMode = ImageColorMode.BlackAndWhite,
    PixelFormat = ImagePixelFormat.Format1bppIndexed
};
```

- SaveFormat.Png: Ini menentukan bahwa kita ingin menyimpan dokumen sebagai gambar PNG.
- PageSet(1): Ini menunjukkan kita hanya mengonversi halaman pertama.
- ImageColorMode.BlackAndWhite: Ini mengatur gambar menjadi hitam dan putih.
- ImagePixelFormat.Format1bppIndexed: Ini menetapkan format gambar ke indeks 1Bpp.

## Langkah 4: Simpan Dokumen sebagai Gambar

Terakhir, kita simpan dokumen sebagai gambar menggunakan `Save` metode dari `Document` obyek.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
```

## Kesimpulan

Nah, itu dia! Hanya dengan beberapa baris kode, Anda telah mengubah dokumen Word Anda menjadi gambar berindeks 1Bpp menggunakan Aspose.Words for .NET. Metode ini sangat berguna untuk membuat gambar dengan kontras tinggi dan hemat ruang dari dokumen Anda. Sekarang, Anda dapat dengan mudah mengintegrasikannya ke dalam proyek dan alur kerja Anda. Selamat membuat kode!

## Pertanyaan yang Sering Diajukan

### Apa itu gambar terindeks 1Bpp?
Gambar berindeks 1Bpp (1 Bit Per Pixel) adalah format gambar hitam putih yang setiap pikselnya direpresentasikan oleh satu bit, baik 0 maupun 1. Format ini sangat hemat ruang.

### Bisakah saya mengonversi beberapa halaman dokumen Word sekaligus?
Ya, Anda bisa. Ubah `PageSet` properti di `ImageSaveOptions` untuk menyertakan beberapa halaman atau seluruh dokumen.

### Apakah saya memerlukan lisensi untuk menggunakan Aspose.Words untuk .NET?
Ya, Aspose.Words untuk .NET memerlukan lisensi untuk fungsionalitas penuh. Anda bisa mendapatkannya [lisensi sementara di sini](https://purchase.aspose.com/temporary-license/).

### Format gambar apa lagi yang dapat saya ubah ke dokumen Word saya?
Aspose.Words mendukung berbagai format gambar termasuk JPEG, BMP, dan TIFF. Cukup ubah `SaveFormat` di dalam `ImageSaveOptions`.

### Di mana saya dapat menemukan dokumentasi lebih lanjut tentang Aspose.Words untuk .NET?
Anda dapat menemukan dokumentasi terperinci di [Halaman dokumentasi Aspose.Words untuk .NET](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}