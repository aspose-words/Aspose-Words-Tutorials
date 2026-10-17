---
category: general
date: 2026-01-11
description: Aktifkan peringatan substitusi font untuk mendeteksi font yang hilang
  dalam dokumen .NET Anda. Pelajari cara mendapatkan nama font yang hilang dan daftar
  font yang hilang dengan Aspose.Words.
draft: false
keywords:
- enable font substitution warnings
- detect missing fonts
- get missing font name
- list missing fonts
language: id
og_description: Aktifkan peringatan substitusi font di Aspose.Words untuk mendeteksi
  font yang hilang, mendapatkan nama font yang hilang, dan mencantumkan font yang
  hilang dalam dokumen Anda.
og_title: Aktifkan Peringatan Substitusi Font – Tutorial C# Langkah demi Langkah
tags:
- Aspose.Words
- C#
- Document Processing
title: Aktifkan Peringatan Substitusi Font di Aspose.Words – Panduan Lengkap
url: /id/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aktifkan Peringatan Substitusi Font – Panduan Lengkap

Pernah bertanya-tanya mengapa dokumen Word terlihat sedikit berbeda setelah Anda memuatnya di server? Kemungkinan besar font yang digunakan penulis asli tidak tersedia di mesin Anda, dan Aspose.Words secara diam-diam menggantinya dengan yang paling mirip. **Enable font substitution warnings** dan Anda akan langsung mengetahui font mana yang hilang, apa yang menggantikannya, dan bagaimana menindaklanjuti informasi tersebut.

Dalam tutorial ini kami akan membahas contoh praktis end‑to‑end yang menunjukkan cara **detect missing fonts**, mengambil **get missing font name**, dan bahkan **list missing fonts** untuk pelaporan. Tanpa basa-basi, hanya solusi jelas yang dapat Anda gunakan dalam proyek .NET apa pun hari ini.

---

## Apa yang Akan Anda Pelajari

- Cara mengonfigurasi `LoadOptions` sehingga Aspose.Words menghasilkan peringatan terperinci.
- Kode tepat yang diperlukan untuk memuat dokumen dan mengenumerasi peringatan terkait font.
- Cara mengekstrak nama font yang hilang dan substitusinya, lalu menghasilkan laporan yang rapi.
- Tips menangani kasus tepi, seperti dokumen dengan puluhan font yang hilang atau folder font khusus.

### Prasyarat

- .NET 6+ (kode ini juga berfungsi dengan .NET Framework 4.7+)
- Aspose.Words untuk .NET 23.10 atau yang lebih baru (Anda dapat mengambilnya dari NuGet)
- Sebuah contoh DOCX yang merujuk pada font yang tidak terpasang di sistem Anda (kami akan menyebutnya `MissingFont.docx`)

Jika Anda sudah memiliki hal‑hal tersebut, mari kita mulai.

---

## Langkah 1: Siapkan LoadOptions untuk Mengaktifkan Peringatan Substitusi Font  

Hal pertama yang perlu Anda lakukan adalah memberi tahu Aspose.Words bahwa Anda peduli dengan font yang hilang. Secara default pustaka hanya mencatat peringatan secara internal. Menetapkan `SubstitutionWarningLevel` ke `Typical` (atau `All` untuk output paling detail) mengaktifkan fitur tersebut.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Create a new LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Attach a FontSettings object so we can tweak font‑related behavior
loadOptions.FontSettings = new FontSettings();

