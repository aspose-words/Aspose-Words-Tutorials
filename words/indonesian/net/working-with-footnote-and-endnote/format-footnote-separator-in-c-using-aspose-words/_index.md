---
category: general
date: 2026-08-10
description: Format pemisah catatan kaki di C# dengan Aspose.Words untuk menyesuaikan
  baris catatan kaki dan catatan akhir. Pelajari pemformatan catatan kaki C# dalam
  hitungan menit.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- format footnote separator
- Aspose.Words footnote separator
- C# footnote formatting
- modify footnote separator
- style footnote separator
- endnote separator formatting
language: id
lastmod: 2026-08-10
og_description: Format pemisah catatan kaki dalam C# menggunakan Aspose.Words. Ikuti
  tutorial ini untuk menata pemisah catatan kaki dan catatan akhir secara cepat dan
  dapat diandalkan.
og_image_alt: Code editor showing C# snippet that styles a footnote separator
og_title: Format pemisah catatan kaki di C# – panduan lengkap Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  headline: Format footnote separator in C# using Aspose.Words
  type: TechArticle
- description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  name: Format footnote separator in C# using Aspose.Words
  steps:
  - name: Styling the continuation separator (optional)
    text: 'The continuation separator appears when a footnote spans multiple pages.
      You can style it similarly:'
  - name: Formatting the endnote separator
    text: 'If your document also uses endnotes, you can apply the same logic to the
      `Endnotes` collection:'
  - name: Using a custom string for the separator
    text: 'Sometimes you want the separator to be a series of asterisks (`***`). Replace
      the existing runs with a new run:'
  - name: Handling documents without a separator node
    text: 'A rare edge case is a document that omits the separator node (e.g., when
      the author deleted it). In that scenario `document.Footnotes.Separator` returns
      `null`. Guard against it:'
  type: HowTo
tags:
- Aspose.Words
- C#
- footnotes
- document‑processing
title: Format pemisah catatan kaki di C# menggunakan Aspose.Words
url: /id/net/working-with-footnote-and-endnote/format-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Memformat pemisah catatan kaki di C# menggunakan Aspose.Words

Jika Anda perlu **memformat pemisah catatan kaki** dalam dokumen Word, panduan ini menunjukkan cara melakukannya dengan Aspose.Words untuk .NET. Anda akan melihat contoh lengkap yang dapat dijalankan yang mengubah perataan dan warna paragraf pemisah, dan Anda akan belajar cara menerapkan teknik yang sama pada pemisah catatan akhir.

Tutorial ini mencakup setiap langkah—dari memuat file sumber hingga menyimpan dokumen yang telah dimodifikasi—sehingga Anda dapat menyalin‑tempel kode ke dalam proyek Anda sendiri tanpa penelitian tambahan.

## Apa yang Anda butuhkan

Sebelum memulai, pastikan Anda memiliki:

* .NET 6.0 atau lebih baru (kode juga berfungsi dengan .NET Framework 4.6+)
* Lisensi Aspose.Words untuk .NET yang valid (versi percobaan gratis dapat digunakan untuk evaluasi)
* File Word yang berisi setidaknya satu catatan kaki atau catatan akhir (misalnya, `Footnotes.docx`)
* Visual Studio 2022 atau IDE C# lain yang Anda sukai

Memiliki semua item ini siap memungkinkan Anda fokus pada logika **pemformatan catatan kaki C#** alih-alih pengaturan lingkungan.

## Langkah 1: Muat dokumen yang berisi catatan kaki dan catatan akhir

Operasi pertama adalah membuat objek `Document` yang menunjuk ke file sumber Anda. Aspose.Words membaca seluruh paket DOCX ke dalam memori, memberi Anda akses penuh ke node catatan kaki dan catatan akhir.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;

