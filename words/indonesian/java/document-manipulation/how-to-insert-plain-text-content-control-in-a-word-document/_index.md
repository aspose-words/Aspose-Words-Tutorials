---
category: general
date: 2026-10-26
description: Pelajari cara menyisipkan kontrol konten teks biasa menggunakan Aspose.Words
  dalam C#. Panduan langkah demi langkah yang mencakup StructuredDocumentTag, judul,
  dan ID tag.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert plain text content control
- structured document tag
- Aspose.Words DocumentBuilder
- C# content control
- SDT appearance
language: id
lastmod: 2026-10-26
og_description: Masukkan kontrol konten teks biasa menggunakan Aspose.Words di C#.
  Ikuti panduan ini untuk menambahkan judul, ID tag, dan menyesuaikan tampilan.
og_image_alt: Screenshot of a Word document showing an inserted plain text content
  control
og_title: Menyisipkan kontrol konten teks biasa di Word dengan C# – panduan lengkap
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  headline: How to insert plain text content control in a Word document with C#
  type: TechArticle
- description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  name: How to insert plain text content control in a Word document with C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Markup;'
  - name: Insert the plain‑text content control (SDT)
    text: '```csharp // Insert a plain‑text Structured Document Tag (SDT) with the
      default appearance. StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
      SdtType.PlainText, // The control type – plain text. SdtAppearance.Default);
      // Visual style; Default shows a light gray shading. ```'
  - name: Set a title and a tag identifier
    text: '```csharp // Give the SDT a friendly title that appears in the Content
      Controls pane. sdt.Title = "MyTag";'
  - name: Variations you might need
    text: '| Scenario | Code change | |----------|-------------| | **No visual shading**
      (border‑less) | Use `SdtAppearance.Hidden` instead of `Default`. | | **Read‑only
      field** | After insertion, set `sdt.LockContentControl = true`. | | **Pre‑populate
      with data** | Set `sdt.Text = "John Doe";` after creating '
  - name: What’s next?
    text: '- Explore other SDT types such as `RichText` or `ComboBox` for dropdowns.
      - Combine multiple content controls inside tables or repeat them using `RepeatingSection`.
      - Use `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` to read or modify
      control values programmatically.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Cara memasukkan kontrol konten teks biasa ke dalam dokumen Word dengan C#
url: /id/java/document-manipulation/how-to-insert-plain-text-content-control-in-a-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Menyisipkan kontrol konten teks biasa dalam dokumen Word dengan C#

Jika Anda perlu **menyisipkan kontrol konten teks biasa** ke dalam file Word, tutorial ini menunjukkan secara tepat cara melakukannya menggunakan Aspose.Words untuk .NET. Baik Anda sedang membangun layanan pembuatan dokumen atau mengotomatisasi pembuatan formulir, langkah‑langkah di bawah ini memungkinkan Anda menambahkan wilayah yang dapat digunakan kembali dan dapat diedit yang dapat diisi oleh pengguna akhir.

Anda akan belajar cara membuat `Document`, menggunakan `DocumentBuilder` untuk menempatkan Structured Document Tag (SDT) teks biasa, menetapkan judul yang ramah, dan memberikan pengenal tag yang unik. Panduan ini juga menjelaskan variasi umum—seperti mengubah tampilan atau menumpuk kontrol—sehingga Anda dapat menyesuaikan solusi untuk proyek apa pun.

## Prasyarat

Sebelum memulai, pastikan Anda memiliki:

- .NET 6.0 atau lebih baru (kode ini juga bekerja dengan .NET Framework 4.6+)
- Lisensi Aspose.Words untuk .NET yang valid (atau kunci evaluasi gratis)
- Visual Studio 2022 atau IDE kompatibel C# apa pun
- Pemahaman dasar tentang sintaks C#

> **Tip profesional:** Jika Anda menggunakan evaluasi gratis, ingat bahwa dokumen output akan berisi watermark. Versi berlisensi akan menghapusnya secara otomatis.

## Cara menyisipkan kontrol konten teks biasa menggunakan Aspose.Words

Inti solusi adalah proses tiga langkah:

1. **Buat `Document` dan `DocumentBuilder`.**  
2. **Sisipkan Structured Document Tag (SDT) teks biasa dengan tampilan default.**  
3. **Tetapkan judul dan pengenal tag ke SDT.**  

