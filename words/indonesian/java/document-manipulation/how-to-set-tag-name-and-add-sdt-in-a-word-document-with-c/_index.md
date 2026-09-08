---
category: general
date: 2026-09-08
description: Tetapkan nama tag dan buat kontrol konten (SDT) dalam dokumen Word menggunakan
  C#. Pelajari cara menambahkan SDT, menulis teks ke tag, dan memodifikasi dokumen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set tag name
- how to add sdt
- modify word document
- create content control
- write text to tag
language: id
lastmod: 2026-09-08
og_description: Tetapkan nama tag dan buat kontrol konten (SDT) dalam dokumen Word
  menggunakan C#. Ikuti panduan langkah demi langkah ini untuk menambahkan SDT, menulis
  teks ke tag, dan memodifikasi dokumen.
og_image_alt: Screenshot showing a Word document with a StructuredDocumentTag whose
  tag name is set
og_title: Atur nama tag dan tambahkan SDT dalam dokumen Word – panduan C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Set tag name and create a content control (SDT) in a Word document
    using C#. Learn how to add SDT, write text to tag, and modify the document.
  headline: How to set tag name and add SDT in a Word document with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Cara mengatur nama tag dan menambahkan SDT dalam dokumen Word dengan C#
url: /id/java/document-manipulation/how-to-set-tag-name-and-add-sdt-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengatur nama tag dan menambahkan SDT dalam dokumen Word dengan C#

Jika Anda perlu **mengatur nama tag** untuk StructuredDocumentTag (SDT) saat bekerja dengan file Word, panduan ini menunjukkan secara tepat caranya. Anda akan melihat contoh lengkap yang dapat dijalankan yang **membuat kontrol konten**, menulis teks ke tag, dan **memodifikasi dokumen Word** dari awal hingga akhir.

Pengembang sering bertanya, *“bagaimana menambahkan sdt* ke .docx yang ada dan kemudian *menulis teks ke tag*?” – jawabannya terletak pada penggunaan API Aspose.Words untuk .NET. Pada akhir tutorial ini Anda akan dapat membuka file Word, menyisipkan SDT teks biasa, mengatur nama tagnya, mengisinya dengan konten, dan menyimpan perubahan tanpa meninggalkan sumber daya yang menggantung.

## Prasyarat

