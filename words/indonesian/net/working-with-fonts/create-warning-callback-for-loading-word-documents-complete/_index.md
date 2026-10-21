---
category: general
date: 2026-03-25
description: Buat callback peringatan untuk memuat dokumen Word dan mendeteksi font
  yang hilang. Pelajari cara mengonfigurasi pengaturan font di Aspose.Words untuk
  .NET.
draft: false
keywords:
- create warning callback
- load word document
- detect missing fonts
- configure font settings
language: id
og_description: Buat callback peringatan untuk memuat dokumen Word sambil mendeteksi
  font yang hilang. Panduan ini menunjukkan cara mengonfigurasi pengaturan font di
  Aspose.Words.
og_title: Buat callback peringatan – Muat dokumen Word & deteksi font yang hilang
tags:
- Aspose.Words
- C#
- Font handling
title: Buat callback peringatan untuk memuat dokumen Word – Panduan Lengkap
url: /id/net/working-with-fonts/create-warning-callback-for-loading-word-documents-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat callback peringatan – Muat dokumen Word & deteksi font yang hilang

Pernah perlu **membuat callback peringatan** saat memuat dokumen Word dan bertanya-tanya mengapa beberapa font tiba‑tiba menghilang? Anda bukan satu‑satunya. Di banyak aplikasi perusahaan, font yang hilang menyebabkan bencana tata letak, dan tanpa callback yang tepat Anda mungkin tidak pernah menyadari masalah tersebut.  

Berita baik? Dengan Aspose.Words for .NET Anda dapat **memuat dokumen Word**, **mendeteksi font yang hilang**, dan **mengonfigurasi pengaturan font** semuanya dalam beberapa baris kode yang rapi. Dalam tutorial ini kami akan membahas contoh lengkap yang dapat dijalankan, menjelaskan mengapa setiap bagian penting, dan menunjukkan cara memverifikasi bahwa callback peringatan bekerja dengan baik.

> **Apa yang akan Anda dapatkan**  
> * Program C# lengkap yang memuat DOCX, melaporkan setiap substitusi font, dan memungkinkan Anda menyesuaikan jalur pencarian font.  
> * Pemahaman tentang kelas `FontSettings`, `LoadOptions`, dan `IWarningCallback`.  
> * Tips untuk menangani kasus‑tepi seperti font tersemat atau folder font sistem‑luas.

---

## Prasyarat

- .NET 6+ (atau .NET Framework 4.7.2+) dengan kompiler C#.  
- Paket NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- File Word contoh (`input.docx`) yang menggunakan setidaknya satu font yang tidak terpasang di mesin (misalnya *Calibri Light* pada kontainer Windows minimal).  
- Familiaritas dasar dengan aplikasi konsol C#.

Tidak ada pustaka tambahan yang diperlukan; semuanya berada di dalam Aspose.Words.

---

## Langkah 1: Buat callback peringatan untuk mendeteksi font yang hilang

Bagian **utama** dari teka‑teki ini adalah kelas yang mengimplementasikan `IWarningCallback`. Aspose.Words akan memanggil callback ini setiap kali menemukan situasi yang memerlukan peringatan – substitusi font adalah yang paling umum.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

/// <summary>
/// Handles warning events raised by Aspose.Words during document loading.
/// Specifically looks for FontSubstitution warnings and writes them to the console.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Mengapa ini penting** – Tanpa callback Anda harus menyaring log setelahnya. Dengan menangani peringatan secara real‑time Anda dapat memutuskan apakah akan menghentikan pemuatan, mengganti font yang hilang dengan fallback, atau cukup mencatat masalah untuk ditinjau nanti.

---

## Langkah 2: Konfigurasikan FontSettings untuk penanganan font khusus

Sebelum kita benar‑benarnya memuat dokumen, kita mungkin ingin memberi tahu Aspose.Words di mana mencari font yang tidak ada di sistem. Di sinilah `FontSettings` berperan.

```csharp
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder (e.g., a shared network location) where your application stores its fonts.
fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);

// Optional: If you have a specific font to use as a universal fallback, set it here.
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

**Mengapa ini penting** – Dengan mengarahkan Aspose.Words ke folder yang berisi font yang hilang, Anda seringkali dapat menghindari substitusi sepenuhnya. Jika itu tidak memungkinkan, default yang masuk akal (seperti *Arial*) menjaga dokumen tetap dapat dibaca.

---

## Langkah 3: Muat dokumen Word dengan callback peringatan yang telah dikonfigurasi

Sekarang kita menggabungkan semuanya: kita membuat `LoadOptions`, menyambungkan `FontSettings` dan `FontWarningHandler` kita, dan akhirnya memuat dokumen.

```csharp
// Prepare LoadOptions with both FontSettings and our warning handler.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontWarningHandler()
};

// Load the Word document. Replace the path with your actual file location.
Document document = new Document(@"C:\Docs\input.docx", loadOptions);

