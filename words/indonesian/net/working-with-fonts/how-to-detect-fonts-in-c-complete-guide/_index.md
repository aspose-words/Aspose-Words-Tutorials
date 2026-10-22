---
category: general
date: 2026-04-02
description: Cara mendeteksi font dalam dokumen C# menggunakan Aspose.Words. Pelajari
  cara mengonfigurasi pengaturan font dan menangani font yang hilang secara efisien.
draft: false
keywords:
- how to detect fonts
- configure font settings
- handle missing fonts
- font substitution warning
- Aspose.Words font handling
language: id
og_description: Cara mendeteksi font dalam dokumen C# menggunakan Aspose.Words. Panduan
  ini menunjukkan cara mengonfigurasi pengaturan font dan menangani font yang hilang.
og_title: Cara Mendeteksi Font di C# – Panduan Lengkap
tags:
- C#
- Aspose.Words
- Document Processing
title: Cara Mendeteksi Font di C# – Panduan Lengkap
url: /id/net/working-with-fonts/how-to-detect-fonts-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Mendeteksi Font di C# – Panduan Lengkap

Pernah bertanya-tanya **bagaimana cara mendeteksi font** yang hilang atau digantikan saat Anda memuat dokumen Word di .NET? Anda bukan satu‑satunya—para pengembang sering menemui kendala ketika sebuah dokumen merujuk pada font yang tidak terpasang di server. Kabar baiknya, Aspose.Words menyediakan cara yang bersih dan programatis untuk menemukan celah‑celah tersebut.

Dalam tutorial ini kami akan membimbing Anda melalui contoh langsung yang tidak hanya menunjukkan **bagaimana cara mendeteksi font**, tetapi juga mendemonstrasikan cara **mengonfigurasi pengaturan font** dan **menangani font yang hilang** dengan elegan. Pada akhir tutorial Anda akan memiliki potongan kode siap‑jalankan yang mencetak setiap peringatan substitusi font, sehingga Anda dapat mencatat, memberi peringatan, atau mengganti font sesuai kebutuhan.

---

## Apa yang Anda Butuhkan

- **Aspose.Words for .NET** (versi terbaru paling cocok; kode di bawah menargetkan .NET 6+)
- Lingkungan pengembangan .NET (Visual Studio, Rider, atau VS Code)
- Contoh file `.docx` yang merujuk pada font yang tidak Anda miliki terpasang (bagus untuk pengujian)

Tidak diperlukan paket NuGet tambahan selain Aspose.Words, dan solusi ini bekerja di Windows, Linux, dan macOS.

---

## Langkah 1: Instal dan Referensikan Aspose.Words

Pertama, tambahkan pustaka ke proyek Anda. Perintah NuGet-nya sangat sederhana:

```bash
dotnet add package Aspose.Words
```

> **Tips Pro:** Jika Anda berada di server CI, kunci versi paket untuk menghindari perubahan yang tidak terduga.

---

## Langkah 2: Konfigurasikan Pengaturan Font (dan Siapkan Load Options)

Sebelum Anda membuka dokumen, Anda dapat memberi tahu Aspose.Words di mana mencari font cadangan. Ini adalah bagian **konfigurasikan pengaturan font** yang mencegah mesin secara diam‑diam menukar font yang mungkin tidak Anda inginkan.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 2: Create a FontSettings object and point it to a folder with fallback fonts
var fontSettings = new FontSettings();

// Example: add a custom folder that contains common Windows fonts
fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);

// You can also embed a default font to use when nothing matches
fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

