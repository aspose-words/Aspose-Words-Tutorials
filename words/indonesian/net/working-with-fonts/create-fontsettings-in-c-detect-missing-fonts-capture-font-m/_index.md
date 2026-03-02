---
category: general
date: 2026-03-01
description: Buat FontSettings di C# untuk mendeteksi font yang hilang, menangkap
  pesan font, dan menangani font yang hilang dengan Aspose.Words. Panduan langkah
  demi langkah untuk pengembang.
draft: false
keywords:
- create fontsettings
- detect missing fonts
- capture font messages
- handle missing fonts
- Aspose.Words font handling
- C# document processing
language: id
og_description: Buat FontSettings di C# untuk mendeteksi font yang hilang, menangkap
  pesan font, dan menangani font yang tidak tersedia menggunakan Aspose.Words. Tutorial
  lengkap dengan kode.
og_title: Buat FontSettings di C# – Deteksi Font yang Hilang & Tangkap Pesan Font
tags:
- Aspose.Words
- C#
- Font Management
title: Buat FontSettings di C# – Deteksi Font yang Hilang dan Tangkap Pesan Font
url: /id/net/working-with-fonts/create-fontsettings-in-c-detect-missing-fonts-capture-font-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat FontSettings di C# – Deteksi Font yang Hilang & Tangkap Pesan Font

Pernahkah Anda perlu **create FontSettings** dalam proyek .NET tetapi tidak yakin cara menemukan font yang tidak terpasang di mesin target? Anda tidak sendirian. Dalam banyak aplikasi dunia nyata—seperti generator laporan otomatis atau konverter dokumen—font yang hilang dapat secara diam‑diam merusak tata letak, dan Anda tidak akan menyadarinya sampai PDF terlihat aneh.  

Bagaimana jika Anda bisa **detect missing fonts**, **capture font messages**, dan **handle missing fonts** sebelum mereka merusak output Anda? Kabar baiknya, Aspose.Words membuat ini sangat mudah. Dalam tutorial ini kami akan menelusuri seluruh proses, mulai dari menyiapkan objek `FontSettings` hingga menghubungkan callback peringatan yang memberi tahu Anda tepat glyph mana yang diganti.

> **TL;DR:** Pada akhir tutorial Anda akan memiliki aplikasi konsol C# yang siap dijalankan dan mencatat setiap substitusi font, sehingga Anda dapat memutuskan apakah akan menyematkan pengganti atau memberi peringatan kepada pengguna.

---

## Prasyarat

- .NET 6 SDK (atau versi .NET terbaru)  
- Visual Studio 2022 atau VS Code dengan ekstensi C#  
- Lisensi Aspose.Words untuk .NET (versi trial gratis cukup untuk demo ini)  
- Sebuah file DOCX contoh yang merujuk pada font yang tidak Anda miliki (misalnya *Comic Sans MS* pada mesin Linux)  

Tidak ada paket NuGet khusus selain `Aspose.Words` yang diperlukan.

---

## Langkah 1 – Instal Aspose.Words dan Siapkan Proyek

Langkah pertama, buat proyek konsol baru dan tambahkan pustaka Aspose.Words ke dalamnya.

```bash
dotnet new console -n FontSettingsDemo
cd FontSettingsDemo
dotnet add package Aspose.Words
```

> **Pro tip:** Jika Anda sudah memiliki solusi, cukup tambahkan paket melalui UI NuGet Package Manager—memudahkan pelacakan versi.

---

## Langkah 2 – Buat FontSettings (Kata Kunci Utama Muncul Di Sini)

Langkah **create FontSettings** adalah fondasi dari setiap alur kerja yang berhubungan dengan font. `FontSettings` memberi tahu Aspose.Words di mana mencari font, apakah menggunakan folder sistem, dan bagaimana fallback ketika sesuatu tidak ditemukan.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a FontSettings object – this is where we’ll configure search paths.
FontSettings fontSettings = new FontSettings();

// Optional: add a custom folder that contains fallback fonts.
fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

Mengapa ini penting? Tanpa `FontSettings` yang dikonfigurasi dengan benar, mesin secara diam‑diam menggantikan glyph yang hilang dengan font sistem default, dan Anda tidak akan pernah melihat peringatan.

---

## Langkah 3 – Hubungkan LoadOptions dengan FontSettings

`LoadOptions` memungkinkan Anda menyuntikkan `FontSettings` ke dalam pemuat dokumen. Ini adalah jembatan yang membuat mesin **detect missing fonts** selama fase konstruksi `Document`.

```csharp
// 2️⃣ Configure LoadOptions to use the FontSettings we just created.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

Sekarang setiap kali Anda memuat DOCX dengan `loadOptions`, Aspose.Words akan merujuk ke `FontSettings` yang telah kami siapkan sebelumnya.

---

## Langkah 4 – Lampirkan Callback Peringatan untuk **Capture Font Messages**

Aspose.Words mengeluarkan peringatan untuk berbagai kondisi—substitusi font adalah yang paling umum. Dengan menyediakan implementasi `IWarningCallback`, Anda dapat **capture font messages** secara real‑time.

```csharp
// 3️⃣ Attach a warning handler that will print font‑substitution warnings.
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

### Kelas Penangan Peringatan

```csharp
/// <summary>
/// Handles font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Source == WarningSource.FontSubstitution)
        {
            Console.WriteLine($"[FontSubstitution] {info.Description}");
        }
    }
}
```

Field `info.Description` berisi pesan yang dapat dibaca manusia seperti *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”* Inilah jenis output yang Anda perlukan untuk **handle missing fonts** secara elegan.

---

