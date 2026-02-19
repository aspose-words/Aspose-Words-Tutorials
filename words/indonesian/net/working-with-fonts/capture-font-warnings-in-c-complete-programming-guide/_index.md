---
category: general
date: 2026-02-18
description: Pelajari cara menangkap peringatan font dan mendeteksi font yang hilang
  di C# menggunakan Aspose.Words. Ikuti panduan langkah demi langkah ini untuk menangani
  font yang hilang secara efisien.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- handle missing fonts
- list missing fonts
language: id
og_description: Tangkap peringatan font di C# dan pelajari cara mendeteksi font yang
  hilang, menangani font yang hilang, serta menampilkan daftar font yang hilang dengan
  contoh kode lengkap.
og_title: Menangkap Peringatan Font di C# – Panduan Lengkap
tags:
- Aspose.Words
- C#
- Font Management
title: Tangkap Peringatan Font di C# – Panduan Pemrograman Lengkap
url: /id/net/working-with-fonts/capture-font-warnings-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menangkap Peringatan Font di C# – Panduan Pemrograman Lengkap

Pernah bertanya-tanya bagaimana **menangkap peringatan font** ketika sebuah dokumen merujuk pada font yang tidak terpasang di server? Anda tidak sendirian. Pada banyak aplikasi perusahaan, font yang hilang menyebabkan gangguan tata letak, dan satu‑satunya cara andal untuk menemukannya adalah dengan mendengarkan peringatan yang dilemparkan oleh pustaka.

Dalam tutorial ini kami akan menunjukkan solusi siap‑jalankan yang tidak hanya **menangkap peringatan font** tetapi juga **mendeteksi font yang hilang**, **menangani font yang hilang**, dan bahkan **mendaftar font yang hilang** sehingga Anda dapat memutuskan apakah akan mengganti, menyematkan, atau memberi peringatan kepada pengguna. Tidak perlu dokumentasi eksternal—cukup salin, tempel, dan jalankan.

## Apa yang Akan Anda Pelajari

- Cara mengonfigurasi `LoadOptions` untuk mengaktifkan peringatan substitusi font.  
- Kode tepat yang Anda perlukan untuk memuat DOCX dan mengambil setiap peringatan.  
- Mengapa setiap langkah penting, termasuk pertimbangan kinerja.  
- Penanganan kasus tepi seperti dokumen dengan font skrip campuran atau folder font khusus.  

**Prasyarat**: .NET 6+ (atau .NET Framework 4.6+), referensi ke paket NuGet **Aspose.Words**, dan pemahaman dasar tentang C#. Jika Anda belum pernah menggunakan Aspose.Words sebelumnya, jangan khawatir—panduan ini membimbing Anda melalui setiap nuansa.

![Diagram showing capture font warnings flow](image.png){alt="diagram peringatan font capture"}

## Menangkap Peringatan Font – Mengapa Ini Penting

Ketika Aspose.Words memuat sebuah dokumen, ia diam‑diam mengganti font yang tidak tersedia dengan fallback. Fallback tersebut menjaga operasi pemuatan tetap hidup, tetapi hasil visualnya bisa sangat melenceng. Dengan mengaktifkan flag **SubstitutionWarningLevel.All**, pustaka menambahkan entri `WarningInfo` untuk setiap font yang hilang, memungkinkan Anda **mendeteksi font yang hilang** sebelum dokumen dirender atau disimpan.

> **Tips profesional:** Jika Anda memproses ratusan file dalam pekerjaan batch, mencatat peringatan ini ke penyimpanan pusat dapat menghemat berjam‑jam QA manual di kemudian hari.

## Langkah 1: Siapkan Proyek Anda

1. Buka IDE favorit Anda (Visual Studio, Rider, VS Code).  
2. Buat proyek konsol baru:

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
```

3. Tambahkan paket Aspose.Words:

```bash
dotnet add package Aspose.Words
```

Itu saja—tanpa DLL tambahan, tanpa interop COM. Pustaka menyediakan semua yang Anda perlukan untuk **menangani font yang hilang**.

## Langkah 2: Siapkan Load Options untuk Menangkap Semua Peringatan Substitusi Font

Agar mesin **menangkap peringatan font**, Anda harus memintanya mencatat setiap substitusi. Potongan kode berikut membuat instance `LoadOptions`, mengaktifkan level peringatan, dan (opsional) menunjuk mesin ke folder yang berisi font khusus yang mungkin ingin Anda gunakan.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // Step 2.1 – Create LoadOptions and turn on font‑substitution warnings
            // -----------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions();

            // Initialise FontSettings if you need to add a custom font folder
            loadOptions.FontSettings = new FontSettings();

            // Capture *all* font substitution events (this is the key for capture font warnings)
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // Optional: add a folder that contains corporate fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);
```

**Mengapa ini penting:**  
- `SubstitutionWarningLevel.All` memastikan **setiap** kejadian font yang hilang tercatat, bukan hanya yang pertama.  
- Tanpa flag ini, Aspose.Words secara diam‑diam mengganti font dan Anda tidak pernah tahu ada masalah.

