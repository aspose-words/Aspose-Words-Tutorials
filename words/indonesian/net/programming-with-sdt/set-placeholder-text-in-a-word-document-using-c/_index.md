---
category: general
date: 2026-10-20
description: Atur teks placeholder dalam dokumen Word menggunakan C#. Pelajari cara
  menambahkan kontrol dan mengatur placeholder dengan cepat menggunakan Aspose.Words
  untuk .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- how to add control
- how to set placeholder
- generate word c#
language: id
lastmod: 2026-10-20
og_description: Atur teks placeholder dalam dokumen Word dengan C#. Tutorial ini menunjukkan
  cara menambahkan kontrol, mengatur placeholder, dan menghasilkan file Word secara
  programatis.
og_image_alt: Screenshot of a Word document showing placeholder text created with
  C# code
og_title: Atur teks placeholder dalam dokumen Word dengan C# – panduan langkah demi
  langkah
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Set placeholder text in a Word document using C#. Learn how to add
    control and set placeholder quickly with Aspose.Words for .NET.
  headline: Set placeholder text in a Word document using C#
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, and .NET
      6+. The same code runs unchanged.
    question: Does this work with .NET Core?
  - answer: Use `sdt.SetText("Default value")` after creating the SDT. The placeholder
      disappears once a value is set.
    question: Can I set a default value in addition to the placeholder?
  - answer: 'Load the document, locate the SDT by its `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag,
      true)`) and read `sdt.GetText()`. ## Conclusion You now know how to **set placeholder
      text** in a Word document using C#. By creating a plain‑text `StructuredDocumentTag`,
      assigning a title and place'
    question: What if I need to retrieve the entered value later?
  type: FAQPage
tags:
- C#
- Aspose.Words
- Word automation
- Content control
title: Atur teks placeholder dalam dokumen Word menggunakan C#
url: /id/net/programming-with-sdt/set-placeholder-text-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menetapkan teks placeholder dalam dokumen Word menggunakan C#

Jika Anda perlu **set placeholder text** dalam file Microsoft Word saat menghasilkan dengan C#, panduan ini menunjukkan secara tepat cara melakukannya. Anda akan melihat solusi singkat, end‑to‑end yang menambahkan content control, mendefinisikan placeholder‑nya, dan menyimpan dokumen—semua dengan Aspose.Words untuk .NET.

Banyak pengembang bertanya **how to add control** ke dokumen Word atau **how to set placeholder** tanpa membuka Word secara manual. Tutorial ini menjawab pertanyaan‑pertanyaan tersebut dan juga mendemonstrasikan cara bersih untuk **generate Word C#** file yang siap untuk input pengguna.

## Apa yang akan Anda capai

* Membuat dokumen Word kosong secara programatis.  
* Menyisipkan Structured Document Tag (SDT) teks‑plain, yang merupakan nama teknis untuk content control.  
* Menetapkan judul yang bermakna dan teks placeholder ke SDT.  
* Menyimpan file `.docx` yang dihasilkan ke disk.

Tidak ada alat tambahan yang diperlukan selain pustaka Aspose.Words dan lingkungan pengembangan .NET 6 (atau lebih baru).

## Prasyarat

* .NET 6 SDK atau yang lebih baru terpasang.  
* Visual Studio 2022 (atau IDE apa pun yang mendukung .NET).  
* Paket NuGet Aspose.Words untuk .NET (`Install-Package Aspose.Words`).  

> **Pro tip:** Gunakan versi evaluasi gratis Aspose.Words jika Anda hanya menguji; versi ini menambahkan watermark tetapi berfungsi sama seperti versi berlisensi.

## Langkah 1: Siapkan proyek dan impor namespace

Buat proyek konsol baru dan tambahkan direktif `using` yang diperlukan. Direktif ini membawa kelas inti Aspose.Words dan namespace markup ke dalam ruang lingkup.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // The complete solution starts here.
        }
    }
}
```

*Why this step matters:* Mengimpor `Aspose.Words.Markup` memberi Anda akses ke `StructuredDocumentTag`, `SdtType`, dan `MarkupLevel`—objek‑objek yang diperlukan untuk **add control** dan **set placeholder**.

## Langkah 2: Buat dokumen kosong dan DocumentBuilder

`Document` mewakili seluruh file Word, sementara `DocumentBuilder` menyediakan kursor yang nyaman untuk menyisipkan elemen.

```csharp
// Step 2: Initialize a new empty document.
Document doc = new Document();

// DocumentBuilder starts at the beginning of the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this step matters:* Memulai dengan dokumen bersih memastikan placeholder yang Anda tetapkan muncul tepat di tempat yang Anda inginkan, tanpa gangguan dari konten yang sudah ada.

## Langkah 3: Buat content control (Structured Document Tag)

Di sini kami membuat SDT teks‑plain, memberi judul, dan menetapkan teks placeholder yang akan dilihat pengguna ketika kontrol kosong.

```csharp
// Step 3: Build a plain‑text Structured Document Tag (SDT).
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,                     // Parent document
    SdtType.PlainText,       // Control type – plain text box
    MarkupLevel.Inline);     // Inline placement (behaves like a word)

