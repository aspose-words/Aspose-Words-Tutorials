---
category: general
date: 2026-08-04
description: Buat dokumen Word secara programatis menggunakan C#. Pelajari cara menambahkan
  kontrol konten ke Word dan mengatur teks placeholder untuk templat dinamis.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add content control to word
- set placeholder text word
- Aspose.Words content control
- dynamic Word template C#
language: id
lastmod: 2026-08-04
og_description: Buat dokumen Word secara programatis dengan C#. Panduan ini menunjukkan
  cara menambahkan kontrol konten ke Word dan mengatur teks placeholder untuk templat
  yang dapat digunakan kembali.
og_image_alt: Screenshot of a Word document with a highlighted content control placeholder
og_title: Buat dokumen Word secara programatis – tambahkan kontrol konten & placeholder
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to add content
    control to word and set placeholder text word for dynamic templates.
  headline: Create word document programmatically – add content control and placeholder
  type: TechArticle
tags:
- C#
- Aspose.Words
- Word automation
title: Buat dokumen Word secara programatis – tambahkan kontrol konten dan placeholder
url: /id/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen Word secara programatis – tambahkan kontrol konten dan placeholder

Jika Anda perlu **create word document programmatically**, tutorial ini menunjukkan solusi lengkap yang siap dijalankan. Anda akan melihat cara **add content control to word**, memberi judul yang bermakna, dan **set placeholder text word** sehingga pengguna akhir dapat mengisi data nanti.

Panduan ini menelusuri setiap baris kode, menjelaskan mengapa setiap langkah penting, dan menyoroti jebakan umum. Pada akhirnya Anda akan memiliki file .docx yang dapat digunakan kembali sebagai templat untuk faktur, kontrak, atau dokumen berbasis formulir apa pun.

## Prasyarat

* .NET 6.0 (atau lebih baru) terpasang – kode ini menggunakan fitur bahasa C# terbaru.
* Lisensi Aspose.Words untuk .NET (versi percobaan gratis dapat digunakan untuk pengembangan).
* Visual Studio 2022 atau IDE apa pun yang dapat membangun proyek .NET.
* Familiaritas dasar dengan C# dan konsep Structured Document Tags (SDT).

> **Pro tip:** Jika Anda menjalankan contoh tanpa lisensi, Aspose.Words menambahkan watermark kecil pada file yang disimpan. Terapkan lisensi Anda lebih awal dalam program untuk menghindarinya.

## Langkah 1: Siapkan proyek dan impor namespace

Buat proyek konsol baru dan tambahkan paket NuGet Aspose.Words.

```bash
dotnet new console -n WordTemplateDemo
cd WordTemplateDemo
dotnet add package Aspose.Words
```

Sekarang impor namespace yang diperlukan di `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

Namespace ini memberi Anda akses ke kelas `Document`, `DocumentBuilder`, dan `StructuredDocumentTag` yang penting untuk **create word document programmatically**.

## Langkah 2: Inisialisasi dokumen kosong dan builder

Kelas `Document` mewakili seluruh file .docx, sementara `DocumentBuilder` memungkinkan Anda menempatkan konten pada lokasi kursor tertentu.

```csharp
// Step 2: Create an empty Word document
Document document = new Document();

// Step 2b: Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Mengapa ini penting*: Memulai dengan `Document` yang kosong memastikan Anda memiliki kontrol penuh atas setiap elemen yang Anda sisipkan. `DocumentBuilder` mempertahankan kursor internal, sehingga Anda dapat menyisipkan node tepat di tempat yang Anda butuhkan.

## Langkah 3: Buat Structured Document Tag (SDT) teks‑biasa

Structured Document Tag adalah nama teknis untuk **content control** di Word. Kami akan membuat tag teks‑biasa inline yang berperilaku seperti bidang placeholder.

```csharp
// Step 3: Create a plain‑text Structured Document Tag (content control)
StructuredDocumentTag plainTextTag = new StructuredDocumentTag(
    document,
    StructuredDocumentTagType.PlainText,   // plain‑text content control
    MarkupLevel.Inline);                    // appears inside a paragraph
```

*Mengapa ini penting*: Menggunakan `StructuredDocumentTagType.PlainText` memberi tahu Word bahwa kontrol hanya akan menerima teks biasa. `MarkupLevel.Inline` membuat kontrol berperilaku seperti kata biasa di dalam paragraf, yang ideal untuk bidang formulir.

## Langkah 4: Tetapkan judul dan teks placeholder

**title** adalah pengidentifikasi internal yang dapat dipanggil aplikasi Anda nanti. **placeholder** adalah petunjuk berwarna abu‑abu yang ditampilkan kepada pengguna sebelum mereka mengetik apa pun.

```csharp
// Step 4: Set a title and placeholder text for the content control
plainTextTag.Title = "CustomerName";          // internal name used by code
plainTextTag.PlaceholderName = "Enter name here"; // visible hint in the UI
```

