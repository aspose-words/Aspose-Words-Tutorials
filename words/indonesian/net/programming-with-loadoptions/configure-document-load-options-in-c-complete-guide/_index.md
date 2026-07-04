---
category: general
date: 2026-06-05
description: Konfigurasikan opsi pemuatan dokumen di C# untuk menangani peringatan
  substitusi font dan menyesuaikan perilaku pemuatan menggunakan callback peringatan.
draft: false
keywords:
- configure document load options
- warning callback
- font substitution warning
- LoadOptions usage
- Aspose.Words document loading
- C# document loading options
language: id
og_description: Konfigurasikan opsi pemuatan dokumen di C# untuk mengelola peringatan
  substitusi font dan menyetel pemuatan dokumen secara detail dengan callback peringatan.
og_title: Konfigurasikan opsi pemuatan dokumen di C# – Panduan Lengkap
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: Configure document load options in C# to handle font substitution warnings
    and customize loading behavior using a warning callback.
  headline: Configure document load options in C# – Complete Guide
  type: TechArticle
- description: Configure document load options in C# to handle font substitution warnings
    and customize loading behavior using a warning callback.
  name: Configure document load options in C# – Complete Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works with .NET Framework 4.6+ as well).
      - Aspose.Words for .NET installed (`dotnet add package Aspose.Words`). - Basic
      familiarity with C# syntax.'
  - name: Implement a Warning Callback for Font Substitution
    text: First things first—what’s a **warning callback**? In Aspose.Words it’s a
      delegate that gets invoked whenever the library encounters something worth flagging,
      like a missing font. By catching `WarningType.FontSubstitution` we can log the
      exact font the engine swapped out.
  - name: Set Up LoadOptions with the Callback
    text: Now that we have a callback, we need to **configure document load options**
      to actually use it. `LoadOptions` is a lightweight container that tells Aspose.Words
      how to behave during the `Document` constructor call.
  - name: Load the Document Using the Configured Options
    text: With the callback wired up, the final act is to actually **load the document**.
      The `Document` constructor accepts a file path and the `LoadOptions` we just
      prepared.
  - name: Optional – Verify Loaded Fonts (Edge Case Handling)
    text: Sometimes you might want to *pre‑validate* the document before loading it
      fully, especially in batch processing scenarios. Aspose.Words offers the `FontSettings`
      class that can enumerate required fonts.
  - name: What if the warning callback throws an exception?
    text: The callback runs on the same thread that loads the document. Throwing inside
      the delegate will abort the load and propagate the exception. Wrap your logic
      in a `try/catch` if you need resilience.
  - name: Can I suppress *all* warnings instead of handling them?
    text: Yes—set `loadOptions.WarningCallback = null;` or provide a callback that
      does nothing. Be aware you’ll lose visibility into potential problems.
  - name: Does this work with encrypted DOCX files?
    text: Absolutely. Just add `Password = "yourPassword"` to `LoadOptions` before
      creating the `Document`. The warning callback will still fire for font issues.
  - name: How does this differ from using `DocumentBuilder`?
    text: '`DocumentBuilder` is for *creating* or *modifying* a document after it’s
      loaded. **Configure document load options** influences the *initial* parsing
      stage, which is where font substitution decisions are made.'
  type: HowTo
tags:
- C#
- Aspose.Words
- LoadOptions
- DocumentProcessing
title: Konfigurasikan opsi pemuatan dokumen di C# – Panduan Lengkap
url: /id/net/programming-with-loadoptions/configure-document-load-options-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Konfigurasikan opsi pemuatan dokumen di C# – Panduan Lengkap

Pernah perlu **mengonfigurasi opsi pemuatan dokumen** di C# karena perilaku pemuatan default tidak memadai? Mungkin Anda melihat substitusi font yang tidak terduga atau ingin mencatat setiap peringatan yang muncul saat mengimpor file. Pada tutorial ini kami akan membahas solusi praktis end‑to‑end yang tidak hanya menyiapkan opsi‑opsi tersebut tetapi juga memperlihatkan **warning callback** untuk peringatan substitusi font.

Kami akan membahas semuanya mulai dari potongan kode kecil yang membuat callback hingga saat Anda akhirnya membuka dokumen dengan pengaturan khusus Anda. Pada akhir tutorial Anda akan memiliki pola yang dapat digunakan kembali dan dapat disisipkan ke proyek Aspose.Words mana pun, baik Anda memproses faktur, kontrak hukum, atau laporan sederhana.

## Apa yang Akan Anda Pelajari

