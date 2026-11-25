---
category: general
date: 2026-11-25
description: Pelajari cara membuat dokumen Word, menambahkan bentuk persegi panjang,
  merangkum dokumen dengan AI, menerjemahkan teks menggunakan AI, dan menyimpan dokumen
  sebagai DOCX menggunakan Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- summarize document with ai
- save document as docx
- translate text using ai
language: id
lastmod: 2026-11-25
og_description: Buat dokumen Word, tambahkan bentuk persegi panjang, rangkum dokumen
  dengan AI, terjemahkan teks menggunakan AI, dan simpan dokumen sebagai DOCX—semua
  dalam satu tutorial C#.
og_image_alt: Screenshot showing a generated Word document with a rectangle shape
  and AI‑generated summary
og_title: Buat dokumen Word dengan bentuk, ringkasan AI, dan terjemahan dalam C#
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a Word document, add rectangle shape, summarize
    document with AI, translate text using AI, and save document as DOCX using Aspose.Words.
  headline: How to create a Word document with shapes, AI summarization, and translation
    in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- AI integration
title: Cara membuat dokumen Word dengan bentuk, ringkasan AI, dan terjemahan dalam
  C#
url: /id/net/ai-powered-document-processing/how-to-create-a-word-document-with-shapes-ai-summarization-a/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat dokumen Word dengan bentuk, rangkuman AI, dan terjemahan dalam C#

Jika Anda perlu **membuat dokumen Word** secara programatis, panduan ini menunjukkan secara tepat cara melakukannya. Dengan menggunakan Aspose.Words untuk .NET Anda akan belajar untuk **menambahkan bentuk persegi panjang**, memanggil layanan AI untuk **merangkum dokumen dengan AI**, menerjemahkan sebuah paragraf dengan **menerjemahkan teks menggunakan AI**, dan akhirnya **menyimpan dokumen sebagai DOCX**.

Banyak pengembang mengalami kesulitan menggabungkan otomatisasi dokumen dengan fitur AI modern. Pada akhir tutorial ini Anda akan memiliki satu proyek C# yang berdiri sendiri yang menghasilkan file *.docx* yang sepenuhnya terformat, lengkap dengan bentuk visual, rangkuman yang dihasilkan AI, dan konten multibahasa.

## Prasyarat

- .NET 6.0 SDK atau yang lebih baru terpasang  
- Visual Studio 2022 (atau IDE C# apa pun)  
- Lisensi Aspose.Words untuk .NET (atau kunci evaluasi gratis)  
- Akses internet untuk panggilan rangkuman AI dan terjemahan  

Tidak ada paket NuGet tambahan yang diperlukan selain `Aspose.Words` dan `Aspose.Words.AI`.

## Langkah 1: Siapkan proyek dan tambahkan paket yang diperlukan

Buat proyek konsol baru dan tambahkan pustaka Aspose.Words.

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

> **Pro tip:** Jika Anda berencana menggunakan mode evaluasi, panggil `Aspose.Words.License.SetLicense("Aspose.Words.lic");` di awal `Main` untuk menghindari watermark.

## Langkah 2: Inisialisasi dokumen – inti dari **create word document**

Baris kode pertama yang dapat dijalankan membuat objek **Word document** baru. Objek ini adalah kanvas untuk semua operasi selanjutnya.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // Create a new, empty Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` mempermudah penyisipan teks, bentuk, dan kontrol tanpa harus menangani pohon node tingkat rendah secara manual.

## Langkah 3: **Add rectangle shape** ke dokumen

Bentuk persegi panjang dapat digunakan sebagai placeholder visual, latar belakang label, atau grafik sederhana. Pertama kami membuat `GroupShape`, lalu menyisipkan `Rectangle` di dalamnya.

```csharp
        // Step 3: Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

Persegi panjang tersebut berukuran 100 poin lebar dan 50 poin tinggi. Karena berada di dalam `GroupShape`, Anda dapat menambahkan elemen lain nanti (mis., kotak teks) tanpa khawatir tentang benturan tata letak.

## Langkah 4: Sisipkan StructuredDocumentTag (SDT) teks biasa

Objek StructuredDocumentTag berguna untuk kontrol konten yang dapat diikat ke sumber data nanti.

```csharp
        // Step 4: Add a plain‑text StructuredDocumentTag (SDT) to the document
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);
```

Flag `true` menandai tag sebagai kontrol **repeating**, yang berguna untuk templat.

## Langkah 5: Tambahkan kontrol ActiveX CommandButton (UI opsional)

Jika dokumen yang dihasilkan akan digunakan dalam lingkungan yang mendukung ActiveX, Anda dapat menyematkan tombol.

```csharp
        // Step 5: Insert an ActiveX CommandButton control (Forms2 OLE control)
        builder.InsertForms2OleControl(OleControlType.CommandButton);
