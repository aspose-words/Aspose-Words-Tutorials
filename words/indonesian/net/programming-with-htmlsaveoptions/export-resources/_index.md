---
title: Ekspor Sumber Daya
linktitle: Ekspor Sumber Daya
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara mengekspor sumber daya seperti CSS dan font sambil menyimpan dokumen Word sebagai HTML menggunakan Aspose.Words untuk .NET. Ikuti panduan langkah demi langkah kami.
weight: 10
url: /id/net/programming-with-htmlsaveoptions/export-resources/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ekspor Sumber Daya

## Perkenalan

Hai, sesama penggemar teknologi! Jika Anda pernah merasa perlu mengonversi dokumen Word ke HTML, Anda berada di tempat yang tepat. Hari ini, kita akan menyelami dunia Aspose.Words for .NET yang menakjubkan. Pustaka canggih ini memudahkan Anda bekerja dengan dokumen Word secara terprogram. Dalam tutorial ini, kita akan membahas langkah-langkah untuk mengekspor sumber daya, seperti font dan CSS, saat menyimpan dokumen Word sebagai HTML menggunakan Aspose.Words for .NET. Bersiaplah untuk pengalaman yang menyenangkan dan informatif!

## Prasyarat

Sebelum kita mulai menggunakan kode, pastikan Anda memiliki semua yang dibutuhkan untuk memulai. Berikut ini daftar periksa singkatnya:

1.  Visual Studio: Pastikan Anda telah menginstal Visual Studio di komputer Anda. Anda dapat mengunduhnya dari[Situs web Visual Studio](https://visualstudio.microsoft.com/).
2.  Aspose.Words untuk .NET: Anda memerlukan pustaka Aspose.Words untuk .NET. Jika Anda belum memilikinya, dapatkan uji coba gratis dari[Rilis Aspose](https://releases.aspose.com/words/net/) atau membelinya dari[Toko Aspose](https://purchase.aspose.com/buy).
3. Pengetahuan Dasar C#: Pemahaman mendasar tentang C# akan membantu Anda mengikuti contoh kode.

Sudah paham? Bagus! Mari kita lanjutkan dengan mengimpor namespace yang diperlukan.

## Mengimpor Ruang Nama

Untuk menggunakan Aspose.Words untuk .NET, Anda perlu menyertakan namespace yang relevan dalam proyek Anda. Berikut cara melakukannya:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Ruang nama ini penting untuk mengakses kelas dan metode Aspose.Words yang akan kita gunakan dalam tutorial kita.

Mari kita bahas proses pengeksporan sumber daya saat menyimpan dokumen Word sebagai HTML. Kita akan membahasnya langkah demi langkah, sehingga mudah diikuti.

## Langkah 1: Siapkan Direktori Dokumen Anda

Pertama-tama, Anda perlu menentukan jalur ke direktori dokumen Anda. Di sinilah dokumen Word Anda berada dan tempat file HTML akan disimpan.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Mengganti`"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya ke direktori Anda.

## Langkah 2: Muat Dokumen Word

 Selanjutnya, mari kita muat dokumen Word yang ingin Anda ubah ke HTML. Untuk tutorial ini, kita akan menggunakan dokumen bernama`Rendering.docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Baris kode ini memuat dokumen dari direktori yang ditentukan.

## Langkah 3: Konfigurasikan Opsi Penyimpanan HTML

Untuk mengekspor sumber daya seperti CSS dan font, Anda perlu mengonfigurasi`HtmlSaveOptions`Langkah ini sangat penting untuk memastikan keluaran HTML Anda terstruktur dengan baik dan mencakup sumber daya yang diperlukan.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External,
    ExportFontResources = true,
    ResourceFolder = dataDir + "Resources",
    ResourceFolderAlias = "http://contoh.com/sumber"
};
```

Mari kita uraikan apa yang dilakukan setiap opsi:
- `CssStyleSheetType = CssStyleSheetType.External`: Opsi ini menentukan bahwa gaya CSS harus disimpan dalam lembar gaya eksternal.
- `ExportFontResources = true`: Ini memungkinkan ekspor sumber daya font.
- `ResourceFolder = dataDir + "Resources"`: Menentukan folder lokal tempat sumber daya (seperti font dan berkas CSS) akan disimpan.
- `ResourceFolderAlias = "http://example.com/resources"`: Menetapkan alias untuk folder sumber daya, yang akan digunakan dalam berkas HTML.

## Langkah 4: Simpan Dokumen sebagai HTML

Setelah opsi penyimpanan dikonfigurasi, langkah terakhir adalah menyimpan dokumen sebagai file HTML. Berikut cara melakukannya:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

Baris kode ini menyimpan dokumen dalam format HTML, bersama dengan sumber daya yang diekspor.

## Kesimpulan

Nah, itu dia! Anda telah berhasil mengekspor sumber daya sambil menyimpan dokumen Word sebagai HTML menggunakan Aspose.Words untuk .NET. Dengan pustaka yang canggih ini, menangani dokumen Word secara terprogram menjadi sangat mudah. Baik Anda bekerja pada aplikasi web atau hanya perlu mengonversi dokumen untuk penggunaan offline, Aspose.Words siap membantu Anda.

## Pertanyaan yang Sering Diajukan

### Bisakah saya mengekspor gambar beserta font dan CSS?
 Ya, Anda bisa! Aspose.Words untuk .NET juga mendukung pengeksporan gambar. Pastikan untuk mengonfigurasi`HtmlSaveOptions` demikian.

### Apakah ada cara untuk menanamkan CSS tanpa menggunakan stylesheet eksternal?
 Tentu saja. Anda dapat mengaturnya`CssStyleSheetType` ke`CssStyleSheetType.Embedded` jika Anda lebih suka gaya tertanam.

### Bagaimana saya dapat menyesuaikan nama berkas HTML keluaran?
 Anda dapat menentukan nama file apa pun yang Anda suka di`doc.Save` metode. Misalnya,`doc.Save(dataDir + "CustomFileName.html", saveOptions);`.

### Apakah Aspose.Words mendukung format lain selain HTML?
 Ya, ini mendukung berbagai format termasuk PDF, DOCX, TXT, dan banyak lagi. Lihat[dokumentasi](https://reference.aspose.com/words/net/) untuk daftar lengkap.

### Di mana saya bisa mendapatkan lebih banyak dukungan dan sumber daya?
Untuk bantuan lebih lanjut, kunjungi[Forum Dukungan Aspose.Words](https://forum.aspose.com/c/words/8) Anda juga dapat menemukan dokumentasi dan contoh terperinci di[Situs web Aspose](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
