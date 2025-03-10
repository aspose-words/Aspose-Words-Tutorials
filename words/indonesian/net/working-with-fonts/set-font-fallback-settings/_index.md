---
title: Tetapkan Pengaturan Font Fallback
linktitle: Tetapkan Pengaturan Font Fallback
second_title: API Pemrosesan Dokumen Aspose.Words
description: Pelajari cara mengatur Pengaturan Font Fallback di Aspose.Words untuk .NET. Panduan komprehensif ini memastikan semua karakter dalam dokumen Anda ditampilkan dengan benar.
weight: 10
url: /id/net/working-with-fonts/set-font-fallback-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tetapkan Pengaturan Font Fallback

## Perkenalan

Saat bekerja dengan dokumen yang berisi berbagai elemen teks, seperti bahasa atau karakter khusus yang berbeda, sangat penting untuk memastikan bahwa elemen-elemen ini ditampilkan dengan benar. Aspose.Words untuk .NET menawarkan fitur canggih yang disebut Pengaturan Penggantian Font, yang membantu dalam menentukan aturan untuk mengganti font saat font asli tidak mendukung karakter tertentu. Dalam panduan ini, kita akan membahas cara menyiapkan Pengaturan Penggantian Font menggunakan Aspose.Words untuk .NET dalam tutorial langkah demi langkah.

## Prasyarat

Sebelum memulai tutorial, pastikan Anda memiliki prasyarat berikut:

- Pengetahuan Dasar C#: Keakraban dengan bahasa pemrograman C# dan kerangka kerja .NET.
-  Aspose.Words untuk .NET: Unduh dan instal dari[tautan unduhan](https://releases.aspose.com/words/net/).
- Lingkungan Pengembangan: Pengaturan seperti Visual Studio untuk menulis dan menjalankan kode Anda.
-  Contoh Dokumen: Miliki contoh dokumen (misalnya,`Rendering.docx`) siap untuk diuji.
- Aturan Penggantian Font XML: Siapkan file XML yang mendefinisikan aturan penggantian font.

## Mengimpor Ruang Nama

Untuk menggunakan Aspose.Words, Anda perlu mengimpor namespace yang diperlukan. Ini memungkinkan akses ke berbagai kelas dan metode yang diperlukan untuk pemrosesan dokumen.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;
```

## Langkah 1: Tentukan Direktori Dokumen

Pertama, tentukan direktori tempat dokumen Anda disimpan. Ini penting untuk menemukan dan memproses dokumen Anda.

```csharp
// Jalur ke direktori dokumen
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Langkah 2: Muat Dokumen

 Muat dokumen Anda ke Aspose.Words`Document` objek. Langkah ini memungkinkan Anda untuk bekerja dengan dokumen secara terprogram.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Langkah 3: Konfigurasikan Pengaturan Font

 Buat yang baru`FontSettings` objek dan memuat pengaturan fallback font dari file XML. File XML ini berisi aturan untuk fallback font.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.FallbackSettings.Load(dataDir + "Font fallback rules.xml");
```

## Langkah 4: Terapkan Pengaturan Font ke Dokumen

 Tetapkan yang dikonfigurasi`FontSettings`ke dokumen. Ini memastikan bahwa aturan fallback font diterapkan saat merender dokumen.

```csharp
doc.FontSettings = fontSettings;
```

## Langkah 5: Simpan Dokumen

Terakhir, simpan dokumen. Pengaturan font fallback akan digunakan selama operasi penyimpanan untuk memastikan penggantian font yang tepat.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontFallbackSettings.pdf");
```

## Berkas XML: Aturan Penggantian Font

Berikut adalah contoh bagaimana file XML Anda yang mendefinisikan aturan fallback font seharusnya terlihat:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<FontFallbackSettings xmlns="Aspose.Words">
    <FallbackTable>
        <Rule Ranges="0B80-0BFF" FallbackFonts="Vijaya"/>
        <Rule Ranges="1F300-1F64F" FallbackFonts="Segoe UI Emoji, Segoe UI Symbol"/>
        <Rule Ranges="2000-206F, 2070-209F, 20B9" FallbackFonts="Arial" />
        <Rule Ranges="3040-309F" FallbackFonts="MS Gothic" BaseFonts="Times New Roman"/>
        <Rule Ranges="3040-309F" FallbackFonts="MS Mincho"/>
        <Rule FallbackFonts="Arial Unicode MS"/>
    </FallbackTable>
</FontFallbackSettings>
```

## Kesimpulan

Dengan mengikuti langkah-langkah ini, Anda dapat secara efektif mengatur dan menggunakan Pengaturan Penggantian Font di Aspose.Words untuk .NET. Ini memastikan bahwa dokumen Anda menampilkan semua karakter dengan benar, meskipun font asli tidak mendukung karakter tertentu. Menerapkan pengaturan ini akan sangat meningkatkan kualitas dan keterbacaan dokumen Anda.

## Pertanyaan yang Sering Diajukan

### Q1: Apa itu Font Fallback?

Font Fallback adalah fitur yang memungkinkan penggantian font ketika font asli tidak mendukung karakter tertentu, memastikan tampilan semua elemen teks yang tepat.

### Q2: Dapatkah saya menentukan beberapa font fallback?

Ya, Anda dapat menentukan beberapa font fallback dalam aturan XML. Aspose.Words akan memeriksa setiap font dalam urutan yang ditentukan hingga menemukan satu yang mendukung karakter tersebut.

### Q3: Di mana saya dapat mengunduh Aspose.Words untuk .NET?

 Anda dapat mengunduhnya dari[Halaman unduhan Aspose](https://releases.aspose.com/words/net/).

### Q4: Bagaimana cara membuat berkas XML untuk aturan fallback font?

Berkas XML dapat dibuat menggunakan penyunting teks apa pun. Berkas ini harus mengikuti struktur yang ditunjukkan dalam contoh yang diberikan dalam tutorial ini.

### Q5: Apakah ada dukungan yang tersedia untuk Aspose.Words?

 Ya, Anda dapat menemukan dukungan di[Forum dukungan Aspose.Words](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