```

Langkah ini opsional; Anda dapat menghapusnya jika audiens target Anda tidak pernah berinteraksi dengan dokumen dalam lingkungan Windows.

## Langkah 6: **Summarize document with AI**

Aspose.Words.AI menyediakan pembungkus yang nyaman di sekitar layanan model bahasa besar. Di sini kami memanggil `DocumentSummarizer.Summarize` dengan backend OpenAI.

```csharp
        // Step 6: Summarize the document content using an AI service
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);
```

Metode ini menganalisis pohon node saat ini, mengekstrak kalimat paling relevan, dan mengembalikan paragraf singkat. Ini adalah inti dari fungsi **summarize document with AI**.

## Langkah 7: **Translate text using AI**

Selanjutnya kami menunjukkan cara menerjemahkan string contoh dari bahasa Inggris ke Prancis. Metode `Translator.Translate` secara internal memanggil model AI Google.

```csharp
        // Step 7: Translate a sample paragraph to French using Google AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);
```

Anda dapat mengganti `Language.French` dengan nilai enum bahasa lain yang didukung, memungkinkan pembuatan dokumen multibahasa secara langsung.

## Langkah 8: **Save document as DOCX**

Akhirnya, simpan dokumen yang telah diedit ke disk. Metode `Save` secara otomatis menulis file *.docx* ketika Anda menentukan ekstensi `.docx`.

```csharp
        // Step 8: Save the modified document
        document.Save("Result.docx"); // **save document as docx**
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

File `Result.docx` kini berisi:

- Sebuah bentuk persegi panjang di dalam group shape  
- Kontrol konten teks biasa (SDT)  
- Sebuah ActiveX CommandButton (jika Anda mempertahankan Langkah 5)  
- Paragraf rangkuman yang dihasilkan AI  
- Terjemahan bahasa Prancis dari “Hello world”

Anda dapat membuka file tersebut di Microsoft Word untuk memverifikasi setiap elemen.

## Kode sumber lengkap

Berikut adalah program lengkap yang siap dijalankan. Salin ke dalam `Program.cs` dan jalankan `dotnet run`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // 1. Create a new Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3. Add a plain‑text StructuredDocumentTag (SDT)
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);

        // 4. Insert an ActiveX CommandButton (optional)
        builder.InsertForms2OleControl(OleControlType.CommandButton);

        // 5. Summarize the document using AI
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);

        // 6. Translate a paragraph to French using AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);

        // 7. Save the document as DOCX
        document.Save("Result.docx");
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

### Output yang diharapkan

```
Document summary:
[AI‑generated concise summary of the document’s current content]

Translated paragraph (English → French):
Bonjour le monde

Document saved as Result.docx
```

Saat Anda membuka `Result.docx`, Anda akan melihat bentuk persegi panjang di bagian atas, placeholder SDT, tombol, paragraf rangkuman, dan terjemahan bahasa Prancis yang disisipkan sebagai teks biasa.

## Kesimpulan

Anda kini tahu cara **membuat dokumen Word** dari awal, **menambahkan bentuk persegi panjang**, **merangkum dokumen dengan AI**, **menerjemahkan teks menggunakan AI**, dan **menyimpan dokumen sebagai DOCX**—semua dengan beberapa baris kode C# yang singkat. Pola ini dapat diskalakan: Anda dapat mengganti string yang dikodekan secara tetap dengan data dinamis, menambahkan lebih banyak bentuk atau diagram, dan mengganti penyedia AI dengan menyesuaikan parameter `SummarizerOptions` atau `Translator`.

### Apa selanjutnya?

- Jelajahi variasi **add rectangle shape**: ubah warna isi, gaya garis, atau tambahkan teks di dalam bentuk.  
- Gunakan **summarize document with AI** pada dokumen yang lebih besar untuk menghasilkan rangkuman eksekutif secara otomatis.  
- Perluas **translate text using AI** untuk memproses batch seluruh paragraf atau tabel untuk laporan multibahasa.  
- Gabungkan API charting Aspose.Words untuk menyematkan visualisasi data bersama wawasan yang dihasilkan AI.  

Silakan bereksperimen, dan bagikan hasil Anda di komentar atau di GitHub. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat dokumen Word kosong dan tambahkan bentuk persegi panjang](/words/english/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)
- [Buat Group Shape dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Tambahkan Watermark Teks dalam Dokumen Word Menggunakan Aspose.Words untuk .NET](/words/english/net/working-with-watermark/add-text-watermark/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}