---
category: general
date: 2026-06-02
description: Cara menyimpan PDF dari DOCX menggunakan Aspose.Words, mengekspor bentuk
  sebagai tag span inline, dan mengonversi Word ke PDF dalam beberapa langkah saja.
draft: false
keywords:
- how to save pdf
- save docx as pdf
- convert word to pdf
- how to export shapes
- inline span tags
language: id
og_description: Cara menyimpan PDF dari dokumen Word menggunakan Aspose.Words, mengekspor
  bentuk mengambang sebagai tag span inline untuk hasil konversi Word ke PDF yang
  bersih.
og_title: Cara Menyimpan PDF dari Word – Tutorial Ekspor Bentuk Inline
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  headline: How to Save PDF from Word with Inline Shape Export – Complete Guide
  type: TechArticle
- description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  name: How to Save PDF from Word with Inline Shape Export – Complete Guide
  steps:
  - name: What if my document contains **SmartArt** or **Charts**?
    text: SmartArt and charts are treated as drawing objects. The `ExportFloatingShapesAsInlineTag`
      flag will still wrap them in `<span>` tags, but complex graphics may lose some
      fidelity. In those cases, consider exporting the chart as an image first (`Chart.ToImage()`)
      and then inserting it inline.
  - name: Can I **preserve hyperlinks** and **bookmarks**?
    text: Absolutely. Those elements are not affected by the `ExportFloatingShapesAsInlineTag`
      setting. Aspose.Words retains all hyperlink and bookmark information automatically.
  - name: How do I **change PDF compression** or **embed fonts**?
    text: '`PdfSaveOptions` offers many additional properties:'
  type: HowTo
tags:
- Aspose.Words
- C#
- PDF conversion
title: Cara Menyimpan PDF dari Word dengan Ekspor Bentuk Inline – Panduan Lengkap
url: /id/net/programming-with-pdfsaveoptions/how-to-save-pdf-from-word-with-inline-shape-export-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara Menyimpan PDF dari Word dengan Ekspor Bentuk Inline – Panduan Lengkap

Pernah bertanya-tanya **cara menyimpan PDF** dari file Word sambil menjaga setiap bentuk mengambang tetap rapi dalam alur? Anda bukan satu-satunya. Dalam banyak aplikasi perusahaan kami perlu *mengonversi Word ke PDF* tanpa menghasilkan gambar yang salah tempat atau objek gambar yang terpisah. Kabar baik? Aspose.Words membuatnya mudah, dan Anda bahkan dapat memberi tahu perpustakaan untuk **mengekspor bentuk sebagai tag `<span>` inline** sehingga PDF terlihat persis seperti DOCX asli.

Dalam tutorial ini kami akan membahas seluruh proses—memuat DOCX, menyesuaikan `PdfSaveOptions`, dan akhirnya menyimpan PDF yang bersih. Pada akhir tutorial Anda akan mengetahui **cara menyimpan PDF**, **menyimpan docx sebagai pdf**, dan bahkan **cara mengekspor bentuk** menggunakan *tag span inline*.

## Apa yang Anda Butuhkan

- **Aspose.Words for .NET** (versi terbaru, 24.x pada saat penulisan).  
- **.NET 6.0** atau lebih baru – kode ini juga berfungsi pada .NET Framework 4.7.2, tetapi .NET 6 adalah pilihan terbaik.  
- Dokumen Word sederhana yang berisi setidaknya satu bentuk mengambang (gambar, kotak teks, atau gambar).  
- IDE apa pun yang Anda suka (Visual Studio, Rider, VS Code + ekstensi C#).  

Itu saja—tidak ada paket NuGet tambahan, tidak ada interop COM yang rumit. Siap? Mari kita mulai.

## Langkah 1: Siapkan Proyek dan Tambahkan Aspose.Words

Pertama, buat aplikasi console (atau integrasikan kode ke dalam layanan yang sudah ada).

```bash
dotnet new console -n WordToPdfDemo
cd WordToPdfDemo
dotnet add package Aspose.Words
```

> **Pro tip:** Jika Anda menggunakan Visual Studio, Anda dapat menambahkan paket melalui UI NuGet Package Manager—cukup cari *Aspose.Words*.

## Langkah 2: Muat Dokumen Sumber

Sekarang perpustakaan sudah direferensikan, kita dapat memuat DOCX. Ini adalah tindakan konkret pertama bagian **cara menyimpan pdf**—memuat sumber ke memori.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Step 2: Load the source document
        // Replace YOUR_DIRECTORY with the actual path on your machine.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded successfully.");
```

**Mengapa ini penting:** Memuat file memvalidasi bahwa jalur benar dan Aspose dapat mengurai struktur Word. Jika file berisi bentuk mengambang, mereka akan menjadi bagian dari pohon node objek `Document`.

## Langkah 3: Konfigurasikan Opsi Penyimpanan PDF – Ekspor Bentuk sebagai Tag Inline

Berikut inti dari **cara mengekspor bentuk**. Secara default Aspose.Words merender bentuk mengambang sebagai objek terpisah dalam PDF, yang dapat menggeser tata letak. Menetapkan `ExportFloatingShapesAsInlineTag` ke `true` memberi tahu mesin untuk membungkus setiap bentuk dalam elemen `<span>` inline, mempertahankan alur.

```csharp
        // Step 3: Configure PDF save options to export floating shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            // Optional: keep the original page size
            PageMode = PdfPageMode.UseTrimBox
        };
        Console.WriteLine("PDF save options configured – shapes will be inline.");
