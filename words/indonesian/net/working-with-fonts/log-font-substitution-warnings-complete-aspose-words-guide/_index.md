---
category: general
date: 2026-01-14
description: Catat peringatan substitusi font saat memuat dokumen Word dengan Aspose.Words.
  Pelajari cara mendeteksi font yang hilang dan cara menangkap font yang hilang di
  C#.
draft: false
keywords:
- log font substitution warnings
- detect missing fonts
- how to capture missing fonts
language: id
og_description: Catat peringatan substitusi font saat memuat dokumen Word dengan Aspose.Words.
  Temukan cara mendeteksi font yang hilang dan menangkap font yang hilang dalam C#.
og_title: Catatan Peringatan Substitusi Font – Panduan Lengkap Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Catatan Peringatan Penggantian Font – Panduan Lengkap Aspose.Words
url: /id/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mencatat Peringatan Substitusi Font – Panduan Lengkap Aspose.Words

Mencatat peringatan substitusi font sangat penting ketika Anda perlu memastikan bahwa dokumen Word terlihat persis sama setelah dimuat oleh Aspose.Words. Jika Anda pernah bertanya-tanya bagaimana cara **detect missing fonts** atau ingin mengetahui **how to capture missing fonts**, Anda berada di tempat yang tepat.  

Dalam tutorial ini kami akan membahas skenario dunia nyata, menunjukkan kode C# lengkap, dan menjelaskan mengapa setiap baris penting. Pada akhir tutorial Anda akan dapat mencatat setiap peristiwa substitusi font dan menindaklanjutinya—tidak ada peringatan misterius yang tersisa.

![Log font substitution warnings example](/images/font-warnings.png "Screenshot showing console output of log font substitution warnings")

## Apa yang Akan Anda Pelajari

- Cara mengkonfigurasi `LoadOptions` sehingga Aspose.Words menghasilkan peringatan bertipe untuk substitusi font.  
- Langkah tepat untuk **detect missing fonts** selama pemuatan dokumen.  
- Cara bersih untuk **capture missing fonts** dan menuliskannya ke log atau sistem pemantauan Anda.  
- Penanganan kasus tepi (misalnya, ketika dokumen berisi font yang tidak terpasang di server).  

### Prasyarat

- .NET 6.0 atau lebih baru (kode ini juga bekerja dengan .NET Framework 4.6+).  
- Lisensi Aspose.Words untuk .NET yang valid (atau percobaan gratis).  
- Pemahaman dasar tentang C# dan aplikasi konsol.  

Jika Anda sudah memiliki semua itu, mari kita mulai.

## Langkah 1 – Siapkan LoadOptions untuk Menghasilkan Peringatan Bertipe

Inti solusi terletak pada `LoadOptions.FontSubstitutionWarning`. Dengan mengubahnya menjadi `RaiseTypedWarnings` Anda memberi tahu Aspose.Words untuk memicu peristiwa **setiap kali** tidak dapat menemukan font tepat yang Anda minta.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Step 1: Create a LoadOptions instance that will raise warnings.
        var loadOptions = new LoadOptions
        {
            // This flag makes Aspose.Words emit detailed warnings instead of silently substituting.
            FontSubstitutionWarning = LoadOptions.FontSubstitutionWarningOption.RaiseTypedWarnings
        };