// Load the source DOCX file
Document document = new Document(@"C:\Docs\Footnotes.docx");
```

*Mengapa ini penting*: Memuat dokumen adalah prasyarat untuk setiap manipulasi. Jika jalur file salah, Aspose.Words akan melempar `FileNotFoundException`, jadi pastikan jalur tersebut benar sebelum melanjutkan.

## Langkah 2: Dapatkan node pemisah dan pemisah‑lanjutan

Pemisah catatan kaki dan catatan akhir disimpan sebagai node khusus di dalam koleksi `Footnotes` dan `Endnotes`. Setiap koleksi menyediakan properti `Separator` dan `ContinuationSeparator` yang mengembalikan referensi `Node`.

```csharp
// Footnote separator nodes
Node footnoteSeparator          = document.Footnotes.Separator;
Node footnoteContinuationSep    = document.Footnotes.ContinuationSeparator;

// Endnote separator nodes
Node endnoteSeparator           = document.Endnotes.Separator;
Node endnoteContinuationSep     = document.Endnotes.ContinuationSeparator;
```

*Mengapa ini penting*: Node `Separator` mewakili garis yang secara visual memisahkan teks utama dari blok catatan kaki. Dengan memperoleh referensi, Anda dapat memodifikasi format paragrafnya, font, atau bahkan mengganti node tersebut sepenuhnya.

## Langkah 3: Ubah gaya visual pemisah catatan kaki

Di kebanyakan dokumen Word, pemisah adalah satu paragraf tunggal yang berisi tanda hubung atau asterisk. Kode di bawah memeriksa apakah pemisah adalah `Paragraph` dan, jika ya, memusatkannya serta mengubah warna teks menjadi abu‑abu.

```csharp
// Ensure the separator is a Paragraph before casting
if (footnoteSeparator is Paragraph separatorParagraph)
{
    // Center the separator paragraph
    separatorParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;

    // Set the separator text color to gray
    if (separatorParagraph.Runs.Count > 0)
    {
        separatorParagraph.Runs[0].Font.Color = Color.Gray;
    }
}
```

### Menata pemisah lanjutan (opsional)

Pemisah lanjutan muncul ketika catatan kaki melintasi beberapa halaman. Anda dapat menatanya dengan cara yang sama:

```csharp
if (footnoteContinuationSep is Paragraph contParagraph)
{
    contParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (contParagraph.Runs.Count > 0)
        contParagraph.Runs[0].Font.Color = Color.DarkGray;
}
```

*Mengapa ini penting*: Menyelaraskan pemisah meningkatkan keterbacaan, dan mengubah warnanya membedakannya dari teks paragraf biasa. Anda dapat mengganti `ParagraphAlignment.Center` dengan `Left` atau `Right` untuk menyesuaikan dengan pedoman desain dokumen Anda.

## Langkah 4: Simpan dokumen yang telah dimodifikasi

Setelah menerapkan gaya yang diinginkan, tulis kembali dokumen ke disk. Anda dapat menimpa file asli atau membuat versi baru.

```csharp
// Save the document with the modified separator
document.Save(@"C:\Docs\Footnotes_Styled.docx");
```

Saat Anda membuka `Footnotes_Styled.docx` di Microsoft Word, pemisah catatan kaki muncul terpusat dan berwarna abu‑abu, persis seperti yang ditentukan oleh kode.

## Variasi lanjutan

### Memformat pemisah catatan akhir

Jika dokumen Anda juga menggunakan catatan akhir, Anda dapat menerapkan logika yang sama pada koleksi `Endnotes`:

```csharp
if (endnoteSeparator is Paragraph endSepParagraph)
{
    endSepParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (endSepParagraph.Runs.Count > 0)
        endSepParagraph.Runs[0].Font.Color = Color.SlateGray;
}
```

### Menggunakan string khusus untuk pemisah

Kadang‑kadang Anda ingin pemisah berupa rangkaian asterisk (`***`). Ganti run yang ada dengan run baru:

```csharp
if (footnoteSeparator is Paragraph sepPara)
{
    // Clear existing content
    sepPara.Runs.Clear();

    // Add a custom separator string
    Run newRun = new Run(document, "***");
    newRun.Font.Color = Color.Gray;
    sepPara.Runs.Add(newRun);
}
```

### Menangani dokumen tanpa node pemisah

Kasus tepi yang jarang terjadi adalah dokumen yang menghilangkan node pemisah (misalnya, ketika penulis menghapusnya). Dalam skenario tersebut `document.Footnotes.Separator` mengembalikan `null`. Lindungi kode Anda:

```csharp
if (footnoteSeparator != null && footnoteSeparator is Paragraph sepPara)
{
    // Apply styling as shown earlier
}
else
{
    // Optionally create a new separator paragraph
    Paragraph newSep = new Paragraph(document);
    newSep.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    Run run = new Run(document, "-");
    run.Font.Color = Color.Gray;
    newSep.Runs.Add(run);
    document.Footnotes.InsertAfter(newSep, document.Footnotes.LastParagraph);
}
```

## Kesulitan umum dan cara menghindarinya

| Kesulitan | Mengapa terjadi | Solusi |
|-----------|----------------|--------|
| **Separator bukan `Paragraph`** | Beberapa templat Word menggunakan `Table` atau `Shape` sebagai pemisah. | Periksa tipe node dengan `is Paragraph` sebelum melakukan casting. |
| **Koleksi `Runs` kosong** | Pemisah mungkin berupa paragraf kosong. | Verifikasi `Runs.Count > 0` sebelum mengakses `Runs[0]`. |
| **Lisensi tidak diterapkan** | Tanpa lisensi, Aspose.Words menambahkan watermark dan dapat membatasi penggunaan API. | Panggil `License license = new License(); license.SetLicense("Aspose.Words.lic");` di awal program Anda. |
| **Menyimpan ke folder baca‑saja** | Metode `Save` melempar `UnauthorizedAccessException`. | Pastikan direktori target memiliki izin menulis. |

Menangani masalah‑masalah ini sejak awal mencegah pengecualian runtime dan memastikan pengalaman **memodifikasi pemisah catatan kaki** yang lancar.

## Contoh lengkap yang dapat dijalankan

Berikut adalah aplikasi konsol mandiri yang mendemonstrasikan setiap langkah yang dibahas di atas. Salin kode ke dalam proyek konsol .NET baru, ganti jalur file, dan jalankan.

```csharp
using Aspose.Words;
using System;
using System.Drawing;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // OPTIONAL: Apply your Aspose.Words license
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1. Load the source document
            string inputPath = @"C:\Docs\Footnotes.docx";
            Document doc = new Document(inputPath);

            // 2. Retrieve separator nodes
            Node footnoteSeparator = doc.Footnotes.Separator;
            Node footnoteContinuationSep = doc.Footnotes.ContinuationSeparator;
            Node endnoteSeparator = doc.Endnotes.Separator;
            Node endnoteContinuationSep = doc.Endnotes.ContinuationSeparator;

            // 3. Style footnote separator
            if (footnoteSeparator is Paragraph footSepPara)
            {
                footSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footSepPara.Runs.Count > 0)
                    footSepPara.Runs[0].Font.Color = Color.Gray;
            }

            // 3a. (Optional) Style footnote continuation separator
            if (footnoteContinuationSep is Paragraph footContPara)
            {
                footContPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footContPara.Runs.Count > 0)
                    footContPara.Runs[0].Font.Color = Color.DarkGray;
            }

            // 4. Style endnote separator (optional)
            if (endnoteSeparator is Paragraph endSepPara)
            {
                endSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (endSepPara.Runs.Count > 0)
                    endSepPara.Runs[0].Font.Color = Color.SlateGray;
            }

            // 5. Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Styled.docx";
            doc.Save(outputPath);

            Console.WriteLine("Footnote separator formatted successfully.");
            Console.WriteLine($"Saved to: {outputPath}");
        }
    }
}
```

**Hasil yang diharapkan**  

Saat Anda membuka `Footnotes_Styled.docx`:

* Garis pemisah catatan kaki terpusat di bawah teks utama.  
* Warnanya muncul sebagai abu‑abu terang, sehingga terlihat berbeda.  
* Jika dokumen berisi catatan akhir, pemisah mereka juga terpusat dan berwarna abu‑abu (atau slate

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait dan membangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Pemrosesan Kata dengan Catatan Kaki dan Catatan Akhir](/words/english/net/working-with-footnote-and-endnote/)
- [Atur Posisi Catatan Kaki dan Catatan Akhir](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Bekerja dengan Catatan Kaki dan Catatan Akhir](/words/german/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}