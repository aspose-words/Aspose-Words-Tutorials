---
category: general
date: 2026-08-07
description: mengambil pemisah catatan kaki menggunakan Aspose.Words untuk .NET. Pelajari
  cara mengekstrak pemisah catatan kaki dan catatan akhir, memeriksa jenis node, serta
  memodifikasinya dalam C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve footnote separator
- Aspose.Words footnote separator
- C# footnote extraction
- endnote separator retrieval
- document node type
language: id
lastmod: 2026-08-07
og_description: mengambil pemisah catatan kaki dengan Aspose.Words untuk .NET. Panduan
  ini menunjukkan cara mengekstrak pemisah catatan kaki dan catatan akhir, memeriksa
  tipe node-nya, dan menyimpan perubahan.
og_image_alt: Console output demonstrating retrieve footnote separator results
og_title: mengambil pemisah catatan kaki di C# – tutorial Aspose.Words langkah demi
  langkah
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: retrieve footnote separator using Aspose.Words for .NET. Learn how
    to extract footnote and endnote separators, inspect node types, and modify them
    in C#.
  headline: retrieve footnote separator in C# – complete Aspose.Words guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
title: mengambil pemisah catatan kaki di C# – panduan lengkap Aspose.Words
url: /id/net/working-with-footnote-and-endnote/retrieve-footnote-separator-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# mengambil pemisah catatan kaki di C# – panduan lengkap Aspose.Words

Jika Anda perlu **retrieve footnote separator** dari dokumen Word, tutorial ini menunjukkan secara tepat cara melakukannya dengan Aspose.Words untuk .NET. Baik Anda sedang membangun layanan pemrosesan dokumen atau membersihkan format catatan kaki, Anda akan melihat contoh lengkap yang dapat dijalankan yang mengekstrak pemisah catatan kaki dan catatan akhir.

Dalam panduan ini Anda akan belajar cara memuat file `.docx`, memanggil properti `FootnoteSeparator` dan `EndnoteSeparator`, memeriksa objek `Node` yang dikembalikan, dan secara opsional mengganti garis pemisah. Tidak diperlukan dokumentasi eksternal—semua yang Anda butuhkan disertakan di bawah ini.

## Prasyarat

* .NET 6.0 atau lebih baru (kode juga berfungsi pada .NET Framework 4.7.2)
* Paket NuGet Aspose.Words untuk .NET (versi 24.9 atau lebih baru)
* Dokumen Word yang berisi catatan kaki dan/atau catatan akhir (misalnya `Footnotes.docx`)

Anda dapat menambahkan paket Aspose.Words dengan perintah CLI berikut:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

## Langkah 1: Siapkan proyek dan impor namespace

Buat proyek konsol baru atau tambahkan kode ke proyek yang sudah ada. Direktif `using` yang diperlukan tercantum di bawah ini.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

Namespace ini memberi Anda akses ke kelas `Document`, hierarki `Node`, dan enumerasi `NodeType` yang diperlukan untuk operasi **retrieve footnote separator**.

## Langkah 2: Muat dokumen yang berisi catatan kaki dan catatan akhir

Operasi pertama dalam alur kerja Aspose.Words mana pun adalah memuat file sumber. Ganti jalur placeholder dengan lokasi sebenarnya dari file `.docx` Anda.

```csharp
// Load a document that contains footnotes and endnotes
Document doc = new Document(@"C:\Docs\Footnotes.docx");

// Verify that the document was loaded
Console.WriteLine($"Document loaded: {doc.OriginalFileName}");
```

Memuat file menyiapkan pohon node internal, yang penting untuk **retrieve footnote separator** karena node pemisah berada di dalam pohon tersebut.

## Langkah 3: Retrieve the footnote separator node

Sekarang Anda dapat **retrieve footnote separator** dengan mengakses properti `FootnoteSeparator` dari objek `Document`. Node ini mewakili garis yang memisahkan catatan kaki dari teks utama.

```csharp
// Retrieve the footnote separator node (the line that separates footnotes from the main text)
Node footnoteSeparator = doc.FootnoteSeparator;

// Output its type for verification
Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");
```

`NodeType` akan menjadi `Paragraph` untuk garis pemisah standar. Mengetahui tipe node membantu Anda memutuskan apakah perlu memodifikasi pemisah atau menggantinya sepenuhnya.

## Langkah 4: Retrieve the endnote separator node

Demikian pula, Anda dapat **retrieve endnote separator** menggunakan properti `EndnoteSeparator`. Node ini memisahkan catatan akhir dari konten utama.

```csharp
// Retrieve the endnote separator node (the line that separates endnotes from the main text)
Node endnoteSeparator = doc.EndnoteSeparator;

// Output its type for verification
Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");
```

Kedua node pemisah berbagi `NodeType` yang sama (`Paragraph`) di sebagian besar dokumen, tetapi dapat disesuaikan secara independen.

