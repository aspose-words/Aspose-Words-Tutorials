---
category: general
date: 2026-04-05
description: Panduan substitusi font Aspose untuk mendeteksi font yang hilang saat
  memuat dokumen Word. Pelajari cara mengonfigurasi pengaturan font dan menangani
  font yang hilang secara efisien.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- configure font settings
- handle missing fonts
language: id
og_description: Panduan substitusi font Aspose untuk mendeteksi font yang hilang saat
  memuat dokumen Word. Pelajari cara mengonfigurasi pengaturan font dan menangani
  font yang hilang secara efisien.
og_title: Penggantian Font Aspose – Deteksi Font yang Hilang dalam Dokumen Word
tags:
- Aspose.Words
- C#
- Font Management
title: Penggantian Font Aspose – Deteksi Font yang Hilang dalam Dokumen Word
url: /id/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docume/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Mendeteksi Font yang Hilang dalam Dokumen Word

Pernah menemukan file Word yang tampak sempurna di satu mesin tetapi menunjukkan perubahan font yang aneh di mesin lain? Itu adalah masalah klasik **aspose font substitution**, dan biasanya berarti beberapa font tidak ada di sistem target. Dalam tutorial ini kami akan menunjukkan, langkah demi langkah, cara **mendeteksi font yang hilang** saat Anda **memuat dokumen Word**, cara **mengonfigurasi pengaturan font**, dan apa yang harus dilakukan untuk **menangani font yang hilang** dengan elegan.

Kami akan membahas contoh C# lengkap yang dapat dijalankan, menjelaskan mengapa setiap baris penting, dan bahkan menunjukkan output konsol yang seharusnya Anda dapatkan. Pada akhir tutorial Anda akan dapat mendeteksi penggantian font begitu dokumen dimuat—tanpa tebakan.

## Apa yang Akan Anda Pelajari

- Cara mengaktifkan kolektor diagnostik Aspose.Words untuk peringatan font.  
- Kode tepat yang diperlukan untuk **memuat dokumen Word** dengan **pengaturan font** khusus.  
- Cara mengiterasi objek `WarningInfo` untuk menampilkan setiap font yang diganti.  
- Tips untuk menekan peringatan yang tidak diinginkan atau menyediakan font cadangan.  
- Contoh siap‑jalankan yang dapat Anda salin‑tempel ke Visual Studio.

### Prasyarat

- .NET 6.0 atau lebih baru (API berfungsi sama pada .NET Framework).  
- Aspose.Words untuk .NET (paket NuGet `Aspose.Words`).  
- File Word yang merujuk pada font yang tidak terpasang di sistem Anda (misalnya, `MissingFont.docx`).  

Jika Anda sudah memiliki semua itu, mari kita mulai.

## Langkah 1 – Aktifkan Kolektor Diagnostik (Konfigurasi Pengaturan Font)

Pertama-tama: Aspose.Words hanya mencatat peringatan penggantian font jika Anda mengaktifkannya. Hal ini dilakukan dengan membuat objek `FontSettings` dan menetapkannya ke instance `LoadOptions`. Anggap ini seperti menyalakan “lampu debug” untuk penanganan font.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options with a fresh FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    // The FontSettings object is the hub for all font‑related configuration.
    FontSettings = new FontSettings()
};
```

**Mengapa?**  
Tanpa objek `FontSettings` kolektor peringatan tetap diam, dan Anda tidak akan pernah tahu font mana yang diganti. Dengan menginisialisasinya kosong, kami membiarkan Aspose menggunakan font sistem default *dan* melacak setiap penggantian.

> **Pro tip:** Jika Anda mengetahui folder tertentu berisi font perusahaan, arahkan `FontSettings` ke sana dengan `SetFontsFolder("path")`. Hal ini dapat mengurangi jumlah peringatan font yang hilang.

## Langkah 2 – Muat Dokumen dengan Opsi yang Dikonfigurasi (Muat Dokumen Word)

Sekarang kolektor sudah aktif, muat file `.docx` Anda menggunakan `LoadOptions` yang sama. Ini adalah saat Aspose memindai dokumen, mencari setiap referensi font, dan memutuskan apakah penggantian diperlukan.

```csharp
// Step 2: Load the Word file while applying the previously defined load options.
Document document = new Document(@"C:\Docs\MissingFont.docx", loadOptions);
```

**Mengapa ini penting?**  
Jika Anda hanya memanggil `new Document("MissingFont.docx")`, pengaturan default akan diterapkan *dan* daftar peringatan tetap kosong. Menyertakan `loadOptions` memastikan kolektor diagnostik terhubung ke alur pemuatan.

## Langkah 3 – Ambil dan Tampilkan Peringatan Penggantian Font (Deteksi Font yang Hilang)

Setelah dokumen berada di memori, Aspose menyimpan semua peringatan di `document.WarningCallback.Warnings`. Lakukan iterasi pada koleksi tersebut, filter untuk `WarningType.FontSubstitution`, dan cetak deskripsinya. Setiap deskripsi memberi tahu Anda font mana yang hilang dan font apa yang digunakan sebagai gantinya.

```csharp
// Step 3: Examine the warning list for any font substitution entries.
foreach (WarningInfo warningInfo in document.WarningCallback.Warnings)
{
    if (warningInfo.Type == WarningType.FontSubstitution)
    {
        // The Description contains a human‑readable message, e.g.,
        // "Font 'Comic Sans MS' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warningInfo.Description}");
    }
}
```

**Output konsol yang diharapkan**

```
Substituted font: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Substituted font: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

