---
category: general
date: 2026-06-02
description: cara menangani font di .NET – mendeteksi font yang hilang dan melacak
  perubahan font menggunakan LoadOptions dan FontSettings. Pelajari solusi lengkap
  yang dapat dijalankan.
draft: false
keywords:
- how to handle fonts
- detect missing fonts
- track font changes
language: id
og_description: cara menangani font di .NET – deteksi font yang hilang dan lacak perubahan
  font. Ikuti panduan langkah demi langkah ini untuk solusi lengkap yang siap dijalankan.
og_title: cara menangani font di .NET – mendeteksi font yang hilang
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: how to handle fonts in .NET – detect missing fonts and track font changes
    using LoadOptions and FontSettings. Learn a complete, runnable solution.
  headline: how to handle fonts in .NET – detect missing fonts
  type: TechArticle
tags:
- .NET
- Aspose.Words
- FontSettings
title: Cara menangani font di .NET – mendeteksi font yang hilang
url: /id/net/working-with-fonts/how-to-handle-fonts-in-net-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cara menangani font di .NET – mendeteksi font yang hilang

Pernah bertanya-tanya **bagaimana menangani font** ketika sebuah dokumen Word merujuk pada jenis huruf yang tidak terpasang di mesin? Anda bukan satu‑satunya. Font yang hilang dapat mengubah laporan yang rapi menjadi berantakan, dan tanpa peringatan yang tepat Anda mungkin tidak pernah tahu apa yang telah diganti.  

Dalam tutorial ini kami akan menunjukkan **bagaimana menangani font** dengan mendeteksi font yang hilang **dan** melacak perubahan font pada waktu berjalan. Pada akhir tutorial Anda akan memiliki aplikasi konsol mandiri yang mencatat setiap substitusi, sehingga Anda tidak akan pernah terkejut melihat Helvetica muncul di tempat Times New Roman seharusnya.

> **Apa yang akan Anda dapatkan:** contoh kode lengkap yang siap disalin‑tempel, penjelasan setiap baris, tips untuk proyek dunia nyata, dan tinjauan cepat tentang kasus‑tepi yang mungkin Anda temui.

## Prasyarat

- .NET 6.0 atau lebih baru (contoh menggunakan `Program.cs` tingkat atas untuk singkatnya)  
- Aspose.Words untuk .NET 23.9 atau lebih baru – Anda dapat mengunduhnya dari NuGet dengan `dotnet add package Aspose.Words`  
- Dokumen Word yang sengaja merujuk pada font yang tidak Anda miliki (misalnya `MissingFont.docx`)  

Tidak ada pustaka lain yang diperlukan.

![Diagram yang menunjukkan alur LoadOptions ke FontSettings dan peristiwa peringatan substitusi – contoh cara menangani font di .NET](https://example.com/images/font‑handling‑flow.png "contoh cara menangani font di .NET")

## Langkah 1: Siapkan LoadOptions dengan FontSettings  

Hal pertama yang kita perlukan adalah objek `LoadOptions` yang memberi tahu Aspose.Words untuk memantau masalah font.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;

// Create LoadOptions and attach a fresh FontSettings instance.
var loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

**Mengapa ini penting:** `LoadOptions` adalah penjaga gerbang saat dokumen dibaca dari disk. Dengan menyediakan `FontSettings` khusus kita mendapatkan kait ke mesin resolusi font internal, satu‑satunya cara untuk **mendeteksi font yang hilang** sebelum dokumen dirender.

## Langkah 2: Langganan ke Peristiwa SubstitutionWarning  

Aspose.Words memicu peristiwa `SubstitutionWarning` setiap kali tidak dapat menemukan font tepat yang Anda minta. Kami akan mencatat detailnya sehingga Anda dapat melihat font apa yang diminta dan font apa yang sebenarnya digunakan.

```csharp
// Hook into the warning event – this is where we “track font changes”.
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.RequestedFontName – the name the document asked for.
    // e.SubstitutedFontName – the name Aspose.Words fell back to.
    // e.WarningType – tells you why the substitution happened.
    Console.WriteLine(
        $"[Font Substitution] Requested: {e.RequestedFontName}, " +
        $"Used: {e.SubstitutedFontName}, Reason: {e.WarningType}");
};
```

**Mengapa kita mendengarkan:** Tanpa pendengar ini Anda tidak akan pernah tahu bahwa substitusi terjadi. Peristiwa ini memberikan jejak audit lengkap, memenuhi kebutuhan “melacak perubahan font”.

## Langkah 3: Muat Dokumen Menggunakan Opsi yang Telah Dikonfigurasi  

Sekarang kita benar‑benar membaca file. Karena kita telah melewatkan `loadOptions`, Aspose.Words akan memicu peristiwa peringatan untuk setiap font yang hilang yang ditemukannya.

```csharp
// Replace the path with the location of your test document.
string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

Document doc = new Document(docPath, loadOptions);
```

Itu saja – dokumen kini telah dimuat, dan setiap masalah font sudah dicetak ke konsol.

## Langkah 4: (Opsional) Verifikasi Font yang Disubstitusi dalam Dokumen  

Jika Anda ingin memeriksa kembali font apa yang berakhir di PDF atau DOCX akhir, Anda dapat menelusuri koleksi font dokumen:

```csharp
Console.WriteLine("\n--- Fonts actually used in the document ---");
foreach (FontInfo fontInfo in doc.FontInfos)
{
    Console.WriteLine($"{fontInfo.FontFamilyName} – {fontInfo.FontStyle}");
}
```

Menjalankan ini setelah pemuatan akan menampilkan setiap font yang diputuskan mesin untuk disematkan atau dirujuk. Berguna saat Anda perlu membuat laporan untuk tim QA.

## Contoh Lengkap yang Berfungsi  

Salin blok di bawah ini ke dalam proyek konsol baru (`dotnet new console`) dan jalankan. Program akan menampilkan setiap substitusi lalu mencantumkan font‑font yang bertahan setelah pemuatan.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Prepare LoadOptions with FontSettings.
        // -------------------------------------------------
        var loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Step 2: Hook the substitution warning event.
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            Console.WriteLine(
                $"[Font Substitution] Requested: {e.RequestedFontName}, " +
                $"Used: {e.SubstitutedFontName}, Reason: {e.WarningType}");
        };

        // -------------------------------------------------
        // Step 3: Load the document (this triggers warnings).
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // Step 4 (optional): List fonts actually used.
        // -------------------------------------------------
        Console.WriteLine("\n--- Fonts actually used in the document ---");
        foreach (FontInfo fontInfo in doc.FontInfos)
        {
            Console.WriteLine($"{fontInfo.FontFamilyName} – {fontInfo.FontStyle}");
        }

        Console.WriteLine("\nDone. Press any key to exit.");
        Console.ReadKey();
    }
}
```

### Output yang Diharapkan  

Jika `MissingFont.docx` meminta *“Comic Sans MS”* (yang tidak terpasang) Anda akan melihat sesuatu seperti:

```
[Font Substitution] Requested: Comic Sans MS, Used: Arial, Reason: FontNotFound
[Font Substitution] Requested: Times New Roman, Used: Times New Roman, Reason: None

