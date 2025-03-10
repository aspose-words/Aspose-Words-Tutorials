---
title: Dicoret
linktitle: Dicoret
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menerapkan format coretan pada teks menggunakan Aspose.Words untuk .NET dengan panduan langkah demi langkah kami. Tingkatkan keterampilan pemrosesan dokumen Anda.
weight: 10
url: /id/net/working-with-markdown/strikethrough/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dicoret

## Perkenalan

Selamat datang di panduan terperinci ini tentang cara menerapkan format coretan pada teks menggunakan Aspose.Words untuk .NET. Jika Anda ingin meningkatkan keterampilan pemrosesan dokumen dan menambahkan sentuhan unik pada teks Anda, Anda berada di tempat yang tepat. Mari kita mulai!

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

-  Aspose.Words untuk .NET: Unduh[Di Sini](https://releases.aspose.com/words/net/).
- .NET Framework: Pastikan Anda telah menginstal .NET Framework di sistem Anda.
- Lingkungan Pengembangan: IDE seperti Visual Studio.
- Pengetahuan Dasar C#: Diperlukan keakraban dengan pemrograman C#.

## Mengimpor Ruang Nama

Untuk memulai, Anda perlu mengimpor namespace yang diperlukan. Namespace ini penting untuk mengakses pustaka Aspose.Words dan fitur-fiturnya.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Langkah 1: Inisialisasi DocumentBuilder

 Itu`DocumentBuilder` kelas adalah alat yang hebat di Aspose.Words yang memungkinkan Anda menambahkan konten ke dokumen Anda dengan mudah.

```csharp
// Inisialisasi DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder();
```

## Langkah 2: Tetapkan Properti Coretan

Sekarang, mari terapkan properti strikethrough ke teks kita. Ini melibatkan pengaturan`StrikeThrough` milik`Font` keberatan terhadap`true`.

```csharp
// Buat teks dicoret.
builder.Font.StrikeThrough = true;
```

## Langkah 3: Tulis Teks dengan Coretan

 Dengan properti strikethrough yang ditetapkan, kita sekarang dapat menambahkan teks kita.`Writeln` metode akan menambahkan teks ke dokumen.

```csharp
// Tulis teks dengan Strikethrough.
builder.Writeln("This text will be StrikeThrough");
```

## Kesimpulan

Nah, itu dia! Anda telah berhasil menambahkan format coretan ke teks Anda menggunakan Aspose.Words untuk .NET. Pustaka canggih ini membuka banyak kemungkinan untuk pemrosesan dan penyesuaian dokumen. Baik Anda membuat laporan, surat, atau jenis dokumen lainnya, menguasai fitur-fitur ini niscaya akan meningkatkan produktivitas dan kualitas hasil kerja Anda.

## Pertanyaan yang Sering Diajukan

### Apa itu Aspose.Words untuk .NET?
Aspose.Words untuk .NET adalah pustaka pemrosesan dokumen canggih yang memungkinkan pengembang untuk membuat, memanipulasi, dan mengonversi dokumen Word secara terprogram.

### Dapatkah saya menggunakan Aspose.Words untuk .NET dalam proyek komersial?
 Ya, Anda dapat menggunakan Aspose.Words untuk .NET dalam proyek komersial. Untuk pilihan pembelian, kunjungi[halaman pembelian](https://purchase.aspose.com/buy).

### Apakah ada uji coba gratis yang tersedia untuk Aspose.Words untuk .NET?
 Ya, Anda dapat mengunduh uji coba gratis[Di Sini](https://releases.aspose.com/).

### Bagaimana cara mendapatkan dukungan untuk Aspose.Words untuk .NET?
Anda bisa mendapatkan dukungan dari komunitas Aspose dan para ahli di[forum dukungan](https://forum.aspose.com/c/words/8).

### Dapatkah saya menerapkan opsi pemformatan teks lain menggunakan Aspose.Words untuk .NET?
Tentu saja! Aspose.Words untuk .NET mendukung berbagai pilihan format teks termasuk cetak tebal, miring, garis bawah, dan banyak lagi.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
