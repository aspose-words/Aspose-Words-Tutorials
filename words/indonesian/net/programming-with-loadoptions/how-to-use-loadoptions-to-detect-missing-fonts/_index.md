---
category: general
date: 2026-06-08
description: Pelajari cara menggunakan LoadOptions di Aspose.Words untuk mendeteksi
  font yang hilang saat mengimpor dokumen. Panduan langkah demi langkah dengan kode,
  penjelasan, dan praktik terbaik.
draft: false
keywords:
- how to use loadoptions
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- C# document loading
language: id
og_description: Cara menggunakan LoadOptions di Aspose.Words dan mendeteksi font yang
  hilang saat memuat dokumen. Panduan lengkap dengan kode dan tips praktis.
og_title: Cara Menggunakan LoadOptions untuk Mendeteksi Font yang Hilang
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  headline: How to Use LoadOptions to Detect Missing Fonts
  type: TechArticle
- description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  name: How to Use LoadOptions to Detect Missing Fonts
  steps:
  - name: Create a Warning Handler
    text: Aspose.Words uses the `IWarningCallback` interface to notify you about non‑critical
      issues, such as font substitution. Implement the interface and decide what to
      do when a warning arrives.
  - name: Attach the Handler to LoadOptions
    text: Now we create a `LoadOptions` instance and tell it to use our `FontWarningHandler`.
      This is the point where **how to use LoadOptions** really shines.
  - name: Load the Document Using the Configured Options
    text: Finally, we feed the `LoadOptions` into the `Document` constructor. If the
      source file references a font that isn’t installed, Aspose.Words will fire the
      warning and your handler will print a message.
  - name: Multiple Documents in a Loop
    text: Often you’ll process a batch of files. The same `LoadOptions` instance can
      be reused, but remember that the `WarningCallback` persists across loads. If
      you need per‑document isolation, instantiate a fresh `LoadOptions` for each
      iteration.
  - name: Custom Font Substitution Logic
    text: 'Instead of merely logging, you might want to substitute a specific missing
      font with a corporate‑approved alternative. Extend the handler:'
  - name: Silencing Unwanted Warnings
    text: If you only care about font issues and want to suppress everything else,
      filter by `WarningType` as shown. Conversely, to log *all* warnings, drop the
      `if` check and output `info.WarningType` alongside `info.Description`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Font Management
title: Cara Menggunakan LoadOptions untuk Mendeteksi Font yang Hilang
url: /id/net/programming-with-loadoptions/how-to-use-loadoptions-to-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menggunakan LoadOptions untuk Mendeteksi Font yang Hilang

Pernah bertanya‑tanya **bagaimana cara menggunakan LoadOptions** saat memuat dokumen Word dengan Aspose.Words? Pada tutorial ini kami akan menunjukkan **cara menggunakan LoadOptions** untuk **mendeteksi font yang hilang** dan menanganinya dengan elegan. Baik Anda membangun layanan konversi dokumen maupun mesin pelaporan, font yang hilang dapat menyebabkan perubahan tata letak yang tak terduga, sehingga menangkapnya lebih awal sangat penting.

Kami akan membimbing Anda melalui setiap langkah—dari menghubungkan callback peringatan hingga menafsirkan hasilnya—sehingga Anda akan selesai dengan contoh C# yang berfungsi penuh dan dapat langsung dipasang ke proyek .NET apa pun. Tanpa dokumen eksternal, hanya solusi mandiri. Pada akhir tutorial Anda akan mengerti mengapa sistem peringatan ada, cara mengaktifkannya, dan apa yang harus dilakukan ketika callback dipicu.

## Prasyarat

Sebelum kita mulai, pastikan Anda memiliki:

