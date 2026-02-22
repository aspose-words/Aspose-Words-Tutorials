---
category: general
date: 2026-02-21
description: Pelajari cara mengaktifkan peringatan, mendeteksi font yang hilang, dan
  cara memuat docx dengan aman menggunakan Aspose.Words di C#. Ikuti panduan langkah
  demi langkah.
draft: false
keywords:
- how to enable warnings
- detect missing fonts
- how to load docx
- font substitution handling
- Aspose.Words warnings
language: id
og_description: Cara mengaktifkan peringatan, mendeteksi font yang hilang, dan memuat
  file docx dengan benar menggunakan Aspose.Words. Contoh kode lengkap disertakan.
og_title: Cara mengaktifkan peringatan dan mendeteksi font yang hilang saat memuat
  DOCX
tags:
- C#
- Aspose.Words
- Document processing
title: Cara mengaktifkan peringatan dan mendeteksi font yang hilang saat memuat file
  DOCX
url: /id/net/working-with-fonts/how-to-enable-warnings-and-detect-missing-fonts-when-loading/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengaktifkan peringatan dan mendeteksi font yang hilang saat memuat file DOCX

Pernah bertanya-tanya **bagaimana cara mengaktifkan peringatan** untuk font yang hilang sebelum mereka diam-diam merusak rendering dokumen Anda? Anda tidak sendirian—kebanyakan pengembang menganggap perpustakaan akan langsung “melakukan hal yang tepat,” hanya untuk menemukan kemudian bahwa sebuah font telah diganti tanpa petunjuk sama sekali.  

Dalam tutorial ini kami akan menunjukkan secara tepat **bagaimana cara mengaktifkan peringatan**, cara **mendeteksi font yang hilang**, dan cara yang tepat **bagaimana cara memuat docx** menggunakan Aspose.Words untuk .NET. Pada akhir tutorial Anda akan memiliki contoh siap‑jalankan yang mencetak setiap peringatan substitusi font ke konsol, sehingga Anda tidak pernah harus menebak apa yang terjadi di dalam file.

## Prasyarat

- .NET 6.0 atau yang lebih baru (kode ini juga berfungsi pada .NET Framework 4.7+)  
- Visual Studio 2022 atau IDE C# apa pun yang Anda sukai  
- Paket NuGet **Aspose.Words** (`Install-Package Aspose.Words`)  
- File DOCX yang mungkin berisi font yang tidak terpasang di mesin Anda (kami akan menyebutnya `input.docx`)

> **Pro tip:** Jika Anda tidak memiliki file uji, cukup buka dokumen Word yang menggunakan font korporat khusus dan simpan sebagai `input.docx`. Itu akan memicu peringatan yang ingin kami tangkap.

## Gambaran Solusi

1. **Buat** objek `LoadOptions` dengan `FontSubstitutionWarnings` diaktifkan.  
2. **Muat** file DOCX menggunakan opsi tersebut.  
3. **Periksa** koleksi `WarningCallback` untuk entri `FontSubstitution` apa pun.  
4. **Reaksi** – Anda dapat mencatat, menampilkan, atau bahkan mengganti font yang hilang secara programatik.

Di bawah ini kami memecah setiap langkah, menjelaskan *mengapa* itu penting, dan memberi Anda potongan kode lengkap yang dapat dijalankan.

---

## Langkah 1: Instal Aspose.Words dan siapkan proyek

Sebelum kita dapat **bagaimana cara mengaktifkan peringatan**, kita memerlukan perpustakaan yang benar‑benar mendukungnya.

```bash
# Using the .NET CLI
dotnet add package Aspose.Words
```

Atau, di Konsol Package Manager Visual Studio:

```powershell
Install-Package Aspose.Words
```

> **Mengapa langkah ini?**  
> Tanpa paket tersebut, `LoadOptions`, `Document`, dan infrastruktur peringatan tidak ada. Menambahkan referensi NuGet memastikan Anda mengambil versi stabil terbaru (pada penulisan ini, 24.5).

---

## Langkah 2: Buat opsi pemuatan yang mengaktifkan peringatan substitusi font

