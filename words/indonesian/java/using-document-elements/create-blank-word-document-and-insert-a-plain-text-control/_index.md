---
category: general
date: 2026-09-18
description: Buat dokumen Word kosong menggunakan C# dan atur teks placeholder, kemudian
  simpan dokumen sebagai docx. Pelajari cara menyisipkan kontrol teks biasa dan menambahkan
  nama placeholder.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set placeholder text
- save document as docx
- insert plain text control
- add placeholder name
language: id
lastmod: 2026-09-18
og_description: Buat dokumen Word kosong menggunakan C#. Atur teks placeholder, sisipkan
  kontrol teks biasa, tambahkan nama placeholder, dan simpan dokumen sebagai docx.
og_image_alt: Screenshot of a Word document showing a plain‑text content control with
  placeholder text
og_title: Buat dokumen Word kosong dengan teks placeholder – panduan C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  headline: Create blank Word document and insert a plain‑text control
  type: TechArticle
- description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  name: Create blank Word document and insert a plain‑text control
  steps:
  - name: An empty Word file (the **blank Word document** you created)
    text: An empty Word file (the **blank Word document** you created)
  - name: A plain‑text content control (the **insert plain text control** step)
    text: A plain‑text content control (the **insert plain text control** step)
  - name: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
    text: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
  - name: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
    text: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
  - name: A line of regular text after the control, demonstrating that normal content
      can follow
    text: A line of regular text after the control, demonstrating that normal content
      can follow
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Buat dokumen Word kosong dan sisipkan kontrol teks biasa
url: /id/java/using-document-elements/create-blank-word-document-and-insert-a-plain-text-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Buat dokumen Word kosong dan sisipkan kontrol plain‑text

Jika Anda perlu **create blank Word document** secara programatis, panduan ini menunjukkan cara melakukannya dengan C#. Anda akan belajar untuk **insert plain text control**, **set placeholder text**, **add placeholder name**, dan akhirnya **save document as docx**. Langkah‑langkahnya sepenuhnya mandiri, sehingga Anda dapat menyalin kode ke proyek .NET apa pun dan menjalankannya segera.

Bekerja dengan file Word sering memerlukan titik awal yang bersih—sebuah dokumen kosong yang sudah berisi kontrol yang akan diisi oleh pengguna Anda. Pada akhir tutorial ini Anda akan memiliki file `.docx` yang berisi kontrol konten plain‑text dengan placeholder yang membantu, diikuti oleh konten biasa.

## Prasyarat

- .NET 6.0 atau lebih baru (kode juga berfungsi dengan .NET Framework 4.6+)
- Referensi ke pustaka **Aspose.Words for .NET** (tersedia melalui NuGet `Install-Package Aspose.Words`)
- Familiaritas dasar dengan aplikasi konsol C#
- Izin menulis ke folder output yang Anda tentukan dalam `doc.save(...)`

## Apa yang akan Anda bangun

Dokumen akhir (`SDT.docx`) berisi:

1. Sebuah file Word kosong ( **blank Word document** yang Anda buat)
2. Kontrol konten plain‑text (langkah **insert plain text control**)
3. Teks placeholder yang muncul di dalam kontrol hingga pengguna mengetik sesuatu (langkah **set placeholder text**)
4. Nama placeholder yang dapat digunakan untuk akses programatis nanti (langkah **add placeholder name**)
5. Sebuah baris teks biasa setelah kontrol, menunjukkan bahwa konten normal dapat mengikuti

## Langkah 1: Buat dokumen Word kosong

Operasi pertama adalah menginstansiasi objek `Document` kosong. Objek ini mewakili **blank Word document** yang sepenuhnya baru dalam memori.

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

// Step 1: Create a new blank document
Document doc = new Document();
```

*Mengapa ini penting:* `Document` kosong memberi Anda kontrol penuh atas setiap elemen yang Anda tambahkan, memastikan tidak ada gaya atau bagian tersembunyi yang mengganggu kontrol konten yang akan Anda sisipkan nanti.

## Langkah 2: Inisialisasi DocumentBuilder

`DocumentBuilder` adalah kelas pembantu yang memungkinkan Anda menulis ke dalam `Document`. Ia melacak posisi kursor saat ini dan menyediakan metode untuk menyisipkan berbagai jenis objek Word.

```csharp
// Step 2: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Mengapa ini penting:* Menggunakan `DocumentBuilder` menyederhanakan proses menambahkan **plain‑text control** karena builder mengetahui titik sisipan yang tepat.

## Langkah 3: Sisipkan kontrol plain‑text

Sekarang kita menambahkan **plain‑text content control** (juga dikenal sebagai Structured Document Tag, atau SDT). Tipe kontrol `StructuredDocumentTagType.PLAIN_TEXT` memberi tahu Word untuk memperlakukan konten sebagai teks biasa, bukan format kaya.

```csharp
// Step 3: Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");
```

*Mengapa ini penting:* Metode `InsertStructuredDocumentTag` membuat kontrol dan mengembalikan referensi (`sdt`) yang dapat Anda konfigurasikan lebih lanjut, seperti menambahkan teks placeholder atau nama khusus.

## Langkah 4: Atur teks placeholder dan tambahkan nama placeholder