- Cara **mengonfigurasi opsi pemuatan dokumen** dengan `LoadOptions`.
- Cara mengimplementasikan **warning callback** yang menangkap peringatan `FontSubstitution`.
- Mengapa menangani **peringatan substitusi font** lebih awal dapat menyelamatkan Anda dari kejutan tata letak.
- Penanganan kasus‑edge untuk font yang hilang dan cara fallback dengan elegan.
- Contoh kode lengkap, siap salin‑tempel, yang dapat Anda jalankan hari ini.

### Prasyarat

- .NET 6.0 atau lebih baru (kode ini juga berfungsi dengan .NET Framework 4.6+).
- Aspose.Words untuk .NET terpasang (`dotnet add package Aspose.Words`).
- Familiaritas dasar dengan sintaks C#.

Jika Anda sudah memiliki semua itu, mari kita mulai.

## Konfigurasikan Opsi Pemuatan Dokumen – Langkah demi Langkah

Berikut adalah alur kerja lengkap yang dibagi menjadi empat langkah jelas. Setiap langkah dijelaskan, kemudian diikuti oleh blok kode ringkas yang dapat Anda tempel langsung ke Visual Studio.

### Langkah 1: Implementasikan Callback Peringatan untuk Substitusi Font

Pertama-tama—apa itu **warning callback**? Di Aspose.Words itu adalah delegate yang dipanggil setiap kali perpustakaan menemukan sesuatu yang layak ditandai, seperti font yang hilang. Dengan menangkap `WarningType.FontSubstitution` kita dapat mencatat font tepat yang diganti oleh mesin.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Define a warning callback that reports font substitution warnings
var fontWarningCallback = new IWarningCallback(
    warningInfo =>
    {
        // Check if the warning is about font substitution
        if (warningInfo.WarningType == WarningType.FontSubstitution)
        {
            // Log the warning – you could also write to a file or telemetry system
            Console.WriteLine($"Font substitution detected: {warningInfo.Description}");
        }
    });
```

**Mengapa ini penting:** Tanpa callback, perpustakaan secara diam‑diam mengganti font yang hilang, yang dapat menyebabkan teks berantakan di PDF atau DOCX akhir. Dengan menampilkan peringatan Anda memperoleh visibilitas dan dapat memutuskan apakah akan menyematkan font yang hilang, beralih ke fallback, atau memberi tahu pengguna.

> **Pro tip:** Jika Anda perlu menangkap *semua* peringatan, hapus pengecekan `if`. Cukup catat `warningInfo.Description` untuk setiap peristiwa.

### Langkah 2: Siapkan LoadOptions dengan Callback

Sekarang kita memiliki callback, kita perlu **mengonfigurasi opsi pemuatan dokumen** agar benar‑benar menggunakannya. `LoadOptions` adalah wadah ringan yang memberi tahu Aspose.Words bagaimana berperilaku selama pemanggilan konstruktor `Document`.

```csharp
// Step 2: Attach the callback to the LoadOptions object
var loadOptions = new LoadOptions
{
    WarningCallback = fontWarningCallback,
    // Optional: enforce strict loading mode (throws on any warning)
    // LoadFormat = LoadFormat.Docx,
    // LoadOptions.LoadFormat can be left null to auto-detect based on file extension
};
```

**Mengapa ini penting:** Dengan menetapkan `WarningCallback`, setiap peringatan yang dikeluarkan selama fase pemuatan dialirkan melalui delegate kami. Anda juga dapat menyesuaikan properti `LoadOptions` lainnya di sini—seperti `LoadFormat` jika Anda mengetahui tipe file secara tepat, atau `Password` untuk dokumen terenkripsi.

### Langkah 3: Muat Dokumen Menggunakan Opsi yang Dikonfigurasi

Dengan callback yang terhubung, aksi terakhir adalah benar‑benar **memuat dokumen**. Konstruktor `Document` menerima jalur file dan `LoadOptions` yang baru saja kita siapkan.

```csharp
// Step 3: Load the document with our custom options
string inputPath = @"C:\Docs\input.docx";   // Adjust to your environment
Document doc = new Document(inputPath, loadOptions);
```

Jika file sumber merujuk pada font yang tidak terpasang di mesin, Anda akan melihat baris seperti:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

di konsol. Umpan balik langsung ini memungkinkan Anda memutuskan apakah akan menyertakan font yang hilang bersama aplikasi Anda atau menggantinya secara programatik.

### Langkah 4: Opsional – Verifikasi Font yang Dimuat (Penanganan Kasus Edge)

Kadang‑kadang Anda mungkin ingin *pre‑validate* dokumen sebelum memuatnya sepenuhnya, terutama dalam skenario pemrosesan batch. Aspose.Words menyediakan kelas `FontSettings` yang dapat mengenumerasi font yang dibutuhkan.

```csharp
// Optional: Check required fonts before full load
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);
loadOptions.FontSettings = fontSettings;

