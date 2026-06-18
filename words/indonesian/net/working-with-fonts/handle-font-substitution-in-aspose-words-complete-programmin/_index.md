---
category: general
date: 2026-06-17
description: Tangani substitusi font di Aspose.Words dan deteksi font yang hilang
  dengan cepat melalui tutorial langkah demi langkah ini untuk pengembang .NET.
draft: false
keywords:
- handle font substitution
- detect missing fonts
- how to detect missing fonts
language: id
og_description: Tangani substitusi font di Aspose.Words dan pelajari cara mendeteksi
  font yang hilang dalam dokumen Anda dengan contoh kode yang jelas.
og_title: Menangani Substitusi Font di Aspose.Words – Panduan Lengkap
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  headline: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  name: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  steps:
  - name: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
    text: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
  - name: Run the console app or API endpoint.
    text: Run the console app or API endpoint.
  - name: Verify that the console (or HTTP response) lists the substitution warning.
    text: Verify that the console (or HTTP response) lists the substitution warning.
  - name: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
    text: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: Menangani Substitusi Font di Aspose.Words – Panduan Pemrograman Lengkap
url: /id/net/working-with-fonts/handle-font-substitution-in-aspose-words-complete-programmin/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menangani Substitusi Font di Aspose.Words – Panduan Pemrograman Lengkap

Pernah bertanya-tanya bagaimana cara **menangani substitusi font** ketika dokumen Word merujuk ke font yang tidak terpasang di server? Anda tidak sendirian. Dalam banyak aplikasi dunia nyata—seperti generator faktur atau layanan laporan otomatis—font yang hilang menyebabkan fallback diam‑diam yang merusak tata letak.  

Kabar baiknya, Aspose.Words menyediakan sistem peringatan bawaan yang memungkinkan Anda **mendeteksi font yang hilang** dan merespons sesuai keinginan. Dalam tutorial ini kami akan menunjukkan cara mendaftarkan penangan peringatan, memuat dokumen, dan mengambil peristiwa substitusi font yang tepat. Pada akhir tutorial Anda juga akan melihat cara menjawab pertanyaan klasik “**bagaimana cara mendeteksi font yang hilang**?” dengan kode bersih yang siap produksi.

## Apa yang Dibahas dalam Tutorial Ini

* Menyiapkan Aspose.Words agar memicu peringatan untuk setiap substitusi font.  
* Menangkap peringatan tersebut dalam penangan kustom sehingga Anda dapat mencatat, mengganti, atau menghentikan proses.  
* Menggunakan data yang ditangkap untuk **mendeteksi font yang hilang** sebelum dokumen disimpan atau dirender.  
* Tips memecahkan masalah kasus tepi—seperti ketika font fallback dipilih secara diam‑diam.  
* Contoh lengkap yang dapat dijalankan dan langsung dimasukkan ke aplikasi konsol .NET apa pun.

> **Prasyarat** – Anda memerlukan .NET SDK terbaru (6.0+ sudah cukup), lisensi Aspose.Words for .NET yang valid (atau kunci evaluasi sementara), serta contoh DOCX yang secara sengaja merujuk ke font yang tidak Anda miliki. Tidak ada pustaka pihak ketiga lain yang diperlukan.

---

## ## Menangani Substitusi Font dengan Penangan Peringatan Kustom