// Enable warnings for typical font substitutions (covers most real‑world cases)
loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;
```

**Mengapa ini penting:**  
Ketika `SubstitutionWarningLevel` diatur, setiap kali Aspose.Words tidak dapat menemukan font yang dirujuk, ia menambahkan `FontSubstitutionWarning` ke koleksi `Warnings` dokumen. Koleksi itu adalah satu‑satunya cara yang dapat diandalkan untuk **detect missing fonts** tanpa harus mem-parsing dokumen secara manual.

> **Pro tip:** Jika Anda menangani sekumpulan dokumen dan ingin memastikan semua substitusi tertangkap, gunakan `FontSubstitutionWarningLevel.All`. Ini sedikit lebih berisik tetapi menjamin tidak ada peringatan yang terlewat.

---

## Langkah 2: Muat Dokumen Menggunakan Opsi yang Dikonfigurasi  

Setelah sistem peringatan siap, muat DOCX Anda dengan `LoadOptions` yang baru saja kami siapkan. Path dapat berupa absolut atau relatif; pastikan file tersebut ada.

```csharp
// Path to the DOCX that references a font you don’t have
string docPath = @"C:\Docs\MissingFont.docx";

// Load the document while respecting our warning configuration
Document document = new Document(docPath, loadOptions);
```

**Apa yang terjadi di balik layar?**  
Aspose.Words mem-parsing XML dokumen, menyelesaikan setiap elemen `<w:font>`, dan memeriksa katalog font sistem (serta folder khusus yang mungkin Anda tambahkan ke `FontSettings`). Ketika tidak dapat menemukan font, ia mencatat peringatan—tepat apa yang kita perlukan untuk **list missing fonts** nanti.

---

## Langkah 3: Iterasi Peringatan dan Ekstrak Detail Font yang Hilang  

Dengan dokumen berada di memori, koleksi `Warnings` menyimpan setiap `FontSubstitutionWarning`. Kami akan melakukan loop, menyaring tipe yang tepat, dan mencetak laporan yang ramah.

```csharp
Console.WriteLine("=== Missing Font Report ===");
foreach (WarningInfo warning in document.Warnings)
{
    // Only interested in font substitution warnings
    if (warning is FontSubstitutionWarning fontWarning)
    {
        // The name of the font that was missing
        string missingFont = fontWarning.FontName;

        // The font Aspose.Words used instead
        string substitutedFont = fontWarning.SubstitutedFontName;

        Console.WriteLine($"Missing font: {missingFont}");
        Console.WriteLine($"Substituted with: {substitutedFont}");
        Console.WriteLine(new string('-', 30));
    }
}
```

**Output yang diharapkan** (asumsi dokumen sumber merujuk pada `MyCustomFont` yang tidak terpasang):

```
=== Missing Font Report ===
Missing font: MyCustomFont
Substituted with: Arial
------------------------------
Missing font: FancyScript
Substituted with: Times New Roman
------------------------------
```

Perhatikan bagaimana setiap entri memberikan Anda baik **get missing font name** (`MyCustomFont`) maupun fallback (`Arial`). Itu tepat informasi yang Anda perlukan untuk memutuskan apakah akan menyematkan font asli, meminta penulis menggantinya, atau cukup menerima substitusi.

---

## Langkah 4: Opsional – Kumpulkan Data ke dalam List untuk Pemrosesan Lebih Lanjut  

Jika Anda perlu mengekspor laporan ke CSV, mengirimnya melalui API, atau hanya menyimpannya di memori untuk nanti, Anda dapat menyimpan peringatan dalam list yang strongly‑typed.

```csharp
// Define a simple DTO to hold the warning details
public class MissingFontInfo
{
    public string MissingFont { get; set; }
    public string SubstitutedFont { get; set; }
}

// Build the list
List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();

foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fsw)
    {
        missingFonts.Add(new MissingFontInfo
        {
            MissingFont = fsw.FontName,
            SubstitutedFont = fsw.SubstitutedFontName
        });
    }
}

// Example: write to a CSV (requires System.IO)
var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);
```

Sekarang Anda telah **list missing fonts** dalam format yang dapat dikonsumsi oleh sistem downstream mana pun. Baik Anda mengisi dashboard atau menghasilkan audit log, data sudah siap.

---

## Langkah 5: Menangani Kasus Tepi dan Kendala Umum  

### Banyak Font yang Hilang dalam Satu Jalankan  

Template korporat besar sering merujuk pada puluhan font khusus. Koleksi peringatan dapat menjadi besar, tetapi pola iterasi di atas berskala linear, jadi kinerja tidak menjadi masalah. Ingatlah untuk menjaga output tetap dapat dibaca—mengelompokkan berdasarkan halaman atau gaya dapat membantu bila Anda memerlukan analisis lebih mendalam.

### Folder Font Khusus  

Jika Anda menyimpan font di direktori non‑standar (misalnya, share jaringan bersama), beri tahu Aspose.Words di mana mencarinya:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"\\fileserver\SharedFonts", recursive: true);
```