```

**Mengapa mengaktifkan flag ini?** Bayangkan sebuah kontrak dengan kotak tanda tangan yang mengambang di atas teks. Saat Anda mengonversinya ke PDF tanpa pengaturan ini, kotak tersebut dapat muncul di halaman yang berbeda. Tag `<span>` inline menjaga bentuk tetap terikat pada paragraf sekitarnya, menghasilkan replika visual yang akurat.

## Langkah 4: Simpan Dokumen sebagai PDF

Akhirnya, kita memanggil `doc.Save` dengan opsi yang baru saja dibuat. Ini adalah momen Anda benar‑benar **menyimpan docx sebagai pdf**.

```csharp
        // Step 4: Save the document as a PDF using the configured options
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved successfully to: {outputPath}");
    }
}
```

Jalankan program (`dotnet run`) dan periksa `output.pdf`. Anda akan melihat bentuk mengambang Anda dirender inline, persis seperti yang muncul di Word.

## Langkah 5: Verifikasi Hasil – Daftar Periksa Cepat

1. **Semua teks ada** – tidak ada paragraf yang hilang.  
2. **Bentuk mengambang muncul di tempat yang seharusnya** – kini mereka menjadi bagian dari alur teks.  
3. **Ukuran PDF wajar** – mengekspor sebagai tag inline biasanya mengurangi pembengkakan file dibandingkan aliran gambar terpisah.  

Jika ada yang tampak tidak tepat, periksa kembali bahwa DOCX sumber benar‑benar menggunakan bentuk *mengambang* (klik kanan → Layout → “In line with text” vs “Square/Behind text”). Mengubah bentuk menjadi “In line” sebelum konversi juga berhasil, tetapi opsi tag inline memberi Anda kontrol tanpa mengedit file asli.

## Kasus Pinggir & Pertanyaan Umum

### Bagaimana jika dokumen saya berisi **SmartArt** atau **Chart**?

SmartArt dan chart diperlakukan sebagai objek gambar. Flag `ExportFloatingShapesAsInlineTag` tetap akan membungkusnya dalam tag `<span>`, tetapi grafik kompleks mungkin kehilangan sebagian fidelitas. Dalam kasus tersebut, pertimbangkan mengekspor chart sebagai gambar terlebih dahulu (`Chart.ToImage()`) lalu menyisipkannya inline.

### Bisakah saya **mempertahankan hyperlink** dan **bookmark**?

Tentu saja. Elemen‑elemen tersebut tidak terpengaruh oleh pengaturan `ExportFloatingShapesAsInlineTag`. Aspose.Words secara otomatis mempertahankan semua informasi hyperlink dan bookmark.

### Bagaimana cara **mengubah kompresi PDF** atau **menyematkan font**?

`PdfSaveOptions` menawarkan banyak properti tambahan:

```csharp
pdfOpts.JpegQuality = 90;               // Adjust image compression
pdfOpts.FontEmbeddingMode = FontEmbeddingMode.EmbedAll; // Embed all used fonts
```

Silakan sesuaikan pengaturan tersebut berdasarkan kebutuhan downstream Anda (mis., kepatuhan PDF/A).

## Contoh Lengkap yang Berfungsi (Siap Salin‑Tempel)

Berikut adalah program lengkap yang dapat Anda salin ke `Program.cs`. Ganti `YOUR_DIRECTORY` dengan jalur folder yang sebenarnya.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load the source DOCX (contains floating shapes)
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded.");

        // Configure PDF save options – export shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            PageMode = PdfPageMode.UseTrimBox,
            // Optional tweaks
            JpegQuality = 90,
            FontEmbeddingMode = FontEmbeddingMode.EmbedAll
        };
        Console.WriteLine("PDF options set – shapes will be inline.");

        // Save as PDF
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved to {outputPath}");
    }
}
```

**Output yang diharapkan di konsol:**

```
Document loaded.
PDF options set – shapes will be inline.
PDF saved to C:\MyDocs\output.pdf
```

Buka `output.pdf`—Anda akan melihat tata letak asli, dengan setiap bentuk mengambang ditempatkan rapi di dalam alur teks.

## Kesimpulan

Kami telah membahas **cara menyimpan PDF** dari dokumen Word sambil memastikan bahwa bentuk mengambang menjadi tag `<span>` inline. Dengan memuat DOCX, mengonfigurasi `PdfSaveOptions`, dan memanggil `doc.Save`, Anda dapat dengan andal **menyimpan docx sebagai pdf** dan **mengonversi word ke pdf** tanpa kejutan tata letak.  

Langkah selanjutnya? Coba gabungkan pendekatan ini dengan kepatuhan **PDF/A** untuk arsip, atau proses batch folder berisi file DOCX dengan loop `foreach` sederhana. Anda juga dapat menjelajahi **rendering khusus** (mis., menambahkan watermark) dengan memanfaatkan API `DocumentVisitor` Aspose.Words.

Ada pertanyaan lebih lanjut tentang penanganan bentuk, penyematan font, atau penyetelan kinerja? Tinggalkan komentar di bawah, dan selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber mencakup contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Cara menyimpan dokumen sebagai pdf dengan Aspose.Words untuk Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Mengonversi Word ke PDF dengan Aspose.Words untuk Java](/words/english/java/document-converting/exporting-documents-to-pdf/)
- [aspose word to pdf – Mengonversi DOCX ke PDF di Java](/words/english/java/document-conversion-and-export/aspose-word-to-pdf-convert-docx-to-pdf-in-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}