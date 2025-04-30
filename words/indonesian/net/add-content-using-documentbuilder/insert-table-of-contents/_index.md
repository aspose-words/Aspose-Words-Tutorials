---
"description": "Pelajari cara memasukkan Daftar Isi di Word menggunakan Aspose.Words untuk .NET. Ikuti panduan langkah demi langkah kami untuk navigasi dokumen yang lancar."
"linktitle": "Masukkan Daftar Isi Dalam Dokumen Word"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Masukkan Daftar Isi Dalam Dokumen Word"
"url": "/id/net/add-content-using-documentbuilder/insert-table-of-contents/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Masukkan Daftar Isi Dalam Dokumen Word

## Perkenalan
Dalam tutorial ini, Anda akan mempelajari cara menambahkan Daftar Isi (TOC) secara efisien ke dokumen Word Anda menggunakan Aspose.Words for .NET. Fitur ini penting untuk mengatur dan menavigasi dokumen yang panjang, meningkatkan keterbacaan, dan memberikan ikhtisar singkat bagian-bagian dokumen.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki hal berikut:

- Pemahaman dasar tentang C# dan kerangka kerja .NET.
- Visual Studio terinstal di komputer Anda.
- Aspose.Words untuk pustaka .NET. Jika Anda belum menginstalnya, Anda dapat mengunduhnya dari [Di Sini](https://releases.aspose.com/words/net/).

## Mengimpor Ruang Nama

Untuk memulai, impor namespace yang diperlukan dalam proyek C# Anda:

```csharp
using Aspose.Words;
using Aspose.Words.Builder;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

Mari kita uraikan prosesnya menjadi beberapa langkah yang jelas:

## Langkah 1: Inisialisasi Dokumen Aspose.Words dan DocumentBuilder

Pertama, inisialisasi Aspose.Words baru `Document` objek dan sebuah `DocumentBuilder` untuk bekerja dengan:

```csharp
// Inisialisasi Dokumen dan DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Langkah 2: Masukkan Daftar Isi

Sekarang, masukkan Daftar Isi menggunakan `InsertTableOfContents` metode:

```csharp
// Masukkan Daftar Isi
builder.InsertTableOfContents("\\o \"1-3\" \\h \\z \\u");
```

## Langkah 3: Mulai Konten Dokumen di Halaman Baru

Untuk memastikan format yang tepat, mulai konten dokumen sebenarnya di halaman baru:

```csharp
// Masukkan jeda halaman
builder.InsertBreak(BreakType.PageBreak);
```

## Langkah 4: Susun Dokumen Anda dengan Judul

Atur konten dokumen Anda menggunakan gaya judul yang sesuai:

```csharp
// Mengatur gaya judul
builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading1;
builder.Writeln("Heading 1");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 1.1");
builder.Writeln("Heading 1.2");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading1;
builder.Writeln("Heading 2");
builder.Writeln("Heading 3");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 3.1");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading3;
builder.Writeln("Heading 3.1.1");
builder.Writeln("Heading 3.1.2");
builder.Writeln("Heading 3.1.3");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 3.2");
builder.Writeln("Heading 3.3");
```

## Langkah 5: Perbarui dan Isi Daftar Isi

Perbarui Daftar Isi untuk mencerminkan struktur dokumen:

```csharp
// Perbarui bidang Daftar Isi
doc.UpdateFields();
```

## Langkah 6: Simpan Dokumen

Terakhir, simpan dokumen Anda ke direktori yang ditentukan:

```csharp
// Simpan dokumen
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
doc.Save(dataDir + "InsertTableOfContentsUsingAsposeWords.docx");
```

## Kesimpulan

Menambahkan Daftar Isi menggunakan Aspose.Words untuk .NET mudah dan meningkatkan kegunaan dokumen Anda secara signifikan. Dengan mengikuti langkah-langkah ini, Anda dapat mengatur dan menavigasi dokumen yang kompleks secara efisien.

## Pertanyaan yang Sering Diajukan

### Bisakah saya menyesuaikan tampilan Daftar Isi?
Ya, Anda dapat menyesuaikan tampilan dan perilaku Daftar Isi menggunakan Aspose.Words untuk .NET API.

### Apakah Aspose.Words mendukung pembaruan bidang secara otomatis?
Ya, Aspose.Words memungkinkan Anda memperbarui bidang seperti Daftar Isi secara dinamis berdasarkan perubahan dokumen.

### Bisakah saya membuat beberapa Daftar Isi dalam satu dokumen?
Aspose.Words mendukung pembuatan beberapa Daftar Isi dengan pengaturan berbeda dalam satu dokumen.

### Apakah Aspose.Words kompatibel dengan berbagai versi Microsoft Word?
Ya, Aspose.Words memastikan kompatibilitas dengan berbagai versi format Microsoft Word.

### Di mana saya dapat menemukan bantuan dan dukungan lebih lanjut untuk Aspose.Words?
Untuk bantuan lebih lanjut, kunjungi [Forum Aspose.Words](https://forum.aspose.com/c/words/8) atau lihat di [dokumentasi resmi](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}