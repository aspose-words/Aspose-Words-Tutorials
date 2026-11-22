---
category: general
date: 2026-11-22
description: Atur teks placeholder dalam kontrol konten Word dengan C#. Pelajari cara
  membuat tag khusus, menyisipkan kontrol teks biasa, dan menambahkan placeholder
  ke tag menggunakan Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- create custom tag
- how to insert content control
- add placeholder to tag
- insert plain text control
language: id
lastmod: 2026-11-22
og_description: Atur teks placeholder dalam kontrol konten Word dengan C#. Tutorial
  ini menunjukkan cara membuat tag khusus, menyisipkan kontrol teks biasa, dan menambahkan
  placeholder ke tag untuk meningkatkan interaktivitas dokumen.
og_image_alt: Screenshot showing a Word document with a content control placeholder
  text set using C#
og_title: Atur teks placeholder dalam kontrol konten Word – panduan C#
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Set placeholder text in a Word content control with C#. Learn how to
    create a custom tag, insert a plain text control, and add placeholder to tag using
    Aspose.Words.
  headline: Set placeholder text in a Word content control with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: Atur teks placeholder dalam kontrol konten Word dengan C#
url: /id/java/using-document-elements/set-placeholder-text-in-a-word-content-control-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Set placeholder text in a Word content control with C#

Jika Anda perlu **set placeholder text** dalam dokumen Word secara programatis, panduan ini menunjukkan secara tepat cara melakukannya. Menggunakan Aspose.Words for .NET Anda dapat membuat tag khusus, menyisipkan kontrol plain‑text, dan menambahkan placeholder ke tag sehingga dokumen siap untuk input pengguna.

Dalam tutorial ini Anda akan belajar cara **create custom tag**, **how to insert content control**, dan **add placeholder to tag** sambil menjaga kode tetap singkat dan siap produksi. Tidak diperlukan alat eksternal—hanya proyek .NET dan pustaka Aspose.Words.

## Prerequisites

Sebelum Anda memulai, pastikan Anda memiliki:

* .NET 6.0 SDK atau yang lebih baru terpasang  
* Lisensi Aspose.Words for .NET yang valid (atau kunci evaluasi gratis)  
* Familiaritas dasar dengan C# dan Visual Studio (atau IDE lain yang Anda sukai)  

Bagian-bagian berikut mengasumsikan Anda telah membuat proyek console bernama `WordPlaceholderDemo`.

## Step 1: Install Aspose.Words

Tambahkan paket NuGet ke proyek Anda:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Gunakan flag `--version` untuk mengunci paket ke rilis stabil terbaru (misalnya, `Aspose.Words.NET 24.9`).

## Step 2: Load the source document and create a `DocumentBuilder`

Hal pertama yang Anda lakukan adalah memuat file `.docx` yang sudah ada (atau membuat dokumen kosong baru) dan menginstansiasi `DocumentBuilder`. Builder memberikan API yang fluent untuk menyisipkan kontrol dan teks.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Load an existing Word file or create a new one
            Document doc = new Document("input.docx");   // <-- replace with your path
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Kode ini **sets the stage** untuk menyisipkan kontrol konten. `DocumentBuilder` bekerja langsung pada objek `doc`, sehingga setiap perubahan yang Anda buat secara otomatis tercermin.

## Step 3: Create a custom tag (StructuredDocumentTag)

*custom tag* di Word disebut **StructuredDocumentTag (SDT)**. Anda dapat menganggapnya sebagai kontrol konten yang membawa pengidentifikasi unik. Membuatnya adalah inti dari langkah **create custom tag**.

```csharp
            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag identifier
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
```

Metode `InsertStructuredDocumentTag` menerima dua argumen:

1. Tipe kontrol (`PlainText` dalam kasus ini).  
2. String yang secara unik mengidentifikasi tag (`"MyTag"`).  

Dengan menggunakan **custom tag**, Anda dapat nanti menemukan atau memanipulasi kontrol secara programatis.

## Step 4: Set a title for accessibility

Judul meningkatkan aksesibilitas dan memudahkan kontrol ditemukan di UI Word.