## Langkah 5: Periksa atau modifikasi konten pemisah (opsional)

Jika Anda perlu mengubah tampilan visual pemisah—misalnya mengganti garis dash dengan aturan tipis—Anda dapat mengedit node `Paragraph` secara langsung. Berikut contoh yang mengganti teks pemisah default dengan string khusus.

```csharp
// Cast to Paragraph to access its text
Paragraph footnotePara = (Paragraph)footnoteSeparator;
footnotePara.Clear(); // Remove existing runs
footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

// Do the same for the endnote separator
Paragraph endnotePara = (Paragraph)endnoteSeparator;
endnotePara.Clear();
endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));
```

Setelah memodifikasi node, Anda dapat menyimpan dokumen untuk melihat perubahan yang tercermin di Word.

```csharp
// Save the updated document
string outputPath = @"C:\Docs\Footnotes_Updated.docx";
doc.Save(outputPath);
Console.WriteLine($"Updated document saved to: {outputPath}");
```

## Output konsol yang diharapkan

Saat Anda menjalankan program dengan `Footnotes.docx` asli, Anda akan melihat sesuatu yang mirip dengan:

```
Document loaded: Footnotes.docx
Footnote separator node type: Paragraph
Endnote separator node type: Paragraph
Updated document saved to: C:\Docs\Footnotes_Updated.docx
```

Jika Anda membuka `Footnotes_Updated.docx` di Microsoft Word, pemisah catatan kaki dan catatan akhir akan menampilkan teks khusus yang Anda sisipkan.

## Pertanyaan umum dan kasus tepi

**Bagaimana jika dokumen tidak memiliki catatan kaki?**  
Properti `FootnoteSeparator` tetap mengembalikan node `Paragraph` karena Word selalu menyertakan placeholder pemisah. Node tersebut akan kosong, sehingga Anda dapat menambahkan konten atau membiarkannya apa adanya.

**Apakah saya dapat mengambil pemisah untuk bagian tertentu?**  
Pemisah catatan kaki dan catatan akhir bersifat seluruh dokumen, bukan spesifik bagian. Jika Anda memerlukan kontrol tingkat bagian, Anda harus bekerja dengan `Section.FootnoteOptions` dan `Section.EndnoteOptions` alih-alih node pemisah global.

**Apakah ini bekerja dengan .NET Core?**  
Ya. Aspose.Words untuk .NET bersifat lintas‑platform, dan kode yang sama berjalan di Windows, Linux, dan macOS dengan .NET 6+.

**Tipe node apa yang harus saya harapkan?**  
Baik `FootnoteSeparator` maupun `EndnoteSeparator` mengembalikan node `Paragraph` (`NodeType.Paragraph`). Jika Anda menemukan tipe yang berbeda, dokumen mungkin rusak, dan Anda harus memuat ulang atau memvalidasi file sumber.

## Kode sumber lengkap untuk salin‑tempel cepat

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace RetrieveFootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // Load the document containing footnotes and endnotes
            Document doc = new Document(@"C:\Docs\Footnotes.docx");
            Console.WriteLine($"Document loaded: {doc.OriginalFileName}");

            // Retrieve footnote separator
            Node footnoteSeparator = doc.FootnoteSeparator;
            Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");

            // Retrieve endnote separator
            Node endnoteSeparator = doc.EndnoteSeparator;
            Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");

            // OPTIONAL: Customize separator text
            Paragraph footnotePara = (Paragraph)footnoteSeparator;
            footnotePara.Clear();
            footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

            Paragraph endnotePara = (Paragraph)endnoteSeparator;
            endnotePara.Clear();
            endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));

            // Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Updated.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Updated document saved to: {outputPath}");
        }
    }
}
```

Salin kode ke file `Program.cs`, sesuaikan jalur file, dan jalankan `dotnet run`. Program ini mendemonstrasikan alur kerja lengkap **retrieve footnote separator**, mulai dari memuat dokumen hingga menyimpan perubahan.

## Kesimpulan

Anda kini tahu cara **retrieve footnote separator** dan **endnote separator retrieval** menggunakan Aspose.Words untuk .NET, memeriksa `document node type` mereka, dan secara opsional mengganti kontennya. Teknik ini memungkinkan Anda mengotomatisasi format catatan kaki, menghasilkan garis pemisah khusus, atau memvalidasi struktur dokumen dalam aplikasi C# apa pun.

Selanjutnya, Anda mungkin ingin menjelajahi topik terkait seperti **C# footnote extraction** untuk teks catatan kaki individual, atau mempelajari cara **modify footnote reference marks** menggunakan `FootnoteOptions`. Kedua konsep tersebut dibangun langsung di atas dasar pohon node yang dibahas di sini.

Selamat coding, dan jangan ragu bereksperimen dengan gaya pemisah yang berbeda untuk menyesuaikan branding proyek Anda!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait dan membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Working With Footnote And Endnote](/words/hindi/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}