Setiap langkah dijelaskan di bawah ini, dengan kode lengkap yang dapat dijalankan.

### Langkah 1: Inisialisasi dokumen dan builder

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document doc = new Document();

        // DocumentBuilder lets you insert content into the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` mewakili seluruh file Word, sementara `DocumentBuilder` menyediakan metode seperti `InsertParagraph`, `InsertImage`, dan, yang paling penting untuk tutorial ini, `InsertStructuredDocumentTag`. Menginisialisasinya terlebih dahulu memberi Anda kanvas untuk menempatkan **kontrol konten teks biasa**.

### Langkah 2: Sisipkan kontrol konten teks biasa (SDT)

```csharp
        // Insert a plain‑text Structured Document Tag (SDT) with the default appearance.
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText,          // The control type – plain text.
            SdtAppearance.Default);    // Visual style; Default shows a light gray shading.
```

`SdtType.PlainText` memberi tahu Aspose.Words untuk membuat **kontrol konten teks biasa**, yang berperilaku seperti kotak teks sederhana yang dapat diedit pengguna. `SdtAppearance.Default` menampilkan kontrol dengan latar belakang halus, sehingga jelas dalam dokumen bahwa wilayah tersebut dapat diedit.

> **Mengapa menggunakan `SdtAppearance.Default`?**  
> Tampilan default adalah gaya yang paling kompatibel secara universal di semua versi Word. Jika Anda membutuhkan tampilan tanpa batas, Anda dapat beralih ke `SdtAppearance.Hidden` nanti.

### Langkah 3: Tetapkan judul dan pengenal tag

```csharp
        // Give the SDT a friendly title that appears in the Content Controls pane.
        sdt.Title = "MyTag";

        // Assign a unique tag identifier; this is useful for programmatic access later.
        sdt.Tag = "TagId";

        // (Optional) Add placeholder text inside the control.
        sdt.PlaceholderName = "Enter your text here";

        // Save the document to verify the result.
        doc.Save("output.docx");
    }
}
```

