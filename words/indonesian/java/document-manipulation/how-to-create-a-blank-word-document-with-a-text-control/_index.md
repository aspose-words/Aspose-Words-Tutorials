---
category: general
date: 2026-09-21
description: Pelajari cara membuat dokumen Word kosong, menambahkan kontrol teks biasa,
  mengatur teks placeholder, dan menyimpan file docx menggunakan Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set placeholder text
- save docx file
- add plain text control
language: id
lastmod: 2026-09-21
og_description: Buat dokumen Word kosong, tambahkan kontrol teks biasa, atur teks
  placeholder, dan simpan file docx dengan Aspose.Words. Ikuti tutorial lengkap ini.
og_image_alt: Screenshot showing a blank Word document created to set placeholder
  text in a text control
og_title: Buat dokumen Word kosong dan tambahkan kontrol teks – panduan langkah demi
  langkah
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create a blank Word document, add a plain text control,
    set placeholder text, and save the docx file using Aspose.Words.
  headline: How to create a blank Word document with a text control
  type: TechArticle
tags:
- Aspose.Words
- Word automation
- .NET
- Document generation
title: Cara membuat dokumen Word kosong dengan kontrol teks
url: /id/java/document-manipulation/how-to-create-a-blank-word-document-with-a-text-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat dokumen Word kosong dengan kontrol teks

Jika Anda perlu **membuat dokumen Word kosong** secara programatik, panduan ini menunjukkan cara melakukannya secara tepat. Anda akan melihat cara menambahkan kontrol teks biasa, mengatur teks placeholder, dan akhirnya **menyimpan file docx** ke disk.

Pada bagian di bawah ini Anda akan mempelajari alur kerja lengkap, mulai dari inisialisasi dokumen hingga memverifikasi bahwa placeholder muncul ketika file dibuka di Microsoft Word. Langkah‑langkah ini bekerja dengan Aspose.Words .NET 2024‑R2, tetapi konsepnya berlaku untuk pustaka pembuatan dokumen .NET apa pun.

## Apa yang Anda perlukan

- .NET 6.0 atau yang lebih baru (kode juga dapat dijalankan pada .NET Framework 4.8)  
- Aspose.Words untuk .NET (paket NuGet `Aspose.Words`)  
- IDE seperti Visual Studio atau VS Code  
- Pengetahuan dasar C#  

> **Pro tip:** Instal paket NuGet dengan `dotnet add package Aspose.Words` untuk menjaga proyek Anda tetap rapi.

## Langkah 1: Buat dokumen Word kosong

Operasi pertama adalah menginstansiasi `Document` kosong. Objek ini mewakili **dokumen Word kosong** yang tidak berisi bagian, paragraf, atau gaya apa pun.

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

// Create a new blank document
Document doc = new Document();
```

Membuat dokumen kosong memberi Anda kanvas bersih, yang penting ketika Anda menginginkan kontrol penuh atas tata letak kontrol yang disisipkan.

## Langkah 2: Tambahkan kontrol teks biasa

Structured Document Tag (SDT) teks biasa berfungsi seperti kontrol konten di Word. Ia memungkinkan Anda menegakkan tipe data tertentu dan menampilkan petunjuk ketika bidang kosong.

```csharp
using Aspose.Words.Markup;

// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a plain‑text StructuredDocumentTag at block level
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, MarkupLevel.Block);
```

Metode `InsertStructuredDocumentTag` mengembalikan objek `StructuredDocumentTag`, yang dapat Anda konfigurasi lebih lanjut. Menambahkan **kontrol teks biasa** pada level blok memastikan kontrol berperilaku seperti paragraf terpisah, sehingga mudah untuk di‑styling nanti.

## Langkah 3: Atur teks placeholder untuk kontrol

Teks placeholder membimbing pengguna untuk memasukkan informasi yang tepat. Di Word ini muncul sebagai teks abu‑abu muda sampai pengguna mengetik sesuatu.

```csharp
// Set a title (used for identification in the Word UI)
sdt.Title = "CustomerName";