// Re-load the document now that we have a custom font folder
Document docWithCustomFonts = new Document(inputPath, loadOptions);
```

**Kapan menggunakan ini:** Jika Anda memelihara repositori font pribadi (misalnya, font merek perusahaan), mengarahkan `FontSettings` ke folder tersebut memastikan mesin menemukan tipe huruf yang tepat tanpa harus kembali ke yang generik.

## Contoh Kerja Lengkap

Berikut adalah seluruh program—cukup salin, tempel, dan jalankan. Program ini memperlihatkan semuanya mulai dari pembuatan callback hingga pemuatan dokumen akhir.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // 1️⃣ Define the warning callback
        var fontWarningCallback = new IWarningCallback(
            warningInfo =>
            {
                if (warningInfo.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substitution detected: {warningInfo.Description}");
                }
            });

        // 2️⃣ Configure LoadOptions with the callback
        var loadOptions = new LoadOptions
        {
            WarningCallback = fontWarningCallback,
            // Uncomment the next line to point to a custom font folder
            // FontSettings = new FontSettings { SetFontsFolder(@"C:\MyFonts", true) }
        };

        // 3️⃣ Load the document using the custom options
        string inputFile = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputFile, loadOptions);

        // 4️⃣ (Optional) Save as PDF to verify everything works
        string outputFile = @"YOUR_DIRECTORY/output.pdf";
        doc.Save(outputFile);
        Console.WriteLine($"Document loaded and saved to {outputFile}");
    }
}
```

**Output yang diharapkan**

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Document loaded and saved to C:\Your\Path\output.pdf
```

Jika tidak ada font yang hilang, callback tetap diam—tidak ada yang perlu dikhawatirkan.

## Pertanyaan Umum & Kasus Edge

### Bagaimana jika callback peringatan melemparkan pengecualian?

Callback dijalankan pada thread yang sama dengan proses pemuatan dokumen. Melempar pengecualian di dalam delegate akan menghentikan pemuatan dan meneruskan pengecualian tersebut. Bungkus logika Anda dalam `try/catch` jika memerlukan ketahanan.

### Bisakah saya menekan *semua* peringatan alih-alih menanganinya?

Ya—set `loadOptions.WarningCallback = null;` atau sediakan callback yang tidak melakukan apa‑apa. Perlu diingat Anda akan kehilangan visibilitas terhadap potensi masalah.

### Apakah ini bekerja dengan file DOCX terenkripsi?

Tentu saja. Cukup tambahkan `Password = "yourPassword"` ke `LoadOptions` sebelum membuat `Document`. Callback peringatan tetap akan dipicu untuk masalah font.

### Bagaimana ini berbeda dari penggunaan `DocumentBuilder`?

`DocumentBuilder` digunakan untuk *membuat* atau *memodifikasi* dokumen setelah dimuat. **Konfigurasikan opsi pemuatan dokumen** memengaruhi tahap *parsing awal*, tempat keputusan substitusi font dibuat.

## Gambaran Visual

![Diagram yang menunjukkan alur konfigurasi opsi pemuatan dokumen](https://example.com/images/load-options-flow.png "Diagram yang menunjukkan alur konfigurasi opsi pemuatan dokumen")

*Gambar ini menggambarkan alur: callback → LoadOptions → konstruktor Document → penanganan peringatan.*

## Kesimpulan

Anda kini tahu cara **mengonfigurasi opsi pemuatan dokumen** di C# untuk menangkap peringatan substitusi font, menyuntikkan folder font khusus, dan mempertahankan kontrol penuh atas proses pemuatan. Pola ini memberi Anda keyakinan bahwa setiap font yang hilang akan dilaporkan, memungkinkan Anda menjaga kesetiaan dokumen di semua lingkungan.

Langkah selanjutnya? Coba ganti pencatatan ke konsol dengan sistem telemetri yang lebih kuat, atau gabungkan pendekatan ini dengan `DocumentBuilder` untuk secara otomatis mengganti font yang hilang dengan default perusahaan. Anda juga dapat menjelajahi nilai `WarningType` lainnya seperti `DocumentStructure` untuk wawasan yang lebih mendalam.

Selamat coding, semoga dokumen Anda selalu tampil persis seperti yang Anda inginkan!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Menguasai Opsi Muat Markdown Aspose.Words di Python untuk Pemrosesan Dokumen yang Ditingkatkan](/words/english/python-net/document-operations/aspose-words-markdown-load-options-python/)
- [Mengoptimalkan Pemuatan Dokumen dengan Opsi HTML, RTF, dan TXT](/words/english/java/word-processing/optimizing-document-loading-options/)
- [Menggunakan Opsi Dokumen dan Pengaturan di Aspose.Words untuk Java](/words/english/java/document-manipulation/using-document-options-and-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}