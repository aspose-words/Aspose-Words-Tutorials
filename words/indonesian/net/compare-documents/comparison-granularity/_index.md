---
title: Perbandingan Granularitas Dalam Dokumen Word
linktitle: Perbandingan Granularitas Dalam Dokumen Word
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari fitur Bandingkan Granularitas dalam dokumen Word Aspose.Words untuk .NET yang memungkinkan dokumen dibandingkan karakter demi karakter, melaporkan perubahan yang dibuat.
weight: 10
url: /id/net/compare-documents/comparison-granularity/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Perbandingan Granularitas Dalam Dokumen Word

Berikut adalah panduan langkah demi langkah untuk menjelaskan kode sumber C# di bawah ini, yang menggunakan fitur Bandingkan Granularitas dalam dokumen Word dari Aspose.Words untuk .NET.

## Langkah 1: Pendahuluan

Fitur Compare Granularity dari Aspose.Words untuk .NET memungkinkan Anda membandingkan dokumen pada tingkat karakter. Ini berarti bahwa setiap karakter akan dibandingkan dan perubahan akan dilaporkan sesuai dengan itu.

## Langkah 2: Menyiapkan lingkungan

Sebelum memulai, Anda perlu menyiapkan lingkungan pengembangan agar dapat bekerja dengan Aspose.Words untuk .NET. Pastikan Anda telah menginstal pustaka Aspose.Words dan memiliki proyek C# yang sesuai untuk menyematkan kode.

## Langkah 3: Tambahkan Perakitan yang Diperlukan

Untuk menggunakan fitur Compare Granularity dari Aspose.Words untuk .NET, Anda perlu menambahkan assembly yang diperlukan ke proyek Anda. Pastikan Anda memiliki referensi yang tepat ke Aspose.Words dalam proyek Anda.

```csharp
using Aspose.Words;
using Aspose.Words.DocumentBuilder;
```

## Langkah 4: Membuat Dokumen

Pada langkah ini, kita akan membuat dua dokumen menggunakan kelas DocumentBuilder. Dokumen-dokumen ini akan digunakan untuk perbandingan.

```csharp
// Buat dokumen A.
DocumentBuilder builderA = new DocumentBuilder(new Document());
builderA.Writeln("This is a simple A word.");

// Buat dokumen B.
DocumentBuilder builderB = new DocumentBuilder(new Document());
builderB.Writeln("This is simple B words.");
```

## Langkah 5: Mengonfigurasi Opsi Perbandingan

Pada langkah ini, kita akan mengonfigurasi opsi perbandingan untuk menentukan granularitas perbandingan. Di sini kita akan menggunakan granularitas tingkat karakter.

```csharp
CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };
```

## Langkah 6: Perbandingan Dokumen

Sekarang mari kita bandingkan dokumen menggunakan metode Compare dari kelas Document. Perubahan akan disimpan dalam dokumen A.

```csharp
builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);
```

 Itu`Compare`metode membandingkan dokumen A dengan dokumen B dan menyimpan perubahan pada dokumen A. Anda dapat menentukan nama penulis dan tanggal perbandingan untuk referensi.

## Kesimpulan

Dalam artikel ini, kami menjelajahi fitur Compare Granularity dari Aspose.Words untuk .NET. Fitur ini memungkinkan Anda membandingkan dokumen pada tingkat karakter dan melaporkan perubahan. Anda dapat menggunakan pengetahuan ini untuk melakukan perbandingan dokumen secara terperinci dalam proyek Anda.

### Contoh kode sumber untuk Perbandingan Granularitas menggunakan Aspose.Words untuk .NET

```csharp
            
DocumentBuilder builderA = new DocumentBuilder(new Document());
DocumentBuilder builderB = new DocumentBuilder(new Document());

builderA.Writeln("This is A simple word");
builderB.Writeln("This is B simple words");

CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };

builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);            
        
```

## Kesimpulan

Dalam tutorial ini, kami menjelajahi fitur Comparison Granularity dari Aspose.Words untuk .NET. Fitur ini memungkinkan Anda menentukan tingkat detail saat membandingkan dokumen. Dengan memilih tingkat granularitas yang berbeda, Anda dapat melakukan perbandingan terperinci pada tingkat karakter, kata, atau blok, tergantung pada kebutuhan spesifik Anda. Aspose.Words untuk .NET menyediakan kemampuan perbandingan dokumen yang fleksibel dan canggih, sehingga memudahkan untuk mengidentifikasi perbedaan dalam dokumen dengan berbagai tingkat granularitas.

### Pertanyaan yang Sering Diajukan

#### T: Apa tujuan penggunaan Comparison Granularity di Aspose.Words untuk .NET?

A: Granularitas Perbandingan di Aspose.Words untuk .NET memungkinkan Anda menentukan tingkat detail saat membandingkan dokumen. Dengan fitur ini, Anda dapat membandingkan dokumen pada berbagai tingkat, seperti tingkat karakter, tingkat kata, atau bahkan tingkat blok. Setiap tingkat granularitas memberikan tingkat detail yang berbeda dalam hasil perbandingan.

#### T: Bagaimana cara menggunakan Granularitas Perbandingan di Aspose.Words untuk .NET?

A: Untuk menggunakan Granularitas Perbandingan di Aspose.Words untuk .NET, ikuti langkah-langkah berikut:
1. Siapkan lingkungan pengembangan Anda dengan pustaka Aspose.Words.
2. Tambahkan rakitan yang diperlukan ke proyek Anda dengan merujuk Aspose.Words.
3.  Buat dokumen yang ingin Anda bandingkan menggunakan`DocumentBuilder` kelas.
4.  Konfigurasikan opsi perbandingan dengan membuat`CompareOptions` objek dan pengaturan`Granularity` properti ke tingkat yang diinginkan (misalnya,`Granularity.CharLevel` untuk perbandingan tingkat karakter).
5.  Gunakan`Compare`metode pada satu dokumen, meneruskan dokumen lain dan`CompareOptions` objek sebagai parameter. Metode ini akan membandingkan dokumen berdasarkan tingkat ketelitian yang ditentukan dan menyimpan perubahan pada dokumen pertama.

#### T: Apa saja tingkat Granularitas Perbandingan yang tersedia di Aspose.Words untuk .NET?

A: Aspose.Words untuk .NET menyediakan tiga tingkat Granularitas Perbandingan:
- `Granularity.CharLevel`: Membandingkan dokumen pada tingkat karakter.
- `Granularity.WordLevel`: Membandingkan dokumen pada tingkat kata.
- `Granularity.BlockLevel`: Membandingkan dokumen pada tingkat blok.

#### T: Bagaimana saya dapat menafsirkan hasil perbandingan dengan tingkat ketelitian tingkat karakter?

A: Dengan ketelitian tingkat karakter, setiap karakter dalam dokumen yang dibandingkan dianalisis untuk mengetahui perbedaannya. Hasil perbandingan akan menunjukkan perubahan pada tingkat karakter individual, termasuk penambahan, penghapusan, dan modifikasi.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