sdt.Title = "CustomerName";                 // Logical name for the control
sdt.PlaceholderName = "Enter name here";    // Text shown when empty
```

*Why this step matters:* Properti `Title` memungkinkan Anda merujuk kontrol nanti (misalnya, untuk data binding). `PlaceholderName` adalah tepat **set placeholder text** yang ingin Anda tampilkan, membimbing pengguna akhir.

## Langkah 4: Sisipkan kontrol pada posisi kursor saat ini

Dengan menggunakan `DocumentBuilder`, sisipkan SDT ke dalam dokumen pada posisi di mana builder saat ini berada.

```csharp
// Step 4: Insert the SDT into the document.
builder.InsertNode(sdt);
```

*Why this step matters:* Menyisipkan node menautkan kontrol ke DOM dokumen. Jika Anda perlu menambahkan beberapa placeholder, Anda dapat memindahkan kursor builder dan mengulangi langkah ini.

## Langkah 5: Simpan dokumen

Akhirnya, tulis dokumen ke disk. Ganti `YOUR_DIRECTORY` dengan jalur aktual di mesin Anda.

```csharp
// Step 5: Save the .docx file.
string outputPath = @"C:\Temp\SDT.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Saat Anda membuka `SDT.docx` di Microsoft Word, Anda akan melihat kotak teks inline berbayang abu‑abu yang berisi **Enter name here**. Mengklik di dalam kotak menghapus placeholder, memungkinkan pengguna mengetik nama pelanggan.

### Output yang diharapkan

| Lokasi file | Pratinjau konten |
|-------------|------------------|
| `C:\Temp\SDT.docx` | Placeholder inline **Enter name here** di dalam content control teks‑plain dengan judul *CustomerName*. |

## Kasus tepi dan variasi

| Situasi | Penyesuaian yang disarankan |
|---------|-----------------------------|
| **Multiple placeholders** | Buat objek `StructuredDocumentTag` tambahan dengan nilai `Title` dan `PlaceholderName` yang berbeda, lalu sisipkan masing‑masing di tempat yang dibutuhkan. |
| **Rich‑text placeholder** | Gunakan `SdtType.RichText` alih‑alih `PlainText` untuk memungkinkan pemformatan di dalam placeholder. |
| **Block‑level control** | Ubah `MarkupLevel.Inline` menjadi `MarkupLevel.Block` agar kontrol berperilaku seperti paragraf penuh. |
| **Placeholder not visible** | Pastikan pengaturan tampilan dokumen di Word tidak diset untuk menyembunyikan content control (`File → Options → Advanced → Show content controls`). |
| **Saving to a stream** | Panggil `doc.Save(stream, SaveFormat.Docx)` jika Anda perlu mengirim file melalui HTTP alih‑alih menulis ke disk. |

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin, tempel, dan jalankan. Program ini mencakup semua langkah di atas dalam satu metode `Main`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Position a builder at the start of the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Define a plain‑text content control (SDT) with placeholder text.
            StructuredDocumentTag sdt = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Inline);

            sdt.Title = "CustomerName";                 // Logical identifier
            sdt.PlaceholderName = "Enter name here";    // The placeholder you see in Word

            // 4️⃣ Insert the SDT into the document.
            builder.InsertNode(sdt);

            // 5️⃣ Save the document to disk.
            string outputPath = @"C:\Temp\SDT.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document successfully saved to {outputPath}");
        }
    }
}
```

Jalankan program, buka file yang dihasilkan, dan Anda akan melihat teks placeholder siap untuk input pengguna.

## Pertanyaan umum terjawab

**Q: Apakah ini bekerja dengan .NET Core?**  
A: Ya. Aspose.Words untuk .NET kompatibel dengan .NET Core, .NET 5, dan .NET 6+. Kode yang sama berjalan tanpa perubahan.

**Q: Bisakah saya menetapkan nilai default selain placeholder?**  
A: Gunakan `sdt.SetText("Default value")` setelah membuat SDT. Placeholder akan menghilang begitu nilai ditetapkan.

**Q: Bagaimana jika saya perlu mengambil nilai yang dimasukkan nanti?**  
A: Muat dokumen, temukan SDT berdasarkan `Title`‑nya (`doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`) dan baca `sdt.GetText()`.

## Kesimpulan

Anda kini tahu cara **set placeholder text** dalam dokumen Word menggunakan C#. Dengan membuat `StructuredDocumentTag` teks‑plain, menetapkan judul dan placeholder, menyisipkannya dengan `DocumentBuilder`, dan menyimpan file, Anda dapat **add control** dan **generate Word C#** secara programatis.  

Dari sini Anda dapat mengeksplor:

* Menambahkan kontrol rich‑text atau dropdown list (`SdtType.RichText`, `SdtType.DropDownList`).  
* Mengisi banyak placeholder dari basis data.  
* Mengonversi `.docx` yang dihasilkan ke PDF dengan Aspose.Words.

Cobalah berbagai tipe kontrol dan gaya placeholder untuk menyesuaikan kebutuhan aplikasi Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait dan membangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Set Placeholder Text in Aspose.Words – Complete C# Guide](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Create word document programmatically – add content control and placeholder](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [How to Add Content Control and Create Word Document with Aspose – Complete](/words/english/net/programming-with-sdt/how-to-add-content-control-and-create-word-document-with-asp/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}