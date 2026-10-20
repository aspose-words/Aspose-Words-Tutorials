---
category: general
date: 2026-09-11
description: Tambahkan kontrol konten dalam dokumen Word menggunakan Aspose.Words.
  Ikuti panduan langkah demi langkah ini untuk menyisipkan Structured Document Tag
  (SDT) teks biasa secara programatis.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add content control in word document
- StructuredDocumentTag
- DocumentBuilder
- Aspose.Words
- plain‑text SDT
- word automation
language: id
lastmod: 2026-09-11
og_description: Tambahkan kontrol konten dalam dokumen Word dengan Aspose.Words. Panduan
  ini menunjukkan cara menyisipkan Structured Document Tag (SDT) teks biasa secara
  programatis dan menyesuaikannya.
og_image_alt: Screenshot of a Word document showing a content control placeholder
og_title: Tambahkan kontrol konten di dokumen Word – tutorial lengkap Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Add content control in Word document using Aspose.Words. Follow this
    step‑by‑step guide to insert a plain‑text Structured Document Tag (SDT) programmatically.
  headline: Add content control in Word document with Aspose.Words
  type: TechArticle
tags:
- word
- content‑control
- csharp
- aspose
title: Tambahkan kontrol konten dalam dokumen Word dengan Aspose.Words
url: /id/java/document-manipulation/add-content-control-in-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tambahkan kontrol konten dalam dokumen Word dengan Aspose.Words

Jika Anda perlu **menambahkan kontrol konten dalam dokumen Word** secara programatis, tutorial ini menunjukkan secara tepat cara melakukannya dengan Aspose.Words untuk .NET. Baik Anda sedang membangun layanan pembuatan dokumen atau mengotomatiskan pembuatan formulir, Anda akan belajar cara menyisipkan Structured Document Tag (SDT) teks‑biasa dan memberi judul yang bermakna.

Dalam panduan ini Anda akan melihat contoh lengkap yang dapat dijalankan, mencakup setiap impor yang diperlukan, menjelaskan mengapa setiap panggilan API penting, dan mendemonstrasikan cara memverifikasi hasilnya. Tidak diperlukan referensi eksternal—cukup salin kode, jalankan, dan buka file *.docx* yang dihasilkan.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

* .NET 6.0 SDK atau yang lebih baru terpasang  
* Visual Studio 2022 (atau IDE C# apa pun)  
* Aspose.Words untuk .NET 23.5 atau lebih baru – Anda dapat memperoleh paket NuGet trial gratis  

Item‑item ini merupakan setup minimal untuk **otomasi Word** dengan Aspose.Words.

## Langkah 1: Siapkan proyek dan impor namespace

Buat proyek konsol baru dan tambahkan paket Aspose.Words:

```bash
dotnet new console -n ContentControlDemo
cd ContentControlDemo
dotnet add package Aspose.Words
```

Sekarang buka `Program.cs` dan tambahkan direktif `using` yang diperlukan:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Builders;
using Aspose.Words.Markup;
```

Namespace ini memberi Anda akses ke `DocumentBuilder`, `StructuredDocumentTag`, dan tipe inti lainnya yang dibutuhkan untuk **menambahkan kontrol konten dalam dokumen Word**.

## Langkah 2: Buat dokumen baru dan DocumentBuilder

`DocumentBuilder` adalah titik masuk utama untuk membangun file Word. Ia menyimpan kursor yang melacak di mana elemen berikutnya akan disisipkan.

```csharp
// Step 2: Initialize a new blank document and a builder
Document doc = new Document();                 // creates an empty .docx
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Mengapa ini penting*: Objek `Document` mewakili seluruh file Word, sementara `DocumentBuilder` menyederhanakan penyisipan paragraf, tabel, dan **kontrol konten** seperti Structured Document Tags.

## Langkah 3: Sisipkan Structured Document Tag (SDT) teks‑biasa

Inti solusi kita adalah metode `insertStructuredDocumentTag`. Metode ini membuat **kontrol konten** yang dapat menampung teks biasa, tanggal, dropdown, dll. Di sini kita menggunakan nilai enum `SdtType.PLAIN_TEXT`.

```csharp
// Step 3: Insert a plain‑text SDT at the current cursor position
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText,   // the type of control – plain‑text here
    true);               // true = the tag is shown as a placeholder in the UI
```

*Mengapa ini penting*: Menetapkan `true` membuat kontrol muncul sebagai placeholder berwarna abu‑abu muda, yang memberi sinyal kepada pengguna akhir bahwa mereka harus mengisi bidang tersebut.

## Langkah 4: Beri judul pada SDT untuk identifikasi selanjutnya

Judul (atau tag) memungkinkan Anda menemukan kontrol tersebut nanti, misalnya ketika Anda perlu mengganti isinya secara programatis.

```csharp
// Step 4: Assign a title so you can find the control later
sdt.Title = "CustomerName";
```

Judul tidak muncul di UI dokumen, tetapi disimpan dalam XML dasar dan dapat di‑query melalui API Aspose.Words.

## Langkah 5: Tambahkan teks placeholder di dalam SDT

Agar kontrol lebih ramah pengguna, sisipkan run default yang memberi tahu pengguna apa yang harus diketik.

```csharp
// Step 5: Add placeholder text inside the SDT
Run placeholder = new Run(builder.Document, "Enter name here");
sdt.AppendChild(placeholder);
```

*Mengapa ini penting*: Objek `Run` mewakili sepotong teks. Dengan menambahkannya ke SDT Anda menciptakan petunjuk visual yang menghilang begitu pengguna mulai mengetik.

## Langkah 6: Simpan dokumen

Akhirnya, tulis dokumen ke disk sehingga Anda dapat membukanya di Microsoft Word.

```csharp
// Step 6: Save the finished document
string outPath = "ContentControlExample.docx";
doc.Save(outPath);
Console.WriteLine($"Document saved to {outPath}");
```

Saat Anda membuka `ContentControlExample.docx`, Anda akan melihat kontrol konten berbayang abu‑abu dengan judul **CustomerName** dan teks placeholder *Enter name here*.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin‑tempel ke `Program.cs`. Program ini mencakup semua langkah, komentar, dan penanganan error yang diperlukan.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Builders;
using Aspose.Words.Markup;

namespace ContentControlDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new empty document
            Document doc = new Document();

            // Initialize the DocumentBuilder – this controls where we insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a plain‑text Structured Document Tag (SDT)
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,   // type of content control
                true);               // show as placeholder

            // Assign a title for later lookup (not visible in the UI)
            sdt.Title = "CustomerName";

            // Add placeholder text that instructs the user
            Run placeholder = new Run(builder.Document, "Enter name here");
            sdt.AppendChild(placeholder);

            // Save the document to the file system
            string outPath = "ContentControlExample.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Output yang diharapkan

