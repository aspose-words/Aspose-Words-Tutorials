---
category: general
date: 2026-04-07
description: Pelajari cara mendeteksi font dan menangkap peringatan saat menangani
  font yang hilang di C# menggunakan Aspose.Words. Kode langkah demi langkah disertakan.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- handle missing fonts
- Aspose.Words font substitution
- C# document loading warnings
language: id
og_description: Bagaimana cara mendeteksi font di Aspose.Words? Ikuti tutorial ini
  untuk menangkap peringatan dan menangani font yang hilang dengan mudah.
og_title: Cara Mendeteksi Font di Aspose.Words – Panduan Lengkap
tags:
- Aspose.Words
- C#
- Font handling
title: Cara Mendeteksi Font di Aspose.Words – Panduan Lengkap
url: /id/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Mendeteksi Font di Aspose.Words – Panduan Lengkap

Pernah bertanya‑tanya **bagaimana cara mendeteksi font** yang tidak ada dalam dokumen Word sebelum Anda mengirimnya ke produksi? Anda tidak sendirian. Dalam banyak skenario perusahaan, satu font yang hilang dapat merusak alur konversi PDF atau menyebabkan gangguan tata letak yang tampak tidak profesional. Kabar baiknya, Aspose.Words menyediakan cara bawaan untuk menemukan tipe huruf yang tidak ada tersebut dan menampilkan peringatan yang jelas.

Dalam tutorial ini kami akan membahas secara detail **cara mendeteksi font**, **cara menangkap peringatan**, dan praktik terbaik untuk **menangani font yang hilang** sehingga aplikasi Anda tetap tangguh. Tanpa alat eksternal, tanpa tebakan—hanya kode C# murni yang dapat Anda tambahkan ke proyek Anda sekarang juga.

> **Pratinjau cepat:** Pada akhir tutorial Anda akan memiliki `FontSubstitutionWarningCollector` yang dapat digunakan kembali untuk mengumpulkan setiap pesan substitusi font selama pemuatan dokumen, dan Anda akan tahu cara merespons ketika sebuah font tidak dapat ditemukan.

---

## Apa yang Akan Anda Pelajari

- Cara mengonfigurasi `LoadOptions` untuk mendengarkan peringatan substitusi font.  
- Cara menangkap peringatan tersebut dalam kelas kolektor khusus.  
- Cara memproses peringatan yang terkumpul dan memutuskan apakah akan menghentikan proses, mencatat, atau mengganti font.  
- Penanganan kasus tepi untuk dokumen yang merujuk font remote atau font yang disematkan.  

**Prasyarat:** .NET 6+ (atau .NET Framework 4.6+), Aspose.Words untuk .NET (versi terbaru), dan pemahaman dasar tentang C#. Jika Anda belum pernah menggunakan Aspose.Words sebelumnya, jangan khawatir—panduan ini mengasumsikan hanya beberapa menit waktu penyiapan.

---

## Cara Mendeteksi Font Menggunakan Aspose.Words LoadOptions

Langkah pertama untuk mendeteksi font yang hilang adalah memberi tahu Aspose.Words untuk melaporkannya. Hal ini dilakukan melalui properti `LoadOptions.WarningCallback`, yang menerima kelas apa pun yang mengimplementasikan `IWarningCallback`. Di bawah ini kami membuat kolektor kecil yang menyimpan setiap peringatan untuk inspeksi selanjutnya.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.Collections.Generic;

/// <summary>
/// Collects all warnings emitted while loading a document.
/// </summary>
public class FontSubstitutionWarningCollector : IWarningCallback
{
    // Thread‑safe static list so we can access warnings after loading.
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();

    // Called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑related warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Warnings.Add(info);
        }
    }

    // Helper to clear previous run’s warnings.
    public static void Clear() => Warnings.Clear();
}
```

**Mengapa ini penting:** Tanpa callback peringatan, Aspose.Words secara diam‑diam mengganti font yang hilang dengan font default, dan Anda tidak pernah tahu bahwa ada masalah. Dengan menangkap `WarningType.FontSubstitution` kita mendapatkan visibilitas penuh—tepat data yang Anda butuhkan untuk **mendeteksi font** yang tidak tersedia di mesin host.

Sekarang kita mengaitkan kolektor ke dalam `LoadOptions` dan memuat sebuah dokumen:

```csharp
// Step 1: Prepare load options with our warning collector.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontSubstitutionWarningCollector()
};

// Optional: clear any stale warnings from a previous run.
FontSubstitutionWarningCollector.Clear();

// Step 2: Load the document. Replace the path with your own file.
Document doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
```

> **Tips pro:** Jika Anda bekerja dengan banyak dokumen secara batch, gunakan kembali instance `FontSubstitutionWarningCollector` yang sama tetapi ingat untuk memanggil `Clear()` di antara pemuatan untuk menghindari pencampuran peringatan dari file yang berbeda.

---

## Menangkap Peringatan Selama Pemuatan Dokumen

Setelah dokumen dimuat, kolektor sudah menyimpan setiap peringatan yang terkait dengan font. Pertanyaan logis berikutnya adalah: *Bagaimana saya menangkap peringatan* dengan cara yang mudah dicatat atau ditampilkan?

```csharp
// Step 3: Iterate over collected warnings and output them.
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    Console.WriteLine($"{warning.Type}: {warning.Message}");
}
```

Output tipikal terlihat seperti:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'Garamond' missing. Using 'Times New Roman' instead.
```

**Apa yang diberitahukan:** Setiap baris mengungkapkan nama font asli dan fallback yang dipilih oleh Aspose.Words. Dengan informasi ini Anda dapat memutuskan apakah fallback tersebut dapat diterima atau apakah Anda perlu menyematkan font yang hilang secara manual.