- **Judul** (`sdt.Title`) muncul di panel *Content Controls* Word, membantu pengguna akhir memahami tujuan bidang tersebut.  
- **Tag** (`sdt.Tag`) adalah pengenal yang ditujukan untuk pengembang yang dapat Anda query nanti melalui `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.  
- **PlaceholderName** menyediakan teks panduan berwarna abu-abu, meningkatkan pengalaman pengguna.

Potongan kode lengkap di atas membentuk program mandiri yang dapat Anda kompilasi dan jalankan. Setelah eksekusi, `output.docx` akan berisi satu kontrol konten teks biasa dengan judul *MyTag* dan tag *TagId*.

![Diagram yang menunjukkan penyisipan kontrol konten teks biasa dalam dokumen Word](image.png){alt="menyisipkan kontrol konten teks biasa"}

## Memahami StructuredDocumentTag (SDT) dan propertinya

A **Structured Document Tag** (SDT) adalah model objek dasar untuk kontrol konten Word. Properti yang paling relevan untuk menyisipkan kontrol teks biasa adalah:

| Properti | Tujuan | Nilai umum |
|----------|--------|------------|
| `SdtType` | Menentukan jenis kontrol (teks biasa, teks kaya, gambar, dll.) | `PlainText`, `RichText`, `ComboBox`, `DatePicker` |
| `SdtAppearance` | Gaya visual kontrol | `Default`, `Hidden`, `BoundingBox`, `Tags` |
| `Title` | Nama yang dapat dibaca manusia yang ditampilkan di panel *Content Controls* | Any short string |
| `Tag` | Pengenal yang dapat dibaca mesin yang digunakan dalam kode | Alphanumeric string |
| `PlaceholderName` | Teks yang ditampilkan ketika kontrol kosong | Custom hint text |

Ketika Anda menetapkan `SdtType.PlainText`, Word membatasi konten hanya pada karakter biasa, mencegah pemformatan kaya. Ini membuat kontrol ideal untuk bidang formulir sederhana seperti *Nama*, *Email*, atau *Nomor Telepon*.

### Variasi yang mungkin Anda butuhkan

| Skenario | Perubahan kode |
|----------|----------------|
| **Tidak ada shading visual** (tanpa batas) | Gunakan `SdtAppearance.Hidden` alih-alih `Default`. |
| **Bidang hanya-baca** | Setelah penyisipan, set `sdt.LockContentControl = true`. |
| **Pra‑isi dengan data** | Set `sdt.Text = "John Doe";` setelah membuat tag. |
| **Beberapa kontrol dalam tabel** | Sisipkan SDT di dalam sel tabel menggunakan `builder.InsertCell();` sebelum pemanggilan `InsertStructuredDocumentTag`. |

## Kesalahan umum dan cara menghindarinya

1. **Lupa menetapkan judul** – Word tetap akan membuat kontrol, tetapi pengguna tidak akan melihat deskripsi yang berarti di panel *Content Controls*. Selalu tetapkan `sdt.Title`.  
2. **Menggunakan `SdtType` yang salah** – Jika Anda membutuhkan teks biasa tetapi secara tidak sengaja memilih `RichText`, kontrol akan mengizinkan pemformatan, yang dapat merusak proses selanjutnya. Periksa kembali nilai enum.  
3. **Menyimpan ke folder hanya-baca** – Pemanggilan `doc.Save` akan melempar `UnauthorizedAccessException`. Pastikan direktori target dapat ditulisi atau gunakan `Path.GetTempPath()` untuk pengujian.  
4. **Lisensi tidak diterapkan** – Tanpa lisensi yang valid, dokumen output berisi watermark evaluasi. Terapkan lisensi di awal program Anda:  

```csharp
License lic = new License();
lic.SetLicense("Aspose.Words.lic");
```

## Contoh lengkap yang dapat dijalankan

Berikut seluruh program, siap untuk disalin‑tempel ke proyek konsol baru.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace InsertPlainTextContentControl
{
    class Program
    {
        static void Main()
        {
            // Apply license (optional for evaluation)
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1️⃣ Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a plain‑text Structured Document Tag (SDT) with default appearance
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,          // Plain text control
                SdtAppearance.Default);    // Light gray shading

            // 3️⃣ Assign a title and a tag identifier to the SDT
            sdt.Title = "MyTag";          // Human‑readable title
            sdt.Tag = "TagId";            // Unique machine identifier
            sdt.PlaceholderName = "Enter your text here";

            // (Optional) Add some introductory text before the control
            builder.MoveToDocumentStart();
            builder.Writeln("Please fill in the following field:");

            // 4️⃣ Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Output yang diharapkan:** Membuka `output.docx` di Microsoft Word menampilkan baris teks *“Please fill in the following field:”* diikuti oleh wilayah berbentuk kotak abu‑abu muda berlabel *MyTag*. Placeholder *Enter your text here* muncul dalam warna abu‑abu muda sampai pengguna mengetik.

## Kesimpulan

Anda kini tahu cara **menyisipkan kontrol konten teks biasa** ke dalam dokumen Word menggunakan Aspose.Words untuk .NET. Tutorial ini mencakup inisialisasi `Document`, penyisipan `StructuredDocumentTag` tipe `PlainText`, serta penyesuaian judul, tag, dan placeholder. Dengan memahami opsi `SdtAppearance` dan kesalahan umum, Anda dapat dengan percaya diri membangun formulir, templat, dan laporan otomatis yang mengandalkan kontrol konten yang dapat diedit.

### Apa selanjutnya?

- Jelajahi tipe SDT lain seperti `RichText` atau `ComboBox` untuk dropdown.  
- Gabungkan beberapa kontrol konten di dalam tabel atau ulangi mereka menggunakan `RepeatingSection`.  
- Gunakan `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` untuk membaca atau memodifikasi nilai kontrol secara programatis.

Silakan bereksperimen dengan variasi yang ditunjukkan sebelumnya, dan integrasikan pola ini ke dalam pipeline pembuatan dokumen Anda yang lebih besar. Selamat coding!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait dan membangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah‑demi‑langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Cara membuat kontrol konten di C# dengan Aspose.Words](/words/english/net/programming-with-sdt/how-to-create-content-control-in-c-with-aspose-words/)
- [Buat dokumen Word baru dan sisipkan kontrol konten di C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)
- [Tambahkan Konten Menggunakan Document Builder di Aspose.Words untuk .NET](/words/english/net/add-content-using-document-builder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}