```csharp
            // Set a descriptive title (used by screen readers)
            sdt.Title = "CustomerName";
```

Properti `Title` bersifat opsional, tetapi menambahkannya merupakan praktik terbaik ketika Anda **add placeholder to tag** untuk pengalaman pengguna yang lebih baik.

## Step 5: Add placeholder text to the tag

Sekarang tiba tujuan utama: **set placeholder text**. Teks ini muncul ketika kontrol kosong, memberi petunjuk kepada pengguna tentang apa yang harus diketik.

```csharp
            // Provide placeholder text that shows when the tag is empty
            sdt.PlaceholderText = "Enter name…";
```

Properti `PlaceholderText` adalah apa yang Anda perlukan untuk **add placeholder to tag**. Ia berperilaku seperti petunjuk abu‑abu yang Anda lihat pada bidang formulir modern.

## Step 6: Save the modified document

Setelah mengonfigurasi kontrol, tulis dokumen kembali ke disk.

```csharp
            // Save the document with the new content control
            doc.Save("output.docx");   // <-- replace with your desired path
        }
    }
}
```

Saat Anda membuka `output.docx` di Microsoft Word, Anda akan melihat kontrol konten plain‑text berlabel “CustomerName” dengan placeholder “Enter name…”. Mengklik di dalam kontrol menghapus placeholder, memungkinkan pengguna mengetik.

### Expected output

* File Word (`output.docx`) yang berisi satu kontrol konten plain‑text.  
* Kontrol menampilkan placeholder “Enter name…” hingga pengguna mengetik sesuatu.  
* Pengidentifikasi tag kontrol adalah `MyTag`, yang dapat Anda query nanti dengan `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.

## Step 7: How to insert content control elsewhere (advanced)

Jika Anda perlu **how to insert content control** pada lokasi tertentu—misalnya, setelah paragraf tertentu—gunakan metode `MoveTo` sebelum menyisipkan tag:

```csharp
            // Move the cursor to the end of the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            // Insert another plain‑text control with a different tag
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";
```

Potongan kode ini mendemonstrasikan **insert plain text control** beberapa kali dalam dokumen yang sama.

## Common pitfalls and how to avoid them

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| Placeholder not visible | The control already contains text (even a space) | Ensure `sdt.Text` is empty before setting `PlaceholderText`. |
| Tag identifier collision | Re‑using the same tag name (`MyTag`) in the same document | Use unique identifiers for each `StructuredDocumentTag`. |
| License exception | Running without a valid Aspose.Words license | Apply a license file (`license.SetLicense("Aspose.Words.lic")`) at the start of `Main`. |
| Document not saved | Forgetting to call `doc.Save` or using a read‑only path | Verify the output path is writable and call `doc.Save`. |

## Full working example

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke `Program.cs`. Program ini mencakup semua langkah—**create custom tag**, **how to insert content control**, **add placeholder to tag**, dan **insert plain text control**—dalam satu alur yang koheren.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Optional: apply your Aspose.Words license here
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // Load the source document (or create a new one)
            Document doc = new Document("input.docx");
            DocumentBuilder builder = new DocumentBuilder(doc);

            // --------- Create custom tag ----------
            StructuredDocumentTag nameTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
            nameTag.Title = "CustomerName";
            nameTag.PlaceholderText = "Enter name…";

            // Insert a second control after the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";

            // Save the result
            doc.Save("output.docx");
            Console.WriteLine("Document saved with placeholder text set.");
        }
    }
}
```

Jalankan program dengan `dotnet run`. Setelah eksekusi, buka `output.docx` untuk memverifikasi bahwa kedua kontrol menampilkan placeholder masing‑masing.

## Next steps

* **Customize appearance** – Gunakan `sdt.Font` untuk mengubah ukuran font, warna, atau gaya di dalam kontrol.  
* **Bind to XML data** – Jelajahi `sdt.XmlMapping` jika Anda membutuhkan kontrol untuk memetakan

## What Should You Learn Next?

Tutorial berikut mencakup topik yang berhubungan erat dan membangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Create word document programmatically – add content control and placeholder](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Set Placeholder Text in Aspose.Words – Complete C# Guide](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Create new Word document and insert content control in C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}