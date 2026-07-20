---
category: general
date: 2026-07-19
description: Atur teks placeholder dalam StructuredDocumentTag dengan Aspose.Words.
  Pelajari cara menambahkan kontrol, berpindah ke kontrol, dan mengatur atribut tag
  dalam C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- move to control
- how to add control
- how to create sdt
- set tag attribute
language: id
lastmod: 2026-07-19
og_description: Atur teks placeholder dalam StructuredDocumentTag menggunakan Aspose.Words.
  Ikuti panduan langkah demi langkah ini untuk menambahkan kontrol, berpindah ke kontrol,
  dan mengatur atribut tag.
og_image_alt: Screenshot showing a Word document with placeholder text inside a content
  control created by Aspose.Words
og_title: Menetapkan Teks Placeholder di Aspose.Words – Tutorial C# Cepat
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Set placeholder text in a StructuredDocumentTag with Aspose.Words.
    Learn how to add control, move to control and set tag attribute in C#.
  headline: Set Placeholder Text in Aspose.Words – Complete C# Guide
  type: TechArticle
- description: Set placeholder text in a StructuredDocumentTag with Aspose.Words.
    Learn how to add control, move to control and set tag attribute in C#.
  name: Set Placeholder Text in Aspose.Words – Complete C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6+ (or .NET Framework 4.7.2) – the code works on any recent runtime.
      - Aspose.Words for .NET (NuGet package `Aspose.Words` version 23.12 or later).
      - A basic understanding of C# and Visual Studio (or your favorite IDE).'
  - name: Expected Result
    text: 'Open `SDTExample.docx` in Microsoft Word:'
  - name: What if I need a **dropdown** instead of plain text?
    text: Replace `SdtType.PlainText` with `SdtType.DropDownList` and populate the
      `ListItems` collection. The rest of the workflow—`InsertNode`, `MoveTo`, `SetTagAttribute`—remains
      the same.
  - name: Can I **set the tag attribute** after insertion?
    text: 'Absolutely. The `Tag` property can be modified at any time:'
  - name: How do I **find a control later** in a large document?
    text: Use the `Document.GetChildNodes(NodeType.StructuredDocumentTag, true)` method
      and filter by `Tag` or `Title`. This is handy when you need to replace placeholder
      text in bulk.
  - name: What if I want the placeholder to appear in **all languages**?
    text: Aspose.Words supports localized placeholder text via the `PlaceholderName`
      property. Set it to a resource string that varies per culture.
  type: HowTo
tags:
- Aspose.Words
- C#
- ContentControl
title: Mengatur Teks Placeholder di Aspose.Words – Panduan Lengkap C#
url: /id/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mengatur Teks Placeholder di Aspose.Words – Panduan Lengkap C#

Pernah bertanya-tanya bagaimana cara **mengatur teks placeholder** di dalam kontrol konten Word menggunakan Aspose.Words? Anda tidak sendirian. Baik Anda sedang membangun mesin pembuatan dokumen atau hanya membutuhkan templat yang dapat digunakan kembali, mengetahui cara menambahkan kontrol, berpindah ke kontrol, dan mengatur atribut tag sangat penting.

Dalam tutorial ini kami akan menelusuri contoh dunia nyata yang menunjukkan secara tepat cara membuat SDT (StructuredDocumentTag), memberi tag, mengatur teks placeholder, dan menulis konten default—semua dalam C# biasa. Pada akhir tutorial Anda akan memiliki potongan kode siap‑jalankan yang dapat Anda sisipkan ke proyek .NET mana pun.

## Apa yang Akan Anda Pelajari

- Cara **membuat SDT** (StructuredDocumentTag) secara programatis.  
- Cara yang tepat untuk **mengatur teks placeholder** agar pengguna melihat petunjuk yang membantu.  
- Menggunakan **move to control** untuk memposisikan kursor di dalam kontrol yang baru ditambahkan.  
- Menetapkan **atribut tag** untuk identifikasi di kemudian hari.  
- Menyimpan dokumen dan memverifikasi hasilnya.

### Prasyarat

