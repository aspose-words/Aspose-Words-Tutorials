---
title: Atur Font Folder Sistem Dan Folder Kustom
linktitle: Atur Font Folder Sistem Dan Folder Kustom
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara mengatur folder sistem dan font kustom dalam dokumen Word menggunakan Aspose.Words untuk .NET, memastikan dokumen Anda ditampilkan dengan benar di berbagai lingkungan.
weight: 10
url: /id/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Atur Font Folder Sistem Dan Folder Kustom

## Perkenalan

Bayangkan Anda sedang membuat dokumen dengan gaya fon yang unik, tetapi ternyata fon tersebut tidak ditampilkan dengan benar di komputer lain. Bikin frustrasi, bukan? Di sinilah konfigurasi folder fon berperan. Dengan Aspose.Words untuk .NET, Anda dapat menentukan folder fon sistem dan kustom untuk memastikan dokumen Anda selalu terlihat sesuai keinginan. Mari kita bahas cara mencapainya.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki hal berikut:

-  Pustaka Aspose.Words untuk .NET: Jika Anda belum memilikinya, unduhlah[Di Sini](https://releases.aspose.com/words/net/).
- Lingkungan Pengembangan: IDE seperti Visual Studio.
- Pengetahuan Dasar C#: Keakraban dengan C# akan membantu Anda mengikuti contoh kode.

## Mengimpor Ruang Nama

Pertama, impor namespace yang diperlukan dalam proyek Anda:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Sekarang, mari kita uraikan prosesnya menjadi beberapa langkah sederhana.

## Langkah 1: Muat Dokumen

 Untuk memulai, muat dokumen Word Anda ke Aspose.Words`Document` objek. Dokumen ini akan menjadi tempat Anda ingin mengatur folder font.

```csharp
// Jalur ke direktori dokumen Anda
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## Langkah 2: Inisialisasi Pengaturan Font

 Buat contoh baru dari`FontSettings`Objek ini akan memungkinkan Anda mengelola sumber font.

```csharp
FontSettings fontSettings = new FontSettings();
```

## Langkah 3: Ambil Sumber Font Sistem

Ambil sumber font sistem default. Pada komputer Windows, ini biasanya mencakup "Windows\Fonts\" direktori.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## Langkah 4: Tambahkan Folder Font Kustom

Tambahkan folder khusus yang berisi fon tambahan Anda. Ini berguna jika Anda memiliki fon tertentu yang tidak terpasang di direktori fon sistem.

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## Langkah 5: Perbarui Sumber Font

 Ubah daftar sumber font kembali ke array dan atur ke`FontSettings` obyek.

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## Langkah 6: Terapkan Pengaturan Font ke Dokumen

 Terakhir, terapkan konfigurasi`FontSettings` ke dokumen Anda dan simpan dalam format yang Anda inginkan, seperti PDF.

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## Kesimpulan

Nah, itu dia! Dengan mengikuti langkah-langkah ini, Anda dapat memastikan bahwa dokumen Word Anda menggunakan fon yang benar, baik fon sistem maupun fon khusus yang disimpan dalam direktori tertentu. Pengaturan ini membantu menjaga integritas tampilan dokumen Anda di berbagai lingkungan.

## Pertanyaan yang Sering Diajukan

### Apa yang terjadi jika font hilang di folder sistem dan kustom?

Aspose.Words akan menggunakan font default untuk menggantikan font yang hilang, memastikan dokumen tetap dapat dibaca.

### Bisakah saya menambahkan beberapa folder font khusus?

 Ya, Anda dapat menambahkan beberapa folder font kustom dengan mengulangi proses pembuatan`FolderFontSource` objek dan menambahkannya ke daftar sumber font.

### Apakah mungkin menggunakan jalur jaringan untuk folder font khusus?

 Ya, Anda dapat menentukan jalur jaringan di`FolderFontSource` konstruktor.

### Format file apa yang didukung Aspose.Words untuk menyimpan dokumen?

Aspose.Words mendukung berbagai format, termasuk DOCX, PDF, HTML, dan banyak lagi.

### Bagaimana cara menangani pemberitahuan penggantian font?

 Anda dapat menangani pemberitahuan penggantian font dengan menggunakan`FontSettings` kelas`FontSubstitutionWarning`peristiwa.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
