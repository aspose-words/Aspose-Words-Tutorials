---
category: general
date: 2026-02-28
description: Pelajari cara menangani peringatan font dan mendeteksi font yang hilang
  di Aspose.Words menggunakan C#. Panduan lengkap langkah demi langkah dengan kode
  lengkap.
draft: false
keywords:
- handle font warnings
- detect missing fonts
language: id
og_description: Tangani peringatan font di Aspose.Words dan deteksi font yang hilang
  dengan contoh C# siap pakai. Ikuti langkah-langkahnya dan lihat hasilnya.
og_title: Menangani Peringatan Font di Aspose.Words – Panduan Lengkap
tags:
- Aspose.Words
- C#
- Document Loading
title: Menangani Peringatan Font di Aspose.Words – Deteksi Font yang Hilang
url: /id/net/working-with-fonts/handle-font-warnings-in-aspose-words-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menangani Peringatan Font di Aspose.Words – Mendeteksi Font yang Hilang

Pernahkah Anda perlu **menangani peringatan font** saat memuat dokumen Word dan bertanya-tanya mengapa beberapa teks terlihat aneh? Anda tidak sendirian. Font yang hilang memicu peringatan substitusi yang dapat secara diam‑diam merusak tata letak visual, dan jika Anda tidak **mendeteksi font yang hilang** Anda tidak akan pernah tahu apa yang salah.

Dalam tutorial ini kami akan menunjukkan cara praktis untuk **menangani peringatan font** menggunakan `IWarningCallback` milik Aspose.Words. Pada akhir panduan Anda akan dapat melihat setiap peristiwa substitusi font, mencatatnya, dan bahkan memutuskan apakah akan menghentikan proses pemuatan. Tanpa dokumen eksternal, hanya contoh siap salin‑tempel tunggal.

## Apa yang Akan Anda Pelajari

- Menyiapkan penangan peringatan khusus yang hanya bereaksi terhadap peringatan substitusi font.  
- Menempelkan penangan ke `LoadOptions` sehingga setiap pemuatan dokumen melewatinya.  
- Memverifikasi output di konsol dan memahami arti setiap peringatan.  

**Prasyarat**

- .NET 6.0 atau lebih baru (kode ini juga berfungsi dengan .NET Framework 4.6+).  
- Aspose.Words untuk .NET terpasang via NuGet (`Install-Package Aspose.Words`).  
- File Word yang merujuk pada font yang tidak terpasang di mesin Anda (misalnya, font korporat khusus).  

Jika Anda belum memiliki salah satu dari itu, dapatkan sekarang—jika tidak, mari kita mulai.

## Cara Menangani Peringatan Font di Aspose.Words

Di bawah ini adalah program lengkap yang dapat dijalankan. Ia mencakup semua mulai dari pernyataan `using` hingga metode `Main`, sehingga Anda dapat menaruhnya dalam aplikasi konsol dan menekan **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

/// <summary>
/// Custom warning handler that reacts only to font‑substitution warnings.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font substitution events.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a clear message to the console – this is how we **detect missing fonts**.
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 1: Create LoadOptions and attach the custom warning callback.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // Step 2: Load the document. Any missing font will trigger our handler.
        // Replace the path with the actual location of your test document.
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        // Keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

> **Output konsol yang diharapkan** (asumsi dokumen menggunakan font yang tidak Anda miliki terpasang):
> ```
> ⚠️ Font substituted: Font 'MyCustomFont' was substituted with 'Arial'.
> ✅ Document loaded successfully.
> 
> Press any key to exit...
> ```

Jika dokumen tidak mengandung **font yang hilang**, baris peringatan tidak pernah muncul—jadi Anda secara efektif **mendeteksi font yang hilang** hanya ketika diperlukan.

### Mengapa Ini Berfungsi

Aspose.Words melempar `WarningInfo` untuk setiap masalah non‑kritikal yang ditemuinya saat mem‑parse file. Dengan mengimplementasikan `IWarningCallback` Anda mendapatkan kait ke dalam alur tersebut. Flag `WarningType.FontSubstitution` memberi tahu Anda secara tepat kapan perpustakaan harus mengganti font yang diminta dengan fallback. Ini adalah cara paling dapat diandalkan untuk **menangani peringatan font** karena dijalankan *selama* pemuatan, sebelum Anda menyentuh model objek dokumen.

