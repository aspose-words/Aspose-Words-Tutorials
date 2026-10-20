---
category: general
date: 2026-03-06
description: Menangkap peringatan font saat memuat dokumen Word di C#. Pelajari cara
  mendeteksi font yang hilang, memeriksa font dokumen, dan menangani font yang hilang
  secara efisien.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- load word document
- check document fonts
- handle missing fonts
language: id
og_description: Tangkap peringatan font saat memuat dokumen Word di C#. Tutorial ini
  menunjukkan cara mendeteksi font yang hilang, memeriksa font dokumen, dan menangani
  font yang hilang.
og_title: Menangkap Peringatan Font di C# – Panduan Lengkap
tags:
- Aspose.Words
- C#
- Font Management
title: Menangkap Peringatan Font di C# – Panduan Lengkap
url: /id/net/working-with-fonts/capture-font-warnings-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menangkap Peringatan Font di C# – Panduan Lengkap

Pernahkah Anda perlu **menangkap peringatan font** saat memproses dokumen Word? Menangkap peringatan font penting untuk **mendeteksi font yang hilang** dan memastikan output akhir terlihat persis seperti yang Anda harapkan.  

Dalam tutorial ini kami akan membahas contoh praktis end‑to‑end yang memuat file `.docx`, memantau proses pemuatan, dan melaporkan setiap substitusi font. Pada akhir tutorial Anda akan tahu cara **memuat dokumen word** dengan aman, **memeriksa font dokumen**, dan **menangani font yang hilang** tanpa kesalahan runtime yang tidak terduga.

## Apa yang Akan Anda Pelajari

- Cara melampirkan kolektor peringatan ke `Document` Aspose.Words.
- Jenis peringatan mana yang menunjukkan font yang hilang atau disubstitusi.
- Cara mencatat atau menanggapi peringatan tersebut dalam aplikasi produksi.
- Tips mengonfigurasi sumber font khusus bila Anda perlu **menangani font yang hilang** dengan elegan.

> **Prasyarat:** Anda memiliki lisensi Aspose.Words for .NET yang valid (atau menggunakan versi percobaan gratis) dan lingkungan pengembangan .NET (Visual Studio, Rider, atau VS Code). Tidak ada pustaka lain yang diperlukan.

---

## Menangkap Peringatan Font – Langkah‑per‑Langkah

Berikut adalah kode lengkap yang dapat dijalankan. Setiap bagian dipisahkan menjadi langkah tersendiri sehingga Anda dapat menyalin‑tempel, bereksperimen, dan memperluas logika.

![Capture font warnings diagram](image.png "Diagram showing warning collection"){: alt="capture font warnings diagram"}

### Langkah 1: Memuat Dokumen Word

