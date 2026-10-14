---
category: general
date: 2026-10-13
description: Buat dokumen Word baru di C# dan sisipkan kontrol konten dengan teks
  placeholder. Pelajari cara mengatur teks placeholder dan menyimpan dokumen Word
  secara efisien.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create new word document
- insert content control
- set placeholder text
- how to create sdt
- save word document c#
language: id
lastmod: 2026-10-13
og_description: Buat dokumen Word baru di C# dengan Aspose.Words, sisipkan kontrol
  konten, atur teks placeholder, dan simpan dokumen Word—semua dalam satu panduan.
og_image_alt: Screenshot of a Word document showing a content control placeholder
og_title: Buat dokumen Word baru dan sisipkan kontrol konten di C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  headline: Create new Word document and insert content control in C#
  type: TechArticle
- description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  name: Create new Word document and insert content control in C#
  steps:
  - name: Run the console app.
    text: Run the console app.
  - name: Open `output.docx` in Microsoft Word.
    text: Open `output.docx` in Microsoft Word.
  - name: Verify that the placeholder text appears inside a gray‑shaded box.
    text: Verify that the placeholder text appears inside a gray‑shaded box.
  - name: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
    text: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
  type: HowTo
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: Buat dokumen Word baru dan sisipkan kontrol konten di C#
url: /id/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Membuat dokumen Word baru dan menyisipkan kontrol konten di C#

Jika Anda perlu **membuat dokumen Word baru** secara programatis, panduan ini menunjukkan cara melakukannya dengan Aspose.Words untuk .NET. Anda akan belajar cara **menyisipkan kontrol konten**, menetapkan **teks placeholder**, dan akhirnya **menyimpan dokumen Word C#** kode yang dapat Anda salin ke dalam proyek Anda.

Tutorial ini melangkah melalui setiap langkah, menjelaskan mengapa setiap panggilan API penting, dan mencakup variasi umum seperti menambahkan SDT teks‑rich atau menangani dokumen yang sudah ada. Pada akhir tutorial Anda akan memiliki contoh lengkap yang dapat dijalankan dan dapat Anda sesuaikan untuk faktur, kontrak, atau output Word berbasis templat apa pun.

## Prasyarat

* .NET 6.0 atau lebih baru (kode ini juga berfungsi dengan .NET Framework 4.7+)
* Paket NuGet Aspose.Words untuk .NET (`Install-Package Aspose.Words`)
* IDE seperti Visual Studio 2022 atau Visual Studio Code

Tidak ada pustaka tambahan yang diperlukan.

## Membuat dokumen Word baru dengan Aspose.Words

Langkah pertama adalah menginstansiasi objek `Document`. Objek ini mewakili file Word kosong di memori.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Step 1: Create a new, empty document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` memberikan API yang fluent untuk menyisipkan elemen pada posisi kursor saat ini. Karena dokumen kosong, kursor mulai di awal bagian pertama (dan satu‑satunya).

## Menyisipkan kontrol konten (StructuredDocumentTag)

Sebuah **kontrol konten** di Word disebut Structured Document Tag (SDT). Kode berikut membuat SDT teks‑plain, menetapkan judulnya, dan mendefinisikan teks placeholder yang muncul ketika pengguna membuka file.

```csharp
// Step 2: Create a plain‑text StructuredDocumentTag (SDT)
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Title is used for identification in the document outline
    Title = "CustomerName",
    // Placeholder text is visible until the user types a value
    PlaceholderName = "Enter name here"
};

