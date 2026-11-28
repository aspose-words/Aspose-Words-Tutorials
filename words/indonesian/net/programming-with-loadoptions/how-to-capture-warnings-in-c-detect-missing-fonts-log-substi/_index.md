---
category: general
date: 2026-04-04
description: Pelajari cara menangkap peringatan, mendeteksi font yang hilang, dan
  mencatat peristiwa substitusi menggunakan Aspose.Words LoadOptions dalam C#.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to log substitution
- Aspose.Words warning handling
- font substitution monitoring
language: id
og_description: Cara menangkap peringatan, mendeteksi font yang hilang, dan mencatat
  peristiwa substitusi menggunakan Aspose.Words LoadOptions dalam C#.
og_title: Cara Menangkap Peringatan di C# – Deteksi Font yang Hilang & Mencatat Substitusi
tags:
- C#
- Aspose.Words
- Document Loading
- Font Management
title: Cara Menangkap Peringatan di C# – Deteksi Font yang Hilang & Catat Substitusi
url: /id/net/programming-with-loadoptions/how-to-capture-warnings-in-c-detect-missing-fonts-log-substi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menangkap Peringatan di C# – Deteksi Font yang Hilang & Log Substitusi

Pernah bertanya‑tanya **bagaimana cara menangkap peringatan** yang muncul saat Anda memuat dokumen Word dengan font yang hilang? Anda tidak sendirian. Dalam banyak proyek dunia nyata, font hilang selama migrasi, dan fallback yang diam dapat merusak tata letak Anda. Kabar baiknya? Aspose.Words menyediakan cara bersih untuk mendengarkan peringatan tersebut, mendeteksi font yang hilang, dan bahkan mencatat setiap substitusi sehingga Anda dapat memperbaiki sumbernya nanti.

Dalam tutorial ini kami akan menelusuri solusi lengkap yang siap dijalankan yang menunjukkan **cara menangkap peringatan**, mendemonstrasikan **deteksi font yang hilang**, dan menjelaskan **cara mencatat peristiwa substitusi**. Pada akhir tutorial, Anda akan memiliki handler peringatan yang dapat digunakan kembali, objek `LoadOptions` yang sepenuhnya dikonfigurasi, dan contoh output konsol yang dapat Anda verifikasi.

> **Prasyarat:** Anda memerlukan Aspose.Words untuk .NET (v24.x atau lebih baru) yang diinstal melalui NuGet dan lingkungan pengembangan C# dasar (Visual Studio 2022 atau VS Code sudah cukup).

---

## Cara Menangkap Peringatan Saat Memuat Dokumen

Inti solusi adalah kelas yang mengimplementasikan `IWarningCallback`. Aspose.Words memanggil callback ini secara otomatis untuk setiap peringatan yang dihasilkan selama pemuatan dokumen, termasuk peringatan substitusi font.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

/// <summary>
/// Handles warning callbacks from Aspose.Words.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This line prints the warning to the console.
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Mengapa langkah ini?**  
> Dengan memfilter pada `WarningType.FontSubstitution` kita menghindari kekacauan dari peringatan yang tidak terkait (seperti fitur yang sudah usang). Ini membuat log terfokus pada masalah tepat yang Anda pedulikan—font yang hilang.

---

## Deteksi Font yang Hilang dengan Aspose.Words

Ketika sebuah dokumen merujuk pada font yang tidak terpasang di mesin, Aspose.Words menggantinya dengan yang paling mirip dan mengeluarkan peringatan. Handler kita di atas akan menangkap setiap kejadian, secara efektif **mendeteksi font yang hilang**.

Untuk melihatnya beraksi, kita perlu mengonfigurasi `LoadOptions` dan melampirkan handler:

```csharp
// Configure load options and attach the warning callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

> **Tip:** Jika Anda lebih suka mengumpulkan peringatan untuk diproses kemudian (misalnya, menulis ke file), ganti `Console.WriteLine` dengan kode yang menambahkan pesan ke `List<string>`.

---

## Cara Mencatat Peristiwa Substitusi

Mencatat sesederhana mengarahkan output peringatan ke penyimpanan yang persisten. Berikut contoh singkat yang menulis setiap peringatan substitusi ke file teks bernama `font-warnings.log`.

```csharp
using System.IO;

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            // Append the message to the log file.
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

