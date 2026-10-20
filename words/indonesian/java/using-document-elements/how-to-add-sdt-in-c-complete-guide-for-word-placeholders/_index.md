---
category: general
date: 2026-08-14
description: Cara menambahkan SDT dengan cepat menggunakan Aspose.Words. Pelajari
  cara membuat placeholder kata dan menyisipkan kontrol teks biasa dalam file .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add sdt
- create word placeholder
- insert plain text control
- Aspose.Words SDT
- C# Word automation
language: id
lastmod: 2026-08-14
og_description: Cara menambahkan SDT di C# menggunakan Aspose.Words. Ikuti tutorial
  ini untuk membuat placeholder kata dan menyisipkan kontrol teks biasa untuk dokumen
  dinamis.
og_image_alt: Screenshot of a Word document showing a plain‑text Structured Document
  Tag placeholder
og_title: Cara menambahkan SDT di C# – panduan placeholder Word langkah demi langkah
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add SDT quickly with Aspose.Words. Learn to create word placeholder
    and insert plain text control in a .docx file.
  headline: How to add SDT in C# – complete guide for Word placeholders
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- SDT
- Document Automation
title: Cara menambahkan SDT di C# – panduan lengkap untuk placeholder Word
url: /id/java/using-document-elements/how-to-add-sdt-in-c-complete-guide-for-word-placeholders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara menambahkan SDT di C# – panduan lengkap untuk placeholder Word

Jika Anda perlu **how to add sdt** dalam file Word, tutorial ini menunjukkan langkah‑langkah tepat menggunakan Aspose.Words untuk .NET. Pada akhir panduan, Anda akan dapat **create word placeholder** tag yang memungkinkan pengguna akhir mengetik langsung ke dalam dokumen, dan Anda akan memahami cara **insert plain text control** dengan andal.

Bekerja dengan Structured Document Tags (SDTs) menghilangkan kebutuhan akan bidang formulir manual dan memberi Anda cara yang bersih dan terprogram untuk membuat kontrak, laporan, atau surat dinamis. Contoh di bawah mencakup semua hal mulai dari penyiapan proyek hingga menyimpan file .docx akhir, sehingga Anda dapat menyalin‑tempel kode ke dalam solusi Anda sendiri tanpa kehilangan dependensi apa pun.

## Prasyarat

- .NET 6.0 atau lebih baru (kode juga berfungsi dengan .NET Framework 4.6+)
- Visual Studio 2022 atau IDE C# apa pun yang Anda sukai
- Lisensi Aspose.Words untuk .NET (lisensi sementara gratis dapat digunakan untuk pengujian)
- Familiaritas dasar dengan sintaks C# dan konsep SDT

> **Pro tip:** Jika Anda berencana mendistribusikan dokumen yang dihasilkan, sematkan file lisensi untuk menghindari watermark evaluasi.

## Langkah 1: Siapkan proyek dan impor Aspose.Words

Buat aplikasi konsol baru dan tambahkan paket NuGet Aspose.Words:

```bash
dotnet new console -n SdtDemo
cd SdtDemo
dotnet add package Aspose.Words
```

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
```

Direktif `using` ini memberi Anda akses ke kelas `Document`, `DocumentBuilder`, dan `StructuredDocumentTag` yang diperlukan untuk operasi **insert plain text control**.

## Langkah 2: Inisialisasi dokumen dan builder

Blok kode pertama membuat dokumen Word kosong dan `DocumentBuilder` yang memungkinkan Anda menulis konten ke dalamnya.

```csharp
// Step 2: Create a new document and a builder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` bekerja seperti kursor; setiap panggilan berikutnya menambahkan konten pada posisi saat ini. Inisialisasi dokumen adalah dasar untuk setiap skenario **how to add sdt** karena SDT harus menjadi bagian dari instance `Document` yang aktif.

## Langkah 3: Sisipkan Structured Document Tag (SDT) teks biasa

Sekarang kita **insert plain text control** yang berfungsi sebagai placeholder dimana pengguna dapat mengetik nama, tanggal, atau nilai kustom apa pun.

```csharp
// Step 3: Insert a plain‑text Structured Document Tag (SDT)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
        StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);
```

- `StructuredDocumentTagType.PlainText` memberi tahu Aspose.Words untuk membuat bidang teks sederhana.
- `SdtAppearanceTags.Default` memberikan tag gaya visual standar Word (kotak berbayang ketika dokumen dibuka di Word).

## Langkah 4: Konfigurasikan SDT dengan judul dan teks placeholder

SDT dengan nama yang baik membuat dokumen menjadi jelas bagi pengguna akhir. Di sini kami **create word placeholder** metadata dan mengatur petunjuk yang muncul di dalam bidang.

```csharp
// Step 4: Give the SDT a meaningful title and placeholder text
plainTextTag.Title = "CustomerName";
plainTextTag.PlaceholderName = "Enter name here";
```

- `Title` adalah pengenal internal yang dapat Anda gunakan nanti saat mengekstrak atau memperbarui nilai secara terprogram.
- `PlaceholderName` adalah petunjuk berwarna abu-abu yang ditampilkan di Word, memberi tahu pengguna apa yang harus diketik.

## Langkah 5: Tambahkan konten di sekitarnya

