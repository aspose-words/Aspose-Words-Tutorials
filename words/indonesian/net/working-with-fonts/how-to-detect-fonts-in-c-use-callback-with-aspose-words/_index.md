---
category: general
date: 2026-03-17
description: Cara mendeteksi font di C# menggunakan Aspose.Words dan callback peringatan.
  Pelajari cara menggunakan callback untuk menangkap substitusi font yang hilang saat
  memuat dokumen.
draft: false
keywords:
- how to detect fonts
- how to use callback
- Aspose.Words font detection
- C# missing font warning
- warning callback example
language: id
og_description: Cara mendeteksi font di C# menggunakan Aspose.Words. Panduan ini menunjukkan
  cara menggunakan callback untuk menangkap peringatan font yang hilang saat memuat
  dokumen.
og_title: Cara Mendeteksi Font di C# – Gunakan Callback dengan Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Cara Mendeteksi Font di C# – Gunakan Callback dengan Aspose.Words
url: /id/net/working-with-fonts/how-to-detect-fonts-in-c-use-callback-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Mendeteksi Font di C# – Gunakan Callback dengan Aspose.Words

Pernah membutuhkan **cara mendeteksi font** dalam dokumen Word secara programatis dan bertanya-tanya mengapa beberapa karakter terlihat aneh setelah konversi? Anda tidak sendirian. Dalam banyak proyek dunia nyata—generator faktur, pengekspor laporan, atau pipeline pemrosesan batch—font yang hilang menyebabkan gangguan tata letak yang diam dan sulit di‑debug.  

Berita baik? Aspose.Words memberi Anda cara bersih untuk menampilkan masalah tersebut dengan callback peringatan. Dalam tutorial ini Anda akan melihat **cara menggunakan callback** untuk menangkap setiap substitusi font yang dilakukan Aspose saat memuat dokumen, dan Anda akan mendapatkan contoh siap‑jalankan yang mencetak laporan jelas tentang font yang hilang.

Kami akan membahas:

* Prasyarat minimal (proyek .NET dan paket NuGet Aspose.Words).  
* Cara mengimplementasikan `IWarningCallback` untuk mendengarkan `WarningType.FontSubstitution`.  
* Cara menyambungkan callback ke `LoadOptions` dan memuat dokumen.  
* Seperti apa outputnya, plus beberapa tip praktis untuk kode produksi.

Pada akhir tutorial, Anda akan dapat secara otomatis **mendeteksi font** dalam file DOCX, DOC, atau RTF apa pun dan menindaklanjuti informasi font yang hilang—baik itu mencatat, memberi peringatan kepada pengguna, atau mengganti dengan font cadangan.

---

![Cara mendeteksi font dalam dokumen Word menggunakan callback peringatan Aspose.Words](https://example.com/images/detect-fonts.png "cara mendeteksi font dalam dokumen Word")

## Apa yang Anda Butuhkan

* **.NET 6.0** atau lebih baru (contoh ini juga dapat dikompilasi dengan .NET Framework 4.6+).  
* **Aspose.Words for .NET** – instal melalui NuGet: `Install-Package Aspose.Words`.  
* File Word contoh yang sengaja merujuk ke font yang tidak Anda miliki (misalnya `MissingFont.docx`).  

Tidak ada pustaka tambahan yang diperlukan; semuanya berada di dalam namespace Aspose.

---

## Cara Mendeteksi Font dengan Callback Peringatan

### Langkah 1: Buat kelas callback peringatan

Callback mengimplementasikan `IWarningCallback`. Ketika Aspose.Words menemukan font yang tidak dapat ditemukan, ia menghasilkan `WarningInfo` dengan `WarningType.FontSubstitution`. Kelas kami hanya menulis satu baris ramah ke konsol.

```csharp
using System;
using Aspose.Words.Warnings;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about missing‑font warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Example output: [Font substitution] Missing: "Comic Sans MS"
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
        }
    }
}
```

**Mengapa ini penting:** Dengan memfilter pada `WarningType.FontSubstitution` kita menghindari peringatan yang berisik (seperti fitur usang) dan menjaga log tetap fokus pada masalah tepat yang ingin Anda selesaikan—**mendeteksi font** yang tidak ada di mesin.

### Langkah 2: Sambungkan callback ke `LoadOptions`

`LoadOptions` memungkinkan Anda menyesuaikan cara dokumen di‑parse. Menetapkan `FontWarningCollector` kami ke properti `WarningCallback` memberi tahu Aspose untuk memanggilnya setiap kali font yang hilang terdeteksi.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Configure load options with our custom warning handler.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Tip:** Anda juga dapat mengatur `LoadOptions.FontSettings` di sini jika ingin menyediakan font cadangan secara programatis. Itu adalah skenario lanjutan yang akan kami sebutkan nanti.

### Langkah 3: Muat dokumen dan perhatikan outputnya

Sekarang kita benar‑benar memuat file. Begitu Aspose mem‑parse dokumen, setiap font yang tidak dapat ditemukan memicu callback kami.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\MissingFont.docx";

try
{
    Document doc = new Document(docPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
}
```

**Output konsol yang diharapkan** (asumsi dokumen merujuk ke *Comic Sans MS* yang tidak terpasang):

```
[Font substitution] Missing: "Comic Sans MS"
Document loaded successfully.
```

Jika dokumen berisi beberapa font yang hilang, Anda akan melihat satu baris per font—tepat informasi **cara mendeteksi font** yang Anda butuhkan.

## Cara Menggunakan Callback untuk Skenario yang Lebih Kompleks

### Mencatat ke file alih‑alih konsol

Di produksi Anda mungkin menginginkan log yang persisten. Ganti `Console.WriteLine` dengan `StreamWriter`:

```csharp
class FontWarningCollector : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            File.AppendAllText(_logPath,
                $"[Font substitution] Missing: {info.Description}{Environment.NewLine}");
        }
    }
}
```

### Mengumpulkan peringatan untuk analisis nanti

Kadang‑kadang Anda memerlukan daftar font yang hilang setelah dokumen dimuat, mungkin untuk menampilkan dialog UI. Simpan peringatan dalam `List<string>` dan expose‑kan:

```csharp
class FontWarningCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}