## Langkah 3: Muat Dokumen Menggunakan Opsi yang Dikonfigurasi

Sekarang kita benar‑benarnya membuka file. Ganti `DocumentWithMissingFonts.docx` dengan jalur ke dokumen uji Anda.

```csharp
            // -----------------------------------------------------------------
            // Step 2.2 – Load the document with the warning‑enabled options
            // -----------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";

            Document document = new Document(docPath, loadOptions);
```

Jika file berisi referensi ke font yang tidak ada di mesin (atau di folder opsional yang Anda tambahkan), `document.WarningInfoCollection` akan terisi.

## Langkah 4: Temukan dan Tampilkan Setiap Peringatan Substitusi Font

Berikut inti tutorial: iterasi atas `WarningInfoCollection` untuk **mendaftar font yang hilang**. Kita akan memfilter dengan `WarningType.FontSubstitution` dan mencetak pesan yang ramah.

```csharp
            // -----------------------------------------------------------------
            // Step 2.3 – Enumerate and output font substitution warnings
            // -----------------------------------------------------------------
            var fontWarnings = document.WarningInfoCollection
                                         .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    // The Description property already contains a readable message
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // Keep console window open when debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Output yang Diharapkan

```
⚠️ Missing fonts detected:
- Missing font: "Comic Sans MS"
- Missing font: "Calibri Light"
```

Jika dokumen hanya menggunakan font yang terpasang, Anda akan melihat baris “✅ Tidak ada font yang hilang terdeteksi”.

## Langkah 5: Lanjutan – Cara **Menangani Font yang Hilang** Secara Programatis

Mencetak daftar mungkin cukup untuk alat diagnostik, tetapi banyak sistem produksi memerlukan **menangani font yang hilang** secara otomatis. Berikut dua strategi umum:

### 5.1 Substitusi dengan Fallback yang Dikenal

```csharp
loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution
{
    // Replace any missing font with Arial, which is universally available
    SubstituteFont = "Arial"
};
```

### 5.2 Menyematkan Font Kustom Secara Dinamis

Jika Anda memiliki file font perusahaan (`MyBrand.ttf`), Anda dapat menyematkannya ketika font yang hilang terdeteksi:

```csharp
foreach (WarningInfo warning in fontWarnings)
{
    string missingFontName = warning.Description.Split('"')[1]; // crude extraction
    // Load your custom font (ensure the path is correct)
    string customFontPath = $@"C:\MyCompany\Fonts\{missingFontName}.ttf";

    if (File.Exists(customFontPath))
    {
        loadOptions.FontSettings.SetFontsFolder(Path.GetDirectoryName(customFontPath), false);
        Console.WriteLine($"🔧 Embedded custom font for \"{missingFontName}\"");
    }
}
```

> **Catatan:** Menyematkan font dapat meningkatkan ukuran file output, jadi timbanglah trade‑off antara kesetiaan tampilan dan bandwidth.

## Kesalahan Umum dan Cara Menghindarinya

| Gejala | Penyebab Kemungkinan | Solusi |
|--------|----------------------|--------|
| Tidak ada peringatan muncul meskipun dokumen terlihat salah | `SubstitutionWarningLevel` tidak disetel ke `All` | Pastikan langkah 2 mengatur flag persis seperti yang ditunjukkan |
| Daftar peringatan menampilkan font yang sama berulang kali | Dokumen berisi font tersebut dalam beberapa gaya | Hilangkan duplikat jika Anda hanya membutuhkan daftar unik: `fontWarnings.Select(w => w.Description).Distinct()` |
| Aplikasi crash pada file DOCX besar | Memuat dengan pengaturan memori default | Gunakan `LoadOptions.LoadFormat` atau alirkan file untuk mengurangi tekanan memori |

## Contoh Lengkap yang Siap Pakai (Copy‑Paste)

```csharp
using System;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ---------------------------------------------------------------
            // Configure LoadOptions to capture font warnings
            // ---------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // OPTIONAL: add a folder with custom fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);

            // ---------------------------------------------------------------
            // Load the document
            // ---------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // ---------------------------------------------------------------
            // Retrieve and display missing‑font warnings
            // ---------------------------------------------------------------
            var fontWarnings = doc.WarningInfoCollection
                                  .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // ---------------------------------------------------------------
            // OPTIONAL: automatic handling (fallback or embedding)
            // ---------------------------------------------------------------
            // Example: substitute everything with Arial
            // loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution { SubstituteFont = "Arial" };

            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

Jalankan program dengan `dotnet run`. Anda akan melihat daftar font yang hilang dicetak ke konsol, mengonfirmasi bahwa Anda telah berhasil **menangkap peringatan font**.

## Kesimpulan

Anda kini memiliki pola lengkap yang siap produksi untuk **menangkap peringatan font**, **mendeteksi font yang hilang**, **menangani font yang hilang**, dan **mendaftar font yang hilang** menggunakan Aspose.Words di C#. Pendekatan ini ringan, hanya memerlukan beberapa baris kode, dan dapat disisipkan ke dalam pipeline apa pun—baik Anda

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}