## Langkah 5 – Muat Dokumen dan Biarkan Callback Bekerja

Dengan semua komponen terhubung, memuat dokumen menjadi sangat sederhana. Jika file sumber merujuk pada font yang tidak ada di sistem, handler peringatan kami akan dipicu.

```csharp
// 4️⃣ Load a document that may contain unknown fonts.
Document doc = new Document(@"C:\Docs\UnknownFont.docx", loadOptions);

// Optional: you can now save the document to PDF or any other format.
doc.Save(@"C:\Docs\Result.pdf");
```

Saat Anda menjalankan program, Anda akan melihat output konsol serupa dengan:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
[FontSubstitution] Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Output tersebut merupakan bagian **capture font messages** dari alur kerja kami. Anda dapat memperluas handler untuk mencatat ke file, mengirim telemetry, atau bahkan menghentikan konversi jika font kritis tidak tersedia.

---

## Langkah 6 – Contoh Lengkap yang Siap Pakai (Semua Bagian Bersatu)

Berikut adalah program lengkap yang siap disalin‑tempel. Tempelkan ke dalam `Program.cs`, sesuaikan jalur file, lalu jalankan `dotnet run`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 1: Create FontSettings -----
            FontSettings fontSettings = new FontSettings();
            // Add any custom folder with fallback fonts (optional)
            fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);

            // ----- Step 2: Configure LoadOptions -----
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontSubstitutionWarningHandler()
            };

            // ----- Step 3: Load the document -----
            string inputPath = @"C:\Docs\UnknownFont.docx";
            Document doc = new Document(inputPath, loadOptions);

            // ----- Step 4: Save the result (optional) -----
            string outputPath = @"C:\Docs\Result.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any font substitution warnings.");
        }
    }

    // ----- Warning handler that captures font messages -----
    class FontSubstitutionWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Source == WarningSource.FontSubstitution)
            {
                Console.WriteLine($"[FontSubstitution] {info.Description}");
            }
        }
    }
}
```

### Output yang Diharapkan

Menjalankan program pada mesin yang tidak memiliki *Comic Sans MS* akan mencetak sesuatu seperti:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document processed. Check console for any font substitution warnings.
```

Anda juga akan mendapatkan `Result.pdf` yang menggunakan font substitusi, memastikan konversi tidak pernah gagal.

---

## Pertanyaan Umum & Kasus Pojok

| Pertanyaan | Jawaban |
|------------|---------|
| **Bagaimana jika saya ingin konversi gagal alih-alih melakukan substitusi?** | Di dalam `FontSubstitutionWarningHandler`, lemparkan exception ketika `info.Description` berisi nama font kritis. |
| **Bisakah saya menyematkan font pengganti secara otomatis?** | Ya. Setelah mendeteksi font yang hilang, Anda dapat memuat `FontInfo` fallback dari jalur yang diketahui dan menambahkannya ke `fontSettings` melalui `fontSettings.SetFontsFolder`. |
| **Apakah ini bekerja di Linux/macOS?** | Tentu saja. `FontSettings` bersifat lintas‑platform; pastikan folder fallback berisi file `.ttf` atau `.otf` yang sesuai. |
| **Apakah callback peringatan thread‑safe?** | Callback dijalankan pada thread yang sama dengan proses pemuatan dokumen, jadi Anda tidak memerlukan sinkronisasi tambahan untuk logging ke konsol. Untuk skenario multi‑thread, lindungi sumber daya bersama. |
| **Bagaimana cara mencatat peringatan ke file?** | Ganti `Console.WriteLine` dengan `File.AppendAllText("font_warnings.log", ...)` atau gunakan kerangka kerja logging apa pun (Serilog, NLog). |

---

## Tips Pro untuk Penanganan Font yang Siap Produksi

1. **Cache Pencarian Font** – Menggunakan kembali instance `FontSettings` yang sama pada beberapa pemuatan dokumen menghindari pemindaian filesystem berulang.  
2. **Whitelist Font Kritikal** – Jika merek Anda memerlukan font tertentu, verifikasi kehadirannya di awal dan hentikan proses dengan pesan error yang jelas.  
3. **Gunakan `SetFontFolder` Secara Rekursif** – Menetapkan `recursive: true` memastikan subfolder dipindai, berguna saat Anda mengirimkan seluruh koleksi font.  
4. **Kombinasikan dengan `FontSubstitutionSettings`** – Anda dapat menyesuaikan aturan substitusi (misalnya, memprioritaskan font dengan nama keluarga yang sama).  

---

## Kesimpulan

Kami baru saja **membuat FontSettings**, mengonfigurasi `LoadOptions` untuk **detect missing fonts**, melampirkan callback yang **captures font messages**, dan mendemonstrasikan cara **handle missing fonts** secara bersih dan siap produksi. Seluruh alur ini dapat ditulis dalam beberapa puluh baris C#, namun memberikan visibilitas penuh terhadap lanskap font pada setiap DOCX yang Anda proses.

Selanjutnya, Anda dapat menjelajahi:

- **Menyematkan font fallback** langsung ke PDF output (`PdfSaveOptions.FontEmbeddingMode`).  
- **Mensubstitusi font secara programatis** berdasarkan aturan branding perusahaan.  
- **Integrasi dengan pipeline CI** untuk secara otomatis menandai dokumen yang menggunakan font tidak sah.

Cobalah, sesuaikan handler peringatan sesuai kebutuhan Anda, dan biarkan pipeline dokumen Anda berjalan dengan percaya diri—tidak ada lagi gangguan tata letak misterius akibat pertukaran font yang tak terlihat.

Selamat coding! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}