Menetapkan ini *sebelum* memuat dokumen memberi pustaka kesempatan menemukan font, yang dapat menghilangkan beberapa peringatan sepenuhnya.

### Menyaring Peringatan Tertentu  

Kadang‑kadang Anda tahu substitusi tertentu dapat diterima (misalnya, font dekoratif yang tidak masalah diganti). Anda dapat menyaringnya setelahnya:

```csharp
missingFonts = missingFonts
    .Where(f => f.MissingFont != "DecorativeFont")
    .ToList();
```

### Kompatibilitas Versi  

Enum `FontSubstitutionWarningLevel` telah stabil sejak Aspose.Words 20.12. Jika Anda menggunakan versi yang lebih lama, Anda mungkin perlu memperbarui untuk mengakses fitur tingkat peringatan.

---

## Contoh Lengkap yang Berfungsi  

Berikut adalah program lengkap yang siap dijalankan yang menggabungkan semua langkah di atas. Tempelkan ke dalam proyek console baru, tambahkan paket NuGet Aspose.Words, dan arahkan `docPath` ke dokumen yang merujuk pada font yang hilang.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    // DTO for storing missing font info
    public class MissingFontInfo
    {
        public string MissingFont { get; set; }
        public string SubstitutedFont { get; set; }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure LoadOptions to enable font substitution warnings
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;

            // Optional: add a custom fonts folder
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

            // 2️⃣ Load the document with the above options
            string docPath = @"C:\Docs\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Gather warnings into a list
            List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();
            foreach (WarningInfo warning in doc.Warnings)
            {
                if (warning is FontSubstitutionWarning fsw)
                {
                    missingFonts.Add(new MissingFontInfo
                    {
                        MissingFont = fsw.FontName,
                        SubstitutedFont = fsw.SubstitutedFontName
                    });
                }
            }

            // 4️⃣ Output a human‑readable report
            Console.WriteLine("=== Missing Font Report ===");
            foreach (var info in missingFonts)
            {
                Console.WriteLine($"Missing font: {info.MissingFont}");
                Console.WriteLine($"Substituted with: {info.SubstitutedFont}");
                Console.WriteLine(new string('-', 30));
            }

            // 5️⃣ (Optional) Export to CSV for further analysis
            var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
            File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);

            Console.WriteLine("Report saved to C:\\Docs\\MissingFontsReport.csv");
        }
    }
}
```

Menjalankan program ini akan **enable font substitution warnings**, **detect missing fonts**, **get missing font name**, dan **list missing fonts** baik di konsol maupun file CSV.

---

## Kesimpulan  

Kami baru saja membahas semua yang Anda perlukan untuk **enable font substitution warnings** di Aspose.Words, mulai dari konfigurasi awal hingga mengekstrak daftar bersih font yang hilang. Dengan mengikuti langkah‑langkah di atas Anda dapat mengaudit dokumen, memastikan kesetiaan visual, dan menghindari kejutan tak menyenangkan saat merender di server.

Selanjutnya, Anda mungkin ingin menjelajahi:

- **Embedding missing fonts** langsung ke dalam PDF atau DOCX output (gunakan `FontSettings.EmbeddedFonts`).
- **Automating font installation** pada agen build berdasarkan laporan yang dihasilkan.
- **Integrating with CI pipelines** untuk membuat build gagal ketika font penting tidak ada.

Cobalah itu, dan Anda akan mengubah sistem peringatan sederhana menjadi alur kerja manajemen font yang lengkap.

Selamat coding, semoga semua font Anda ditemukan!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}