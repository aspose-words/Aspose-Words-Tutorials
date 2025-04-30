---
"description": "Pelajari cara menambahkan kode rahasia dan string info ke dokumen Word menggunakan Aspose.Words untuk .NET. Panduan langkah demi langkah disertakan. Tingkatkan keterampilan pemformatan dokumen Anda."
"linktitle": "Kode Pagar"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Kode Pagar"
"url": "/id/net/working-with-markdown/fenced-code/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Kode Pagar

## Perkenalan

Hai, rekan pembuat kode! Hari ini, kita akan menyelami dunia Aspose.Words untuk .NET untuk menguasai seni menambahkan kode berpagar dan kode berpagar dengan string info ke dokumen Word Anda. Bayangkan dokumen Word Anda sebagai kanvas, dan Anda, sang seniman, akan melukis dengan presisi seperti pengembang berpengalaman. Dengan Aspose.Words, Anda memperoleh kekuatan untuk menyempurnakan dokumen Anda secara terprogram dengan blok kode terstruktur dan terformat, yang membuat dokumen teknis Anda bersinar dengan profesionalisme dan kejelasan.

## Prasyarat

Sebelum kita masuk ke tutorial, mari pastikan Anda memiliki semua yang Anda butuhkan:

- Pengetahuan dasar C#: Pemahaman umum tentang C# akan membantu Anda memahami konsep dengan cepat.
- Aspose.Words untuk .NET: Anda perlu menginstal Aspose.Words untuk .NET. Jika Anda belum memilikinya, unduhlah [Di Sini](https://releases.aspose.com/words/net/).
- Lingkungan Pengembangan: Visual Studio atau IDE C# lain yang Anda sukai.

## Mengimpor Ruang Nama

Pertama-tama, Anda perlu mengimpor namespace yang diperlukan. Ini seperti mengumpulkan semua peralatan sebelum memulai proyek.

```csharp
using Aspose.Words;
using Aspose.Words.Style;
```

Sekarang, mari kita uraikan prosesnya langkah demi langkah.

## Langkah 1: Menyiapkan Proyek Anda

Sebelum kita dapat membuat blok kode yang indah dan diformat dalam dokumen Word kita, kita perlu menyiapkan proyek baru di Visual Studio.

1. Buat Proyek Baru: Buka Visual Studio dan buat Aplikasi Konsol C# baru.
2. Tambahkan Aspose.Words Referensi: Instal Aspose.Words melalui NuGet Package Manager. Anda dapat melakukannya dengan mengklik kanan proyek Anda di Solution Explorer, memilih "Manage NuGet Packages," dan mencari Aspose.Words.

## Langkah 2: Inisialisasi DocumentBuilder

Sekarang proyek Anda sudah disiapkan, mari inisialisasi DocumentBuilder, yang akan menjadi alat utama untuk menambahkan konten ke dokumen Word.

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## Langkah 3: Buat Gaya untuk Kode Berpagar

Untuk menambahkan kode berpagar, pertama-tama kita perlu membuat gaya. Anggap saja ini sebagai pengaturan tema untuk blok kode kita.

```csharp
Style fencedCode = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode");
fencedCode.Font.Name = "Courier New";
fencedCode.Font.Size = 10;
fencedCode.ParagraphFormat.LeftIndent = 20;
fencedCode.ParagraphFormat.RightIndent = 20;
fencedCode.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## Langkah 4: Tambahkan Kode Tertutup ke Dokumen

Setelah gaya kita siap, sekarang kita dapat menambahkan blok kode berpagar ke dokumen.

```csharp
builder.ParagraphFormat.Style = fencedCode;
builder.Writeln("This is a fenced code block");
```

## Langkah 5: Buat Gaya untuk Kode Berpagar dengan String Info

Terkadang, Anda mungkin ingin menentukan bahasa pemrograman atau menambahkan informasi tambahan ke blok kode Anda. Mari buat gaya untuk itu.

```csharp
Style fencedCodeWithInfo = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode.C#");
fencedCodeWithInfo.Font.Name = "Courier New";
fencedCodeWithInfo.Font.Size = 10;
fencedCodeWithInfo.ParagraphFormat.LeftIndent = 20;
fencedCodeWithInfo.ParagraphFormat.RightIndent = 20;
fencedCodeWithInfo.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## Langkah 6: Tambahkan Kode Berpagar dengan String Info ke Dokumen

Sekarang, mari tambahkan blok kode berpagar dengan string info untuk menunjukkan bahwa itu adalah kode C#.

```csharp
builder.ParagraphFormat.Style = fencedCodeWithInfo;
builder.Writeln("This is a fenced code block with info string - C#");
```

## Kesimpulan

Selamat! Anda baru saja menambahkan blok kode berpagar dan kode berpagar dengan string info ke dokumen Word Anda menggunakan Aspose.Words untuk .NET. Ini baru permulaan. Dengan Aspose.Words, Anda dapat mengotomatiskan dan menyempurnakan pemrosesan dokumen Anda ke tingkat yang lebih tinggi. Teruslah menjelajah dan selamat membuat kode!

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?
Aspose.Words untuk .NET adalah pustaka hebat yang memungkinkan pengembang untuk membuat, memanipulasi, dan mengonversi dokumen Word secara terprogram.

### Bisakah saya menggunakan Aspose.Words dengan bahasa pemrograman lain?
Aspose.Words terutama mendukung bahasa .NET, tetapi ada versi yang tersedia untuk Java, Python, dan bahasa lainnya.

### Apakah Aspose.Words gratis untuk digunakan?
Aspose.Words adalah produk komersial, tetapi Anda dapat mengunduh uji coba gratis [Di Sini](https://releases.aspose.com/) untuk menjelajahi fitur-fiturnya.

### Bagaimana saya bisa mendapatkan dukungan untuk Aspose.Words?
Anda bisa mendapatkan dukungan dari komunitas dan pengembang Aspose [Di Sini](https://forum.aspose.com/c/words/8).

### Fitur apa lagi yang ditawarkan Aspose.Words?
Aspose.Words menawarkan berbagai fitur termasuk konversi dokumen, pembuatan dokumen berbasis templat, pelaporan, dan banyak lagi.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}