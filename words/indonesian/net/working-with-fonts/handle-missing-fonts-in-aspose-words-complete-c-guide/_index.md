---
category: general
date: 2026-03-14
description: Tangani font yang hilang dengan cepat menggunakan Aspose.Words. Pelajari
  cara menangkap peringatan substitusi font, mengonfigurasi LoadOptions, dan menghindari
  masalah rendering.
draft: false
keywords:
- handle missing fonts
- Aspose.Words
- font substitution
- LoadOptions
- DocumentWarnings
- C# document loading
language: id
og_description: Tangani font yang hilang di Aspose.Words menggunakan pengumpul peringatan.
  Tutorial ini menunjukkan langkah demi langkah cara mendeteksi dan mencatat substitusi
  font.
og_title: Menangani Font yang Hilang di Aspose.Words – Panduan Lengkap C#
tags:
- Aspose
- C#
- Fonts
- DocumentProcessing
title: Menangani Font yang Hilang di Aspose.Words – Panduan Lengkap C#
url: /id/net/working-with-fonts/handle-missing-fonts-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menangani Font yang Hilang di Aspose.Words – Panduan Lengkap C#

Pernahkah Anda **menangani font yang hilang** saat memuat dokumen Word dan bertanya-tanya mengapa output PDF atau gambar Anda terlihat aneh? Anda tidak sendirian. File font yang tidak ada adalah penyebab masalah yang diam‑diam namun dapat mengubah laporan yang dirancang dengan sempurna menjadi berantakan.  

Kabar baiknya? Aspose.Words menyediakan cara bersih untuk menangkap peristiwa substitusi font, mencatatnya, dan bahkan mengganti dengan font cadangan jika Anda mau. Pada tutorial ini kami akan menelusuri contoh lengkap yang siap dijalankan, menunjukkan cara menyiapkan kolektor peringatan, mengaitkannya ke `LoadOptions`, dan memuat dokumen yang mungkin berisi font yang hilang.

Pada akhir panduan ini Anda akan dapat:

* Mendeteksi setiap substitusi font yang terjadi selama pemuatan dokumen.  
* Mengeluarkan pesan konsol yang ramah (atau mengarahkannya ke logger) untuk setiap font yang hilang.  
* Memperluas solusi untuk mengganti font, bila diperlukan.  

**Prasyarat** – Anda memerlukan:

* .NET 6.0 atau lebih baru (kode ini juga berfungsi dengan .NET Core dan .NET Framework).  
* Paket NuGet Aspose.Words untuk .NET (versi terbaru 23.11).  
* File Word yang sengaja merujuk pada font yang tidak Anda miliki – kami sebut `doc-with-missing-font.docx`.  

Jika Anda sudah nyaman dengan C# dan memiliki proyek yang siap, Anda dapat langsung ke kode. Jika tidak, teruskan membaca; kami akan membahas langkah‑langkah penyiapan singkat terlebih dahulu.

---

## Mengapa Menangani Font yang Hilang Penting

Saat Aspose.Words memuat dokumen, ia berusaha mencocokkan setiap glyph dengan font yang terpasang di mesin. Jika tidak menemukan font yang tepat, ia secara diam‑diam menggantinya dengan yang paling mirip. Substitusi tersebut dapat mengubah tinggi baris, kerning, bahkan membuat karakter menghilang. Dengan menangkap peristiwa `WarningType.FontSubstitution` Anda mendapatkan tampilan transparan tentang **apa** yang diganti dan **mengapa**, yang penting untuk:

* Menjaga konsistensi merek (font perusahaan Anda harus muncul persis seperti yang dirancang).  
* Men-debug masalah konversi PDF—seringkali penyebabnya adalah font yang hilang.  
* Membangun pipeline dokumen otomatis di mana Anda perlu menandai file bermasalah untuk ditinjau secara manual.

Setelah “mengapa” jelas, mari kita selami **bagaimana**nya.

---

## Langkah 1 – Menyiapkan Kolektor Peringatan

