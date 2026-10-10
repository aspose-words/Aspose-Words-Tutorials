---
category: general
date: 2026-10-10
description: Buat dokumen Word secara programatis dengan Aspose.Words dan sisipkan
  kontrol konten teks biasa – panduan langkah demi langkah untuk pengembang .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- insert plain text content control
language: id
lastmod: 2026-10-10
og_description: Buat dokumen Word secara programatis dengan Aspose.Words dan tambahkan
  kontrol konten teks biasa yang menampilkan teks placeholder, memungkinkan bidang
  formulir dinamis dalam file .docx.
og_image_alt: Screenshot of a Word document displaying a plain text content control
  placeholder
og_title: Buat Dokumen Word Secara Programatis dan Tambahkan Kontrol Konten Teks Biasa
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Create word document programmatically with Aspose.Words and insert
    plain text content control – a step‑by‑step guide for .NET developers.
  headline: How to create word document programmatically and insert plain text content
    control
  type: TechArticle
tags:
- word
- document automation
- content control
- Aspose.Words
- C#
title: Cara membuat dokumen Word secara programatis dan menyisipkan kontrol konten
  teks biasa
url: /id/java/document-manipulation/how-to-create-word-document-programmatically-and-insert-plai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara membuat dokumen Word secara programatis dan menyisipkan kontrol konten teks biasa

Jika Anda perlu **membuat dokumen Word secara programatis**, panduan ini menunjukkan secara tepat cara melakukannya dengan Aspose.Words untuk .NET. Dalam beberapa baris kode saja Anda juga akan belajar cara **menyisipkan kontrol konten teks biasa** (juga disebut Structured Document Tag) sehingga dokumen dapat berfungsi sebagai formulir yang dapat diisi.

Anda akan menelusuri alur kerja lengkap—dari menginisialisasi objek `Document` baru hingga menyimpan file .docx akhir. Tidak diperlukan alat eksternal, dan contoh ini bekerja dengan .NET 6, .NET 7, atau runtime .NET terbaru mana pun.

## Prasyarat

* Lisensi Aspose.Words untuk .NET yang valid (atau gunakan mode evaluasi gratis).  
* .NET 6+ SDK terpasang.  
* IDE seperti Visual Studio 2022, Rider, atau VS Code.  

Jika Anda belum menginstal paket NuGet Aspose.Words, jalankan:

```bash
dotnet add package Aspose.Words
```

## Langkah 1: Membuat dokumen Word secara programatis

Langkah pertama adalah menginstansiasi `Document` kosong dan `DocumentBuilder`. Builder memberikan API yang nyaman untuk menambahkan konten, halaman, dan Structured Document Tags (SDT).

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;
using Aspose.Words.Markup;

// Create an empty document and a builder attached to it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Mengapa ini penting** – `Document` mewakili seluruh file .docx dalam memori. Dengan membuatnya secara programatis Anda menghindari beban membuka file templat, yang berguna untuk menghasilkan laporan, faktur, atau dokumen on‑the‑fly apa pun.

## Langkah 2: Menyisipkan kontrol konten teks biasa

**Kontrol konten teks biasa** (SDT) memungkinkan pengguna mengetik teks ke dalam wilayah yang telah ditentukan. Ini juga mendukung teks placeholder yang muncul ketika kontrol kosong.

```csharp
// Insert a plain‑text Structured Document Tag (SDT) with an identifier "MyTag"
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Set placeholder text that shows inside the control when it is empty
plainTextTag.PlaceholderName = "Enter name";
```

**Penjelasan** – `InsertStructuredDocumentTag` membuat SDT pada posisi kursor saat ini dari `DocumentBuilder`. Nilai enum `StructuredDocumentTagType.PlainText` memberi tahu Aspose.Words untuk menampilkan kotak teks biasa alih-alih kotak kombo atau pemilih tanggal. Properti `PlaceholderName` memberikan petunjuk visual bagi pengguna, mirip dengan teks hint abu-abu yang Anda lihat pada formulir Word modern.

### Variasi umum

| Variasi | Cara mencapainya |
|-----------|-------------------|
| **Rich‑text content control** | Use `StructuredDocumentTagType.RichText` instead of `PlainText`. |
| **Repeating section** | Use `StructuredDocumentTagType.Group` and nest other tags inside. |
| **Custom XML mapping** | Call `plainTextTag.SetXmlMapping(xmlPart, xpath, false)` after creating an `XmlPart`. |

## Langkah 3: Menambahkan konten dokumen tambahan (opsional)

Anda dapat menambahkan paragraf biasa, tabel, atau gambar sebelum atau sesudah kontrol konten. Berikut contoh singkat yang menambahkan judul dan paragraf:

```csharp
// Add a heading above the content control
builder.Font.Size = 16;
builder.Font.Bold = true;
builder.Writeln("Employee Information");

// Move the cursor back to the placeholder location (already set by InsertStructuredDocumentTag)
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Writeln(); // Adds a line break after the control
```

**Tip** – Kursor builder secara otomatis berpindah ke akhir SDT yang disisipkan, sehingga panggilan `Writeln` berikutnya akan muncul setelah kontrol.