Aspose.Words menghasilkan objek `WarningInfo` setiap kali tidak dapat menemukan font yang diminta. Secara default peringatan tersebut diabaikan, itulah mengapa Anda sering tidak menyadari adanya substitusi. Untuk **menangani substitusi font**, Anda mengganti penangan peringatan default dengan yang benar‑benar melakukan sesuatu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Register a custom warning handler that prints font‑substitution events.
        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (sender, args) =>
            {
                // We're only interested in font‑substitution warnings.
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substituted: {args.Description}");
                }
            });

        // Load a document that deliberately references an unavailable font.
        Document doc = new Document("Samples/MissingFont.docx");

        // Force a save to trigger any pending warnings (e.g., PDF conversion).
        doc.Save("Output/Result.pdf");
    }
}
```

### Mengapa Ini Berfungsi

* `FontSettings.DefaultWarningHandler` adalah properti statis global—setelah Anda mengaturnya, **setiap** operasi Aspose.Words dalam AppDomain saat ini akan menggunakan delegasi Anda.  
* `WarningInfoCollectionHandler` menerima objek `WarningInfo` yang berisi `WarningType` dan `Description` yang dapat dibaca manusia. Menyaring pada `WarningType.FontSubstitution` memastikan Anda hanya melihat peristiwa yang relevan.  
* Memanggil `doc.Save` memaksa pustaka menyelesaikan semua font, pada saat itulah peringatan dipicu. Jika Anda hanya perlu memeriksa dokumen tanpa menyimpan, Anda dapat memanggil `doc.UpdatePageLayout()` sebagai gantinya.

**Output konsol yang diharapkan** (misalkan font yang hilang adalah “Papyrus”):

```
⚠️ Font substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
```

Baris itu adalah bukti bahwa pustaka **mendeteksi font yang hilang** dan memilih fallback.

---

## ## Mendeteksi Font yang Hilang Sebelum Rendering

Kadang‑kadang Anda ingin menghentikan proses sepenuhnya jika font yang diperlukan tidak ada—mungkin karena pedoman merek menuntut tipografi yang tepat. Penangan peringatan dapat diperluas untuk mengumpulkan semua pesan font‑hilang ke dalam daftar, kemudian Anda dapat membuat keputusan.

```csharp
using System.Collections.Generic;

// ...

static List<string> missingFonts = new List<string>();

static void Main()
{
    FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
        (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                // Store the description for later analysis.
                missingFonts.Add(args.Description);
                Console.WriteLine($"⚠️ Font substituted: {args.Description}");
            }
        });

    Document doc = new Document("Samples/MissingFont.docx");
    doc.UpdatePageLayout();   // Triggers warnings without saving.

    if (missingFonts.Count > 0)
    {
        Console.WriteLine("\n❗ Detected missing fonts:");
        foreach (var msg in missingFonts)
            Console.WriteLine($" - {msg}");

        // Optionally abort the operation.
        // throw new InvalidOperationException("Missing required fonts.");
    }
    else
    {
        Console.WriteLine("\n✅ No font substitution detected.");
    }

    // Continue with saving or further processing if you wish.
    doc.Save("Output/Result.pdf");
}
```

### Bagaimana Ini Menjawab “bagaimana cara mendeteksi font yang hilang”

* Daftar `missingFonts` berfungsi sebagai catatan setiap peristiwa substitusi.  
* Setelah `UpdatePageLayout`, Anda dapat memeriksa daftar tersebut dan memutuskan apakah akan melanjutkan, mencatat, atau melempar pengecualian.  
* Pola ini bekerja untuk format output apa pun (PDF, HTML, gambar) karena sistem peringatan bersifat format‑agnostik.

---

## ## Tips Lanjutan: Ganti Font yang Hilang dengan Substitusi Khusus

Jika Anda memiliki font korporat yang harus digunakan, Anda dapat memberi tahu Aspose.Words untuk mengganti setiap font yang hilang dengan fallback Anda secara otomatis. Ini berguna ketika Anda ingin dokumen *tetap* terlihat dapat diterima tanpa pemrosesan manual.

```csharp
// Configure a fallback font collection.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", new string[] { "Calibri", "Arial" });