Hal pertama yang kita perlukan adalah objek yang dapat mendengarkan peringatan Aspose.Words. `DocumentWarnings` mengimplementasikan `IWarningCallback`, memungkinkan kita bereaksi setiap kali perpustakaan mengeluarkan peringatan.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a collector that will receive warning events.
DocumentWarnings fontWarnings = new DocumentWarnings();

// Subscribe to the Warning event.
fontWarnings.Warning += (sender, e) =>
{
    // We only care about font substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Log the original font name that was missing.
        Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
    }
};
```

**Apa yang terjadi?**  
* `DocumentWarnings` adalah pembungkus tipis di sekitar antarmuka callback.  
* Lambda memeriksa `e.WarningType` sehingga kami mengabaikan peringatan yang tidak relevan (seperti fitur yang sudah usang).  
* `e.WarningInfo` berisi nama font yang hilang, yang kami cetak ke konsol.  

*Tips*: Ganti `Console.WriteLine` dengan logger terstruktur (Serilog, NLog) di produksi—dengan begitu Anda mendapatkan cap waktu dan level log secara otomatis.

---

## Langkah 2 – Mengaitkan Kolektor ke LoadOptions

`LoadOptions` adalah penjaga gerbang untuk setiap dokumen yang Anda buka dengan Aspose.Words. Dengan menetapkan instance `fontWarnings` ke properti `WarningCallback`‑nya, kami memastikan kolektor aktif selama proses pemuatan.

```csharp
// Configure load options to use our warning callback.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = fontWarnings
};
```

**Mengapa menggunakan LoadOptions?**  
Selain peringatan, `LoadOptions` memungkinkan Anda mengontrol penanganan kata sandi, encoding, dan bahkan pemuatan sumber daya khusus. Di sini kami fokus pada sisi peringatan, namun pola yang sama berlaku untuk callback lainnya.

---

## Langkah 3 – Memuat Dokumen dengan Opsi yang Dikonfigurasi

Sekarang kami akhirnya memuat dokumen ke memori. Jika ada font yang hilang, kolektor kami akan memicu dan Anda akan melihat baris konsol untuk setiap substitusi.

```csharp
// Path to the document that may reference missing fonts.
string docPath = Path.Combine(
    Environment.CurrentDirectory,
    "doc-with-missing-font.docx");

// Load the document using the previously configured LoadOptions.
Document document = new Document(docPath, loadOptions);
```

Jika Anda menjalankan potongan kode ini dengan dokumen yang merujuk, misalnya, *Calibri Light* sementara mesin uji Anda hanya memiliki *Calibri*, Anda akan mendapatkan output serupa dengan:

```
Font 'Calibri Light' was substituted.
```

Itulah seluruh loop deteksi—sederhana, namun kuat.

---

## Langkah 4 – (Opsional) Mengganti Font yang Hilang dengan Substitusi yang Dikenal

Terkadang Anda tidak hanya ingin mencatat masalah; Anda ingin menegakkan font cadangan sehingga output yang di‑render terlihat konsisten. Aspose.Words memungkinkan Anda menyediakan objek `FontSettings` khusus yang memetakan font yang hilang ke pengganti.

```csharp
// Create FontSettings and map any missing font to Arial.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "*", // wildcard – applies to any missing font
    new[] { "Arial" } // fallback font(s)
);

// Apply the FontSettings to the document.
document.FontSettings = fontSettings;

