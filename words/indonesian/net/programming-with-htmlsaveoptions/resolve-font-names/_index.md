---
"description": "Pelajari cara mengatasi nama font dalam dokumen Word saat mengonversi ke HTML menggunakan Aspose.Words untuk .NET. Panduan langkah demi langkah dengan penjelasan terperinci."
"linktitle": "Selesaikan Nama Font"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Selesaikan Nama Font"
"url": "/id/net/programming-with-htmlsaveoptions/resolve-font-names/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Selesaikan Nama Font

## Perkenalan

Hai, rekan pembuat kode! Jika Anda pernah mengalami masalah font saat menyimpan dokumen Word sebagai HTML, Anda tidak sendirian. Font memang sulit, tetapi jangan khawatir; saya siap membantu Anda. Hari ini, kita akan membahas cara mengubah nama font di dokumen Word Anda menggunakan Aspose.Words untuk .NET. Panduan ini akan memandu Anda melalui proses ini langkah demi langkah, memastikan font Anda terlihat tepat dalam format HTML.

## Prasyarat

Sebelum kita mulai, mari pastikan Anda memiliki semua yang Anda butuhkan:

1. Aspose.Words untuk .NET: Jika Anda belum melakukannya, Anda dapat mengunduhnya [Di Sini](https://releases.aspose.com/words/net/).
2. Lisensi yang Valid: Anda dapat membeli lisensi [Di Sini](https://purchase.aspose.com/buy) atau dapatkan lisensi sementara [Di Sini](https://purchase.aspose.com/temporary-license/).
3. Pengetahuan Dasar C# dan .NET: Tutorial ini mengasumsikan Anda memahami konsep pemrograman dasar dalam C#.
4. Visual Studio: Versi apa pun yang mendukung kerangka kerja .NET.

Sekarang setelah prasyarat kita terpenuhi, mari kita mulai aksinya!

## Mengimpor Ruang Nama

Sebelum kita mulai membuat kode, pastikan Anda telah mengimpor namespace yang diperlukan ke dalam proyek Anda. Ini penting untuk mengakses fungsi Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Langkah 1: Menyiapkan Direktori Dokumen

Pertama-tama, mari kita atur jalur ke direktori dokumen Anda. Di sinilah dokumen Word Anda berada dan tempat Anda akan menyimpan output Anda.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Penjelasan:
Di Sini, `dataDir` menyimpan jalur ke direktori dokumen Anda. Ganti `"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya pada sistem Anda.

## Langkah 2: Memuat Dokumen Word

Selanjutnya, kita perlu memuat dokumen Word yang ingin kita proses. Dokumen ini harus memiliki font yang ingin Anda ubah.

```csharp
Document doc = new Document(dataDir + "Missing font.docx");
```

Penjelasan:
Kami menciptakan sebuah `Document` objek dan memuat dokumen Word bernama "Missing font.docx" dari kami `dataDir`.

## Langkah 3: Mengonfigurasi Opsi Penyimpanan HTML

Sekarang, mari kita atur opsi untuk menyimpan dokumen sebagai HTML. Di sini, kita akan memastikan bahwa nama font telah diatur dengan benar.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    PrettyFormat = true,
    ResolveFontNames = true
};
```

Penjelasan:
Kami membuat sebuah contoh dari `HtmlSaveOptions` dengan `SaveFormat.Html`. Itu `PrettyFormat` opsi membuat output HTML lebih mudah dibaca, dan `ResolveFontNames` memastikan nama font teratasi.

## Langkah 4: Menyimpan Dokumen sebagai HTML

Terakhir, kami menyimpan dokumen sebagai berkas HTML menggunakan opsi penyimpanan yang dikonfigurasi.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ResolveFontNames.html", saveOptions);
```

Penjelasan:
Kami menyebutnya `Save` metode pada `Document` objek, yang menentukan jalur keluaran dan opsi penyimpanan yang telah kami konfigurasikan. Ini akan menghasilkan berkas HTML dengan nama font yang telah ditentukan.

## Kesimpulan

Nah, itu dia! Dengan mengikuti langkah-langkah ini, Anda telah berhasil mengatasi nama font saat mengonversi dokumen Word ke HTML menggunakan Aspose.Words untuk .NET. Ini tidak hanya memastikan bahwa font Anda ditampilkan dengan benar, tetapi juga membuat output HTML Anda terlihat bagus dan profesional. Selamat membuat kode!

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?
Aspose.Words untuk .NET adalah pustaka hebat yang memungkinkan pengembang untuk membuat, memodifikasi, dan mengonversi dokumen Word secara terprogram.

### Bagaimana cara menginstal Aspose.Words untuk .NET?
Anda dapat mengunduh Aspose.Words untuk .NET dari [Di Sini](https://releases.aspose.com/words/net/)Ikuti petunjuk instalasi yang tersedia dalam dokumentasi.

### Dapatkah saya menggunakan Aspose.Words untuk .NET tanpa lisensi?
Ya, tetapi akan ada beberapa keterbatasan. Untuk fungsionalitas penuh, Anda dapat membeli lisensi [Di Sini](https://purchase.aspose.com/buy) atau dapatkan lisensi sementara [Di Sini](https://purchase.aspose.com/temporary-license/).

### Mengapa font saya tidak ditampilkan dengan benar dalam HTML?
Hal ini dapat terjadi jika font tidak diselesaikan dengan benar selama konversi. Menggunakan `ResolveFontNames = true` di dalam `HtmlSaveOptions` dapat membantu memperbaiki masalah ini.

### Di mana saya bisa mendapatkan dukungan untuk Aspose.Words untuk .NET?
Anda bisa mendapatkan dukungan dari [Forum dukungan Aspose.Words](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}