- .NET 6+ (atau .NET Framework 4.7.2) – kode ini bekerja pada runtime terbaru apa pun.  
- Aspose.Words untuk .NET (paket NuGet `Aspose.Words` versi 23.12 atau lebih baru).  
- Pemahaman dasar tentang C# dan Visual Studio (atau IDE favorit Anda).

Tidak ada pustaka eksternal lain yang diperlukan.

## Langkah 1: Inisialisasi Dokumen dan Builder

Hal pertama yang harus dilakukan—buat `Document` kosong dan `DocumentBuilder`. Builder adalah kuas melukis Anda; dokumen adalah kanvasnya.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Create a brand‑new blank document.
Document document = new Document();

// DocumentBuilder lets us insert text, tables, and controls.
DocumentBuilder docBuilder = new DocumentBuilder(document);
```

> **Mengapa ini penting:** Memulai dengan `Document` yang bersih menjamin placeholder yang kita atur nanti tidak bentrok dengan konten yang sudah ada.

## Langkah 2: Buat StructuredDocumentTag (SDT)

Sekarang kita akan **cara membuat sdt** – sebuah kontrol konten yang dapat menampung teks biasa, tanggal, dropdown, dll. Dalam kasus ini kita membutuhkan kontrol teks biasa.

```csharp
// Create a plain‑text StructuredDocumentTag (content control).
StructuredDocumentTag plainTextSdt = new StructuredDocumentTag(
    document, SdtType.PlainText, true);

// Give the control a friendly name and a tag for later lookup.
plainTextSdt.Title = "CustomerName";
plainTextSdt.Tag   = "CustomerNameTag";

