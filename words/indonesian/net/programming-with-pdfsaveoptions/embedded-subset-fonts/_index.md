---
"description": "Kurangi ukuran file PDF dengan hanya menyematkan subset font yang diperlukan menggunakan Aspose.Words untuk .NET. Ikuti panduan langkah demi langkah kami untuk mengoptimalkan PDF Anda secara efisien."
"linktitle": "Sematkan Subset Font dalam Dokumen PDF"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Sematkan Subset Font dalam Dokumen PDF"
"url": "/id/net/programming-with-pdfsaveoptions/embedded-subset-fonts/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sematkan Subset Font dalam Dokumen PDF

## Perkenalan

Pernahkah Anda memperhatikan bagaimana beberapa file PDF jauh lebih besar daripada yang lain, bahkan ketika file tersebut berisi konten yang serupa? Penyebabnya sering kali terletak pada font. Menyematkan font dalam PDF memastikan bahwa tampilannya sama di perangkat apa pun, tetapi juga dapat membuat ukuran file menjadi besar. Untungnya, Aspose.Words untuk .NET menawarkan fitur praktis untuk menyematkan hanya subset font yang diperlukan, sehingga PDF Anda tetap ramping dan efisien. Tutorial ini akan memandu Anda melalui proses tersebut, langkah demi langkah.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

- Aspose.Words untuk .NET: Anda dapat mengunduhnya [Di Sini](https://releases.aspose.com/words/net/).
- Lingkungan .NET: Pastikan Anda memiliki lingkungan pengembangan .NET yang berfungsi.
- Pengetahuan Dasar C#: Keakraban dengan pemrograman C# akan membantu Anda mengikutinya.

## Mengimpor Ruang Nama

Untuk menggunakan Aspose.Words untuk .NET, Anda perlu mengimpor namespace yang diperlukan dalam proyek Anda. Tambahkan namespace ini di bagian atas file C# Anda:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Langkah 1: Muat Dokumen

Pertama, kita perlu memuat dokumen Word yang ingin kita ubah ke PDF. Ini dilakukan dengan menggunakan `Document` kelas yang disediakan oleh Aspose.Words.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

Potongan kode ini memuat dokumen yang terletak di `dataDir`Pastikan untuk mengganti `"YOUR DOCUMENT DIRECTORY"` dengan jalur sebenarnya ke dokumen Anda.

## Langkah 2: Konfigurasikan Opsi Penyimpanan PDF

Selanjutnya kita konfigurasikan `PdfSaveOptions` untuk memastikan bahwa hanya subset font yang diperlukan yang disematkan. Dengan menyetel `EmbedFullFonts` ke `false`, kami memberi tahu Aspose.Words untuk hanya menanamkan glif yang digunakan dalam dokumen.

```csharp
// Hasil PDF akan berisi sebagian font yang ada di dokumen.
// Hanya huruf glif yang digunakan dalam dokumen yang disertakan dalam font PDF.
PdfSaveOptions saveOptions = new PdfSaveOptions { EmbedFullFonts = false };
```

Langkah kecil namun penting ini membantu mengurangi ukuran berkas PDF secara signifikan.

## Langkah 3: Simpan Dokumen sebagai PDF

Terakhir, kami menyimpan dokumen sebagai PDF menggunakan `Save` metode, menerapkan konfigurasi `PdfSaveOptions`.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf", saveOptions);
```

Kode ini akan menghasilkan file PDF dengan nama `WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf` di direktori yang ditentukan, dengan hanya menanamkan subset font yang diperlukan.

## Kesimpulan

Nah, itu dia! Dengan mengikuti langkah-langkah sederhana ini, Anda dapat mengurangi ukuran file PDF secara efisien dengan hanya menyematkan subset fon yang diperlukan menggunakan Aspose.Words for .NET. Ini tidak hanya menghemat ruang penyimpanan tetapi juga memastikan waktu muat yang lebih cepat dan kinerja yang lebih baik, terutama untuk dokumen dengan fon yang ekstensif.

## Pertanyaan yang Sering Diajukan

### Mengapa saya harus menyematkan hanya subset font dalam PDF?
Menanamkan hanya subset font yang diperlukan dapat mengurangi ukuran berkas PDF secara signifikan tanpa mengurangi tampilan dan keterbacaan dokumen.

### Bisakah saya kembali menyematkan font penuh jika diperlukan?
Ya, Anda bisa. Cukup atur `EmbedFullFonts` properti untuk `true` di dalam `PdfSaveOptions`.

### Apakah Aspose.Words untuk .NET mendukung fitur pengoptimalan PDF lainnya?
Tentu saja! Aspose.Words untuk .NET menawarkan berbagai opsi untuk mengoptimalkan PDF, termasuk kompresi gambar dan menghapus objek yang tidak digunakan.

### Jenis font apa yang dapat disematkan menggunakan Aspose.Words untuk .NET?
Aspose.Words untuk .NET mendukung penyematan subset untuk semua font TrueType yang digunakan dalam dokumen.

### Bagaimana saya dapat memverifikasi font mana yang tertanam dalam PDF saya?
Anda dapat membuka PDF di Adobe Acrobat Reader dan memeriksa properti di bawah tab Font untuk melihat font yang tertanam.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}