---
title: Tambahkan Awalan Nama Kelas CSS
linktitle: Tambahkan Awalan Nama Kelas CSS
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara menambahkan awalan nama kelas CSS saat menyimpan dokumen Word sebagai HTML menggunakan Aspose.Words untuk .NET. Panduan langkah demi langkah, cuplikan kode, dan Tanya Jawab Umum disertakan.
weight: 10
url: /id/net/programming-with-htmlsaveoptions/add-css-class-name-prefix/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tambahkan Awalan Nama Kelas CSS

## Perkenalan

Selamat datang! Jika Anda ingin mendalami dunia Aspose.Words untuk .NET, Anda akan dimanjakan. Hari ini, kita akan membahas cara menambahkan awalan nama kelas CSS saat menyimpan dokumen Word sebagai HTML menggunakan Aspose.Words untuk .NET. Fitur ini sangat berguna saat Anda ingin menghindari konflik nama kelas dalam file HTML Anda.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

-  Aspose.Words untuk .NET: Jika Anda belum menginstalnya,[unduh disini](https://releases.aspose.com/words/net/).
- Lingkungan Pengembangan: Visual Studio atau IDE C# lainnya.
-  Dokumen Word: Kami akan menggunakan dokumen bernama`Rendering.docx`Letakkan di direktori proyek Anda.

## Mengimpor Ruang Nama

Pertama, pastikan Anda telah mengimpor namespace yang diperlukan ke dalam proyek C# Anda. Tambahkan namespace ini di bagian atas berkas kode Anda:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Sekarang, mari kita simak panduan langkah demi langkahnya!

## Langkah 1: Siapkan Proyek Anda

Sebelum kita dapat mulai menambahkan awalan nama kelas CSS, mari kita siapkan proyek kita.

### Langkah 1.1: Buat Proyek Baru

 Jalankan Visual Studio Anda dan buat proyek Aplikasi Konsol baru. Beri nama yang menarik seperti`AsposeCssPrefixExample`.

### Langkah 1.2: Tambahkan Aspose.Words untuk .NET

Jika Anda belum melakukannya, tambahkan Aspose.Words for .NET ke proyek Anda melalui NuGet. Cukup buka NuGet Package Manager Console dan jalankan:

```bash
Install-Package Aspose.Words
```

Bagus! Sekarang, kita siap untuk memulai coding.

## Langkah 2: Muat Dokumen Anda

Hal pertama yang perlu kita lakukan adalah memuat dokumen Word yang ingin kita ubah ke HTML.

### Langkah 2.1: Tentukan Jalur Dokumen

 Atur jalur ke direktori dokumen Anda. Untuk tutorial ini, mari kita asumsikan dokumen Anda ada di folder bernama`Documents` dalam direktori proyek Anda.

```csharp
string dataDir = @"C:\YourProject\Documents\";
```

### Langkah 2.2: Muat Dokumen

Sekarang, mari memuat dokumen menggunakan Aspose.Words:

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Langkah 3: Konfigurasikan Opsi Penyimpanan HTML

Berikutnya, kita perlu mengonfigurasi opsi penyimpanan HTML untuk menyertakan awalan nama kelas CSS.

### Langkah 3.1: Buat Opsi Penyimpanan HTML

 Membuat contoh`HtmlSaveOptions` objek dan atur jenis lembar gaya CSS ke`External`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External
};
```

### Langkah 3.2: Mengatur Awalan Nama Kelas CSS

 Sekarang, mari kita atur`CssClassNamePrefix` properti ke awalan yang Anda inginkan. Untuk contoh ini, kami akan menggunakan`"pfx_"`.

```csharp
saveOptions.CssClassNamePrefix = "pfx_";
```

## Langkah 4: Simpan Dokumen sebagai HTML

Terakhir, mari simpan dokumen sebagai berkas HTML dengan opsi yang telah kita konfigurasikan.


Tentukan jalur file HTML keluaran dan simpan dokumen.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
```

## Langkah 5: Verifikasi Output

 Setelah menjalankan proyek Anda, navigasikan ke`Documents` folder. Anda akan menemukan file HTML bernama`WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html` Buka file ini di editor teks atau browser untuk memverifikasi bahwa kelas CSS memiliki awalan`pfx_`.

## Kesimpulan

Nah, itu dia! Dengan mengikuti langkah-langkah ini, Anda telah berhasil menambahkan awalan nama kelas CSS ke output HTML Anda menggunakan Aspose.Words untuk .NET. Fitur sederhana namun canggih ini dapat membantu Anda mempertahankan gaya yang bersih dan bebas konflik dalam dokumen HTML Anda.

## Pertanyaan yang Sering Diajukan

### Dapatkah saya menggunakan awalan yang berbeda untuk setiap operasi penyimpanan?
 Ya, Anda dapat menyesuaikan awalan setiap kali Anda menyimpan dokumen dengan mengubah`CssClassNamePrefix` milik.

### Apakah metode ini mendukung CSS sebaris?
 Itu`CssClassNamePrefix`properti bekerja dengan CSS eksternal. Untuk CSS sebaris, Anda memerlukan pendekatan yang berbeda.

### Bagaimana saya bisa menyertakan opsi penyimpanan HTML lainnya?
 Anda dapat mengonfigurasi berbagai properti`HtmlSaveOptions` untuk menyesuaikan keluaran HTML Anda. Periksa[dokumentasi](https://reference.aspose.com/words/net/) untuk lebih jelasnya.

### Apakah mungkin untuk menyimpan HTML ke aliran?
 Tentu saja! Anda dapat menyimpan dokumen ke aliran dengan meneruskan objek aliran ke`Save` metode.

### Bagaimana cara mendapatkan dukungan jika saya mengalami masalah?
 Anda bisa mendapatkan dukungan dari[Forum Aspose](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