Inti dari **bagaimana cara mengaktifkan peringatan** berada di kelas `LoadOptions`. Mengatur `FontSubstitutionWarnings` menjadi `true` memberi tahu mesin untuk mencatat setiap kali harus mengganti font yang hilang.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Step 2: Build the options object
LoadOptions loadOptions = new LoadOptions
{
    // This flag makes the library emit warnings for any font it cannot find.
    FontSubstitutionWarnings = true
};
```

> **Mengapa mengaktifkan flag ini?**  
> Secara default Aspose.Words secara diam‑diam menukar font yang hilang dengan fallback (biasanya Arial). Hal ini dapat menyebabkan pergeseran tata letak, karakter tak terlihat, atau pelanggaran merek. Mengaktifkan flag memberikan Anda visibilitas penuh.

---

## Langkah 3: Muat file DOCX menggunakan opsi yang dikonfigurasi

Sekarang kami tahu **bagaimana cara memuat docx** dengan peringatan diaktifkan, kami benar‑benar melakukan pemuatan.

```csharp
// Step 3: Load the document – replace the path with your own file location.
string docPath = @"YOUR_DIRECTORY\input.docx";
Document document = new Document(docPath, loadOptions);
```

> **Apa yang terjadi di balik layar?**  
> Saat mem‑parsing DOCX, Aspose.Words memeriksa setiap elemen `<w:rFonts>`. Jika font yang ditentukan tidak terpasang, ia mencatat peringatan `FontSubstitution` dan beralih ke font default. Karena kami mengaktifkan peringatan, entri‑entri tersebut masuk ke `document.WarningCallback.Warnings`.

---

## Langkah 4: Ambil dan tampilkan peringatan substitusi font

Properti `WarningCallback` menyimpan `WarningInfoCollection`. Lakukan perulangan, filter untuk `WarningType.FontSubstitution`, dan keluarkan pesannya.

```csharp
// Step 4: Iterate over warnings and print font‑substitution details.
foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substituted: {warning.Message}");
    }
}
```

**Output yang diharapkan** (contoh):

```
⚠️ Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
⚠️ Font substituted: Font 'CorporateLogo' was not found. Substituted with 'Times New Roman'.
```

> **Apa yang harus dilakukan dengan pesan ini?**  
> Anda dapat mencatatnya ke file, menampilkannya di UI, atau bahkan memicu rutinitas fallback font khusus. Kuncinya adalah Anda kini *mendeteksi font yang hilang* alih‑alih menebak nanti.

---

## Langkah 5: (Opsional) Ganti font yang hilang dengan fallback khusus

Jika Anda memiliki font korporat yang ingin ditegakkan, Anda dapat menangani peringatan dan menggantinya secara langsung.

```csharp
// Optional: Custom fallback font
string fallbackFont = "Calibri";

foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        // Extract the missing font name from the warning message
        string missingFont = warning.Message.Split('\'')[1];
        Console.WriteLine($"Replacing missing font '{missingFont}' with '{fallbackFont}'");
        document.FontInfos[missingFont].SubstitutedFont = fallbackFont;
    }
}
```

> **Mengapa mempertimbangkan ini?**  
> Ini menjamin konsistensi visual di semua dokumen yang dihasilkan, yang penting untuk kepatuhan merek.

---

## Contoh lengkap yang dapat dijalankan

Di bawah ini adalah satu file C# yang dapat Anda salin‑tempel ke aplikasi konsol. Ini mencakup semuanya—dari menginstal paket hingga mencetak peringatan.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with warnings enabled
            LoadOptions loadOptions = new LoadOptions
            {
                FontSubstitutionWarnings = true
            };

            // 2️⃣ Load the DOCX (adjust the path as needed)
            string docPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Show all font‑substitution warnings
            Console.WriteLine("=== Font Substitution Warnings ===");
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Message}");
                }
            }

            // 4️⃣ (Optional) Replace missing fonts with Calibri
            string fallback = "Calibri";
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    string missingFont = warning.Message.Split('\'')[1];
                    Console.WriteLine($"Replacing '{missingFont}' with '{fallback}'");
                    doc.FontInfos[missingFont].SubstitutedFont = fallback;
                }
            }

            // 5️⃣ Save the corrected document (optional)
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Jalankan**: `dotnet run` dari folder proyek. Jika ada font yang hilang, Anda akan melihat peringatan tercetak, dan penggantian opsional akan diterapkan sebelum file disimpan.

---

## Pertanyaan yang sering diajukan

### Apakah ini juga bekerja dengan konversi PDF?

Ya. Setelah Anda menangani peringatan, Anda dapat memanggil `doc.Save("output.pdf")` dan font yang diganti akan muncul di PDF seperti pada DOCX.

### Bagaimana jika saya perlu menekan peringatan untuk font tertentu?

Anda dapat menyaringnya dalam perulangan—cukup lewati `WarningInfo` yang `Message`‑nya berisi nama font yang ingin diabaikan.

### Apakah `FontSubstitutionWarnings` tersedia di versi Aspose.Words yang lebih lama?

Fitur ini diperkenalkan pada versi 20.5. Jika Anda terjebak pada rilis yang lebih lama, tingkatkan melalui NuGet; perubahan API bersifat kompatibel mundur.

---

## Kesimpulan

Kami telah membahas **bagaimana cara mengaktifkan peringatan**, menunjukkan **mendeteksi font yang hilang**, dan mendemonstrasikan cara yang tepat **bagaimana cara memuat docx** dengan Aspose.Words sambil mempertahankan visibilitas penuh pada substitusi font. Dengan memeriksa `document.WarningCallback.Warnings` Anda mendapatkan jejak audit yang dapat diandalkan—tidak ada lagi fallback diam‑diam.

Langkah selanjutnya? Coba hubungkan logika peringatan ke kerangka kerja logging seperti Serilog, atau bangun UI yang menyoroti font yang hilang sebelum Anda mengirimkan dokumen ke pengguna. Anda juga dapat menjelajahi kelas `FontSettings` untuk kontrol yang lebih detail atas kebijakan substitusi font.

Selamat coding, dan semoga dokumen Anda selalu dirender persis seperti yang Anda inginkan! 

![Diagram yang menggambarkan alur dari memuat file DOCX hingga menangkap peringatan substitusi font – cara mengaktifkan peringatan di Aspose.Words](/images/font-warning-flow.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}