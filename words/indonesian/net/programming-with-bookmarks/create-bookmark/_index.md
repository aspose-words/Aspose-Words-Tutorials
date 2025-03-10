---
title: Membuat Bookmark di Dokumen Word
linktitle: Membuat Bookmark di Dokumen Word
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara membuat bookmark dalam dokumen Word menggunakan Aspose.Words for .NET dengan panduan terperinci dan langkah demi langkah ini. Sempurna untuk navigasi dan pengaturan dokumen.
weight: 10
url: /id/net/programming-with-bookmarks/create-bookmark/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat Bookmark di Dokumen Word

## Perkenalan

Membuat bookmark dalam dokumen Word dapat mengubah segalanya, terutama saat Anda ingin menavigasi dokumen besar dengan mudah. Hari ini, kita akan membahas proses pembuatan bookmark menggunakan Aspose.Words untuk .NET. Tutorial ini akan memandu Anda langkah demi langkah, memastikan Anda memahami setiap bagian dari proses tersebut. Jadi, mari kita langsung mulai!

## Prasyarat

Sebelum kita mulai, Anda perlu memiliki hal berikut ini:

1.  Aspose.Words untuk Pustaka .NET: Unduh dan instal dari[Di Sini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Visual Studio atau lingkungan pengembangan .NET lainnya.
3. Pengetahuan Dasar C#: Memahami konsep dasar pemrograman C#.

## Mengimpor Ruang Nama

Untuk bekerja dengan Aspose.Words untuk .NET, Anda perlu mengimpor namespace yang diperlukan:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Langkah 1: Siapkan Dokumen dan DocumentBuilder

Inisialisasi Dokumen

Pertama, kita perlu membuat dokumen baru dan menginisialisasi`DocumentBuilder`Ini adalah titik awal untuk menambahkan konten dan penanda ke dokumen Anda.

```csharp
// Jalur ke direktori dokumen.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Penjelasan:`Document` objek adalah kanvas Anda.`DocumentBuilder` seperti pena, yang memungkinkan Anda menulis konten dan membuat penanda dalam dokumen.

## Langkah 2: Buat Bookmark Utama

Mulai dan Akhiri Bookmark Utama

Untuk membuat bookmark, Anda perlu menentukan titik awal dan titik akhir. Di sini, kita akan membuat bookmark bernama "My Bookmark".

```csharp
builder.StartBookmark("My Bookmark");
builder.Writeln("Text inside a bookmark.");
```

 Penjelasan:`StartBookmark` metode menandai awal penanda, dan`Writeln` menambahkan teks di dalam penanda buku.

## Langkah 3: Buat Bookmark Bersarang

Tambahkan Bookmark Bersarang di Dalam Bookmark Utama

Anda dapat menumpuk bookmark di dalam bookmark lainnya. Di sini, kami menambahkan "Nested Bookmark" di dalam "My Bookmark".

```csharp
builder.StartBookmark("Nested Bookmark");
builder.Writeln("Text inside a NestedBookmark.");
builder.EndBookmark("Nested Bookmark");
```

 Penjelasan: Bookmark bersarang memungkinkan organisasi konten yang lebih terstruktur dan hierarkis.`EndBookmark` metode menutup penanda saat ini.

## Langkah 4: Tambahkan Teks di Luar Bookmark Bersarang

Terus Menambahkan Konten

Setelah penanda bersarang, kita dapat meneruskan menambahkan lebih banyak konten dalam penanda utama.

```csharp
builder.Writeln("Text after Nested Bookmark.");
builder.EndBookmark("My Bookmark");
```

Penjelasan: Ini memastikan bahwa penanda utama mencakup penanda bertingkat dan teks tambahan.

## Langkah 5: Konfigurasikan Opsi Penyimpanan PDF

Siapkan Opsi Penyimpanan PDF untuk Bookmark

Saat menyimpan dokumen sebagai PDF, kita dapat mengonfigurasi opsi untuk menyertakan penanda buku.

```csharp
PdfSaveOptions options = new PdfSaveOptions();
options.OutlineOptions.BookmarksOutlineLevels.Add("My Bookmark", 1);
options.OutlineOptions.BookmarksOutlineLevels.Add("Nested Bookmark", 2);
```

 Penjelasan:`PdfSaveOptions` kelas memungkinkan Anda menentukan bagaimana dokumen harus disimpan sebagai PDF.`BookmarksOutlineLevels` properti mendefinisikan hierarki penanda dalam PDF.

## Langkah 6: Simpan Dokumen

Simpan Dokumen sebagai PDF

Terakhir, simpan dokumen dengan opsi yang ditentukan.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.CreateBookmark.pdf", options);
```

 Penjelasan:`Save` metode menyimpan dokumen dalam format dan lokasi yang ditentukan. PDF sekarang akan menyertakan bookmark yang kita buat.

## Kesimpulan

Membuat bookmark dalam dokumen Word menggunakan Aspose.Words for .NET mudah dan sangat berguna untuk navigasi dan pengaturan dokumen. Baik Anda membuat laporan, membuat eBook, atau mengelola dokumen besar, bookmark memudahkan hidup Anda. Ikuti langkah-langkah yang diuraikan dalam tutorial ini, dan Anda akan memiliki PDF yang diberi bookmark dalam waktu singkat.

## Pertanyaan yang Sering Diajukan

### Bisakah saya membuat beberapa penanda pada level yang berbeda?

Tentu saja! Anda dapat membuat bookmark sebanyak yang diperlukan dan menentukan tingkat hierarkinya saat menyimpan dokumen sebagai PDF.

### Bagaimana cara memperbarui teks penanda buku?

 Anda dapat menavigasi ke penanda menggunakan`DocumentBuilder.MoveToBookmark` dan kemudian memperbarui teksnya.

### Apakah mungkin untuk menghapus penanda buku?

 Ya, Anda dapat menghapus penanda menggunakan`Bookmarks.Remove` metode dengan menentukan nama penanda.

### Bisakah saya membuat penanda buku dalam format lain selain PDF?

Ya, Aspose.Words mendukung bookmark dalam berbagai format, termasuk DOCX, HTML, dan EPUB.

### Bagaimana saya dapat memastikan penanda buku muncul dengan benar dalam PDF?

 Pastikan untuk menentukan`BookmarksOutlineLevels` dengan benar di`PdfSaveOptions`Ini memastikan penanda buku disertakan dalam kerangka PDF.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