// Step 3: Insert the SDT at the builder's current insertion point
builder.InsertNode(sdt);
```

**Mengapa ini penting:**  
* `SdtType.PlainText` membatasi konten ke satu baris teks biasa, yang ideal untuk bidang sederhana seperti nama atau email.  
* Menetapkan `PlaceholderName` memberikan petunjuk visual (`Enter name here`) yang membimbing pengguna akhir.  

Jika Anda memerlukan bidang yang lebih kaya (mis., teks multi‑baris atau pemilih tanggal), ganti `SdtType.PlainText` dengan `SdtType.RichText` atau `SdtType.Date`.

## Menambahkan teks di sekeliling (opsional)

Sebagian besar templat menyertakan label sebelum kontrol konten. Anda dapat menambahkannya dengan instance `DocumentBuilder` yang sama:

```csharp
// Optional: add a label before the content control
builder.Writeln("Customer Name:");
builder.InsertNode(sdt);   // Re‑insert the SDT after the label
```

File Word yang dihasilkan menampilkan:

```
Customer Name: [Enter name here]
```

## Menyimpan dokumen Word gaya C#

Akhirnya, tulis dokumen ke disk. Aspose.Words secara otomatis menentukan format dari ekstensi file.

```csharp
// Step 4: Save the document to verify the result
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Saat Anda membuka `output.docx` di Microsoft Word, Anda akan melihat teks placeholder di dalam kontrol konten berbayang abu‑abu. Pengguna dapat mengklik kontrol tersebut dan mengganti placeholder dengan nilai mereka sendiri.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program konsol mandiri yang menggabungkan semuanya. Salin kode ke dalam proyek konsol baru dan jalankan.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Add a descriptive label
            builder.Writeln("Customer Name:");

            // Create and configure a plain‑text content control (SDT)
            StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
            {
                Title = "CustomerName",
                PlaceholderName = "Enter name here"
            };

            // Insert the SDT after the label
            builder.InsertNode(sdt);

            // Save the document
            string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Output yang diharapkan** (konsol):

```
Document saved to C:\YourProject\bin\Debug\net6.0\output.docx
```

Membuka `output.docx` menampilkan satu baris dengan label *Customer Name:* diikuti oleh kontrol konten yang menampilkan *Enter name here*.

## Variasi umum dan kasus tepi

| Scenario | Code change | Reason |
|----------|-------------|--------|
| **Rich‑text field** | `new StructuredDocumentTag(doc, SdtType.RichText, true)` | Memungkinkan input multi‑baris dan pemformatan dasar. |
| **Read‑only control** | `sdt.LockContentControl = true;` | Mencegah pengguna mengedit konten kontrol. |
| **Pre‑populate with data** | `sdt.AppendChild(new Run(doc, "John Doe"));` | Menyisipkan nilai default yang menimpa placeholder. |
| **Add to an existing document** | Load with `new Document("template.docx")` instead of an empty `Document` | Memungkinkan skenario templating di mana kontrol ditempatkan dalam tata letak yang telah ditentukan. |
| **Multiple controls** | Repeat the creation block with different titles and placeholders | Berguna untuk formulir yang mengumpulkan beberapa informasi. |

### Tips profesional

Saat menghasilkan dokumen besar, gunakan kembali satu instance `DocumentBuilder` alih‑alih membuat yang baru untuk setiap kontrol. Ini mengurangi beban memori dan meningkatkan kinerja.

## Menguji hasil

1. Jalankan aplikasi konsol.  
2. Buka `output.docx` di Microsoft Word.  
3. Verifikasi bahwa teks placeholder muncul di dalam kotak berbayang abu‑abu.  
4. Klik kotak, ketik nama, dan simpan file. Teks yang dimasukkan menggantikan placeholder.

Jika placeholder tidak muncul, pastikan Anda menggunakan Aspose.Words versi 23.9 atau lebih baru, karena rilis lama memiliki bug dengan `PlaceholderName` pada SDT teks‑plain.

## Kesimpulan

Anda sekarang tahu cara **membuat dokumen Word baru**, **menyisipkan kontrol konten**, **menetapkan teks placeholder**, dan **menyimpan dokumen Word C#** menggunakan Aspose.Words. Contoh lengkap menunjukkan pola standar, dan tabel variasi memperlihatkan cara menyesuaikan solusi untuk skenario yang lebih kaya.

Selanjutnya, Anda mungkin ingin menjelajahi:

* **Menyisipkan kontrol konten untuk tanggal** – gunakan enumerasi `SdtType.Date`.  
* **Mengisi templat dengan data** – gabungkan `StructuredDocumentTag` dengan bidang mail‑merge.  
* **Ekspor ke PDF** – panggil `doc.Save("output.pdf")` setelah menambahkan kontrol.

Silakan bereksperimen dengan berbagai tipe SDT, pengaturan kunci, dan gaya untuk menyesuaikan kebutuhan proyek Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Dokumen Word Baru](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Sisipkan Formulir Input Teks di Dokumen Word](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Buat Dokumen Word dengan Aspose.Words untuk .NET](/words/english/net/add-content-using-documentbuilder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}