```

> **Mengapa ini penting:**  
> Perilaku default secara diam-diam mengganti font yang hilang dengan yang paling mirip, yang dapat menyebabkan gangguan tata letak yang tidak terduga. Menghasilkan peringatan bertipe memberi Anda visibilitas penuh.

## Langkah 2 – Berlangganan ke Peristiwa Peringatan

Sekarang kita mengaitkan ke `loadOptions.FontSubstitutionWarning`. Lambda menerima objek `e` yang memberi tahu kita secara tepat font mana yang hilang dan font apa yang digunakan sebagai gantinya.

```csharp
        // Step 2: Attach an event handler to capture each substitution.
        loadOptions.FontSubstitutionWarning += (sender, e) =>
        {
            // Log to console – replace with your own logger if needed.
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

> **Tips pro:** Jika Anda menjalankan ini di server web, ganti `Console.WriteLine` dengan logger terstruktur (Serilog, NLog, dll.) sehingga Anda dapat menanyakan data nanti.

## Langkah 3 – Muat Dokumen Menggunakan Opsi yang Dikonfigurasi

Dengan mekanisme peringatan sudah siap, cukup muat dokumen seperti biasanya. Peristiwa ini secara otomatis dipicu untuk setiap font yang hilang.

```csharp
        // Step 3: Load the target document while the warning handler is active.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath, loadOptions);

        // Optional: do something with the document – e.g., save as PDF.
        // doc.Save(@"YOUR_DIRECTORY\output.pdf");
    }
}
```

### Output Konsol yang Diharapkan

Jika `input.docx` merujuk pada font bernama *MyFancyFont* yang tidak terpasang, Anda akan melihat:

```
Missing font: MyFancyFont – substituted with Arial
Missing font: AnotherMissingFont – substituted with Times New Roman
```

Setiap baris sesuai dengan peristiwa **detect missing fonts**, memberikan jejak audit lengkap.

## Langkah 4 – Menangani Kasus Tepi dan Skenario Lanjutan

### 4.1 Ketika Tidak Ada Substitusi

Kadang-kadang dokumen hanya menggunakan font sistem yang sudah ada. Dalam kasus tersebut peristiwa peringatan tidak pernah dipicu, dan Anda akan mendapatkan konsol bersih tanpa output. Itu tanda yang baik—lingkungan Anda sudah memiliki semua font yang diperlukan.

### 4.2 Menangkap Peringatan untuk Analisis Selanjutnya

Jika Anda perlu menyimpan peringatan untuk laporan malam, kumpulkan mereka dalam sebuah daftar:

```csharp
        var missingFonts = new List<(string Original, string Substituted)>();
        loadOptions.FontSubstitutionWarning += (s, e) =>
        {
            missingFonts.Add((e.FontName, e.SubstitutedFontName));
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

Setelah memuat, Anda dapat men-serialize `missingFonts` ke JSON, menulis ke basis data, atau mengirim ringkasan via email.

### 4.3 Bekerja dengan PDF atau Format Lain

Pendekatan `LoadOptions` yang sama bekerja untuk pemanggilan `Load` pada PDF, RTF, dan bahkan file HTML. Cukup berikan instance opsi yang sama, dan Aspose.Words akan menghasilkan peringatan untuk setiap font yang tidak dapat dicocokkan.

## Langkah 5 – Verifikasi Hasil Secara Programatik

Jika Anda lebih suka tes otomatis alih-alih melihat konsol, pastikan bahwa daftar berisi entri yang diharapkan:

```csharp
        // Simple verification (use a testing framework in real projects)
        if (missingFonts.Count == 0)
        {
            Console.WriteLine("All fonts were available – no substitution warnings.");
        }
        else
        {
            Console.WriteLine($"Total missing fonts detected: {missingFonts.Count}");
        }
```

Potongan kode ini menunjukkan **how to capture missing fonts** dalam kode, bukan hanya di log.

## Kesalahan Umum & Cara Menghindarinya

| Kesalahan | Mengapa Terjadi | Solusi |
|-----------|----------------|--------|
| Lupa mengatur `RaiseTypedWarnings` | Defaultnya adalah `DoNotRaise`, sehingga tidak ada peristiwa yang dipicu. | Secara eksplisit atur `FontSubstitutionWarning` seperti yang ditunjukkan pada Langkah 1. |
| Menggunakan `Console.WriteLine` dalam aplikasi web | Output konsol menghilang di IIS/ASP.NET Core. | Beralih ke logger yang persisten (mis., Serilog). |
| Memuat dokumen dengan path relatif | Direktori kerja dapat berbeda saat runtime. | Gunakan path absolut atau `Path.Combine(AppContext.BaseDirectory, "input.docx")`. |
| Mengabaikan `SubstitutedFontName` | Anda kehilangan wawasan tentang fallback mana yang dipilih. | Selalu catat kedua `FontName` dan `SubstitutedFontName`. |

## Bonus: Mengotomatiskan Instalasi Font

Jika Anda mengontrol lingkungan penyebaran, Anda dapat pra‑menginstal font yang hilang menggunakan skrip PowerShell:

```powershell
$fonts = @("MyFancyFont.ttf", "AnotherMissingFont.otf")
foreach ($font in $fonts) {
    $dest = "$env:SystemRoot\Fonts\$font"
    Copy-Item -Path ".\fonts\$font" -Destination $dest -Force
}
```

Menjalankan ini sebelum aplikasi Anda dimulai menghilangkan sebagian besar peringatan **detect missing fonts** secara keseluruhan.

## Kesimpulan

Kami telah membahas semua yang Anda perlukan untuk **log font substitution warnings** saat memuat dokumen Word dengan Aspose.Words. Dengan mengkonfigurasi `LoadOptions`, berlangganan ke peristiwa peringatan, dan opsional menyimpan hasilnya, Anda dapat secara andal **detect missing fonts** dan memahami **how to capture missing fonts** untuk proyek .NET apa pun.

Ambil kode tersebut, sesuaikan logger agar cocok dengan stack Anda, dan Anda tidak akan pernah lagi terkejut oleh pertukaran font yang diam. Langkah selanjutnya mungkin meliputi:

- Mengintegrasikan daftar peringatan dengan pipeline CI/CD Anda untuk gagal membangun ketika font kritis tidak ada.  
- Memperluas pendekatan untuk memantau penggunaan font di seluruh kumpulan dokumen.  
- Mengeksplorasi API `FontSettings` Aspose.Words untuk menyediakan font fallback khusus.

Ada pertanyaan atau skenario rumit? Tinggalkan komentar, dan mari kita selesaikan bersama. Selamat coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}