Di sini kami **set placeholder text word** menjadi “Enter name here”. Saat dokumen dibuka di Microsoft Word, placeholder muncul dalam warna abu‑abu muda sampai pengguna mengetik nilai.

## Langkah 5: Sisipkan content control pada posisi kursor saat ini

`DocumentBuilder.InsertNode` menempatkan SDT tepat di mana kursor builder berada. Secara default, kursor berada di awal paragraf pertama.

```csharp
// Step 5: Insert the content control into the document at the builder's current position
builder.InsertNode(plainTextTag);
```

Jika Anda memerlukan kontrol di dalam paragraf tertentu, pindahkan kursor terlebih dahulu:

```csharp
builder.Writeln("Please provide the customer name:");
builder.InsertNode(plainTextTag);
```

Contoh ini menunjukkan cara **add content control to word** sambil mempertahankan teks di sekitarnya.

## Langkah 6: Simpan dokumen

Akhirnya, simpan file ke disk. Anda dapat memilih folder mana saja; pastikan aplikasi memiliki izin menulis.

```csharp
// Step 6: Save the document with the content control
string outputPath = @"YOUR_DIRECTORY\SDT.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Saat Anda membuka `SDT.docx` di Microsoft Word, Anda akan melihat placeholder “Enter name here” di dalam kotak abu‑abu muda. Pengguna dapat mengklik kotak tersebut dan mengganti petunjuk dengan nama pelanggan yang sebenarnya.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin, tempel, dan jalankan tanpa modifikasi (kecuali jalur output).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Optional: apply your Aspose.Words license here
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new empty document
        Document document = new Document();

        // 2. Initialize a DocumentBuilder for editing the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3. Write a brief instruction line (optional)
        builder.Writeln("Please enter the customer's name below:");

        // 4. Create a plain‑text Structured Document Tag (content control)
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(
            document,
            StructuredDocumentTagType.PlainText,
            MarkupLevel.Inline);

        // 5. Set a title and placeholder text for the content control
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // 6. Insert the content control at the current cursor position
        builder.InsertNode(plainTextTag);

        // 7. Save the document
        string outputPath = @"C:\Temp\SDT.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Expected output** – Saat Anda menjalankan program, konsol mencetak jalur file, dan file Word yang dihasilkan berisi satu baris teks diikuti placeholder abu‑abu yang menampilkan “Enter name here”.

## Variasi umum dan kasus tepi

| Skenario | Cara menyesuaikan kode |
|----------|-----------------------|
| **Placeholder multi‑baris** | Gunakan `StructuredDocumentTagType.RichText` alih-alih `PlainText` dan atur `plainTextTag.MultipleLines = true;`. |
| **Mengulang kontrol yang sama** | Klon tag dengan `plainTextTag.Clone(true)` dan sisipkan klonnya di mana pun diperlukan. |
| **Mengikat ke sumber data** | Setelah pengguna mengisi dokumen, ambil nilai dengan `document.GetChildNodes(NodeType.StructuredDocumentTag, true).Cast<StructuredDocumentTag>().First(t => t.Title == "CustomerName").GetText();`. |
| **Mengunci kontrol** | Atur `plainTextTag.LockContentControl = true;` untuk mencegah pengguna menghapus kontrol. |
| **Mengubah warna placeholder** | Word tidak menyediakan styling placeholder melalui SDK; Anda harus mengedit templat secara manual atau menggunakan macro Word. |

## Praktik terbaik dan pemecahan masalah

* **Selalu tetapkan title** – Tanpa title, menemukan kontrol nanti menjadi sulit.
* **Hindari placeholder kosong** – Word menyembunyikan placeholder kosong jika properti `ShowPlaceholderText` pada kontrol bernilai false. Jaga agar tetap true untuk UX yang lebih baik.
* **Validasi jalur output** – Jika `document.Save` melempar `UnauthorizedAccessException`, pastikan folder ada dan proses Anda memiliki hak menulis.
* **Lisensi lebih awal** – Letakkan kode lisensi sebelum objek Aspose.Words apa pun diinstansiasi untuk mencegah watermark percobaan.

## Kesimpulan

Anda sekarang tahu cara **create word document programmatically**, **add content control to word**, dan **set placeholder text word** menggunakan Aspose.Words untuk .NET. Contoh lengkap menunjukkan setiap langkah yang diperlukan, mulai dari inisialisasi dokumen hingga menyimpan templat yang dapat diisi oleh pengguna akhir.

Selanjutnya, Anda mungkin ingin menjelajahi:

* Menambahkan **repeating content controls** untuk tabel (kata kunci sekunder: add content control to word).
* Mengisi placeholder dengan data dari basis data (kata kunci sekunder: set placeholder text word).
* Mengonversi .docx yang dihasilkan ke PDF atau HTML untuk pemrosesan lanjutan.

Silakan bereksperimen dengan berbagai jenis tag, styling, dan teknik pengikatan data. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Buat Dokumen Word Baru](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Buat Dokumen Word dengan Header dan Footer Menggunakan Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Buat Dokumen Word dengan Tabel Menggunakan Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}