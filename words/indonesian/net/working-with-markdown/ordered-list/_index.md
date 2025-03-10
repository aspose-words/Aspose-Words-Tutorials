---
title: Daftar Berurutan
linktitle: Daftar Berurutan
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara membuat daftar berurutan dalam dokumen Word menggunakan Aspose.Words untuk .NET dengan panduan langkah demi langkah kami. Sempurna untuk mengotomatiskan pembuatan dokumen.
weight: 10
url: /id/net/working-with-markdown/ordered-list/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Daftar Berurutan

## Perkenalan

Jadi, Anda telah memutuskan untuk mencoba Aspose.Words for .NET untuk membuat dokumen Word yang menakjubkan secara terprogram. Pilihan yang fantastis! Hari ini, kita akan membahas cara membuat daftar berurutan dalam dokumen Word. Kita akan membahasnya langkah demi langkah, jadi, baik Anda seorang pemula dalam bidang coding atau profesional yang berpengalaman, Anda akan merasa panduan ini sangat membantu. Mari kita mulai!

## Prasyarat

Sebelum kita masuk ke kode, ada beberapa hal yang Anda perlukan:

1. Aspose.Words untuk .NET: Pastikan Anda telah menginstal Aspose.Words untuk .NET. Jika belum, Anda dapat mengunduhnya[Di Sini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Visual Studio atau IDE lain yang kompatibel dengan .NET.
3. Pengetahuan Dasar C#: Anda harus memahami dasar-dasar C# agar mudah dipahami.

## Mengimpor Ruang Nama

Untuk menggunakan Aspose.Words dalam proyek Anda, Anda perlu mengimpor namespace yang diperlukan. Ini seperti menyiapkan kotak peralatan sebelum Anda mulai bekerja.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
```

Mari kita uraikan kode tersebut menjadi beberapa langkah kecil dan jelaskan setiap bagiannya. Siap? Kita mulai!

## Langkah 1: Inisialisasi Dokumen

Pertama-tama, Anda perlu membuat dokumen baru. Anggap saja ini seperti membuka dokumen Word kosong di komputer Anda.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Di sini, kita menginisialisasi dokumen baru dan objek DocumentBuilder. DocumentBuilder seperti pena, yang memungkinkan Anda menulis konten ke dalam dokumen.

## Langkah 2: Terapkan Format Daftar Bernomor

Sekarang, mari terapkan format daftar bernomor default. Ini seperti mengatur dokumen Word Anda untuk menggunakan poin-poin bernomor.

```csharp
builder.ListFormat.ApplyNumberDefault();
```

Baris kode ini mengatur penomoran untuk daftar Anda. Mudah, bukan?

## Langkah 3: Tambahkan Item Daftar

Selanjutnya, mari tambahkan beberapa item ke dalam daftar kita. Bayangkan Anda sedang menuliskan daftar belanjaan.

```csharp
builder.Writeln("Item 1");
builder.Writeln("Item 2");
```

Dengan baris ini, Anda menambahkan dua item pertama ke daftar Anda.

## Langkah 4: Buat Indentasi pada Daftar

Bagaimana jika Anda ingin menambahkan sub-item di bawah suatu item? Mari kita lakukan itu!

```csharp
builder.ListFormat.ListIndent();

builder.Writeln("Item 2a");
builder.Writeln("Item 2b");
```

 Itu`ListIndent` metode membuat indentasi pada daftar, sehingga membuat sub-daftar. Sekarang Anda membuat daftar hierarkis, seperti daftar tugas bertingkat.

## Kesimpulan

Membuat daftar berurutan dalam dokumen Word secara terprogram mungkin tampak menakutkan pada awalnya, tetapi dengan Aspose.Words untuk .NET, itu mudah. Dengan mengikuti langkah-langkah sederhana ini, Anda dapat dengan mudah menambahkan dan mengelola daftar dalam dokumen Anda. Baik Anda membuat laporan, membuat dokumen terstruktur, atau hanya mengotomatiskan alur kerja Anda, Aspose.Words untuk .NET siap membantu Anda. Jadi, tunggu apa lagi? Mulailah membuat kode dan lihat keajaibannya!

## Pertanyaan yang Sering Diajukan

### Bisakah saya menyesuaikan gaya penomoran daftar?  
 Ya, Anda dapat menyesuaikan gaya penomoran menggunakan`ListFormat`properti. Anda dapat mengatur berbagai gaya penomoran seperti angka Romawi, huruf, dll.

### Bagaimana cara menambahkan lebih banyak tingkat indentasi?  
 Anda dapat menggunakan`ListIndent` metode beberapa kali untuk membuat tingkat sub-daftar yang lebih dalam. Setiap panggilan ke`ListIndent` menambahkan satu tingkat indentasi.

### Bisakah saya mencampur poin-poin dan daftar bernomor?  
 Tentu saja! Anda dapat menerapkan format daftar yang berbeda dalam dokumen yang sama menggunakan`ListFormat` milik.

### Apakah mungkin untuk melanjutkan penomoran dari daftar sebelumnya?  
Ya, Anda dapat melanjutkan penomoran dengan menggunakan format daftar yang sama. Aspose.Words memungkinkan Anda untuk mengontrol penomoran daftar di berbagai paragraf.

### Bagaimana cara menghapus format daftar?  
 Anda dapat menghapus format daftar dengan memanggil`ListFormat.RemoveNumbers()`Ini akan mengubah item daftar kembali menjadi paragraf biasa.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