// Wrap the settings into LoadOptions so Aspose.Words uses them when loading
var loadOptions = new LoadOptions { FontSettings = fontSettings };
```

Mengapa repot? Jika dokumen merujuk pada *Comic Sans* tetapi server Anda hanya memiliki *Calibri*, Aspose.Words akan menggantinya dengan *Calibri* dan mengeluarkan peringatan. Dengan mengonfigurasi jalur pencarian, Anda mengurangi kejutan yang tidak diinginkan.

---

## Langkah 3: Muat Dokumen dengan Opsi yang Telah Disiapkan

Sekarang kita benar‑benar membuka file. `LoadOptions` yang kami buat pada langkah sebelumnya diteruskan langsung ke konstruktor `Document`.

```csharp
// Step 3: Load the Word file using the configured FontSettings
var docPath = @"C:\Docs\input.docx";
var document = new Document(docPath, loadOptions);
```

Jika file tidak dapat ditemukan atau rusak, sebuah pengecualian akan dilempar—sehingga Anda mungkin ingin membungkusnya dalam blok try/catch pada kode produksi.

---

## Langkah 4: Pindai Peringatan Dokumen untuk Substitusi Font

Aspose.Words mengumpulkan daftar peringatan saat melakukan parsing. Di antaranya, `FontSubstitutionWarning` memberi tahu Anda secara tepat font mana yang diganti.

```csharp
// Step 4: Iterate over warnings and look for FontSubstitutionWarning instances
foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fontWarning)
    {
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
}
```

Koleksi `Warnings` juga dapat berisi item lain (misalnya, `DocumentStructureWarning`). Menyaring untuk `FontSubstitutionWarning` memastikan kita hanya melaporkan skenario **menangani font yang hilang** yang kami pedulikan.

---

## Langkah 5: Gabungkan Semua – Contoh Lengkap yang Dapat Dijalankan

Berikut adalah program lengkapnya. Salin‑tempel ke dalam aplikasi konsol baru dan jalankan; Anda akan melihat setiap font yang hilang dicetak ke konsol.

```csharp
// Full example: Detect font substitutions in a Word document
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare font settings (configure font settings)
        var fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);
        fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

        // 2️⃣ Build load options with those settings
        var loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document (handle missing fonts gracefully)
        var docPath = @"C:\Docs\input.docx";
        Document document;
        try
        {
            document = new Document(docPath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Scan warnings for font substitution events
        bool anySubstitutions = false;
        foreach (WarningInfo warning in document.Warnings)
        {
            if (warning is FontSubstitutionWarning fontWarning)
            {
                anySubstitutions = true;
                Console.WriteLine(
                    $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
            }
        }

        // 5️⃣ Inform the user if everything was fine
        if (!anySubstitutions)
        {
            Console.WriteLine("No font substitutions detected – all fonts were found.");
        }
    }
}
```

**Output yang diharapkan** (contoh):

```
Font 'Times New Roman' was substituted with 'Arial'.
Font 'Comic Sans MS' was substituted with 'Arial'.
```

Jika dokumen hanya menggunakan font yang ada di mesin, Anda akan melihat baris “No font substitutions detected” sebagai gantinya.

---

## Kasus Pojok & Pertanyaan Umum

### Bagaimana jika dokumen tidak mengandung **peringatan** sama sekali?

Itu berarti semua font yang dirujuk ditemukan di folder pencarian yang Anda konfigurasikan. Flag `anySubstitutions` dalam contoh menangani kasus ini.

### Bisakah saya **mencatat** peringatan ke file alih‑alih ke konsol?

Tentu saja. Ganti pemanggilan `Console.WriteLine` dengan logger pilihan Anda (Serilog, NLog, dll.). Objek `WarningInfo` juga menyediakan `WarningType` dan `WarningMessage` jika Anda memerlukan detail lebih lanjut.

### Bagaimana saya dapat **mengabaikan** font tertentu, seperti font merek perusahaan yang tidak boleh pernah ditukar?

Anda dapat menambahkan aturan substitusi khusus:

```csharp
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("MyBrandFont", new[] { "Arial", "Helvetica" });
```

Sekarang Aspose.Words hanya akan mengganti *MyBrandFont* dengan alternatif yang terdaftar, dan Anda tetap akan menerima peringatan yang dapat ditindaklanjuti.

### Apakah ini bekerja pada kontainer **Linux**?

Ya—pastikan Anda memasang folder dengan file `.ttf`/`.otf` yang diperlukan dan arahkan `SetFontsFolder` ke sana. Aspose.Words tidak bergantung pada font yang terpasang di OS.

---

## Gambaran Visual

![alur deteksi font](detect-fonts.png "Diagram yang menunjukkan langkah‑langkah mendeteksi font dalam dokumen")

*Teks alt gambar:* **alur deteksi font** diagram yang menggambarkan konfigurasi, pemuatan, dan inspeksi peringatan.

---

## Ringkasan – Apa yang Telah Kita Pelajari

- **Cara mendeteksi font** yang hilang atau digantikan menggunakan peringatan Aspose.Words.  
- Cara **mengonfigurasi pengaturan font** untuk menunjuk ke folder font khusus dan menetapkan fallback default.  
- Strategi untuk **menangani font yang hilang**, mulai dari pencatatan hingga aturan substitusi khusus.

Semua ini dapat dimasukkan ke dalam aplikasi konsol yang ringkas dan mandiri yang dapat Anda sisipkan ke dalam solusi .NET apa pun.

---

## Langkah Selanjutnya & Topik Terkait

- **Menyematkan font** langsung ke dalam dokumen output untuk menghindari substitusi di masa mendatang (`SaveOptions` dengan `EmbedFullFonts`).  
- **Penggantian font secara programatis** – mengganti font yang hilang dengan alternatif tertentu sebelum menyimpan.  
- **Pengoptimalan kinerja** – cache `FontSettings` saat memproses banyak dokumen secara batch.  

Jika Anda tertarik pada topik tersebut, cari *configure font settings* dan *handle missing fonts*—mereka akan mengarahkan Anda ke pembahasan lebih mendalam tentang manajemen font dengan Aspose.Words.

---

Selamat coding! Memiliki kasus tepi font yang aneh? Tinggalkan komentar, dan kami akan membantu memecahkannya bersama.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}