// Set the placeholder that the user sees
sdt.PlaceholderName = "Enter name";
```

Di sini kami **mengatur teks placeholder** menggunakan properti `PlaceholderName`. Properti `Title` bersifat opsional tetapi berguna untuk akses programatik nanti, terutama jika Anda perlu menemukan kontrol dalam dokumen yang lebih besar.

## Langkah 4: Tambahkan konten biasa setelah kontrol

Seringkali Anda perlu melanjutkan penulisan setelah kontrol. Metode `DocumentBuilder.Writeln` menambahkan paragraf baru dengan teks yang diberikan.

```csharp
// Write a normal paragraph after the SDT
builder.Writeln("After the SDT");
```

Ini menunjukkan bahwa dokumen tetap dapat diedit setelah penyisipan kontrol, dan Anda dapat mencampur paragraf biasa dengan kontrol konten secara bebas.

## Langkah 5: Simpan file docx

Akhirnya, persistenkan dokumen dalam memori ke file fisik. Metode `Save` secara otomatis menentukan format dari ekstensi file.

```csharp
// Save the document to a .docx file
string outputPath = @"C:\Temp\SDTExample.docx";
doc.Save(outputPath);
```

Setelah menjalankan program, buka `SDTExample.docx` di Microsoft Word. Anda akan melihat dokumen kosong dengan **kontrol teks biasa** yang menampilkan “Enter name” sebagai teks placeholder, diikuti baris “After the SDT”.

### Output yang diharapkan

Saat file dibuka:

1. Baris pertama menampilkan placeholder berwarna abu‑abu **Enter name** di dalam kotak kontrol konten.  
2. Baris kedua berisi **After the SDT** sebagai paragraf normal.

Jika Anda mengetik nama dan menekan **Enter**, placeholder akan menghilang, menandakan bahwa kontrol berfungsi sebagaimana mestinya.

## Variasi umum dan kasus tepi

| Situasi | Apa yang perlu diubah |
|-----------|----------------|
| **Beberapa placeholder** | Panggil `InsertStructuredDocumentTag` berulang kali dan berikan nilai `Title`/`PlaceholderName` yang berbeda. |
| **Kontrol inline** | Gunakan `MarkupLevel.Inline` alih‑alih `MarkupLevel.Block`. |
| **Kontrol rich‑text** | Ganti `StructuredDocumentTagType.PlainText` dengan `StructuredDocumentTagType.RichText`. |
| **Menyimpan ke stream** | Gunakan `doc.Save(stream, SaveFormat.Docx)` ketika Anda perlu mengirim file melalui HTTP. |

> **Waspadai:** Mencoba mengatur `PlaceholderName` pada SDT tipe `RichText` akan melempar `ArgumentException`. Hanya kontrol teks biasa yang mendukung placeholder.

## Contoh lengkap yang dapat dijalankan

```csharp
using System;
using Aspose.Words;
using Aspose.Words.BuildingBlocks;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document
        Document doc = new Document();

        // Step 2: Prepare a builder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a plain‑text control (SDT)
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            StructuredDocumentTagType.PlainText, MarkupLevel.Block);

        // Step 4: Set title and placeholder text
        sdt.Title = "CustomerName";
        sdt.PlaceholderName = "Enter name";

        // Step 5: Add normal content after the control
        builder.Writeln("After the SDT");

        // Step 6: Save the document
        string path = @"C:\Temp\SDTExample.docx";
        doc.Save(path);

        Console.WriteLine($"Document saved to {path}");
    }
}
```

Menjalankan program menghasilkan file yang dijelaskan pada bagian *Output yang diharapkan* di atas.

## Kesimpulan

Anda kini tahu cara **membuat dokumen Word kosong**, **menambahkan kontrol teks biasa**, **mengatur teks placeholder**, dan **menyimpan file docx** menggunakan Aspose.Words. Solusi end‑to‑end ini memungkinkan Anda menghasilkan templat Word yang membimbing pengguna dengan petunjuk jelas, menjadikan otomatisasi dokumen dapat diandalkan dan ramah pengguna.

**Langkah selanjutnya**

- Jelajahi variasi **add plain text control** seperti kontrol inline atau tag rich‑text.  
- Gabungkan beberapa placeholder untuk membangun formulir lengkap (misalnya blok alamat, tanggal).  
- Gunakan `DocumentBuilder` untuk menerapkan gaya atau menggabungkan data dari basis data, memperluas alur kerja **save docx file**.

Silakan bereksperimen dengan nilai placeholder dan tipe kontrol yang berbeda—pembuatan dokumen adalah cara yang kuat untuk mengotomatisasi laporan, kontrak, dan output Word yang berulang. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang berhubungan erat dan membangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Buat Dokumen Word dengan Aspose.Words untuk .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Buat Dokumen Word dengan Tabel Menggunakan Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Buat Dokumen Word dengan Header dan Footer Menggunakan Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}