Menjalankan program mencetak:

```
Document saved to ContentControlExample.docx
```

Membuka file yang dihasilkan di Word menampilkan satu kontrol konten dengan placeholder abu‑abu **Enter name here**. Kontrol tersebut dapat diedit, dihapus, atau diakses secara programatis nanti menggunakan judul *CustomerName*.

## Variasi umum dan kasus tepi

| Skenario | Cara menyesuaikan kode |
|----------|------------------------|
| **Beberapa kontrol konten** | Panggil `InsertStructuredDocumentTag` berulang kali, berikan `Title` yang unik setiap kali. |
| **Kontrol konten rich‑text** | Gunakan `SdtType.RichText` alih‑alih `PlainText`. |
| **Kontrol pemilih tanggal** | Gunakan `SdtType.Date` dan opsional atur `sdt.DateDisplayFormat`. |
| **Mengunci kontrol** | Set `sdt.LockContentControl = true` untuk mencegah pengguna menghapusnya. |
| **Menemukan kontrol nanti** | Gunakan `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` dan filter berdasarkan `Title`. |

Variasi‑variasi ini menggambarkan fleksibilitas **Aspose.Words** ketika Anda perlu **menambahkan kontrol konten dalam dokumen Word** untuk berbagai skenario pengisian formulir.

## Tips profesional

* **Kinerja** – Jika Anda menghasilkan banyak dokumen dalam sebuah loop, gunakan kembali satu instance `DocumentBuilder` dan panggil `doc.Clone()` untuk setiap iterasi guna menghindari pembuatan objek berulang.  
* **Styling** – Anda dapat menerapkan `ParagraphFormat` atau `Font` pada `Run` placeholder agar sesuai dengan tema visual dokumen Anda.  
* **Validasi** – Setelah menyisipkan kontrol, Anda dapat memeriksa `sdt.IsShowingPlaceholderText` untuk memastikan placeholder ditampilkan dengan benar.  

## Kesimpulan

Anda kini tahu cara **menambahkan kontrol konten dalam dokumen Word** dengan Aspose.Words, mulai dari membuat `DocumentBuilder` hingga menyisipkan `StructuredDocumentTag` teks‑biasa, memberi judul, dan menambahkan teks placeholder. Contoh lengkap dapat diperluas ke tipe SDT lain, banyak kontrol, serta opsi penguncian atau styling lanjutan.

Siap melangkah lebih jauh? Jelajahi topik terkait berikut:

* **Bekerja dengan tabel di dalam kontrol konten** – gunakan `DocumentBuilder.InsertTable` setelah SDT.  
* **Mengekstrak data dari kontrol yang telah diisi** – ambil node `Sdt` berdasarkan judul dan baca properti `Text`‑nya.  
* **Menggunakan OpenXML SDK** – pendekatan alternatif jika Anda lebih menyukai perpustakaan gratis yang didukung Microsoft.

Cobalah kode tersebut, sesuaikan dengan alur kerja pembuatan formulir Anda, dan nikmati kekuatan otomasi Word secara programatis.


## Apa yang Harus Anda Pelajari Selanjutnya?


Tutorial berikut mencakup topik yang berhubungan erat dan membangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang dapat dijalankan dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}