// At this point the warning handler has already printed any font‑substitution messages.
Console.WriteLine("✅ Document loaded successfully.");
```

**Mengapa ini penting** – `LoadOptions` adalah satu‑satunya tempat Anda mengonfigurasi *bagaimana* dokumen dibaca. Dengan menyediakan baik konfigurasi font maupun callback peringatan, kami memastikan bahwa setiap font yang hilang dicari di tempat yang tepat **dan** dilaporkan segera.

---

## Langkah 4: Verifikasi output – apa yang harus Anda lihat?

Jalankan program dari konsol. Jika `input.docx` menggunakan font yang tidak terpasang dan juga tidak ada di `C:\SharedFonts`, Anda akan melihat sesuatu seperti:

```
⚠️ Font substitution detected: Font 'Roboto' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
```

Jika semua font tersedia, baris peringatan tidak akan muncul sama sekali. Loop umpan balik langsung ini sangat berharga selama pipeline pemrosesan dokumen otomatis di mana pertukaran font secara diam‑diam dapat melanggar pedoman merek.

---

## Langkah 5: Kesalahan umum dan tips praktik terbaik

| Jebakan | Cara menghindarinya |
|---------|---------------------|
| **Lupa merujuk `Aspose.Words.Fonts`** | Pastikan Anda memiliki `using Aspose.Words.Fonts;` di bagian atas; jika tidak, kompiler akan mengeluh tentang tipe yang hilang. |
| **Jalur folder font salah** | Periksa kembali jalurnya dan setel `recursive: true` jika Anda memiliki sub‑folder. Gunakan `Path.GetFullPath` untuk debug. |
| **Beberapa callback peringatan** | Aspose.Words hanya menghormati `WarningCallback` terakhir yang Anda tetapkan. Pertahankan satu handler yang mendelagasikan jika Anda memerlukan logika yang lebih kompleks. |
| **Menjalankan di server tanpa UI** | Penulisan ke konsol baik‑baik saja, tetapi untuk aplikasi web Anda mungkin ingin mencatat ke file atau sistem pemantauan alih‑alih `Console.WriteLine`. |
| **Dokumen besar menyebabkan penurunan performa** | Gunakan kembali satu instance `FontSettings` di beberapa pemuatan; membuatnya berulang‑ulang dapat menjadi mahal. |

**Tip pro:** Jika Anda perlu *mengumpulkan* peringatan untuk analisis nanti, simpan mereka dalam `List<string>` di dalam handler alih‑alih mencetak langsung.

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Anda kemudian dapat memeriksa `handler.Messages` setelah dokumen dimuat.

---

## Langkah 6: Memperluas solusi – bagaimana jika saya perlu menyematkan font fallback?

Terkadang Anda ingin font yang hilang *disematkan* dalam PDF output sehingga penampil di hilir melihat tampilan yang tepat. Setelah memuat dokumen, Anda dapat memaksa penyematan:

```csharp
// Ensure the fallback font is embedded when saving to PDF.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    EmbedStandardPdfFonts = false,
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};

document.Save(@"C:\Docs\output.pdf", pdfOptions);
Console.WriteLine("✅ PDF saved with embedded fonts.");
```

Potongan kode ini menunjukkan bagaimana pendekatan **mengonfigurasi pengaturan font** yang sama dapat diperluas selain sekadar memuat.

---

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke proyek Console App baru. Program ini mencakup semua bagian yang dibahas di atas.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    // Step 1 – Warning handler
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2 – Configure FontSettings
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);
            fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";

            // Step 3 – LoadOptions with warning callback
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontWarningHandler()
            };

            // Step 4 – Load the document
            string docPath = @"C:\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");

            // Optional: Save as PDF with embedded fonts
            var pdfOptions = new PdfSaveOptions
            {
                EmbedStandardPdfFonts = false,
                FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
            };
            doc.Save(@"C:\Docs\output.pdf", pdfOptions);
            Console.WriteLine("✅ PDF saved with embedded fonts.");
        }
    }
}
```

**Output yang diharapkan** (ketika ada font yang hilang):

```
⚠️ Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
✅ PDF saved with embedded fonts.
```

Jika tidak ada substitusi, hanya pesan keberhasilan yang muncul.

---

## Kesimpulan

Kami baru saja **membuat callback peringatan** yang secara andal **mendeteksi font yang hilang** saat **memuat dokumen Word** dengan Aspose.Words, dan kami menunjukkan cara **mengonfigurasi pengaturan font** untuk mengontrol di mana perpustakaan mencari font dan fallback mana yang digunakan. Dengan menghubungkan `FontSettings` dan `LoadOptions` bersama, Anda memperoleh visibilitas penuh terhadap masalah terkait font—tidak ada lagi gangguan tata letak yang diam.

Langkah selanjutnya? Coba ganti `FontWarningHandler` dengan logger yang menulis ke basis data, atau bereksperimen dengan **aturan substitusi font** untuk memetakan font yang hilang tertentu ke alternatif yang disetujui merek. Anda juga dapat menjelajahi **pemuat font dinamis** dari penyimpanan cloud jika aplikasi Anda berjalan di lingkungan terkontainer.

Ada pertanyaan tentang kasus tepi tertentu—seperti menangani fitur OpenType atau berurusan dengan file DOCX terenkripsi? Tinggalkan komentar di bawah, dan selamat coding!  

![Diagram buat callback peringatan](https://example.com/images/create-warning-callback.png "Diagram buat callback peringatan")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}