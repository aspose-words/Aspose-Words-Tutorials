---
"description": "Pelajari cara memeriksa efek teks DrawingML dalam dokumen Word menggunakan Aspose.Words untuk .NET dengan panduan terperinci dan langkah demi langkah. Sempurnakan dokumen Anda dengan mudah."
"linktitle": "Periksa Efek Teks DrawingML"
"second_title": "API Pemrosesan Dokumen Aspose.Words"
"title": "Periksa Efek Teks DrawingML"
"url": "/id/net/working-with-fonts/check-drawingml-text-effect/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Periksa Efek Teks DrawingML

## Perkenalan

Selamat datang di tutorial terperinci lainnya tentang cara bekerja dengan Aspose.Words untuk .NET! Hari ini, kita akan menyelami dunia efek teks DrawingML yang menarik. Baik Anda ingin menyempurnakan dokumen Word dengan bayangan, pantulan, atau efek 3D, panduan ini akan menunjukkan cara memeriksa efek teks ini di dokumen Anda menggunakan Aspose.Words untuk .NET. Mari kita mulai!

## Prasyarat

Sebelum kita masuk ke tutorial, ada beberapa prasyarat yang perlu Anda siapkan:

- Pustaka Aspose.Words untuk .NET: Pastikan Anda telah menginstal pustaka Aspose.Words untuk .NET. Anda dapat mengunduhnya dari [Aspose merilis halaman](https://releases.aspose.com/words/net/).
- Lingkungan Pengembangan: Anda harus menyiapkan lingkungan pengembangan, seperti Visual Studio.
- Pengetahuan Dasar C#: Sedikit pengetahuan tentang pemrograman C# akan sangat membantu.

## Mengimpor Ruang Nama

Pertama, Anda perlu mengimpor namespace yang diperlukan. Namespace ini akan memberi Anda akses ke kelas dan metode yang diperlukan untuk memanipulasi dokumen Word dan memeriksa efek teks DrawingML.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Panduan Langkah demi Langkah untuk Memeriksa Efek Teks DrawingML

Sekarang, mari kita uraikan prosesnya menjadi beberapa langkah, agar lebih mudah diikuti.

## Langkah 1: Muat Dokumen

Langkah pertama adalah memuat dokumen Word yang ingin Anda periksa efek teks DrawingML. 

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "DrawingML text effects.docx");
```

Potongan kode ini memuat dokumen bernama "DrawingML text effects.docx" dari direktori yang Anda tentukan.

## Langkah 2: Akses Koleksi Run

Selanjutnya, kita perlu mengakses kumpulan run pada paragraf pertama dokumen. Run adalah bagian teks dengan format yang sama.

```csharp
RunCollection runs = doc.FirstSection.Body.FirstParagraph.Runs;
```

Baris kode ini mengambil inti dari paragraf pertama di bagian pertama dokumen.

## Langkah 3: Dapatkan Font untuk Jalankan Pertama Kali

Sekarang, kita akan mendapatkan properti font dari run pertama dalam koleksi runs. Ini memungkinkan kita untuk memeriksa berbagai efek teks DrawingML yang diterapkan pada teks.

```csharp
Font runFont = runs[0].Font;
```

## Langkah 4: Periksa Efek Teks DrawingML

Terakhir, kita dapat memeriksa berbagai efek teks DrawingML seperti Bayangan, Efek 3D, Refleksi, Garis Besar, dan Isi.

```csharp
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Shadow));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Effect3D));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Reflection));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Outline));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Fill));
```

Baris kode ini akan dicetak `true` atau `false` tergantung pada apakah setiap efek teks DrawingML tertentu diterapkan pada font yang dijalankan.

## Kesimpulan

Selamat! Anda baru saja mempelajari cara memeriksa efek teks DrawingML dalam dokumen Word menggunakan Aspose.Words untuk .NET. Fitur canggih ini memungkinkan Anda mendeteksi dan memanipulasi pemformatan teks yang canggih secara terprogram, sehingga Anda memiliki kendali yang lebih besar atas tugas pemrosesan dokumen Anda.


## Pertanyaan yang Sering Diajukan

### Apa itu efek teks DrawingML?
Efek teks DrawingML adalah opsi pemformatan teks tingkat lanjut dalam dokumen Word, termasuk bayangan, efek 3D, pantulan, garis luar, dan isian.

### Dapatkah saya menerapkan efek teks DrawingML menggunakan Aspose.Words untuk .NET?
Ya, Aspose.Words untuk .NET memungkinkan Anda memeriksa dan menerapkan efek teks DrawingML secara terprogram.

### Apakah saya memerlukan lisensi untuk menggunakan Aspose.Words untuk .NET?
Ya, Aspose.Words untuk .NET memerlukan lisensi untuk fungsionalitas penuh. Anda dapat memperoleh lisensi [lisensi sementara](https://purchase.aspose.com/temporary-license/) untuk evaluasi.

### Apakah ada uji coba gratis yang tersedia untuk Aspose.Words untuk .NET?
Ya, Anda dapat mengunduh [uji coba gratis](https://releases.aspose.com/) untuk mencoba Aspose.Words untuk .NET sebelum membeli.

### Di mana saya dapat menemukan dokumentasi lebih lanjut tentang Aspose.Words untuk .NET?
Anda dapat menemukan dokumentasi terperinci di [Halaman Dokumentasi Aspose.Words untuk .NET](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}