// Now re-save the document; all missing fonts will render as Arial.
document.Save("output-with-fallback.pdf");
Console.WriteLine("Document saved with fallback font applied.");
```

**Penjelasan**  
* Wildcard `"*"` memberi tahu Aspose.Words untuk memperlakukan *setiap* font yang hilang dengan cara yang sama.  
* Anda juga dapat memetakan font tertentu secara individual bila memerlukan kontrol yang lebih halus.  
* Setelah menetapkan `document.FontSettings`, setiap rendering selanjutnya (PDF, gambar, HTML) menghormati substitusi tersebut.

---

## Contoh Lengkap yang Siap Pakai

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke aplikasi konsol. Ia mencakup semua pernyataan `using` yang diperlukan, penanganan error, dan komentar untuk kejelasan.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        try
        {
            // -------------------------------------------------
            // Step 1: Create a warnings collector.
            // -------------------------------------------------
            DocumentWarnings fontWarnings = new DocumentWarnings();
            fontWarnings.Warning += (sender, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
                }
            };

            // -------------------------------------------------
            // Step 2: Attach the collector to LoadOptions.
            // -------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = fontWarnings
            };

            // -------------------------------------------------
            // Step 3: Load the document (may contain missing fonts).
            // -------------------------------------------------
            string docPath = Path.Combine(
                Environment.CurrentDirectory,
                "doc-with-missing-font.docx");

            Document doc = new Document(docPath, loadOptions);

            // -------------------------------------------------
            // Step 4 (optional): Apply a fallback font.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
                "*", new[] { "Arial" });

            doc.FontSettings = fontSettings;

            // Save the result to verify the substitution.
            string outPath = Path.Combine(
                Environment.CurrentDirectory,
                "output-with-fallback.pdf");

            doc.Save(outPath);
            Console.WriteLine($"Document saved to '{outPath}'.");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Error: {ex.Message}");
        }
    }
}
```

**Output yang diharapkan** (ketika font yang hilang terdeteksi):

```
Font 'Times New Roman PS' was substituted.
Document saved to 'C:\MyProject\output-with-fallback.pdf'.
```

Jika dokumen sumber sudah berisi semua font yang diperlukan, baris peringatan tidak akan muncul—tidak ada yang perlu dikhawatirkan.

---

## Pertanyaan Umum & Kasus Pinggir

| Pertanyaan | Jawaban |
|------------|---------|
| **Bagaimana jika saya hanya ingin mencatat, bukan mengganti font?** | Lewati blok `FontSettings` sepenuhnya; kolektor peringatan saja sudah cukup. |
| **Bisakah saya mengarahkan peringatan ke file?** | Ya—ganti `Console.WriteLine` dengan `File.AppendAllText("font-warnings.log", …)`. |
| **Apakah ini bekerja untuk DOC, DOCX, dan ODT?** | Tentu saja. `LoadOptions` berlaku untuk semua format yang didukung Aspose.Words. |
| **Bagaimana dengan font khusus yang tertanam di dokumen?** | Font yang tertanam melewati mekanisme substitusi; mereka digunakan apa adanya. |
| **Apakah ada dampak performa?** | Overheadnya minimal—hanya satu callback per font yang hilang. Untuk batch besar, pertimbangkan mengakumulasi peringatan daripada menulis per peristiwa. |

---

## Kesimpulan

Kami telah menunjukkan **cara menangani font yang hilang** di Aspose.Words dengan menghubungkan kolektor `DocumentWarnings` ke `LoadOptions`, secara opsional mengganti dengan font cadangan, dan menyimpan hasilnya. Pola ini memberi Anda visibilitas penuh terhadap peristiwa substitusi font, membantu menjaga kesetiaan visual pada konversi PDF, gambar, atau HTML.

Langkah selanjutnya yang dapat Anda eksplorasi:

* Mengintegrasikan kolektor peringatan dengan kerangka logging terpusat.  
* Membangun dasbor UI yang menampilkan dokumen dengan font yang hilang untuk pemrosesan batch.  
* Menggabungkan pendekatan ini dengan Aspose.PDF untuk memverifikasi bahwa PDF yang dihasilkan benar‑benar menggunakan font cadangan.  

Silakan bereksperimen—ganti `"Arial"` dengan `"Tahoma"` atau muat set dokumen yang berbeda. Ide dasarnya tetap sama: tangkap peringatan, tindak lanjuti, dan pastikan dokumen Anda tetap tampil persis seperti yang diharapkan.

Selamat coding! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}