---

## Menangani Font yang Hilang dengan Elegan

Mendeteksi dan menangkap peringatan hanyalah setengah dari perjuangan. Nilai sebenarnya muncul ketika Anda **menangani font yang hilang** secara siap produksi. Berikut tiga strategi umum:

1. **Catat dan Lanjutkan** – Cocok untuk pemrosesan batch di mana Anda hanya memerlukan jejak audit.  
2. **Hentikan pada Font Kritis** – Lemparkan exception jika font tertentu (misalnya, tipe huruf merek khusus) tidak ada.  
3. **Sematkan Font Secara Dinamis** – Muat font yang hilang dari folder yang diketahui dan daftarkan ke Aspose.Words sebelum memuat ulang dokumen.

### Contoh: Hentikan pada Font Kritis

```csharp
// Define a list of fonts that must be present.
var requiredFonts = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };

foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    // Extract the original font name from the warning message.
    string missingFont = ExtractFontName(warning.Message);
    if (requiredFonts.Contains(missingFont))
    {
        throw new InvalidOperationException(
            $"Critical font '{missingFont}' is missing. Document load aborted.");
    }
}

// Helper method to parse font name from warning text.
string ExtractFontName(string message)
{
    // Message pattern: "Font 'X' was not found..."
    int start = message.IndexOf('\'') + 1;
    int end = message.IndexOf('\'', start);
    return (start > 0 && end > start) ? message[start..end] : string.Empty;
}
```

### Contoh: Auto‑Embed Font yang Hilang

```csharp
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    string missingFont = ExtractFontName(warning.Message);
    string fontPath = $@"C:\Fonts\{missingFont}.ttf";

    if (File.Exists(fontPath))
    {
        // Register the font with Aspose.Words.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(Path.GetDirectoryName(fontPath), false);
        doc.FontSettings = fontSettings;

        // Reload the document now that the font is available.
        doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
        break; // Re‑load once; subsequent warnings will be resolved.
    }
}
```

**Mengapa pola ini membantu:** Dengan secara eksplisit memutuskan apa yang harus dilakukan ketika sebuah font tidak ada, Anda menghilangkan fallback diam‑diam yang dapat merusak merek atau keterbacaan. Inilah inti dari **menangani font yang hilang** secara terkontrol.

---

## Contoh Kerja Lengkap

Menggabungkan semuanya, berikut adalah program tunggal yang siap dijalankan yang mendemonstrasikan **cara mendeteksi font**, **cara menangkap peringatan**, dan kebijakan sederhana untuk **menangani font yang hilang** dengan mencatatnya.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.Collections.Generic;
using System.IO;

public class FontSubstitutionWarningCollector : IWarningCallback
{
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Warnings.Add(info);
    }
    public static void Clear() => Warnings.Clear();
}

class Program
{
    static void Main()
    {
        string docPath = @"C:\Docs\MissingFonts.docx";

        // 1️⃣ Configure LoadOptions with the warning collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontSubstitutionWarningCollector()
        };
        FontSubstitutionWarningCollector.Clear();

        // 2️⃣ Load the document – this is where fonts are detected.
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Process the collected warnings.
        if (FontSubstitutionWarningCollector.Warnings.Count == 0)
        {
            Console.WriteLine("✅ No missing fonts detected.");
        }
        else
        {
            Console.WriteLine("⚠️ Font substitution warnings:");
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
                Console.WriteLine($"{w.Type}: {w.Message}");

            // Example policy: abort if a brand‑critical font is missing.
            var critical = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
            {
                string missing = ExtractFontName(w.Message);
                if (critical.Contains(missing))
                {
                    Console.WriteLine($"❌ Critical font '{missing}' missing. Stopping.");
                    return;
                }
            }
        }

        // 4️⃣ Continue with normal processing (e.g., save as PDF).
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
        Console.WriteLine("✅ Document saved as PDF.");
    }

    // Helper to pull the original font name out of the warning text.
    static string ExtractFontName(string message)
    {
        int first = message.IndexOf('\'') + 1;
        int last = message.IndexOf('\'', first);
        return (first > 0 && last > first) ? message[first..last] : string.Empty;
    }
}
```

**Hasil yang diharapkan:** Saat Anda menjalankan program terhadap dokumen yang merujuk font yang tidak ada di mesin, konsol akan menampilkan setiap peringatan substitusi. Jika ada peringatan yang melibatkan font dari himpunan `critical`, program akan keluar lebih awal, mencegah PDF yang cacat dihasilkan.

---

## Pertanyaan yang Sering Diajukan (FAQ)

| Pertanyaan | Jawaban |
|------------|----------|
| *Apakah saya memerlukan lisensi untuk Aspose.Words agar dapat menggunakan kode ini?* | Ya, lisensi Aspose.Words yang valid menghilangkan watermark evaluasi dan membuka semua fungsi penuh. |
| *Apakah pendekatan ini dapat mendeteksi font yang disematkan?* | Font yang disematkan sudah menjadi bagian dari file, sehingga Aspose.Words tidak akan mengeluarkan peringatan substitusi. Anda dapat memeriksa `Document.FontInfos` untuk mendaftar font yang disematkan bila diperlukan. |
| *Bagaimana jika font yang hilang adalah font sistem di Windows tetapi tidak ada di Linux?* | Peringatan yang sama akan muncul di Linux karena font tidak terpasang di sana. Gunakan strategi “menangani font yang hilang” untuk menyertakan file `.ttf` yang diperlukan bersama aplikasi Anda. |
| *Apakah kolektor peringatan berjalan di thread |  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}