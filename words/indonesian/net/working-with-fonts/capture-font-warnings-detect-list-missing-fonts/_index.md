---
category: general
date: 2025-12-31
description: Tangkap peringatan font di Aspose.Words untuk mendeteksi font yang hilang
  dan daftar font yang hilang dalam aplikasi .NET Anda. Pelajari solusi C# langkah
  demi langkah.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- list missing fonts
- Aspose.Words font warnings
- C# document loading
language: id
og_description: Tangkap peringatan font di Aspose.Words untuk mendeteksi font yang
  hilang dan daftar font yang hilang. Panduan lengkap C# dengan kode dan tips.
og_title: Tangkap Peringatan Font – Deteksi & Daftar Font yang Hilang
tags:
- Aspose.Words
- C#
- .NET
- Font Substitution
title: Tangkap Peringatan Font – Deteksi & Daftar Font yang Hilang
url: /id/net/working-with-fonts/capture-font-warnings-detect-list-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menangkap Peringatan Font – Deteksi & Daftar Font yang Hilang

Pernah perlu **menangkap peringatan font** saat memuat dokumen Word tetapi tidak yakin bagaimana menampilkan detail font yang hilang? Anda tidak sendirian. Dalam banyak proyek dunia nyata, font yang hilang menyebabkan gangguan tata letak, dan tanpa peringatan yang tepat Anda akan mengejar bug yang tidak terlihat.  

Dalam tutorial ini kami akan menunjukkan cara **mendeteksi font yang hilang** dan **mendaftar font yang hilang** menggunakan Aspose.Words untuk .NET. Pada akhir tutorial Anda akan memiliki potongan kode C# yang siap dijalankan dan mencetak setiap peringatan substitusi, sehingga Anda dapat mencatat, memberi peringatan, atau bahkan mengganti font secara otomatis.

---

## Mengapa Menangkap Peringatan Font Penting

Ketika Aspose.Words membuka file DOCX yang merujuk pada font yang tidak terpasang di server, secara diam‑diam ia mengganti dengan fallback. Dokumen terlihat baik, tetapi kesetiaan visual terganggu—bayangkan logo merek perusahaan yang ditampilkan dengan jenis huruf yang salah.  

Menangkap peringatan tersebut memungkinkan Anda untuk:

* **Mempertahankan konsistensi merek** – Anda tahu persis font mana yang hilang.  
* **Mengotomatiskan perbaikan** – mengganti font yang hilang secara programatis.  
* **Audit kepatuhan** – menghasilkan laporan untuk tinjauan hukum atau desain.  

Singkatnya, **menangkap peringatan font** adalah barisan pertahanan pertama melawan substitusi font yang diam.

---

## Mengatur LoadOptions untuk Mendeteksi Font yang Hilang

Kunci untuk menampilkan peringatan adalah properti `LoadOptions.FontSubstitutionWarning`. Secara default nilainya `None`, yang berarti Aspose.Words menelan pesan tersebut. Mengubahnya menjadi `All` memberi tahu perpustakaan untuk merekam setiap peristiwa substitusi.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Configure LoadOptions so every font‑substitution warning is stored
LoadOptions loadOptions = new LoadOptions
{
    // Provide a fresh FontSettings instance – you can also pre‑load custom fonts here
    FontSettings = new FontSettings(),

    // This flag tells Aspose.Words to capture *all* font‑related warnings
    FontSubstitutionWarning = FontSubstitutionWarning.All
};
```

> **Pro tip:** Jika Anda sudah memiliki folder font khusus, tetapkan ke `FontSettings.SetFontsFolder("path")` sebelum memuat dokumen. Dengan begitu Anda dapat **mendeteksi font yang hilang** yang tidak ada di direktori sistem.

---

## Memuat Dokumen dan Mendaftar Font yang Hilang

Setelah `LoadOptions` siap, langkah selanjutnya adalah memuat file Word. Konstruktor menerima objek opsi, dan setiap substitusi akan dicatat dalam `WarningInfoCollection` dokumen.

```csharp
// Path to the DOCX that may contain unknown fonts
string docPath = @"C:\Docs\UnknownFonts.docx";

// Load the document with the warning‑capture options
Document document = new Document(docPath, loadOptions);
```

Jika file merujuk pada font yang tidak tersedia, setiap font yang hilang menghasilkan entri `WarningInfo`. Anda dapat **mendaftar font yang hilang** dengan mengiterasi koleksi tersebut.

```csharp
// Iterate through the warnings and output them to the console
foreach (WarningInfo warning in document.WarningInfoCollection)
{
    // The warning.Type will be FontSubstitution, and Description contains details
    Console.WriteLine($"{warning.Type}: {warning.Description}");
}
```

Output tipikal terlihat seperti:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Setiap baris memberi tahu Anda secara tepat font mana yang hilang, memenuhi kebutuhan **mendaftar font yang hilang**.

---

## Membaca dan Menginterpretasikan WarningInfoCollection

`WarningInfoCollection` dapat berisi berbagai jenis peringatan (misalnya, `DocumentStructure`, `ImageLoading`). Untuk fokus hanya pada masalah font, filter dengan `WarningType.FontSubstitution`.

```csharp
var fontWarnings = document.WarningInfoCollection
                           .Where(w => w.Type == WarningType.FontSubstitution);