// Usage
var collector = new FontWarningCollector();
LoadOptions opts = new LoadOptions { WarningCallback = collector };
Document doc = new Document(docPath, opts);

if (collector.MissingFonts.Any())
{
    Console.WriteLine("Missing fonts detected:");
    collector.MissingFonts.ForEach(f => Console.WriteLine($"- {f}"));
}
```

### Menyediakan font cadangan secara programatis

Jika Anda memiliki font korporat yang ingin ditegakkan, Anda dapat menambahkannya ke `FontSettings` sebelum memuat:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";

LoadOptions opts = new LoadOptions
{
    WarningCallback = new FontWarningCollector(),
    FontSettings = fontSettings
};

Document doc = new Document(docPath, opts);
```

Sekarang Aspose menggantikan font yang hilang dengan *Arial Unicode MS* sambil tetap melaporkan substitusi melalui callback. Ini adalah cara yang bagus untuk **cara menggunakan callback** baik untuk deteksi maupun remediasi otomatis.

## Kesulitan Umum dan Pro Tips

| Kesulitan | Mengapa Terjadi | Cara Menghindari |
|-----------|----------------|------------------|
| **Lupa merujuk `Aspose.Words.Warnings`** | Antarmuka `IWarningCallback` berada di sana. | Tambahkan `using Aspose.Words.Warnings;` di bagian atas. |
| **Memuat dokumen tanpa `LoadOptions`** | Loader default secara diam‑diam menggantikan font tanpa notifikasi. | Selalu buat instance `LoadOptions` dan tetapkan callback Anda. |
| **Menjalankan di server dengan izin terbatas** | Menulis ke file log dapat melempar `UnauthorizedAccessException`. | Gunakan folder yang dapat ditulis (mis., direktori data aplikasi) atau tetap gunakan koleksi dalam memori. |
| **Beberapa thread berbagi collector yang sama** | `FontWarningCollector` tidak thread‑safe secara default. | Buat collector terpisah per thread atau lindungi list dengan lock. |
| **Mengira callback dipicu untuk font yang ter‑embed** | Font yang ter‑embed sudah ada dalam dokumen; tidak ada peringatan. | Jika Anda perlu memverifikasi integritas font ter‑embed, inspeksi `FontInfo` melalui `FontSettings`. |

## Contoh Lengkap yang Siap Pakai (Copy‑Paste)

```csharp
// ------------------------------------------------------------
// Detect missing fonts in a Word document using Aspose.Words
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningCollector : IWarningCallback
{
    // Store warnings for later use (optional)
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Print to console
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
            // Keep a copy in memory
            MissingFonts.Add(info.Description);
        }
    }
}

class Program
{
    static void Main()
    {
        // Path to the document you want to inspect
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

        // 1️⃣ Create the callback collector
        var collector = new FontWarningCollector();

        // 2️⃣ Set up LoadOptions with the callback
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = collector
        };

        // 3️⃣ Load the document – warnings will fire automatically
        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");

            // Optional: act on the collected data
            if (collector.MissingFonts.Count > 0)
            {
                Console.WriteLine("\nSummary of missing fonts:");
                foreach (var font in collector.MissingFonts)
                    Console.WriteLine($"- {font}");
            }
            else
            {
                Console.WriteLine("\nNo missing fonts detected.");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Apa yang harus Anda lihat** (asumsi file merujuk ke dua font yang tidak ada):

```
[Font substitution] Missing: "Comic Sans MS"
[Font substitution] Missing: "Papyrus"
Document loaded successfully.

Summary of missing fonts:
- Comic Sans MS
- Papyrus
```

Jika file hanya menggunakan font yang terpasang, konsol cukup mencetak:

```
Document loaded successfully.

No missing fonts detected.
```

## Penutup

Kami telah membahas **cara mendeteksi font** dalam dokumen Word dengan menyambungkan callback peringatan khusus ke Aspose.Words. Pendekatan ini ringan, memerlukan

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}