Output tersebut memberi tahu Anda secara tepat font mana yang hilang pada mesin yang menjalankan kode. Anda kini dapat memutuskan apakah akan menginstal font yang hilang, menyematkannya ke dalam dokumen, atau mempertahankan penggantian.

![Output konsol yang menampilkan peringatan penggantian font aspose](/images/aspose-font-substitution-console.png)

*Teks alt gambar:* penggantian font aspose – output konsol yang menampilkan daftar font yang diganti

## Langkah 4 – Opsional: Sesuaikan Perilaku Penggantian (Tangani Font yang Hilang)

Terkadang Anda tidak hanya ingin mengetahui *bahwa* sebuah penggantian terjadi—Anda ingin mengontrol *bagaimana* itu terjadi. Aspose.Words memungkinkan Anda mendaftarkan `IFontSubstitutionRule` khusus. Berikut contoh singkat yang memaksa setiap font yang hilang menggunakan fallback ke `Tahoma`.

```csharp
// Optional Step 4 – Define a custom substitution rule.
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        // Always return Tahoma regardless of the missing font.
        return new FontInfo("Tahoma");
    }
}

// Apply the rule to the FontSettings we created earlier.
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(new TahomaFallbackRule());
```

**Kapan Anda akan menggunakan ini?**  
Jika Anda menghasilkan PDF untuk layanan web dan Anda tahu setiap klien dapat merender `Tahoma`, memaksa fallback menjamin konsistensi visual tanpa harus mengirimkan puluhan file font.

## Contoh Lengkap yang Berfungsi (Semua Langkah Digabungkan)

Berikut seluruh program yang dapat Anda tempel ke dalam proyek konsol baru. Program ini dapat dikompilasi apa adanya, dengan asumsi Anda telah menginstal paket NuGet Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1 – Enable diagnostic collector (configure font settings)
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Optional: Force all missing fonts to Tahoma
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(
            new TahomaFallbackRule());

        // -------------------------------------------------
        // Step 2 – Load the document (load word document)
        // -------------------------------------------------
        Document doc = new Document(@"C:\Docs\MissingFont.docx", loadOptions);

        // -------------------------------------------------
        // Step 3 – List any font substitutions (detect missing fonts)
        // -------------------------------------------------
        foreach (WarningInfo warning in doc.WarningCallback.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"Substituted font: {warning.Description}");
        }
    }
}

// -------------------------------------------------
// Optional custom rule class (handle missing fonts)
// -------------------------------------------------
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        return new FontInfo("Tahoma");
    }
}
```

Jalankan program, perhatikan konsol, dan Anda akan melihat setiap peristiwa font yang hilang dicetak. Dari situ Anda dapat memutuskan apakah akan menginstal font yang hilang, menyematkannya, atau mempertahankan fallback.

## Pertanyaan yang Sering Diajukan

**Q: Apakah ini bekerja dengan konversi PDF?**  
Ya. Ketika Anda kemudian memanggil `doc.Save("output.pdf")`, font apa pun yang diganti selama pemuatan akan menjadi font yang disematkan dalam PDF. Jadi menangkap peringatan lebih awal membantu Anda menghindari perubahan font yang tidak terduga pada PDF akhir.

**Q: Bagaimana jika saya memiliki banyak dokumen untuk diproses?**  
Bungkus logika pemuatan dalam blok try‑catch dan gunakan kembali satu instance `FontSettings` untuk semua dokumen. Hal ini mengurangi beban dan menjaga kolektor peringatan tetap aktif untuk setiap file.

**Q: Bisakah saya menonaktifkan peringatan sepenuhnya?**  
Anda dapat mengatur `loadOptions.WarningCallback = null;` sebelum memuat, tetapi Anda akan kehilangan kemampuan untuk **mendeteksi font yang hilang**—yang biasanya bukan yang Anda inginkan.

## Kesimpulan

Kami telah membahas semua yang Anda perlukan untuk menguasai **aspose font substitution**: mengaktifkan kolektor diagnostik, memuat file Word dengan **pengaturan font** khusus, mengekstrak daftar font yang hilang, dan bahkan mengganti aturan penggantian default untuk **menangani font yang hilang** sesuai keinginan Anda. Dengan hanya beberapa baris C#, Anda mendapatkan visibilitas penuh terhadap masalah font yang biasanya tersembunyi di balik perubahan tata letak yang halus.

Langkah selanjutnya? Coba sematkan font asli ke dalam dokumen dengan `FontSettings.SetFontsFolder` atau jelajahi `FontSourceBase` untuk memuat font dari basis data. Anda juga dapat bereksperimen dengan koleksi `Document.BuiltInStyle` untuk melihat bagaimana perubahan font pada tingkat gaya menyebar.

Masih ada pertanyaan tentang Aspose.Words atau manajemen font? Tinggalkan komentar, jelajahi dokumentasi resmi Aspose, atau buat proyek baru dan coba kode di atas. Selamat coding, dan semoga dokumen Anda selalu ditampilkan persis seperti yang diharapkan!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}