--- Fonts actually used in the document ---
Arial – Regular
Times New Roman – Regular
```

Baris pertama membuktikan kami **mendeteksi font yang hilang** dan **melacak perubahan font**. Baris kedua menunjukkan substitusi yang tidak perlu terjadi (tidak ada peringatan, karena font tersebut ada).

## Kesalahan Umum & Tips Pro  

| Kesalahan | Apa yang Terjadi | Cara Memperbaiki / Menghindari |
|-----------|------------------|--------------------------------|
| **Tidak ada peristiwa peringatan yang dipicu** | Anda mungkin berpikir API rusak. | Pastikan Anda *menetapkan* `FontSettings` ke `LoadOptions` **sebelum** memuat dokumen. Kait peristiwa harus dipasang **sebelum** pemanggilan `new Document(...)`. |
| **Font yang disubstitusi masih terlihat salah** | Aspose.Words beralih ke font generik yang tidak cocok dengan gaya. | Sediakan folder font khusus melalui `fontSettings.SetFontsFolder(@"C:\MyFonts", true)`. Ini memberi mesin lebih banyak pilihan sebelum beralih ke font generik. |
| **Penurunan kinerja pada dokumen besar** | Memindai setiap font dapat menambah beberapa milidetik. | Cache objek `FontSettings` jika Anda memuat banyak dokumen secara berurutan. Menggunakan kembali instance yang sama menghindari pembacaan ulang tabel font sistem. |
| **Output konsol hilang pada aplikasi GUI** | Anda tidak akan melihat peringatan. | Alihkan peristiwa ke logger (misalnya `Serilog`) atau tulis ke file: `File.AppendAllText("font-warnings.log", …)`. |

## Memperluas Solusi  

- **Ekspor ke PDF dengan font tersemat** – setelah memuat, panggil `doc.Save("output.pdf", SaveOptions.CreateSaveOptions(SaveFormat.Pdf));` dan pastikan mengatur `PdfSaveOptions.FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll;`.  
- **Pemrosesan batch** – bungkus logika pemuatan dalam `foreach` pada folder berisi file DOCX. Catat peringatan tiap file ke CSV untuk keperluan audit.  
- **Antarmuka pengguna yang ramah** – ekspos logika yang sama di balik tombol dalam aplikasi WinForms/WPF, menampilkan peringatan di `ListBox`.

## Kesimpulan  

Kami telah membahas **cara menangani font** di .NET dengan mengonfigurasi `LoadOptions`, berlangganan ke peristiwa `SubstitutionWarning`, dan akhirnya memuat dokumen. Contoh ini tidak hanya **mendeteksi font yang hilang** tetapi juga **melacak perubahan font** sehingga Anda dapat mengaudit setiap substitusi.  

Cobalah dengan dokumen Anda sendiri, sesuaikan jalur folder font, dan Anda tidak akan lagi terkejut oleh pertukaran font yang tak terduga. Jika panduan ini berguna, pertimbangkan untuk menjelajahi topik terkait seperti *“menyematkan font khusus ke PDF dengan Aspose.Words”* atau *“membuat strategi fallback font untuk aplikasi .NET lintas platform.”*  

Selamat coding, semoga dokumen Anda selalu tampil persis seperti yang Anda inginkan!

## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Use LoadOptions in Aspose.Words – Complete Guide](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}