// Here’s the crucial part: set the placeholder text that the user sees.
plainTextSdt.PlaceholderText = "Enter name here";
```

> **Pro tip:** Properti `PlaceholderText` adalah apa yang dilihat pengguna sebelum mereka mengetik apa pun. Ini berbeda dari teks default yang mungkin Anda tulis kemudian.

## Langkah 3: Sisipkan Kontrol ke dalam Dokumen

Dengan SDT siap, kita perlu **cara menambahkan kontrol** ke dokumen. Metode `InsertNode` melakukan hal itu secara tepat.

```csharp
// Insert the content control at the current cursor position.
docBuilder.InsertNode(plainTextSdt);
```

> **Apa yang terjadi di balik layar?** `InsertNode` menempatkan SDT sebagai anak dari paragraf saat ini, mempertahankan format di sekitarnya.

## Langkah 4: Pindah ke Kontrol dan Tulis Konten Default (Opsional)

Jika Anda ingin mengisi kontrol dengan nilai sebelumnya (misalnya, nama pelanggan default), pertama‑tama **pindah ke kontrol** lalu menulis.

```csharp
// Optionally clear the placeholder and write a default name.
plainTextSdt.RemoveAllChildren();          // Remove the placeholder node.
docBuilder.MoveTo(plainTextSdt);           // Move cursor inside the SDT.
docBuilder.Write("John Doe");              // Write default text.
```

> **Mengapa kami menghapus placeholder:** Placeholder adalah petunjuk visual, bukan konten dokumen yang sebenarnya. Menghapusnya sebelum menulis memastikan dokumen akhir hanya berisi teks yang sesungguhnya.

## Langkah 5: Simpan Dokumen

Akhirnya, persistenkan file ke disk. Anda juga dapat mengirimnya sebagai aliran respons di aplikasi web—cukup ganti pemanggilan `Save`.

```csharp
// Save the Word document to the desired location.
document.Save("C:/Temp/SDTExample.docx");
```

### Hasil yang Diharapkan

Buka `SDTExample.docx` di Microsoft Word:

- Anda akan melihat kontrol konten teks biasa dengan judul **CustomerName**.  
- Kontrol menampilkan “Enter name here” sebagai teks placeholder yang samar (jika Anda tidak menulis konten default).  
- Jika Anda mempertahankan baris `Write("John Doe")`, “John Doe” muncul di dalam kontrol, dan placeholder menghilang.

## Contoh Kerja Lengkap

Berikut adalah program lengkap yang siap disalin‑tempel. Program ini mencakup semua langkah di atas, plus beberapa pemeriksaan defensif.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise document and builder.
        Document document = new Document();
        DocumentBuilder docBuilder = new DocumentBuilder(document);

        // 2️⃣ Create a plain‑text SDT (content control).
        StructuredDocumentTag plainTextSdt = new StructuredDocumentTag(
            document, SdtType.PlainText, true);
        plainTextSdt.Title = "CustomerName";
        plainTextSdt.Tag   = "CustomerNameTag";
        plainTextSdt.PlaceholderText = "Enter name here";

        // 3️⃣ Insert the control into the document.
        docBuilder.InsertNode(plainTextSdt);

        // 4️⃣ (Optional) Move to the control and set default text.
        plainTextSdt.RemoveAllChildren();   // Clear placeholder.
        docBuilder.MoveTo(plainTextSdt);    // Move cursor inside.
        docBuilder.Write("John Doe");       // Write default value.

        // 5️⃣ Save the file.
        string outputPath = @"C:\Temp\SDTExample.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Jalankan program, buka file yang dihasilkan, dan Anda akan melihat semuanya berfungsi persis seperti yang dijelaskan.

## Pertanyaan Umum & Kasus Tepi

### Bagaimana jika saya membutuhkan **dropdown** alih-alih teks biasa?

Ganti `SdtType.PlainText` dengan `SdtType.DropDownList` dan isi koleksi `ListItems`. Sisa alur kerja—`InsertNode`, `MoveTo`, `SetTagAttribute`—tetap sama.

### Bisakah saya **mengatur atribut tag** setelah penyisipan?

Tentu saja. Properti `Tag` dapat diubah kapan saja:

```csharp
plainTextSdt.Tag = "NewTagValue";
```

Ingatlah untuk menyimpan dokumen lagi agar perubahan tersebut bertahan.

### Bagaimana cara **menemukan kontrol nanti** dalam dokumen besar?

Gunakan metode `Document.GetChildNodes(NodeType.StructuredDocumentTag, true)` dan filter berdasarkan `Tag` atau `Title`. Ini berguna ketika Anda perlu mengganti teks placeholder secara massal.

```csharp
foreach (StructuredDocumentTag sdt in document.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    if (sdt.Tag == "CustomerNameTag")
    {
        // Do something with this control.
    }
}
```

### Bagaimana jika saya ingin placeholder muncul dalam **semua bahasa**?

Aspose.Words mendukung teks placeholder yang dilokalisasi melalui properti `PlaceholderName`. Atur properti ini ke string sumber daya yang berbeda per budaya.

## Tips & Trik (Pro Tips)

- **Gunakan kembali SDT yang sama** di banyak dokumen dengan mengkloningnya (`plainTextSdt.Clone(true)`), lalu sisipkan klon tersebut di tempat yang diperlukan.  
- **Hindari tag duplikat**; mereka membuat pencarian di kemudian hari menjadi ambigu. Jaga agar tag tetap unik per dokumen.  
- **Tip kinerja:** Jika Anda menghasilkan ribuan dokumen, gunakan satu instance `Document` sebagai templat dan hanya ganti teks placeholder. Ini mengurangi beban pembuatan objek.

## Kesimpulan

Kami telah membahas semua yang Anda perlukan untuk **mengatur teks placeholder** dalam StructuredDocumentTag Aspose.Words, mulai dari membuat kontrol, berpindah ke kontrol, menulis konten default, hingga menetapkan atribut tag. Dengan pengetahuan ini Anda dapat membangun templat Word dinamis yang memandu pengguna, menegakkan aturan entri data, dan tetap mudah dipelihara.

Siap untuk tantangan berikutnya? Cobalah mengganti SDT teks biasa dengan **date picker** atau **combo box**, atau jelajahi cara mengikat SDT ke sumber data XML untuk otomatisasi dokumen yang lebih kaya.

Selamat coding, semoga dokumen Anda selalu tertata sempurna!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Atur Gaya Kontrol Konten](/words/hindi/net/programming-with-sdt/set-content-control-style/)
- [Atur Warna Kontrol Konten](/words/hindi/net/programming-with-sdt/set-content-control-color/)
- [Cara membuat bidang formulir dan menambahkan konten menggunakan DocumentBuilder di Aspose.Words untuk Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}