Sebuah dokumen jarang hanya terdiri dari satu SDT. Anda biasanya memerlukan paragraf reguler sebelum dan sesudah placeholder. Gunakan metode `WriteLine` builder untuk menambahkan teks statis.

```csharp
// Step 5: Add regular content before and after the SDT
builder.Writeln("Dear ");
builder.InsertNode(plainTextTag);   // Re‑insert the tag at the current cursor position
builder.Writeln(",");
builder.Writeln("After the SDT");
```

Pemanggilan `InsertNode` menempatkan SDT yang telah dibuat sebelumnya tepat di tempat yang Anda butuhkan, mempertahankan alur teks di sekitarnya.

## Langkah 6: Simpan dokumen ke file .docx

Akhirnya, simpan dokumen ke disk. Jalur dapat berupa absolut atau relatif terhadap folder proyek.

```csharp
// Step 6: Save the document to a file
string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Membuka `SDT.docx` di Microsoft Word menampilkan placeholder abu-abu yang berisi **Enter name here**. Pengguna dapat mengklik bidang, mengetik nilai, dan dokumen akan mempertahankan nilai tersebut saat disimpan kembali.

## Contoh lengkap yang dapat dijalankan

Menggabungkan semua bagian memberikan Anda program mandiri yang dapat dijalankan secara langsung:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a plain‑text SDT
        StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
            StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);

        // Configure the SDT
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // Add surrounding content
        builder.Writeln("Dear ");
        builder.InsertNode(plainTextTag);
        builder.Writeln(",");
        builder.Writeln("After the SDT");

        // Save the file
        string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Expected output** ketika Anda menjalankan program:

```
Document saved to C:\YourProject\bin\Debug\net6.0\SDT.docx
```

Membuka `SDT.docx` yang dihasilkan menampilkan:

```
Dear [Enter name here],
After the SDT
```

Teks dalam kurung adalah placeholder **insert plain text control** yang dapat diganti oleh pengguna.

## Variasi umum dan kasus tepi

| Situasi | Cara menyesuaikan kode |
|-----------|-----------------------|
| **Multiple placeholders** | Panggil `InsertStructuredDocumentTag` berulang kali dan berikan setiap tag `Title` yang unik. |
| **Rich‑text SDT** | Gunakan `StructuredDocumentTagType.RichText` alih‑alih `PlainText`. |
| **Lock the placeholder** | Setel `plainTextTag.LockContentControl = true;` untuk mencegah pengguna menghapus bidang. |
| **Pre‑populate with a value** | Tetapkan `plainTextTag.Text = "John Doe";` sebelum menyimpan. |
| **Conditional appearance** | Gunakan `plainTextTag.SdtType = StructuredDocumentTagType.CheckBox;` untuk kontrol kotak centang. |

Variasi ini memungkinkan Anda **create word placeholder** struktur yang cocok dengan hampir semua skenario seperti formulir.

## Tips pemecahan masalah

- **Placeholder not visible** – Pastikan Anda membuka file di Microsoft Word (atau penampil yang kompatibel). Beberapa editor ringan menyembunyikan SDT.
- **License warning** – Jika Anda melihat watermark evaluasi, verifikasi bahwa file lisensi Anda telah dimuat dengan benar (`License license = new License(); license.SetLicense("Aspose.Words.lic");`).
- **Incorrect cursor position** – Setelah menyisipkan SDT, kursor builder tetap *setelah* tag. Jika Anda perlu menambahkan teks *di dalam* tag, gunakan `builder.MoveTo(plainTextTag);` sebelum menulis.

## Kesimpulan

Anda sekarang tahu **how to add sdt** ke dokumen Word menggunakan Aspose.Words untuk .NET, cara **create word placeholder** tag, dan cara **insert plain text control** yang dapat diedit langsung oleh pengguna di Word. Contoh lengkap menunjukkan inisialisasi, penyisipan tag, konfigurasi, konten di sekitarnya, dan penyimpanan—semuanya dalam satu program yang dapat dijalankan.

Selanjutnya, jelajahi topik terkait seperti **insert rich text control**, **populate SDTs from a database**, atau **convert the final document to PDF**. Semua ini dibangun di atas dasar yang sama yang dibahas di sini, sehingga Anda dapat memperluas pipeline otomatisasi Anda dengan percaya diri.

Selamat coding, dan silakan bereksperimen dengan berbagai tipe SDT untuk memenuhi kebutuhan otomatisasi dokumen Anda!

## Apa yang Harus Anda Pelajari Selanjutnya?

Tutorial berikut mencakup topik yang sangat terkait yang dibangun di atas teknik yang ditunjukkan dalam panduan ini. Setiap sumber daya menyertakan contoh kode lengkap yang berfungsi dengan penjelasan langkah demi langkah untuk membantu Anda menguasai fitur API tambahan dan mengeksplorasi pendekatan implementasi alternatif dalam proyek Anda sendiri.

- [Cara membuat bidang formulir dan menambahkan konten menggunakan DocumentBuilder di Aspose.Words untuk Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Cara Membuat Rentang yang Dapat Diedit dalam Dokumen Hanya‑Baca Menggunakan Aspose.Words untuk Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)
- [Menambahkan Bookmark Word dengan Aspose.Words untuk Java – Sisipkan, Perbarui, Hapus](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}