Teks placeholder memberi pengguna petunjuk visual tentang apa yang harus diketik. Langkah **add placeholder name** menetapkan pengidentifikasi programatis yang dapat Anda query nanti dengan `doc.GetChildNodes` atau API serupa.

```csharp
// Step 4a: Set a placeholder text that appears when the SDT is empty
sdt.SetPlaceholderName("Enter text…");

// Step 4b: Add a placeholder name (tag ID) for later retrieval
sdt.Tag = "MyTag";
```

*Mengapa ini penting:* `SetPlaceholderName` mengatur teks petunjuk abu‑abu yang ditampilkan di dalam kontrol konten. Menetapkan `Tag` (aksi **add placeholder name**) memungkinkan Anda menemukan kontrol dalam pohon dokumen tanpa memindai seluruh file.

## Langkah 5: Tambahkan konten biasa setelah kontrol

Untuk membuktikan bahwa dokumen berlanjut secara normal setelah kontrol, kami menulis satu baris teks sederhana.

```csharp
// Step 5: Add regular content after the SDT
builder.Writeln("After the tag.");
```

## Langkah 6: Simpan dokumen sebagai docx

Akhirnya, kami menyimpan dokumen dalam memori ke disk. Ini adalah operasi **save document as docx** yang menghasilkan file yang dapat Anda buka di Microsoft Word.

```csharp
// Step 6: Save the document as a .docx file
string outputPath = @"YOUR_DIRECTORY/SDT.docx";
doc.Save(outputPath);
```

*Mengapa ini penting:* Menggunakan format `.docx` memastikan kompatibilitas maksimum dengan versi Word modern, Google Docs, dan alat kompatibel Office lainnya.

## Contoh lengkap yang dapat dijalankan

Berikut adalah program lengkap yang dapat Anda salin ke proyek console‑app. Ganti `YOUR_DIRECTORY` dengan jalur folder yang sebenarnya di mesin Anda.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

namespace WordSdtExample
{
    class Program
    {
        static void Main()
        {
            // Create a new blank Word document
            Document doc = new Document();

            // Initialize a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");

            // Set a placeholder text that appears when the SDT is empty
            sdt.SetPlaceholderName("Enter text…");

            // Add a placeholder name (tag) for later retrieval
            sdt.Tag = "MyTag";

            // Add regular content after the SDT
            builder.Writeln("After the tag.");

            // Save the document as a .docx file
            string outputPath = @"C:\Temp\SDT.docx"; // change to your folder
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Hasil yang diharapkan

- Membuka `SDT.docx` di Word menampilkan kotak abu‑abu kosong dengan teks **Enter text…** di dalamnya.
- Kotak tersebut adalah kontrol konten plain‑text; Anda dapat mengetik langsung di dalamnya.
- Di bawah kotak, baris **After the tag.** muncul sebagai teks paragraf biasa.

Jika placeholder tidak muncul, pastikan Anda menggunakan versi terbaru Aspose.Words (v23.1 atau lebih baru) dan dokumen dibuka di versi Word yang mendukung kontrol konten (Word 2007+).

## Variasi umum dan kasus tepi

| Scenario | How to adapt the code |
|----------|-----------------------|
| **Multiple placeholders** | Panggil `InsertStructuredDocumentTag` lagi dengan ID tag yang berbeda dan nama placeholder. |
| **Rich‑text control** | Gunakan `StructuredDocumentTagType.RichText` alih-alih `PlainText`. |
| **Setting default text** | Setelah penyisipan, tetapkan `sdt.Text = "Default value";` – teks ini menggantikan placeholder saat dokumen dimuat. |
| **Saving to a stream** | Ganti `doc.Save(outputPath);` dengan `doc.Save(stream, SaveFormat.Docx);` untuk mengirim file melalui HTTP. |
| **Changing placeholder color** | Gunakan `sdt.PlaceholderTextColor = System.Drawing.Color.Gray;` (memerlukan `using System.Drawing`). |

## Tips profesional

- **Reuse the tag ID**: Menjaga tag (`MyTag`) konsisten di seluruh dokumen memungkinkan Anda mengotomatisasi pengisian data nanti dengan `doc.Range.Replace` atau `StructuredDocumentTagCollection`.
- **Avoid hard‑coded paths**: Gunakan `Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), "SDT.docx")` untuk lokasi output yang dapat dipindahkan.
- **Performance**: Jika Anda perlu menghasilkan ribuan dokumen, buat satu templat `Document` dengan SDT yang sudah ada, lalu kloning dengan `doc.Clone()` untuk setiap iterasi.

## Kesimpulan

Anda sekarang tahu cara **create blank Word document**, **insert plain text control**, **set placeholder text**, **add placeholder name**, dan **save document as docx** menggunakan Aspose.Words untuk .NET. Pola ini menjadi dasar untuk membangun templat Word berisi formulir, laporan otomatis, atau solusi apa pun yang memerlukan placeholder yang dapat diedit pengguna.

Silakan bereksperimen dengan tipe kontrol lain, menggabungkan beberapa placeholder, atau mengintegrasikan kode ini ke dalam API web yang mengembalikan file `.docx` yang dihasilkan langsung ke pemanggil. Untuk langkah selanjutnya, jelajahi **populate a content control with data programmatically** atau **convert the generated Word file to PDF** menggunakan fitur konversi bawaan Aspose.Words. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang terkait erat yang membangun teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda.

- [Insert Text Input Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}