## Deteksi Font yang Hilang Tanpa Merusak Aplikasi Anda

Kadang‑kadang Anda mungkin ingin memperlakukan font yang hilang sebagai kesalahan fatal—mungkin pedoman merek Anda melarang substitusi apa pun. Anda dapat memodifikasi penangan untuk melempar pengecualian alih‑alih hanya mencatat:

```csharp
public void Warning(WarningInfo info)
{
    if (info.WarningType == WarningType.FontSubstitution)
    {
        // Throwing stops the load process; you can catch it higher up.
        throw new InvalidOperationException($"Missing font detected: {info.Description}");
    }
}
```

Sekarang blok `try…catch` di sekitar `new Document(...)` akan menangkap masalah, memberi Anda pilihan untuk menghentikan, menggunakan fallback, atau meminta pengguna.

## Bonus: Memvisualisasikan Peringatan dalam Aplikasi UI

Jika Anda membangun aplikasi WinForms atau WPF, ganti `Console.WriteLine` dengan pemanggilan yang ramah UI:

```csharp
MessageBox.Show($"Font substituted: {info.Description}", "Font Warning",
                MessageBoxButtons.OK, MessageBoxIcon.Warning);
```

Dengan cara itu, pengguna akhir melihat peringatan secara langsung, dan Anda tetap **menangani peringatan font** secara konsisten di semua platform.

## Kesalahan Umum & Tips Pro

- **Pitfall:** Lupa mengatur `WarningCallback`. Perilaku default adalah mengabaikan peringatan font, sehingga Anda tidak akan pernah melihatnya.  
  **Pro tip:** Selalu buat instance `LoadOptions` meskipun Anda hanya membutuhkan penangan peringatan. Ini murah dan eksplisit.  

- **Pitfall:** Menggunakan pemisah jalur yang salah pada OS non‑Windows.  
  **Pro tip:** Gunakan `Path.Combine` atau literal string mentah (`@"C:\Docs\MissingFont.docx"` berfungsi di Windows; di Linux gunakan `"/home/user/docs/MissingFont.docx"`).  

- **Pitfall:** Mengasumsikan peringatan akan muncul untuk font yang di‑embed.  
  **Pro tip:** Font yang di‑embed dianggap hadir, jadi tidak ada peringatan substitusi. Uji dengan font yang benar‑benar *hilang* untuk melihat penangan beraksi.  

- **Pitfall:** Mencatat semua jenis peringatan secara berlebihan.  
  **Pro tip:** Filter dengan `WarningType.FontSubstitution` seperti yang ditunjukkan—ini menjaga konsol tetap bersih dan memfokuskan pada skenario **mendeteksi font yang hilang**.  

## Ringkasan Contoh Kerja Penuh

Berikut seluruh program lagi, kali ini tanpa komentar bagi yang lebih suka tampilan bersih:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
    }
}

class Program
{
    static void Main()
    {
        var loadOptions = new LoadOptions { WarningCallback = new FontWarningHandler() };
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

Salin, tempel, jalankan—konsol Anda kini akan **menangani peringatan font** dan **mendeteksi font yang hilang** secara otomatis.

## Langkah Selanjutnya

- **Log ke file:** Ganti `Console.WriteLine` dengan logger (misalnya, NLog) untuk pelacakan tingkat produksi.  
- **Pemrosesan batch:** Loop melalui folder dokumen, mengumpulkan semua peristiwa substitusi font dalam laporan CSV.  
- **Instalasi font otomatis:** Kaitkan ke penangan peringatan untuk mengunduh font yang hilang dari repositori korporat sebelum pemuatan dilanjutkan.  

Setiap ekstensi ini dibangun di atas gagasan inti **menangani peringatan font** secara bersih dan dapat digunakan kembali.

---

*Selamat coding! Jika Anda menemukan kejanggalan saat mencoba **mendeteksi font yang hilang**, tinggalkan komentar di bawah. Saya dengan senang hati akan membantu Anda memecahkan masalah.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}