// Later, when creating LoadOptions:
var loadOptions = new LoadOptions
{
    WarningCallback = new FileLoggingWarningHandler()
};
```

> **Mengapa mencatat ke file?**  
> Log yang persisten memungkinkan Anda mengaudit masalah font di banyak run, mengotomatisasi peringatan, atau memasukkan data ke dalam pemeriksaan pipeline build.

---

## Contoh Lengkap yang Berfungsi

Menggabungkan semuanya, berikut aplikasi konsol mandiri yang dapat Anda salin, tempel, dan jalankan. Ini mendemonstrasikan **cara menangkap peringatan**, **deteksi font yang hilang**, dan **cara mencatat substitusi** dalam satu langkah.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

class Program
{
    static void Main()
    {
        // Choose which handler you want:
        // var handler = new FontWarningHandler();          // console output
        var handler = new FileLoggingWarningHandler();    // file logging

        var loadOptions = new LoadOptions
        {
            WarningCallback = handler
        };

        // Path to the document that may contain missing fonts.
        string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        try
        {
            // Load the document – warnings are raised automatically.
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
        }

        // If you used the file logger, show where the log lives.
        if (handler is FileLoggingWarningHandler)
        {
            Console.WriteLine($"Font warnings have been written to 'font-warnings.log'.");
        }
    }
}
```

### Output Konsol yang Diharapkan

Jika `input.docx` merujuk pada font yang tidak terpasang, Anda akan melihat sesuatu seperti:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

Jika Anda beralih ke `FileLoggingWarningHandler`, baris‑baris yang sama akan muncul di dalam `font-warnings.log` dengan stempel waktu.

![output konsol cara menangkap peringatan](image-placeholder.png)

---

## Pertanyaan Umum & Kasus Tepi

### Bagaimana jika saya perlu menangkap *semua* peringatan, bukan hanya substitusi font?

Cukup hapus pengecekan `if (info.Type == WarningType.FontSubstitution)`. Callback akan menerima setiap tipe peringatan (`WarningType.DegradedDocument`, `WarningType.UnexpectedContent`, dll.). Anda kemudian dapat membranch pada `info.Type` untuk menangani masing‑masing kasus secara berbeda.

### Apakah ini bekerja dengan PDF atau hanya dokumen Word?

`LoadOptions` dan `IWarningCallback` merupakan bagian dari Aspose.Words, sehingga berlaku untuk format yang kompatibel dengan Word (`.docx`, `.doc`, `.rtf`, `.html`). Untuk PDF Anda harus menggunakan mekanisme peringatan milik Aspose.PDF.

### Bagaimana cara menekan peringatan alih‑alih mencatatnya?

Setel `LoadOptions.WarningCallback = null` atau implementasikan callback tetapi biarkan isi metodenya kosong. Perpustakaan tetap akan melakukan substitusi secara diam‑diam.

### Bagaimana dengan keamanan thread?

Instansi callback dipanggil pada thread yang sama dengan yang memuat dokumen, jadi Anda tidak memerlukan sinkronisasi tambahan kecuali Anda membagikan handler di antara pemuatan paralel. Dalam kasus tersebut, lindungi sumber daya bersama (misalnya, file log) dengan `lock` atau gunakan koleksi bersamaan.

---

## Kesimpulan

Kami telah membahas **cara menangkap peringatan** dari Aspose.Words, menunjukkan **cara mendeteksi font yang hilang**, dan menjelaskan **cara mencatat peristiwa substitusi** untuk analisis selanjutnya. Dengan menyematkan implementasi sederhana `IWarningCallback` ke dalam `LoadOptions`, Anda mendapatkan visibilitas penuh terhadap masalah terkait font tanpa menambah kebisingan pada basis kode Anda.

Langkah selanjutnya? Coba perpanjang logger untuk mengirim email, integrasikan dengan Azure Monitor, atau secara otomatis menginstal font yang hilang pada server build. Anda juga dapat menjelajahi tipe peringatan lain—`WarningType.DegradedDocument` dapat memberi tahu Anda tentang fitur yang tidak bertahan selama proses konversi.

Masih ada pertanyaan tentang penanganan font atau Aspose.Words secara umum? Tinggalkan komentar atau buat isu baru di forum Aspose. Selamat coding, semoga dokumen Anda selalu tampil dengan tipe huruf yang tepat!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}