foreach (var fw in fontWarnings)
{
    Console.WriteLine($"Missing font detected: {fw.Description}");
}
```

apa harus filter? Karena dokumen besar mungkin juga menghasilkan peringatan tentang gambar rusak atau fitur yang tidak didukung. Dengan mempersempit koleksi Anda menghindari kebisingan dan menjaga output **menangkap peringatan font** tetap bersih.

---

## Contoh Lengkap yang Berfungsi – Menangkap Peringatan Font dalam Aksi

Berikut adalah program lengkap yang dapat Anda masukkan ke proyek konsol .NET apa pun. Program ini menunjukkan setiap langkah mulai dari mengonfigurasi `LoadOptions` hingga mencetak daftar font yang hilang secara rapi.

```csharp
// ------------------------------------------------------------
// Complete C# example: Capture Font Warnings, Detect & List Missing Fonts
// ------------------------------------------------------------
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare LoadOptions to capture all font‑substitution warnings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings(),
            FontSubstitutionWarning = FontSubstitutionWarning.All
        };

        // OPTIONAL: If you have a custom font folder, point Aspose.Words to it
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyFonts", true);

        // 2️⃣ Load the document with the configured options
        string docPath = @"C:\Docs\UnknownFonts.docx";
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Filter only font‑substitution warnings
        var fontWarnings = doc.WarningInfoCollection
                               .Where(w => w.Type == WarningType.FontSubstitution);

        // 4️⃣ Output the missing‑font details
        Console.WriteLine("=== Missing Font Report ===");
        foreach (var warning in fontWarnings)
        {
            Console.WriteLine(warning.Description);
        }

        // 5️⃣ If no warnings were found, let the user know
        if (!fontWarnings.Any())
            Console.WriteLine("All referenced fonts are available – no warnings captured.");
    }
}
```

**Output konsol yang diharapkan**

```
=== Missing Font Report ===
Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Jika dokumen tidak memiliki font yang hilang, Anda akan melihat:

```
All referenced fonts are available – no warnings captured.
```

---

## Kasus Pinggir Umum & Cara Menanganinya

| Situasi | Mengapa Terjadi | Perbaikan yang Disarankan |
|-----------|----------------|-----------------|
| **Dokumen menggunakan font OpenType yang tersemat** | Aspose.Words dapat membaca font yang tersemat, tetapi hanya jika file tidak rusak. | Verifikasi DOCX di Word terlebih dahulu; sematkan kembali font jika diperlukan. |
| **Banyak peringatan** (misalnya, 200+ font yang hilang) | Impor massal dari sistem lama sering merujuk pada banyak jenis font. | Proses peringatan secara batch: simpan ke basis data, lalu jalankan skrip instalasi font. |
| **WarningInfoCollection kosong** | Bisa jadi dokumen memiliki semua font, atau `FontSubstitutionWarning` masih `None`. | Periksa kembali konfigurasi `LoadOptions` Anda dan pastikan Anda memuat jalur file yang benar. |
| **Font khusus berada di share jaringan** | Latensi jaringan dapat menyebabkan timeout saat pencarian font. | Pramuat font ke `FontSettings` menggunakan `SetFontsFolder` dan set `CacheFontData = true`. |

Tips ini membantu Anda **mendeteksi font yang hilang** secara andal, bahkan di lingkungan yang kompleks.

---

## Ilustrasi Gambar

![contoh menangkap peringatan font](https://example.com/images/capture-font-warnings.png "contoh menangkap peringatan font")

*Tangkap layar menunjukkan sebuah run konsol di mana dua font yang hilang dilaporkan.*

---

## Langkah Selanjutnya – Lebih dari Sekadar Pelaporan Sederhana

Sekarang Anda dapat **menangkap peringatan font**, pertimbangkan mengotomatiskan perbaikan:

1. **Substitusi Font Otomatis** – Ganti font yang hilang dengan fallback yang disetujui perusahaan dengan memodifikasi `FontSettings.SubstitutionSettings`.  
2. **Mencatat ke Sistem Monitoring** – Alirkan pesan peringatan ke Serilog, ELK, atau Azure Application Insights.  
3. **Laporan untuk Pengguna** – Hasilkan ringkasan HTML atau PDF bagi desainer untuk meninjau font mana yang perlu dipasang.

Semua ekstensi ini dibangun di atas fondasi yang sama yang telah kami bahas: mengonfigurasi `LoadOptions`, memuat dokumen, dan membaca `WarningInfoCollection`.

---

## Kesimpulan

Anda baru saja mempelajari cara **menangkap peringatan font** di Aspose.Words, **mendeteksi font yang hilang**, dan **mendaftar font yang hilang** dengan output konsol yang bersih. Pendekatannya sederhana, hanya memerlukan beberapa baris C#, dan bekerja dengan versi .NET apa pun yang mendukung Aspose.Words 23.x atau lebih baru.  

Cobalah pada contoh DOCX yang merujuk pada font yang sengaja Anda hapus – peringatan akan muncul seketika. Dari situ, Anda dapat memutuskan apakah akan memasang jenis huruf yang hilang, menggantinya secara programatis, atau sekadar mencatat masalah untuk ditinjau nanti.

Selamat coding, semoga dokumen Anda selalu ditampilkan dengan font yang tepat!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}