* .NET 6.0 atau lebih baru terinstal.
* Lisensi Aspose.Words untuk .NET yang valid (atau Anda dapat menggunakan versi evaluasi).
* Visual Studio 2022 (atau IDE apa pun yang mendukung C#).
* Dokumen Word input (`input.docx`) yang ditempatkan di folder yang dapat Anda referensikan dari kode.

## Langkah 1: Siapkan proyek dan impor namespace

Buat proyek Console App baru dan tambahkan paket NuGet Aspose.Words:

```bash
dotnet new console -n WordSdtDemo
cd WordSdtDemo
dotnet add package Aspose.Words
```

Kemudian, tambahkan direktif `using` yang diperlukan di bagian atas `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;
```

Namespace ini memberi Anda akses ke kelas `Document`, `DocumentBuilder`, dan `StructuredDocumentTag`, yang penting untuk **memodifikasi dokumen Word**.

## Langkah 2: Muat dokumen Word yang ada

Operasi pertama adalah memuat file yang ingin Anda edit. Langkah ini diperlukan untuk setiap skenario di mana Anda **memodifikasi konten dokumen Word**.

```csharp
// Load an existing Word document from disk
string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
Console.WriteLine($"Loaded document: {inputPath}");
```

> **Mengapa kita memuat dokumen terlebih dahulu** – Objek `Document` mewakili seluruh paket .docx dalam memori. Hanya setelah dimuat Anda dapat menyisipkan node baru seperti SDT dengan aman.

## Langkah 3: Sisipkan StructuredDocumentTag (SDT) dan atur nama tagnya

Sekarang kami menjawab pertanyaan utama: **bagaimana menambahkan sdt** dan **mengatur nama tag**. Kami menggunakan `DocumentBuilder.InsertStructuredDocumentTag` dengan `SdtType.PlainText`. Argumen kedua adalah nama tag, yang dapat Anda referensikan secara programatis atau melalui UI Word nanti.

```csharp
// Create a DocumentBuilder attached to the loaded document
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a plain‑text StructuredDocumentTag (content control) at the cursor position
// The second parameter ("MyTag") is the tag name we are setting.
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Confirm that the tag name has been set
Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");
```

> **Penjelasan** – `InsertStructuredDocumentTag` mengembalikan instance `StructuredDocumentTag`. Dengan memberikan `"MyTag"` kami **mengatur nama tag** secara langsung pada saat pembuatan. Jika Anda perlu mengubahnya nanti, Anda dapat menetapkan nilai baru ke `sdt.Tag`.

## Langkah 4: Tulis teks ke tag yang baru dibuat

Setelah SDT ada, biasanya Anda ingin **menulis teks ke tag** sehingga pengguna akhir melihat placeholder atau konten default. Metode `SetText` melakukan hal itu.

```csharp
// Populate the SDT with sample content
sdt.SetText("Sample content");

// Optionally, you can also set the placeholder text that appears when the tag is empty
sdt.PlaceholderName = "Enter your text here";
Console.WriteLine("Text written to the SDT.");
```

> **Mengapa menggunakan SetText** – Menetapkan langsung ke properti `Text` akan menggantikan seluruh hierarki node. `SetText` dengan aman memperbarui teks dalam kontrol konten sambil mempertahankan strukturnya.

## Langkah 5: Simpan dokumen yang telah dimodifikasi

Akhirnya, simpan perubahan ke file baru. Ini menyelesaikan alur kerja **memodifikasi dokumen Word**.

```csharp
// Define the output path
string outputPath = @"YOUR_DIRECTORY\output.docx";

// Save the document with the inserted content control
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Saat Anda membuka `output.docx` di Microsoft Word, Anda akan melihat kontrol konten teks biasa berlabel **MyTag** yang berisi teks “Sample content”. Kontrol tersebut dapat diedit secara manual, dan nama tag tetap dapat diakses melalui alat pengembang Word.

## Kode sumber lengkap

Berikut adalah program lengkap yang berdiri sendiri. Salin ke `Program.cs` dan jalankan; tidak diperlukan potongan kode tambahan.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the existing Word document
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(inputPath);
            Console.WriteLine($"Loaded document: {inputPath}");

            // 2️⃣ Create a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and set its tag name
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText, "MyTag");
            Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");

            // 4️⃣ Write text to the tag (and optionally set a placeholder)
            sdt.SetText("Sample content");
            sdt.PlaceholderName = "Enter your text here";
            Console.WriteLine("Text written to the SDT.");

            // 5️⃣ Save the modified document
            string outputPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Output yang diharapkan di konsol

```
Loaded document: YOUR_DIRECTORY\input.docx
Inserted SDT with tag name: MyTag
Text written to the SDT.
Document saved to: YOUR_DIRECTORY\output.docx
```

### Tampilan file Word yang dihasilkan

![Dokumen Word yang menampilkan kontrol konten bernama MyTag dengan teks “Sample content”](/images/word-sdt-example.png){: .img-fluid alt="Contoh mengatur nama tag dalam dokumen Word"}

*Tangkapan layar ini menggambarkan SDT dengan **nama tag** yang diatur menjadi *MyTag* dan teks yang disematkan terlihat.*

## Variasi umum dan kasus tepi

| Situasi | Cara menanganinya |
|-----------|------------------|
| **Buat SDT teks kaya** | Gunakan `SdtType.RichText` alih-alih `PlainText`. |
| **Atur nama tag yang berbeda setelah penyisipan** | `sdt.Tag = "NewTag";` – Anda dapat menetapkan kembali nama tag kapan saja. |
| **Tambahkan SDT di dalam paragraf tertentu** | Pindahkan kursor builder (`builder.MoveToParagraph(index)`) sebelum memanggil `InsertStructuredDocumentTag`. |
| **Beberapa SDT dalam dokumen yang sama** | Ulangi langkah 3‑4 untuk setiap kontrol; masing‑masing dapat memiliki nama tag unik. |
| **Bekerja dengan dokumen yang dilindungi** | Pastikan dokumen tidak dilindungi (`doc.Unprotect()`) sebelum menyisipkan SDT. |

## Tips profesional untuk otomasi Word yang kuat

* **Lisensi lebih awal** – Panggil `Aspose.Words.License license = new Aspose.Words.License(); license.SetLicense("Aspose.Words.lic");` di awal `Main` untuk menghindari watermark evaluasi.
* **Dispose objek** – Bungkus `Document` dalam blok `using` jika Anda menargetkan .NET Framework untuk menjamin handle file dilepaskan.
* **Validasi keberadaan tag** – Saat membaca dokumen nanti, gunakan `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` untuk menemukan tag berdasarkan properti `Tag`.
* **Kinerja** – Untuk dokumen besar, muat hanya bagian yang diperlukan menggunakan `LoadOptions` dengan `LoadFormat.Docx` dan `LoadFormat.Auto`.  

## Kesimpulan

Anda sekarang tahu cara **mengatur nama tag**, **membuat kontrol konten**, **menulis teks ke tag**, dan **memodifikasi dokumen Word** menggunakan C#. Contoh lengkap ini menunjukkan pola standar untuk **bagaimana menambahkan sdt** dan menyimpan perubahan dengan aman.  

Dari sini

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Tambahkan Konten Menggunakan Document Builder di Aspose.Words untuk .NET](/words/english/net/add-content-using-document-builder/)
- [Dokumen Word - Cara Menghapus Konten](/words/english/net/remove-content/)
- [Buat Dokumen Word dengan Aspose.Words – Panduan Langkah‑per‑Langkah](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}