- **Aspose.Words for .NET** (versi terbaru apa pun; API yang kami gunakan stabil sejak 2022).
- Lingkungan pengembangan .NET (Visual Studio, Rider, atau VS Code dengan ekstensi C#).
- File Word contoh (`input.docx`) yang merujuk pada font yang *tidak* terpasang di mesin.

Itu saja—tidak ada paket NuGet tambahan selain Aspose.Words.

## Cara Menggunakan LoadOptions dengan Aspose.Words

Kelas **LoadOptions** adalah pintu gerbang untuk menyesuaikan cara dokumen dibaca. Dengan menyematkan callback peringatan ke dalamnya, Anda dapat **mendeteksi font yang hilang** pada saat Aspose.Words mem-parsing file. Mari kita uraikan.

### Langkah 1: Buat Handler Peringatan

Aspose.Words menggunakan antarmuka `IWarningCallback` untuk memberi tahu Anda tentang masalah non‑kritikal, seperti substitusi font. Implementasikan antarmuka tersebut dan tentukan apa yang akan dilakukan ketika peringatan muncul.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

// Step 1: Define a warning handler that will be notified of font substitutions.
class FontWarningHandler : IWarningCallback
{
    // The Process method is called for every warning Aspose.Words generates.
    public void Process(WarningInfo info)
    {
        // We're only interested in font substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

**Mengapa ini penting:**  
Tanpa callback, Aspose.Words secara diam‑diam mengganti font yang hilang dengan font default (biasanya Arial). Dengan menangkap peringatan `FontSubstitution` Anda dapat mencatat masalah, memberi tahu pengguna, atau bahkan mengganti font yang hilang dengan fallback khusus.

### Langkah 2: Sambungkan Handler ke LoadOptions

Sekarang kita membuat instance `LoadOptions` dan memberitahukannya untuk menggunakan `FontWarningHandler` kita. Inilah titik di mana **cara menggunakan LoadOptions** benar‑benar bersinar.

```csharp
using Aspose.Words.LoadOptions;

// Step 2: Create LoadOptions and attach the warning handler.
var loadOptions = new LoadOptions
{
    // The WarningCallback property accepts any IWarningCallback implementation.
    WarningCallback = new FontWarningHandler()
};
```

**Mengapa ini penting:**  
`LoadOptions` adalah satu‑tempat untuk banyak pengaturan saat impor (encoding, password, dll.). Dengan mengatur `WarningCallback`, Anda mengaktifkan mekanisme berbasis event yang ringan dan bekerja untuk dokumen apa pun yang Anda muat dengan opsi ini.

### Langkah 3: Muat Dokumen Menggunakan Opsi yang Dikonfigurasi

Akhirnya, kita memasukkan `LoadOptions` ke dalam konstruktor `Document`. Jika file sumber merujuk pada font yang tidak terpasang, Aspose.Words akan memicu peringatan dan handler Anda akan mencetak pesan.

```csharp
// Step 3: Load the document using the configured LoadOptions.
// Any missing fonts will trigger the FontWarningHandler.
Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Apa yang akan Anda lihat:**  
Dengan asumsi `input.docx` menggunakan font bernama *“MyCustomFont”* yang tidak ada di mesin, output konsol akan terlihat seperti:

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
```

Jika semua font tersedia, callback tetap diam—tidak ada output, tidak ada penurunan kinerja.

## Mendeteksi Font yang Hilang dengan Callback Peringatan (Kata Kunci Sekunder dalam Aksi)

Frasa **detect missing fonts** muncul secara alami di header di atas, memperkuat kata kunci sekunder. Mari jelajahi beberapa variasi yang mungkin Anda temui dalam proyek nyata.

### Banyak Dokumen dalam Loop

Seringkali Anda akan memproses sekumpulan file. Instance `LoadOptions` yang sama dapat dipakai ulang, tetapi ingat bahwa `WarningCallback` tetap ada di seluruh pemuatan. Jika Anda memerlukan isolasi per‑dokumen, buat `LoadOptions` baru untuk setiap iterasi.

```csharp
string[] files = Directory.GetFiles(@"C:\Docs", "*.docx");
foreach (var file in files)
{
    var options = new LoadOptions { WarningCallback = new FontWarningHandler() };
    var document = new Document(file, options);
    // Perform further processing...
}
```

### Logika Substitusi Font Kustom

Alih‑alih hanya mencatat, Anda mungkin ingin mengganti font yang hilang dengan alternatif yang disetujui perusahaan. Perluas handler:

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Extract the missing font name from the description.
            string missingFont = info.Description.Split('\'')[1];
            // Choose a fallback based on your policy.
            string fallback = missingFont.Equals("MyCustomFont") ? "Calibri" : "Arial";
            Console.WriteLine($"Missing '{missingFont}'. Using fallback '{fallback}'.");
            // You could also modify FontSettings here if needed.
        }
    }
}
```

Sekarang Anda tidak hanya **mendeteksi font yang hilang**, tetapi juga memutuskan bagaimana menggantinya.

### Menonaktifkan Peringatan yang Tidak Diinginkan

Jika Anda hanya peduli pada masalah font dan ingin menekan semua peringatan lain, filter berdasarkan `WarningType` seperti yang ditunjukkan. Sebaliknya, untuk mencatat *semua* peringatan, hapus pengecekan `if` dan keluarkan `info.WarningType` bersama `info.Description`.

## Contoh Lengkap yang Dapat Dijalankan

Menggabungkan semuanya, berikut program lengkap yang dapat Anda kompilasi dan jalankan. Ganti `"YOUR_DIRECTORY/input.docx"` dengan path ke file uji Anda.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Ensure the Aspose.Words license is set if you have one.
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        string docPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
            // You can now work with 'doc' – save, modify, export, etc.
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Output konsol yang diharapkan (ketika ada font yang hilang):**

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

Jika tidak ada font yang hilang, Anda hanya akan melihat:

```
Document loaded successfully.
```

## Kesalahan Umum & Tips Pro

- **Kesalahan:** Lupa mengatur `WarningCallback`. API tetap akan mengganti font, tetapi Anda tidak akan pernah tahu bahwa hal itu terjadi.  
  **Tips pro:** Selalu lampirkan handler ketika Anda membutuhkan kesetiaan font; biayanya hampir nol.

- **Kesalahan:**


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Capture Fonts in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}