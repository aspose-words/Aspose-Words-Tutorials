---
title: Dapatkan Spasi Baris Font
linktitle: Dapatkan Spasi Baris Font
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara mendapatkan spasi baris font menggunakan Aspose.Words untuk .NET dengan tutorial langkah demi langkah ini. Sempurna untuk pengembang.
weight: 10
url: /id/net/working-with-fonts/get-font-line-spacing/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dapatkan Spasi Baris Font

## Perkenalan

Aspose.Words untuk .NET adalah pustaka canggih yang memungkinkan Anda membuat, memanipulasi, dan mengonversi dokumen Word secara terprogram. Salah satu tugas umum yang mungkin perlu Anda lakukan adalah mengambil spasi baris dari fon tertentu dalam dokumen. Dalam tutorial ini, kami akan memandu Anda melalui proses ini langkah demi langkah, memastikan bahwa Anda dapat dengan mudah mendapatkan spasi baris fon menggunakan Aspose.Words untuk .NET. 

## Prasyarat

Sebelum kita masuk ke kode, pastikan Anda memiliki prasyarat berikut:

1.  Aspose.Words untuk Pustaka .NET: Unduh dan instal versi terbaru dari[Di Sini](https://releases.aspose.com/words/net/).
2. Lingkungan Pengembangan: Pastikan Anda telah menyiapkan IDE seperti Visual Studio.
3. Pengetahuan Dasar C#: Tutorial ini mengasumsikan Anda memiliki pemahaman dasar tentang pemrograman C#.

## Mengimpor Ruang Nama

Pertama, Anda perlu mengimpor namespace yang diperlukan dalam proyek C# Anda. Namespace ini akan memungkinkan Anda mengakses fungsionalitas Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Mari kita uraikan proses mengatur spasi baris font menjadi beberapa langkah yang sederhana dan mudah dikelola.

## Langkah 1: Buat Dokumen Baru

Langkah pertama adalah membuat contoh dokumen Word baru menggunakan Aspose.Words untuk .NET.

```csharp
Document doc = new Document();
```

## Langkah 2: Inisialisasi DocumentBuilder

Selanjutnya, kita perlu menginisialisasi`DocumentBuilder` objek. Objek ini akan membantu kita membuat dan memanipulasi konten dokumen.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Langkah 3: Mengatur Properti Font

Sekarang, kita atur properti font untuk teks yang ingin kita masukkan. Untuk contoh ini, kita akan menggunakan font "Calibri".

```csharp
builder.Font.Name = "Calibri";
```

## Langkah 4: Tulis Teks ke Dokumen

 Menggunakan`DocumentBuilder` objek, tulis beberapa teks ke dalam dokumen. Teks ini akan menggunakan properti font yang telah kita atur pada langkah sebelumnya.

```csharp
builder.Writeln("Sample Text");
```

## Langkah 5: Ambil Objek Font

Untuk mendapatkan spasi baris, kita perlu mengakses objek font dari teks yang baru saja kita tambahkan. Ini dapat dilakukan dengan menavigasi melalui struktur dokumen hingga paragraf pertama.

```csharp
Font font = builder.Document.FirstSection.Body.FirstParagraph.Runs[0].Font;
```

## Langkah 6: Dapatkan Spasi Baris

Terakhir, kita mengambil spasi baris dari objek font dan mencetaknya ke konsol.

```csharp
Console.WriteLine($"lineSpacing = {font.LineSpacing}");
```

## Kesimpulan

Nah, itu dia! Mengambil spasi baris font menggunakan Aspose.Words untuk .NET mudah dilakukan jika Anda membaginya ke dalam beberapa langkah sederhana berikut. Baik Anda membuat dokumen baru atau mengerjakan dokumen yang sudah ada, Aspose.Words menyediakan semua alat yang Anda perlukan untuk mengelola properti font secara efisien.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?
Aspose.Words untuk .NET adalah pustaka hebat yang memungkinkan pengembang untuk membuat, memanipulasi, dan mengonversi dokumen Word secara terprogram menggunakan C#.

### Dapatkah saya menggunakan Aspose.Words untuk .NET dalam bahasa .NET lainnya?
Ya, Anda dapat menggunakan Aspose.Words untuk .NET dengan bahasa .NET apa pun, termasuk VB.NET dan F#.

### Bagaimana cara mengunduh Aspose.Words untuk .NET?
 Anda dapat mengunduh versi terbaru Aspose.Words untuk .NET dari[Di Sini](https://releases.aspose.com/words/net/).

### Apakah ada uji coba gratis yang tersedia untuk Aspose.Words untuk .NET?
 Ya, Anda bisa mendapatkan uji coba gratis dari[Di Sini](https://releases.aspose.com/).

### Di mana saya dapat menemukan dokumentasi untuk Aspose.Words untuk .NET?
 Dokumentasi untuk Aspose.Words untuk .NET tersedia[Di Sini](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