FontSettings.DefaultFontSettings = fontSettings;
```

Letakkan potongan kode di atas **sebelum** memuat dokumen. Sekarang setiap font yang hilang—tidak peduli nama aslinya—akan diganti dengan “Calibri” (atau “Arial” jika Calibri tidak ada). Anda tetap akan menerima peringatan, tetapi dokumen akan dirender dengan font yang Anda kontrol.

---

## ## Kesalahan Umum & Cara Menghindarinya

| Kesalahan | Mengapa Terjadi | Solusi |
|-----------|----------------|--------|
| **Peringatan menghilang setelah pemanggilan pertama** | Properti statis `DefaultWarningHandler` ditimpa kemudian dalam aplikasi. | Atur penangan **sekali** saat aplikasi mulai, atau simpan referensi dan tetapkan kembali jika Anda mengubahnya. |
| **Hanya font yang hilang pertama yang dilaporkan** | Beberapa API mengumpulkan peringatan; Anda perlu memanggil `UpdatePageLayout` atau `Save` untuk mengosongkan antrean. | Paksa pembaruan tata letak atau simpan dalam format yang akan Anda hasilkan. |
| **Substitusi tetap terjadi meskipun sudah menghentikan** | Penangan peringatan dijalankan *setelah* substitusi sudah terjadi. | Gunakan penangan untuk **mencatat** lalu lempar pengecualian untuk menghentikan pemrosesan lebih lanjut. |
| **Font yang hilang pada kontainer Linux** | Linux sering tidak memiliki katalog font Windows, sehingga banyak substitusi terjadi. | Pasang font yang diperlukan ke dalam kontainer atau gunakan `FontSettings.SetFontsFolder` untuk menunjuk ke direktori font khusus. |

---

## ## Mendeteksi Substitusi Font dalam Skenario Web API

Jika Anda menyajikan dokumen melalui ASP.NET Core, Anda mungkin tidak ingin menulis ke konsol. Sebagai gantinya, kumpulkan peringatan dan kembalikan sebagai bagian dari respons HTTP.

```csharp
[ApiController]
[Route("api/[controller]")]
public class DocumentController : ControllerBase
{
    [HttpPost("convert")]
    public IActionResult Convert(IFormFile file)
    {
        var missingFonts = new List<string>();

        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (s, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                    missingFonts.Add(e.Description);
            });

        using var stream = file.OpenReadStream();
        var doc = new Document(stream);
        doc.UpdatePageLayout();

        if (missingFonts.Any())
        {
            return BadRequest(new { message = "Missing fonts detected", details = missingFonts });
        }

        // Convert to PDF and stream back.
        var pdfStream = new MemoryStream();
        doc.Save(pdfStream, SaveFormat.Pdf);
        pdfStream.Position = 0;
        return File(pdfStream, "application/pdf", "result.pdf");
    }
}
```

Sekarang API **mendeteksi font yang hilang** dan mengembalikan payload JSON yang jelas sebelum PDF apa pun dihasilkan. Ini merupakan ilustrasi praktis tentang “bagaimana cara mendeteksi font yang hilang” dalam layanan produksi.

---

## ## Menguji Implementasi Anda

1. **Buat DOCX uji** yang merujuk ke font yang Anda tahu tidak ada di mesin (misalnya “Comic Sans MS” pada gambar Docker minimal).  
2. Jalankan aplikasi konsol atau endpoint API.  
3. Verifikasi bahwa konsol (atau respons HTTP) menampilkan peringatan substitusi.  
4. Opsional, buka PDF yang dihasilkan dan periksa properti font—Aspose.Words harus menampilkan font fallback yang Anda konfigurasikan.

Jika Anda melihat peringatan tetapi PDF masih menggunakan font yang tidak diharapkan, periksa kembali urutan `SubstitutionSettings`; kecocokan pertama yang ditemukan akan dipilih.

---

## ## Kesimpulan

Kami telah membahas semua yang Anda perlukan untuk **menangani substitusi font** di Aspose.Words, mulai dari mendaftarkan penangan peringatan hingga secara programatis **mendeteksi font yang hilang** dan bahkan menggantinya dengan tipe huruf korporat. Dengan memanfaatkan sistem peringatan bawaan, Anda mendapatkan visibilitas penuh atas setiap peristiwa “font tidak ditemukan”, yang secara langsung menjawab pertanyaan “**bagaimana cara mendeteksi font yang hilang**?” yang sering diajukan pengembang saat mengotomatisasi pembuatan dokumen.

Apa selanjutnya? Cobalah menggabungkan logika ini dengan **pemuatan font dinamis** (`FontSettings.SetFontsFolder`) untuk mendukung font yang diunggah pengguna secara langsung, atau perpanjang penangan peringatan untuk menulis entri ke layanan logging terpusat seperti Serilog. Semakin banyak Anda menginstrumentasi penanganan font, semakin andal alur dokumen Anda.

Punya skenario substitusi font yang rumit dan sedang Anda hadapi? Tinggalkan komentar di bawah, dan mari kita selesaikan bersama. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang memperluas teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang dapat dijalankan dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}