Pertama, kita perlu **memuat dokumen word** yang mungkin berisi font yang tidak terpasang di mesin saat ini. Konstruktor `Document` melakukan pekerjaan berat, tetapi kami akan memisahkan pemanggilannya sehingga Anda dapat menggantinya dengan stream atau byte array nanti bila diperlukan.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        // 👉 Replace the path with the location of your .docx file.
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Step 1: Load the Word document.
        Document doc = LoadDocument(inputPath);

        // Step 2 and 3 are performed inside LoadDocument – see below.
    }

    /// <summary>
    /// Loads a document while attaching a warning collector.
    /// Returns the Document instance ready for further processing.
    /// </summary>
    private static Document LoadDocument(string path)
    {
        // Create the warning collector before the load.
        var warningCollector = new WarningInfoCollector();

        // Attach the collector to the document’s warning callback.
        // This ensures that any font‑related warnings are captured.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // Load the file – this is where Aspose.Words may discover missing fonts.
        tempDoc = new Document(path);

        // After loading, iterate over warnings and report them.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }
```

**Mengapa ini penting:** Memuat dokumen tanpa penangan peringatan berarti setiap substitusi font akan diabaikan secara diam‑diam. Dengan menetapkan `WarningCallback` *sebelum* pemuatan, kita menjamin semua peringatan `FontSubstitution` akan terlihat.

### Langkah 2: Menempelkan Kolektor Peringatan

Kelas `WarningInfoCollector` adalah implementasi bawaan dari `IWarningCallback`. Kelas ini hanya menyimpan setiap peringatan dalam daftar yang dapat kita periksa nanti.

```csharp
    /// <summary>
    /// Scans the collected warnings and prints information about missing fonts.
    /// </summary>
    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            // We’re only interested in font‑related warnings.
            if (warning.Type == WarningType.FontSubstitution)
            {
                // warning.Description contains the original font name.
                // warning.Subtype holds the name of the font that was actually used.
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Tips pro:** Jika Anda perlu **menangani font yang hilang** secara lebih agresif (misalnya, menghentikan pemuatan atau mengganti dengan fallback tertentu), Anda dapat mengganti `Console.WriteLine` dengan logika khusus—melempar pengecualian, mencatat ke file, atau bahkan menambahkan sumber font khusus.

### Langkah 3: Memverifikasi Output

Jalankan program dari konsol. Jika `input.docx` Anda menggunakan font yang tidak terpasang, Anda akan melihat baris seperti:

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
```

Jika tidak ada output yang muncul, berarti dokumen hanya menggunakan font yang sudah tersedia **atau** Aspose.Words menemukan font yang cocok dalam koleksi fallback bawaannya. Bagaimanapun, Anda telah berhasil **memeriksa font dokumen**.

---

## Mendeteksi Font yang Hilang Tanpa Lisensi (Versi Percobaan)

Bahkan jika Anda menggunakan percobaan 30‑hari, mekanisme peringatan berfungsi persis sama. Satu‑satunya perbedaan adalah percobaan menambahkan watermark pada output yang dihasilkan, yang **tidak** memengaruhi pengumpulan peringatan. Jadi Anda dapat dengan aman **mendeteksi font yang hilang** sebelum memutuskan membeli lisensi penuh.

---

## Menangani Font yang Hilang – Opsi Lanjutan

Kadang‑kadang Anda ingin menyediakan file font sendiri (misalnya font merek perusahaan) sehingga substitusi tidak pernah terjadi. Aspose.Words memungkinkan Anda mendaftarkan folder font khusus:

```csharp
// Register a folder that contains all your custom .ttf/.otf files.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
doc.FontSettings = fontSettings;
```

Letakkan kode di atas **sebelum** Anda memuat dokumen jika Anda ingin loader mempertimbangkan font tersebut selama fase parsing awal. Ini adalah cara paling dapat diandalkan untuk **menangani font yang hilang** tanpa bergantung pada font sistem default.

---

## Kesalahan Umum & Cara Menghindarinya

| Kesalahan | Mengapa Terjadi | Solusi |
|-----------|----------------|--------|
| **Kolektor peringatan dipasang setelah pemuatan** | Dokumen sudah diparse, sehingga tidak ada peringatan yang tercatat. | Pasang `WarningCallback` **sebelum** memanggil `new Document(path)`. |
| **Hanya peringatan umum yang muncul** | Anda memfilter `WarningType` yang salah. | Gunakan `WarningType.FontSubstitution` untuk fokus pada masalah font. |
| **Tidak ada output meskipun ada font yang hilang** | Aspose.Words menemukan fallback bawaan (misalnya Arial). | Nonaktifkan fallback bawaan melalui `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` |
| **Penurunan performa saat memindai dokumen besar** | Mengumpulkan setiap peringatan dapat memakan biaya. | Batasi pengumpulan hanya pada `FontSubstitution`, atau proses peringatan secara batch. |

---

## Contoh Lengkap yang Siap Pakai (Copy‑Paste)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Load the document and capture any font warnings.
        Document doc = LoadDocument(inputPath);

        // At this point you can continue processing the document,
        // knowing that you’ve already reported any missing fonts.
        Console.WriteLine("Document loaded successfully.");
    }

    private static Document LoadDocument(string path)
    {
        var warningCollector = new WarningInfoCollector();

        // IMPORTANT: set the callback BEFORE the load.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // OPTIONAL: register custom font folder to reduce substitutions.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
        tempDoc.FontSettings = fontSettings;

        // Load the document – this triggers warning collection.
        tempDoc = new Document(path);

        // Report any font substitutions.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }

    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Output konsol yang diharapkan** (asumsi dua font yang hilang):

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
Document loaded successfully.
```

Jika konsol tetap diam kecuali menampilkan “Document loaded successfully,” berarti Anda telah **memeriksa font dokumen** dan tidak menemukan font yang hilang.

---

## Kesimpulan

Kami telah menunjukkan cara **menangkap peringatan font** di C# menggunakan Aspose.Words, cara yang dapat diandalkan untuk **mendeteksi font yang hilang**, **memuat dokumen word** dengan aman, **memeriksa font dokumen**, dan **menangani font yang hilang** melalui sumber font khusus.  

Dengan pola ini Anda dapat mengintegrasikan validasi font ke dalam pipeline otomatisasi apa pun—baik Anda menghasilkan PDF, mengonversi ke HTML, atau sekadar mengarsipkan file Word.

### Apa Selanjutnya?

- Jelajahi API **FontSettings.SubstitutionSettings** untuk mendefinisikan aturan fallback Anda sendiri.
- Gabungkan pengumpulan peringatan dengan kerangka pencatatan (Serilog, NLog) untuk pemantauan produksi.
- Gunakan pendekatan yang sama untuk menangkap jenis peringatan lain, seperti resolusi gambar atau fitur yang tidak didukung.

Masih ada pertanyaan tentang penanganan font atau Aspose.Words secara umum? Tinggalkan komentar atau kunjungi forum komunitas Aspose. Selamat coding, semoga dokumen Anda selalu ditampilkan dengan font yang Anda harapkan!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}