## Langkah 4: Menyimpan dokumen yang berisi kontrol konten

Akhirnya, tulis dokumen ke disk. Anda dapat memilih format yang didukung apa pun (`.docx`, `.pdf`, `.html`, dll.). Untuk tutorial ini kami menyimpan sebagai file Word.

```csharp
// Save the document to the specified path
string outputPath = Path.Combine(Environment.CurrentDirectory, "SdtExample.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### Output yang diharapkan

Saat Anda membuka *SdtExample.docx* di Microsoft Word, Anda akan melihat:

1. Sebuah judul **Employee Information**.  
2. Sebuah kontrol konten teks biasa dengan placeholder abu-abu **Enter name**.  

Jika Anda mengklik di dalam kontrol, placeholder akan menghilang dan Anda dapat mengetik teks apa pun. Identifier tag kontrol (`MyTag`) dapat diakses secara programatis nanti untuk ekstraksi data atau validasi.

## Contoh lengkap yang dapat dijalankan

Berikut adalah aplikasi konsol mandiri yang menggabungkan semua langkah. Salin kode ke dalam proyek konsol .NET baru dan jalankan.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordContentControlDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create an empty document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a plain‑text content control (SDT) with a tag identifier
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");

            // 3️⃣ Set placeholder text that appears when the control is empty
            sdt.PlaceholderName = "Enter name";

            // Optional: add a heading above the control
            builder.MoveToDocumentStart(); // Ensure heading appears before the control
            builder.Font.Size = 16;
            builder.Font.Bold = true;
            builder.Writeln("Employee Information");

            // Move back to the end of the control to continue writing
            builder.MoveToDocumentEnd();
            builder.Font.Size = 12;
            builder.Font.Bold = false;
            builder.Writeln(); // Adds a line break after the control

            // 4️⃣ Save the document
            string outputPath = Path.Combine(Environment.CurrentDirectory, "SdtExample.docx");
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

Menjalankan program mencetak jalur lengkap file yang dihasilkan. Buka file di Word untuk memverifikasi bahwa **kontrol konten teks biasa** muncul dengan placeholder-nya.

## Pemecahan masalah dan kasus tepi

| Masalah | Penyebab | Solusi |
|-------|-------|-----|
| Teks placeholder tidak muncul | Kontrol sudah terisi teks atau dokumen dibuka dalam mode yang menyembunyikan placeholder. | Pastikan SDT kosong sebelum menyimpan, atau setel `sdt.IsShowingPlaceholder = true` (tersedia di versi Aspose.Words yang lebih baru). |
| Kontrol konten menghilang setelah disimpan sebagai PDF | Ekspor PDF tidak mempertahankan bidang formulir interaktif secara default. | Gunakan `PdfSaveOptions` dengan `SaveFormat.Pdf` dan setel `ExportDocumentStructure = true`. |
| Identifier tag tidak ditemukan selama pemrosesan selanjutnya | Nama tag salah eja atau ditimpa. | Verifikasi identifier yang diberikan ke `InsertStructuredDocumentTag` cocok dengan nama yang Anda query nanti (`MyTag`). |

## Praktik terbaik untuk membuat dokumen Word secara programatis

* **Gunakan kembali satu `DocumentBuilder`** per dokumen untuk menghindari alokasi memori yang tidak perlu.  
* **Setel font dan gaya sebelum menulis teks**; mengubahnya setelah konten ditambahkan dapat menyebabkan format yang tidak konsisten.  
* **Bebaskan objek besar** (mis., `MemoryStream` jika Anda men-stream dokumen) dengan pernyataan `using`.  
* **Validasi dokumen** dengan `doc.UpdateFields()` dan `doc.UpdatePageLayout()` sebelum menyimpan, terutama ketika Anda menambahkan tabel atau gambar.  

## Kesimpulan

Anda kini tahu cara **membuat dokumen Word secara programatis** dan **menyisipkan kontrol konten teks biasa** menggunakan Aspose.Words untuk .NET. Contoh lengkap menunjukkan inisialisasi dokumen, penyisipan SDT dengan teks placeholder, konten tambahan opsional, dan penyimpanan ke file .docx.

Dari sini Anda dapat:

* Ganti kontrol teks biasa dengan kontrol **rich‑text** atau **date picker**.  
* Isi dokumen dengan data dari basis data dan kemudian ekstrak nilai yang dimasukkan nanti menggunakan `StructuredDocumentTag.GetText()`.  
* Ekspor dokumen yang sama ke format PDF, HTML, atau OpenXML sambil mempertahankan bidang formulir.

Bereksperimenlah dengan berbagai tipe tag dan jelajahi API Aspose.Words untuk membangun templat Word yang canggih dan dapat diisi yang terintegrasi mulus ke dalam aplikasi .NET Anda. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Menambahkan Field Form Combo Box ke Dokumen Word dengan Aspose.Words untuk .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Menyisipkan Field Form Input Teks di Dokumen Word](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Menambahkan Field Form Check Box ke Dokumen Word dengan Aspose.Words untuk .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}